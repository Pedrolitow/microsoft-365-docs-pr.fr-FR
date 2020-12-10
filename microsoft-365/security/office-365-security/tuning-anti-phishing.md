---
title: Régler la protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- MET150
description: Les administrateurs peuvent apprendre à identifier les raisons et le mode de réception d’un message de hameçonnage dans Microsoft 365, ainsi que la marche à suivre pour éviter d’autres messages de hameçonnage.
ms.openlocfilehash: 8a2c63d499317427b921d7786dd60b3ad4f18c42
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615383"
---
# <a name="tune-anti-phishing-protection"></a>Régler la protection anti-hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Bien que Microsoft 365 propose plusieurs fonctionnalités anti-hameçonnage qui sont activées par défaut, il est possible que certains messages de phishing continuent à accéder à vos boîtes aux lettres. Cette rubrique décrit ce que vous pouvez faire pour découvrir pourquoi un message de hameçonnage s’affiche, et ce que vous pouvez faire pour ajuster les paramètres anti-hameçonnage dans votre organisation Microsoft 365 _sans accidentellement_ compliquer les choses.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Tout d’abord : traitez les comptes compromis et assurez-vous de bloquer les messages de hameçonnage

Si le compte d’un destinataire a été compromis suite à un message de hameçonnage, suivez les étapes décrites dans la [réponse à un compte de messagerie compromis dans Microsoft 365](responding-to-a-compromised-email-account.md).

Si votre abonnement inclut Microsoft Defender pour Office 365, vous pouvez utiliser [office 365 Threat Intelligence](office-365-ti.md) pour identifier les autres utilisateurs qui ont également reçu le message de hameçonnage. Vous disposez d’options supplémentaires pour bloquer les messages de hameçonnage :

- [Liens fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-links-policies.md)

- [Pièces jointes fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-attachments-policies.md)

- [Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-atp-anti-phishing-policies.md). Notez que vous pouvez augmenter temporairement les **seuils de phishing avancés** dans la stratégie, de **standard** à **agressif**, **plus agressif** ou **plus agressif**.

Vérifiez que les fonctionnalités de ces fonctionnalités de Defender pour Office 365 sont activées.

## <a name="report-the-phishing-message-to-microsoft"></a>Signaler le message de hameçonnage à Microsoft

La création de messages de phishing est utile pour régler les filtres utilisés pour protéger tous les clients dans Microsoft 365. Pour obtenir des instructions, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Inspecter les en-têtes de message

Vous pouvez examiner les en-têtes du message de hameçonnage pour voir s’il y a quelque chose que vous pouvez faire vous-même pour empêcher d’autres messages de phishing de venir. En d’autres termes, l’examen des en-têtes de messages peut vous aider à identifier tous les paramètres de votre organisation qui ont été chargés d’autoriser les messages de hameçonnage dans.

