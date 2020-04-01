---
title: 'Signaler les courriers indésirables et les tentatives de hameçonnage dans Outlook sur le web '
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 758822b5-0126-463a-9d08-7366bb2a807d
ms.collection:
- M365-security-compliance
description: Les utilisateurs d’Office 365 avec des boîtes aux lettres Exchange Online peuvent utiliser Outlook sur le Web (Outlook Web App) pour soumettre les messages de courrier indésirable, de courrier non indésirable et de hameçonnage à Microsoft pour analyse.
ms.openlocfilehash: b58e3ae5be9bf2a473b655287ad9bb1cb8ef2c78
ms.sourcegitcommit: 4d4d27a49eb258dc560439ca4baf61ebb9c1eff3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "43075619"
---
# <a name="report-junk-and-phishing-email-in-outlook-on-the-web-in-office-365"></a>Signaler les messages de courrier indésirable et de hameçonnage dans Outlook sur le Web dans Office 365

Si vous êtes un client Office 365 avec des boîtes aux lettres Exchange Online, vous pouvez utiliser les options de création de rapports intégrées dans Outlook sur le Web (anciennement Outlook Web App) pour soumettre des faux positifs (courrier marqué comme courrier indésirable), des faux négatifs (courrier incorrect autorisé) et des messages de hameçonnage vers Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

- Si vous êtes administrateur d’une organisation Office 365 avec des boîtes aux lettres Exchange Online, nous vous recommandons d’utiliser le portail d’envoi du centre de sécurité & de la sécurité Office 365. Pour plus d’informations, consultez la rubrique [utiliser la soumission de l’administrateur pour envoyer des courriers indésirables, des hameçons, des URL et des fichiers à Microsoft](admin-submission.md).

