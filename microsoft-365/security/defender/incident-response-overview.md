---
title: Examiner et répondre à l’Microsoft 365 Defender
description: Examiner les incidents et y répondre avec les fonctionnalités de Microsoft 365 Defender.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
ms.localizationpriority: medium
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
ms.openlocfilehash: abd075ae76eefc4a86d3e99471f092b3f4f03b34
ms.sourcegitcommit: cfcdb11cc5d39c6c71a34e09c03e8859cd6708d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60724813"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Examiner et répondre à l’Microsoft 365 Defender

Voici les principales tâches d’examen et de réponse pour Microsoft 365 Defender :

- [Répondre aux incidents](#incident-response)
- [Examiner et approuver les actions de correction automatique](#automated-investigation-and-remediation)
- [Rechercher les menaces connues dans vos données](#proactive-search-for-threats-with-advanced-hunting)
- [Comprendre les dernières cyberattaques](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Obtenir de l’aide](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Réponse aux incidents

Les services et applications Microsoft 365 créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques contre différents types d’entités, comme les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client. Étant donné que le regroupement des alertes individuelles pour obtenir des insights sur une attaque peut s’avérer difficile et fastidieux, Microsoft 365 Defender agrège automatiquement les alertes et leurs informations associées dans un incident.

En continu, identifiez les incidents les plus prioritaires pour l’analyse et la résolution dans la file d’attente des incidents et préparez-les pour la réponse. Il s’agit d’une combinaison de :

- [Tri pour](incident-queue.md) déterminer les incidents les plus prioritaires via le filtrage et le tri de la file d’attente d’incidents.
- [Gestion](manage-incidents.md) des incidents en modifiant leur titre, en les attribuant à un analyste et en ajoutant des balises et des commentaires.

Pour chaque incident, utilisez votre flux de travail de réponse aux incidents pour analyser l’incident, ses alertes et ses données afin de contenir l’attaque, d’éliminer la menace, de récupérer de l’attaque et d’en tirer des informations. Consultez [cet exemple](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) pour Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

Si votre organisation utilise Microsoft 365 Defender, votre équipe des opérations de sécurité reçoit une alerte dans le portail Microsoft 365 Defender chaque fois qu’une activité ou un artefact malveillant ou suspect est détecté. Étant donné le flux sans fin des menaces qui peuvent survenir, les équipes de sécurité doivent souvent relever le défi de traiter le volume élevé d’alertes. Heureusement, Microsoft 365 Defender inclut des fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent aider votre équipe des opérations de sécurité à traiter les menaces plus efficacement.

Lorsqu’une enquête automatisée se termine, un verdict est atteint pour chaque élément de preuve d’un incident impliqué. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, des actions de correction sont prises automatiquement . dans d’autres cas, les actions de correction attendent l’approbation du centre Microsoft 365 Defender actions. 

Pour plus [d’informations,](m365d-autoir.md) voir Examen et réponse Microsoft 365 Defender automatisés.

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Recherche proactive des menaces avec le recherche avancée

Il ne suffit pas de répondre aux attaques à mesure qu’elles se produisent. Pour les attaques étendues en plusieurs phases telles que les ransomware, vous devez rechercher de manière proactive les preuves d’une attaque en cours et prendre des mesures pour l’arrêter avant qu’elle ne se termine.

Le recherche avancée est un outil de recherche de menace basé sur une requête dans Microsoft 365 Defender qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. Cet accès flexible aux données Microsoft 365 Defender permet un recherche sans contraintes pour les menaces connues et potentielles.

Vous pouvez utiliser les mêmes requêtes de repérage de menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour vérifier et répondre aux activités suspectées de violation, aux ordinateurs mal configurés et à d’autres conclusions.

Pour [plus d’informations,](advanced-hunting-overview.md) voir la recherche proactive des menaces avec le Microsoft 365 Defender avancé.

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Prendre de l’avance sur les menaces émergentes avec l’analyse des menaces

L’analyse des menaces est une fonctionnalité d’intelligence des menaces Microsoft 365 Defender conçue pour aider votre équipe de sécurité à être aussi efficace que possible face aux menaces émergentes. Il inclut une analyse détaillée et des informations sur :

- Acteurs actifs contre les menaces et leurs campagnes
- Techniques d’attaques nouvelles et populaires
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

L’analyse des menaces inclut également des informations sur les incidents connexes et les biens touchés au sein de votre client Microsoft 365 pour chaque menace identifiée.

Chaque menace identifiée inclut un rapport d’analyste, une analyse complète de la menace écrite par des chercheurs en sécurité Microsoft qui sont à la pointe de la détection et de l’analyse de la cybersécurité et peuvent fournir des informations sur la façon dont les attaques apparaissent dans Microsoft 365 Defender.

Pour plus d’informations, voir [l’analyse des menaces dans Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Collaborer avec des experts Microsoft

Spécialistes des menaces Microsoft - Les notifications d’attaques ciblées sont un service de recherche de menace gérée. Une fois que vous avez appliqué et accepté, vous recevrez des notifications d’attaque ciblée de la part d’experts microsoft en matière de menaces, afin que vous ne manquez pas les menaces critiques pour votre environnement. Ces notifications vous aideront à protéger les points de terminaison, le courrier électronique et les identités de votre organisation. Spécialistes des menaces Microsoft : les experts à la demande vous permettent d’obtenir des conseils experts sur les menaces que votre organisation fait face et vous pouvez demander de l’aide sur les menaces que votre organisation fait face. Il est disponible en tant que service d’abonnement supplémentaire.

Pour plus d’informations, [voir Spécialistes des menaces Microsoft dans Microsoft 365 vue d’ensemble.](/security/mtp/microsoft-threat-experts.md)
