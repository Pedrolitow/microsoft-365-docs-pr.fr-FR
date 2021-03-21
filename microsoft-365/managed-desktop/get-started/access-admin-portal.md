---
title: Accès au portail d’administration
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
description: Découvrez comment rechercher et utiliser le portail d’administration, y compris le contrôle de l’accès à celui-ci.
ms.service: m365-md
ms.author: jaimeo
author: jaimeo
ms.topic: article
audience: ITPro
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: laurawi
ms.openlocfilehash: 7293c8ced43332f84ced56908ea5203ba867e600
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50925903"
---
# <a name="access-the-admin-portal"></a>Accéder au portail d’administration

Votre passerelle vers le service Bureau géré Microsoft est [Microsoft Endpoint Manager.](https://endpoint.microsoft.com/) Si vous ne connaissez pas les fonctionnalités de ce portail pour la gestion des appareils, consultez la documentation de [Microsoft Endpoint Manager.](/mem/)

> [!NOTE]
> Dans [Microsoft Endpoint Manager,](https://endpoint.microsoft.com/) les navigateurs suivants sont pris en charge :
> - Microsoft Edge (dernière version)
> - Microsoft Internet Explorer 11
> - Safari (dernière version, Mac uniquement)
> - Chrome (dernière version)
> - Firefox (dernière version)

Votre compte d’administration aura besoin d’autorisations spécifiques pour accéder aux fonctionnalités d’administration du Bureau géré Microsoft dans Microsoft Endpoint Manager. Vous pouvez gérer l’accès administrateur à ces fonctionnalités au sein de votre organisation à l’aide du contrôle d’accès basé sur les rôles. Plusieurs rôles d’administrateur Azure Active Directory (Azure AD) et rôles de bureau géré Microsoft intégrés sont disponibles pour fournir un contrôle plus granulaire aux différentes fonctionnalités dans le portail d’administration du bureau géré Microsoft. Pour plus d’informations sur les rôles Azure Active Directory, voir Autorisations de rôle [d’administrateur dans Azure Active Directory.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) Contrairement aux rôles d’administrateur Azure AD qui s’appliquent à différents produits et services Microsoft, les rôles intégrés sont spécifiques au Bureau géré Microsoft et garantissent uniquement l’accès aux fonctionnalités d’administration de ce service. Les administrateurs peuvent attribuer des rôles intégrés aux utilisateurs individuellement ou en combinaison avec les rôles d’administrateur Azure AD pour ajouter des autorisations Bureau géré Microsoft aux comptes d’administrateur existants.

## <a name="azure-active-directory-roles-with-microsoft-managed-desktop-access"></a>Rôles Azure Active Directory avec accès Bureau géré Microsoft

|Rôle Azure AD  |Autorisations bureau géré Microsoft  |
|---------|---------|
|Administrateur général     | Les administrateurs dotés de ce rôle disposeront d’autorisations de lecture et d’écriture sur toutes les **fonctionnalités** du portail d’administration du bureau géré Microsoft.         |
|Lecteur général     | Les administrateurs dotés de ce rôle disposeront **d’autorisations** en lecture seule sur toutes les fonctionnalités du portail d’administration du bureau géré Microsoft.         |
|Administrateur de service Intune     |  Les administrateurs dotés de ce rôle disposeront d’autorisations de lecture et d’écriture sur les **fonctionnalités non liées** à la sécurité dans le portail d’administration du bureau géré Microsoft.       |
|Administrateur du support technique     | Les administrateurs dotés de ce rôle disposeront d’autorisations en lecture seule sur les **fonctionnalités** non **liées** à la sécurité et d’autorisations d’écriture pour gérer les demandes de support dans le portail d’administration du bureau géré Microsoft.         |
|Administrateur de sécurité | Les administrateurs dotés de ce rôle disposeront d’autorisations en lecture seule sur toutes les **fonctionnalités** et d’autorisations d’écriture pour les **fonctionnalités liées** à la sécurité dans bureau géré Microsoft dans le portail d’administration. |
|Lecteur de sécurité |Les administrateurs dotés de ce rôle disposeront **d’autorisations** en lecture seule sur toutes les fonctionnalités du portail d’administration du bureau géré Microsoft.|

Si vous avez besoin d’aide pour attribuer des rôles Azure Active Directory, consultez autorisations de rôle [d’administrateur dans Azure Active Directory.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)

> [!IMPORTANT]
> Seul le rôle Administrateur général dispose  des autorisations nécessaires pour inscrire votre organisation dans Bureau géré Microsoft. N’ignorez pas que les rôles Azure Active Directory donnent des privilèges de comptes d’utilisateur dans divers services Microsoft. Une fois l’inscription avec Bureau géré Microsoft terminé, vous devez toujours utiliser le rôle avec le moins de privilèges nécessaires pour accomplir vos autres tâches. 

## <a name="built-in-roles-provided-by-microsoft-managed-desktop"></a>Rôles intégrés fournis par Bureau géré Microsoft


|Rôle intégré  |Autorisations bureau géré Microsoft  |
|---------|---------|
|Administrateur du service Bureau géré Microsoft  | Lorsqu’il est attribué à un utilisateur, ce rôle donne à l’administrateur des autorisations de lecture et d’écriture sur les fonctionnalités non **liées** à la sécurité dans le portail d’administration du bureau géré Microsoft.  |
|Lecteur de service Bureau géré Microsoft | Lorsqu’il est attribué à un utilisateur, ce rôle donne à l’administrateur des autorisations en lecture seule sur les fonctionnalités non **liées** à la sécurité dans le portail d’administration du bureau géré Microsoft. |
|Gestionnaire de sécurité du bureau géré Microsoft |Lorsqu’il est attribué à un utilisateur, ce rôle accorde à l’administrateur des autorisations de lecture et d’écriture uniquement pour les **fonctionnalités liées** à la sécurité dans le portail d’administration du bureau géré Microsoft.   |

> [!NOTE]
> Les fonctionnalités de sécurité incluent les communications liées à la sécurité, la gestion des contacts de sécurité, la gestion des demandes de support liées à la sécurité et l’accès aux rapports liés à la sécurité. 

### <a name="assigning-built-in-roles-to-user"></a>Attribution de rôles intégrés à l’utilisateur

Pour faciliter la gestion des rôles intégrés, il existe un groupe de sécurité pour chaque rôle personnalisé nommé « Modern Workplace Roles - _Role Name_» (par exemple, « Modern Workplace Roles – Security Manager »). Pour affecter des utilisateurs à l’un de ces groupes de sécurité, suivez les étapes suivantes :
1.  Go the Microsoft Endpoint Manager portal.
2.  Sélectionnez **Groupes** sur le côté gauche.
3.  Recherchez **les rôles de l’espace** de travail moderne, puis sélectionnez le groupe associé au rôle que vous souhaitez attribuer. 
4.  Sélectionnez **Membres** sur le côté gauche, puis **sélectionnez + Ajouter des membres** dans la barre de commandes.
5.  Entrez le courrier électronique de la personne ajoutée. S’ils sont invités, vous devez les inviter avant de pouvoir affecter le groupe.
6.  Sélectionnez **Sélectionner** en bas.

> [!NOTE]
> L’imbrmbrage de groupes de sécurité pour l’attribution de rôle n’est actuellement pas pris en charge. 

### <a name="assigning-built-in-roles-to-groups"></a>Attribution de rôles intégrés à des groupes

Si vous devez attribuer un ou plusieurs des rôles intégrés à un groupe existant, suivez les étapes suivantes :
1. Go to [portal.azure.com](https://portal.azure.com/).
2. Recherchez et ouvrez **des applications d’entreprise.**
3. Modifiez **le filtre de type** Application en Applications _Microsoft,_ puis sélectionnez **Appliquer**.
4. Recherchez et sélectionnez _les API clientes de l’espace de travail moderne._
5. Sélectionnez **Utilisateurs et groupes** dans le volet de gauche, puis **sélectionnez + Ajouter un utilisateur/groupe.**
6. Recherchez le groupe que vous souhaitez auprès des **utilisateurs et des groupes.**
7. Recherchez le rôle applicable à partir **de Sélectionner** un rôle, puis sélectionnez-le.
8. Sélectionnez **Affecter**.
