---
title: 'Phase de déploiement des règles asr 1 : planifier'
description: Fournit des conseils pour planifier le déploiement de vos règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.reviewer: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: ca6c7ed6265a1c68a513d6025227780fa429f6e8
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2021
ms.locfileid: "61217397"
---
# <a name="attack-surface-reduction-rules-deployment-phase-1-plan"></a>Phase 1 de déploiement des règles de réduction de la surface d’attaque : planifier

Commencer à tester les règles de la asr. implique de commencer avec la bonne unité commerciale. Vous souhaiterez commencer par un petit groupe de personnes dans une unité commerciale spécifique. Vous pouvez identifier certains champions de la RSA au sein d’une unité commerciale particulière qui peuvent fournir un impact réel sur les règles de la asr et vous aider à régler votre implémentation.

> [!div class="mx-imgBorder"]
> ![Étapes de planification des règles asr](images/asr-rules-planning-steps.png)

## <a name="start-with-the-right-business-unit"></a>Commencer avec la bonne unité commerciale

La façon dont vous sélectionnez l’unité d’entreprise pour déployer votre déploiement de règles de asr dépend de facteurs tels que :

- Taille de l’unité commerciale
- Disponibilité des champions de règles de la asr.  
- Distribution et utilisation des :
  - Logiciels
  - Dossiers partagés
  - Utilisation de scripts
  - Office macros
  - Autres entités affectées par les règles de la asr.

En fonction des besoins de votre entreprise, vous pouvez décider d’inclure plusieurs unités d’entreprise pour obtenir un large échantillonnage de logiciels, dossiers partagés, scripts, macros, etc. À l’inverse, vous pouvez décider de limiter l’étendue de votre premier déploiement de règles asr à une seule unité commerciale, puis de répéter l’ensemble du processus de déploiement des règles de la asr dans vos autres unités d’entreprise, une par une.

## <a name="identify-asr--rules-champions"></a>Identifier les champions de règles de la asr.

Les champions des règles de RSA sont des membres de votre organisation qui vous aideront lors du déploiement initial des règles de la asr lors des phases préliminaires de test et d’implémentation. Vos champions sont généralement des employés qui sont plus techniquesment adap et qui ne sont pas déraillés par des pannes intermittentes de flux de travail. L’implication des champions se poursuit tout au long du développement plus large du déploiement des règles de la asr dans votre organisation. Vos champions de règles asr seront les premiers à découvrir chaque niveau du déploiement des règles de la asr.

Il est important de fournir un canal de commentaires et de réponse à vos champions de règles de asr pour vous avertir des interruptions de travail liées aux règles de la asr et recevoir les communications liées au déploiement des règles de la asr.

## <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Obtenir l’inventaire des applications métier et comprendre les processus de l’unité métier

Il est essentiel de bien comprendre les applications et les processus par unité d’entreprise utilisés au sein de votre organisation pour réussir le déploiement des règles de la asr. En outre, il est impératif que vous compreniez la façon dont ces applications sont utilisées dans les différentes unités commerciales de votre organisation.
Pour commencer, vous devez obtenir un inventaire des applications approuvées pour être utilisées dans l’ensemble de l’organisation. Vous pouvez utiliser des outils tels que Microsoft 365 Apps centre d’administration pour vous aider à inventorier les applications logicielles. Voir : [Vue d’ensemble de l’inventaire dans Microsoft 365 Apps centre d’administration.](/deployoffice/admincenter/inventory)

## <a name="define-reporting-and-response-team--roles-and-responsibilities"></a>Définir les rôles et responsabilités de l’équipe de signalement et de réponse

Clairement l’articul des rôles et des responsabilités des personnes responsables de la surveillance et de la communication de l’état et de l’activité des règles de la asr. Par conséquent, il est important de déterminer :

- La personne ou l’équipe responsable de la collecte des rapports
- Comment et avec qui les rapports sont partagés
- Comment l’escalade est traitée pour les menaces nouvellement identifiées ou les blocages indésirables causés par les règles de la astéreur

Les rôles et responsabilités classiques sont les suivants :

- Administrateurs informatiques : implémentez des règles de asr, gérez les exclusions. Travailler avec différentes unités d’entreprise sur des applications et des processus. Assemblage et partage de rapports aux parties prenantes
- Analyste certifié du Centre d’opérations de sécurité (CSOC) : responsable de l’investissement de processus bloqués à priorité élevée, afin de déterminer si la menace est valide ou non
- Responsable de la sécurité des informations (CISO) : responsable de la sécurité globale et de l’état de santé de l’organisation

## <a name="ring-deployment"></a>Déploiement sonnerie

Pour les grandes entreprises, Microsoft recommande de déployer des règles asr dans des « anneaux ». Les anneaux sont des groupes d’appareils qui sont visuellement représentés sous forme de cercles concentriques qui s’imbriquent vers l’extérieur comme des anneaux d’arborescence qui ne se chevauchent pas. Lorsque l’anneau le plus au centre est correctement déployé, vous pouvez passer l’anneau suivant à la phase de test. Une évaluation approfondie de vos unités d’entreprise, de vos règles de RSA, de vos applications et de vos processus est impérative pour définir vos anneaux.
Dans la plupart des cas, votre organisation a conçu des anneaux de déploiement pour des déploiements par phases Windows mises à jour. Vous pouvez utiliser votre conception d’anneau existante pour implémenter des règles asr.
Voir : [Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiements

[Guide de déploiement des règles asr : vue d’ensemble](attack-surface-reduction-rules-deployment.md)

[Phase de déploiement des règles asr 2 : test](attack-surface-reduction-rules-deployment-phase-2.md)

[Phase 3 de déploiement des règles asr : implémenter](attack-surface-reduction-rules-deployment-phase-3.md)

[Phase de déploiement des règles asr 4 : opérationnel](attack-surface-reduction-rules-deployment-phase-4.md)
