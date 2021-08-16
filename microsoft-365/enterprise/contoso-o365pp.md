---
title: Déploiement de Microsoft 365 Apps for enterprise pour Consoto.
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre la façon dont Contoso utilise Microsoft Endpoint Configuration Manager pour déployer de Microsoft 365 Apps for enterprise.
ms.openlocfilehash: 65c73ccccd3e0ca5a3d9e09d1643692d56f5c341
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58356287"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Déploiement de Microsoft 365 Apps for enterprise pour Consoto.

Contoso a mis à niveau ses PC vers Windows 10 Entreprise et Applications Microsoft 365 pour les grandes entreprises pour permettre une collaboration plus efficace, une meilleure sécurité et une expérience de bureau plus moderne. Après avoir évalué ses besoins en matière d’infrastructure et d’entreprise, Contoso a identifié ces exigences clés pour le déploiement :

- Tous les PC doivent s’exécuter Applications Microsoft 365 pour les grandes entreprises.
- Le déploiement doit utiliser l’infrastructure et les outils de gestion existants dans la mesure du possible.
- Le déploiement doit prendre en charge plusieurs langues et architectures existantes sur les appareils des utilisateurs.
- Les PC doivent rester à jour et sécurisés avec un minimum de coûts d’administration et un impact minimal sur les utilisateurs.

## <a name="deployment-tools"></a>Outils de déploiement

En fonction de ses besoins, Contoso a choisi de déployer Windows 10 Entreprise et Applications Microsoft 365 pour les grandes entreprises configuration manager (Current Branch). Configuration Manager assure la mise à l’échelle des environnements de grande taille et permet de contrôler de manière étendue l’installation, les mises à jour et les paramètres. Il inclut également des fonctionnalités intégrées qui simplifient et optimisent le déploiement et la gestion d’Office, notamment :

- Cache homologue, qui peut aider avec une capacité réseau limitée lors du déploiement sur des appareils dans des emplacements distants.
- Le tableau Office de gestion des clients, qui facilite le déploiement de Office et la surveillance des mises à jour, et donne aux administrateurs l’accès aux dernières fonctionnalités de déploiement et de gestion.
- Déploiement de packs linguistiques intelligent, y compris le déploiement automatique de la même langue que le système d’exploitation.
- Une méthode entièrement prise en charge et facile à utiliser pour supprimer les versions existantes de Office d’un client pendant le déploiement.

Outre Configuration Manager, Contoso a utilisé le Shared Computer Toolkit de préparation pour les compléments Office et [VBA,](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps)un outil gratuit de Microsoft, pour évaluer les problèmes de compatibilité avec leurs macros et compléments Office.

## <a name="managing-deployment-and-updates"></a>Gestion du déploiement et des mises à jour

Applications Microsoft 365 pour les grandes entreprises a un nouveau modèle de publication : Office en tant que service. Le modèle de service permet de rester à jour facilement avec les nouvelles fonctionnalités. Toutefois, il est souvent nécessaire que les services informatiques modifient la façon dont ils déploient et testent les nouvelles publication. Pour minimiser les problèmes de compatibilité et s’assurer que leurs ordinateurs restent à jour, Contoso a déployé Windows et Office en deux étapes :

- Tout d’abord, ils Applications Microsoft 365 pour les grandes entreprises sur un petit ensemble d’appareils représentatifs au sein de l’organisation. Ce groupe pilote a été utilisé pour tester les applications, les modules et le matériel avec Applications Microsoft 365 pour les grandes entreprises.
- Quatre mois plus tard, après avoir résolu tous les problèmes essentiels rencontrés avec les applications, les compléments et le matériel dans le groupe pilote, Contoso a déployé Microsoft 365 Apps for enterprise sur le reste des périphériques de l’organisation (groupe large).

Au lieu de gérer les mises à jour Office à l’aide de Configuration Manager, Contoso a activé les mises à jour automatiques à partir du cloud. Les mises à jour basées sur le cloud réduisent la surcharge administrative tout en garantissant que les appareils restent à jour.

