---
title: Accès au portail d’administration
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
description: Découvrez comment rechercher et utiliser le portail d’administration, y compris le contrôle de l’accès à celui-ci.
ms.service: m365-md
ms.author: tiaraquan
author: tiaraquan
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.openlocfilehash: 89170c4479af29e9a4b3f46fa3b44ae2fcfa5500
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62444616"
---
# <a name="access-the-admin-portal"></a>Accéder au portail d’administration

Votre passerelle vers le service Microsoft Manged Desktop est [Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Si vous ne connaissez pas les fonctionnalités de ce portail pour la gestion des appareils, consultez [la documentation Microsoft Endpoint Manager.](/mem/)

> [!NOTE]
> Dans [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) navigateurs suivants sont pris en charge :
> - Microsoft Edge (dernière version)
> - Safari (dernière version, Mac uniquement)
> - Chrome (dernière version)
> - Firefox (dernière version)

Votre compte d’administration aura besoin d’autorisations spécifiques pour accéder aux fonctionnalités Microsoft Manged Desktop d’administration dans Microsoft Endpoint Manager.

Vous pouvez gérer l’accès administrateur à ces fonctionnalités au sein de votre organisation à l’aide du contrôle d’accès basé sur les rôles. Plusieurs Azure Active Directory administrateurs (Azure AD) et des rôles Microsoft Manged Desktop intégrés sont disponibles pour fournir un contrôle plus granulaire aux différentes fonctionnalités du portail d’administration Microsoft Manged Desktop. Pour plus d’informations sur Azure Active Directory rôles intégrés, [voir Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).

Contrairement aux rôles d’administrateur Azure AD qui s’appliquent à différents produits et services Microsoft, les rôles intégrés sont spécifiques à Microsoft Manged Desktop et garantissent uniquement l’accès aux fonctionnalités d’administration de ce service. Les administrateurs peuvent attribuer des rôles intégrés aux utilisateurs individuellement ou en combinaison avec des rôles d’administrateur Azure AD pour ajouter des autorisations Microsoft Manged Desktop aux comptes d’administrateur existants.

## <a name="azure-active-directory-roles-with-microsoft-managed-desktop-access"></a>Azure Active Directory rôles avec accès Microsoft Manged Desktop’accès

| Azure AD rôle | Microsoft Manged Desktop autorisations |
| ----- | ----- |
| Administrateur général | Les administrateurs dotés de ce rôle disposeront d’autorisations de lecture et d’écriture sur toutes les **fonctionnalités** du portail Microsoft Manged Desktop’administration. |
| Lecteur général | Les administrateurs dotés de ce rôle disposeront **d’autorisations** en lecture seule sur toutes les fonctionnalités du portail Microsoft Manged Desktop’administration. |
| Administrateur de services Intune | Les administrateurs dotés de ce rôle disposeront d’autorisations de lecture et d’écriture pour les **fonctionnalités** non liées à la sécurité dans Microsoft Manged Desktop portail d’administration. |
| Administrateur du support technique | Les administrateurs dotés de ce rôle disposeront d’autorisations en lecture seule sur les **fonctionnalités** non **liées** à la sécurité et d’autorisations d’écriture pour gérer les demandes de support, y compris les demandes d’escalade dans le portail d’administration Microsoft Manged Desktop. |
| Administrateur de sécurité | Les administrateurs dotés de ce rôle disposeront d’autorisations en lecture seule sur toutes les **fonctionnalités** et d’autorisations d’écriture pour les **fonctionnalités liées** à la sécurité Microsoft Manged Desktop dans le portail d’administration. |
| Lecteur de sécurité |Les administrateurs dotés de ce rôle disposeront **d’autorisations** en lecture seule sur toutes les fonctionnalités du portail Microsoft Manged Desktop’administration. |

Si vous avez besoin d’aide pour attribuer Azure Active Directory rôles, voir [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).

> [!IMPORTANT]
> Seul le rôle Administrateur général dispose des autorisations nécessaires pour  inscrire votre organisation dans Microsoft Manged Desktop. N’Azure Active Directory pas que les rôles de compte d’utilisateur donnent des privilèges de comptes d’utilisateurs à différents services Microsoft. Une fois l’inscription Microsoft Manged Desktop, vous devez toujours utiliser le rôle avec le moins de  privilèges nécessaires pour accomplir vos autres tâches.

## <a name="built-in-roles-provided-by-microsoft-managed-desktop"></a>Rôles intégrés fournis par Microsoft Manged Desktop

Voici les rôles intégrés fournis par les Microsoft Manged Desktop :

| Rôle intégré | Microsoft Manged Desktop autorisations |
| ----- | ----- |
| Microsoft Manged Desktop service d’administration | Lorsqu’il est attribué à un utilisateur, ce rôle donne à l’administrateur des autorisations de lecture et d’écriture pour Microsoft Manged Desktop **fonctionnalités non liées** à la sécurité dans le portail d’administration Microsoft Manged Desktop. |
| lecteur Microsoft Manged Desktop service | Lorsqu’il est attribué à un utilisateur, ce rôle donne à l’administrateur des autorisations en lecture seule pour Microsoft Manged Desktop **fonctionnalités non liées** à la sécurité dans le portail d Microsoft Manged Desktop’administration. |
| Microsoft Manged Desktop Security Manager | Lorsqu’il est attribué à un utilisateur, ce rôle accorde à l’administrateur des autorisations de lecture et d’écriture uniquement pour les **fonctionnalités liées** à la sécurité dans Microsoft Manged Desktop portail d’administration. |
| Microsoft Manged Desktop support technique |Lorsqu’il est attribué à un utilisateur, ce rôle accorde à l’administrateur des **autorisations** de lecture et d’écriture uniquement pour la création et la gestion des demandes d’élévation et pour prendre en charge les demandes d’escalade engagées par le partenaire dans le portail d’administration Microsoft Manged Desktop. |

> [!NOTE]
> Les fonctionnalités de sécurité incluent les communications liées à la sécurité, la gestion des contacts de sécurité, la gestion des demandes de support liées à la sécurité et l’accès aux rapports liés à la sécurité.

### <a name="assigning-built-in-roles-to-user"></a>Attribution de rôles intégrés à l’utilisateur

Pour faciliter la gestion des rôles intégrés, il existe un groupe de sécurité pour chaque rôle personnalisé nommé « Modern Workplace Roles - _Role Name_ ». Par exemple, « Rôles d’espace de travail modernes – Gestionnaire de sécurité »).

