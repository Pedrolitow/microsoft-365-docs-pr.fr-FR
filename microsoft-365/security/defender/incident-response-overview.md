---
title: Examiner et répondre avec Microsoft 365 Defender
description: Examinez et répondez aux incidents avec les fonctionnalités de Microsoft 365 Defender.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier1
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 655858dab8b590909073f42c54148f7d0cbe4f06
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503509"
---
# <a name="investigate-and-respond-with-microsoft-365-defender"></a>Examiner et répondre avec Microsoft 365 Defender

Voici les principales tâches d’examen et de réponse pour Microsoft 365 Defender :

- [Répondre aux incidents](#incident-response)
- [Examiner et approuver les actions de correction automatique](#automated-investigation-and-remediation)
- [Rechercher des menaces connues dans vos données](#proactive-search-for-threats-with-advanced-hunting)
- [Comprendre les dernières cyberattaques](#get-ahead-of-emerging-threats-with-threat-analytics)
- [Obtenir de l’aide](#collaborate-with-microsoft-experts)

## <a name="incident-response"></a>Réponse aux incidents

Les services et applications Microsoft 365 créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques contre différents types d’entités, comme les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client. Étant donné que le regroupement des alertes individuelles pour obtenir des insights sur une attaque peut s’avérer difficile et fastidieux, Microsoft 365 Defender agrège automatiquement les alertes et leurs informations associées dans un incident.

En permanence, vous devez identifier les incidents les plus prioritaires pour l’analyse et la résolution dans la file d’attente d’incidents et les préparer pour la réponse. Il s’agit d’une combinaison de :

- [Hiérarchisation de](incident-queue.md) la détermination des incidents les plus prioritaires via le filtrage et le tri de la file d’attente d’incidents. C’est aussi ce que l’on appelle le tri.
- [Gestion](manage-incidents.md) des incidents en modifiant leur titre, en les affectant à un analyste, en ajoutant des balises et des commentaires, et une fois résolus, en les classifiant.

Pour chaque incident, utilisez votre flux de travail de réponse aux incidents pour analyser l’incident et ses alertes et ses données afin de contenir l’attaque, éliminer la menace, récupérer de l’attaque et en tirer des enseignements. Consultez [cet exemple](incidents-overview.md#example-incident-response-workflow-for-microsoft-365-defender) pour Microsoft 365 Defender.

## <a name="automated-investigation-and-remediation"></a>Investigation et résolution automatiques

Si votre organisation utilise Microsoft 365 Defender, votre équipe chargée des opérations de sécurité reçoit une alerte dans le portail Microsoft 365 Defender chaque fois qu’une activité ou un artefact malveillant ou suspect est détecté. Étant donné le flux sans fin de menaces qui peuvent entrer, les équipes de sécurité sont souvent confrontées au défi de résoudre le volume élevé d’alertes. Heureusement, Microsoft 365 Defender inclut des fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent aider votre équipe chargée des opérations de sécurité à traiter les menaces plus efficacement et plus efficacement.

Une fois l’enquête automatisée terminée, un verdict est rendu pour chaque élément de preuve d’un incident. Selon le verdict, les actions de correction sont identifiées. Dans certains cas, les actions de correction sont effectuées automatiquement ; dans d’autres cas, les actions de correction attendent l’approbation par le biais du centre d’action Microsoft 365 Defender. 

Pour plus d’informations, consultez [Examen automatisé et réponse dans Microsoft 365 Defender](m365d-autoir.md).

## <a name="proactive-search-for-threats-with-advanced-hunting"></a>Recherche proactive des menaces avec repérage avancé

Il ne suffit pas de répondre aux attaques au fur et à mesure qu’elles se produisent. Pour les attaques étendues à plusieurs phases telles que les ransomware, vous devez rechercher de manière proactive les preuves d’une attaque en cours et prendre des mesures pour l’arrêter avant qu’elle ne se termine.

La chasse avancée est un outil de chasse aux menaces basé sur une requête dans Microsoft 365 Defender qui vous permet d’explorer jusqu’à 30 jours de données brutes. Vous pouvez inspecter de manière proactive les événements de votre réseau pour localiser les indicateurs et entités de menace. Cet accès flexible aux données Microsoft 365 Defender permet de rechercher sans contrainte les menaces connues et potentielles.

Vous pouvez utiliser les mêmes requêtes de chasse aux menaces pour créer des règles de détection personnalisées. Ces règles s’exécutent automatiquement pour rechercher et répondre aux activités suspectes de violation, aux machines mal configurées et à d’autres résultats.

Pour plus [d’informations, consultez la recherche proactive des menaces avec une chasse avancée dans Microsoft 365 Defender](advanced-hunting-overview.md).

## <a name="get-ahead-of-emerging-threats-with-threat-analytics"></a>Anticiper les menaces émergentes avec l’analytique des menaces

L’analytique des menaces est une fonctionnalité de renseignement sur les menaces dans Microsoft 365 Defender conçue pour aider votre équipe de sécurité à être aussi efficace que possible face aux menaces émergentes. Il inclut une analyse détaillée et des informations sur les éléments suivants :

- Acteurs de menaces actifs et leurs campagnes
- Techniques d’attaque populaires et nouvelles
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

Analyse des menaces inclut également des informations sur les incidents connexes et les ressources affectées au sein de votre locataire Microsoft 365 pour chaque menace identifiée.

Chaque menace identifiée comprend un rapport d’analyste, une analyse complète de la menace écrite par des chercheurs en sécurité Microsoft qui sont à l’avant-garde de la détection et de l’analyse de la cybersécurité. Ces rapports peuvent également fournir des informations sur la façon dont les attaques apparaissent dans Microsoft 365 Defender.

Pour plus d’informations, consultez [Analyse des menaces dans Microsoft 365 Defender](threat-analytics.md).

## <a name="collaborate-with-microsoft-experts"></a>Collaborer avec des experts Microsoft

Les notifications d’attaque de point de terminaison (précédemment appelées Spécialistes des menaces Microsoft - Notifications d’attaque ciblées) sont un service de chasse aux menaces managée. Une fois que vous avez présenté votre demande et que vous êtes accepté, vous recevrez des notifications d’attaque de point de terminaison de la part d’experts microsoft en matière de menaces, afin de ne pas manquer les menaces critiques pour votre environnement. Ces notifications vous aideront à protéger les points de terminaison, l’e-mail et les identités de votre organisation. Microsoft Defender Experts – Experts à la demande vous permet d’obtenir des conseils d’experts sur les menaces auxquelles votre organisation est confrontée et vous pouvez demander de l’aide sur les menaces auxquelles votre organisation est confrontée. Il est disponible en tant que service d’abonnement supplémentaire.

Pour plus d’informations, consultez [Microsoft Defender Présentation des experts dans Microsoft 365](/microsoft-365/security/defender/microsoft-threat-experts).
