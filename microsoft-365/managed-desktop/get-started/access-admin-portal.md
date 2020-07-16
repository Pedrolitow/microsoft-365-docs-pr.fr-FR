---
title: Accéder au portail d’administration
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
ms.author: jaimeo
author: jaimeo
ms.prod: microsoft-365-enterprise
ms.topic: article
audience: ITPro
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b6310849f27200adbbcbcb1584903011fbdf6145
ms.sourcegitcommit: 9af890ef1b1c95bfc7cc52f7f4e395b62dc5263f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "45146266"
---
# <a name="access-the-admin-portal"></a>Accéder au portail d’administration

Votre passerelle vers le service bureau géré Microsoft est le [portail Microsoft Azure](https://portal.azure.com). Pour en savoir plus sur l’utilisation et la personnalisation de votre expérience de portail Azure, consultez la documentation sur le [portail Azure](https://docs.microsoft.com/azure/azure-portal/). 

Votre compte d’administrateur a besoin d’autorisations spécifiques pour accéder au portail d’administration de bureau géré Microsoft. Vous pouvez gérer l’accès administrateur à ces fonctionnalités au sein de votre organisation à l’aide du contrôle d’accès basé sur un rôle (RBAC). Pour plus d’informations sur les rôles Azure Active Directory, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

Affectez à vos comptes d’utilisateur d’administrateur les rôles suivants pour garantir l’accès :

|Rôle Azure AD  |Autorisations du bureau géré Microsoft  |
|---------|---------|
|Administrateur général     | Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.         |
|Lecteur général     | Les administrateurs disposant de ce rôle disposent d' **autorisations en lecture seule** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.         |
|Administrateur du service Intune     |  Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.       |
|Administrateur de support de service     | Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.         |

> [!IMPORTANT]
> Seul le rôle administrateur général dispose des autorisations nécessaires pour *inscrire* votre organisation dans le bureau géré Microsoft. N’oubliez pas que les rôles Azure Active Directory accorderont des privilèges de compte d’utilisateur à travers différents services Microsoft. Après avoir effectué l’enregistrement avec le bureau géré Microsoft, vous devez toujours utiliser le rôle avec les privilèges *minimum* nécessaires pour accomplir vos autres tâches.

## <a name="assigning-roles-to-administrators"></a>Affectation de rôles aux administrateurs

Si vous avez besoin d’aide pour attribuer des rôles Azure Active Directory, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).
