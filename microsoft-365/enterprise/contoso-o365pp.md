---
title: Déploiement de Microsoft 365 Apps for enterprise pour Consoto.
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre la façon dont Contoso utilise Microsoft Endpoint Configuration Manager pour déployer de Microsoft 365 Apps for enterprise.
ms.openlocfilehash: eca3978103ca1e590d747b3549a3c9e393f871ca
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43625253"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Déploiement de Microsoft 365 Apps for enterprise pour Consoto.

Contoso a mis à niveau ses PC vers Windows 10 Entreprise et Microsoft 365 Apps for enterprise pour accroître l’efficacité de la collaboration, améliorer la sécurité et moderniser l’expérience d’ordinateur de bureau. Après évaluation de ses besoins d’infrastructure et de ses besoins métier, Contoso a identifié les exigences principales suivantes en matière de déploiement :

- Tous les PC doivent exécuter Microsoft 365 Apps for enterprise
- Le déploiement doit utiliser l’infrastructure et les outils de gestion existants dans la mesure du possible.
- Le déploiement doit prendre en charge plusieurs langues et les architectures existantes sur les périphériques des utilisateurs finaux.
- Les PC doivent rester à jour et sécurisés moyennant des coûts d’administration informatique minimes et avec un faible impact pour les utilisateurs finaux.

## <a name="deployment-tools"></a>Outils de déploiement

Selon ses besoins, Contoso a choisi de déployer Windows 10 Entreprise et Microsoft 365 Apps for enterprise avec Configuration Manager (branche actuelle). Le gestionnaire de configuration s’adapte à des environnements volumineux et offre un contrôle extensif sur l’installation, les mises à jour et les paramètres. Il dispose également de fonctionnalités intégrées pour simplifier et accroître l’efficacité du déploiement et de la gestion d’Office, notamment :

- un cache d’homologue, pouvant aider avec la capacité limitée du réseau lors du déploiement de périphériques dans des emplacements à distance ;
- le tableau de bord de gestion des clients Office, qui facilite le déploiement Office, surveille les mises à jour et permet aux administrateurs d’accéder aux dernières fonctionnalités de déploiement et de gestion ;
- le déploiement du module linguistique intelligent, dont le déploiement automatique de la même langue que celle du système d’exploitation ;
- la méthode facile d’utilisation et entièrement prise en charge de suppression des versions existantes d’Office à partir d’un client pendant le déploiement.

