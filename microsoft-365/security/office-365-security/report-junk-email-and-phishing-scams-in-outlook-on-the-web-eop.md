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
description: Les administrateurs peuvent en savoir plus sur les options intégrées de signalement du courrier indésirable, non indésirable et du hameçonnage dans Outlook sur le web (Outlook Web App) dans Exchange Online, et comment désactiver ces options de rapport pour les utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1139871f5929ff9fef29e980b7614e5bc7b92570
ms.sourcegitcommit: b09aee96a1e2266b33ba81dfe497f24c5300bb56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2021
ms.locfileid: "52788306"
---
# <a name="report-junk-and-phishing-email-in-outlook-on-the-web-in-exchange-online"></a>Signaler le courrier indésirable et le hameçonnage dans Outlook sur le web dans Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou locales utilisant l’authentification moderne [hybride,](../../enterprise/hybrid-modern-auth-overview.md)vous pouvez soumettre des faux positifs (courrier électronique de qualité marqué comme courrier indésirable), des faux négatifs (courrier indésirable autorisé) et des messages de hameçonnage à Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

> [!IMPORTANT]
> Nous recommandons le module de signalement du message ou le module de signalement du hameçonnage pour les soumissions d’utilisateurs. Pour plus d’informations, voir [Enable the Report Message or the Report Phishing add-ins](./enable-the-report-message-add-in.md). Nous vous déconseillons d’utiliser l’expérience de rapport intégrée dans Outlook car elle ne peut pas utiliser la stratégie de [soumission d’utilisateur.](./user-submission.md)

- Si vous êtes un administrateur d’une organisation Exchange Online boîtes aux lettres, nous vous recommandons d’utiliser le portail Soumissions dans le Centre de sécurité & conformité. Pour plus d’informations, voir Utiliser la soumission d’administrateur pour soumettre des messages suspects de courrier indésirable, d’hameçonnage, d’URL et [de fichiers à Microsoft.](admin-submission.md)

- Les administrateurs peuvent désactiver ou activer la possibilité pour les utilisateurs de signaler des messages à Microsoft Outlook sur le web. Pour plus d’informations, voir la section Désactiver ou activer les rapports de courrier indésirable Outlook sur [le web](#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) plus loin dans cet article.

- Vous pouvez configurer la copie ou la redirection des messages signalés vers une boîte aux lettres que vous spécifiez. Pour plus d’informations, voir [Stratégies d’envoi des utilisateurs.](user-submission.md)

- Pour plus d’informations sur la notification des messages à Microsoft, voir [Signaler des messages et des fichiers à Microsoft.](report-junk-email-messages-to-microsoft.md)

## <a name="disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Désactiver ou activer les rapports de courrier indésirable dans Outlook sur le web

Par défaut, les utilisateurs peuvent signaler à Microsoft des faux positifs de courrier indésirable, des faux négatifs et des messages de hameçonnage pour analyse dans Outlook sur le web. Les administrateurs peuvent configurer Outlook stratégies de boîte aux lettres web dans Exchange Online PowerShell pour empêcher les utilisateurs de signaler des faux positifs et des faux négatifs de courrier indésirable à Microsoft. Vous ne pouvez pas désactiver la possibilité pour les utilisateurs de signaler des messages de hameçonnage à Microsoft.

### <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées Exchange Online avant de pouvoir suivre les procédures de cet article. Plus précisément,  vous avez besoin des **rôles Stratégies** des  destinataires ou Destinataires de messagerie, qui sont attribués par défaut aux groupes de rôles Gestion de l’organisation et Gestion des destinataires.  Pour plus d’informations sur les groupes de rôles Exchange Online, voir [Autorisations](/exchange/permissions-exo/permissions-exo) dans Exchange Online et Modifier les groupes de rôles [dans Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups).

- Chaque organisation possède une stratégie par défaut nommée OwaMailboxPolicy-Default, mais vous pouvez créer des stratégies personnalisées. Les stratégies personnalisées sont appliquées aux utilisateurs d’étendue avant la stratégie par défaut. Pour plus d’informations Outlook sur les stratégies de boîte aux lettres web, voir Outlook [stratégies](/Exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/outlook-web-app-mailbox-policies)de boîte aux lettres web dans Exchange Online .

- La désactivation de la signalement du courrier indésirable ne supprime pas la possibilité de marquer un message comme courrier indésirable ou non indésirable dans Outlook sur le web. La sélection d’un message dans  le dossier Courrier indésirable et le fait de cliquer sur Ne pas courrier indésirable déplace toujours le \>  message dans la boîte de réception. La sélection d’un message dans  un autre dossier de courrier électronique et le fait de cliquer sur Courrier indésirable déplace toujours le message dans le \>  dossier Courrier indésirable. Ce qui n’est plus disponible, c’est la possibilité de signaler le message à Microsoft.

### <a name="use-exchange-online-powershell-to-disable-or-enable-junk-email-reporting-in-outlook-on-the-web"></a>Utiliser Exchange Online PowerShell pour désactiver ou activer les rapports de courrier indésirable dans Outlook sur le web

1. Pour rechercher vos stratégies de boîte aux lettres Outlook sur le web et l’état du signalement du courrier indésirable, exécutez la commande suivante :

   ```powershell
   Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
   ```

2. Pour désactiver ou activer les rapports de courrier indésirable dans Outlook sur le web, utilisez la syntaxe suivante :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-OwaMailboxPolicy](/powershell/module/exchange/get-owamailboxpolicy) et [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez réussi à activer ou désactiver la signalement du courrier indésirable dans Outlook sur le web, utilisez l’une des étapes suivantes :

- Dans Exchange Online PowerShell, exécutez la commande suivante et vérifiez la valeur de la propriété **ReportJunkEmailEnabled** :

  ```powershell
  Get-OwaMailboxPolicy | Format-Table Name,ReportJunkEmailEnabled
  ```

- Ouvrez la boîte aux lettres d’un utilisateur affecté dans Outlook sur  le web, sélectionnez un message dans la boîte de réception, cliquez sur Courrier indésirable et vérifiez que l’invite de signalement du message à Microsoft s’affiche ou \>  non.<sup>\*</sup>

- Ouvrez la boîte aux lettres d’un utilisateur affecté dans Outlook sur le  web, sélectionnez un message dans le dossier Courrier indésirable, cliquez sur Courrier indésirable et vérifiez que l’invite de signalement du message à Microsoft s’affiche ou \>  non.<sup>\*</sup>

<sup>\*</sup> Les utilisateurs peuvent masquer l’invite de signalement du message tout en le signalant. Pour vérifier ce paramètre dans Outlook sur le web :

1. Cliquez **Paramètres** Outlook sur l’icône paramètres web Afficher tous ![ les ](../../media/owa-settings-icon.png) \> **paramètres Outlook courrier** \> **indésirable.**
2. Dans la section **Création de** rapports, vérifiez la valeur : **Demandez-moi avant d’envoyer un rapport.**

   ![Outlook de création de rapports de courrier indésirable sur le web](../../media/owa-junk-email-reporting-options.png)
