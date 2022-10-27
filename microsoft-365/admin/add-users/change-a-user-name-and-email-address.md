---
title: Modifier un nom d’utilisateur et une adresse de messagerie
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb5ac074-e203-4e1f-9843-b9d1a3e03297
description: Découvrez comment un administrateur général Microsoft 365 peut modifier l’adresse e-mail et le nom complet d’un utilisateur lorsque son nom change.
ms.openlocfilehash: b1770f4749815c74eaa8b909642fac73f1d72a3b
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68722085"
---
# <a name="change-a-user-name-and-email-address"></a>Modifier un nom d’utilisateur et une adresse de messagerie

Consultez [l’aide Microsoft 365 pour les petites entreprises](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Vous devrez peut-être modifier l’adresse de messagerie et le nom complet d’une personne si, par exemple, elle se marie et change son nom.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="watch-change-a-users-name-or-email-address"></a>Regardez : modifier le nom ou l’adresse de courrier d’un utilisateur

Regardez cette vidéo ainsi que d’autres sur notre [Chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198016).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc]

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.
1. Sélectionnez l’utilisateur dans la liste des utilisateurs actifs.
1. Sélectionnez **Gérer les informations de contact**.
1. Modifiez le nom complet, puis sélectionnez **Enregistrer les modifications**.

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un[administrateur général](about-admin-roles.md) pour effectuer ces étapes.

## <a name="change-a-users-email-address"></a>Modifier l’adresse de courrier d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

1. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer le nom d’utilisateur**.

1. In the first box, type the first part of the new email address. If you added your own domain to Microsoft 365, choose the domain for the new email alias by using the drop-down list. [Learn how to add a domain](../setup/add-domain.md).

1. Sélectionnez **Enregistrer les modifications**.

> [!IMPORTANT]
> IMPORTANT : Si vous recevez un message d’erreur, consultez la rubrique [Résolution des messages d’erreur](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Définition de l’adresse de courrier principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les alias de courrier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne.

   > [!IMPORTANT]
   > You won't see this option to Set as Primary if you purchased Microsoft 365 from GoDaddy or another Partner service that provides a management console. Instead, sign in to the GoDaddy / partner's management console to set the primary alias.
   >
   > De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.

4. You'll see a big yellow warning that you're about to change the person's sign-in information. Select **Save**, then **Close**.

5. Communiquez les informations suivantes à la personne :

   - Cette modification peut prendre du temps.

   - Their new username. They'll need it to sign in to Microsoft 365.

   - Si cette personne utilise Skype Entreprise Online, elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

   - Si cette personne utilise OneDrive, l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, elle aura sans doute besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.

   - Si son mot de passe change aussi, elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.

## <a name="change-a-users-display-name"></a>Modifier le nom d’affichage d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les informations de contact**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

   Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

It might take up to 24 hours for this change to take effect across all services. After the change has taken effect, the person will have to sign in to Outlook, Skype for Business and SharePoint with their updated username.

## <a name="resolve-error-messages"></a>Résolution des messages d'erreur

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>« Impossible de trouver un paramètre correspondant au nom "EmailAddresses" »

If you get the error message " **A parameter cannot be found that matches parameter name 'EmailAddresses**" it means that it's taking a bit longer to finish setting up your tenant, or your custom domain if you recently added one. The setup process can take up to 4 hours to complete. Wait a while so the setup process has time to finish, and then try again. If the problem persists, call [support](../../business-video/get-help-support.md) and ask them to do a full sync for you.

### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>"We're sorry, the user couldn't be edited. Review the user information and try again"

If you get the error message " **We're sorry, the user couldn't be edited. Review the user information and try again**." it means you aren't a global admin and you don't have permissions to change the user name. Find the global admin in your business and ask them to make the change.

## <a name="what-to-do-with-old-email-addresses"></a>Procédure à suivre avec les anciennes adresses de courrier

A person's previous primary email address is retained as an additional email address. **We strongly recommend that you don't remove the old email address.**

Some people might continue to send email to the person's old email address and deleting it may result in NDR failures. Microsoft automatically routes it to the new one. Also, do not reuse old SMTP email addresses and apply them to new accounts. This can also cause NDR failures or delivery to an unintended mailbox.

## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Que se passe-t-il si le carnet d’adresses en mode hors connexion d’une personne ne parvient pas à se synchroniser avec la liste d’adresses globale ?

If they are using Exchange Online or if their account is linked with your organization's on-premises Exchange environment, you might see this error when you try to change a username and email address: "This user is synchronized with your local Active Directory. Some details can be edited only through your local Active Directory."

This is due to the Microsoft Online Email Routing Address (MOERA). The MOERA is constructed from the person's  _userPrincipalName_ attribute in Active Directory and is automatically assigned to the cloud account during the initial sync and once created, it cannot be modified or removed in Microsoft 365. You can subsequently change the username in the Active Directory, but it doesn't change the MOERA and you may run into issues displaying the newly changed name in the Global Address List.

To fix this, log in to the [Azure Active Directory Module for PowerShell](https://go.microsoft.com/fwlink/?LinkId=823193) with your Microsoft 365 administrator credentials. and use the following syntax:

```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> This changes the person's **userPrincipalName** attribute and has no bearing on their Microsoft Online Email Routing Address (MOERA) email address. It is best practice, however, to have the person's logon UPN match their primary SMTP address.

Pour découvrir comment modifier le nom d'utilisateur de quelqu'un dans Active Directory, dans Windows Server 2003 et version ultérieure, voir [Renommer un compte d'utilisateur](/previous-versions/windows/it-pro/windows-server-2003/cc772952(v=ws.10)).

## <a name="related-content"></a>Contenu associé

[Ajouter un domaine](../setup/add-domain.md)
[Admins : réinitialiser un mot de passe pour un ou plusieurs utilisateurs](reset-passwords.md)
[Ajouter une autre adresse e-mail à un utilisateur](../email/add-another-email-alias-for-a-user.md)
[Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md)
