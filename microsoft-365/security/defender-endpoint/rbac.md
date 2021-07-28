---
title: Utiliser le contrôle d’accès basé sur les rôles pour accorder un accès fin à Microsoft 365 Defender portail
description: Créez des rôles et des groupes au sein de vos opérations de sécurité pour accorder l’accès au portail.
keywords: rbac, role, based, access, control, groups, control, tier, aad
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 594adb952f9c5f98a5c51a176f3fe7f0ac56692c
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53624271"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Gérer l’accès au portail à l’aide du contrôle d’accès basé sur un rôle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- Azure Active Directory
- Office 365

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-rbac-abovefoldlink)

À l’aide du contrôle d’accès basé sur un rôle (RBAC), vous pouvez créer des rôles et des groupes au sein de votre équipe des opérations de sécurité pour accorder un accès approprié au portail. En fonction des rôles et des groupes que vous créez, vous avez un contrôle fin sur ce que les utilisateurs ayant accès au portail peuvent voir et faire. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Les grandes équipes d’opérations de sécurité distribuées géographiquement adoptent généralement un modèle basé sur un niveau pour attribuer et autoriser l’accès aux portails de sécurité. Les niveaux classiques incluent les trois niveaux suivants :

Niveau|Description
:---|:---
Niveau 1|**Équipe des opérations de sécurité locale/équipe informatique** <br> Cette équipe trie et examine généralement les alertes contenues dans leur géolocalisation et atteint le niveau 2 dans les cas où une correction active est nécessaire.
Niveau 2|**Équipe des opérations de sécurité régionales** <br> Cette équipe peut voir tous les appareils de leur région et effectuer des actions de correction.
Niveau 3|**Équipe des opérations de sécurité globale** <br> Cette équipe est constituée d’experts en sécurité et est autorisée à voir et à effectuer toutes les actions à partir du portail.

Defender for Endpoint RBAC est conçu pour prendre en charge votre modèle de choix basé sur des rôles ou des niveaux et vous donne un contrôle granulaire sur les rôles qu’ils peuvent voir, les appareils accessibles et les actions qu’ils peuvent prendre. L’infrastructure RBAC est centrée autour des contrôles suivants :

- **Contrôler les personnes qui peuvent prendre des mesures spécifiques**
  - Créez des rôles personnalisés et contrôlez les fonctionnalités de Defender for Endpoint accessibles avec granularité.
- **Contrôler qui peut voir les informations sur un ou plusieurs groupes d’appareils spécifiques**
  - [Créez](machine-groups.md) des groupes d’appareils en fonction de critères spécifiques tels que des noms, des balises, des domaines et d’autres, puis accordez-leur l’accès au rôle à l’aide d’un groupe d’utilisateurs Azure Active Directory (Azure AD).

Pour implémenter l’accès basé sur les rôles, vous devez définir des rôles d’administrateur, attribuer des autorisations correspondantes et affecter des groupes d’utilisateurs Azure AD affectés aux rôles.

### <a name="before-you-begin"></a>Avant de commencer

Avant d’utiliser le RBAC, il est important de comprendre les rôles qui peuvent accorder des autorisations et les conséquences de l’utilisation du RBAC.

> [!WARNING]
> Avant d’activer la fonctionnalité, il est important que vous disposez d’un rôle d’administrateur général ou d’administrateur de la sécurité dans Azure AD et que vos groupes Azure AD sont prêts à réduire le risque d’être verrouillé du portail. 

Lorsque vous vous connectez pour la première fois au portail Microsoft 365 Defender, l’accès total ou l’accès en lecture seule vous est accordé. Les droits d’accès total sont accordés aux utilisateurs ayant des rôles Administrateur de sécurité ou Administrateur général dans Azure AD. L’accès en lecture seule est accordé aux utilisateurs ayant un rôle de lecteur de sécurité dans Azure AD. 

Une personne ayant un rôle d’administrateur général Defender pour point de terminaison dispose d’un accès illimité à tous les appareils, quelle que soit l’association de leur groupe d’appareils et les affectations des groupes d’utilisateurs Azure AD.

> [!WARNING]
> Initialement, seules les personnes ayant des droits d’administrateur général Azure AD ou d’administrateur de sécurité pourront créer et attribuer des rôles dans le portail Microsoft 365 Defender. Par conséquent, il est important que les groupes soient prêts dans Azure AD.
>
> **Si vous lisez le contrôle d’accès basé sur un rôle, les utilisateurs ayant des autorisations en lecture seule (par exemple, les utilisateurs affectés au rôle lecteur Azure AD Security) perdent l’accès jusqu’à ce qu’ils soient affectés à un rôle.** 
>
>Le rôle d’administrateur général Defender for Endpoint intégré par défaut est automatiquement attribué aux utilisateurs ayant des autorisations d’administrateur avec des autorisations complètes. Après avoir choisi d’utiliser le contrôle d’accès en fonction du rôle, vous pouvez affecter d’autres utilisateurs qui ne sont pas des administrateurs globaux ou de sécurité Azure AD au rôle d’administrateur général Defender for Endpoint. 
>
> Après avoir choisi d’utiliser le RBAC, vous ne pouvez pas revenir aux rôles initiaux comme lorsque vous vous êtes connecté au portail pour la première fois.

## <a name="related-topic"></a>Rubrique connexe

- [Créer et gérer des groupes d’appareils dans Microsoft Defender pour le point de terminaison](machine-groups.md)
