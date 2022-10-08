---
title: Régler la protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- m365-security
- m365initiative-defender-office365
- MET150
description: Les administrateurs peuvent apprendre à identifier les raisons pour lesquelles et comment un message de hameçonnage a été transmis dans Microsoft 365, et ce qu’il faut faire pour empêcher d’autres messages de hameçonnage à l’avenir.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: f206894cee57a497506a6dce1a652e52140f1028
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68086484"
---
# <a name="tune-anti-phishing-protection"></a>Régler la protection anti-hameçonnage

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bien que Microsoft 365 soit fourni avec une variété de fonctionnalités anti-hameçonnage activées par défaut, il est possible que certains messages de hameçonnage puissent encore être transmis à vos boîtes aux lettres. Cette rubrique décrit ce que vous pouvez faire pour découvrir pourquoi un message de hameçonnage a réussi et ce que vous pouvez faire pour ajuster les paramètres anti-hameçonnage dans votre organisation Microsoft 365 _sans aggraver accidentellement les choses_.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Tout d’abord : traitez les comptes compromis et assurez-vous que vous empêchez les messages d’hameçonnage de passer

Si le compte d’un destinataire a été compromis à la suite du message d’hameçonnage, suivez les étapes décrites dans [Répondre à un compte de messagerie compromis dans Microsoft 365](responding-to-a-compromised-email-account.md).

Si votre abonnement inclut Microsoft Defender pour Office 365, vous pouvez utiliser [Office 365 Threat Intelligence](office-365-ti.md) pour identifier les autres utilisateurs qui ont également reçu le message de hameçonnage. Vous disposez d’options supplémentaires pour bloquer les messages d’hameçonnage :

- [Liens sécurisés dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md)

- [Pièces jointes sécurisées dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md)

- [Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md). Notez que vous pouvez augmenter temporairement les **seuils de hameçonnage avancés** dans la stratégie de **Standard** à **Agressif**, **Plus agressif** ou **Plus agressif**.

Vérifiez que ces fonctionnalités Defender pour Office 365 sont activées.

## <a name="report-the-phishing-message-to-microsoft"></a>Signaler le message d’hameçonnage à Microsoft

