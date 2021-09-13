---
title: Ajouter ou supprimer des membres de Microsoft 365 groupes
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
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
ms.openlocfilehash: 7eaa74a53ac5f27d801d1cf16c9af035c63c68b1
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59176803"
---
# <a name="add-or-remove-members-from-microsoft-365-groups-using-the-admin-center"></a>Ajouter ou supprimer des membres de groupes Microsoft 365 à l’aide du Centre d’administration

Dans Microsoft 365, les membres du groupe créent généralement leurs propres groupes, s’ajoutent aux groupes qu’ils souhaitent rejoindre ou sont invités par les propriétaires du groupe. Si la propriété du groupe change ou si vous déterminez qu’un membre doit être ajouté ou supprimé, en tant qu’administrateur, vous pouvez également effectuer cette modification. Seul un administrateur général, un administrateur Exchange, un administrateur de groupes ou un administrateur utilisateur peut apporter ces modifications. [Qu’est-ce qu Microsoft 365 groupe de travail ?](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

> [!TIP]
> Si vous n’êtes pas un administrateur, vous pouvez ajouter [ou supprimer](https://support.microsoft.com/office/3b650f4a-5c9b-4f94-a1bb-0cca4b1091de)des membres à l’aide Outlook .
  
## <a name="add-a-member-to-a-group-in-the-admin-center"></a>Ajouter un membre à un groupe dans le Centre d’administration

1. Dans le Centre d’administration, allez à la page [**Groupes**](https://admin.microsoft.com/Adminportal/Home?#/groups) actifs.  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres,** sélectionnez Afficher **tout** et gérer les membres, puis **sélectionnez Ajouter des membres.**

4. Recherchez ou sélectionnez le nom du membre que vous voulez ajouter.

5. Sélectionnez **Enregistrer**.

## <a name="add-a-group-to-a-member-in-the-admin-center"></a>Ajouter un groupe à un membre dans le Centre d’administration

1. Dans le Centre d’administration, allez à la page [**Utilisateurs**](https://admin.microsoft.com/Adminportal/Home?#/users) actifs.  

2. Cliquez sur un utilisateur.

3. Dans le volet d’informations, sous **l’onglet** Compte, sélectionnez Gérer les **groupes.**

4. Recherchez ou sélectionnez le nom du groupe que vous souhaitez ajouter.

5. Sélectionnez **Enregistrer**.

## <a name="remove-a-member-from-a-group-in-the-admin-center"></a>Supprimer un membre d’un groupe dans le Centre d’administration

> [!NOTE]
> Lorsque vous supprimez un membre d’un groupe privé, il faut 5 minutes pour que la personne soit bloquée du groupe.

1. Dans le Centre d’administration, allez à la page [**Groupes**](https://admin.microsoft.com/Adminportal/Home?#/groups) actifs.  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres,** **sélectionnez Afficher tout et gérer les membres.**

4. En de côté du membre que vous souhaitez supprimer, sélectionnez le X.

5. Sélectionnez **Enregistrer** pour supprimer le membre.

## <a name="manage-group-owner-status"></a>Gérer l’état du propriétaire du groupe

Par défaut, la personne qui a créé le groupe en est le propriétaire. Un groupe possède souvent plusieurs propriétaires pour le support ou d'autres raisons. Les membres peuvent être promus au statut de propriétaire et les propriétaires peuvent être rétrogradés au statut de membre.
  
### <a name="promote-a-member-to-owner-status-in-the-admin-center"></a>Promouvoir un membre au statut de propriétaire dans le Centre d’administration

1. Dans le Centre d’administration, allez à la page [**Groupes**](https://admin.microsoft.com/Adminportal/Home?#/groups) actifs.  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres,** sélectionnez **Afficher tout et gérer les propriétaires.**

4. Sélectionnez **Ajouter des propriétaires.**

5. Cochez la case en regard du nom du membre que vous souhaitez ajouter.

6. Sélectionnez **Enregistrer,** puis **Fermez.**

### <a name="remove-owner-status-in-the-admin-center"></a>Supprimer l’état du propriétaire dans le Centre d’administration

1. Dans le Centre d’administration, allez à la page [**Groupes**](https://admin.microsoft.com/Adminportal/Home?#/groups) actifs.  

2. Cliquez sur un nom de groupe.

3. Dans le volet d’informations, sous l’onglet **Membres,** sélectionnez **Afficher tout et gérer les propriétaires.**

4. Sélectionnez le X à côté du nom du propriétaire.

5. Sélectionnez **Enregistrer**.

## <a name="next-steps"></a>Étapes suivantes

- [Gérer les groupes dynamiquement dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal): voir la section « Comment puis-je gérer l'appartenance à un groupe dynamiquement ? »

- Pour ajouter des centaines ou des milliers d’utilisateurs à des groupes, utilisez [add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks).

- [Attribuer un nouveau propriétaire à un groupe orphelin](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732)

## <a name="related-content"></a>Contenu associé

[Mettre à niveau les listes de distribution Microsoft 365 groupes dans Outlook](../manage/upgrade-distribution-lists.md) (article)\
[Pourquoi mettre à niveau vos listes de distribution vers des groupes dans Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188) (article)\
[Gérer l’accès invité dans Microsoft 365 groupes de travail](manage-guest-access-in-groups.md) (article)\
[Gérer Microsoft 365 groupes](../../enterprise/manage-microsoft-365-groups-with-powershell.md)avec PowerShell : cet article vous présente les cmdlets clés et fournit des exemples (article)\
[Microsoft 365 de noms de groupes](../../solutions/groups-naming-policy.md) (article)