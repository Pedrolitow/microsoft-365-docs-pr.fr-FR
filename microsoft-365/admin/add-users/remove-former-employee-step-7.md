---
title: 'Étape 7 : supprimer le compte d’utilisateur d’un ancien employé'
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
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez ces étapes pour supprimer le compte d’utilisateur d’un ancien employé.
ms.openlocfilehash: 0afa9b112919d2668d7553ac5bcf08e664bc1749
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244234"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>Étape 7 : supprimer le compte d’utilisateur d’un ancien employé

Une fois que vous avez enregistré et consulté les données utilisateur de l'ancien employé, vous pouvez supprimer le compte de l'ancien employé.

> [!IMPORTANT]
> Ne supprimez pas le compte si vous avez configuré le transfert de courrier ou si vous l'avez converti en boîte aux lettres partagée. Les deux ont besoin du compte pour ancrer le transfert ou la boîte aux lettres partagée.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé à supprimer.
3. Sous le nom de l’utilisateur, sélectionnez **Supprimer l’utilisateur.** Choisissez les options que vous souhaitez pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur.** Si vous avez déjà accordé à un autre utilisateur l’accès aux e-mails et aux OneDrive de cet utilisateur, vous n’avez pas besoin de le faire à nouveau ici.

Lorsque vous supprimez un utilisateur, le compte devient inactif pendant 30 jours environ. Vous disposez de cette durée pour restaurer le compte avant sa suppression définitive.
  
## <a name="does-your-organization-use-active-directory"></a>Votre organisation utilise Active Directory ?

Si votre organisation synchronise les comptes d’utilisateur avec Microsoft 365 à partir d’un environnement Active Directory local, vous devez supprimer et restaurer ces comptes d’utilisateurs dans votre service Active Directory local. Vous ne pouvez pas les supprimer et les restaurer dans Office 365.

Pour découvrir comment supprimer et restaurer un compte d’utilisateur dans Active Directory, voir [Supprimer un compte d’utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))
  
Si vous utilisez Azure Active Directory, voir l’cmdlet [Remove-MsolUser](https://go.microsoft.com/fwlink/?linkid=842230) PowerShell.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé

Voici les informations sur la suppression de l'accès d'un employé au courrier électronique (Exchange).
  
|||
|:-----|:-----|
|**Ce que vous pouvez faire** <br/> |**Procédure à suivre** <br/> |
|Clôturer une session (par exemple, Outlook sur le web, Outlook, Exchange Active Sync, etc.) et forcer à ouvrir une nouvelle session  <br/> |Réinitialiser le mot de passe  <br/> |
|Clôturer une session et bloquer les sessions suivantes (pour tous les protocoles)  <br/> |Désactivez le compte. Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) :  <br/>  `Set-Mailbox user@contoso.com -AccountDisabled:$true` <br/> |
|Clôturer la session pour un protocole particulier (par exemple, ActiveSync)  <br/> |Désactivez le protocole. Par exemple, (dans le centre d’administration Exchange ou à l’aide de PowerShell) :  <br/>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false` <br/> |

Les opérations ci-dessus peuvent être réalisées à trois endroits :
  
|||
|:-----|:-----|
|**Si vous clôturez la session ici** <br/> |**Temps nécessaire** <br/> |
|Dans le centre d'administration Exchange ou à l'aide de PowerShell  <br/> |Le délai prévu est de moins de 30 minutes  <br/> |
|Dans le centre d'administration Azure Active Directory  <br/> |Le délai prévu est de 60 minutes  <br/> |
|Dans un environnement local  <br/> |Le délai prévu est de 3 heures ou plus  <br/> |

### <a name="how-to-get-fastest-response-for-account-termination"></a>Comment obtenir une réponse plus rapide à une demande de clôture de compte

 **Plus rapide**: utilisez le centre d'administration Exchange (avec PowerShell) ou le centre d'administration Azure Active Directory. Dans un environnement local, la synchronisation de la modification via DirSync peut prendre plusieurs heures.
  
 **Plus rapide pour un utilisateur ayant une présence locale et dans le centre de données Exchange**: clôturez la session via le centre d'administration Azure Active Directory/Exchange ET apportez la modification aussi dans l'environnement local. À défaut, la modification dans le centre d'administration Azure Active Directory/Exchange est remplacée par DirSync.
  
## <a name="related-articles"></a>Articles connexes

[Restaurer un utilisateur](restore-user.md)