---
title: Créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: Apprenez à créer, modifier ou supprimer un groupe de sécurité.
ms.openlocfilehash: 283f1eca7500bfb1d8172657639bbc7cff76906f
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400087"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

Sur la page **groupes** Microsoft 365, vous pouvez créer des groupes de comptes d’utilisateur que vous pouvez utiliser pour attribuer les mêmes autorisations à dans SharePoint Online et CRM Online. Par exemple, un administrateur peut créer un groupe de sécurité pour accorder à un certain groupe de personnes l’accès à un site SharePoint. Seuls les administrateurs de gestion des utilisateurs et globaux sont autorisés à créer, modifier ou supprimer des groupes de sécurité ; Pour plus d’informations sur les rôles d’administrateur, consultez la rubrique [attribution de rôles](../add-users/assign-admin-roles.md)d’administrateur. 
  
En outre, vous pouvez utiliser des [Groupes dans Exchange Online et SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) pour envoyer du courrier électronique ou affecter des autorisations à un groupe d'utilisateurs, ainsi que des [Groupes dans Exchange Online et SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) qui accordent des droits d'utilisateur et un accès aux sites et aux collections de sites. 
  
> [!IMPORTANT]
>  Vous prévoyez d'utiliser des boîtes aux lettres de site ? Tous les utilisateurs ajoutés à un site SharePoint via un groupe de sécurité plutôt qu'individuellement ne peuvent utiliser la boîte aux lettres de site qu'à partir de SharePoint. Ils n'auront pas accès à la boîte aux lettres de site à partir d'Outlook. Pour plus d’informations, consultez la rubrique [utiliser des groupes Microsoft 365 à la place des boîtes aux lettres de site](https://support.office.com/article/737d6b1f-67cc-41fe-8db8-f2d09dd1673b.aspx). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>Gérer les groupes de sécurité dans le centre d’administration

### <a name="add-a-security-group"></a>Ajouter un groupe de sécurité

1. Dans le centre d’administration Microsoft 365, accédez à **la page groupes de**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes</a> .
  
2. Dans la page **groupes** , sélectionnez **Ajouter un groupe**.
    
3. Dans la page **choisir un type de groupe** , choisissez **sécurité**. 
    
4. Suivez les étapes pour terminer la création du groupe. 
 
### <a name="add-members-to-a-security-group"></a>Ajouter des membres à un groupe de sécurité

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.
    
1. Sélectionnez le nom du groupe de sécurité sur la page **groupes** , puis sous l’onglet **membres** , sélectionnez **Afficher tout et gérer les membres**. 
    
2. Dans le volet groupe, sélectionnez **Ajouter des membres** , choisissez la personne dans la liste ou tapez le nom de la personne que vous souhaitez ajouter dans la zone de **recherche** , puis sélectionnez **Enregistrer**.
    
    Pour supprimer des membres, sélectionnez le X en regard de leur nom. 
  
::: moniker-end

::: moniker range="o365-germany"

1. Sélectionnez le nom du groupe de sécurité sur la page **groupes** , puis sélectionnez **modifier** en regard de **membres**. 
    
2. Dans le volet groupe, sélectionnez **Ajouter des membres** , choisissez la personne dans la liste ou tapez le nom de la personne que vous souhaitez ajouter dans la zone de **recherche** , puis sélectionnez **Enregistrer**.
    
    Pour supprimer des membres, sélectionnez le X en regard de leur nom. 
  
::: moniker-end

::: moniker range="o365-21vianet"


1. Sélectionnez le nom du groupe de sécurité sur la page **groupes** , puis sélectionnez **modifier** en regard de **membres**. 
    
2. Dans le volet groupe, sélectionnez **Ajouter des membres** , choisissez la personne dans la liste ou tapez le nom de la personne que vous souhaitez ajouter dans la zone de **recherche** , puis sélectionnez **Enregistrer**.
    
    Pour supprimer des membres, sélectionnez le X en regard de leur nom.

::: moniker-end

### <a name="edit-a-security-group"></a>Modifier un groupe de sécurité

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

1. Dans le centre d’administration, accédez à **la page groupes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes</a> .
  
2. Dans la page **groupes** , sélectionnez le nom du groupe. 
    
3. Dans le volet Paramètres, sélectionnez l’onglet **général** ou l’onglet **membres** pour modifier les détails du groupe ou les membres.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à **la page groupes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes</a> .
  
2. Dans la page **groupes** , sélectionnez le nom du groupe. 
    
3. Dans le volet groupe de sécurité, sélectionnez **modifier** en regard de l’onglet **nom** ou **membres** pour modifier les détails ou les membres du groupe.
    
