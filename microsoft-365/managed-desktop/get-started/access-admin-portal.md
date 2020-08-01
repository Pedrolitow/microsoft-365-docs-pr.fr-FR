---
title: Accès au portail d’administration
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
ms.author: jaimeo
author: jaimeo
ms.prod: microsoft-365-enterprise
ms.topic: article
audience: ITPro
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.openlocfilehash: 420cdaabb607eacf0d7a7109827fe5437e2f999c
ms.sourcegitcommit: 126d22d8abd190beb7101f14bd357005e4c729f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "46530222"
---
# <a name="access-the-admin-portal"></a>Accéder au portail d’administration

Votre passerelle vers le service bureau géré Microsoft est le [portail Microsoft Azure](https://portal.azure.com). Pour en savoir plus sur l’utilisation et la personnalisation de votre expérience de portail Azure, consultez la documentation sur le [portail Azure](https://docs.microsoft.com/azure/azure-portal/). Disponible dans l’aperçu maintenant, vous pouvez également trouver Microsoft Managed Desktop dans le [Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com/). Si vous n’êtes pas familiarisé avec les fonctionnalités de ce portail pour la gestion des périphériques, consultez la [documentation du gestionnaire de points de terminaison Microsoft](https://docs.microsoft.com/mem/).

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
