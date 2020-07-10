---
title: Modifier un nom d’utilisateur et une adresse de messagerie
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb5ac074-e203-4e1f-9843-b9d1a3e03297
description: 'Découvrez comment un administrateur général peut modifier l’adresse de messagerie et le nom complet d’un utilisateur. '
ms.openlocfilehash: fedc1532bfec246392180d386a6960dbb08bd137
ms.sourcegitcommit: 5b769f74bcc76ac8d38aad815d1728824783cd9f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "45079712"
---
# <a name="change-a-user-name-and-email-address"></a>Modifier un nom d’utilisateur et une adresse de messagerie

Vous devrez peut-être modifier l’adresse de messagerie et le nom complet d’une personne si, par exemple, elle se marie et change son nom.

Regardez une courte vidéo sur la modification de l’adresse de courrier d’un utilisateur. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

## <a name="change-a-users-email-address"></a>Modifier l’adresse de courrier d’un utilisateur

Vous devez être un [administrateur général](about-admin-roles.md) pour effectuer ces étapes. 

::: moniker range="o365-worldwide"
 
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer le nom d’utilisateur**.
    
3. Dans la première zone, tapez la première partie de la nouvelle adresse de courrier. Si vous avez ajouté votre domaine à Microsoft 365, vous pouvez choisir le domaine du nouvel alias de messagerie dans la liste déroulante. 

4. Sélectionnez **Enregistrer les modifications**.

   
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Dans la première zone, tapez la première partie de la nouvelle adresse de courrier. Si vous avez ajouté votre domaine à Microsoft 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante.

4. Sélectionnez **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Dans la première zone, tapez la première partie de la nouvelle adresse de courrier. Si vous avez ajouté votre domaine à Microsoft 365, vous pouvez choisir le domaine du nouvel alias d'e-mail dans la liste déroulante.

4. Sélectionnez **Enregistrer**.

::: moniker-end

