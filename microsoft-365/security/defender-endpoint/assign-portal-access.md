---
title: Attribuer à l’utilisateur l’accès Centre de sécurité Microsoft Defender
description: Attribuez un accès en lecture et en écriture ou en lecture seule au portail Microsoft Defender for Endpoint.
keywords: attribuer des rôles d’utilisateur, attribuer un accès en lecture et en écriture, attribuer un accès en lecture seule, utilisateur, rôles d’utilisateur, rôles
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
ms.date: 11/28/2018
ms.technology: mde
ms.openlocfilehash: 0970314509efbcfad79d7f9f52f5ae3605f3d8fe538a18b142340fe6a2cf8d1f
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53857822"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>Attribuer à l’utilisateur l’accès Centre de sécurité Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- Azure Active Directory
- Office 365
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Defender pour le point de terminaison prend en charge deux méthodes de gestion des autorisations :

- **Gestion des autorisations de base**: définissez les autorisations en accès total ou en lecture seule.
- Contrôle d’accès basé sur les rôles **:** définissez des autorisations granulaires en définissant des rôles, en attribuant des groupes d’utilisateurs Azure AD aux rôles et en accordant aux groupes d’utilisateurs l’accès aux groupes d’appareils. Pour plus d’informations sur le contrôle d’accès basé sur un rôle, voir Gérer l’accès au portail à l’aide du contrôle [d’accès basé sur un rôle.](rbac.md)

> [!NOTE]
> Si vous avez déjà attribué des autorisations de base, vous pouvez basculer vers RBAC à tout moment. Prenez en compte les considérations suivantes avant d’effectuer le basculement :
> 
> - Les utilisateurs ayant un accès total (utilisateurs affectés au rôle d’administrateur général ou d’administrateur de sécurité dans Azure AD) se voit automatiquement attribuer le rôle d’administrateur Defender pour point de terminaison par défaut, qui dispose également d’un accès total. Des groupes d’utilisateurs Azure AD supplémentaires peuvent être affectés au rôle d’administrateur Defender for Endpoint après le passage au RBAC.  Seuls les utilisateurs affectés au rôle d’administrateur Defender pour le point de terminaison peuvent gérer les autorisations à l’aide du contrôle d’accès en fonction du rôle. 
> - Les utilisateurs qui ont un accès en lecture seule (lecteurs de sécurité) perdent l’accès au portail tant qu’un rôle ne leur est pas attribué. Notez que seuls les groupes d’utilisateurs Azure AD peuvent se voir attribuer un rôle sous RBAC.
> - Après avoir basé vers RBAC, vous ne pourrez pas revenir à l’utilisation de la gestion des autorisations de base.

## <a name="related-topics"></a>Sujets connexes

- [Utiliser des autorisations de base pour accéder au portail](basic-permissions.md)
- [Gérer l’accès au portail à l’aide de RBAC](rbac.md)
