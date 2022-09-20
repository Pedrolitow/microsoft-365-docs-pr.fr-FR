---
title: Attribuer l’accès utilisateur au centre de sécurité Microsoft Defender.
description: Attribuez un accès en lecture et en écriture ou en lecture seule au portail Microsoft Defender pour point de terminaison.
keywords: attribuer des rôles d’utilisateur, attribuer un accès en lecture et en écriture, attribuer un accès en lecture seule, utilisateur, rôles d’utilisateur, rôles
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.service: microsoft-365-security
ms.subservice: mde
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 1a02bcd596043ee27fc250f60ab68e627246bf62
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67811633"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>Attribuer l’accès utilisateur au centre de sécurité Microsoft Defender.

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Azure Active Directory
- Office 365
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Defender pour point de terminaison prend en charge deux façons de gérer les autorisations :

- **Gestion des autorisations de base** : définissez les autorisations sur un accès complet ou en lecture seule.
- **Contrôle d’accès en fonction du rôle (RBAC)** : définissez des autorisations granulaires en définissant des rôles, en attribuant des groupes d’utilisateurs Azure AD aux rôles et en accordant aux groupes d’utilisateurs l’accès aux groupes d’appareils. Pour plus d’informations sur RBAC, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).

> [!NOTE]
> Si vous avez déjà affecté des autorisations de base, vous pouvez basculer vers RBAC à tout moment. Prenez en compte les points suivants avant d’effectuer le commutateur :
>
> - Les utilisateurs disposant d’un accès complet (utilisateurs auxquels le rôle d’administrateur général ou d’administrateur de sécurité est attribué dans Azure AD) se voient automatiquement attribuer le rôle d’administrateur Defender pour point de terminaison par défaut, qui dispose également d’un accès complet. Des groupes d’utilisateurs Azure AD supplémentaires peuvent être affectés au rôle d’administrateur Defender pour point de terminaison après le basculement vers RBAC. Seuls les utilisateurs affectés au rôle d’administrateur Defender pour point de terminaison peuvent gérer les autorisations à l’aide de RBAC. 
> - Les utilisateurs disposant d’un accès en lecture seule (lecteurs de sécurité) perdront l’accès au portail jusqu’à ce qu’un rôle leur soit attribué. Notez que seuls les groupes d’utilisateurs Azure AD peuvent se faire attribuer un rôle sous RBAC.
> - Après avoir basculé vers RBAC, vous ne pourrez plus revenir à l’utilisation de la gestion des autorisations de base.

## <a name="related-topics"></a>Voir aussi

- [Utiliser des autorisations de base pour accéder au portail](basic-permissions.md)
- [Gérer l’accès au portail à l’aide de RBAC](rbac.md)