**IMPORTANT** : Si vous recevez un message d’erreur, consultez la rubrique [Résolution des messages d’erreur](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Définition de l’adresse de courrier principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les alias de courrier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
    **IMPORTANT**: You won't see this option to Set as Primary if you purchased Microsoft 365 from GoDaddy or another Partner service that provides a management console. Instead, sign in to the GoDaddy / partner's management console to set the primary alias. 
    
    De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
  - Cette modification peut prendre du temps.
  
  - Their new username. They'll need it to sign in to Microsoft 365.
    
  - Si cette personne utilise Skype Entreprise Online, elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

  - Si cette personne utilise OneDrive, l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, elle aura sans doute besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.    
  
  - Si son mot de passe change aussi, elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.
  
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
    **IMPORTANT**: You won't see this option to Set as Primary if you purchased Microsoft 365 from GoDaddy or another Partner service that provides a management console. Instead, sign in to the GoDaddy / partner's management console to set the primary alias. 
    
    De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
  - L’application de cette modification peut prendre un certain temps.
  
  - What their new username is. They'll need it to sign in to Microsoft 365.
    
  - Si elle utilise Skype Entreprise Online, indiquez-lui qu'elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et qu'elle devra également demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

  - Si cette personne utilise OneDrive, indiquez-lui que l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, il se peut qu’elle ait besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.    
  
  - Si son mot de passe change, signalez-lui qu’elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
    **IMPORTANT**: You won't see this option to Set as Primary if you purchased Microsoft 365 from GoDaddy or another Partner service that provides a management console. Instead, sign in to the GoDaddy / partner's management console to set the primary alias. 
    
    De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
  - L’application de cette modification peut prendre un certain temps.
  
  - What their new username is. They'll need it to sign in to Microsoft 365.
    
  - Si elle utilise Skype Entreprise Online, indiquez-lui qu'elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et qu'elle devra également demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

  - Si cette personne utilise OneDrive, indiquez-lui que l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, il se peut qu’elle ait besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.    
  
  - Si son mot de passe change, signalez-lui qu’elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.

::: moniker-end
  
## <a name="change-a-users-display-name"></a>Modifier le nom d’affichage d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les informations de contact**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

    Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

It might take up to 24 hours for this change to take effect across all services. After the change has taken effect, the person will have to sign in to Outlook, Skype for Business and SharePoint with their updated username.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de la zone **Informations de contact**, sélectionnez **Modifier**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

    Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

It might take up to 24 hours for this change to take effect across all services. After the change has taken effect, the person will have to sign in to Outlook, Skype for Business and SharePoint with their updated username, so be sure to tell them about this change.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de la zone **Informations de contact**, sélectionnez **Modifier**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

    Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

It might take up to 24 hours for this change to take effect across all services. After the change has taken effect, the person will have to sign in to Outlook, Skype for Business and SharePoint with their updated username, so be sure to tell them about this change.

::: moniker-end

## <a name="resolve-error-messages"></a>Résolution des messages d'erreur

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>« Impossible de trouver un paramètre correspondant au nom "EmailAddresses" »

If you get the error message " **A parameter cannot be found that matches parameter name 'EmailAddresses**" it means that it's taking a bit longer to finish setting up your tenant, or your custom domain if you recently added one. The setup process can take up to 4 hours to complete. Wait a while so the set up process has time to finish, and then try again. If the problem persists, call [support](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products) and ask them to do a full sync for you.
  
### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>« Impossible de modifier l’utilisateur. Vérifiez les informations sur l’utilisateur et réessayez. »

Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez.** Cela signifie que vous n’êtes pas un administrateur général et que vous n’êtes pas autorisé à modifier le nom de l’utilisateur. Recherchez l'administrateur global au sein de votre entreprise et demandez-lui d'apporter la modification.


## <a name="what-to-do-with-old-email-addresses"></a>Procédure à suivre avec les anciennes adresses de courrier

A person's previous primary email address is retained as an additional email address. **We strongly recommend that you don't remove the old email address.**
  
Some people might continue to send email to the person's old email address and deleting it may result in NDR failures. Microsoft automatically routes it to the new one. Also, do not reuse old SMTP email addresses and apply them to new accounts. This can also cause NDR failures or delivery to an unintended mailbox.
   
## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Que se passe-t-il si le carnet d’adresses en mode hors connexion d’une personne ne parvient pas à se synchroniser avec la liste d’adresses globale ?

If they are using Exchange Online or if their account is linked with your organization's on-premises Exchange environment, you might see this error when you try to change a username and email address: "This user is synchronized with your local Active Directory. Some details can be edited only through your local Active Directory."
  
This is due to the Microsoft Online Email Routing Address (MOERA). The MOERA is constructed from the person's  _userPrincipalName_ attribute in Active Directory and is automatically assigned to the cloud account during the initial sync and once created, it cannot be modified or removed in Microsoft 365. You can subsequently change the username in the Active Directory, but it doesn't change the MOERA and you may run into issues displaying the newly changed name in the Global Address List. 
  
Pour résoudre ce problème, connectez-vous au [module Azure Active Directory pour PowerShell]( https://go.microsoft.com/fwlink/?LinkId=823193) avec vos informations d’identification d’administrateur Microsoft 365. et utilisez la syntaxe suivante : 
  
```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> Cela a pour effet de modifier l'attribut **userPrincipalName** de la personne et n'a aucun effet sur son adresse de courrier Microsoft Online Email Routing Address (MOERA). Nous vous conseillons toutefois de faire correspondre l'UPN de connexion de la personne avec son adresse SMTP principale. 
  
Pour découvrir comment modifier le nom d'utilisateur de quelqu'un dans Active Directory, dans Windows Server 2003 et version ultérieure, voir [Renommer un compte d'utilisateur](https://go.microsoft.com/fwlink/?LinkId=809091).
  
## <a name="related-articles"></a>Articles connexes

[Administrateurs : réinitialiser le mot de passe d'un ou de plusieurs utilisateurs](reset-passwords.md)
  
[Ajouter une autre adresse de courrier à un utilisateur](../email/add-another-email-alias-for-a-user.md)
