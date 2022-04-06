---
title: Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision
description: Principes de base de la définition des rôles, des responsabilités et de la supervision lors de l’intégration de Microsoft 365 Defender dans vos opérations de sécurité.
keywords: incidents, alertes, investigation, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, Microsoft 365, réponse aux incidents, cyberattaque, étendues, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
- M365-security-compliance
- m365solution-m365dsecops
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 5410db413ece81a39453070985e6c744e8b684a6
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664059"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Votre organisation doit établir la propriété et la responsabilité des Microsoft 365 Defender licences, configurations et administration en tant que tâches initiales avant de pouvoir définir des rôles opérationnels. En règle générale, la propriété des licences, les coûts d’abonnement et l’administration des services Microsoft 365 et Enterprise Sécurité + Mobilité (EMS) (qui peuvent inclure Microsoft 365 Defender) relèvent des équipes du Centre des opérations de sécurité (SOC). Les équipes de la SOC devraient collaborer avec ces personnes pour assurer une surveillance adéquate des Microsoft 365 Defender. 

De nombreuses SOC modernes attribuent à ses membres d’équipe des catégories en fonction de leurs compétences et de leurs fonctions. Par exemple :

- Une équipe de renseignement sur les menaces affectée aux tâches liées à la gestion du cycle de vie des fonctions d’analyse et de menaces.
- Une équipe de supervision composée d’analystes SOC chargés de gérer les journaux d’activité, les alertes, les événements et les fonctions de surveillance.
- Une équipe d’ingénierie & des opérations affectée à l’ingénierie et à l’optimisation des appareils de sécurité.

Les rôles et responsabilités de l’équipe SOC pour Microsoft 365 Defender s’intégreraient naturellement à ces équipes.

Le tableau suivant présente les rôles et responsabilités de chaque équipe SOC, ainsi que la façon dont leurs rôles s’intègrent à Microsoft 365 Defender.

| Équipe SOC | Rôles et responsabilités | tâches Microsoft 365 Defender  |
|:-------|:-----|:-------|
| Surveillance SOC | <ul><li>Exécute la gouvernance SOC</li><li>Établit des processus quotidiens, hebdomadaires et mensuels</li><li>Fournit une formation et une sensibilisation</li><li>Embauche du personnel, participe à des groupes d’homologues et à des réunions</li><li>Effectue des exercices d’équipe bleu, rouge, violet</ul>  | <ul><li>Microsoft 365 Defender contrôles d’accès au portail</li><li>Gère le registre des mises à jour des fonctionnalités/URL et des licences</li><li>Maintient la communication avec les parties prenantes informatiques, juridiques, de conformité et de confidentialité</li><li>Participe aux réunions de contrôle des modifications pour les nouvelles initiatives Microsoft 365 ou Microsoft Azure</ul> |
| Analyse des & de renseignement sur les menaces  | <ul><li>Gestion des flux Intel sur les menaces</li><li>Attribution de virus et de programmes malveillants</li><li>Modélisation des menaces & catégorisations d’événements de menace</li><li>Développement d’attributs de menace interne </li><li>Intégration d’Intel aux menaces avec le programme de gestion des risques</li><li>Intègre des insights de données à la science des données, à la décisionnel et à l’analytique au sein des équipes RH, juridiques, informatiques et de sécurité<ul> | <ul><li>Maintient Microsoft Defender pour Identity modélisation des menaces</li><li>Maintient Microsoft Defender pour Office 365 modélisation des menaces</li><li>Maintient Microsoft Defender pour point de terminaison modélisation des menaces</ul> |
| Analyse | <ul><li>Analystes de niveau 1, 2, 3</li><li>Maintenance et ingénierie de la source de journal</li><li>Ingestion de la source de données </li><li>Analyse SIEM, alertes, corrélation, optimisation</li><li>Génération d’événements et d’alertes</li><li>Analyse des événements et des alertes</li><li>Rapports d’événements et d’alertes</li><li>Maintenance du système de tickets</ul> | Utilise: <ul><li>Centre de sécurité et conformité</li><li>Portail Microsoft 365 Defender</ul> |
| Ingénierie & SecOps | <ul><li>Gestion des vulnérabilités pour les applications, les systèmes et les points de terminaison</li><li>Automatisation XDR/SOAR</li><li>Test de conformité</li><li>Hameçonnage et ingénierie DLP</li><li>Ingénierie</li><li>Contrôle de modification des coordonnées</li><li>Coordonne les mises à jour des runbooks</li><li>Test de pénétration<ul> | <ul><li>Microsoft Defender for Cloud Apps</li><li>Defender pour point de terminaison</li><li>Defender pour l’identité</ul> |
| Équipe de réponse aux incidents de sécurité informatique (CSIRT) | <ul><li>Enquête et répond aux cyber incidents</li><li>Effectue des investigations judiciaires</li><li>**Peut souvent être isolé de SOC**</ul> | Collaborer et gérer Microsoft 365 Defender playbooks de réponse aux incidents |
||||


## <a name="next-step"></a>Étape suivante

[Étape 5. Développer et tester des cas d’utilisation](integrate-microsoft-365-defender-secops-use-cases.md)
