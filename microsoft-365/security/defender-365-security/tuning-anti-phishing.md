---
title: Régler la protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- MET150
description: Les administrateurs peuvent apprendre à identifier les raisons et la façon dont un message de hameçonnage a été envoyé dans Microsoft 365, et ce qu’il faut faire pour empêcher d’autres messages de hameçonnage à l’avenir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1772a0329825b8808352892c8d99f0d7680112f5
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064441"
---
# <a name="tune-anti-phishing-protection"></a>Régler la protection anti-hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bien que Microsoft 365 soit fourni avec une variété de fonctionnalités anti-hameçonnage activées par défaut, il est possible que certains messages d’hameçonnage soient encore envoyés à vos boîtes aux lettres. Cette rubrique décrit ce que vous pouvez faire pour découvrir pourquoi un message d’hameçonnage est passé à travers et ce que vous pouvez faire pour ajuster les paramètres anti-hameçonnage dans votre organisation Microsoft 365 sans que les choses se dégradent accidentellement.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Tout d’abord , traitez les comptes compromis et assurez-vous que vous bloquez toute autre tentative de hameçonnage

Si le compte d’un destinataire a été compromis à la suite du message d’hameçonnage, suivez les étapes de réponse à un compte de messagerie compromis dans [Microsoft 365](responding-to-a-compromised-email-account.md).

Si votre abonnement inclut Microsoft Defender pour Office 365, vous pouvez utiliser l’Intelligence des menaces [Office 365](office-365-ti.md) pour identifier les autres utilisateurs qui ont également reçu le message de hameçonnage. Vous avez d’autres options pour bloquer les messages d’hameçonnage :

- [Liens sécurisés dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md)

- [Pièces jointes sécurisées dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md)

- [Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](configure-atp-anti-phishing-policies.md) Notez que vous pouvez augmenter temporairement les **seuils** de hameçonnage avancés dans la stratégie de **Standard** à **Agressif,** Plus agressif **ou** Plus **agressif**.

Vérifiez que ces fonctionnalités de Defender pour Office 365 sont allumées.

## <a name="report-the-phishing-message-to-microsoft"></a>Signaler le message de hameçonnage à Microsoft

