---
title: Signaler le courrier indésirable et le hameçonnage dans Outlook sur le web
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
ms.assetid: 758822b5-0126-463a-9d08-7366bb2a807d
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur les options intégrées de signalement de courrier indésirable, non indésirable et de hameçonnage dans Outlook sur le web (Outlook Web App) dans Exchange Online, et comment désactiver ces options de rapport pour les utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0bd2da9b774b3557ebb820102ba86c17ebe44c69
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50289220"
---
# <a name="report-junk-and-phishing-email-in-outlook-on-the-web-in-exchange-online"></a>Signaler le courrier indésirable et le hameçonnage dans Outlook sur le web dans Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, vous pouvez utiliser les options de rapport intégrées dans Outlook sur le web (anciennement Outlook Web App) pour envoyer des faux positifs (courrier électronique de qualité marqué comme courrier indésirable), des faux négatifs (courrier indésirable autorisé) et des messages de hameçonnage à Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Si vous êtes un administrateur d’une organisation ayant des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail Soumissions dans le Centre de sécurité & conformité. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

- Les administrateurs peuvent désactiver ou activer la possibilité pour les utilisateurs de signaler des messages à Microsoft dans Outlook sur le web. Pour plus d’informations, voir la section Désactiver ou activer la signalement du courrier indésirable [dans Outlook sur](#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) le web plus loin dans cet article.

- Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)

- Pour plus d’informations sur la notification des messages à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="report-spam-and-phishing-messages-in-outlook-on-the-web"></a>Signaler le courrier indésirable et le hameçonnage dans Outlook sur le web

1. Pour les messages dans la boîte de réception ou tout autre dossier de courrier électronique à l’exception du courrier indésirable, utilisez l’une des méthodes suivantes pour signaler le courrier indésirable et les messages de hameçonnage :

   - Sélectionnez le message, cliquez **sur Courrier** indésirable dans la barre d’outils, puis **sélectionnez** Courrier indésirable ou **Hameçonnage.**

     ![Signaler le courrier indésirable ou le hameçonnage à partir du ruban](../../media/owa-report-junk.png)

   - Sélectionnez un ou plusieurs messages, cliquez avec le bouton droit, puis **sélectionnez Marquer comme courrier indésirable.**

2. Dans la boîte de dialogue qui s’affiche, cliquez sur **Rapport.** Si vous changez d’avis, cliquez sur **Ne pas signaler.**

   |Courrier indésirable|Hameçonnage|
   |:---:|:---:|
   |![Boîte de dialogue Signaler comme courrier indésirable](../../media/owa-report-as-junk-dialog.png)|![Boîte de dialogue Signaler comme hameçonnage](../../media/owa-report-as-phishing-dialog.png)|

3. Les messages sélectionnés sont envoyés à Microsoft pour analyse. Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="report-non-spam-and-phishing-messages-from-the-junk-email-folder-in-outlook-on-the-web"></a>Signaler les messages de courrier non indésirable et de hameçonnage à partir du dossier Courrier indésirable dans Outlook sur le web

1. Dans le dossier Courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les faux positifs du courrier indésirable ou les messages de hameçonnage :

   - Sélectionnez le message, cliquez **sur Ne** pas courrier indésirable dans la barre d’outils, puis sélectionnez Ne pas être indésirable **ou** **Hameçonnage.**

     ![Signaler le courrier électronique non indésirable ou non de hameçonnage à partir du ruban](../../media/owa-report-not-junk.png)

   - Sélectionnez un ou plusieurs messages, cliquez avec le bouton droit, puis **sélectionnez Marquer comme courrier indésirable.**

2. Dans la boîte de dialogue qui s’affiche, lisez les informations et cliquez sur **Rapport.** Si vous changez d’avis, cliquez sur **Ne pas signaler.**

   |Non indésirable|Hameçonnage|
   |:---:|:---:|
   |![Boîte de dialogue Signaler comme courrier indésirable](../../media/owa-report-as-not-junk-dialog.png)|![Boîte de dialogue Signaler comme hameçonnage](../../media/owa-report-as-phishing-dialog.png)|

3. Les messages sélectionnés sont envoyés à Microsoft pour analyse. Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Désactiver ou activer les rapports de courrier indésirable dans Outlook sur le web

