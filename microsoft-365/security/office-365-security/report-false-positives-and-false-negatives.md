---
title: Signaler les faux positifs et les faux négatifs dans Outlook
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Découvrez comment signaler des faux positifs et des faux négatifs dans Outlook à l’aide de la fonctionnalité Message de rapport.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 762f16916e03940f4d0f95c48f13751d3cbd63c7
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416969"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Signaler les faux positifs et les faux négatifs dans Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes administrateur dans une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser la page **Soumissions** dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Utiliser le portail Soumissions pour envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft](admin-submission.md).

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des boîtes aux lettres Exchange Online ou locales à l’aide de l’authentification moderne hybride, vous pouvez envoyer des faux positifs (bon e-mail bloqué ou envoyé au dossier indésirable) et de faux négatifs (courrier indésirable ou hameçonnage qui a été remis à la boîte de réception) à Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

- Pour une meilleure expérience d’envoi des utilisateurs, utilisez le complément Message de rapport ou le complément Report Phishing.

- Le complément Message de rapport et le complément Report Phishing fonctionnent pour les Outlook sur toutes les plateformes (Outlook sur le web, iOS, Android et Desktop).

- Si vous êtes administrateur dans une organisation avec des boîtes aux lettres Exchange Online, utilisez le portail Soumissions dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Utiliser la soumission d’administrateur pour envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft](admin-submission.md).

- Vous pouvez configurer l’envoi de messages directement à Microsoft, une boîte aux lettres que vous spécifiez ou les deux. Pour plus d’informations, consultez [les stratégies d’envoi des utilisateurs](user-submission.md).

- Pour plus d’informations sur l’obtention et l’activation du message de rapport ou des compléments d’hameçonnage de rapport, consultez [Activer le message de rapport ou les compléments d’hameçonnage](enable-the-report-message-add-in.md) de rapport.

- Pour plus d’informations sur la création de rapports de messages à Microsoft, consultez [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

Regardez cette courte vidéo pour découvrir comment vous pouvez utiliser Microsoft Defender pour Office 365 pour examiner facilement les soumissions d’utilisateurs afin de déterminer le contenu d’un message et de répondre à la soumission en appliquant l’action de correction appropriée. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBHof]

### <a name="turn-off-the-built-in-reporting-experience"></a>Désactiver l’expérience de création de rapports intégrée

Nous ne recommandons pas l’expérience de création de rapports intégrée dans Outlook, car elle ne peut pas utiliser la [stratégie de soumission utilisateur](./user-submission.md). Nous vous recommandons d’utiliser le complément Message de rapport ou le complément Report Phishing à la place.

Des autorisations doivent vous être attribuées avant de pouvoir exécuter cette cmdlet. Pour rechercher les autorisations requises pour exécuter une cmdlet ou un paramètre dans votre organisation, voir [Find the permissions required to run any Exchange cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

Exécutez la commande PowerShell suivante pour désactiver l’expérience de création de rapports intégrée dans Outlook sur le web :

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```

## <a name="use-the-report-message-feature"></a>Utiliser la fonctionnalité Message de rapport

### <a name="report-junk-and-phishing-messages"></a>Signaler des messages indésirables et de hameçonnage

Pour les messages dans la boîte de réception ou tout autre dossier de courrier, à l’exception du courrier indésirable, utilisez la méthode suivante pour signaler le courrier indésirable et les messages de hameçonnage :

1. Sélectionnez les points de suspension **Plus d’actions** dans le coin supérieur droit du message sélectionné, sélectionnez **Signaler le message** dans le menu déroulant, puis sélectionnez **Courrier indésirable** ou **hameçonnage**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Icône Plus d’actions" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Option Courrier indésirable et hameçonnage dans le volet Message de rapport" lightbox="../../media/report-message-junk-phishing.png":::

2. Les messages sélectionnés seront envoyés à Microsoft pour analyse et :
   - Déplacé vers le dossier Courrier indésirable s’ils ont été signalés comme courrier indésirable.
   - Supprimé s’ils ont été signalés comme hameçonnage.

### <a name="report-messages-that-are-not-junk"></a>Signaler les messages qui ne sont pas indésirables

1. Sélectionnez les points de suspension **Plus d’actions** dans le coin supérieur droit du message sélectionné, sélectionnez **Signaler le message** dans le menu déroulant, puis sélectionnez **Non indésirable**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Icône qui fournit d’autres actions" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Option Not Junk sous le volet Message de rapport" lightbox="../../media/report-message-not-junk.png":::

2. Le message sélectionné sera envoyé à Microsoft pour analyse et déplacé vers la boîte de réception ou tout autre dossier spécifié.

## <a name="view-and-review-reported-messages"></a>Afficher et passer en revue les messages signalés

Pour passer en revue les messages que les utilisateurs signalent à Microsoft, vous disposez des options suivantes :

- Utilisez la page **Soumissions** dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Afficher les soumissions d’utilisateurs à Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- Créez une règle de flux de courrier (également appelée règle de transport) pour envoyer des copies des messages signalés. Pour obtenir des instructions, consultez [Utiliser les règles de flux de courrier pour voir ce que les utilisateurs signalent à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
