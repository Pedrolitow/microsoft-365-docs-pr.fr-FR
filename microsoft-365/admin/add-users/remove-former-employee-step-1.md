---
title: 'Étape 1 : empêcher un employé de se connecter à Microsoft 365'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services.
ms.openlocfilehash: b33f3aa74ebdcf785b75889f5f3263e91b127cdc
ms.sourcegitcommit: aebcdbef52e42f37492a7f780b8b9b2bc0998d5c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2021
ms.locfileid: "59773450"
---
# <a name="step-1---prevent-a-former-employee-from-logging-in-and-block-access-to-microsoft-365-services"></a>Étape 1 : empêcher un ancien employé de se connecter et bloquer l’accès Microsoft 365 services

Si vous devez empêcher immédiatement l’accès à la signature d’un utilisateur, vous devez réinitialiser son mot de passe. Dans cette étape, forcez la sortie de l’utilisateur de Microsoft 365.

> [!NOTE]
> Vous devez être un administrateur général pour lancer la signature pour d’autres administrateurs. Pour les utilisateurs non administrateurs, vous pouvez utiliser un administrateur utilisateur ou un utilisateur d’administrateur du service d’aide pour effectuer cette action. [En savoir plus sur les rôles d’administrateur](about-admin-roles.md)

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la case à côté du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe.**
3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.** (Ne leur envoyez pas de message.)
4. Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Se sortir **de toutes les sessions.**

Dans l’heure qui s’affiche( ou après avoir quitté la page de Microsoft 365 en cours), ils sont invités à se ré-inscrire. Un jeton d’accès est bon pendant une heure, donc la chronologie dépend du temps qui reste sur ce jeton et de la façon dont il quitte la page web actuelle.
  
> [!IMPORTANT]
> Si l’utilisateur est Outlook sur le web, il se peut qu’il ne soit pas immédiatement mis hors de la boîte aux lettres en cliquant dessus. Dès qu’ils sélectionnent une autre vignette, telle que OneDrive, ou actualisent leur navigateur, la signature est lancée.
  
Pour utiliser PowerShell pour décrémenter un utilisateur immédiatement, consultez l’cmdlet [Revoke-AzureADUserAllRefreshToken.](/powershell/module/azuread/revoke-azureaduserallrefreshtoken)
  
Pour plus d'informations sur le temps nécessaire pour supprimer l'accès d'un utilisateur au courrier électronique, voir [Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé](remove-former-employee-step-7.md#what-you-need-to-know-about-terminating-an-employees-email-session).

## <a name="block-a-former-employees-access-to-microsoft-365-services"></a>Bloquer l’accès d’un ancien employé Microsoft 365 services

> [!IMPORTANT]
 > Le blocage d’un compte peut prendre jusqu’à 24 heures. Si vous devez empêcher immédiatement l’accès à la signature d’un utilisateur, suivez les étapes ci-dessus et réinitialisez son mot de passe.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sous le nom de l’utilisateur, sélectionnez le symbole bloquer **cet utilisateur.**
3. Sélectionnez **Bloquer la signature de l’utilisateur,** puis sélectionnez **Enregistrer.**

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Bloquer l'accès d'un ancien employé aux courriers (Exchange Online)

Si vous avez des messages électroniques dans le cadre de votre abonnement Microsoft 365, connectez-vous au Centre d’administration Exchange et suivez ces étapes pour empêcher votre ancien employé d’accéder à son courrier électronique.
  
1. Accédez au <a href="https://admin.exchange.microsoft.com/" target="_blank">Centre d’administration Exchange</a>.
2. Dans le Centre d'administration Exchange, accédez à **Destinataires** \> **Boîtes aux lettres**.
3. Sélectionnez la boîte aux lettres utilisateur dans la liste, puis, dans le volet d’informations *(à* droite), sélectionnez Gérer les **paramètres** des applications de messagerie sous Applications de **messagerie.** Désactiver **le** curseur pour toutes les options ; **Mobile (Exchange ActiveSync)**, **Outlook sur le web**, **Outlook bureau (MAPI)**, **Exchange services web,** **POP3** et **IMAP**.
4. Cliquez sur **Enregistrer**.

## <a name="related-content"></a>Contenu associé

[Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center)

[Restaurer un utilisateur](restore-user.md)
