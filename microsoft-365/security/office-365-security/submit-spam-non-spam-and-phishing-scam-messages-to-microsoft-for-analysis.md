---
title: Envoyer manuellement des messages à Microsoft pour analyse
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: dad30e2f-93fe-4d21-9a36-21c87ced85c1
ms.collection:
- M365-security-compliance
description: Les administrateurs et les utilisateurs finaux peuvent apprendre à envoyer des messages électroniques (messages électroniques de qualité marqués comme courriers indésirables ou indésirables autorisés) à Microsoft pour analyse.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9c3a02c710472a996245a38d996ff4485efd1748
ms.sourcegitcommit: 686f192e1a650ec805fe8e908b46ca51771ed41f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52624024"
---
# <a name="manually-submit-messages-to-microsoft-for-analysis"></a>Envoyer manuellement des messages à Microsoft pour analyse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes un administrateur d’une organisation Exchange Online boîtes aux lettres, nous vous recommandons d’utiliser le portail Soumissions dans le Centre de sécurité & conformité. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

Cela peut être frustrant lorsque les utilisateurs de votre organisation reçoivent des messages indésirables (courrier indésirable) ou de hameçonnage dans leur boîte de réception, ou s’ils ne reçoivent pas de message électronique légitime parce qu’il est marqué comme courrier indésirable. Nous affinons constamment nos filtres de courrier indésirable pour être plus précis.

Vous et vos utilisateurs pouvez vous aider à ce processus en envoyant des faux positifs (e-mail de qualité marqué comme faux), des faux négatifs (courrier indésirable autorisé) et des messages de hameçonnage à Microsoft pour analyse.

> [!NOTE]
> En raison du volume élevé de soumissions que nous recevons, nous ne pouvons peut-être pas répondre à toutes les demandes d’analyse.

## <a name="submit-false-negatives-to-microsoft"></a>Envoyer des faux négatifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux négatifs, les utilisateurs de Outlook et de Outlook sur le web (anciennement Outlook Web App) peuvent utiliser le add-in Report Message ou report Phishing. Pour plus d’informations sur l’installation et l’utilisation de ces outils, voir [Enable the Report Message add-in](enable-the-report-message-add-in.md) and Enable the Report [Phishing add-in](enable-the-report-phish-add-in.md).

Si vous recevez un message qui a été transmis par le biais du filtrage du courrier indésirable et qui doit avoir été identifié comme courrier indésirable ou hameçonnage, vous pouvez le soumettre aux équipes d’analyse du courrier indésirable de Microsoft et d’analyse du hameçonnage Microsoft, le cas échéant. Les analystes examinent le message et l’ajoutent aux filtres à l’échelle du service s’il répond aux critères de classification.

1. Créez un message électronique vide avec l’un des destinataires suivants :

   - **Courrier** indésirable : `junk@office365.microsoft.com`
   - **Hameçonnage**: `phish@office365.microsoft.com`

2. Faites glisser et déposez le message de courrier indésirable ou de hameçonnage dans le nouveau message. Cela permet d’enregistrer le message de courrier indésirable ou de hameçonnage en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou ne le faites pas passer (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes du message).

   > [!NOTE]
   >
   > - Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : messages de hameçonnage ou courrier indésirable.
   > - Laissez le corps du message vide.
   > - Utilisez les formats .msg (format Outlook par défaut) ou .eml (Outlook format Web par défaut) pour les messages joints.

3. Lorsque vous avez terminé, cliquez sur **Envoyer.**

> [!TIP]
> Les administrateurs ont plusieurs façons de bloquer des messages spécifiques qui sont identifiés comme courrier indésirable. Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans EOP.](create-block-sender-lists-in-office-365.md)

## <a name="submit-false-positives-to-microsoft"></a>Envoyer des faux positifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux positifs, les utilisateurs de Outlook et de Outlook sur le web (anciennement appelés Outlook Web App) peuvent utiliser le add-in Message de rapport ou le module de signalement du hameçonnage. Pour plus d’informations sur l’installation et l’utilisation de ces outils, voir [Enable the Report Message add-in](enable-the-report-message-add-in.md) and Enable the Report [Phishing add-in](enable-the-report-phish-add-in.md).

Si un message a été identifié à tort comme courrier indésirable, vous pouvez le soumettre à l’équipe d’analyse du courrier indésirable de Microsoft. Les analystes évaluent le message et (en fonction des résultats de l’analyse) les filtres à l’échelle du service peuvent être ajustés pour autoriser le message.

1. Créez un message électronique vide avec `not_junk@office365.microsoft.com` comme destinataire.

2. Faites glisser et déposez le message non identifié dans le nouveau message. Cela permet d’enregistrer le message non identifié en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou ne le faites pas passer (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes du message).

   > [!NOTE]
   >
   > - Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : messages de hameçonnage ou courrier indésirable.
   > - Laissez le corps du message vide.
   > - Utilisez les formats .msg (format Outlook par défaut) ou .eml (Outlook format Web par défaut) pour les messages joints.

3. Lorsque vous avez terminé, cliquez sur **Envoyer.**

> [!TIP]
> Les administrateurs ont plusieurs façons d’autoriser des messages spécifiques à ignorer le filtrage du courrier indésirable. Pour plus d’informations, voir [Créer des listes d’expéditeurs sûrs dans EOP.](create-safe-sender-lists-in-office-365.md)

## <a name="where-is-the-data-from-submissions-to-microsoft-stored"></a>Où sont stockées les données des soumissions à Microsoft ?

Les données résident dans la limite de conformité Office 365 des centres de données d’Amérique du Nord. Les données sont examinées par les analystes de l’équipe d’ingénierie afin d’améliorer l’efficacité des filtres.

## <a name="create-a-mail-flow-rule-to-receive-copies-of-messages-that-are-reported-to-microsoft"></a>Créer une règle de flux de messagerie pour recevoir des copies des messages signalés à Microsoft

Pour obtenir des instructions, voir Utiliser des règles de flux de messagerie pour voir les rapports [des utilisateurs à Microsoft.](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)
