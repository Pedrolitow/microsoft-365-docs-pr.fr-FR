---
title: Restaurer un utilisateur
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
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
description: Découvrez comment restaurer des comptes d’utilisateurs supprimés et toutes les données associées.
ms.openlocfilehash: 27b3f4a0077b5ef0dcfaef1dbe5019a5d69652f2
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44387000"
---
# <a name="restore-a-user"></a>Restaurer un utilisateur

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end
   
Lorsque vous restaurez un compte d'utilisateur dans les 30 jours après sa suppression, celui-ci et toutes les données associées sont restaurés. L'utilisateur peut se connecter avec le même compte professionnel ou scolaire. Sa boîte aux lettres est entièrement restaurée. Pour déterminer le temps restant avant qu'un compte d'utilisateur spécifique ne puisse plus être restauré, [contactez-nous](../contact-support-for-business-products.md).
  
Voici quelques conseils :
  
- Assurez-vous que les licences sont disponibles pour les affecter au compte.
    
- Si votre entreprise utilise Active Directory, consultez [Comment résoudre les problèmes liés aux comptes d'utilisateurs supprimés dans Office 365](https://support.microsoft.com/kb/2619308) pour obtenir des instructions sur la restauration d'un compte d'utilisateur. 
    
## <a name="restore-one-or-more-user-accounts"></a>Restaurer un ou plusieurs comptes d'utilisateur

Pour effectuer ces étapes, vous devez être un administrateur général Microsoft 365 ou un administrateur de gestion des utilisateurs. 
  
 
::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à **la page utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=848041), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=850627), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

2. Sur la page **utilisateurs supprimés** , sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **restaurer**.
    
 
3. Suivez les invites pour définir le mot de passe, puis sélectionnez **restaurer**.
    
4. Si l’utilisateur est correctement restauré, sélectionnez **Envoyer un message électronique et fermer**. Si vous rencontrez un conflit de noms ou d'adresses de proxy, consultez les instructions ci-dessous pour savoir comment restaurer ces comptes.
    
Une fois que vous avez restauré un utilisateur, vérifiez que son mot de passe a changé et que vous le suivez.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Restaurer un utilisateur présentant un conflit de noms d'utilisateur
<a name="RestoreUserNameConflict"> </a>

Un conflit de noms d'utilisateur survient lorsque vous supprimez un compte d'utilisateur, créez un nouveau avec le même nom (pour le même utilisateur ou un autre portant le même nom), puis tentez de restaurer le compte supprimé.
  
Pour résoudre ce problème, vous pouvez soit remplacer le compte d'utilisateur actif par celui que vous restaurez, soit attribuer un autre nom au compte restauré, afin que les deux comptes ne se servent plus du même nom d'utilisateur. Voici comment procéder.
  

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à **la page utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .

::: moniker-end

::: moniker range="o365-germany"

1. Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=848041), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=850627), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

  
2. Sur la page **utilisateurs supprimés** , sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **restaurer**.
    
    > [!NOTE]
    > Lorsque la restauration de deux ou plusieurs utilisateurs échoue, un message d'erreur vous en avertit. Dans ce cas, consultez le journal pour identifier les utilisateurs qui n'ont pas été restaurés, puis procédez de nouveau à la restauration des comptes, un par un. 
  
3. Suivez les invites pour définir le mot de passe et sélectionnez **restaurer**.
    
4. Un message indiquant qu'un problème s'est produit lors de la restauration du compte s'affiche. Effectuez l'une des opérations suivantes :
    
  - Annulez la restauration et renommez l'utilisateur actif. Essayez d'effectuer la restauration de nouveau.
    
  - OU, tapez une nouvelle adresse de messagerie principale pour l’utilisateur et sélectionnez **restaurer**.
    
5. Examinez les résultats, puis sélectionnez **Fermer**.
    
## <a name="restore-a-user-that-has-a-proxy-address-conflict"></a>Restaurer un utilisateur présentant un conflit d’adresses de proxy

Un conflit d'adresses proxy survient lorsque vous supprimez un compte d'utilisateur contenant une adresse proxy, attribuez cette adresse à un autre compte, puis tentez de restaurer le compte supprimé. Suivez les étapes ci-dessous pour résoudre ce problème.
  
Pour ce faire, vous devez disposer des [autorisations d’administrateur](about-admin-roles.md) dans Microsoft 365. 
  

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à **la page utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés</a> .

::: moniker-end

::: moniker range="o365-germany"

Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=848041), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au [Centre d’administration](https://go.microsoft.com/fwlink/p/?linkid=850627), puis sélectionnez **utilisateurs** \> **supprimés**.

::: moniker-end

2. Sur la page **Utilisateurs supprimés**, sélectionnez l'utilisateur à restaurer, puis **Restaurer**. 
    
3. Sur la page **restaurer** , suivez les instructions permettant de définir le mot de passe et sélectionnez **restaurer**. Toutes les adresses proxy en conflit sont supprimées automatiquement de l'utilisateur que vous restaurez.
    
4. Examinez les résultats, puis sélectionnez **Fermer**.

## <a name="related-articles"></a>Articles connexes

[Supprimer un utilisateur](delete-a-user.md)
  
