---
title: Envoi manuel de messages à Microsoft pour analyse
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: dad30e2f-93fe-4d21-9a36-21c87ced85c1
ms.collection:
- M365-security-compliance
description: Les administrateurs et les utilisateurs finaux peuvent apprendre à envoyer des messages électroniques (courrier marqué comme faux ou courrier incorrect) à Microsoft pour analyse.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 94f00f8399164a84d2cb9dae0c4c416b73dfb0dc
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46827808"
---
# <a name="manually-submit-messages-to-microsoft-for-analysis"></a>Envoi manuel de messages à Microsoft pour analyse

> [!NOTE]
> Si vous êtes administrateur d’une organisation avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail d’envoi du centre de sécurité & conformité. Pour plus d’informations, consultez la rubrique [utiliser la soumission de l’administrateur pour envoyer des courriers indésirables, des hameçons, des URL et des fichiers à Microsoft](admin-submission.md).

Il peut être frustrant lorsque les utilisateurs de votre organisation reçoivent des courriers indésirables (spam) ou des messages de hameçonnage dans leur boîte de réception, ou s’ils ne reçoivent pas de message électronique légitime, car il est marqué comme courrier indésirable. Nous ajustons constamment les filtres de courrier indésirable pour qu’ils soient plus précis.

Vous et vos utilisateurs pouvez aider ce processus en soumettant des faux positifs (courrier électronique marqué comme incorrect), des faux négatifs (courrier incorrect) et des messages de hameçonnage à Microsoft pour analyse.

> [!NOTE]
> En raison du volume élevé des envois que nous recevons, il se peut que nous ne parvenons pas à répondre à toutes les demandes d’analyse.

## <a name="submit-false-negatives-to-microsoft"></a>Soumettre des faux négatifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux négatifs, les utilisateurs dans Outlook et Outlook sur le Web (anciennement appelé Outlook Web App) peuvent utiliser le complément de message de rapport pour Microsoft Outlook. Pour plus d’informations sur l’installation et l’utilisation de cet outil, voir [activer le complément de message de rapport](enable-the-report-message-add-in.md).

Si vous recevez un message transmis par le biais du filtrage du courrier indésirable qui aurait dû être identifié comme courrier indésirable ou hameçonnage, vous pouvez envoyer le message aux équipes analyse du courrier indésirable et Microsoft Phishing Analysis, selon le cas. Les analystes examineront le message et l’ajouteront aux filtres à l’échelle du service s’il répond aux critères de classification.

1. Créez un message électronique vide avec l’un des destinataires suivants :

   - **Courrier indésirable**: `junk@office365.microsoft.com`

   - **Hameçonnage**: `phish@office365.microsoft.com`

2. Faites glisser et déposez le message de courrier indésirable dans le nouveau message. Cette opération permet d’enregistrer le message de courrier indésirable ou de hameçonnage en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou transférez le message (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes des messages).

   > [!NOTE]
   >
   > - Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : les messages de hameçonnage ou les messages électroniques de courrier indésirable.
   >
   > - Laissez le corps du message vide.
   >
   > - Utilisez les formats. MSG (format Outlook par défaut) ou. eml (Outlook sur le format Web par défaut) pour les messages joints.

3. Lorsque vous avez terminé, cliquez sur **Envoyer**.

> [!TIP]
> Les administrateurs disposent de différentes manières de bloquer des messages spécifiques identifiés comme courrier indésirable. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md).

## <a name="submit-false-positives-to-microsoft"></a>Soumettre des faux positifs à Microsoft

> [!TIP]
> Au lieu d’utiliser les procédures suivantes pour signaler les faux positifs, les utilisateurs dans Outlook et Outlook sur le Web peuvent utiliser le complément de message de rapport pour Microsoft Outlook. Pour plus d’informations sur l’installation et l’utilisation de cet outil, voir [activer le complément de message de rapport](enable-the-report-message-add-in.md).

Si un message a été identifié de manière incorrecte comme courrier indésirable, vous pouvez envoyer le message à l’équipe d’analyse du courrier indésirable de Microsoft. Les analystes évaluent le message et (en fonction des résultats de l’analyse) les filtres à l’échelle du service peuvent être ajustés pour autoriser le message.

1. Créez un message électronique vide avec `not_junk@office365.microsoft.com` comme destinataire :

2. Faites glisser et déposez le message qui a été identifié dans le nouveau message. Cette opération permet d’enregistrer le message identifié de manière indéterminée en tant que pièce jointe dans le nouveau message. Ne copiez pas et ne collez pas le contenu du message ou transférez le message (nous avons besoin du message d’origine pour pouvoir inspecter les en-têtes des messages).

   > [!NOTE]
   >
   > - Vous pouvez joindre plusieurs messages dans le nouveau message. Assurez-vous que tous les messages sont du même type : les messages de hameçonnage ou les messages électroniques de courrier indésirable.
   >
   > - Laissez le corps du message vide.
   >
   > - Utilisez les formats. MSG (format Outlook par défaut) ou. eml (Outlook sur le format Web par défaut) pour les messages joints.

3. Lorsque vous avez terminé, cliquez sur **Envoyer**.

> [!TIP]
> Les administrateurs disposent de différentes manières d’autoriser des messages spécifiques à ignorer le filtrage du courrier indésirable. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans EOP](create-safe-sender-lists-in-office-365.md).

## <a name="create-a-mail-flow-rule-to-receive-copies-of-messages-that-are-reported-to-microsoft"></a>Créer une règle de flux de messagerie pour recevoir des copies des messages signalés à Microsoft

Pour obtenir des instructions, consultez [la rubrique utiliser des règles de flux de messagerie pour voir ce que vos utilisateurs signalent à Microsoft](use-mail-flow-rules-to-see-what-your-users-are-reporting-to-microsoft.md).
