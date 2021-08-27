---
title: Gérer l’accès Microsoft 365 Defender données dans le portail Microsoft 365 Defender web
description: Découvrez comment gérer les autorisations d’accès aux données dans Microsoft 365 Defender
keywords: access, permissions, Microsoft 365 Defender, M365, security, MCAS, Sécurité des applications cloud, Microsoft Defender for Endpoint, scope, scoping, RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 7a4176e5b375c32edb1e1fae3ab74f0760f28366
ms.sourcegitcommit: 132b8dc316bcd4b456de33d6a30e90ca69b0f956
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58595149"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>Gérer l’accès aux Microsoft 365 Defender avec Azure Active Directory rôles globaux

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Il existe deux façons de gérer l’accès Microsoft 365 Defender
- **Rôles Azure Active Directory (AD) globaux**
- **Accès aux rôles personnalisés**

Les comptes affectés aux rôles **Azure Active Directory global (AD)** suivants peuvent accéder aux Microsoft 365 Defender et aux données suivantes :
- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

Pour passer en revue les comptes avec ces [rôles, affichez les autorisations](https://security.microsoft.com/permissions)dans le portail Microsoft 365 Defender.

**L’accès** aux rôles personnalisés est une nouvelle fonctionnalité de Microsoft 365 Defender et vous permet de gérer l’accès à des données, des tâches et des fonctionnalités spécifiques dans Microsoft Defender 365. Les rôles personnalisés offrent plus de contrôle que les rôles Azure AD globaux, fournissant aux utilisateurs uniquement l’accès dont ils ont besoin avec les rôles les moins permissifs nécessaires.  Les rôles personnalisés peuvent être créés en plus des rôles Azure AD globaux. [En savoir plus sur les rôles personnalisés.](custom-roles.md)

> [!NOTE]
> Cet article s’applique uniquement à la gestion des rôles Azure Active Directory globaux. Pour plus d’informations sur l’utilisation du contrôle d’accès basé sur un rôle personnalisé, voir [Rôles](custom-roles.md) personnalisés pour le contrôle d’accès basé sur un rôle

## <a name="access-to-functionality"></a>Accéder aux fonctionnalités
L’accès à des fonctionnalités spécifiques est déterminé par votre[rôle Azure AD](/azure/active-directory/roles/permissions-reference). Contactez un administrateur général si vous avez besoin d’accéder à des fonctionnalités spécifiques qui nécessitent l'affectation d'un nouveau rôle à vous ou à votre groupe d'utilisateurs.

### <a name="approve-pending-automated-tasks"></a>Approuver les tâches automatisées en attente
[Un examen et correction automatisés](m365d-autoir-actions.md) peuvent prendre une action sur les e-mails, les règles de transfert, les fichiers, les mécanismes de persistance et d’autres artefacts détectés lors des examens. Pour approuver ou refuser les actions en attente qui nécessitent une autorisation explicite, vous devez avoir certains rôles affectés dans Microsoft 365. Si vous souhaitez en savoir plus, veuillez consulter[Autorisation du centre de notification](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Accès aux données
L’accès Microsoft 365 Defender données peut être contrôlé à l’aide de l’étendue attribuée aux groupes d’utilisateurs dans Microsoft Defender for Endpoint role-based access control (RBAC). Si votre accès n’a pas été limité à un ensemble spécifique d’appareils dans Defender for Endpoint, vous aurez un accès total aux données dans Microsoft 365 Defender. Cependant, une fois votre compte étendu, vous verrez uniquement les données relatives aux appareils dans votre étendue.

Par exemple, si vous n’appartenez qu’à un seul groupe d’utilisateurs avec un rôle Microsoft Defender pour point de terminaison et que ce groupe d’utilisateurs n’a accès qu’aux appareils commerciaux, vous ne verrez que les données relatives aux appareils de vente dans Microsoft 365 Defender. [En savoir plus sur les paramètres RBAC dans Microsoft Defender pour endpoint](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-cloud-app-security-access-controls"></a>Contrôles d'accès Microsoft Cloud App Security (MCAS)
Pendant la prévisualisation, Microsoft 365 Defender n’applique pas les contrôles d’accès basés sur Sécurité des applications cloud paramètres. L’accès Microsoft 365 Defender données n’est pas affecté par ces paramètres.

## <a name="related-topics"></a>Voir aussi
- [Rôles personnalisés dans le contrôle d’accès basé sur les rôles pour Microsoft 365 Defender](custom-roles.md)
- [Rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference)
- [Microsoft Defender pour point de terminaison RBAC](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Rôles des sécurité de l’application cloud](/cloud-app-security/manage-admins)
