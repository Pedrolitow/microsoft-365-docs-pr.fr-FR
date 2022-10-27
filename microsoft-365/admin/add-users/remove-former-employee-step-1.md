---
title: 'Étape 1 : Empêcher un ancien employé de se connecter et bloquer l’accès aux services Microsoft 365'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
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
ms.openlocfilehash: 6f59c4295f98164c152e2b42ddf08a07d8bc9eee
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68721777"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Étape 1 : Empêcher un ancien employé de se connecter et bloquer l’accès aux services Microsoft 365

Si vous devez immédiatement empêcher l’accès à la connexion d’un utilisateur, vous devez réinitialiser son mot de passe. Dans cette étape, forcez la déconnexion de l’utilisateur de Microsoft 365.

> [!NOTE]
> Vous devez être administrateur général pour lancer la déconnexion d’autres administrateurs. Pour les utilisateurs non administrateurs, vous pouvez utiliser un administrateur d’utilisateurs ou un utilisateur du support technique pour effectuer cette action. [En savoir plus sur les rôles Administration](about-admin-roles.md)

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Cochez la case en regard du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe**.
3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser**. (Ne les envoyez pas.)
4. Sélectionnez le nom de l’utilisateur pour accéder au volet des propriétés, puis, sous l’onglet **Compte** , sélectionnez **Se déconnecter de toutes les sessions**.

Dans l’heure ou après avoir quitté la page Microsoft 365 actuelle sur laquelle ils se trouvent, ils sont invités à se reconnecter. Un jeton d’accès étant valide pendant une heure, la chronologie dépend de la durée restante sur ce jeton et du fait qu’ils quittent leur page web actuelle.
  
> [!IMPORTANT]
> Si l’utilisateur est dans Outlook sur le web, en cliquant simplement dans sa boîte aux lettres, il peut ne pas être expulsé immédiatement. Dès qu’ils sélectionnent une autre vignette, telle que OneDrive, ou actualisent leur navigateur, la déconnexion est lancée.
  
Pour utiliser PowerShell pour déconnecter immédiatement un utilisateur, consultez l’applet de commande [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken) .
  
Pour plus d'informations sur le temps nécessaire pour supprimer l'accès d'un utilisateur au courrier électronique, voir [Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Bloquer l’accès d’un ancien employé aux services Microsoft 365

> [!IMPORTANT]
 > L’application du blocage d’un compte peut prendre jusqu’à 24 heures. Si vous devez immédiatement empêcher l’accès à la connexion d’un utilisateur, suivez les étapes ci-dessus et réinitialisez son mot de passe.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sous le nom de l’utilisateur, sélectionnez le symbole **Bloquer cet utilisateur**.
3. Sélectionnez **Bloquer la connexion de l’utilisateur**, puis sélectionnez **Enregistrer**.

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Bloquer l'accès d'un ancien employé aux courriers (Exchange Online)

Si vous avez un e-mail dans le cadre de votre abonnement Microsoft 365, connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> et suivez ces étapes pour empêcher votre ancien employé d’accéder à ses e-mails.
  
1. Accédez au Centre d’administration Exchange > <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">boîtes aux lettres</a> **destinataires**\>.
1. Sélectionnez la boîte aux lettres utilisateur dans la liste, puis, dans le *volet d’informations* (à droite), sélectionnez **Gérer les paramètres des applications de messagerie** sous **Email applications**. **Désactivez** le curseur pour toutes les options ; **Mobile (Exchange ActiveSync),** **Outlook sur le web**, **Outlook Desktop (MAPI),** **services web Exchange**, **POP3** et **IMAP**.
1. Cliquez sur **Enregistrer**.

## <a name="related-content"></a>Contenu associé

[Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center) (article)\

[Restaurer un utilisateur](restore-user.md) (article)
