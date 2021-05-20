---
title: Gérer l’accès des clients Microsoft 365 groupes
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
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Découvrez comment ajouter des invités à un groupe Microsoft 365, afficher les utilisateurs invités et utiliser PowerShell pour contrôler l’accès des invités.
ms.openlocfilehash: c52f0094e724040b71d5d72cded049fed57e3969
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52571936"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gérer l’accès des clients Microsoft 365 groupes

Par défaut, l’accès des Microsoft 365 groupes est activé pour votre organisation. Les administrateurs peuvent contrôler s’il y a un accès des clients à des groupes pour l’ensemble de leur organisation ou pour des groupes individuels.

Lorsqu’il est activé, les membres du groupe peuvent inviter les utilisateurs invités à un groupe Microsoft 365 par le biais Outlook sur le Web. Des invitations sont envoyées au propriétaire du groupe pour approbation.

Une fois approuvé, l’utilisateur invité est ajouté à l’annuaire et au groupe.

> [!Note]
> Yammer Entreprise réseaux qui sont en mode autochtone ou dans le géo de [l’UE ne soutiennent](/yammer/manage-security-and-compliance/manage-data-compliance) pas les clients du réseau.
> Microsoft 365 Les Yammer groupes de personnes ne supportent pas actuellement l’accès des clients, mais vous pouvez créer des groupes externes non connectés dans votre Yammer réseau. Voir [Créer et gérer des groupes externes dans Yammer pour](/yammer/work-with-external-users/create-and-manage-external-groups) les instructions.

L’accès des invités en groupe est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes pour la mise en place du partage d’invités entre les groupes, SharePoint et Teams, voir :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer l’accès des hôtes des groupes

Si vous souhaitez activer ou désactiver l’accès des invités en groupes, vous pouvez le faire dans le centre d Microsoft 365'administration.

1. Dans le centre d’administration, allez **afficher** \> **tous les paramètres Paramètres** \> **Org** et sur **l’onglet Services,** **sélectionnez Microsoft 365 groupes**.
  
2. Sur la page **Microsoft 365 groupes,** choisissez si vous souhaitez laisser des personnes extérieures à votre organisation accéder aux ressources du groupe ou laisser les propriétaires de groupes ajouter des personnes en dehors de votre organisation à des groupes.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Ajouter des invités à un Microsoft 365 groupe du centre d’administration

Si l’invité existe déjà dans votre répertoire, vous pouvez les ajouter à vos groupes à partir du centre d Microsoft 365'administration. (Les groupes avec des membres dynamiques [doivent être gérés Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. Dans le centre d’administration, rendez-vous sur la page   >  **Groupes Groupes.**
  
2. Cliquez sur le groupe à qui vous souhaitez ajouter l’invité et sélectionnez **Afficher tous et gérer les membres sur** l’onglet Membres.  
  
4. Sélectionnez **Ajouter des** membres et choisissez le nom de l’invité que vous souhaitez ajouter.
    
5. Sélectionnez **Enregistrer**.

Si vous souhaitez ajouter directement un invité à l’annuaire, vous pouvez [ajouter Azure Active Directory utilisateurs de la collaboration B2B dans le portail Azure](/azure/active-directory/b2b/add-users-administrator).

Si vous souhaitez modifier l’une ou l’autre des informations d’un invité, vous [pouvez ajouter ou mettre à jour les informations de profil d’un utilisateur à l’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>Contenu connexe

[Bloquer les utilisateurs invités d’un groupe](../../solutions/per-group-guest-access.md) spécifique (article)

[Gérer l’adhésion au groupe dans Microsoft 365 centre d’administration](add-or-remove-members-from-groups.md) (article)
  
[Azure Active Directory d’accès (article)](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (article)