Plus précisément, vous devez vérifier le champ d’en-tête **X-Forefront-antispam-Report** dans les en-têtes de message pour obtenir des indications de filtrage ignoré pour le courrier indésirable ou le hameçonnage dans la valeur de filtrage du courrier indésirable (SFV). Les messages qui ignorent le filtrage auront une entrée de `SCL:-1` , ce qui signifie que l’un de vos paramètres a autorisé ce message en remplaçant le courrier indésirable ou le score de phishing déterminé par le service. Pour plus d’informations sur l’obtention des en-têtes de message et la liste complète des en-têtes de message anti-courrier indésirable et anti-hameçonnage disponibles, consultez les en [-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Meilleures pratiques pour rester protégé

- Sur une base mensuelle, exécutez le [score sécurisé](../mtp/microsoft-secure-score.md) pour évaluer les paramètres de sécurité de votre organisation.

- Pour les messages qui sont mis en quarantaine par erreur ou pour les messages autorisés, nous vous recommandons de rechercher ces messages dans l' [Explorateur de menaces et les détections en temps réel](threat-explorer.md). Vous pouvez effectuer une recherche par expéditeur, destinataire ou ID de message. Une fois que vous avez trouvé le message, accédez à détails en cliquant sur l’objet. Pour un message en quarantaine, consultez la rubrique « technologie de détection » afin de pouvoir utiliser la méthode appropriée pour le remplacement. Pour obtenir un message autorisé, vérifiez quelle stratégie a autorisé le message.

- Le courrier usurpé est marqué comme hameçonnage dans Defender pour Office 365. Parfois, l’usurpation d’identité est inoffensive et les utilisateurs ne doivent pas être mis en quarantaine. Pour réduire l’impact sur les utilisateurs, consultez régulièrement le rapport d’aide à la [décision](learn-about-spoof-intelligence.md). Une fois que vous avez vérifié et effectué les remplacements nécessaires, vous pouvez être sûr de [configurer](set-up-anti-phishing-policies.md#spoof-settings) l’aide à la **mise en quarantaine** des messages suspects au lieu de les transmettre au dossier de courrier indésirable de l’utilisateur.

- Vous pouvez répéter l’étape ci-dessus pour l’emprunt d’identité (domaine ou utilisateur). Le rapport d’emprunt d’identité se trouve sous informations sur le tableau de bord **gestion des menaces** \> **Dashboard** \> **Insights**.

- Examinez régulièrement le [rapport d’état de protection contre les menaces](view-reports-for-atp.md#threat-protection-status-report).

- Certains clients peuvent accidentellement autoriser les messages d’hameçonnage en plaçant leurs propres domaines dans la liste autoriser l’expéditeur ou autoriser le domaine dans les stratégies de blocage du courrier indésirable. Bien que cette configuration autorise certains messages légitimes, elle autorise également les messages malveillants qui seraient normalement bloqués par le courrier indésirable et/ou les filtres de hameçonnage. Au lieu d’autoriser le domaine, vous devez corriger le problème sous-jacent.

  La meilleure façon de traiter les messages légitimes bloqués par Microsoft 365 (faux positifs) qui impliquent des expéditeurs dans votre domaine est de configurer entièrement et complètement les enregistrements SPF, DKIM et DMARC dans le système DNS pour _tous_ vos domaines de messagerie :

  - Vérifiez que votre enregistrement SPF identifie _toutes les_ sources de courrier pour les expéditeurs de votre domaine (n’oubliez pas les services tiers).

  - Utilisez la défaillance matérielle ( \- tout) pour vous assurer que les expéditeurs non autorisés sont rejetés par les systèmes de messagerie qui sont configurés pour le faire. Vous pouvez utiliser l’Assistant d’aide à la [décision](learn-about-spoof-intelligence.md) pour identifier les expéditeurs qui utilisent votre domaine afin que vous puissiez inclure des expéditeurs tiers autorisés dans votre enregistrement SPF.

  Pour obtenir des instructions de configuration, voir :

  - [Configurer SPF pour empêcher l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md)

  - [Utiliser DMARC pour valider les messages électroniques](use-dmarc-to-validate-email.md)

- Dans la mesure du possible, nous vous recommandons de livrer le courrier électronique pour votre domaine directement à Microsoft 365. En d’autres termes, pointez l’enregistrement MX de votre domaine Microsoft 365 vers Microsoft 365. Exchange Online Protection (EOP) est capable de fournir la meilleure protection aux utilisateurs de votre nuage lorsque leur courrier est remis directement à Microsoft 365. Si vous devez utiliser un système d’hygiène de messagerie tiers devant l’interface EOP, utilisez un filtrage amélioré pour les connecteurs. Pour obtenir des instructions, voir [Enhanced Filtering for Connectors in Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Les utilisateurs doivent [signaler les messages](enable-the-report-message-add-in.md) à Microsoft, qui peuvent former notre système. Les administrateurs doivent également tirer parti des fonctionnalités de soumission de l' [administrateur](admin-submission.md) .

- L’authentification multifacteur (MFA) est un moyen efficace pour empêcher les comptes compromis. Vous devez sérieusement envisager d’activer l’authentification multifacteur pour tous vos utilisateurs. Pour une approche progressive, commencez par activer l’authentification multifacteur pour vos utilisateurs les plus sensibles (administrateurs, cadres, etc.) avant d’activer l’authentification multifacteur pour tout le monde. Pour consulter des instructions, voir [Configurer Multi-factor Authentification (MFA)](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Les règles de transfert vers des destinataires externes sont souvent utilisées par des agresseurs pour extraire des données. Utilisez les **règles de transfert des boîtes aux lettres** dans le [score de sécurité Microsoft](../mtp/microsoft-secure-score.md) pour rechercher et même empêcher le transfert des règles vers des destinataires externes. Pour plus d’informations, consultez la rubrique [minimisation des règles de transfert externe des clients avec le score sécurisé](https://docs.microsoft.com/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
