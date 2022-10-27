---
title: Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365
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
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: Découvrez comment créer, modifier ou supprimer un groupe de sécurité.
ms.openlocfilehash: f205c300cf094a9368a49a412a312d96e0896352
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68719951"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365

Dans la page **Groupes** Microsoft 365, vous pouvez créer des groupes de comptes d’utilisateur que vous pouvez utiliser pour attribuer les mêmes autorisations dans SharePoint Online et CRM Online. Par exemple, un administrateur peut créer un groupe de sécurité pour accorder à un certain groupe de personnes l’accès à un site SharePoint. Seuls les administrateurs généraux et de gestion des utilisateurs disposent des autorisations nécessaires pour créer, modifier ou supprimer des groupes de sécurité. Pour plus d’informations sur les rôles d’administrateur, consultez [Attribution de rôles d’administrateur](../add-users/assign-admin-roles.md). 
  
En outre, vous pouvez utiliser des [Groupes dans Exchange Online et SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) pour envoyer du courrier électronique ou affecter des autorisations à un groupe d'utilisateurs, ainsi que des [Groupes dans Exchange Online et SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) qui accordent des droits d'utilisateur et un accès aux sites et aux collections de sites. 
  
> [!IMPORTANT]
>  Vous prévoyez d'utiliser des boîtes aux lettres de site ? Tous les utilisateurs ajoutés à un site SharePoint via un groupe de sécurité plutôt qu'individuellement ne peuvent utiliser la boîte aux lettres de site qu'à partir de SharePoint. Ils n'auront pas accès à la boîte aux lettres de site à partir d'Outlook. Pour plus d’informations, consultez [Utiliser Groupes Microsoft 365 plutôt que des boîtes aux lettres de site](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>Gérer les groupes de sécurité dans le centre d’administration

### <a name="add-a-security-group"></a>Ajouter un groupe de sécurité

1. Dans la Centre d'administration Microsoft 365, accédez à la page **Groupes** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Dans la page **Groupes** , sélectionnez **Ajouter un groupe**.
    
3. Dans la page **Choisir un type de groupe** , choisissez **Sécurité**. 
    
4. Suivez les étapes pour terminer la création du groupe. 
 
### <a name="add-members-to-a-security-group"></a>Ajouter des membres à un groupe de sécurité
    
1. Sélectionnez le nom du groupe de sécurité dans la page **Groupes** , puis sous l’onglet **Membres** , sélectionnez **Afficher tout et gérer les membres**. 
    
2. Dans le volet de groupe, sélectionnez **Ajouter des membres** et choisissez la personne dans la liste ou tapez le nom de la personne que vous souhaitez ajouter dans la zone **De recherche** , puis sélectionnez **Enregistrer**.
    
    Pour supprimer des membres, sélectionnez le X en regard de leur nom. 
  
### <a name="edit-a-security-group"></a>Modifier un groupe de sécurité

1. Dans le Centre d’administration, accédez à la page **Groupes** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">.</a>
  
2. Dans la page **Groupes** , sélectionnez le nom du groupe. 
    
3. Dans le volet paramètres, sélectionnez l’onglet **Général** ou **l’onglet Membres** pour modifier les détails du groupe ou les membres.

### <a name="delete-a-security-group"></a>Supprimer un groupe de sécurité

1. Dans le Centre d’administration, accédez à la page **Groupes** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">.</a>
    
2. Dans la page **Groupes** , sélectionnez le nom du groupe. 
    
3. Sélectionnez **Supprimer le groupe** (icône de wasetbin), puis confirmez en sélectionnant **Supprimer**.
    
    Sélectionnez **Fermer** une fois le groupe supprimé. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Groupes dans Exchange Online et SharePoint Online

Si vous souhaitez créer des groupes d’utilisateurs afin de pouvoir leur envoyer des e-mails en même temps, vous pouvez le faire dans le Centre d’administration Exchange en accédant à **Administration** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**Groupes**</a> de **destinataires** \> **Exchange**\>. Ensuite, sélectionnez **Nouveau**![complément,](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png) puis sélectionnez le type de groupe que vous souhaitez créer : 
  
- **Groupe de distribution**: un groupe de distribution permet de distribuer des messages à un groupe d'utilisateurs. Il est également appelé groupe de  *distribution* à extension messagerie, ou  *liste de distribution*. Pour plus d'informations, voir [Gestion des groupes de distribution](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).
    
- **Groupe de sécurité**: un groupe de sécurité permet de distribuer des messages à un groupe d'utilisateurs ou d'accorder des autorisations d'accès à des ressources. Ce groupe est également appelé *groupe de sécurité à extension messagerie*. Pour plus d'informations, voir [Gérer les groupes de sécurité à extension de messagerie](/Exchange/recipients/mail-enabled-security-groups).
    
- **Groupe de distribution dynamique**: type de groupe de distribution dont la liste de destinataires est recalculée chaque fois que vous envoyez un message en fonction des filtres et des conditions définis par vos soins. Pour plus d'informations, reportez-vous à [Gérer des groupes de distribution dynamiques](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups).
    
Une fois que vous avez créé des groupes de distribution et des groupes de sécurité à extension messagerie dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, leurs noms et listes d’utilisateurs apparaissent dans la page **Groupes de sécurité** . Vous pouvez supprimer ces groupes aux deux emplacements, mais vous ne pouvez les modifier que dans le Centre d'administration Exchange. Les groupes de distribution dynamiques n’apparaissent pas dans la page **Groupes de sécurité** . 
  
 Les groupes SharePoint sont générés automatiquement quand vous créez une collection de sites. Les groupes par défaut utilisent les niveaux d'autorisation par défaut dans SharePoint  parfois appelés rôles SharePoint  pour accorder aux utilisateurs des droits et un accès. Pour plus d’informations, consultez [Groupes SharePoint par défaut dans SharePoint Online](/sharepoint/default-sharepoint-groups).
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>En quoi un groupe de sécurité est-il différent des groupes de sécurité que je crée dans SharePoint ?

Les groupes de sécurité peuvent être utilisés avec SharePoint, Exchange, MDM, Windows, etc. Un groupe de sécurité que vous créez dans SharePoint est uniquement reconnu par cette collection de sites SharePoint.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>Dois-je utiliser des groupes de sécurité pour que mon organisation soit sécurisée ?

Non. Il s’agit simplement d’une autre façon de gérer la sécurité de votre organisation. Vous pouvez toujours accorder des autorisations utilisateur et l’accès aux sites individuellement. Toutefois, avec les groupes de sécurité, vous pouvez facilement gérer des groupes d’utilisateurs plus importants.
  
## <a name="can-i-send-email-to-a-security-group"></a>Puis-je envoyer un e-mail à un groupe de sécurité ?

Oui. Toutefois, si vous souhaitez utiliser des groupes pour la messagerie électronique et la collaboration, nous vous recommandons de [créer un groupe Microsoft 365](../create-groups/create-groups.md) à la place. 

## <a name="related-content"></a>Contenu associé

[Créer un groupe dans le Centre d'administration Microsoft 365](../create-groups/create-groups.md) (article)\
[Explication des Groupes Microsoft 365 à vos utilisateurs](../create-groups/explain-groups-knowledge-worker.md) (article)\
[Gérer un groupe dans le Centre d'administration Microsoft 365](../create-groups/manage-groups.md) (article)