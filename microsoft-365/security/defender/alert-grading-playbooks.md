---
title: Manuels de notation des alertes
description: Examinez les alertes pour les attaques connues et prenez les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, courrier électronique, 365, microsoft, m365
search.appverid: met150
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: fe0beb88cf613a5a966fc0534dfa4def715e81d2
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62355149"
---
# <a name="alert-grading-playbooks"></a>Manuels de notation des alertes

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les manuels de notation des alertes vous permettent de passer en revue et de classer rapidement les alertes pour les attaques connues et de prendre les mesures recommandées pour corriger l’attaque et protéger votre réseau. La notation des alertes vous aidera également à classer correctement l’incident global.

En tant qu’analyste du Centre d’opérations de sécurité ou de recherche sur la sécurité, vous devez avoir accès au portail Microsoft 365 Defender pour pouvoir :

- Évaluez et examinez les alertes générées et les incidents associés. Voir [examiner les alertes](investigate-alerts.md).
- Recherchez les données du signal de sécurité de votre client et recherchez les menaces potentielles et les activités suspectes. Voir [la recherche avancée](advanced-hunting-overview.md).

>[!Note]
>Vous pouvez fournir des commentaires à Microsoft sur les alertes vraies positives et fausses positives, non seulement à la fin de l’enquête, mais également pendant le processus d’examen. Cela peut aider Microsoft à analyser et à classificationr ultérieurement les événements de sécurité.
>

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. Defender pour Office 365 inclut :

- Stratégies de protection contre les menaces

   Définir des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.

- Rapports

  Affichez les rapports en temps réel pour surveiller Defender pour Office 365 performances au niveau de votre organisation.

- Fonctionnalités d’examen et de réponse aux menaces

  Utilisez des outils de pointe pour examiner, comprendre, simuler et prévenir les menaces.

- Fonctionnalités automatisées d’examen et de réponse

  Gagnez du temps et des efforts pour examiner et atténuer les menaces.

Defender for Office 365 alerts can be classified as: 

- Vrai positif (TP) pour les activités malveillantes confirmées. 
- Faux positif (FP) pour une activité non malveillante confirmée.

>[!Note]
>Microsoft 365 Defender portail regroupe [https://security.microsoft.com](https://security.microsoft.com) les fonctionnalités des portails de sécurité Microsoft existants. Le portail Microsoft 365 Defender met l’accent sur l’accès rapide aux informations, des dispositions plus simples et la mise en réseau des informations associées pour faciliter leur utilisation.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

[Microsoft Defender pour les applications cloud](/defender-cloud-apps) est un courtier de sécurité d’accès cloud (CASB) qui prend en charge différents modes de déploiement, notamment la collecte de journaux, les connecteurs d’API et le proxy inverse. Il vous offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre les cybermenaces sur l’ensemble de vos services cloud tiers et Microsoft.

Defender pour les applications cloud s’intègre en natif aux solutions Microsoft de pointe et est conçu avec les professionnels de la sécurité à l’esprit. Il offre un déploiement simple, une gestion centralisée et des fonctionnalités d’automatisation innovantes.

L’infrastructure Defender pour les applications cloud inclut la possibilité de protéger votre réseau contre les cybermenaces et les anomalies, détecte un comportement inhabituel entre les applications cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non malveillantes. Il permet d’analyser l’utilisation à risque élevé et peut corriger automatiquement les risques pour votre organisation.

Les alertes Defender pour les applications cloud peuvent être classées comme : 

- TP pour les activités malveillantes confirmées. 
- Vrai positif non positif (B-TP) pour les activités suspectes mais non malveillantes, telles qu’un test de pénétration ou toute autre action suspecte autorisée. 
- FP pour les activités non malveillantes confirmées.

## <a name="alert-grading-playbooks"></a>Manuels de notation des alertes

Consultez ces manuels pour obtenir la procédure à suivre pour obtenir une note plus rapide des alertes pour les menaces suivantes :

- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Règles de forwarding de boîte de réception suspectes](alert-grading-playbook-inbox-forwarding-rules.md)

Voir [Examiner les alertes](investigate-alerts.md) pour plus d’informations sur la façon d’examiner les alertes à l’Microsoft 365 Defender portail.
