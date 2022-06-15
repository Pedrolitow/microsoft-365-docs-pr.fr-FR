---
title: Configuration requise pour Microsoft Defender pour entreprises
description: Microsoft Defender pour entreprises la configuration requise pour les licences, le matériel et les logiciels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ab24e3898d897df6813338fd0d2131c3787f0a09
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089581"
---
# <a name="microsoft-defender-for-business-requirements"></a>exigences de Microsoft Defender pour entreprises

Cet article décrit les conditions requises pour Microsoft Defender pour entreprises.

## <a name="what-to-do"></a>Procédure

1. [Passez en revue les exigences et assurez-vous de les respecter](#review-the-requirements).
2. [Passez à vos étapes suivantes](#next-steps).


## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les exigences de base pour configurer et utiliser Microsoft Defender pour entreprises.

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium ou Microsoft Defender pour entreprises (autonome). Découvrez [comment obtenir Microsoft Defender pour entreprises](get-defender-business.md).<br/><br/>Notez que si vous avez plusieurs abonnements, l’abonnement le plus élevé est prioritaire. Par exemple, si vous avez Microsoft Defender pour point de terminaison plan 2 (abonnement acheté ou d’évaluation) et que vous obtenez Microsoft Defender pour entreprises, Defender pour point de terminaison Plan 2 est prioritaire. Dans ce cas, vous ne verrez pas l’expérience Defender entreprise.  |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |
| Comptes d’utilisateur | - Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>- Microsoft Defender pour entreprises licences sont attribuées dans le Centre d'administration Microsoft 365<br/><br/>Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences](mdb-add-users.md). |
| Autorisations  | Pour vous inscrire à Microsoft Defender pour entreprises, vous devez être un Administration global.<br/><br/>Pour accéder au portail Microsoft 365 Defender, l’un des rôles suivants doit être attribué [aux utilisateurs dans Azure AD](mdb-roles-permissions.md) : <br/>- Lecteur sécurité<br/>- Administration de sécurité<br/>- Administration globale<br/><br/>Pour en savoir plus, consultez [Rôles et autorisations dans Microsoft Defender pour entreprises](mdb-roles-permissions.md). |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation | Pour gérer les appareils dans le portail Microsoft 365 Defender, vos appareils doivent exécuter l’un des systèmes d’exploitation suivants : <br/>- Windows 10 Business ou version ultérieure <br/>- Windows 10 Professional ou version ultérieure <br/>- Windows 10 Entreprise ou version ultérieure <br/>- macOS (les trois versions les plus actuelles sont prises en charge)<br/><br/>Vérifiez que [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installé sur Windows appareils. <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune, vous pouvez continuer à utiliser le centre d’administration Microsoft Endpoint Manager. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) est utilisé pour gérer les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender entreprise. 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD est approvisionné pour vous pendant le processus d’activation. 
> - Si vous avez un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous pouvez utiliser votre service Azure AD existant. 
> - Si vous utilisez [Microsoft 365 Business Premium](../../business/index.yml) lorsque vous démarrez votre version d’évaluation de Defender entreprise, vous avez la possibilité de gérer vos appareils à l’aide de Intune. 

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 2 : Attribuer des rôles et des autorisations dans Microsoft Defender pour entreprises](mdb-roles-permissions.md).
 
