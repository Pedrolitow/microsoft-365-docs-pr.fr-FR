---
title: Gérer l’accès aux données Microsoft 365 Defender dans le portail Microsoft 365 Defender
description: Découvrez comment gérer les autorisations sur les données dans Microsoft 365 Defender
keywords: access, permissions, Microsoft 365 Defender, M365, security, Defender for Cloud Apps, Microsoft Defender pour point de terminaison, scope, scoping, RBAC
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 6cb6f8897b6abfcba0d728baa0523cf9dddad2a1
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091012"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>Gérer l’accès à Microsoft 365 Defender avec des rôles globaux Azure Active Directory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Il existe deux façons de gérer l’accès à Microsoft 365 Defender :
- **Rôles Azure Active Directory (AD) globaux**
- **Accès au rôle personnalisé**

Les comptes auxquels les **rôles Azure Active Directory (AD) globaux suivants sont affectés** peuvent accéder à Microsoft 365 Defender fonctionnalités et données :
- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

Pour passer en revue les comptes avec ces [rôles, affichez les autorisations dans le portail Microsoft 365 Defender](https://security.microsoft.com/permissions).

**L’accès aux rôles personnalisés** est une nouvelle fonctionnalité dans Microsoft 365 Defender et vous permet de gérer l’accès à des données, des tâches et des fonctionnalités spécifiques dans Microsoft 365 Defender. Les rôles personnalisés offrent plus de contrôle que les rôles Azure AD globaux, en fournissant aux utilisateurs uniquement l’accès dont ils ont besoin avec les rôles les moins permissifs nécessaires.  Des rôles personnalisés peuvent être créés en plus des rôles Azure AD globaux. [En savoir plus sur les rôles personnalisés](custom-roles.md).

> [!NOTE]
> Cet article s’applique uniquement à la gestion des rôles Azure Active Directory globaux. Pour plus d’informations sur l’utilisation du contrôle d’accès en fonction du rôle personnalisé, consultez [Rôles personnalisés pour le contrôle d’accès en fonction du rôle](custom-roles.md)

## <a name="access-to-functionality"></a>Accéder aux fonctionnalités
L’accès à des fonctionnalités spécifiques est déterminé par votre[rôle Azure AD](/azure/active-directory/roles/permissions-reference). Contactez un administrateur général si vous avez besoin d’accéder à des fonctionnalités spécifiques qui nécessitent l'affectation d'un nouveau rôle à vous ou à votre groupe d'utilisateurs.

### <a name="approve-pending-automated-tasks"></a>Approuver les tâches automatisées en attente
[Un examen et correction automatisés](m365d-autoir-actions.md) peuvent prendre une action sur les e-mails, les règles de transfert, les fichiers, les mécanismes de persistance et d’autres artefacts détectés lors des examens. Pour approuver ou refuser les actions en attente qui nécessitent une autorisation explicite, vous devez avoir certains rôles affectés dans Microsoft 365. Si vous souhaitez en savoir plus, veuillez consulter[Autorisation du centre de notification](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Accès aux données
L’accès aux données Microsoft 365 Defender peut être contrôlé à l’aide de l’étendue affectée aux groupes d’utilisateurs dans Microsoft Defender pour point de terminaison contrôle d’accès en fonction du rôle (RBAC). Si votre accès n’a pas été limité à un ensemble spécifique d’appareils dans Defender pour point de terminaison, vous aurez un accès complet aux données dans Microsoft 365 Defender. Cependant, une fois votre compte étendu, vous verrez uniquement les données relatives aux appareils dans votre étendue.

Par exemple, si vous appartenez à un seul groupe d’utilisateurs doté d’un rôle Microsoft Defender pour point de terminaison et que ce groupe d’utilisateurs n’a accès qu’aux appareils commerciaux, seules les données relatives aux appareils commerciaux sont disponibles dans Microsoft 365 Defender. [En savoir plus sur les paramètres RBAC dans Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-defender-for-cloud-apps-access-controls"></a>Microsoft Defender for Cloud Apps contrôles d’accès
Pendant la préversion, Microsoft 365 Defender n’applique pas de contrôles d’accès basés sur les paramètres de Defender pour Cloud Apps. L’accès aux données Microsoft 365 Defender n’est pas affecté par ces paramètres.

## <a name="related-topics"></a>Voir aussi
- [Rôles personnalisés dans le contrôle d’accès en fonction du rôle pour Microsoft 365 Defender](custom-roles.md)
- [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference)
- [Microsoft Defender pour point de terminaison RBAC](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Rôles Defender pour Cloud Apps](/cloud-app-security/manage-admins)
