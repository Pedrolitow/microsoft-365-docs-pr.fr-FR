---
title: Playbooks de notation d’alerte
description: Passez en revue les alertes pour les attaques connues et prenez les mesures recommandées pour corriger l’attaque et protéger votre réseau.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
search.appverid: met150
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
- tier2
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: bdb8acc0e3b56d59f6afb6fcbf8a3f6c4c538874
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68089144"
---
# <a name="alert-grading-playbooks"></a>Playbooks de notation d’alerte

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les playbooks de notation d’alertes vous permettent d’examiner et de classer rapidement les alertes pour les attaques connues et de prendre des mesures recommandées pour corriger l’attaque et protéger votre réseau. La notation des alertes permet également de classifier correctement l’incident global.

En tant que chercheur en sécurité ou analyste du Centre des opérations de sécurité (SOC), vous devez avoir accès au portail Microsoft 365 Defender afin de pouvoir :

- Évaluez et examinez les alertes générées et les incidents associés. Consultez [examiner les alertes](investigate-alerts.md).
- Recherchez les données de signal de sécurité de votre locataire et recherchez les menaces potentielles et les activités suspectes. Consultez [la chasse avancée](advanced-hunting-overview.md).

>[!Note]
>Vous pouvez envoyer des commentaires à Microsoft sur les alertes de vrais positifs et de faux positifs, non seulement à la fin de l’enquête, mais également pendant le processus d’investigation. Cela peut aider Microsoft à effectuer une analyse et une classification ultérieures des événements de sécurité.
>

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) protège votre organisation contre les menaces malveillantes posées par les e-mails, les liens (URL) et les outils de collaboration. Defender pour Office 365 inclut :

- Stratégies de protection contre les menaces

   Définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.

- Rapports

  Affichez les rapports en temps réel pour surveiller Defender pour Office 365 performances dans votre organisation.

- Fonctionnalités d’investigation et de réponse aux menaces

  Utilisez des outils de pointe pour examiner, comprendre, simuler et empêcher les menaces.

- Fonctionnalités d’investigation et de réponse automatisées

  Gagnez du temps et des efforts pour examiner et atténuer les menaces.

Defender pour Office 365 alertes peuvent être classées comme suit : 

- Vrai positif (TP) pour une activité malveillante confirmée. 
- Faux positif (FP) pour une activité non malveillante confirmée.

>[!Note]
>Microsoft 365 Defender portail [https://security.microsoft.com](https://security.microsoft.com) rassemble les fonctionnalités des portails de sécurité Microsoft existants. Le portail Microsoft 365 Defender met l’accent sur l’accès rapide aux informations, les dispositions plus simples et le regroupement d’informations connexes pour faciliter leur utilisation.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](/defender-cloud-apps) est un service Cloud Access Security Broker (CASB) qui prend en charge différents modes de déploiement, notamment la collecte des journaux, les connecteurs d’API et le proxy inverse. Il vous offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre les cybermenaces sur l’ensemble de vos services cloud tiers et Microsoft.

Defender pour Cloud Apps s’intègre en mode natif aux principales solutions Microsoft et est conçu avec les professionnels de la sécurité à l’esprit. Il offre un déploiement simple, une gestion centralisée et des fonctionnalités d’automatisation innovantes.

Defender pour Cloud Apps framework offre la possibilité de protéger votre réseau contre les cybermenaces et les anomalies, de détecter les comportements inhabituels entre les applications cloud pour identifier les ransomware, les utilisateurs compromis ou les applications non autorisées. Il permet l’analyse de l’utilisation à haut risque et peut corriger automatiquement pour limiter le risque pour votre organisation.

Les alertes Defender pour Cloud Apps peuvent être classées comme suit : 

- TP pour une activité malveillante confirmée. 
- Vrai positif bénin (B-TP) pour une activité suspecte mais non malveillante, telle qu’un test de pénétration ou une autre action suspecte autorisée. 
- FP pour les activités non malveillantes confirmées.

## <a name="alert-grading-playbooks"></a>Playbooks de notation d’alerte

Consultez ces playbooks pour connaître les étapes permettant de classer plus rapidement les alertes pour les menaces suivantes :

- [Activité suspecte de transfert d’e-mail](alert-grading-playbook-email-forwarding.md)
- [Règles de manipulation de la boîte de réception suspectes](alert-grading-playbook-inbox-manipulation-rules.md)
- [Règle de transfert de boîte de réception suspect](alert-grading-playbook-inbox-forwarding-rules.md)

Consultez [Examiner les alertes](investigate-alerts.md) pour plus d’informations sur l’examen des alertes avec le portail Microsoft 365 Defender.
