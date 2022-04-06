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
description: Découvrez comment signaler les faux positifs et les faux négatifs dans Outlook à l’aide de la fonctionnalité Signaler un message.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f2181df44f8d193f8c19c508451733773bd20708
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473501"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Signaler les faux positifs et les faux négatifs dans Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Si vous êtes un administrateur d’une organisation Microsoft 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser la page **Soumissions** dans le portail Microsoft 365 Defender. Pour plus d’informations, voir Utiliser le portail Soumissions pour soumettre des courriers indésirables, du hameçonnage, des URL et des fichiers [suspects à Microsoft](admin-submission.md).

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou locales utilisant l’authentification moderne hybride, vous pouvez envoyer des faux positifs (messages électroniques de qualité bloqués ou envoyés à un dossier de courrier indésirable) et des faux négatifs (courrier indésirable ou hameçonnage remis à la boîte de réception) à Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour une meilleure expérience de soumission d’utilisateurs, utilisez le add-in Report Message ou report Phishing.

- Le add-in Report Message et le add-in Report Phishing fonctionnent pour Outlook sur toutes les plateformes (Outlook sur le web, iOS, Android et Desktop).

- Si vous êtes un administrateur d’une organisation Exchange Online boîtes aux lettres, utilisez le portail Soumissions dans Microsoft 365 Defender portail. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des courriers indésirables [, du hameçonnage, des URL et des fichiers suspectés à Microsoft](admin-submission.md).

- Vous pouvez configurer pour envoyer des messages directement à Microsoft, une boîte aux lettres que vous spécifiez ou les deux. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs](user-submission.md).

- Pour plus d’informations sur la façon d’obtenir et d’activer le message de rapport ou les add-ins Report Phishing, voir [Enable the Report Message or the Report Phishing add-ins](enable-the-report-message-add-in.md).

- Pour plus d’informations sur la notification des messages à Microsoft, voir [Signaler les messages et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

### <a name="turn-off-the-built-in-reporting-experience"></a>Désactiver l’expérience de rapport intégrée

Nous vous déconseillons d’utiliser l’expérience de rapport intégrée dans Outlook car elle ne peut pas utiliser la stratégie [de soumission utilisateur](./user-submission.md). Nous vous recommandons plutôt d’utiliser le add-in Report Message ou report Phishing.

Des autorisations doivent vous être attribuées avant de pouvoir exécuter cette cmdlet. Pour rechercher les autorisations requises pour exécuter une cmdlet ou un paramètre dans votre organisation, voir [Find the permissions required to run any Exchange cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

Exécutez la commande PowerShell suivante pour désactiver l’expérience de rapport intégrée dans Outlook sur le web :

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```


## <a name="use-the-report-message-feature"></a>Utiliser la fonctionnalité Signaler un message

### <a name="report-junk-and-phishing-messages"></a>Signaler les messages de courrier indésirable et de hameçonnage

Pour les messages dans la boîte de réception ou tout autre dossier de courrier électronique à l’exception du courrier indésirable, utilisez la méthode suivante pour signaler le courrier indésirable et les messages de hameçonnage :

1. Sélectionnez les ellipses  Plus **d’actions** dans le coin supérieur droit du message sélectionné, sélectionnez Signaler **le message** dans le menu déroulant, puis sélectionnez Courrier indésirable ou **Hameçonnage**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Icône Autres actions" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Option Courrier indésirable et hameçonnage dans le volet Signaler un message" lightbox="../../media/report-message-junk-phishing.png":::

2. Les messages sélectionnés sont envoyés à Microsoft pour analyse et :
   - Déplacé vers le dossier Courrier indésirable s’ils ont été signalés comme courrier indésirable.
   - Supprimé s’ils ont été signalés comme hameçonnage.

### <a name="report-messages-that-are-not-junk"></a>Signaler les messages qui ne sont pas indésirables

1. Sélectionnez **les ellipses Plus d’actions** dans le coin supérieur droit du message sélectionné, sélectionnez Signaler **le message** dans le menu déroulant, puis sélectionnez Non **indésirable.**

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Icône qui fournit davantage d’actions" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Option Non indésirable sous le volet Signaler un message" lightbox="../../media/report-message-not-junk.png":::

2. Le message sélectionné est envoyé à Microsoft pour analyse et déplacé vers la boîte de réception ou tout autre dossier spécifié.

## <a name="view-and-review-reported-messages"></a>Afficher et examiner les messages signalés

Pour passer en revue les messages que les utilisateurs signalent à Microsoft, vous avez les options ci-après :

- Utilisez la page **Soumissions** dans le portail Microsoft 365 Defender web. Pour plus d’informations, voir [Afficher les soumissions d’utilisateurs à Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- Créez une règle de flux de messagerie (également appelée règle de transport) pour envoyer des copies des messages signalés. Pour obtenir des instructions, voir [Utiliser des règles de flux de messagerie pour voir les rapports des utilisateurs à Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
