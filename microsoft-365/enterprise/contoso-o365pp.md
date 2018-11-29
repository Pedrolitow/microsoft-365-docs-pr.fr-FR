---
title: Déploiement d’Office 365 ProPlus pour Contoso
author: JoeDavies-MSFT
ms.author: josephd
manager: laurawi
ms.date: 09/13/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre la façon dont Contoso utilise System Center Configuration Manager pour déployer Office 365 ProPlus.
ms.openlocfilehash: 5b98f72561d7a431a4ca4a0b0241c6105c87026f
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26866984"
---
# <a name="office-365-proplus-deployment-for-contoso"></a>Déploiement d’Office 365 ProPlus pour Contoso

**Résumé :** Comprendre la façon dont Contoso utilise System Center Configuration Manager pour déployer Office 365 ProPlus.

Contoso a mis à niveau ses PC vers Windows 10 Entreprise et Office 365 ProPlus pour accroître l’efficacité de la collaboration, améliorer la sécurité et moderniser l’expérience d’ordinateur de bureau. Après évaluation de ses besoins d’infrastructure et de ses besoins métier, Contoso a identifié les exigences principales suivantes en matière de déploiement :

- Tous les PC doivent exécuter Office 365 ProPlus.
- Le déploiement doit utiliser l’infrastructure et les outils de gestion existants dans la mesure du possible.
- Le déploiement doit prendre en charge plusieurs langues et les architectures existantes sur les périphériques des utilisateurs finaux.
- Les PC doivent rester à jour et sécurisés moyennant des coûts d’administration informatique minimes et avec un faible impact pour les utilisateurs finaux.

## <a name="deployment-tools"></a>Outils de déploiement

Selon ses besoins, Contoso a choisi de déployer Windows et Office avec System Center Configuration Manager (branche actuelle). Le gestionnaire de configuration s’adapte à des environnements volumineux et offre un contrôle extensif sur l’installation, les mises à jour et les paramètres. Il dispose également de fonctionnalités intégrées pour simplifier et accroître l’efficacité du déploiement et de la gestion d’Office, notamment :

- un cache d’homologue, pouvant aider avec la capacité limitée du réseau lors du déploiement de périphériques dans des emplacements à distance ;
- le tableau de bord de gestion des clients Office, qui facilite le déploiement Office, surveille les mises à jour et permet aux administrateurs d’accéder aux dernières fonctionnalités de déploiement et de gestion ;
- le déploiement du module linguistique intelligent, dont le déploiement automatique de la même langue que celle du système d’exploitation ;
- la méthode facile d’utilisation et entièrement prise en charge de suppression des versions existantes d’Office à partir d’un client pendant le déploiement.

