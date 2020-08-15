---
title: Déploiement de Windows 10 Entreprise pour Contoso
author: JoeDavies-MSFT
f1.keywords:
- NOCSH
ms.author: josephd
manager: laurawi
ms.date: 10/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: Comprendre la façon dont Contoso a utilisé Microsoft Endpoint Configuration Manager pour déployer les mises à niveau sur place pour Windows 10 Entreprise.
ms.openlocfilehash: a100eb07408053fd270c26f388265696549fff9f
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46686417"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>Déploiement de Windows 10 Entreprise pour Contoso

Avant le déploiement étendu de Microsoft 365 pour Enterprise, contoso disposait de PC et de périphériques compatibles avec Windows qui exécutent un mélange de Windows 7 (10%), de Windows 8,1 (65%) et de Windows 10 (25%). Contoso souhaitait mettre à niveau ses PC pour Windows 10 entreprise tirer parti de la sécurité avancée et avoir réduit les charges de travail informatiques des déploiements automatisés de mises à jour. 

Après évaluation de ses besoins d’infrastructure et de ses besoins métier, Contoso a identifié les exigences principales suivantes en matière de déploiement :

- Le plus possible de PC et de périphériques doivent exécuter Windows 10 Entreprise
- Déploiement des mises à niveau sur place exploitant l’infrastructure Configuration Manager existante
- Contrôler les versions de Windows 10 Entreprise à déployer, et les mises à jour sont effectuées via des anneaux
- Les PC et les périphériques doivent rester à jour moyennant des coûts d’administration informatique minimes et avec un faible impact pour les utilisateurs finaux

Une version « à jour » est définie comme la version de Windows 10 Entreprise prise en charge qui répond aux besoins métier de Contoso, ce qui peut être différent d’avoir tous les PC compatibles avec Windows exécutant la dernière version de Windows 10 Entreprise.

## <a name="deployment-tools"></a>Outils de déploiement

Avant et pendant les mises à niveau sur place de Windows 10 Entreprise, Contoso a utilisé les solutions de Windows Analytics suivantes :

- Préparation des mises à niveau  

  Collecte les données du pilote, des applications et du système en vue d’une analyse, puis identifie les problèmes de compatibilité susceptibles d’empêcher une mise à niveau et les correctifs aux problèmes suggérés et connus par Microsoft.

- Conformité des mises à niveau  

  Indique l’état de vos appareils par rapport aux mises à jour Windows, afin que vous puissiez vous assurer que ceux-ci disposent des mises à jour les plus récentes, si nécessaire.

- Intégrité du périphérique  

  Identifie les appareils qui se bloquent fréquemment et qui, par conséquent, doivent être recréés ou remplacés et les pilotes de périphériques qui provoquent des blocages sur les appareils, avec des suggestions d’autres versions de ces pilotes susceptibles de réduire le nombre d’incidents. Fournit une notification de configurations incorrectes de la Protection des informations Windows qui envoient des invites à des utilisateurs finaux.
 
Contoso dispose d’une infrastructure Configuration Manager (branche actuelle) existante. Le gestionnaire de configuration s’adapte à des environnements volumineux et offre un contrôle extensif sur l’installation, les mises à jour et les paramètres. Il dispose également de fonctionnalités intégrées pour simplifier et accroître l’efficacité du déploiement et de la gestion de Windows 10 Entreprise.

## <a name="planning-process"></a>Processus de planification

Avant le déploiement, Contoso a défini les anneaux suivants :

- Trois anneaux pour la gestion intermédiaire de la validation et du déploiement 
  - Un anneau pour les versions précédentes 
  - Un anneau pour les nouvelles versions publiées
  - Un anneau pour une version précédente 
- Un anneau pour le déploiement large de Windows 10 Entreprise en fonction des données provenant des anneaux de validation

Contoso a également utilisé la solution de préparation des mises à niveau de Windows Analytics pour déterminer l’ensemble des applications installées et leur compatibilité avec Windows 10 Entreprise.

## <a name="deployment-process"></a>Processus de déploiement

Pour effectuer le déploiement de mises à niveau sur place de Windows 10 Entreprise, Contoso a implémenté le processus suivant, qui inclut les recommandations concernant les meilleures pratiques de Microsoft suivantes :

1. Activation d’un cache d’homologue pour le gestionnaire de configuration
2. Création de packages Windows personnalisés basés sur des images du centre de service de gestion des licences en volume
3. Utilisation du gestionnaire de configuration pour déployer les packages Windows aux points de distribution au sein de son réseau et des versions déployées pour les trois anneaux de gestion intermédiaire de la validation et du déploiement.
4. Exécution de l’évaluation de réussite pour les PC et les périphériques dans les trois anneaux de gestion intermédiaire de la validation et du déploiement utilisant des solutions de conformité de mise à jour et d’intégrité des périphériques de Windows Analytics.
5. En fonction des informations de Windows Analytics, Contoso a déterminé la version de Windows 10 Entreprise à déployer vers l’anneau de déploiement large.
6. Exécution des séquences de tâches du déploiement du gestionnaire de configuration pour déployer le package Windows sélectionné vers l’anneau de déploiement large.
7. Surveillance des PC et des périphériques dans l’anneau de déploiement large en utilisant des solutions de conformité de mise à jour et d’intégrité des périphériques pour résoudre les problèmes.

Voici la mise à niveau sur place et l’architecture de déploiement de mises à jour en cours de Contoso.

![Infrastructure de déploiement de Windows 10 Entreprise de Contoso](../media/contoso-win10/contoso-win10-fig1.png)

Cette infrastructure se compose des éléments suivants :

- Configuration Manager, qui :
  - obtient des images pour les packages Windows 10 Entreprise à partir du centre de gestion des licences en volume Microsoft dans The Microsoft Network ;
  - est le point d’administration central pour les packages de déploiement.
- Les points de distribution régionaux généralement situés dans les centres régionaux de Contoso.
- Les périphériques et les PC Windows dans divers emplacements qui reçoivent et installent les packages de déploiement pour la mise à niveau sur place ou les mises à jour en continu basées sur l’appartenance à un anneau.

## <a name="next-step"></a>Étape suivante

[Découvrez](contoso-o365pp.md) comment Contoso utilise son infrastructure Configuration Manager pour déployer et conserver les Applications Microsoft 365 actuelles pour les entreprises au sein de son organisation. 

## <a name="see-also"></a>Voir aussi

[Windows 10 Entreprise](https://docs.microsoft.com/windows/deployment/)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Guides de laboratoire de test](m365-enterprise-test-lab-guides.md)