Contoso a suivi la même approche en deux étapes pour les mises à jour de fonctionnalités que pour le déploiement des Office : les appareils du groupe pilote ont reçu les mises à jour des fonctionnalités quatre mois plus tôt que les appareils dans le reste de l’organisation (groupe large). Pour activer cette option pour Office, Contoso a utilisé deux [canaux de mise à jour](/DeployOffice/overview-update-channels) recommandés :

- Canal d’entreprise semi-annuel (préversion) pour les mises à jour du groupe pilote
- Semi-Annual Enterprise canal pour les mises à jour du groupe étendu

Étant donné que le canal d’entreprise semi-annuel (préversion) a publié une version des applications Microsoft 365 pour les grandes entreprises quatre mois plus tôt que le canal d’entreprise semi-annuel, Contoso a le temps de valider les mises à jour sans avoir à les gérer.

## <a name="deployment-process"></a>Processus de déploiement

Pour effectuer le déploiement d’Office, Contoso a implémenté le processus suivant, qui inclut les recommandations concernant les meilleures pratiques de Microsoft suivantes :

1. Avant le déploiement, Contoso a utilisé le Shared Computer Toolkit de préparation pour les Office et VBA pour tester leurs applications et leurs Office pour évaluer leur compatibilité avec les Applications Microsoft 365 pour les grandes entreprises.
1. Dans Configuration Manager, ils ont activé le cache d’homologues sur leurs appareils clients, ce qui permet de limiter la capacité du réseau lors du déploiement sur les appareils clients dans des emplacements distants. 
1. Contoso a défini deux groupes de déploiement en tant que collections d’appareils dans Configuration Manager : un groupe pilote et un groupe large. Le groupe pilote, qui comprenait un petit ensemble d’appareils représentatifs au sein de l’organisation, a été utilisé pour des tests supplémentaires d’applications, de compléments et de matériel avec Windows 10 Entreprise et Applications Microsoft 365 pour les grandes entreprises.
1. Ils ont créé des packages de déploiement pour Office à l’aide du tableau de bord de gestion des clients Office et de l’Assistant Office 365 Installer, qui font tous deux partie de la console Configuration Manager. Ils ont créé deux packages Applications Microsoft 365 pour les grandes entreprises, un pour le groupe pilote sur le canal Semi-Annual Enterprise (prévisualisation) et un pour le groupe large sur le canal Semi-Annual Enterprise.
2. Chaque Office inclut des packs linguistiques anglais, français et allemand. Si un appareil nécessitait une langue qui n’était pas incluse dans le package Office, ce pack de langue était automatiquement téléchargé à partir du Office réseau de distribution de contenu (CDN).
3. La société a utilisé la fonctionnalité intégrée dans le package Office afin de supprimer automatiquement toutes les versions MSI d’Office existantes avant d’installer Microsoft 365 Apps for enterprise.
4. Dans Configuration Manager, ils ont déployé les packages Windows et Office vers des points de distribution sur leur réseau. Ils ont ensuite déployé les séquences de tâches de déploiement configuration Manager pour déployer le package Applications Microsoft 365 pour les grandes entreprises pilote dans le groupe pilote.
5. Après avoir résolu les problèmes de compatibilité avec le groupe pilote, Contoso a mis en place les séquences de tâches pour déployer le package Applications Microsoft 365 pour les grandes entreprises au groupe étendu.

Étant donné que Contoso a choisi de mettre à jour automatiquement les appareils à partir du cloud, il n’était pas nécessaire de gérer le processus dans le Gestionnaire de Configuration. Leurs appareils sont automatiquement mis à jour directement à partir du cloud en fonction du canal de mise à jour défini dans le déploiement initial.

Voici l’architecture de déploiement de l Applications Microsoft 365 pour les grandes entreprises des mises à jour en cours de Contoso.

![Infrastructure de déploiement Contoso pour Applications Microsoft 365 pour les grandes entreprises](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso utilise Microsoft Intune [dans](contoso-mdm.md) Microsoft 365 entreprise pour gérer ses appareils et les applications qu’ils exécutent au sein de l’organisation.

## <a name="see-also"></a>Voir aussi

[Applications Microsoft 365 pour les entreprises](/deployoffice/deployment-guide-microsoft-365-apps)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)