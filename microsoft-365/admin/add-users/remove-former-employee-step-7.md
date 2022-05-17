---
title: 'Étape 7 : Supprimer le compte d’utilisateur d’un ancien employé'
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Une fois que vous avez enregistré et accédé à toutes les données utilisateur d’un ancien employé, vous pouvez supprimer le compte de l’ancien employé dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: d6e53dd8d14add9383e3eff9d3c1d90a5087ec45
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436264"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>Étape 7 : Supprimer le compte d’utilisateur d’un ancien employé

Une fois que vous avez enregistré et consulté les données utilisateur de l'ancien employé, vous pouvez supprimer le compte de l'ancien employé.

> [!IMPORTANT]
> Ne supprimez pas le compte si vous avez configuré le transfert de courrier ou si vous l'avez converti en boîte aux lettres partagée. Les deux ont besoin du compte pour ancrer le transfert ou la boîte aux lettres partagée.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé à supprimer.
3. Sous le nom de l’utilisateur, **sélectionnez Supprimer l’utilisateur**. Choisissez les options souhaitées pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur**. Si vous avez déjà donné à un autre utilisateur l’accès à l’e-mail de cet utilisateur et OneDrive, vous n’avez pas besoin de le refaire ici.

Lorsque vous supprimez un utilisateur, le compte devient inactif pendant 30 jours environ. Vous disposez de cette durée pour restaurer le compte avant sa suppression définitive.

## <a name="watch-delete-a-former-employees-user-account"></a>Regarder : Supprimer le compte d’utilisateur d’un ancien employé

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>Votre organisation utilise Active Directory ?

Si votre organisation synchronise les comptes d’utilisateur avec Microsoft 365 à partir d’un environnement Active Directory local, vous devez supprimer et restaurer ces comptes d’utilisateur dans votre service Active Directory local. Vous ne pouvez pas les supprimer et les restaurer dans Office 365.

Pour savoir comment supprimer et restaurer un compte d’utilisateur dans Active Directory, consultez [Supprimer un compte d’utilisateur](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
Si vous utilisez Azure Active Directory, consultez l’applet de commande PowerShell [Remove-MsolUser](/powershell/module/msonline/remove-msoluser).
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé

Voici les informations sur la suppression de l'accès d'un employé au courrier électronique (Exchange).

<br>

****

|Ce que vous pouvez faire|Procédure à suivre|
|:-----|:-----|
|Clôturer une session (par exemple, Outlook sur le web, Outlook, Exchange Active Sync, etc.) et forcer à ouvrir une nouvelle session|Réinitialiser le mot de passe|
|Clôturer une session et bloquer les sessions suivantes (pour tous les protocoles)|Désactivez le compte. Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) : <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|Clôturer la session pour un protocole particulier (par exemple, ActiveSync)|Désactivez le protocole. Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) : <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

Les opérations ci-dessus peuvent être effectuées à trois endroits :
  
<br>

****

|Si vous clôturez la session ici|Temps nécessaire|
|---|---|
|Dans le centre d'administration Exchange ou à l'aide de PowerShell|Le délai prévu est de moins de 30 minutes|
|Dans le centre d'administration Azure Active Directory|Le délai prévu est de 60 minutes|
|Dans un environnement local|Le délai prévu est de 3 heures ou plus|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>Comment obtenir une réponse plus rapide à une demande de clôture de compte

**Plus rapide**: utilisez le centre d'administration Exchange (avec PowerShell) ou le centre d'administration Azure Active Directory. Dans un environnement local, la synchronisation de la modification via DirSync peut prendre plusieurs heures.
  
**Plus rapide pour un utilisateur ayant une présence locale et dans le centre de données Exchange**: clôturez la session via le centre d'administration Azure Active Directory/Exchange ET apportez la modification aussi dans l'environnement local. À défaut, la modification dans le centre d'administration Azure Active Directory/Exchange est remplacée par DirSync.
  
## <a name="related-content"></a>Contenu connexe

[Restaurer un utilisateur](restore-user.md) (article)

[Réinitialiser les mots de passe](reset-passwords.md) (article)
