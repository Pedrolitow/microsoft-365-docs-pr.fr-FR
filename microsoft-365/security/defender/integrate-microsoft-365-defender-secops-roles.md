---
title: Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision
description: Principes de base de la définition des rôles, des responsabilités et de la supervision lors de l’intégration Microsoft 365 Defender vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, Microsoft 365, réponse aux incidents, cyber-attaque, secops, opérations de sécurité, soc
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
ms.openlocfilehash: 597550afd40f61ad40b52ed8c9651109a523bb1d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60197988"
---
# <a name="step-4-define-microsoft-365-defender-roles-responsibilities-and-oversight"></a>Étape 4. Définir Microsoft 365 Defender rôles, responsabilités et supervision

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Votre organisation doit établir la propriété et la responsabilité des licences Microsoft 365 Defender, des configurations et de l’administration en tant que tâches initiales avant de pouvoir définir des rôles opérationnels. En règle générale, la propriété des licences, les coûts d’abonnement et l’administration des services Microsoft 365 et Enterprise Security + Mobility (EMS) (qui peuvent inclure Microsoft 365 Defender) ne font pas partie des équipes du Centre des opérations de sécurité (SOC). Les équipes SOC doivent travailler avec ces personnes pour assurer une supervision appropriée des Microsoft 365 Defender. 

De nombreux socs modernes affectent à leurs membres d’équipe des catégories en fonction de leurs compétences et fonctions. Par exemple :

- Une équipe d’intelligence des menaces affectée à des tâches liées à la gestion du cycle de vie des fonctions de menace et d’analyse.
- Une équipe de surveillance composée d’analystes SOC responsables de la maintenance des journaux, des alertes, des événements et des fonctions de surveillance.
- Une équipe d'& d’ingénierie affectée à l’ingénierie et à l’optimisation des périphériques de sécurité.

Les rôles et responsabilités d’équipe SOC pour Microsoft 365 Defender intégreraient naturellement ces équipes.

Le tableau suivant décompose les rôles et responsabilités de chaque équipe SOC et la façon dont leurs rôles s’intègrent Microsoft 365 Defender.

| Équipe SOC | Rôles et responsabilités | Microsoft 365 Defender tâches  |
|:-------|:-----|:-------|
| Supervision SOC | <ul><li>Effectue la gouvernance SOC</li><li>Établit des processus quotidiens, hebdomadaires et mensuels</li><li>Formation et sensibilisation</li><li>Embauche du personnel, participe à des groupes d’homologues et à des réunions</li><li>Effectue des exercices d’équipe bleu, rouge et violet</ul>  | <ul><li>Microsoft 365 Defender’accès au portail</li><li>Maintient le registre de mise à jour des fonctionnalités/URL et des licences</li><li>Maintient la communication avec les parties prenantes en matière d’information, juridique, de conformité et de confidentialité</li><li>Participe à des réunions de contrôle des changements pour Microsoft 365 ou Microsoft Azure initiatives</ul> |
| Threat Intelligence & Analytics  | <ul><li>Gestion des flux Intel contre les menaces</li><li>Attribution de virus et de programmes malveillants</li><li>Modélisation des menaces & catégorisations des événements de menace</li><li>Développement d’attributs contre les menaces internes </li><li>Programme d’intégration Intel contre les menaces avec la gestion des risques</li><li>Intègre des informations sur les données à la science des données, à l’aide à la base de données et à l’analyse au sein des équipes ressources humaines, juridiques, informatiques et de sécurité<ul> | <ul><li>Maintient microsoft Defender pour la modélisation des menaces d’identité</li><li>Maintient Microsoft Defender pour la modélisation Office 365 menaces</li><li>Maintient microsoft Defender pour la modélisation des menaces de point de terminaison</ul> |
| Analyse | <ul><li>Analystes de niveau 1, 2, 3</li><li>Maintenance et ingénierie des sources de journaux</li><li>Ingestion de la source de données </li><li>SiEM : l’simulation, l’alerte, la corrélation, l’optimisation</li><li>Génération d’événements et d’alertes</li><li>Analyse des événements et des alertes</li><li>Rapports d’événements et d’alertes</li><li>Maintenance du système de gestion des tickets</ul> | Utilise : <ul><li>Centre de sécurité et conformité</li><li>Portail Microsoft 365 Defender</ul> |
| Ingénierie & SecOps | <ul><li>Gestion des vulnérabilités pour les applications, les systèmes et les points de terminaison</li><li>Automatisation XDR/AUTOMATION</li><li>Tests de conformité</li><li>Hameçonnage et ingénierie DLP</li><li>Ingénierie</li><li>Contrôle de modification des coordonnées</li><li>Coordonnées des mises à jour du runbook</li><li>Test de pénétration<ul> | <ul><li>Microsoft Cloud App Security</li><li>Defender pour point de terminaison</li><li>Defender pour l’identité</ul> |
| Computer Security Incident Response Team (CSIRT) | <ul><li>Examine les cyber incidents et y répond</li><li>Effectue des enquêtes légales</li><li>**Peut souvent être isolé de SOC**</ul> | Collaborer et gérer des Microsoft 365 Defender de réponse aux incidents |
||||


## <a name="next-step"></a>Étape suivante

[Étape 5. Développer et tester des cas d’utilisation](integrate-microsoft-365-defender-secops-use-cases.md)