En plus du gestionnaire de configuration, Contoso a utilisé le [Kit de ressources de préparation](https://docs.microsoft.com/deployoffice/use-the-readiness-toolkit-to-assess-application-compatibility-for-office-365-pro), un outil gratuit de Microsoft permettant d’évaluer les problèmes de compatibilité avec ses compléments et macros Office.

## <a name="managing-the-deployment-and-updates"></a>Gestion du déploiement et des mises à jour

Office 365 ProPlus possède un nouveau modèle de publication : Office as a service. Le modèle de service permet de rester à jour plus facilement avec les nouvelles fonctionnalités, mais nécessite souvent un changement d’approche dans la façon que les services informatiques ont de déployer et de tester les nouvelles versions. Pour minimiser les problèmes de compatibilité et pour s’assurer que ses ordinateurs restent à jour, Contoso a déployé Windows et Office en deux étapes : 

- Pendant la première étape, ils ont déployé Office 365 ProPlus sur un petit groupe de périphériques représentatifs au sein de l’organisation. Ce groupe pilote a été utilisé pour tester des applications, des compléments et du matériel avec Office 365 ProPlus.
- Quatre mois plus tard, après avoir résolu tous les problèmes essentiels rencontrés avec les applications, les compléments et le matériel dans le groupe pilote, Contoso a déployé Office 365 ProPlus sur le reste des périphériques de l’organisation (groupe large). 

Au lieu de gérer les mises à jour Office avec le gestionnaire de configuration, Contoso a activé les mises à jour automatiques à partir du cloud. Les mises à jour sur le cloud ont permis de réduire les frais généraux d’administration, et de vérifier la mise à jour des périphériques. 

Contoso a suivi la même approche en deux étapes pour la fonctionnalité de mises à jour updates+ que la société a utilisée pour le déploiement d’Office : les périphériques du groupe pilote ont reçu les mises à jour des fonctionnalités quatre mois avant les périphériques du reste de l’organisation (groupe large). Pour activer cette option pour Office, Contoso a utilisé deux [canaux de mise à jour](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus) recommandés : 

- Canal semi-annuel (ciblé) pour les mises à jour au groupe pilote 
- Canal semi-annuel pour les mises à jour au groupe pilote 

Étant donné que le canal semi-annuel (ciblé) a publié une version d’Office 365 ProPlus quatre mois plus tôt que le canal semi-annuel, Contoso a le temps de valider les mises à jour sans avoir à les gérer. 

## <a name="deployment-process"></a>Processus de déploiement

Pour effectuer le déploiement d’Office, Contoso a implémenté le processus suivant, qui inclut les recommandations concernant les meilleures pratiques de Microsoft suivantes :

1. Avant d’effectuer le déploiement, ils ont utilisé le kit de ressources de préparation pour tester ses applications et compléments Office afin d’en évaluer la compatibilité avec Office 365 ProPlus.
2. Dans le gestionnaire de configuration, Contoso a activé un cache d’homologue sur ses périphériques clients qui a aidé avec la capacité réseau limitée lors du déploiement aux périphériques clients dans les emplacements à distance. 
3. La société a défini deux groupes de déploiements comme collections de périphériques dans le gestionnaire de configuration : un groupe pilote et un groupe large. Le groupe pilote, qui inclut un petit groupe d’appareils représentatifs au sein de l’organisation, a été utilisé pour effectuer des tests supplémentaires sur les applications, les compléments et le matériel avec Windows 10 Entreprise et Office 365 ProPlus. 
4. Elle a créé des packages de déploiement pour Office à l’aide du tableau de bord de gestion des clients Office et de l’Assistant du programme d’installation d’Office 365, faisant tous les deux partie de la console du gestionnaire de configuration. Elle a créé deux packages Office 365 ProPlus, un pour le groupe pilote sur le canal semi-annuel (ciblé) et un pour le groupe large sur le canal semi-annuel. 
5. Dans le cadre de chaque package Office, les modules linguistiques anglais, français et allemand ont été inclus. Si un périphérique nécessitait une langue non incluse dans le package Office, celle-ci était automatiquement téléchargée à partir du réseau de distribution de contenu (CDN) Office.
6. La société a utilisé la fonctionnalité intégrée dans le package Office afin de supprimer automatiquement toutes les versions MSI d’Office existantes avant d’installer Office 365 ProPlus.
7. Dans le gestionnaire de configuration, Contoso a déployé les packages Windows et Office aux points de distribution au sein de son réseau, et a exécuté les séquences de tâches de déploiement du gestionnaire de configuration pour déployer le package Office 365 ProPlus pilote pour le groupe pilote.
8. Après avoir résolu tous les problèmes de compatibilité avec le groupe pilote, Contoso a exécuté les séquences de tâches pour déployer le package Office 365 ProPlus large au groupe large.

Étant donné que Contoso a choisi de mettre à jour les périphériques à partir du cloud, il n’était pas nécessaire de gérer le processus dans le gestionnaire de configuration. Ses périphériques sont automatiquement mis à jour directement à partir du cloud en fonction du canal de mise à jour défini dans le cadre du déploiement initial. 

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-mdm.md) comment Contoso utilise Enterprise Mobility + Security (EMS) dans Microsoft 365 Entreprise pour gérer ses appareils et les applications qui y sont exécutées au sein de son organisation.

## <a name="see-also"></a>Voir aussi

[Office 365 ProPlus pour Microsoft 365 Entreprise](office365proplus-infrastructure.md)

[Guide de déploiement](deploy-microsoft-365-enterprise.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
