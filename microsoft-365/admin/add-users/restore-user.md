---
title: Restaurer un utilisateur
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
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: Dans les 30 jours suivant la suppression d’un compte d’utilisateur, vous pouvez restaurer le compte et toutes les données, et l’utilisateur peut se connecter avec le même compte.
ms.openlocfilehash: 126cb9ca4a9b74445aad2cc3f7cec4f6feab8eb7
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68200096"
---
# <a name="restore-a-user-in-the-microsoft-365-admin-center"></a>Restaurer un utilisateur dans le Centre d'administration Microsoft 365
   
When you restore a user account within 30 days after deleting it, the account and all associated data are restored. The user can sign in with the same work or school account. Their mailbox will be fully restored. To find out how much time remains before a specific user account can no longer be restored, [contact us](../../business-video/get-help-support.md).
  
Voici quelques conseils :
  
- Assurez-vous que les licences sont disponibles pour l’attribution au compte.
    
- Si votre entreprise utilise Active Directory, pour obtenir des instructions sur la restauration d’un compte d’utilisateur, consultez [Comment résoudre les problèmes de comptes d’utilisateur supprimés dans Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Restaurer un ou plusieurs comptes d'utilisateur

Pour effectuer ces étapes, vous devez être administrateur général microsoft 365 ou administrateur de gestion des utilisateurs. 

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .

2. Dans la page **Utilisateurs supprimés** , sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **Restaurer**.
    
3. Suivez les invites pour définir leur mot de passe, puis sélectionnez **Restaurer**.
    
4. Si l’utilisateur est correctement restauré, sélectionnez **Envoyer un e-mail et fermez**. Si vous rencontrez un conflit de noms ou d'adresses de proxy, consultez les instructions ci-dessous pour savoir comment restaurer ces comptes.
    
Une fois que vous avez restauré un utilisateur, assurez-vous de l’informer que son mot de passe a changé et de le suivre.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Restaurer un utilisateur présentant un conflit de noms d'utilisateur

Un conflit de noms d'utilisateur survient lorsque vous supprimez un compte d'utilisateur, créez un nouveau avec le même nom (pour le même utilisateur ou un autre portant le même nom), puis tentez de restaurer le compte supprimé.
  
To fix this, replace the active user account with the one that you are restoring. Or, assign a different user name to the account that you are restoring so that there aren't two accounts with the same user name. Here are the steps.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .
  
2. Dans la page **Utilisateurs supprimés** , sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **Restaurer**.
    
    > [!NOTE]
    > If two or more users fail to be restored, an error message advises you that the restore operation failed for some users. View the log to see which users were not restored, and then restore the failed accounts one at a time. 
  
3. Suivez les invites pour définir le mot de passe, puis sélectionnez **Restaurer**.
    
4. Un message indiquant qu'un problème s'est produit lors de la restauration du compte s'affiche. Effectuez l'une des opérations suivantes :
    
     - Annulez la restauration et renommez l'utilisateur actif. Essayez d'effectuer la restauration de nouveau.
    
     - OU, tapez une nouvelle adresse e-mail principale pour l’utilisateur et sélectionnez **Restaurer**.
    
5. Examinez les résultats, puis sélectionnez **Fermer**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Restaurer un utilisateur présentant un conflit d’adresses de proxy

A proxy address conflict occurs when you delete a user account that contains a proxy address, assign the same proxy address to another account, and then try to restore the deleted account. Follow the steps below to fix this issue.
  
Pour ce faire, vous devez disposer [d’autorisations d’administrateur](about-admin-roles.md) dans Microsoft 365. 

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .

2. Sur la page **Utilisateurs supprimés**, sélectionnez l'utilisateur à restaurer, puis **Restaurer**. 
    
3. Dans la page **Restaurer** , suivez les instructions pour définir le mot de passe et sélectionnez **Restaurer**. Toutes les adresses proxy en conflit sont supprimées automatiquement de l'utilisateur que vous restaurez.
    
4. Examinez les résultats, puis sélectionnez **Fermer**.

## <a name="related-content"></a>Contenu associé

[Supprimer un utilisateur](delete-a-user.md) (article)\
[Attribuer des rôles d’administrateur](assign-admin-roles.md) (vidéo)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)
