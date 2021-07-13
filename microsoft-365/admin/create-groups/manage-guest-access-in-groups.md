---
title: Gérer l’accès invité dans Microsoft 365 groupes
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
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Découvrez comment ajouter des invités à un groupe Microsoft 365, afficher les utilisateurs invités et utiliser PowerShell pour contrôler l’accès invité.
ms.openlocfilehash: 41a42a0b4fc76b71892f758519db56f4c1adc897
ms.sourcegitcommit: 00f001019c653269d85718d410f970887d904304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "53394062"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gérer l’accès invité dans Microsoft 365 groupes

Par défaut, l’accès invité pour Microsoft 365 groupes est désactivé pour votre organisation. Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité à des groupes pour l’ensemble de leur organisation ou pour des groupes individuels.

Lorsqu’il est allumé, les membres du groupe peuvent inviter des utilisateurs invités à un groupe Microsoft 365 via Outlook web. Les invitations sont envoyées au propriétaire du groupe pour approbation.

Une fois approuvé, l’utilisateur invité est ajouté à l’annuaire et au groupe.

> [!Note]
> Yammer Entreprise réseaux qui sont en mode natif ou la région ue ne [sont](/yammer/manage-security-and-compliance/manage-data-compliance) pas en charge les invités réseau.
> Microsoft 365 Les groupes Yammer connectés ne peuvent pas prendre en charge l’accès invité pour le moment, mais vous pouvez créer des groupes externes non connectés dans Yammer réseau. Voir [Créer et gérer des groupes externes dans Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) pour obtenir des instructions.

L’accès invité dans les groupes est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes sur la configuration du partage d’invités entre groupes, SharePoint et Teams, voir :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer l’accès invité des groupes

Si vous souhaitez activer ou désactiver l’accès invité dans les groupes, vous pouvez le faire dans le Centre d’administration Microsoft 365.

1. Dans le Centre d’administration, sélectionnez **Afficher** tous Paramètres l’organisation et sous l’onglet \>  \>  **Services,** **sélectionnez Microsoft 365 groupes.**
  
2. Dans la page **Microsoft 365** groupes, choisissez si vous souhaitez laisser des personnes extérieures à votre organisation accéder aux ressources de groupe ou laisser les propriétaires de groupes ajouter des personnes extérieures à votre organisation à des groupes.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Ajouter des invités à un groupe Microsoft 365 à partir du Centre d’administration

Si l’invité existe déjà dans votre annuaire, vous pouvez l’ajouter à vos groupes à partir du Centre d’administration Microsoft 365. (Les groupes avec appartenance dynamique doivent être [gérés Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. Dans le Centre d’administration, allez à la page   >  **Groupes.**
  
2. Cliquez sur le groupe à qui vous souhaitez ajouter l’invité, puis sélectionnez Afficher **tout et gérer** les membres sous **l’onglet Membres.** 
  
4. Sélectionnez **Ajouter** des membres et choisissez le nom de l’invité que vous souhaitez ajouter.
    
5. Sélectionnez **Enregistrer**.

Si vous souhaitez ajouter un invité directement à l’annuaire, vous pouvez ajouter Azure Active Directory utilisateurs [de collaboration B2B](/azure/active-directory/b2b/add-users-administrator)dans le portail Azure.

Si vous souhaitez modifier les informations d’un invité, vous pouvez ajouter ou mettre à jour les informations de profil d’un utilisateur à [l’aide Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>Contenu associé

[Bloquer les utilisateurs invités d’un groupe spécifique](../../solutions/per-group-guest-access.md) (article)\
[Gérer l’appartenance à un groupe dans le Centre d’administration Microsoft 365](add-or-remove-members-from-groups.md) (article)\
[Azure Active Directory révisions d’accès](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (article)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (article)