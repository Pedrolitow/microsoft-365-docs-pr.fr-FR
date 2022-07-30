---
title: Gérer l’accès invité dans les groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: Découvrez comment ajouter des invités à un groupe Microsoft 365, afficher des invités et utiliser PowerShell pour contrôler l’accès invité.
ms.openlocfilehash: 59ec932aea516107f08570f899987c4d619aa66b
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084210"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gérer l’accès invité dans les groupes Microsoft 365

Par défaut, l’accès invité pour les groupes Microsoft 365 est activé pour votre organisation. Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité aux groupes pour l’ensemble de leur organisation ou pour des groupes individuels.

Lorsqu’il est activé, les membres du groupe peuvent inviter des invités à un groupe Microsoft 365 via Outlook sur le web. Les invitations sont envoyées au propriétaire du groupe pour approbation.

Une fois approuvé, l’invité est ajouté au répertoire et au groupe.

> [!Note]
> Yammer Entreprise réseaux en mode natif ou géo [de l’UE](/yammer/manage-security-and-compliance/manage-data-compliance) ne prennent pas en charge les invités réseau.
> Les groupes Yammer connectés à Microsoft 365 ne prennent actuellement pas en charge l’accès invité, mais vous pouvez créer des groupes externes non connectés dans votre réseau Yammer. Pour obtenir des instructions, consultez [Créer et gérer des groupes externes dans Yammer](/yammer/work-with-external-users/create-and-manage-external-groups) .

L’accès invité dans les groupes est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes sur la configuration du partage d’invités entre les groupes, SharePoint et Teams, consultez :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer l’accès invité aux groupes

Si vous souhaitez activer ou désactiver l’accès invité dans des groupes, vous pouvez le faire dans les <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**groupes**</a>.

1. Dans le centre d’administration, accédez à **Afficher tous les** \> **paramètres** \> de **l’organisation des paramètres** et, sous l’onglet <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>, sélectionnez **Groupes Microsoft 365**.
  
2. Dans la page **Groupes Microsoft 365**, choisissez si vous souhaitez autoriser les personnes extérieures à votre organisation à accéder aux ressources de groupe ou autoriser les propriétaires de groupes à ajouter des personnes extérieures à votre organisation à des groupes.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Ajouter des invités à un groupe Microsoft 365 à partir du Centre d’administration

Si l’invité existe déjà dans votre répertoire, vous pouvez l’ajouter à vos groupes à partir du <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Centre d'administration Microsoft 365</a>. (Les groupes avec appartenance dynamique doivent être [gérés dans Azure Active Directory](/azure/active-directory/enterprise-users/groups-create-rule).)
  
1. Dans le centre d’administration, accédez aux **groupes** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Cliquez sur le groupe auquel vous souhaitez ajouter l’invité, puis sélectionnez **Afficher tout et gérer les membres** sous l’onglet **Membres** . 
  
4. Sélectionnez **Ajouter des membres**, puis choisissez le nom de l’invité que vous souhaitez ajouter.
    
5. Sélectionnez **Enregistrer**.

Si vous souhaitez ajouter un invité directement au répertoire, vous pouvez [ajouter des utilisateurs Azure Active Directory B2B Collaboration dans le Portail Azure](/azure/active-directory/b2b/add-users-administrator).

Si vous souhaitez modifier les informations d’un invité, vous pouvez [ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="related-content"></a>Contenu associé

[Bloquer les invités d’un groupe spécifique](../../solutions/per-group-guest-access.md) (article)\
[Gérer l’appartenance à un groupe dans le Centre d'administration Microsoft 365](add-or-remove-members-from-groups.md) (article)\
[Révisions d’accès Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review) (article)\
[Set-AzureADUser](/powershell/module/azuread/set-azureaduser) (article)
