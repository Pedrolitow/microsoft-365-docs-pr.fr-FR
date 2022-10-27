---
title: Gérer l’accès invité dans les groupes Microsoft 365
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
- admindeeplinkMAC
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Découvrez comment ajouter des invités à un groupe Microsoft 365, afficher les invités et utiliser PowerShell pour contrôler l’accès invité.
ms.openlocfilehash: ce3155371ecead5c6773bd30862a75ae4d5aba17
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720413"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gérer l’accès invité dans les groupes Microsoft 365

Par défaut, l’accès invité pour les groupes Microsoft 365 est activé pour votre organisation. Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité aux groupes pour l’ensemble de leur organisation ou pour des groupes individuels.

Lorsqu’il est activé, les membres du groupe peuvent inviter des invités à un groupe Microsoft 365 via Outlook sur le web. Les invitations sont envoyées au propriétaire du groupe pour approbation.

Une fois approuvé, l’invité est ajouté au répertoire et au groupe.

> [!Note]
> Yammer Entreprise réseaux qui sont en mode natif ou dans la [zone géographique de l’UE](/yammer/manage-security-and-compliance/manage-data-compliance) ne prennent pas en charge les invités réseau.
> Les groupes Yammer connectés Microsoft 365 ne prennent pas en charge l’accès invité, mais vous pouvez créer des groupes externes non connectés dans votre réseau Yammer. Pour obtenir des instructions, consultez [Créer et gérer des groupes externes dans Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) .

L’accès invité dans les groupes est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes sur la configuration du partage invité entre les groupes, SharePoint et Teams, consultez :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer l’accès invité aux groupes

Si vous souhaitez activer ou désactiver l’accès invité dans les groupes, vous pouvez le faire dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**groupes**</a>.

1. Dans le Centre d’administration, accédez à **Afficher tous les** \> **paramètres** \> **Paramètres** De l’organisation, puis sous <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">l’onglet **Services**</a>, sélectionnez **Groupes Microsoft 365**.
  
2. Dans la page **Groupes Microsoft 365**, indiquez si vous souhaitez autoriser les personnes extérieures à votre organisation à accéder aux ressources du groupe ou autoriser les propriétaires de groupe à ajouter des personnes extérieures à votre organisation à des groupes.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Ajouter des invités à un groupe Microsoft 365 à partir du Centre d’administration

Si l’invité existe déjà dans votre annuaire, vous pouvez l’ajouter à vos groupes à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Centre d'administration Microsoft 365</a>. (Les groupes avec appartenance dynamique doivent être [gérés dans Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. Dans le centre d’administration, accédez aux **groupes** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groupes**</a>.
  
2. Sélectionnez le groupe auquel vous souhaitez ajouter l’invité, puis sélectionnez **Afficher tout et gérer les membres** sous l’onglet **Membres** . 
  
3. Sélectionnez **Ajouter des membres**, puis choisissez le nom de l’invité que vous souhaitez ajouter.

4. Sélectionnez **Enregistrer**.

Si vous souhaitez ajouter un invité à l’annuaire directement, vous pouvez [ajouter des utilisateurs Azure Active Directory B2B Collaboration dans le Portail Azure](/azure/active-directory/b2b/add-users-administrator).

Si vous souhaitez modifier les informations d’un invité, vous pouvez [ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="remove-a-guest"></a>Supprimer un invité

Une fois que vous avez terminé de collaborer avec un utilisateur invité, vous pouvez le supprimer et il n’aura plus accès à votre organisation.

1. Dans la Centre d'administration Microsoft 365, développez **Utilisateurs**, puis choisissez <a href="https://go.microsoft.com/fwlink/p/?linkid=2074830" target="_blank">**Utilisateurs invités**</a>.
1. Dans la page **Utilisateurs invités** , choisissez l’utilisateur que vous souhaitez supprimer, puis **choisissez Supprimer un utilisateur**.

Pour supprimer des utilisateurs dans le portail Azure AD, consultez [Supprimer un utilisateur invité et des ressources](/azure/active-directory/b2b/b2b-quickstart-add-guest-users-portal#clean-up-resources).


## <a name="related-content"></a>Contenu associé

[Bloquer les invités d’un groupe spécifique](../../solutions/per-group-guest-access.md) (article)\
[Gérer l’appartenance au groupe dans le Centre d'administration Microsoft 365](add-or-remove-members-from-groups.md) (article)\
[Révisions d’accès Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (article)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (article)
