---
title: Ajouter ou supprimer des membres de groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
ms.assetid: e186d224-a324-4afa-8300-0e4fc0c3000a
description: Découvrez comment ajouter un membre à un groupe, supprimer un membre du groupe et gérer l’état du propriétaire du groupe dans le Centre d'administration Microsoft 365.
ms.openlocfilehash: 89a180bddb5965def4fd5ea763f266a8a289ed4c
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720457"
---
# <a name="add-or-remove-members-from-microsoft-365-groups-using-the-admin-center"></a>Ajouter ou supprimer des membres de groupes Microsoft 365 à l’aide du Centre d’administration

Dans Microsoft 365, les membres du groupe créent généralement leurs propres groupes, s’ajoutent aux groupes qu’ils souhaitent rejoindre ou sont invités par des propriétaires de groupe. Si la propriété du groupe change, ou si vous déterminez qu’un membre doit être ajouté ou supprimé, en tant qu’administrateur, vous pouvez également apporter cette modification. Seul un administrateur général, un administrateur Exchange, un administrateur de groupes ou un administrateur d’utilisateurs peut apporter ces modifications. [Qu’est-ce qu’un groupe Microsoft 365 ?](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

> [!TIP]
> Si vous n’êtes pas administrateur, vous pouvez [ajouter ou supprimer des membres à l’aide d’Outlook](https://support.microsoft.com/office/3b650f4a-5c9b-4f94-a1bb-0cca4b1091de).
  
## <a name="add-a-member-to-a-group-in-the-admin-center"></a>Ajouter un membre à un groupe dans le Centre d’administration

1. Dans le Centre d’administration, accédez à la page [**Groupes actifs**](https://admin.microsoft.com/Adminportal/Home?#/groups) .  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres** , sélectionnez **Afficher tout et gérer les membres**, puis **sélectionnez Ajouter des membres**.

4. Recherchez ou sélectionnez le nom du membre que vous voulez ajouter.

5. Sélectionnez **Enregistrer**.

## <a name="add-a-group-to-a-member-in-the-admin-center"></a>Ajouter un groupe à un membre dans le Centre d’administration

1. Dans le Centre d’administration, accédez à la page [**Utilisateurs actifs**](https://admin.microsoft.com/Adminportal/Home?#/users) .  

2. Cliquez sur un utilisateur.

3. Dans le volet d’informations, sous l’onglet **Compte** , sélectionnez **Gérer les groupes**.

4. Recherchez ou sélectionnez le nom du groupe que vous souhaitez ajouter.

5. Sélectionnez **Enregistrer**.

## <a name="remove-a-member-from-a-group-in-the-admin-center"></a>Supprimer un membre d’un groupe dans le Centre d’administration

> [!NOTE]
> Lorsque vous supprimez un membre d’un groupe privé, le blocage du groupe prend 5 minutes.

1. Dans le Centre d’administration, accédez à la page [**Groupes actifs**](https://admin.microsoft.com/Adminportal/Home?#/groups) .  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres** , sélectionnez **Afficher tout et gérer les membres**.

4. En regard du membre que vous souhaitez supprimer, sélectionnez le X.

5. Sélectionnez **Enregistrer** pour supprimer le membre.

## <a name="manage-group-owner-status"></a>Gérer l’état du propriétaire du groupe

By default, the person who created the group is the group owner. Often a group will have multiple owners for backup support or other reasons. Members can be promoted to owner status and owners can be demoted to member status.
  
### <a name="promote-a-member-to-owner-status-in-the-admin-center"></a>Promouvoir un membre au statut de propriétaire dans le Centre d’administration

1. Dans le Centre d’administration, accédez à la page [**Groupes actifs**](https://admin.microsoft.com/Adminportal/Home?#/groups) .  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres** , sélectionnez **Afficher tout et gérer les propriétaires**.

4. Sélectionnez **Ajouter des propriétaires**.

5. Cochez la case en regard du nom du membre que vous souhaitez ajouter.

6. Sélectionnez **Enregistrer**, puis **Fermer**.

### <a name="remove-owner-status-in-the-admin-center"></a>Supprimer l’état du propriétaire dans le Centre d’administration

1. Dans le Centre d’administration, accédez à la page [**Groupes actifs**](https://admin.microsoft.com/Adminportal/Home?#/groups) .  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres** , sélectionnez **Afficher tout et gérer les propriétaires**.

4. Sélectionnez le X en regard du nom du propriétaire.

5. Sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

- [Gérer les groupes dynamiquement dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal): voir la section « Comment puis-je gérer l'appartenance à un groupe dynamiquement ? »

- Pour ajouter des centaines ou des milliers d’utilisateurs à des groupes, utilisez [add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks).

- [Attribuer un nouveau propriétaire à un groupe orphelin](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732)

## <a name="related-content"></a>Contenu associé

[Mettre à niveau des listes de distribution vers des groupes Microsoft 365 dans Outlook](../manage/upgrade-distribution-lists.md) (article)\
[Pourquoi mettre à niveau vos listes de distribution vers des groupes dans Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188) (article)\
[Gérer l’accès invité dans les groupes Microsoft 365](manage-guest-access-in-groups.md) (article)\
[Gérer des groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) : cet article présente les applets de commande clés et fournit des exemples (article)\
[Stratégie de nommage des groupes Microsoft 365](../../solutions/groups-naming-policy.md) (article)