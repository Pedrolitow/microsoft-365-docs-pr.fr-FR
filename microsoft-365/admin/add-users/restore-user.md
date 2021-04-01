---
title: Restaurer un utilisateur
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
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: Découvrez comment restaurer les comptes d’utilisateur supprimés et toutes les données associées.
ms.openlocfilehash: 75e664c68dec13b857e4bd308d49e5b58d5edfc8
ms.sourcegitcommit: d4604e333507c6f57d5bf327531a241b649052de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "51471012"
---
# <a name="restore-a-user"></a>Restaurer un utilisateur
   
Lorsque vous restaurez un compte d'utilisateur dans les 30 jours après sa suppression, celui-ci et toutes les données associées sont restaurés. L'utilisateur peut se connecter avec le même compte professionnel ou scolaire. Sa boîte aux lettres est entièrement restaurée. Pour déterminer le temps restant avant qu'un compte d'utilisateur spécifique ne puisse plus être restauré, [contactez-nous](../contact-support-for-business-products.md).
  
Voici quelques conseils :
  
- Assurez-vous que les licences peuvent être assignées au compte.
    
- Si votre entreprise utilise Active Directory, consultez [Comment résoudre les problèmes liés aux comptes d'utilisateurs supprimés dans Office 365](https://support.microsoft.com/kb/2619308) pour obtenir des instructions sur la restauration d'un compte d'utilisateur. 
    
## <a name="restore-one-or-more-user-accounts"></a>Restaurer un ou plusieurs comptes d'utilisateur

Vous devez être administrateur global Microsoft 365 ou administrateur de gestion des utilisateurs pour suivre ces étapes. 
  
 
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>

::: moniker-end

::: moniker range="o365-germany"

1. Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=848041)and then select **Users** \> **Deleted users**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=850627)and then select **Users** \> **Deleted users**.

::: moniker-end

2. Dans la page **Utilisateurs** supprimés, sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **Restaurer.**
    
 
3. Suivez les invites pour définir leur mot de passe, puis sélectionnez **Restaurer**.
    
4. Si l’utilisateur est correctement restauré, sélectionnez **Envoyer un e-mail et fermez.** Si vous rencontrez un conflit de noms ou d'adresses de proxy, consultez les instructions ci-dessous pour savoir comment restaurer ces comptes.
    
Une fois que vous avez restauré un utilisateur, assurez-vous de l’informer que son mot de passe a été modifié et de le suivre.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Restaurer un utilisateur présentant un conflit de noms d'utilisateur
<a name="RestoreUserNameConflict"> </a>

Un conflit de noms d'utilisateur survient lorsque vous supprimez un compte d'utilisateur, créez un nouveau avec le même nom (pour le même utilisateur ou un autre portant le même nom), puis tentez de restaurer le compte supprimé.
  
Pour résoudre ce problème, vous pouvez soit remplacer le compte d'utilisateur actif par celui que vous restaurez, soit attribuer un autre nom au compte restauré, afin que les deux comptes ne se servent plus du même nom d'utilisateur. Voici comment procéder.
  

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>

::: moniker-end

::: moniker range="o365-germany"

1. Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=848041)and then select **Users** \> **Deleted users**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=850627)and then select **Users** \> **Deleted users**.

::: moniker-end

  
2. Dans la page **Utilisateurs** supprimés, sélectionnez les noms des utilisateurs à restaurer, puis sélectionnez **Restaurer.**
    
    > [!NOTE]
    > Lorsque la restauration de deux ou plusieurs utilisateurs échoue, un message d'erreur vous en avertit. Dans ce cas, consultez le journal pour identifier les utilisateurs qui n'ont pas été restaurés, puis procédez de nouveau à la restauration des comptes, un par un. 
  
3. Suivez les invites pour définir le mot de passe et sélectionnez **Restaurer.**
    
4. Un message indiquant qu'un problème s'est produit lors de la restauration du compte s'affiche. Effectuez l'une des opérations suivantes :
    
  - Annulez la restauration et renommez l'utilisateur actif. Essayez d'effectuer la restauration de nouveau.
    
  - OU, tapez une nouvelle adresse de messagerie principale pour l’utilisateur et sélectionnez **Restaurer**.
    
5. Examinez les résultats, puis sélectionnez **Fermer**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Restaurer un utilisateur présentant un conflit d’adresses de proxy

Un conflit d'adresses proxy survient lorsque vous supprimez un compte d'utilisateur contenant une adresse proxy, attribuez cette adresse à un autre compte, puis tentez de restaurer le compte supprimé. Suivez les étapes ci-dessous pour résoudre ce problème.
  
Pour ce [faire, vous devez](about-admin-roles.md) avoir des autorisations d’administrateur dans Microsoft 365. 
  

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>

::: moniker-end

::: moniker range="o365-germany"

Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=848041)and then select **Users** \> **Deleted users**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Go to the [admin center,](https://go.microsoft.com/fwlink/p/?linkid=850627)and then select **Users** \> **Deleted users**.

::: moniker-end

2. Sur la page **Utilisateurs supprimés**, sélectionnez l'utilisateur à restaurer, puis **Restaurer**. 
    
3. Dans la page **Restaurer,** suivez les instructions pour définir le mot de passe et sélectionnez **Restaurer.** Toutes les adresses proxy en conflit sont supprimées automatiquement de l'utilisateur que vous restaurez.
    
4. Examinez les résultats, puis sélectionnez **Fermer**.

## <a name="related-articles"></a>Articles connexes

[Supprimer un utilisateur](delete-a-user.md)
