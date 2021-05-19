---
title: Modifier un nom d’utilisateur et une adresse de messagerie
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
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
description: "Apprenez comment un administrateur global Microsoft 365 peut modifier l'adresse électronique et le nom d'affichage d'un utilisateur lorsque son nom change. "
ms.openlocfilehash: 2614e0ae53e5ff1cf08ded384e7470cc5967e682
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52535985"
---
# <a name="change-a-user-name-and-email-address"></a>Modifier un nom d’utilisateur et une adresse de messagerie

Vous devrez peut-être modifier l’adresse de messagerie et le nom complet d’une personne si, par exemple, elle se marie et change son nom.

Regardez une courte vidéo sur la modification de l’adresse de courrier d’un utilisateur. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

Vous devez être un [administrateur général](about-admin-roles.md) pour effectuer ces étapes. 

## <a name="change-a-users-email-address"></a>Modifier l’adresse de courrier d’un utilisateur

::: moniker range="o365-worldwide"
 
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer le nom d’utilisateur**.
    
3. Dans la première case, tapez la première partie de la nouvelle adresse e-mail. Si vous avez ajouté votre propre domaine à Microsoft 365, choisissez le domaine pour le nouvel alias de messagerie en utilisant la liste déroulante. 

4. Sélectionnez **Enregistrer les modifications**.

   
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Dans la première case, tapez la première partie de la nouvelle adresse e-mail. Si vous avez ajouté votre propre domaine à Microsoft 365, vous pouvez choisir le domaine pour le nouvel alias de messagerie en utilisant la liste déroulante.

4. Sélectionnez **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Dans la première case, tapez la première partie de la nouvelle adresse e-mail. Si vous avez ajouté votre propre domaine à Microsoft 365, vous pouvez choisir le domaine pour le nouvel alias de messagerie en utilisant la liste déroulante.

4. Sélectionnez **Enregistrer**.

::: moniker-end