En plus du gestionnaire de configuration, Contoso a utilisé le [Kit de ressources de préparation](https://docs.microsoft.com/deployoffice/use-the-readiness-toolkit-to-assess-application-compatibility-for-office-365-pro), un outil gratuit de Microsoft permettant d’évaluer les problèmes de compatibilité avec ses compléments et macros Office.

## <a name="managing-the-deployment-and-updates"></a>Gestion du déploiement et des mises à jour

Microsoft 365 Apps for enterprise possède un nouveau modèle de publication : Office as a service. Le modèle de service permet de rester à jour plus facilement avec les nouvelles fonctionnalités, mais nécessite souvent un changement d’approche dans la façon que les services informatiques ont de déployer et de tester les nouvelles versions. Pour minimiser les problèmes de compatibilité et pour s’assurer que ses ordinateurs restent à jour, Contoso a déployé Windows et Office en deux étapes : 

- Pendant la première étape, ils ont déployé Microsoft 365 Apps for enterprise sur un petit groupe de périphériques représentatifs au sein de l’organisation. Ce groupe pilote a été utilisé pour tester des applications, des compléments et du matériel avec les Applications Microsoft 365 pour les entreprises.
- Quatre mois plus tard, après avoir résolu tous les problèmes essentiels rencontrés avec les applications, les compléments et le matériel dans le groupe pilote, Contoso a déployé Microsoft 365 Apps for enterprise sur le reste des périphériques de l’organisation (groupe large). 

Au lieu de gérer les mises à jour Office avec le gestionnaire de configuration, Contoso a activé les mises à jour automatiques à partir du cloud. Les mises à jour sur le cloud ont permis de réduire les frais généraux d’administration, et de vérifier la mise à jour des périphériques. 

Contoso a suivi la même approche en deux étapes pour la fonctionnalité de mises à jour updates+ que la société a utilisée pour le déploiement d’Office : les périphériques du groupe pilote ont reçu les mises à jour des fonctionnalités quatre mois avant les périphériques du reste de l’organisation (groupe large). Pour activer cette option pour Office, Contoso a utilisé deux [canaux de mise à jour](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) recommandés : 

- Canal semi-annuel (ciblé) pour les mises à jour au groupe pilote 
- Canal semi-annuel pour les mises à jour au groupe pilote 

Étant donné que le canal semi-annuel (ciblé) a publié une version de Microsoft 365 Apps for enterprise quatre mois plus tôt que le canal semi-annuel, Contoso a le temps de valider les mises à jour sans avoir à les gérer. 

## <a name="deployment-process"></a>Processus de déploiement

Pour effectuer le déploiement d’Office, Contoso a implémenté le processus suivant, qui inclut les recommandations concernant les meilleures pratiques de Microsoft suivantes :

1. Avant d’effectuer le déploiement, ils ont utilisé le kit de ressources de préparation pour tester ses applications et compléments Office afin d’en évaluer la compatibilité avec Microsoft 365 Apps for enterprise.
2. Dans le gestionnaire de configuration, Contoso a activé un cache d’homologue sur ses périphériques clients qui a aidé avec la capacité réseau limitée lors du déploiement aux périphériques clients dans les emplacements à distance. 
3. La société a défini deux groupes de déploiements comme collections de périphériques dans le gestionnaire de configuration : un groupe pilote et un groupe large. Le groupe pilote, qui inclut un petit groupe d’appareils représentatifs au sein de l’organisation, a été utilisé pour effectuer des tests supplémentaires sur les applications, les compléments et le matériel avec Windows 10 Entreprise et Microsoft 365 Apps for enterprise. 
4. Elle a créé des packages de déploiement pour Office à l’aide du tableau de bord de gestion des clients Office et de l’Assistant du programme d’installation d’Office 365, faisant tous les deux partie de la console du gestionnaire de configuration. Elle a créé deux packages Microsoft 365 Apps for enterprise, un pour le groupe pilote sur le canal semi-annuel (ciblé) et un pour le groupe large sur le canal semi-annuel. 
5. Dans le cadre de chaque package Office, les modules linguistiques anglais, français et allemand ont été inclus. Si un périphérique nécessitait une langue non incluse dans le package Office, celle-ci était automatiquement téléchargée à partir du réseau de distribution de contenu (CDN) Office.
6. La société a utilisé la fonctionnalité intégrée dans le package Office afin de supprimer automatiquement toutes les versions MSI d’Office existantes avant d’installer Microsoft 365 Apps for enterprise.
7. Dans le gestionnaire de configuration, Contoso a déployé les packages Windows et Office aux points de distribution au sein de son réseau, et a exécuté les séquences de tâches de déploiement du gestionnaire de configuration pour déployer le package Microsoft 365 Apps for enterprise pilote pour le groupe pilote.
8. Après avoir résolu tous les problèmes de compatibilité avec le groupe pilote, Contoso a exécuté les séquences de tâches pour déployer le package Microsoft 365 Apps for enterprise large au groupe large.

Étant donné que Contoso a choisi de mettre à jour automatiquement les appareils à partir du cloud, il n’était pas nécessaire de gérer le processus dans le Gestionnaire de Configuration. Leurs appareils sont mis à jour automatiquement directement à partir du cloud en fonction du canal de mise à jour qui a été défini dans le cadre du déploiement initial. 

Voici l’installation Microsoft 365 Apps for enterprise et l’architecture de déploiement de mises à jour en cours de Contoso.

![Infrastructure de déploiement de Microsoft 365 Apps for enterprise pour Consoto.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>Étape suivante

[En savoir plus](contoso-mdm.md) sur la façon dont Contoso utilise Microsoft Intune dans Microsoft 365 Entreprise pour gérer ses appareils et les applications qui y sont exécutées au sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 Apps for enterprise pour Microsoft 365 Entreprise](office365proplus-infrastructure.md)

[Guide de déploiement](deploy-microsoft-365-enterprise.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
