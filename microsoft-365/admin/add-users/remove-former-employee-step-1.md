---
title: 'Étape 1 : empêcher un ancien employé de se connecter et de bloquer l’accès aux services Microsoft 365'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Les administrateurs généraux peuvent empêcher un ancien employé de se connecter et bloquer son accès aux services Microsoft 365.
ms.openlocfilehash: eec436a182f5e065f445167dea38fe99390ca105
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436644"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Étape 1 : empêcher un ancien employé de se connecter et de bloquer l’accès aux services Microsoft 365

Si vous devez empêcher immédiatement l’accès à la connexion d’un utilisateur, vous devez réinitialiser son mot de passe. Dans cette étape, forcez une déconnexion de l’utilisateur à partir de Microsoft 365.

> [!NOTE]
> Vous devez être un administrateur général pour lancer la déconnexion pour d’autres administrateurs. Pour les utilisateurs non administrateurs, vous pouvez utiliser un administrateur d’utilisateurs ou un utilisateur administrateur du support technique pour effectuer cette action. [En savoir plus sur les rôles d’administrateur](about-admin-roles.md)

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la zone en regard du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe**.
3. Entrez un nouveau mot de passe, puis **sélectionnez Réinitialiser**. (Ne l’envoyez pas à eux.)
4. Sélectionnez le nom de l’utilisateur pour accéder à son volet propriétés, puis sous l’onglet **Compte** , sélectionnez **Se déconnecter de toutes les sessions**.

Dans l’heure - ou après avoir quitté la page Microsoft 365 actuelle sur laquelle ils se trouvent - ils sont invités à se reconnecter. Un jeton d’accès est valide pendant une heure. La chronologie dépend donc du temps restant sur ce jeton et de la sortie de sa page web actuelle.
  
> [!IMPORTANT]
> Si l’utilisateur est dans Outlook sur le web, il suffit de cliquer dans sa boîte aux lettres, il se peut qu’il ne soit pas immédiatement exclu. Dès qu’ils sélectionnent une autre vignette, telle que OneDrive, ou actualisent leur navigateur, la déconnexion est lancée.
  
Pour utiliser PowerShell pour déconnecter immédiatement un utilisateur, consultez l’applet de commande [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Pour plus d'informations sur le temps nécessaire pour supprimer l'accès d'un utilisateur au courrier électronique, voir [Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Bloquer l’accès d’un ancien employé aux services Microsoft 365

> [!IMPORTANT]
 > Le blocage d’un compte peut prendre jusqu’à 24 heures. Si vous devez empêcher immédiatement l’accès à la connexion d’un utilisateur, suivez les étapes ci-dessus et réinitialisez son mot de passe.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sous le nom de l’utilisateur, sélectionnez le symbole **pour Bloquer cet utilisateur**.
3. Sélectionnez **Empêcher l’utilisateur de se connecter**, puis **sélectionnez Enregistrer**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Bloquer l'accès d'un ancien employé aux courriers (Exchange Online)

Si vous avez un e-mail dans le cadre de votre abonnement Microsoft 365, connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> et suivez ces étapes pour empêcher votre ancien employé d’accéder à son courrier électronique.
  
1. Accédez au centre d’administration Exchange > boîtes <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">aux lettres destinataires</a>\>.
1. Sélectionnez la boîte aux lettres de l’utilisateur dans la liste, puis, dans le *volet Détails* (à droite), sélectionnez **Gérer les paramètres des applications de messagerie** sous **Applications** de messagerie. **Désactivez** le curseur pour toutes les options ; **Mobile (Exchange ActiveSync),****Outlook sur le web**, **bureau Outlook (MAPI),** **Exchange services web**, **POP3** et **IMAP**.
1. Cliquez sur **Enregistrer**.

## <a name="related-content"></a>Contenu associé

[Exchange centre d’administration dans Exchange Online](/exchange/exchange-admin-center) (article)\

[Restaurer un utilisateur](restore-user.md) (article)