> [!IMPORTANT]
> IMPORTANT : Si vous recevez un message d’erreur, consultez la rubrique [Résolution des messages d’erreur](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Définition de l’adresse de courrier principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les alias de courrier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
   > [!IMPORTANT]
   > IMPORTANT : l’option Définir comme principale n’apparaît pas si vous avez acheté Microsoft 365 auprès de GoDaddy ou d’un autre service partenaire qui fournit une console de gestion. Au lieu de cela, connectez-vous à la console de gestion de GoDaddy ou du partenaire pour définir l’alias principal. 
   >  
   > De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
   - Cette modification peut prendre du temps.
  
   - Son nouveau nom d’utilisateur. Elle en aura besoin pour se connecter à Microsoft 365.
    
   - Si cette personne utilise Skype Entreprise Online, elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

   - Si cette personne utilise OneDrive, l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, elle aura sans doute besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.    
  
   - Si son mot de passe change aussi, elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.
  
::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
   > [!IMPORTANT]
   > IMPORTANT : l’option Définir comme principale n’apparaît pas si vous avez acheté Microsoft 365 auprès de GoDaddy ou d’un autre service partenaire qui fournit une console de gestion. Au lieu de cela, connectez-vous à la console de gestion de GoDaddy ou du partenaire pour définir l’alias principal. 
   > 
   > De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
   - L’application de cette modification peut prendre un certain temps.
  
   - Son nouveau nom d'utilisateur. Elle en aura besoin pour se connecter à Microsoft 365.
    
   - Si elle utilise Skype Entreprise Online, indiquez-lui qu'elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et qu'elle devra également demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

   - Si cette personne utilise OneDrive, indiquez-lui que l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, il se peut qu’elle ait besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.    
  
   - Si son mot de passe change, signalez-lui qu’elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de **Nom d’utilisateur/E-mail**, sélectionnez **Modifier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne. 
    
   > [!IMPORTANT]
   > IMPORTANT : l’option Définir comme principale n’apparaît pas si vous avez acheté Microsoft 365 auprès de GoDaddy ou d’un autre service partenaire qui fournit une console de gestion. Au lieu de cela, connectez-vous à la console de gestion de GoDaddy ou du partenaire pour définir l’alias principal. 
   >  
   > De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.
  
4. Un avertissement jaune de grande taille s’affiche, indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.
    
5. Communiquez les informations suivantes à la personne :
 
   - L’application de cette modification peut prendre un certain temps.
  
   - Son nouveau nom d'utilisateur. Elle en aura besoin pour se connecter à Microsoft 365.
    
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

L'application de cette modification dans tous les services peut prendre jusqu'à 24 heures. Une fois la modification appliquée, la personne devra se connecter à Outlook, à Skype Entreprise et à SharePoint avec son nom d'utilisateur mis à jour.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.  

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de la zone **Informations de contact**, sélectionnez **Modifier**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

   Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

L'application de cette modification dans tous les services peut prendre jusqu'à 24 heures. Une fois la modification appliquée, la personne devra se connecter à Outlook, à Skype Entreprise et à SharePoint avec son nom d'utilisateur mis à jour. Vous devez donc en informer celui-ci.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>. 

2. Sélectionnez l’utilisateur. Dans le volet du menu volant, en regard de la zone **Informations de contact**, sélectionnez **Modifier**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

   Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

L'application de cette modification dans tous les services peut prendre jusqu'à 24 heures. Une fois la modification appliquée, la personne devra se connecter à Outlook, à Skype Entreprise et à SharePoint avec son nom d'utilisateur mis à jour. Vous devez donc en informer celui-ci.

::: moniker-end

## <a name="resolve-error-messages"></a>Résolution des messages d'erreur

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>« Impossible de trouver un paramètre correspondant au nom "EmailAddresses" »

Si le message d’erreur « **Impossible de trouver un paramètre correspondant au nom ’EmailAddresses** » s’affiche, cela signifie qu’il faut un peu plus de temps pour configurer votre client, ou votre domaine personnalisé si vous venez d’en ajouter un. Le processus de configuration peut prendre jusqu’à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le [support](../../business-video/get-help-support.md) et demandez-lui d’effectuer une synchronisation complète pour vous.
  
### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>«Nous sommes désolés, l'utilisateur n'a pas pu être édité. Vérifiez les informations de l'utilisateur et réessayez»

Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez.** Cela signifie que vous n’êtes pas un administrateur général et que vous n’êtes pas autorisé à modifier le nom de l’utilisateur. Recherchez l'administrateur global au sein de votre entreprise et demandez-lui d'apporter la modification.


## <a name="what-to-do-with-old-email-addresses"></a>Procédure à suivre avec les anciennes adresses de courrier

L’ancienne adresse e-mail principale d’une personne est conservée en tant qu’adresse e-mail supplémentaire. **Nous vous conseillons vivement de ne pas supprimer l’ancienne adresse de courrier.**
  
Certains continueront sans doute à envoyer des e-mails à l’ancienne adresse de la personne. Le fait de la supprimer risque d’entraîner la génération de notifications d’échec de remise. Microsoft l’achemine automatiquement vers la nouvelle adresse. De plus, évitez de réutiliser d’anciennes adresses e-mail SMTP et de les appliquer aux nouveaux comptes. Cela peut également provoquer la génération de notifications d’échec de remise ou la remise à une boîte aux lettres inattendue.
   
## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Que se passe-t-il si le carnet d’adresses en mode hors connexion d’une personne ne parvient pas à se synchroniser avec la liste d’adresses globale ?

Si une personne utilise Exchange Online ou si son compte est lié à l’environnement Exchange local de votre organisation, vous risquez de rencontrer cette erreur lorsque vous essayez de modifier un nom d’utilisateur et une adresse de messagerie : « Cet utilisateur est synchronisé avec votre environnement Active Directory local. Certains détails peuvent uniquement être modifiés via votre environnement Active Directory local. »
  
Cela est dû à l'adresse MOERA (Microsoft Online Email Routing Address). L'adresse MOERA est construite à partir de l'attribut _userPrincipalName_ de la personne dans Active Directory et est automatiquement attribuée au compte cloud lors de la synchronisation initiale. Une fois attribuée, elle ne peut plus être modifiée ou supprimée dans Microsoft 365. Vous pouvez ensuite modifier le nom d'utilisateur dans l'annuaire Active Directory, mais cela ne modifie pas l'adresse MOERA et vous risquez de rencontrer des problèmes lors de l'affichage du nom nouvellement modifié dans la liste d'adresses globale. 
  
Pour résoudre ce problème, connectez-vous au [module Azure Active Directory pour PowerShell]( https://go.microsoft.com/fwlink/?LinkId=823193) avec vos informations d’identification d’administrateur Microsoft 365. et utilisez la syntaxe suivante : 
  
```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> Cela a pour effet de modifier l'attribut **userPrincipalName** de la personne et n'a aucun effet sur son adresse de courrier Microsoft Online Email Routing Address (MOERA). Nous vous conseillons toutefois de faire correspondre l'UPN de connexion de la personne avec son adresse SMTP principale. 
  
Pour découvrir comment modifier le nom d'utilisateur de quelqu'un dans Active Directory, dans Windows Server 2003 et version ultérieure, voir [Renommer un compte d'utilisateur](/previous-versions/windows/it-pro/windows-server-2003/cc772952(v=ws.10)).
  
## <a name="related-content"></a>Contenu associé

[ Administrateurs : Réinitialiser un mot de passe pour un ou plusieurs utilisateurs (article)](reset-passwords.md)
  
[Ajouter une autre adresse email à un utilisateur (article)](../email/add-another-email-alias-for-a-user.md)

[Créer une boîte aux lettres ](../email/create-a-shared-mailbox.md)partagée (article)