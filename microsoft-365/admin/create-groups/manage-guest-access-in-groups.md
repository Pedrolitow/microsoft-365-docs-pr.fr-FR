---
title: Gérer l’accès invité dans les groupes Microsoft 365
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
description: Découvrez comment ajouter des invités à un groupe Microsoft 365, afficher des utilisateurs invités et utiliser PowerShell pour contrôler l’accès invité.
ms.openlocfilehash: 3fba6b4498f275b07148c2d879d141474ddf4a13
ms.sourcegitcommit: 3cdb670f10519f7af4015731e7910954ba9f70dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48753276"
---
# <a name="manage-guest-access-in-microsoft-365-groups"></a>Gérer l’accès invité dans les groupes Microsoft 365

Par défaut, l’accès invité pour les groupes Microsoft 365 est activé pour votre organisation. Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité à des groupes pour l’ensemble de l’organisation ou pour des groupes individuels.

Lorsqu’elle est activée, les membres du groupe peuvent inviter des utilisateurs invités à un groupe Microsoft 365 via Outlook sur le Web. Les invitations sont envoyées au propriétaire du groupe pour approbation.

Une fois approuvé, l’utilisateur invité est ajouté au répertoire et au groupe.

> [!Note]
> Les réseaux d’entreprise yammer en mode natif ou dans l' [Union européenne](https://go.microsoft.com/fwlink/?linkid=2107357) ne prennent pas en charge les invités réseau.
> Les groupes Yammer connectés à Microsoft 365 ne prennent actuellement pas en charge l’accès invité, mais vous pouvez créer des groupes externes non connectés dans votre réseau Yammer. Consultez la rubrique [créer et gérer des groupes externes dans Yammer](https://docs.microsoft.com/yammer/work-with-external-users/create-and-manage-external-groups) pour obtenir des instructions.

L’accès invité dans des groupes est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes sur la configuration du partage d’invités entre les groupes, SharePoint et Teams, voir :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer les groupes accès invité

Si vous souhaitez activer ou désactiver l’accès invité dans des groupes, vous pouvez le faire dans le centre d’administration 365 de Microsoft.

1. Dans le centre d’administration, accédez à la section **Afficher tous les** \> **paramètres** de \> l' **organisation** , puis, sous l’onglet **services** , sélectionnez **groupes Microsoft 365**.
  
2. Sur la page **groupes Microsoft 365** , indiquez si vous souhaitez autoriser les personnes extérieures à votre organisation à accéder aux ressources de groupe ou les propriétaires de groupes à ajouter des personnes en dehors de votre organisation à des groupes.

## <a name="add-guests-to-a-microsoft-365-group-from-the-admin-center"></a>Ajouter des invités à un groupe Microsoft 365 à partir du centre d’administration

Si l’invité existe déjà dans votre répertoire, vous pouvez l’ajouter à vos groupes à partir du centre d’administration 365 de Microsoft.
  
1. Dans le centre d’administration, accédez à **la page groupes de**  >  **groupes** .
  
2. Cliquez sur le groupe auquel vous souhaitez ajouter l’invité, puis sélectionnez **Afficher tout et gérer les membres** sous l’onglet **membres** . 
  
4. Sélectionnez **Ajouter des membres**, puis choisissez le nom de l’invité que vous souhaitez ajouter.
    
5. Sélectionnez **Enregistrer**.

Si vous souhaitez ajouter un invité directement à l’annuaire, vous pouvez [Ajouter des utilisateurs de collaboration B2B Azure Active Directory dans le portail Azure](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

Si vous souhaitez modifier les informations d’un invité, vous pouvez [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

## <a name="see-also"></a>Voir aussi

[Bloquer les utilisateurs invités d’un groupe spécifique](https://docs.microsoft.com/microsoft-365/solutions/per-group-guest-access)

[Gérer l’appartenance au groupe dans le centre d’administration Microsoft 365](add-or-remove-members-from-groups.md)
  
[Avis d’accès à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser)
