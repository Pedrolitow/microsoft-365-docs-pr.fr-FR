---
title: Incidents dans Microsoft 365 Defender
description: Examinez les incidents rencontrés sur les appareils, les utilisateurs et les boîtes aux lettres dans le Centre de sécurité Microsoft 365.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 890e64367c49c24c8c70e2cbda9869a5d0797219
ms.sourcegitcommit: 4076b43a4b661de029f6307ddc1a989ab3108edb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "51939583"
---
# <a name="incidents-in-microsoft-365-defender"></a>Incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Un incident dans Microsoft 365 Defender est une collection d'alertes corrélées et de données associées qui constitue l'histoire d'une attaque. 

Les applications et services Microsoft 365 créent des alertes lorsqu'ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques pour différents types d'entités, telles que les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client. 

Étant donné que l'agrégation des alertes individuelles pour obtenir des informations sur une attaque peut être difficile et chronophage, Microsoft 365 Defender agrège automatiquement les alertes et leurs informations associées dans un incident.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Comment Microsoft 365 Defender met en corrélation les événements des entités avec un incident":::

Regardez cette courte présentation des incidents dans Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Le regroupement d'alertes associées dans un incident vous offre une vue complète d'une attaque. Par exemple, vous pouvez voir :

- Point de départ de l'attaque.
- Quelles tactiques ont été utilisées .
- Jusqu'où l'attaque est passée dans votre client.
- Étendue de l'attaque, telle que le nombre d'appareils, d'utilisateurs et de boîtes aux lettres qui ont été touchés. 
- Toutes les données associées à l'attaque.