Par défaut, les utilisateurs peuvent signaler à Microsoft des faux positifs de courrier indésirable, des faux négatifs et des messages de hameçonnage pour analyse dans Outlook sur le web. Les administrateurs peuvent configurer des stratégies de boîte aux lettres Outlook sur le web dans Exchange Online PowerShell pour empêcher les utilisateurs de signaler des faux positifs et des faux négatifs de courrier indésirable à Microsoft. Vous ne pouvez pas désactiver la possibilité pour les utilisateurs de signaler des messages de hameçonnage à Microsoft.

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées dans Exchange Online avant de pouvoir suivre les procédures de cet article. Plus précisément,  vous avez besoin des **rôles Stratégies** des  destinataires ou Destinataires de messagerie, qui sont attribués par défaut aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.  Pour plus d’informations sur les groupes de rôles dans Exchange Online, voir [Autorisations dans Exchange Online](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo) et Modifier des groupes de [rôles dans Exchange Online.](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups)

- Chaque organisation possède une stratégie par défaut nommée OwaMailboxPolicy-Default, mais vous pouvez créer des stratégies personnalisées. Les stratégies personnalisées sont appliquées aux utilisateurs d’étendue avant la stratégie par défaut. Pour plus d’informations sur les stratégies de boîte aux lettres Outlook sur le web, consultez stratégies de boîte aux lettres [Outlook sur le web dans Exchange Online.](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/outlook-web-app-mailbox-policies)

- La désactivation de la signalement du courrier indésirable ne supprime pas la possibilité de marquer un message comme courrier indésirable ou non indésirable dans Outlook sur le web. La sélection d’un message dans  le dossier Courrier indésirable et le fait de cliquer sur Ne pas courrier indésirable déplace toujours le \>  message dans la boîte de réception. La sélection d’un message dans  un autre dossier de courrier électronique et le fait de cliquer sur Courrier indésirable déplace toujours le message dans le \>  dossier Courrier indésirable. Ce qui n’est plus disponible, c’est la possibilité de signaler le message à Microsoft.

### <a name="use-exchange-online-powershell-to-disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Utiliser Exchange Online PowerShell pour désactiver ou activer la signalement du courrier indésirable dans Outlook sur le web

1. Pour rechercher vos stratégies de boîte aux lettres Outlook sur le web existantes et l’état des rapports de courrier indésirable, exécutez la commande suivante :

   ```powershell
   Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
   ```

2. Pour désactiver ou activer la signalement du courrier indésirable dans Outlook sur le web, utilisez la syntaxe suivante :

   ```powershell
   Set-OwaMailboxPolicy -Identity "<OWAMailboxPolicyName>" -ReportJunkEmailEnabled <$true | $false>
   ```

   Cet exemple désactive le signalement du courrier indésirable dans la stratégie par défaut.

   ```powershell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -ReportJunkEmailEnabled $false
   ```

   Cet exemple active la création de rapports de courrier indésirable dans la stratégie personnalisée nommée Responsables Contoso.

   ```powershell
   Set-OwaMailboxPolicy -Identity "Contoso Managers" -ReportJunkEmailEnabled $true
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-OwaMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/get-owamailboxpolicy) et [Set-OwaMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/set-owamailboxpolicy).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien activé ou désactivé le signalement du courrier indésirable dans Outlook sur le web, utilisez l’une des étapes suivantes :

- Dans Exchange Online PowerShell, exécutez la commande suivante et vérifiez la valeur de la propriété **ReportJunkEmailEnabled** :

  ```powershell
  Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
  ```

- Ouvrez la boîte aux lettres d’un utilisateur affecté dans Outlook  sur le web, sélectionnez un message dans la boîte de réception, cliquez sur Courrier indésirable et vérifiez que l’invite de signalement du message à Microsoft est ou n’est \>  pas affichée.<sup>\*</sup>

- Ouvrez la boîte aux lettres d’un utilisateur affecté dans Outlook  sur le web, sélectionnez un message dans le dossier Courrier indésirable, cliquez sur Courrier indésirable et vérifiez que l’invite de signalement du message à Microsoft est ou n’est pas \>  affichée.<sup>\*</sup>

<sup>\*</sup> Les utilisateurs peuvent masquer l’invite de signalement du message tout en le signalant. Pour vérifier ce paramètre dans Outlook sur le web :

1. Cliquez **sur l’icône Paramètres** ![ Outlook sur le web Icône Afficher tous les ](../../media/owa-settings-icon.png) \> **paramètres Outlook Courrier** \> **indésirable.**
2. Dans la section **Création de** rapports, vérifiez la valeur : **Demandez-moi avant d’envoyer un rapport.**

   ![Paramètres de création de rapports de courrier indésirable Outlook sur le web](../../media/owa-junk-email-reporting-options.png)
