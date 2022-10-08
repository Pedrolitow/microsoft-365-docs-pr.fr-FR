---
title: Préparation d’un domaine non routable pour la synchronisation d’annuaires
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- scotvorg
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Découvrez ce qu’il faut faire si vous avez un domaine non routable associé à vos comptes d’utilisateur locaux avant de les synchroniser avec votre locataire Microsoft 365.
ms.openlocfilehash: e88daebce6ae11ec8741a49894e15509471a5701
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68189734"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>Préparation d’un domaine non routable pour la synchronisation d’annuaires

Lorsque vous synchronisez votre annuaire local avec Microsoft 365, vous devez disposer d’un domaine vérifié dans Azure Active Directory (Azure AD). Seuls les noms d’utilisateur principal (UPN) associés au domaine Active Directory local Domain Services (AD DS) sont synchronisés. Toutefois, tout UPN qui contient un domaine non routable, tel que « .local » (exemple : billa@contoso.local), est synchronisé avec un domaine .onmicrosoft.com (exemple : billa@contoso.onmicrosoft.com). 

Si vous utilisez actuellement un domaine « .local » pour vos comptes d’utilisateur dans AD DS, il est recommandé de les modifier pour utiliser un domaine vérifié, tel que billa@contoso.com, afin de synchroniser correctement avec votre domaine Microsoft 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>Que se passe-t-il si je n’ai qu’un domaine local « .local » ?

Vous utilisez Azure AD Connect pour synchroniser votre service AD DS avec le locataire Azure AD de votre locataire Microsoft 365. Pour plus d’informations, consultez [Intégration de vos identités locales à Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD Connect synchronise l’UPN et le mot de passe de vos utilisateurs afin que les utilisateurs puissent se connecter avec les mêmes informations d’identification qu’ils utilisent localement. Toutefois, Azure AD Connect synchronise uniquement les utilisateurs avec les domaines vérifiés par Microsoft 365. Cela signifie que le domaine est également vérifié par Azure AD, car les identités Microsoft 365 sont gérées par Azure AD. En d’autres termes, le domaine doit être un domaine Internet valide (par exemple, .com, .org, .net, .us). Si votre service AD DS interne utilise uniquement un domaine non routable (par exemple, « .local »), cela ne peut pas correspondre au domaine vérifié que vous avez pour votre locataire Microsoft 365. Vous pouvez résoudre ce problème en modifiant votre domaine principal dans votre AD DS local ou en ajoutant un ou plusieurs suffixes UPN.
  
### <a name="change-your-primary-domain"></a>Modifier votre domaine principal

Remplacez votre domaine principal par un domaine que vous avez vérifié dans Microsoft 365, par exemple, contoso.com. Chaque utilisateur disposant du domaine contoso.local est ensuite mis à jour pour contoso.com. Il s’agit toutefois d’un processus impliqué et une solution plus facile est décrite dans la section suivante.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>Ajouter des suffixes UPN et y mettre à jour vos utilisateurs

Vous pouvez résoudre le problème « .local » en inscrivant de nouveaux suffixes UPN dans AD DS pour qu’ils correspondent au domaine (ou domaines) que vous avez vérifié dans Microsoft 365. Après avoir inscrit le nouveau suffixe, vous mettez à jour les upN utilisateur pour remplacer « .local » par le nouveau nom de domaine, par exemple, afin qu’un compte d’utilisateur ressemble à billa@contoso.com.
  
Une fois que vous avez mis à jour les UPN pour utiliser le domaine vérifié, vous êtes prêt à synchroniser votre AD DS local avec Microsoft 365.
  
#### <a name="step-1-add-the-new-upn-suffix"></a>Étape 1 : Ajouter le nouveau suffixe UPN
  
1. Sur le contrôleur de domaine AD DS, dans le Gestionnaire de serveur choisissez Domaines **et approbations Active Directory** **Tools**\>.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez **sur Touche Windows + R** pour ouvrir la boîte de dialogue **Exécuter** , puis tapez Domain.msc, puis choisissez **OK**.
    
    ![Choisissez Domaines et approbations Active Directory.](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. Dans la fenêtre **Domaines et approbations Active Directory** , cliquez avec le bouton droit sur **Domaines et approbations Active Directory**, puis choisissez **Propriétés**.
    
    ![Cliquez avec le bouton droit sur Domaines et approbations Active Directory, puis choisissez Propriétés.](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. Sous l’onglet **Suffixes UPN** , dans la zone **Alternative UPN Suffixes** , tapez votre nouveau suffixe UPN ou suffixes, puis choisissez **Ajouter** \> **appliquer**.
    
    ![Ajoutez un nouveau suffixe UPN.](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    Choisissez **OK** lorsque vous avez terminé d’ajouter des suffixes. 
    
 #### <a name="step-2-change-the-upn-suffix-for-existing-users"></a>Étape 2 : Modifier le suffixe UPN pour les utilisateurs existants
  
1. Sur le contrôleur de domaine AD DS, dans le Gestionnaire de serveur choisissez **Outils** \> **Utilisateurs et ordinateurs Active Directory**.
    
    **Ou, si vous n’avez pas Windows Server 2012**
    
    Appuyez **sur Touche Windows + R** pour ouvrir la boîte de dialogue **Exécuter**, puis tapez Dsa.msc, puis cliquez sur **OK**.
    
2. Sélectionnez un utilisateur, cliquez avec le bouton droit, puis choisissez **Propriétés**.
    
3. Sous l’onglet **Compte** , dans la liste déroulante suffixe UPN, choisissez le nouveau suffixe UPN, puis **choisissez OK**.
    
    ![Ajoutez un nouveau suffixe UPN pour un utilisateur.](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. Effectuez ces étapes pour chaque utilisateur.
    
   
### <a name="use-powershell-to-change-the-upn-suffix-for-all-of-your-users"></a>Utiliser PowerShell pour modifier le suffixe UPN pour tous vos utilisateurs

Si vous avez de nombreux comptes d’utilisateur à mettre à jour, il est plus facile d’utiliser PowerShell. L’exemple suivant utilise les applets de commande [Get-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617241(v=technet.10)) et [Set-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617215(v=technet.10)) pour remplacer tous les suffixes contoso.local par contoso.com dans AD DS. 

Par exemple, vous pouvez exécuter les commandes PowerShell suivantes pour mettre à jour tous les suffixes contoso.local pour contoso.com :
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

Consultez le [module Windows PowerShell Active Directory](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617195(v=technet.10)) pour en savoir plus sur l’utilisation de Windows PowerShell dans AD DS.
