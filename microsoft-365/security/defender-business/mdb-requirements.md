---
title: Configuration requise pour Microsoft Defender pour les PME
description: Microsoft Defender pour les PME la configuration requise pour les licences, le matériel et les logiciels
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: dd30af8003e6c5bc6a4348efe16626d2d45317f1
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64747070"
---
# <a name="microsoft-defender-for-business-requirements"></a>Microsoft Defender pour les PME exigences

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement pour les clients et les partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici. 

Cet article décrit les conditions requises pour Microsoft Defender pour les PME.

## <a name="what-to-do"></a>Procédure

1. [Passez en revue les exigences et assurez-vous de les respecter](#review-the-requirements).

2. [Passez à vos étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">court sondage sur Microsoft Defender pour les PME</a>. Vos commentaires sont les bienvenus.
>

## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les exigences de base pour configurer et utiliser Microsoft Defender pour les PME. <br/><br/>

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium <br/>--- ou ---<br/>Microsoft Defender pour les PME (autonome ; actuellement en préversion). <br/><br/> Découvrez [comment obtenir Microsoft Defender pour les PME](get-defender-business.md).<br/><br/>Notez que si vous avez plusieurs abonnements, l’abonnement le plus élevé est prioritaire. Par exemple, si vous avez Microsoft Defender pour point de terminaison plan 2 (abonnement acheté ou d’évaluation) et que vous obtenez Microsoft Defender pour les PME, Defender pour point de terminaison Plan 2 est prioritaire. Dans ce cas, vous ne verrez pas l’expérience Defender entreprise.  |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |
| Comptes d’utilisateur | Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender pour les PME licences sont attribuées dans le Centre d'administration Microsoft 365<br/><br/>Pour obtenir de l’aide sur cette tâche, consultez [Ajouter des utilisateurs et attribuer des licences](../../admin/add-users/add-users.md). |
| Autorisations  | Pour vous inscrire à Microsoft Defender pour les PME, vous devez être administrateur général.<br/><br/>Pour accéder au portail Microsoft 365 Defender, les utilisateurs doivent avoir l’un des [rôles suivants dans Azure AD](mdb-roles-permissions.md) attribués : <br/>- Lecteur sécurité<br/>- Administrateur de sécurité<br/>- Administrateur général<br/><br/>Pour en savoir plus, consultez [Rôles et autorisations dans Microsoft Defender pour les PME](mdb-roles-permissions.md). |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation | Pour gérer les appareils dans Microsoft Defender pour les PME, vos appareils doivent exécuter l’un des systèmes d’exploitation suivants : <br/>- Windows 10 Business ou version ultérieure <br/>- Windows 10 Professional ou version ultérieure <br/>- Windows 10 Entreprise ou version ultérieure <br/><br/>Vérifiez que [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installé. <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune (ou Microsoft Endpoint Manager), vous pouvez intégrer ces appareils à Defender entreprise. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) est utilisé pour gérer les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender Entreprise. 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD sera provisionné pour vous pendant le processus d’activation. 
> - Si vous avez un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous pouvez utiliser votre service Azure AD existant. 
> - Si vous utilisez [Microsoft 365 Business Premium](../../business/index.yml) lorsque vous démarrez votre version d’évaluation de Defender Entreprise, vous avez la possibilité de gérer les appareils dans Microsoft Intune. 

## <a name="next-steps"></a>Prochaines étapes

Passez à [l’étape 2 : Attribuer des rôles et des autorisations dans Microsoft Defender pour les PME](mdb-roles-permissions.md).
 