[S'il est](m365d-enable.md)activé, Microsoft 365 Defender peut automatiquement examiner et résoudre les alertes par le biais de l'automatisation et de l'intelligence artificielle. Vous pouvez également effectuer des étapes de correction supplémentaires pour résoudre l'attaque. 

## <a name="incidents-and-alerts-in-the-microsoft-365-security-center"></a>Incidents et alertes dans le Centre de sécurité Microsoft 365

Vous gérez les incidents à partir **d'incidents & alertes** > Incidents dans le lancement rapide du Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le Centre de sécurité Microsoft 365":::

La sélection d'un nom d'incident affiche un résumé de l'incident et donne accès aux onglets avec des informations supplémentaires.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Exemple de page Résumé d'un incident dans le Centre de sécurité Microsoft 365":::

Les onglets supplémentaires pour un incident sont les suivants :

- Alertes 

  Toutes les alertes liées à l'incident et leurs informations.

- Appareils

  Tous les appareils identifiés comme faisant partie ou liés à l'incident.

- Utilisateurs

  Tous les utilisateurs identifiés comme faisant partie ou associés à l'incident.

- Boîtes aux lettres

  Toutes les boîtes aux lettres identifiées comme faisant partie ou liées à l'incident.

- Examens

  Toutes les enquêtes automatisées déclenchées par des alertes dans l'incident.

- Preuve et réponse

  Tous les événements pris en charge et entités suspectes dans les alertes dans l'incident.

Voici la relation entre un incident et ses données et les onglets d'un incident dans le Centre de sécurité Microsoft 365.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relation d'un incident et de ses données avec les onglets d'un incident dans le Centre de sécurité Microsoft 365":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Exemple de flux de travail de réponse aux incidents pour Microsoft 365 Defender

Voici un exemple de flux de travail pour répondre aux incidents dans Microsoft 365 avec le Centre de sécurité Microsoft 365.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Exemple de flux de travail de réponse aux incidents pour Microsoft 365":::

Identifiez régulièrement les incidents les plus prioritaires pour l'analyse et la résolution dans la file d'attente des incidents et préparez-les à répondre. Il s'agit d'une combinaison de :

- [Tri pour](incident-queue.md) déterminer les incidents les plus prioritaires via le filtrage et le tri de la file d'attente d'incidents.
- [Gestion](manage-incidents.md) des incidents en modifiant leur titre, en les attribuant à un analyste et en ajoutant des balises et des commentaires.

1. Pour chaque incident, lancez une analyse [d'attaque et d'alerte](investigate-incidents.md):

   a. Affichez le résumé de l'incident pour comprendre sa portée et sa gravité, ainsi que les entités concernées (onglet **Résumé).**

   b. Commencez à analyser les alertes pour comprendre leur origine, leur étendue et leur gravité (onglet **Alertes).**

   c. Si nécessaire, rassemblez des informations sur les appareils, les utilisateurs et les boîtes aux lettres touchés (onglets **Appareils,** Utilisateurs et Boîtes **aux lettres).**

   d. Découvrez comment Microsoft 365 Defender a résolu automatiquement certaines alertes (onglet **Enquêtes).**
   
   e. Si nécessaire, utilisez les informations du jeu de données pour l'incident pour plus d'informations (onglet Preuve **et** réponse).

2. Après ou pendant votre analyse, adressez le contenu pour réduire tout impact supplémentaire de l'attaque et l'éradication de la menace de sécurité.

3. Dans la mesure du possible, récupérez à partir de l'attaque en restaurant les ressources de votre client à l'état où elles se sont trouver avant l'incident.

4. [Résolvez](manage-incidents.md#resolve-incident) l'incident et prenez le temps d'apprendre après l'incident pour :

   - Comprendre le type de l'attaque et son impact.
   - Recherchez une tendance des attaques de sécurité dans [l'analyse](threat-analytics.md) des menaces et la communauté de sécurité.
   - Rappelez-vous du flux de travail que vous avez utilisé pour résoudre l'incident et mettre à jour vos flux de travail, processus, stratégies et playbooks standard si nécessaire.
   - Déterminez si des modifications sont nécessaires dans votre configuration de sécurité et implémentez-les.

## <a name="example-security-operations-for-microsoft-365-defender"></a>Exemples d'opérations de sécurité pour Microsoft 365 Defender

Voici un exemple d'opérations de sécurité pour Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Exemple d'opérations de sécurité pour Microsoft 365 Defender":::

Les tâches quotidiennes peuvent inclure les tâches suivantes :

- [Gestion des](manage-incidents.md) incidents
- Examen des actions [d'investigation et de réponse automatisées (AIR)](m365d-action-center.md)
- Examen de la dernière [analyse des menaces](threat-analytics.md)
- [Réponse aux](investigate-incidents.md) incidents

Les tâches mensuelles peuvent inclure les tâches suivantes :

- Examen des [paramètres AIR](m365d-configure-auto-investigation-response.md)
- Examen de [la gestion des niveaux de sécurité](microsoft-secure-score-improvement-actions.md) et & des [vulnérabilités](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Rapports à votre chaîne de gestion de la sécurité informatique

Les tâches trimestrielles peuvent inclure un rapport et un briefing des résultats de sécurité au directeur de la sécurité des informations (CISO).

Les tâches annuelles peuvent inclure la conduite d'un incident majeur ou d'un exercice de violation pour tester votre personnel, vos systèmes et vos processus. 

Les tâches quotidiennes, mensuelles, trimestrielles et annuelles peuvent être utilisées pour mettre à jour ou affiner des processus, des stratégies et des configurations de sécurité.

## <a name="next-steps"></a>Étapes suivantes

La file d'attente des incidents de la page **Incidents** répertorie les incidents les plus récents. À partir de là, vous pouvez :

- Voir quels incidents doivent [être](incident-queue.md) hiérarchisés en fonction de la gravité et d'autres facteurs. 
- [Gérer les incidents,](manage-incidents.md)ce qui inclut le changement de nom, l'affectation, la classification et l'ajout de balises et de commentaires pour votre flux de travail de gestion des incidents.
- Effectuer une [analyse](investigate-incidents.md) d'un incident.
