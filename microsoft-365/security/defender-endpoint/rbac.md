---
title: Utiliser le contrôle d’accès basé sur les rôles pour accorder un accès fin au Microsoft 365 Defender web
description: Créez des rôles et des groupes au sein de vos opérations de sécurité pour accorder l’accès au portail.
keywords: rbac, role, based, access, control, groups, control, tier, aad
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8c1ff743aa6c9c215c3894185a4096c9a35a16e0
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2021
ms.locfileid: "61320826"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Gérer l’accès au portail à l’aide du contrôle d’accès basé sur un rôle

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Active Directory
- Office 365

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

À l’aide du contrôle d’accès basé sur un rôle (RBAC), vous pouvez créer des rôles et des groupes au sein de votre équipe des opérations de sécurité pour accorder un accès approprié au portail. En fonction des rôles et des groupes que vous créez, vous avez un contrôle fin sur ce que les utilisateurs ayant accès au portail peuvent voir et faire. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Les grandes équipes d’opérations de sécurité distribuées géographiquement adoptent généralement un modèle basé sur un niveau pour attribuer et autoriser l’accès aux portails de sécurité. Les niveaux classiques incluent les trois niveaux suivants :

Niveau|Description|
:---|:---|
Niveau 1|**Équipe des opérations de sécurité locale/équipe informatique** <br> Cette équipe trie et examine généralement les alertes contenues dans leur géolocalisation et atteint le niveau 2 dans les cas où une correction active est nécessaire.|
Niveau 2|**Équipe des opérations de sécurité régionales** <br> Cette équipe peut voir tous les appareils de leur région et effectuer des actions de correction.|
Niveau 3|**Équipe des opérations de sécurité globale** <br> Cette équipe est constituée d’experts en sécurité et est autorisée à voir et à effectuer toutes les actions à partir du portail.|

> [!NOTE]
> Pour les ressources de niveau [](/azure/active-directory/privileged-identity-management/pim-configure) 0, reportez-vous Privileged Identity Management aux administrateurs de sécurité pour fournir un contrôle plus granulaire de Microsoft Defender pour les points de terminaison et les Microsoft 365 Defender.  

Defender for Endpoint RBAC est conçu pour prendre en charge votre modèle de choix basé sur des rôles ou des niveaux et vous donne un contrôle granulaire sur les rôles qu’ils peuvent voir, les appareils accessibles et les actions qu’ils peuvent prendre. L’infrastructure RBAC est centrée autour des contrôles suivants :

- **Contrôler les personnes qui peuvent prendre des mesures spécifiques**
  - Créez des rôles personnalisés et contrôlez les fonctionnalités de Defender for Endpoint accessibles avec granularité.
- **Contrôler qui peut voir les informations sur un ou plusieurs groupes d’appareils spécifiques**
  - [Créez](machine-groups.md) des groupes d’appareils en fonction de critères spécifiques tels que des noms, des balises, des domaines et d’autres, puis accordez-leur l’accès au rôle à l’aide d’un groupe d’utilisateurs Azure Active Directory (Azure AD).

Pour implémenter l’accès basé sur les rôles, vous devez définir des rôles d’administrateur, attribuer les autorisations correspondantes et affecter Azure AD groupes d’utilisateurs affectés aux rôles.

### <a name="before-you-begin"></a>Avant de commencer

Avant d’utiliser le RBAC, il est important de comprendre les rôles qui peuvent accorder des autorisations et les conséquences de l’utilisation du RBAC.

> [!WARNING]
> Avant d’activer la fonctionnalité, il est important que vous disposez d’un rôle d’administrateur général ou d’administrateur de sécurité dans Azure AD et que vos groupes Azure AD sont prêts à réduire le risque d’être verrouillé du portail. 

Lorsque vous vous connectez pour la première fois au portail Microsoft 365 Defender, l’accès total ou l’accès en lecture seule vous est accordé. Les droits d’accès total sont accordés aux utilisateurs ayant des rôles Administrateur de sécurité ou Administrateur général dans Azure AD. L’accès en lecture seule est accordé aux utilisateurs ayant un rôle lecteur de sécurité dans Azure AD. 

Une personne ayant un rôle d’administrateur général Defender pour point de terminaison dispose d’un accès illimité à tous les appareils, quelle que soit l’association de leur groupe d’appareils et les Azure AD groupes d’utilisateurs.

> [!WARNING]
> À l’origine, seules les personnes ayant des droits d’administrateur général ou d’administrateur de sécurité Azure AD pourront créer et attribuer des rôles dans le portail Microsoft 365 Defender. Par conséquent, il est important de disposer des groupes prêts dans Azure AD.
>
> **Si vous lisez le contrôle d’accès basé sur un rôle, les utilisateurs ayant des autorisations en lecture seule (par exemple, les utilisateurs affectés au rôle de lecteur Azure AD Security) perdent l’accès jusqu’à ce qu’ils soient affectés à un rôle.** 
>
>Le rôle d’administrateur général Defender for Endpoint intégré par défaut est automatiquement attribué aux utilisateurs ayant des autorisations d’administrateur avec des autorisations complètes. Après avoir choisi d’utiliser RBAC, vous pouvez affecter des utilisateurs supplémentaires qui ne sont pas Azure AD administrateurs globaux ou de sécurité au rôle d’administrateur général Defender for Endpoint. 
>
> Après avoir choisi d’utiliser le RBAC, vous ne pouvez pas revenir aux rôles initiaux comme lorsque vous vous êtes connecté au portail pour la première fois.

## <a name="related-topic"></a>Rubrique connexe

- [Rôles RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Créer et gérer des groupes d’appareils dans Microsoft Defender pour le point de terminaison](machine-groups.md)