Le signalement de messages de hameçonnage est utile pour régler les filtres utilisés pour protéger tous les clients dans Microsoft 365. Pour obtenir des instructions, [reportez-vous aux messages et fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="inspect-the-message-headers"></a>Inspecter les en-têtes de message

Vous pouvez examiner les en-têtes du message d’hameçonnage pour voir s’il existe une chose que vous pouvez faire vous-même pour éviter que d’autres messages de hameçonnage ne s’en approchent. En d’autres termes, l’examen des en-têtes de messages peut vous aider à identifier les paramètres de votre organisation qui étaient chargés d’autoriser les messages de hameçonnage.

Plus précisément, vous devez vérifier le champ **d’en-tête X-Forefront-Antispam-Report** dans les en-têtes de message pour obtenir des indications sur le filtrage ignoré pour le courrier indésirable ou le hameçonnage dans la valeur SFV (Spam Filtering Verdict). Les messages qui ignorent le filtrage auront une entrée de , ce qui signifie que l’un de vos paramètres a autorisé ce message en remplacement des verdicts de courrier indésirable ou de hameçonnage qui ont été déterminés par `SCL:-1` le service. Pour plus d’informations sur la façon d’obtenir des en-têtes de message et la liste complète de tous les en-têtes de messages anti-courrier indésirable et anti-hameçonnage disponibles, consultez les en-têtes de message anti-courrier indésirable dans [Microsoft 365.](anti-spam-message-headers.md)

## <a name="best-practices-to-stay-protected"></a>Meilleures pratiques pour rester protégé

- Sur une base mensuelle, exécutez [le niveau de sécurisation](../defender/microsoft-secure-score.md) pour évaluer les paramètres de sécurité de votre organisation.

- Pour les messages qui sont mis en quarantaine par erreur ou pour les messages autorisés, nous vous recommandons de rechercher ces messages dans l’Explorateur de menaces et les [détections en temps réel.](threat-explorer.md) Vous pouvez effectuer une recherche par expéditeur, destinataire ou ID de message. Après avoir localisé le message, consultez les détails en cliquant sur l’objet. Pour un message mis en quarantaine, recherchez la « technologie de détection » afin de pouvoir utiliser la méthode appropriée pour remplacer. Pour un message autorisé, recherchez la stratégie qui a autorisé le message.

- Le courrier usurpé est marqué comme hameçonnage dans Defender pour Office 365. Parfois, l’usurpation d’un état est anodin, et parfois les utilisateurs ne veulent pas qu’elle soit mise en quarantaine. Pour minimiser l’impact sur les utilisateurs, examinez régulièrement le [rapport sur l’usurpation d’informations.](learn-about-spoof-intelligence.md) Une fois que vous avez examiné et effectué les [](set-up-anti-phishing-policies.md#spoof-settings) remplacements nécessaires,  vous pouvez être certain de configurer la veille contre l’usurpation d’adresse pour mettre en quarantaine les messages suspects au lieu de les remettre dans le dossier Courrier indésirable de l’utilisateur.

- Vous pouvez répéter l’étape ci-dessus pour l’emprunt d’identité (domaine ou utilisateur). Le rapport d’emprunt d’identité se trouve sous **Threat Management** \> **Dashboard** \> **Insights**.

- Examinez régulièrement le rapport [d’état de la protection contre les menaces.](view-reports-for-mdo.md#threat-protection-status-report)

- Certains clients autorisent par inadvertance les messages de hameçonnage en placer leurs propres domaines dans la liste Autoriser l’expéditeur ou Autoriser le domaine dans les stratégies anti-courrier indésirable. Bien que cette configuration autorise certains messages légitimes, elle autorise également les messages malveillants qui seraient normalement bloqués par les filtres de courrier indésirable et/ou de hameçonnage. Au lieu d’autoriser le domaine, vous devez corriger le problème sous-jacent.

  La meilleure façon de traiter les messages légitimes bloqués par Microsoft 365 (faux positifs) qui impliquent des expéditeurs dans votre domaine consiste  à configurer entièrement et entièrement les enregistrements SPF, DKIM et DMARC dans DNS pour tous vos domaines de messagerie :

  - Vérifiez que votre enregistrement SPF identifie toutes les _sources_ de courrier pour les expéditeurs de votre domaine (n’oubliez pas les services tiers !).

  - Utilisez l’échec en dur (tout) pour vous assurer que les expéditeurs non autorisés sont rejetés par les systèmes de messagerie \- configurés pour le faire. Vous pouvez [utiliser](learn-about-spoof-intelligence.md) la veille contre l’usurpation d’identité pour identifier les expéditeurs qui utilisent votre domaine afin d’inclure des expéditeurs tiers autorisés dans votre enregistrement SPF.

  Pour obtenir des instructions de configuration, voir :

  - [Configurer SPF pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md)

  - [Utiliser DMARC pour valider les messages électroniques](use-dmarc-to-validate-email.md)

- Dans la mesure du possible, nous vous recommandons de remettre le courrier électronique de votre domaine directement à Microsoft 365. En d’autres termes, pointez l’enregistrement MX de votre domaine Microsoft 365 vers Microsoft 365. Exchange Online Protection (EOP) est en mesure de fournir la meilleure protection pour vos utilisateurs cloud lorsque leurs messages sont remis directement à Microsoft 365. Si vous devez utiliser un système d’hygiène de messagerie tiers devant EOP, utilisez le filtrage amélioré pour les connecteurs. Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online.](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)

- Les utilisateurs doivent utiliser le [](enable-the-report-phish-add-in.md) module de [signalement](enable-the-report-message-add-in.md) des messages ou le module de signalement du hameçonnage pour signaler des messages à Microsoft, qui peut entraîner notre système. Les administrateurs doivent également tirer parti des fonctionnalités [de soumission](admin-submission.md) d’administrateur.

- L’authentification multifacteur (MFA) est un bon moyen d’éviter les comptes compromis. Vous devez vivement envisager d’activer l’activant MFA pour tous vos utilisateurs. Pour une approche par phases, commencez par activer l’famf pour vos utilisateurs les plus sensibles (administrateurs, cadres, etc.) avant d’activer l’mf pour tout le monde. Pour consulter des instructions, voir [Configurer Multi-factor Authentification (MFA)](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Les règles de forwarding à des destinataires externes sont souvent utilisées par les attaquants pour extraire des données. Utilisez les informations **des règles de forwarding de boîte** aux lettres de révision dans le Score de sécurité [Microsoft](../defender/microsoft-secure-score.md) pour rechercher et même empêcher les règles de forwarding à des destinataires externes. Pour plus d’informations, voir [Atténuation des règles de forwarding externe client avec le score de sécurisation.](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score)
