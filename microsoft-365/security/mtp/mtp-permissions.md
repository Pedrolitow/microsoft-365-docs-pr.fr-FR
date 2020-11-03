---
title: Gérer l’accès aux données Microsoft 365 Defender dans le centre de sécurité Microsoft 365
description: Découvrez comment gérer les autorisations d’accès aux données dans Microsoft 365 Defender
keywords: accès, autorisations, MTP, Protection Microsoft contre les menaces, M365, sécurité, MCAS, MDATP, Cloud App Security, Microsoft Defender – Protection avancée contre les menaces, étendue, contrôle, RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
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
ms.openlocfilehash: 55b7b8c5755b773a4d53c95017a0a17a85495dee
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48847247"
---
# <a name="manage-access-to-microsoft-365-defender"></a>Gérer l’accès à Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Comptes affectés les rôles Azure Active Directory (AD) suivants peuvent accéder aux fonctionnalités et aux données de Microsoft 365 Defender :
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
L’accès aux données Microsoft 365 Defender peut être contrôlé à l’aide de l’étendue affectée aux groupes d’utilisateurs dans Microsoft Defender pour le contrôle d’accès basé sur un rôle de point de terminaison (RBAC). Si votre accès n’est pas inclus dans l’étendue d’un ensemble spécifique d’appareils dans l’application Defender pour le point de terminaison, vous aurez un accès complet aux données dans Microsoft 365 Defender. Cependant, une fois votre compte étendu, vous verrez uniquement les données relatives aux appareils dans votre étendue.

Par exemple, si vous appartenez à un seul groupe d’utilisateurs avec un rôle Microsoft Defender pour le point de terminaison et que ce groupe d’utilisateurs a été autorisé à accéder uniquement aux appareils de vente, vous verrez uniquement les données sur les périphériques de vente dans Microsoft 365 Defender. [En savoir plus sur les paramètres RBAC dans Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-cloud-app-security-access-controls"></a>Contrôles d'accès Microsoft Cloud App Security (MCAS)
Pendant l’aperçu, Microsoft 365 Defender n’applique pas les contrôles d’accès basés sur les paramètres de sécurité de l’application Cloud. L’accès aux données Microsoft 365 Defender n’est pas affecté par ces paramètres.

## <a name="related-topics"></a>Sujets associés

- [Rôles Azure AD](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles)
- [Microsoft Defender pour le RBAC de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [Rôles des sécurité de l’application cloud](https://docs.microsoft.com/cloud-app-security/manage-admins)
