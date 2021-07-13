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
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c261e42-5dd1-48b0-845f-2a016d29cfc1
description: Dans les 30 jours suivant la suppression d’un compte d’utilisateur, vous pouvez restaurer le compte et toutes les données, et l’utilisateur peut se connecter avec le même compte.
ms.openlocfilehash: e37f913bcc6a54bdcc1e0f52168fe1aab0c8afdd
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394266"
---
# <a name="restore-a-user"></a>Restaurer un utilisateur
   
Lorsque vous restaurez un compte d'utilisateur dans les 30 jours après sa suppression, celui-ci et toutes les données associées sont restaurés. L'utilisateur peut se connecter avec le même compte professionnel ou scolaire. Sa boîte aux lettres est entièrement restaurée. Pour déterminer le temps restant avant qu'un compte d'utilisateur spécifique ne puisse plus être restauré, [contactez-nous](../../business-video/get-help-support.md).
  
Voici quelques conseils :
  
- Assurez-vous que les licences peuvent être assignées au compte.
    
- Si votre entreprise utilise Active Directory, pour les problèmes de restauration d’un compte d’utilisateur, voir Comment résoudre les problèmes de comptes d’utilisateur [supprimés dans Office 365](/office365/troubleshoot/active-directory/restore-deleted-user-accounts). 
    
## <a name="restore-one-or-more-user-accounts"></a>Restaurer un ou plusieurs comptes d'utilisateur

Vous devez être administrateur Microsoft 365 administrateur global ou administrateur de gestion des utilisateurs pour suivre ces étapes. 

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>

2. Dans la page **Utilisateurs** supprimés, sélectionnez les noms des utilisateurs que vous souhaitez restaurer, puis sélectionnez **Restaurer.**
    
3. Suivez les invites pour définir leur mot de passe, puis sélectionnez **Restaurer**.
    
4. Si l’utilisateur est correctement restauré, sélectionnez **Envoyer un e-mail et fermez.** Si vous rencontrez un conflit de noms ou d'adresses de proxy, consultez les instructions ci-dessous pour savoir comment restaurer ces comptes.
    
Une fois que vous avez restauré un utilisateur, assurez-vous de l’informer que son mot de passe a été modifié et de le suivre.
  
## <a name="restore-a-user-that-has-a-user-name-conflict"></a>Restaurer un utilisateur présentant un conflit de noms d'utilisateur

Un conflit de noms d'utilisateur survient lorsque vous supprimez un compte d'utilisateur, créez un nouveau avec le même nom (pour le même utilisateur ou un autre portant le même nom), puis tentez de restaurer le compte supprimé.
  
Pour résoudre ce problème, vous pouvez soit remplacer le compte d'utilisateur actif par celui que vous restaurez, soit attribuer un autre nom au compte restauré, afin que les deux comptes ne se servent plus du même nom d'utilisateur. Voici comment procéder.

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>
  
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
  
Pour ce [faire,](about-admin-roles.md) vous devez Microsoft 365 administrateur. 

1. Dans le Centre d’administration, allez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2071581" target="_blank">supprimés.</a>

2. Sur la page **Utilisateurs supprimés**, sélectionnez l'utilisateur à restaurer, puis **Restaurer**. 
    
3. Dans la page **Restaurer,** suivez les instructions pour définir le mot de passe et sélectionnez **Restaurer.** Toutes les adresses proxy en conflit sont supprimées automatiquement de l'utilisateur que vous restaurez.
    
4. Examinez les résultats, puis sélectionnez **Fermer**.

## <a name="related-content"></a>Contenu associé

[Supprimer un utilisateur](delete-a-user.md) (article)\
[Attribuer des rôles d’administrateur](assign-admin-roles.md) (vidéo)\
[Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md) (article)
