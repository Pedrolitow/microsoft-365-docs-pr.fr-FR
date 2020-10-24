---
title: Déploiement de Microsoft 365 Apps for enterprise pour Consoto.
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
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
ms.openlocfilehash: 2c02c28ddba7c24592ce09d87bf6f5c9df700a2a
ms.sourcegitcommit: 66b8fc1d8ba4f17487cd2004ac19cf2fff472f3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48754347"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Déploiement de Microsoft 365 Apps for enterprise pour Consoto.

Contoso a mis à niveau ses PC vers les applications Windows 10 entreprise et Microsoft 365 pour entreprise afin de garantir une collaboration plus efficace, une meilleure sécurité et une expérience de bureau plus moderne. Une fois qu’ils ont évalué leurs besoins en matière d’infrastructure et d’entreprise, Contoso a identifié ces exigences clés pour le déploiement :

- Tous les PC doivent exécuter les applications Microsoft 365 pour entreprises.
- Le déploiement doit utiliser les outils de gestion et l’infrastructure existants lorsque cela est possible.
- Le déploiement doit prendre en charge plusieurs langues et architectures existantes sur les appareils des utilisateurs.
- Les PC doivent rester à jour et sécurisés avec des coûts d’administration informatique minimes et un impact minimal sur les utilisateurs.

## <a name="deployment-tools"></a>Outils de déploiement

En fonction de leurs besoins, Contoso a choisi de déployer les applications Windows 10 entreprise et Microsoft 365 pour Enterprise via le gestionnaire de configuration (branche actuelle). Configuration Manager évolue pour les environnements de grande taille et permet un contrôle étendu de l’installation, des mises à jour et des paramètres. Elle comporte également des fonctionnalités intégrées pour faciliter et optimiser le déploiement et la gestion d’Office, notamment :

- Le cache d’homologue, qui peut vous aider à limiter la capacité du réseau lors du déploiement sur des appareils distants.
- Le tableau de bord de gestion des clients Office, qui facilite le déploiement d’Office et la surveillance des mises à jour, et permet aux administrateurs d’accéder aux dernières fonctionnalités de déploiement et de gestion.
- Le déploiement de module linguistique intelligent, y compris le déploiement automatique de la même langue que le système d’exploitation.
- Méthode entièrement prise en charge et facile à utiliser pour supprimer des versions existantes d’Office d’un client lors du déploiement.

