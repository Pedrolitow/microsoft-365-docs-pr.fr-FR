---
title: Passer en revue les exigences d’architecture et les concepts de planification pour Microsoft Defender pour Office 365
description: Le diagramme technique de Microsoft Defender pour Office 365 dans Microsoft 365 Defender vous aidera à comprendre l’identité de Microsoft 365 avant de créer votre laboratoire d’essai ou votre environnement pilote.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 07/01/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
ms.topic: conceptual
ms.openlocfilehash: e23324a7d779e2dd59beda8270099f3514d57746
ms.sourcegitcommit: e9323a90a1156c10b037abca3e16d7367ef92dd7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67567266"
---
# <a name="review-microsoft-defender-for-office-365-architecture-requirements-and-key-concepts"></a>Passer en revue les exigences d’architecture Microsoft Defender pour Office 365 et les concepts clés

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 1 sur 3](eval-defender-office-365-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Avant d’activer Defender pour Office 365, veillez à bien comprendre l’architecture et à répondre aux exigences. Cet article décrit l’architecture, les concepts clés et les prérequis que votre environnement Exchange Online doit respecter.

## <a name="understand-the-architecture"></a>Comprendre l’architecture

Le diagramme suivant illustre l’architecture de base de Microsoft Defender pour Office, qui peut inclure une passerelle SMTP tierce ou une intégration locale. Les scénarios de coexistence hybride (autrement dit, les boîtes aux lettres de production sont à la fois locales et en ligne) nécessitent des configurations plus complexes et ne sont pas abordés dans cet article ou les conseils d’évaluation.

:::image type="content" source="../../media/defender/m365-defender-office-architecture.png" alt-text="Architecture du Microsoft Defender pour Office 365." lightbox="../../media/defender/m365-defender-office-architecture.png":::

Le tableau suivant décrit cette illustration.

|Appel sortant|Description|
|---|---|
|1|Le serveur hôte de l’expéditeur externe effectue généralement une recherche DNS publique pour un enregistrement MX, qui fournit au serveur cible le relais du message. Cette référence peut être directement Exchange Online (EXO) ou une passerelle SMTP configurée pour effectuer un relais par rapport à EXO.|
|2|Exchange Online Protection négocie et valide la connexion entrante et inspecte les en-têtes et le contenu du message pour déterminer les stratégies supplémentaires, le balisage ou le traitement requis.|
|3|Exchange Online s’intègre à Microsoft Defender pour Office 365 pour offrir une protection, une atténuation et une correction des menaces plus avancées.|
|4|Un message qui n’est pas malveillant, bloqué ou mis en quarantaine est traité et remis au destinataire dans EXO, où les préférences utilisateur liées à la courrier indésirable, aux règles de boîte aux lettres ou à d’autres paramètres sont évaluées et déclenchées.|
|5|L’intégration à Active Directory local peut être activée à l’aide d’Azure AD Connect pour synchroniser et approvisionner des objets et des comptes à extension messagerie dans Azure Active Directory et, en fin de compte, Exchange Online.|
|6|Lors de l’intégration d’un environnement local, il est recommandé d’utiliser un serveur Exchange pour la gestion et l’administration prises en charge des attributs, paramètres et configurations liés à la messagerie|
|7 |Microsoft Defender pour Office 365 partage des signaux vers Microsoft 365 Defender pour la détection et la réponse étendues (XDR).|

L’intégration locale est courante, mais facultative. Si votre environnement est cloud uniquement, ces conseils fonctionneront également pour vous.

## <a name="understand-key-concepts"></a>Comprendre les concepts clés

Le tableau suivant a identifié des concepts clés qui sont importants à comprendre lors de l’évaluation, de la configuration et du déploiement de MDO.

|Concept|Description|Plus d’informations|
|---|---|---|
|Exchange Online Protection|Exchange Online Protection (EOP) est le service de filtrage basé sur le cloud qui permet de protéger votre organisation contre les courriers indésirables et les programmes malveillants. EOP est inclus dans toutes les licences Microsoft 365 qui incluent Exchange Online.|[Vue d’ensemble d’Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)|
|Protection anti-programme malveillant|Les organisations avec des boîtes aux lettres dans EXO sont automatiquement protégées contre les programmes malveillants.|[Protection contre les programmes malveillants dans EOP](../office-365-security/anti-malware-protection.md)|
|Protection anti-courrier indésirable|Les organisations avec des boîtes aux lettres dans EXO sont automatiquement protégées contre les stratégies de courrier indésirable et de courrier indésirable.|[Protection anti-courrier indésirable dans EOP](../office-365-security/anti-spam-protection.md)|
|Protection anti-hameçonnage|MDO offre une protection anti-hameçonnage plus avancée liée au harponnage, à la chasse à la baleine, aux ransomwares et à d’autres activités malveillantes.|[Protection anti-hameçonnage supplémentaire dans Microsoft Defender pour Office 365](../office-365-security/anti-phishing-protection.md)|
|Protection contre l’usurpation d’identité|EOP inclut des fonctionnalités pour protéger votre organisation contre les expéditeurs usurpés (falsifiés).|[Protection contre l’usurpation d’identité dans EOP](../office-365-security/anti-spoofing-protection.md)|
|Pièces jointes fiables|Les pièces jointes sécurisées fournissent une couche supplémentaire de protection en utilisant un environnement virtuel pour vérifier et « détoner » les pièces jointes dans les messages électroniques avant qu’elles ne soient remises.|[Pièces jointes sécurisées dans Microsoft Defender pour Office 365](../office-365-security/safe-attachments.md)|
|Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams|En outre, les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams offrent une couche supplémentaire de protection pour les fichiers qui ont été chargés dans des référentiels de stockage cloud.|[Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md)|
|Liens sûrs|Les liens sécurisés sont une fonctionnalité qui fournit l’analyse et la réécriture des URL dans les messages électroniques entrants et offre la vérification de ces liens avant qu’ils ne soient remis ou cliqués.|[Liens sécurisés dans Microsoft Defender pour Office 365](../office-365-security/safe-links.md)|

Pour plus d’informations sur les fonctionnalités incluses dans Microsoft Defender pour Office, consultez [Microsoft Defender pour Office 365 description du service](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="review-architecture-requirements"></a>Passer en revue les exigences en matière d’architecture

Un pilote d’évaluation ou de production MDO réussi suppose les prérequis suivants :

- Toutes vos boîtes aux lettres de destinataire sont actuellement en Exchange Online.
- Votre enregistrement MX public est résolu directement en EOP ou en passerelle SMTP tierce qui relaie ensuite directement les e-mails externes entrants à EOP.
- Votre domaine de messagerie principal est configuré comme *faisant autorité* dans Exchange Online.
- Vous avez correctement déployé et configuré le *blocage d’arêtes basée sur l’annuaire* (DBEB) selon les besoins. Pour plus d’informations, consultez [Utiliser Directory-Based Blocage edge pour rejeter les messages envoyés à des destinataires non valides](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

> [!IMPORTANT]
> Si ces exigences ne sont pas applicables ou si vous êtes toujours dans un scénario de coexistence hybride, une évaluation de Microsoft Defender pour Office 365 peut nécessiter des configurations plus complexes ou avancées qui ne sont pas entièrement couvertes par ce guide.

## <a name="siem-integration"></a>Intégration SIEM

Vous pouvez intégrer Microsoft Defender pour Office 365 à Microsoft Sentinel pour analyser plus en détails les événements de sécurité au sein de votre organisation et créer des playbooks pour une réponse efficace et immédiate. Pour plus d’informations, consultez [Les alertes de connexion à partir de Microsoft Defender pour Office 365](/azure/sentinel/connect-office-365-advanced-threat-protection).

Microsoft Defender pour Office 365 peuvent également être intégrées à d’autres solutions SIEM (Security Information and Event Management) à l’aide de [l’API de gestion des activités Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

## <a name="next-steps"></a>Prochaines étapes

Étape 2 sur 3 : [Activer l’environnement d’évaluation Microsoft Defender pour Office 365](eval-defender-office-365-enable-eval.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
