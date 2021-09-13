---
title: Gestion des groupes Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Découvrez comment gérer les groupes Microsoft 365'équipe.
ms.openlocfilehash: 72bc47bb699e32f849f21ea4c5470a95d6228b68
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209353"
---
# <a name="manage-microsoft-365-groups"></a>Gestion des groupes Microsoft 365

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Vous pouvez gérer Microsoft 365 groupes de différentes manières, en fonction de votre configuration. Vous pouvez gérer les comptes d’utilisateurs dans [Centre d'administration Microsoft 365,](../admin/add-users/index.yml)PowerShell, dans les services de domaine Active Directory (AD DS) ou dans le Centre d’administration [Azure Active Directory (Azure AD).](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) 

## <a name="plan-for-where-and-how-you-will-manage-your-groups"></a>Planifier l’endroit et la façon dont vous allez gérer vos groupes

L’endroit où et comment vous pouvez gérer vos comptes d’utilisateur dépend du modèle d’identité que vous souhaitez utiliser pour votre Microsoft 365. Les deux modèles globaux sont uniquement cloud et hybrides.
  
### <a name="cloud-only"></a>Cloud uniquement

Vous créez et gérez des groupes avec :

- [Le Centre d’administration Microsoft 365](../admin/add-users/index.yml)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centre d’administration d’Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    
### <a name="hybrid"></a>Hybride

Les groupes AD DS sont synchronisés avec les Microsoft 365 d’AD DS. Vous devez donc utiliser les outils AD DS locaux pour gérer ces groupes.

Vous pouvez également créer et gérer des groupes Azure AD séparés des groupes AD DS, mais qui peuvent contenir des utilisateurs et des groupes d’AD DS. Dans ce cas, vous pouvez utiliser :

- [Le Centre d’administration Microsoft 365](../admin/add-users/index.yml)
- [PowerShell](maintain-group-membership-with-microsoft-365-powershell.md)
- [Centre d’administration d’Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)

## <a name="allow-users-to-create-and-manage-their-own-groups"></a>Autoriser les utilisateurs à créer et gérer leurs propres groupes

Azure AD autorise les groupes qui peuvent être gérés par les propriétaires de groupes plutôt que par les administrateurs informatiques. Appelée *gestion de groupes en libre-service*, cette fonctionnalité permet aux propriétaires de groupes qui ne disposent d’aucun rôle administratif de créer et de gérer des groupes de sécurité. 

Les utilisateurs peuvent demander à appartenir à un groupe de sécurité. Cette demande est envoyée au propriétaire du groupe, et non à l’administrateur informatique. Ainsi, le contrôle quotidien de l’appartenance au groupe peut être délégué aux propriétaires d’équipes, de projets ou d’entreprises qui comprennent l’usage du groupe pour l’entreprise et peuvent gérer ses membres.

>[!Note]
>La gestion des groupes en libre-service est réservée aux groupes Microsoft 365 et aux groupes de sécurité Azure AD. Il n’est pas disponible pour les groupes à messagerie, les listes de distribution ou les groupes qui ont été synchronisés à partir d’AD DS.
>

Pour plus d’informations, consultez les [instructions de configuration d’un groupe Azure AD pour la gestion en libre-service](/azure/active-directory/active-directory-accessmanagement-self-service-group-management).

## <a name="set-up-dynamic-group-membership"></a>Configurer l’appartenance à un groupe dynamique

Azure AD prend en charge la configuration d’une série de règles qui ajoutent ou suppriment automatiquement des comptes d’utilisateur en tant que membres d’un groupe Azure AD. C’est ce que l’on appelle l’*appartenance à un groupe dynamique*. Les règles sont basées sur les attributs du compte d’utilisateur, comme le département ou le pays.

Voici comment les règles sont appliquées :

- Si un compte d’utilisateur correspond à toutes les règles pour le groupe, il devient un membre.
- Si un compte d’utilisateur n’est pas membre du groupe, mais que ses attributs changent pour qu’il corresponde à toutes les règles pour le groupe, il devient un membre de ce groupe.
- Si un compte d’utilisateur ne correspond pas à toutes les règles pour le groupe, il n’est pas ajouté au groupe.
- Si un compte d’utilisateur est membre du groupe, mais que ses attributs changent pour qu’il ne corresponde plus à toutes les règles pour le groupe, il est supprimé comme membre du groupe.

Pour utiliser l’appartenance dynamique, vous devez commencer par déterminer les ensembles de groupes qui ont un ensemble commun d’attributs de compte d’utilisateur. Par exemple, tous les membres du service Ventes doivent être dans le groupe Ventes Azure AD, en fonction de l’attribut de compte d’utilisateur Service défini sur « Ventes ».

Reportez-vous aux [instructions pour créer et configurer les règles pour un groupe Azure AD dynamique](/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal).

## <a name="set-up-automatic-licensing"></a>Configurer la gestion des licences automatique

Vous pouvez configurer des groupes de sécurité dans Azure AD pour attribuer automatiquement des licences d’un ensemble d’abonnements à tous les membres du groupe. C’est ce que l’on appelle la *gestion des licences basée sur les groupes*. Si un compte d’utilisateur est ajouté au groupe ou supprimé de ce dernier, les licences des abonnements du groupe sont automatiquement attribuées au compte d’utilisateur ou supprimées du compte.

Pour Microsoft 365 Entreprise, vous allez configurer des groupes de sécurité Azure AD afin d’attribuer la licence Microsoft 365 Entreprise qui convient.

Vérifiez que vous disposez de suffisamment de licences pour tous les membres du groupe. Si vous n’avez plus de licences, aucune licence ne sera attribuée aux nouveaux utilisateurs tant que d’autres licences ne seront pas disponibles.

>[!Note]
>Vous ne devez pas configurer la gestion des licences par groupes pour des groupes qui contiennent des comptes B2B Azure.
>

Pour plus d’informations, voir les informations de base sur les [licences basées sur les groupes dans Azure AD.](/azure/active-directory/active-directory-licensing-whatis-azure-portal)

Consultez les instructions pour configurer la gestion des licences basée sur [les groupes pour un groupe de sécurité Azure.](/azure/active-directory/active-directory-licensing-group-assignment-azure-portal)