4. Une fois que vous avez apporté des modifications, sélectionnez **Enregistrer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à **la page groupes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes</a> .
  
2. Dans la page **groupes** , sélectionnez le nom du groupe. 
    
3. Dans le volet groupe de sécurité, sélectionnez **modifier** en regard de l’onglet **nom** ou **membres** pour modifier les détails ou les membres du groupe.
    
4. Une fois que vous avez apporté des modifications, sélectionnez **Enregistrer** > **Fermer**.

::: moniker-end


### <a name="delete-a-security-group"></a>Supprimer un groupe de sécurité

1. Dans le centre d’administration, accédez à **la page groupes de**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes</a> .
    
2. Dans la page **groupes** , sélectionnez le nom du groupe. 
    
3. Sélectionnez **supprimer un groupe** (wasetbin Icon), puis confirmez-le en sélectionnant **supprimer**.
    
    Sélectionnez **Fermer** une fois le groupe supprimé. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Groupes dans Exchange Online et SharePoint Online

Si vous souhaitez créer des groupes d’utilisateurs afin de pouvoir leur envoyer des courriers électroniques tous en même temps, vous pouvez le faire dans le centre d’administration Exchange en **Admin** accédant à groupes de \> **Exchange** \> **destinataires** Exchange d’administration \> **Groups**. Ensuite, sélectionnez **nouveau** ![ ajouter ](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png) , puis sélectionnez le type de groupe que vous souhaitez créer : 
  
- **Groupe de distribution**: un groupe de distribution permet de distribuer des messages à un groupe d'utilisateurs. Il est également appelé *groupe de distribution à extension messagerie*, ou liste de *distribution*. Pour plus d'informations, voir [Gestion des groupes de distribution](https://technet.microsoft.com/library/bb124513.aspx).
    
- **Groupe de sécurité**: un groupe de sécurité permet de distribuer des messages à un groupe d'utilisateurs ou d'accorder des autorisations d'accès à des ressources. Ce groupe est également appelé *groupe de sécurité à extension messagerie*. Pour plus d'informations, voir [Gérer les groupes de sécurité à extension de messagerie](https://technet.microsoft.com/library/bb123521.aspx).
    
- **Groupe de distribution dynamique**: type de groupe de distribution dont la liste de destinataires est recalculée chaque fois que vous envoyez un message en fonction des filtres et des conditions définis par vos soins. Pour plus d'informations, reportez-vous à [Gérer des groupes de distribution dynamiques](https://technet.microsoft.com/library/bb123722.aspx).
    
Après avoir créé des groupes de distribution et des groupes de sécurité à extension messagerie dans le centre d’administration Exchange, leurs noms et leurs listes d’utilisateurs apparaissent dans la page **groupes de sécurité** . Vous pouvez supprimer ces groupes aux deux emplacements, mais vous ne pouvez les modifier que dans le Centre d'administration Exchange. Les groupes de distribution dynamique n’apparaissent pas dans la page **groupes de sécurité** . 
  
 Les groupes SharePoint sont générés automatiquement quand vous créez une collection de sites. Les groupes par défaut utilisent les niveaux d'autorisation par défaut dans SharePoint  parfois appelés rôles SharePoint  pour accorder aux utilisateurs des droits et un accès. Pour plus d’informations, voir [groupes SharePoint par défaut dans SharePoint Online](https://docs.microsoft.com/sharepoint/default-sharepoint-groups).
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>En quoi un groupe de sécurité est-il différent des groupes de sécurité que j’ai créés dans SharePoint ?

Les groupes de sécurité peuvent être utilisés avec SharePoint, Exchange, MDM, Windows et bien plus encore. Un groupe de sécurité que vous créez dans SharePoint n’est reconnu que par cette collection de sites SharePoint.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>Dois-je utiliser les groupes de sécurité de mon organisation pour assurer la sécurité ?

Non. Il s’agit simplement d’une autre façon de gérer la sécurité pour votre organisation. Vous pouvez toujours accorder des autorisations utilisateur et l’accès aux sites individuellement. Toutefois, avec les groupes de sécurité, vous pouvez facilement gérer des groupes d’utilisateurs plus importants.
  
## <a name="can-i-send-email-to-a-security-group"></a>Puis-je envoyer des courriers électroniques à un groupe de sécurité ?

Oui. Toutefois, si vous souhaitez utiliser des groupes pour la messagerie et la collaboration, nous vous recommandons de [créer un groupe Microsoft 365 à la](../create-groups/create-groups.md) place. 
  