La création de rapports de messages d’hameçonnage est utile pour paramétrer les filtres utilisés pour protéger tous les clients dans Microsoft 365. Pour obtenir des instructions, consultez [Les messages de rapport et les fichiers envoyés à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Inspecter les en-têtes de message

Vous pouvez examiner les en-têtes du message de hameçonnage pour voir s’il existe quelque chose que vous pouvez faire vous-même pour empêcher d’autres messages de hameçonnage de passer. En d’autres termes, l’examen des en-têtes de messages peut vous aider à identifier tous les paramètres de votre organisation chargés d’autoriser les messages de hameçonnage.

Plus précisément, vous devez vérifier le champ **d’en-tête X-Forefront-Antispam-Report dans les en-têtes** de message pour obtenir des indications de filtrage ignoré pour le courrier indésirable ou le hameçonnage dans la valeur SFV (Spam Filtering Verdict). Les messages qui ignorent le filtrage auront une entrée de `SCL:-1`, ce qui signifie que l’un de vos paramètres a autorisé ce message en remplaçant les verdicts de courrier indésirable ou de hameçonnage qui ont été déterminés par le service. Pour plus d’informations sur la façon d’obtenir des en-têtes de message et la liste complète de tous les en-têtes de messages anti-courrier indésirable et anti-hameçonnage disponibles, consultez [les en-têtes de messages anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Meilleures pratiques pour rester protégé

- Sur une base mensuelle, [exécutez le degré de sécurisation](../defender/microsoft-secure-score.md) pour évaluer les paramètres de sécurité de votre organisation.

- Pour les messages qui se retrouvent en quarantaine par erreur ou pour les messages autorisés, nous vous recommandons de rechercher ces messages dans [l’Explorateur de menaces et les détections en temps réel](threat-explorer.md). Vous pouvez effectuer une recherche par expéditeur, destinataire ou ID de message. Une fois que vous avez localisé le message, accédez aux détails en cliquant sur le sujet. Pour un message mis en quarantaine, recherchez la « technologie de détection » qui vous permet d’utiliser la méthode appropriée pour remplacer. Pour un message autorisé, recherchez la stratégie qui a autorisé le message.

- Email des expéditeurs usurpés (l’adresse From du message ne correspond pas à la source du message) est classée comme hameçonnage dans Defender pour Office 365. Parfois, l’usurpation d’identité est bénigne, et parfois les utilisateurs ne souhaitent pas que les messages d’un expéditeur usurpé d’identité spécifique soient mis en quarantaine. Pour réduire l’impact sur les utilisateurs, passez régulièrement en revue [l’insight d’intelligence](learn-about-spoof-intelligence.md) de l’usurpation d’identité, l’onglet **Expéditeurs usurpés** dans la [liste d’autorisations/blocages du locataire](manage-tenant-allow-block-list.md) et le [rapport de détections d’usurpation](view-email-security-reports.md#spoof-detections-report) d’identité. Une fois que vous avez examiné les expéditeurs autorisés et bloqués d’usurpation d’identité et effectué les remplacements nécessaires, vous pouvez être certain de [configurer l’intelligence de l’usurpation d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings) pour mettre **en quarantaine** les messages suspects au lieu de les remettre au dossier Junk Email de l’utilisateur.

- Vous pouvez répéter l’étape ci-dessus pour l’emprunt d’identité (domaine ou utilisateur) dans Microsoft Defender pour Office 365. Le rapport d’emprunt d’identité se trouve sous **Threat Management** \> **Dashboard** \> **Insights**.

- Passez régulièrement en revue le [rapport d’état de la protection contre les menaces](view-reports-for-mdo.md#threat-protection-status-report).

- Certains clients autorisent par inadvertance les messages de hameçonnage en plaçant leurs propres domaines dans la liste Autoriser l’expéditeur ou autoriser le domaine dans les stratégies anti-courrier indésirable. Bien que cette configuration autorise certains messages légitimes, elle autorise également les messages malveillants qui seraient normalement bloqués par les filtres de courrier indésirable et/ou de hameçonnage. Au lieu d’autoriser le domaine, vous devez corriger le problème sous-jacent.

  La meilleure façon de traiter les messages légitimes bloqués par Microsoft 365 (faux positifs) qui impliquent des expéditeurs dans votre domaine consiste à configurer complètement et complètement les enregistrements SPF, DKIM et DMARC dans DNS pour _tous_ vos domaines de messagerie :

  - Vérifiez que votre enregistrement SPF identifie _toutes les_ sources de courrier pour les expéditeurs de votre domaine (n’oubliez pas les services tiers!).

  - Utilisez un échec forcé (\-tous) pour vous assurer que les expéditeurs non autorisés sont rejetés par les systèmes de messagerie configurés pour ce faire. Vous pouvez utiliser [l’information sur l’usurpation d’identité](learn-about-spoof-intelligence.md) pour identifier les expéditeurs qui utilisent votre domaine afin de pouvoir inclure des expéditeurs tiers autorisés dans votre enregistrement SPF.

  Pour obtenir des instructions de configuration, consultez :

  - [Configurer SPF pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md)

  - [Utiliser DMARC pour valider les messages électroniques](use-dmarc-to-validate-email.md)

- Dans la mesure du possible, nous vous recommandons de remettre le courrier électronique de votre domaine directement à Microsoft 365. En d’autres termes, pointez l’enregistrement MX de votre domaine Microsoft 365 vers Microsoft 365. Exchange Online Protection (EOP) est en mesure de fournir la meilleure protection pour vos utilisateurs cloud lorsque leur courrier est remis directement à Microsoft 365. Si vous devez utiliser un système d’hygiène de messagerie tiers devant EOP, utilisez le filtrage amélioré pour les connecteurs. Pour obtenir des instructions, consultez [Filtrage amélioré pour les connecteurs dans Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Les utilisateurs doivent utiliser le [complément Message de](enable-the-report-message-add-in.md) rapport ou le [complément Report Phishing](enable-the-report-phish-add-in.md) pour signaler des messages à Microsoft, qui peut entraîner notre système. Les administrateurs doivent également tirer parti de Administration fonctionnalités de [soumission](admin-submission.md).

- L’authentification multifacteur (MFA) est un bon moyen d’éviter les comptes compromis. Vous devez envisager fortement d’activer l’authentification multifacteur pour tous vos utilisateurs. Pour une approche par phases, commencez par activer l’authentification multifacteur pour vos utilisateurs les plus sensibles (administrateurs, cadres, etc.) avant d’activer l’authentification multifacteur pour tout le monde. Pour consulter des instructions, voir [Configurer Multi-factor Authentification (MFA)](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Les règles de transfert vers des destinataires externes sont souvent utilisées par les attaquants pour extraire des données. Utilisez les informations sur les **règles de transfert de boîte aux lettres de révision** dans [Microsoft Secure Score](../defender/microsoft-secure-score.md) pour rechercher et même empêcher le transfert de règles vers des destinataires externes. Pour plus d’informations, consultez [Atténuation des règles de transfert externe du client avec un score sécurisé](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
