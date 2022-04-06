---
title: Planifier le déploiement de règles ASR pour la réduction de la surface d’attaque
description: Fournit des conseils pour planifier le déploiement de vos règles de réduction de la surface d’attaque (ASR).
keywords: Déploiement de règles de réduction de la surface d’attaque, déploiement ASR, activer des règles asr, configurer asr, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 94c66591a99a92ebd9d710de573d32e440386573
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663135"
---
# <a name="step-1-plan-asr-rules-deployment"></a>Étape 1 : Planifier le déploiement des règles ASR

Lors du test des règles de réduction de la surface d’attaque (ASR), il est important de commencer par l’unité commerciale appropriée. Vous souhaiterez commencer par un petit groupe de personnes dans une unité commerciale spécifique. Vous pouvez identifier certains champions ASR au sein d’une unité commerciale particulière qui peuvent fournir un impact réel sur les règles ASR et vous aider à paramétrer votre implémentation.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-planning-steps.png" alt-text="Étapes de planification des règles ASR" lightbox="images/asr-rules-planning-steps.png":::

## <a name="start-with-the-right-business-unit"></a>Commencez par l’unité métier appropriée

La façon dont vous sélectionnez l’unité métier pour déployer votre déploiement de règles ASR dépend de facteurs tels que :

- Taille de l’unité commerciale
- Disponibilité des champions de règles ASR  
- Distribution et utilisation de :
  - Logiciels
  - Dossiers partagés
  - Utilisation de scripts
  - macros Office
  - Autres entités affectées par les règles ASR

En fonction des besoins de votre entreprise, vous pouvez décider d’inclure plusieurs unités commerciales pour obtenir un large échantillonnage de logiciels, dossiers partagés, scripts, macros, etc. À l’inverse, vous pouvez décider de limiter l’étendue de votre premier déploiement de règles ASR à une seule unité commerciale, puis de répéter l’intégralité du processus de déploiement des règles ASR à vos autres unités commerciales, une à la fois.

## <a name="identify-asr--rules-champions"></a>Identifier les champions de règles ASR

Les champions des règles ASR sont des membres de votre organisation qui vous aideront à déployer vos règles ASR initiales pendant les phases préliminaires de test et d’implémentation. Vos champions sont généralement des employés qui sont plus habiles techniquement et qui ne sont pas déraillés par des interruptions intermittentes de flux de travail. La participation des champions se poursuivra tout au long de l’expansion plus large du déploiement de règles ASR dans votre organisation. Vos champions de règles ASR seront les premiers à connaître chaque niveau du déploiement des règles ASR.

Il est important de fournir un canal de commentaires et de réponse pour que vos champions des règles ASR vous avertissent des interruptions de travail liées aux règles ASR et reçoivent des communications liées au déploiement des règles ASR.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Obtenir l’inventaire des applications métier et comprendre les processus de l’unité métier

Il est essentiel de bien comprendre les applications et les processus par unité métier utilisés dans votre organisation pour un déploiement réussi des règles ASR. En outre, il est impératif que vous compreniez comment ces applications sont utilisées au sein des différentes unités commerciales de votre organisation.
Pour commencer, vous devez obtenir un inventaire des applications approuvées pour une utilisation dans l’ensemble de l’organisation. Vous pouvez utiliser des outils tels que le centre d’administration Microsoft 365 Apps pour vous aider à inventorier les applications logicielles. Voir : [Vue d’ensemble de l’inventaire dans le centre d’administration Microsoft 365 Apps](/deployoffice/admincenter/inventory).

## <a name="define-reporting-and-response-team-roles-and-responsibilities"></a>Définir les rôles et responsabilités de l’équipe de création de rapports et de réponse

Il est clair que l’articulation des rôles et des responsabilités des personnes responsables de la surveillance et de la communication de l’état et de l’activité des règles ASR est une activité essentielle de la maintenance ASR. Par conséquent, il est important de déterminer :

- La personne ou l’équipe responsable de la collecte des rapports
- Comment et avec qui les rapports sont partagés
- Comment l’escalade est traitée pour les menaces nouvellement identifiées ou les blocages indésirables causés par les règles ASR

Les rôles et responsabilités classiques sont les suivants :

- Administrateurs informatiques : implémentez des règles ASR, gérez les exclusions. Travaillez avec différentes unités commerciales sur des applications et des processus. Assemblage et partage de rapports aux parties prenantes
- Analyste du Centre des opérations de sécurité certifié (CSOC) : Responsable de l’investissement de processus bloqués de priorité élevée, afin de déterminer si la menace est valide ou non
- Responsable de la sécurité des informations (CISO) : Responsable de la posture de sécurité globale et de l’intégrité de l’organisation

## <a name="ring-deployment"></a>Déploiement sonnerie

Pour les grandes entreprises, Microsoft recommande de déployer des règles ASR dans des « anneaux ». Les anneaux sont des groupes d’appareils qui sont représentés visuellement sous forme de cercles concentriques qui rayonnent vers l’extérieur comme des anneaux d’arbre qui ne se chevauchent pas. Lorsque l’anneau le plus profond est déployé avec succès, vous pouvez passer l’anneau suivant à la phase de test. Une évaluation approfondie de vos unités commerciales, des champions des règles ASR, des applications et des processus est impérative pour définir vos anneaux.
Dans la plupart des cas, votre organisation aura conçu des anneaux de déploiement pour les déploiements par phases de mises à jour Windows. Vous pouvez utiliser votre conception d’anneau existante pour implémenter des règles ASR.
Voir : [Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiement

[Prérequis pour le déploiement des règles ASR](attack-surface-reduction-rules-deployment.md)

[Étape 2 : Tester les règles ASR](attack-surface-reduction-rules-deployment-test.md)

[Étape 3 : Mettre en œuvre les règles ASR](attack-surface-reduction-rules-deployment-implement.md)

[Étape 4 : Opérationnaliser les règles ASR](attack-surface-reduction-rules-deployment-operationalize.md)