- Les administrateurs peuvent désactiver ou activer la possibilité pour les utilisateurs de signaler des messages à Microsoft dans Outlook sur le Web. Pour plus d’informations, consultez la section [désactiver ou activer la création de rapports de courrier indésirable dans Outlook sur le Web](#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) plus loin dans cette rubrique.

- Pour plus d’informations sur la création de rapports de messages à Microsoft, consultez la rubrique [signaler des messages et des fichiers à Microsoft dans Office 365](report-junk-email-messages-to-microsoft.md).

## <a name="report-spam-and-phishing-messages-in-outlook-on-the-web"></a>Signaler les messages de courrier indésirable et de hameçonnage dans Outlook sur le Web

1. Pour les messages de la boîte de réception ou de tout autre dossier de messagerie, à l’exception du courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les messages de courrier indésirable et de hameçonnage :

   - Sélectionnez le message, cliquez sur **courrier indésirable** dans la barre d’outils, puis sélectionnez **courrier indésirable** ou **hameçonnage**.

     ![Signaler le courrier indésirable ou de hameçonnage à partir du ruban](../../media/owa-report-junk.png)

   - Sélectionnez un ou plusieurs messages, cliquez dessus avec le bouton droit, puis sélectionnez **marquer comme courrier indésirable**.

2. Dans la boîte de dialogue qui s’affiche, cliquez sur **rapport**. Si vous changez d’avis, cliquez sur **ne pas signaler**.

   ![Boîte de dialogue signaler comme courrier indésirable](../../media/owa-report-as-junk-dialog.png)

   ![Boîte de dialogue signaler en tant que hameçonnage](../../media/owa-report-as-phishing-dialog.png)

3. Les messages sélectionnés seront envoyés à Microsoft pour analyse. Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="report-non-spam-and-phishing-messages-from-the-junk-email-folder-in-outlook-on-the-web"></a>Signaler les messages de courrier indésirable et de hameçonnage dans le dossier courrier indésirable dans Outlook sur le Web

1. Dans le dossier courrier indésirable, utilisez l’une des méthodes suivantes pour signaler les fausses alertes de courrier indésirable ou les messages de hameçonnage :

   - Sélectionnez le message, cliquez sur **légitime** dans la barre d’outils, puis sélectionnez **pas de courrier indésirable** ou de **hameçonnage**.

     ![Signaler le courrier indésirable ou de hameçonnage à partir du ruban](../../media/owa-report-not-junk.png)

   - Sélectionnez un ou plusieurs messages, cliquez dessus avec le bouton droit, puis sélectionnez **marquer comme légitime**.

2. Dans la boîte de dialogue qui s’affiche, lisez les informations, puis cliquez sur **rapport**. Si vous changez d’avis, cliquez sur **ne pas signaler**.

   ![Boîte de dialogue signaler comme légitime](../../media/owa-report-as-not-junk-dialog.png)

   ![Boîte de dialogue signaler en tant que hameçonnage](../../media/owa-report-as-phishing-dialog.png)

3. Les messages sélectionnés seront envoyés à Microsoft pour analyse. Pour confirmer que les messages ont été envoyés, ouvrez le dossier **Éléments envoyés** pour afficher les messages envoyés.

## <a name="disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Désactiver ou activer la création de rapports de courrier indésirable dans Outlook sur le Web

Par défaut, les utilisateurs peuvent signaler des faux positifs de courrier indésirable, des faux négatifs et des messages de hameçonnage à Microsoft pour analyse dans Outlook sur le Web. Les administrateurs peuvent configurer les stratégies de boîte aux lettres Outlook sur le Web dans Exchange Online PowerShell pour empêcher les utilisateurs de signaler les faux positifs de courrier indésirable et les faux négatifs de courrier indésirable à Microsoft. Vous ne pouvez pas désactiver la possibilité pour les utilisateurs de signaler les messages de hameçonnage à Microsoft.

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu’il faut savoir avant de commencer

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Vous avez spécifiquement besoin des rôles **stratégies de destinataire** ou **destinataires de messagerie** dans Exchange Online, qui sont attribués par défaut aux groupes de rôles gestion de l' **organisation** et **gestion des destinataires** . Pour plus d’informations sur les groupes de rôles dans Exchange Online, consultez la rubrique [modifier des groupes de rôles dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups).

- Chaque organisation a une stratégie par défaut nommée OwaMailboxPolicy-default, mais vous pouvez créer des stratégies personnalisées. Les stratégies personnalisées sont appliquées aux utilisateurs délimités avant la stratégie par défaut. Pour plus d’informations sur les stratégies de boîte aux lettres Outlook sur le Web, consultez [la rubrique relative aux stratégies de boîte aux lettres Outlook sur le Web dans Exchange Online](https://docs.microsoft.com/Exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/outlook-web-app-mailbox-policies).

- La désactivation de la création de rapports de courrier indésirable ne supprime pas la possibilité de marquer un message comme indésirable ou légitime dans Outlook sur le Web. Si vous sélectionnez un message dans le dossier courrier **indésirable** et que vous cliquez sur **légitime** \> , le message est renvoyé dans la boîte de réception. Le fait de sélectionner un message dans un autre dossier de messagerie et **de cliquer sur** \> **Junk** courrier indésirable déplace le message dans le dossier courrier indésirable. Ce qui n’est plus disponible est la possibilité de signaler le message à Microsoft.

### <a name="use-exchange-online-powershell-to-disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Utiliser Exchange Online PowerShell pour désactiver ou activer la création de rapports de courrier indésirable dans Outlook sur le Web

1. Pour rechercher vos stratégies de boîte aux lettres Outlook sur le Web et l’état de la création de rapports de courrier indésirable, exécutez la commande suivante :

   ```powershell
   Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
   ```

2. Pour désactiver ou activer la création de rapports de courrier indésirable dans Outlook sur le Web, utilisez la syntaxe suivante :

   ```powershell
   Set-OwaMailboxPolicy -Identity "<OWAMailboxPolicyName>" -ReportJunkEmailEnabled <$true | $false>
   ```

   Cet exemple désactive la création de rapports de courrier indésirable dans la stratégie par défaut.

   ```powershell
   Set-OwaMailboxPolicy -Identity "OwaMailboxPolicy-Default" -ReportJunkEmailEnabled $false
   ```

   Cet exemple active la création de rapports de courrier indésirable dans la stratégie personnalisée nommée Contoso managers.

   ```powershell
   Set-OwaMailboxPolicy -Identity "Contoso Managers" -ReportJunkEmailEnabled $true
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-OwaMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/client-access/get-owamailboxpolicy) et [Set-OwaMailboxPolicy](https://docs.microsoft.com/powershell/module/exchange/client-access/set-owamailboxpolicy).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien activé ou désactivé la création de rapports de courrier indésirable dans Outlook sur le Web, procédez comme suit :

- Dans Exchange Online PowerShell, exécutez la commande suivante et vérifiez la valeur de la propriété **ReportJunkEmailEnabled** :

  ```powershell
  Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
  ```

- Ouvrez la boîte aux lettres d’un utilisateur concerné dans Outlook sur le Web, sélectionnez un message dans la boîte de réception **, cliquez sur** \> **courrier indésirable** et vérifiez que l’invite de signalement du message à Microsoft est ou non affichée.<sup>\*</sup>

- Ouvrez la boîte aux lettres d’un utilisateur concerné dans Outlook sur le Web, sélectionnez un message dans le dossier courrier indésirable **, cliquez sur** \> **courrier** indésirable et vérifiez que l’invite de signalement du message à Microsoft est ou non affichée.<sup>\*</sup>

<sup>\*</sup>Les utilisateurs peuvent masquer l’invite de signalement du message tout en continuant à signaler le message. Pour vérifier ce paramètre dans Outlook sur le Web, procédez comme suit :

1. Cliquez sur **paramètres** ![Outlook sur l'](../../media/owa-settings-icon.png) \> icône Paramètres du site Web **Afficher tous les paramètres** \> Outlook **courrier indésirable**.
2. Dans la section **création de rapports** , vérifiez la valeur : **me demander avant d’envoyer un rapport**.

   ![Paramètres Outlook sur le courrier indésirable pour le courrier indésirable](../../media/owa-junk-email-reporting-options.png)