En plus du gestionnaire de configuration, Contoso a utilisé la [boîte à outils de préparation pour les compléments Office et VBA](https://docs.microsoft.com/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps), un outil gratuit de Microsoft pour évaluer les problèmes de compatibilité avec leurs macros et compléments Office.

## <a name="managing-deployment-and-updates"></a>Gestion du déploiement et des mises à jour

Les applications Microsoft 365 pour les entreprises ont un nouveau modèle de version : Office as a service. Le modèle de service facilite la mise à jour avec les nouvelles fonctionnalités. Toutefois, il est souvent nécessaire que les services informatiques modifient la manière dont ils déploient et testent de nouvelles versions. Pour minimiser les problèmes de compatibilité et garantir que leurs ordinateurs restent à jour, Contoso a déployé Windows et Office en deux étapes :

- Tout d’abord, ils ont déployé des applications Microsoft 365 pour entreprise sur un petit ensemble d’appareils représentatifs au sein de l’organisation. Ce groupe pilote a été utilisé pour tester des applications, des compléments et du matériel avec les applications Microsoft 365 pour Enterprise.
- Quatre mois plus tard, après avoir résolu tous les problèmes essentiels rencontrés avec les applications, les compléments et le matériel dans le groupe pilote, Contoso a déployé Microsoft 365 Apps for enterprise sur le reste des périphériques de l’organisation (groupe large).

Au lieu de gérer les mises à jour d’Office à l’aide du gestionnaire de configuration, Contoso a activé les mises à jour automatiques à partir du Cloud. Les mises à jour en nuage réduisent la charge administrative tout en s’assurant que les appareils restent à jour.

Contoso a suivi la même approche en deux étapes pour les mises à jour de fonctionnalité qu’elles ont utilisé pour le déploiement d’Office : les appareils dans le groupe pilote reçoivent des mises à jour de fonctionnalité quatre mois plus tôt que les appareils dans le reste de l’organisation (groupe étendu). Pour activer cette option pour Office, Contoso a utilisé deux [canaux de mise à jour](https://docs.microsoft.com/DeployOffice/overview-update-channels) recommandés :

- Canal d’entreprise semi-annuel (préversion) pour les mises à jour du groupe pilote
- Semi-Annual Enterprise Channel pour les mises à jour du groupe large

Étant donné que le canal d’entreprise semi-annuel (préversion) a publié une version des applications Microsoft 365 pour les grandes entreprises quatre mois plus tôt que le canal d’entreprise semi-annuel, Contoso a le temps de valider les mises à jour sans avoir à les gérer.

## <a name="deployment-process"></a>Processus de déploiement

Pour effectuer le déploiement d’Office, Contoso a implémenté le processus suivant, qui inclut les recommandations concernant les meilleures pratiques de Microsoft suivantes :

1. Avant le déploiement, Contoso a utilisé la boîte à outils de préparation pour le complément Office et VBA pour tester ses applications et compléments Office afin d’évaluer sa compatibilité avec les applications Microsoft 365 pour les entreprises.
1. Dans le gestionnaire de configuration, ils ont activé le cache d’homologue sur leurs appareils clients, ce qui permet une capacité réseau limitée lors du déploiement vers des appareils clients situés dans des emplacements distants. 
1. Contoso a défini deux groupes de déploiement en tant que collections d’appareils dans le gestionnaire de configuration : un groupe pilote et un grand groupe. Le groupe pilote, qui comprenait un petit ensemble d’appareils représentatifs au sein de l’organisation, a été utilisé pour tester les applications, les compléments et le matériel avec les applications Windows 10 entreprise et Microsoft 365 pour les entreprises.
1. Ils ont créé des packages de déploiement pour Office à l’aide du tableau de bord de gestion des clients Office et de l’Assistant Installation d’Office 365, qui font partie de la console Configuration Manager. Ils ont créé deux applications Microsoft 365 pour les packages d’entreprise, un pour le groupe pilote sur le Semi-Annual Enterprise Channel (Preview) et un pour le groupe large de la Semi-Annual Channel Enterprise.
2. Chaque package Office comprenait des modules linguistiques Anglais, français et allemands. Si un périphérique exigeait une langue qui n’était pas incluse dans le package Office, ce module linguistique a été automatiquement téléchargé à partir du réseau de distribution de contenu (CDN) Office.
3. La société a utilisé la fonctionnalité intégrée dans le package Office afin de supprimer automatiquement toutes les versions MSI d’Office existantes avant d’installer Microsoft 365 Apps for enterprise.
4. Dans le gestionnaire de configuration, les packages Windows et Office sont déployés sur les points de distribution sur leur réseau. Ils ont ensuite exécuté les séquences de tâches de déploiement du gestionnaire de configuration pour déployer le package d’applications Microsoft 365 applications pour Enterprise dans le groupe pilote.
5. Une fois qu’ils ont résolu les problèmes de compatibilité avec le groupe pilote, Contoso a exécuté les séquences de tâches pour déployer le package Microsoft 365 Apps for Enterprise dans le groupe large.

Étant donné que Contoso a choisi de mettre à jour automatiquement les appareils à partir du cloud, il n’était pas nécessaire de gérer le processus dans le Gestionnaire de Configuration. Leurs appareils sont automatiquement mis à jour directement à partir du nuage sur le canal de mise à jour qui a été défini dans le déploiement initial.

Voici les applications contoso Microsoft 365 pour l’installation et l’architecture de déploiement des mises à jour continues.

![Infrastructure de déploiement contoso pour les applications Microsoft 365 pour les entreprises](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Étape suivante

Découvrez comment Contoso [utilise Microsoft Intune](contoso-mdm.md) dans Microsoft 365 pour entreprise pour gérer ses appareils et les applications qu’ils exécutent dans l’organisation.

## <a name="see-also"></a>Voir aussi

[Applications Microsoft 365 pour les entreprises](https://docs.microsoft.com/deployoffice/deployment-guide-microsoft-365-apps)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
