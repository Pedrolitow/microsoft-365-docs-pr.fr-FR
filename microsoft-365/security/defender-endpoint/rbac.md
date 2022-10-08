---
title: Utiliser le contrôle d’accès en fonction du rôle pour accorder un accès affiné à Microsoft 365 Defender portail
description: Créez des rôles et des groupes dans vos opérations de sécurité pour accorder l’accès au portail.
keywords: rbac, role, based, access, control, groups, control, tier, aad
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: f55ca70c94fa73c26cefd067f2006f174ce4b15c
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232669"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Active Directory
- Office 365

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

À l’aide du contrôle d’accès en fonction du rôle (RBAC), vous pouvez créer des rôles et des groupes au sein de votre équipe des opérations de sécurité pour accorder un accès approprié au portail. En fonction des rôles et des groupes que vous créez, vous disposez d’un contrôle précis sur ce que les utilisateurs ayant accès au portail peuvent voir et faire. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Les grandes équipes d’opérations de sécurité géodistribuées adoptent généralement un modèle basé sur un niveau pour attribuer et autoriser l’accès aux portails de sécurité. Les niveaux classiques incluent les trois niveaux suivants :

|Niveau |Description  |
|---------|---------|
|Niveau 1    | **Équipe des opérations de sécurité locale/équipe informatique** <br> Cette équipe trie et examine généralement les alertes contenues dans sa géolocalisation et passe au niveau 2 dans les cas où une correction active est nécessaire.        |
|Niveau 2    | **Équipe des opérations de sécurité régionales** <br> Cette équipe peut voir tous les appareils de leur région et effectuer des actions de correction.        |
|Niveau 3     |**Équipe des opérations de sécurité globale** <br> Cette équipe se compose d’experts en sécurité et est autorisée à voir et à effectuer toutes les actions à partir du portail.         |

> [!NOTE]
> Pour les ressources de niveau 0, reportez-vous à [Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure) pour que les administrateurs de sécurité fournissent un contrôle plus précis des Microsoft Defender pour point de terminaison et des Microsoft 365 Defender.  

Defender pour point de terminaison RBAC est conçu pour prendre en charge votre modèle de niveau ou de rôle de votre choix et vous donne un contrôle précis sur les rôles qui peuvent être vus, les appareils auxquels ils peuvent accéder et les actions qu’ils peuvent effectuer. L’infrastructure RBAC est centrée sur les contrôles suivants :

- **Contrôler qui peut prendre des mesures spécifiques**
  - Créez des rôles personnalisés et contrôlez les fonctionnalités de Defender pour point de terminaison aux laquelle ils peuvent accéder avec granularité.
- **Contrôler qui peut afficher des informations sur des groupes ou des groupes d’appareils spécifiques**
  - [Créez des groupes d’appareils](machine-groups.md) selon des critères spécifiques tels que des noms, des balises, des domaines et d’autres, puis accordez-leur l’accès au rôle à l’aide d’un groupe d’utilisateurs Azure Active Directory (Azure AD) spécifique.
    > [!NOTE]
    > La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.  

Pour implémenter l’accès en fonction du rôle, vous devez définir des rôles d’administrateur, attribuer des autorisations correspondantes et affecter des groupes d’utilisateurs Azure AD affectés aux rôles.

### <a name="before-you-begin"></a>Avant de commencer

Avant d’utiliser RBAC, il est important de comprendre les rôles qui peuvent accorder des autorisations et les conséquences de l’activation de RBAC.

> [!WARNING]
> Avant d’activer la fonctionnalité, il est important que vous ayez un rôle d’administrateur général ou d’administrateur de sécurité dans Azure AD et que vos groupes Azure AD soient prêts à réduire le risque de verrouillage hors du portail. 

Lorsque vous vous connectez pour la première fois au portail Microsoft 365 Defender, vous bénéficiez d’un accès complet ou en lecture seule. Les droits d’accès complets sont accordés aux utilisateurs disposant de rôles Administrateur de sécurité ou Administrateur général dans Azure AD. L’accès en lecture seule est accordé aux utilisateurs disposant d’un rôle Lecteur sécurité dans Azure AD. 

Une personne ayant un rôle Defender pour point de terminaison Administrateur général a un accès illimité à tous les appareils, indépendamment de leur association de groupes d’appareils et des affectations de groupes d’utilisateurs Azure AD.

> [!WARNING]
> Initialement, seuls les utilisateurs disposant de droits d’administrateur général ou d’administrateur de sécurité Azure AD pourront créer et attribuer des rôles dans le portail Microsoft 365 Defender. Par conséquent, il est important de disposer des groupes appropriés dans Azure AD.
>
> **L’activation du contrôle d’accès en fonction du rôle entraîne la perte d’accès aux utilisateurs disposant d’autorisations en lecture seule (par exemple, les utilisateurs affectés au rôle lecteur Sécurité Azure AD) jusqu’à ce qu’ils soient affectés à un rôle.** 
>
>Les utilisateurs disposant d’autorisations d’administrateur se voient automatiquement attribuer le rôle d’administrateur général Defender pour point de terminaison intégré par défaut avec des autorisations complètes. Après avoir choisi d’utiliser RBAC, vous pouvez affecter des utilisateurs supplémentaires qui ne sont pas administrateurs généraux ou de sécurité Azure AD au rôle d’administrateur général Defender pour point de terminaison. 
>
> Après avoir choisi d’utiliser RBAC, vous ne pouvez pas revenir aux rôles initiaux comme lorsque vous vous êtes connecté pour la première fois au portail.

## <a name="related-topic"></a>Rubrique connexe

- [Rôles RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Créer et gérer des groupes d’appareils dans Microsoft Defender pour point de terminaison](machine-groups.md)
