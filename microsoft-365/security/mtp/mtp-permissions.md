---
title: Gérer l’accès aux données de Protection contre menaces dans le Centre de sécurité Microsoft 365
description: Découvrir comment gérer les autorisations d’accès aux données dans Protection Microsoft contre les menaces
keywords: accès, autorisations, MTP, Protection Microsoft contre les menaces, M365, sécurité, MCAS, MDATP, Cloud App Security, Microsoft Defender – Protection avancée contre les menaces, étendue, contrôle, RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: df4450271b7cbbd1862b86cbed295c88c168d66d
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911056"
---
# <a name="manage-access-to-microsoft-threat-protection"></a>Gérer l’accès à la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

Les comptes affectés aux rôles Azure Active Directory (AD) suivants peuvent accéder aux fonctionnalités et données de la Protection Microsoft contre les menaces :
- Administrateur général
- Administrateur de sécurité
- Opérateur de sécurité
- Lecteur général
- Lecteur de sécurité

Pour examiner les comptes avec ces rôles, [afficher les autorisations dans le Centre de sécurité Microsoft 365](https://security.microsoft.com/permissions).

## <a name="access-to-functionality"></a>Accéder aux fonctionnalités
L’accès à des fonctionnalités spécifiques est déterminé par votre[rôle Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). Contactez un administrateur général si vous avez besoin d’accéder à des fonctionnalités spécifiques qui nécessitent l'affectation d'un nouveau rôle à vous ou à votre groupe d'utilisateurs.

### <a name="approve-pending-automated-tasks"></a>Approuver les tâches automatisées en attente
[Un examen et correction automatisés](mtp-autoir-actions.md) peuvent prendre une action sur les e-mails, les règles de transfert, les fichiers, les mécanismes de persistance et d’autres artefacts détectés lors des examens. Pour approuver ou refuser les actions en attente qui nécessitent une autorisation explicite, vous devez avoir certains rôles affectés dans Microsoft 365. Si vous souhaitez en savoir plus, veuillez consulter[Autorisation du centre de notification](mtp-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>Accès aux données
L'accès aux données de la Protection Microsoft contre les menaces peut être contrôlé à l'aide de l'étendue affectée aux groupes d'utilisateurs dans le contrôle d'accès basé sur le rôle Microsoft Defender - Protection avancée contre les menaces (RBAC). Si votre accès n’a pas été étendu à un ensemble spécifique d’appareils dans Microsoft Defender - Protection avancée contre les menaces, vous disposerez d’un accès total aux données dans la Protection Microsoft contre les menaces. Cependant, une fois votre compte étendu, vous verrez uniquement les données relatives aux appareils dans votre étendue.

Par exemple, si vous appartenez à un seul groupe d’utilisateurs avec un rôle Microsoft Defender - Protection avancée contre les menaces et que ce groupe d’utilisateurs n’a accès qu’aux appareils de vente, vous ne verrez que les données sur les appareils commerciaux dans Protection Microsoft contre les menaces. [Apprenez-en davantage sur paramètres RBAC dans Microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-cloud-app-security-access-controls"></a>Contrôles d'accès Microsoft Cloud App Security (MCAS)
Pendant l’aperçu, la Protection Microsoft contre les menaces n’applique pas les contrôles d’accès basés sur les paramètres Cloud App Security. L’accès aux données de la Protection Microsoft contre les menaces n’est pas affecté par ces paramètres.

## <a name="related-topics"></a>Sujets associés

- [Rôles Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)
- [Microsoft Defender - PACM RBAC](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Rôles des sécurité de l’application cloud](https://docs.microsoft.com/cloud-app-security/manage-admins)