**Pour affecter des utilisateurs à l’un de ces groupes de sécurité :**

1. Go the Microsoft Endpoint Manager portal.
2. Dans le volet gauche, sélectionnez **Groupes**.
3. Recherchez **les rôles d’espace** de travail modernes, puis sélectionnez le groupe associé au rôle que vous souhaitez attribuer.
4. **Sélectionnez Membres** sur le côté gauche, puis **sélectionnez + Ajouter des membres** dans la barre de commandes.
5. Entrez le courrier électronique de la personne ajoutée. S’il s’agit d’un invité, vous devez l’inviter avant de pouvoir affecter le groupe.
6. **Sélectionnez Sélectionner** en bas.

> [!NOTE]
> L’imbrmbrage de groupes de sécurité pour l’attribution de rôle n’est actuellement pas pris en charge.

### <a name="assigning-built-in-roles-to-groups"></a>Attribution de rôles intégrés à des groupes

**Pour attribuer un ou plusieurs des rôles intégrés à un groupe existant :**

1. Go to [portal.azure.com](https://portal.azure.com/).
2. Recherchez et ouvrez **Enterprise applications.**
3. Modifiez **le filtre de type** Application en _Applications Microsoft_ , puis sélectionnez **Appliquer**.
4. Recherchez et sélectionnez _les API clientes de l’espace de travail moderne_.
5. **Sélectionnez Utilisateurs et groupes** dans le volet de gauche, puis **sélectionnez + Ajouter un utilisateur/groupe**.
6. Recherchez le groupe que vous souhaitez auprès des **utilisateurs et des groupes**.
7. Recherchez le rôle applicable dans **Sélectionner un rôle**, puis sélectionnez-le.
8. Sélectionnez **Affecter**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en Microsoft Manged Desktop

1. Portail d’administration Access (cet article).
1. [Ajouter et vérifier des contacts d’administrateur dans le portail d’administration](add-admin-contacts.md).
1. [Ajuster les paramètres après l’inscription](conditional-access.md).
1. Déployez et affectez le[Portail d’entreprise Intune](company-portal.md).
1. [Attribuer des licences](assign-licenses.md).
1. [Déployer des applications](deploy-apps.md).
1. [Configurer les appareils](set-up-devices.md).
1. Configurez l’[Expérience de première exécution avec Autopilot et la page d’état d’inscription](esp-first-run.md).
1. [Activer les fonctionnalités de support utilisateur](enable-support.md).
1. [Préparez vos utilisateurs à utiliser des appareils](get-started-devices.md).
1. [Démarrage avec le contrôle d’application](get-started-app-control.md).
