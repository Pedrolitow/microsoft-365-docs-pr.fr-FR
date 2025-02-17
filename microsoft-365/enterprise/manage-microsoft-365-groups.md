---
title: Gestion des groupes Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- scotvorg
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Découvrez comment gérer les groupes Microsoft 365.
ms.openlocfilehash: 28af0d9581753e1852c0274feb92123ec70b23fd
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185466"
---
# <a name="manage-microsoft-365-groups"></a>Gestion des groupes Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez gérer les groupes Microsoft 365 de plusieurs façons, en fonction de votre configuration. Vous pouvez gérer des comptes d’utilisateur dans le [Centre d'administration Microsoft 365](/admin), PowerShell, dans services de domaine Active Directory (AD DS) ou dans le [Centre d’administration Azure Active Directory (Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)). 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planifier l’emplacement et la façon dont vous allez gérer vos groupes

L’emplacement et la façon dont vous pouvez gérer vos comptes d’utilisateur dépendent du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles globaux sont cloud uniquement et hybrides.
  
### <a name="cloud-only"></a>Cloud uniquement

Vous créez et gérez des groupes avec :

- [Le Centre d'administration Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centre d’administration Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybride

Les groupes AD DS étant synchronisés avec Microsoft 365 à partir d’AD DS, vous devez utiliser les outils AD DS locaux pour gérer ces groupes.

Vous pouvez également créer et gérer des groupes Azure AD distincts des groupes AD DS, mais qui peuvent contenir des utilisateurs et des groupes d’AD DS. Dans ce cas, vous pouvez utiliser :

- [Le Centre d'administration Microsoft 365](/admin)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centre d’administration Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Autoriser les utilisateurs à créer et gérer leurs propres groupes

Azure AD autorise les groupes qui peuvent être gérés par des propriétaires de groupes au lieu d’administrateurs informatiques. Appelée *gestion de groupes en libre-service*, cette fonctionnalité permet aux propriétaires de groupes qui ne disposent d’aucun rôle administratif de créer et de gérer des groupes de sécurité. 

Users can request membership in a security group and that request goes to the group owner, rather than an IT administrator. This allows the day-to-day control of group membership to be delegated to team, project, or business owners who understand the business use for the group and can manage its membership.

>[!Note]
>La gestion des groupes en libre-service est réservée aux groupes Microsoft 365 et aux groupes de sécurité Azure AD. Il n’est pas disponible pour les groupes, les listes de distribution ou les groupes compatibles avec la messagerie ou tout groupe qui a été synchronisé à partir d’AD DS.
>

Pour plus d’informations, consultez les [instructions de configuration d’un groupe Azure AD pour la gestion en libre-service](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Configurer l’appartenance à un groupe dynamique

Azure AD prend en charge la configuration d’une série de règles qui ajoutent ou suppriment automatiquement des comptes d’utilisateur en tant que membres d’un groupe Azure AD. C’est ce que l’on appelle l’*appartenance à un groupe dynamique*. Les règles sont basées sur les attributs du compte d’utilisateur, comme le département ou le pays.

Voici comment les règles sont appliquées :

- Si un compte d’utilisateur correspond à toutes les règles pour le groupe, il devient un membre.
- Si un compte d’utilisateur n’est pas membre du groupe, mais que ses attributs changent pour qu’il corresponde à toutes les règles pour le groupe, il devient un membre de ce groupe.
- Si un compte d’utilisateur ne correspond pas à toutes les règles pour le groupe, il n’est pas ajouté au groupe.
- Si un compte d’utilisateur est membre du groupe, mais que ses attributs changent pour qu’il ne corresponde plus à toutes les règles pour le groupe, il est supprimé comme membre du groupe.

To use dynamic membership, you must first determine the sets of groups that have a common set of user account attributes. For example, all members of the Sales department should be in the Sales Azure AD group, based on the user account attribute Department set to "Sales".

Reportez-vous aux [instructions pour créer et configurer les règles pour un groupe Azure AD dynamique](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Configurer la gestion des licences automatique

Vous pouvez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement des licences à partir d’un ensemble d’abonnements à tous les membres du groupe. C’est ce que l’on appelle la *gestion des licences basée sur les groupes*. Si un compte d’utilisateur est ajouté au groupe ou supprimé de ce dernier, les licences des abonnements du groupe sont automatiquement attribuées au compte d’utilisateur ou supprimées du compte.

Pour Microsoft 365 Entreprise, vous allez configurer des groupes de sécurité Azure AD afin d’attribuer la licence Microsoft 365 Entreprise qui convient.

Vérifiez que vous disposez de suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne seront pas disponibles.

>[!Note]
>Vous ne devez pas configurer la gestion des licences par groupes pour des groupes qui contiennent des comptes B2B Azure.
>

Pour plus d’informations, consultez [les principes de base des licences basées sur les groupes dans Azure AD](/azure/active-directory/active-directory-licensing-whatis-azure-portal).

Consultez les [instructions pour configurer les licences basées sur un groupe pour un groupe de sécurité Azure](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal).