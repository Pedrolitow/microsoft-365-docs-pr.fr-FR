---
title: Accès au portail d’administration
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
ms.author: jaimeo
author: jaimeo
ms.topic: article
audience: ITPro
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.openlocfilehash: 2ac0bb01c1a941d460e92c7e75e765ceb85b2bc0
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546573"
---
# <a name="access-the-admin-portal"></a>Accéder au portail d’administration

Votre passerelle vers le service bureau géré Microsoft est le [portail Microsoft Azure](https://portal.azure.com). Pour en savoir plus sur l’utilisation et la personnalisation de votre expérience de portail Azure, consultez la documentation sur le [portail Azure](https://docs.microsoft.com/azure/azure-portal/). Disponible dans l’aperçu maintenant, vous pouvez également trouver Microsoft Managed Desktop dans le [Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com/). Si vous n’êtes pas familiarisé avec les fonctionnalités de ce portail pour la gestion des périphériques, consultez la [documentation du gestionnaire de points de terminaison Microsoft](https://docs.microsoft.com/mem/).

Votre compte d’administrateur a besoin d’autorisations spécifiques pour accéder aux fonctionnalités d’administration de bureau géré Microsoft dans le portail Azure ou le gestionnaire de points de terminaison Microsoft. Vous pouvez gérer l’accès administrateur à ces fonctionnalités au sein de votre organisation à l’aide du contrôle d’accès basé sur un rôle (RBAC). Plusieurs rôles d’administrateur Azure AD et de rôles personnalisés intégrés permettent de contrôler plus précisément les différentes fonctionnalités du portail d’administration de bureau géré Microsoft. Pour plus d’informations sur les rôles Azure Active Directory, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). Contrairement aux rôles d’administrateur AAD qui s’appliquent à un grand nombre de produits et de services Microsoft, les rôles personnalisés sont propres à Microsoft Managed Desktop et ne garantissent l’accès qu’aux fonctionnalités d’administration de ce service. Les administrateurs peuvent attribuer des rôles personnalisés aux utilisateurs individuellement ou en combinaison avec les rôles d’administrateur AAD pour ajouter des autorisations de bureau géré Microsoft à des comptes d’administrateur existants.

Chacun des rôles ci-dessous peut être affecté pour fournir différents niveaux d’accès :

|Rôle Azure AD  |Autorisations du bureau géré Microsoft  |
|---------|---------|
|Administrateur général     | Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.         |
|Lecteur général     | Les administrateurs disposant de ce rôle disposent d' **autorisations en lecture seule** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.         |
|Administrateur du service Intune     |  Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft. **Modifier :** Démarrage de septembre 2020 les administrateurs ayant ce rôle n’auront pas accès aux fonctionnalités de sécurité de bureau géré Microsoft.       |
|Administrateur de support de service     | Les administrateurs disposant de ce rôle disposent d' **autorisations de lecture et d’écriture** sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft. **Modifier :** Démarrage de septembre 2020 les administrateurs ayant ce rôle n’auront pas accès aux fonctionnalités de sécurité de bureau géré Microsoft.         |
|Administrateur de la sécurité | **(En aperçu de septembre 2020)** Les administrateurs disposant de ce rôle disposent d’autorisations en lecture seule sur toutes les fonctionnalités et des autorisations d’écriture pour les fonctionnalités liées à la sécurité dans le bureau géré Microsoft dans le portail d’administration. |
|Lecteur de sécurité | **(En aperçu de septembre 2020)**  Les administrateurs disposant de ce rôle disposent d’autorisations en lecture seule sur toutes les fonctionnalités du portail d’administration de bureau géré Microsoft.|

> [!IMPORTANT]
> Seul le rôle administrateur général dispose des autorisations nécessaires pour *inscrire* votre organisation dans le bureau géré Microsoft. N’oubliez pas que les rôles Azure Active Directory accorderont des privilèges de compte d’utilisateur à travers différents services Microsoft. Après avoir effectué l’enregistrement avec le bureau géré Microsoft, vous devez toujours utiliser le rôle avec les privilèges *minimum* nécessaires pour accomplir vos autres tâches.

 
|Rôle personnalisé  |Autorisations du bureau géré Microsoft  |
|---------|---------|
|Administrateur du service bureau géré Microsoft  | **(En aperçu de septembre 2020)** Lorsqu’il est affecté à un utilisateur, ce rôle accorde à l’administrateur des **autorisations en lecture & en écriture sur des fonctionnalités qui ne sont pas liées à la sécurité** dans le portail d’administration de bureau géré Microsoft.  |
|Lecteur de bureau géré Microsoft | **(En aperçu de septembre 2020)** Lorsqu’il est affecté à un utilisateur, ce rôle accorde aux administrateurs des **autorisations de lecture seule pour les fonctionnalités qui ne sont pas liées à la sécurité** dans le portail d’administration de bureau géré Microsoft. |
|Gestionnaire de sécurité du bureau géré Microsoft | **(En aperçu de septembre 2020)** Lorsqu’il est affecté à un utilisateur, ce rôle accorde à cet administrateur **des autorisations en lecture & en écriture uniquement pour les fonctionnalités liées** à la sécurité dans le portail d’administration de bureau géré Microsoft.   |

> [!NOTE]
> Les fonctionnalités de sécurité incluent les communications liées à la sécurité, la gestion des contacts de sécurité, la gestion des demandes de support liées à la sécurité et l’accès aux rapports liés à la sécurité. 

## <a name="assigning-roles-to-administrators"></a>Affectation de rôles aux administrateurs

Si vous avez besoin d’aide pour attribuer des rôles Azure Active Directory, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

Pour faciliter la gestion des rôles intégrés, un groupe de sécurité a été créé pour chaque rôle personnalisé (par exemple, « rôles Workplace modernes – gestionnaire de sécurité »). Pour attribuer des utilisateurs à l’un des groupes de sécurité, procédez comme suit :
1.  Accédez au portail Azure et accédez au panneau Azure Active Directory.
2.  Sélectionnez groupes sur le côté gauche.
3.  Recherchez les rôles Workplace modernes, puis sélectionnez le groupe associé au rôle que vous souhaitez attribuer. 
4.  Sélectionnez membres sur le côté gauche, puis sélectionnez + Ajouter des membres dans la barre de commandes.
5.  Entrez l’adresse de messagerie de la personne ajoutée. S’il s’agit d’un utilisateur externe, vous devez les inviter avant de pouvoir assigner le groupe.
6.  Sélectionnez sélectionner dans la partie inférieure.

> [!NOTE]
> L’imbrication de groupes de sécurité pour l’attribution de rôle n’est pas prise en charge actuellement. 
