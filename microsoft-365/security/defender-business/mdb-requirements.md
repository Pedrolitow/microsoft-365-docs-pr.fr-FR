---
title: Conditions requises pour Microsoft Defender pour les entreprises (prévisualisation)
description: Configuration requise pour la licence, le matériel et les logiciels microsoft Defender pour les entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/08/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 519fd95a712d92760bf0963438aac4a0ea4ab471
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62465158"
---
# <a name="microsoft-defender-for-business-preview-requirements"></a>Conditions requises pour Microsoft Defender pour les entreprises (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Cet article décrit les conditions requises pour Microsoft Defender entreprise (prévisualisation).

## <a name="what-to-do"></a>Procédure

1. [Examinez les conditions requises et assurez-vous de les respecter](#review-the-requirements).

2. [Procédez comme vous le faire pour les étapes suivantes](#next-steps).

## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les conditions de base requises pour configurer et utiliser Microsoft Defender pour les entreprises (prévisualisation). <br/><br/>

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft Defender pour Les Entreprises (actuellement en prévisualisation !). Découvrez [comment obtenir Microsoft Defender pour les entreprises (prévisualisation).](get-defender-business.md)<br/><br/>**Vous n’êtes pas obligé d’avoir un autre abonnement Microsoft 365 pour essayer Microsoft Defender entreprise** (prévisualisation).<br/><br/>Si vous avez plusieurs abonnements, l’abonnement le plus élevé est prioritaire. Par exemple, si vous avez Microsoft Defender pour Endpoint Plan 2 (achat ou abonnement d’évaluation) et que vous obtenez Microsoft Defender pour Entreprise (prévisualisation), Defender pour Endpoint Plan 2 est prioritaire. Dans ce cas, vous ne verrez pas l’expérience De Defender entreprise (prévisualisation).  |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |
| Comptes d’utilisateur | Les comptes d’utilisateur sont créés dans le Centre d'administration Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Les licences Microsoft Defender pour Entreprise (prévisualisation) sont affectées dans le Centre d'administration Microsoft 365<br/><br/>Pour obtenir de l’aide sur cette tâche, voir [Ajouter des utilisateurs et attribuer des licences](../../admin/add-users/add-users.md). |
| Autorisations  | Pour vous inscrire à Microsoft Defender pour les entreprises (prévisualisation), vous devez être un administrateur global.<br/><br/>Pour accéder au portail Microsoft 365 Defender, les utilisateurs doivent avoir l’un des rôles suivants [Azure AD](mdb-roles-permissions.md) affectés : <br/>- Lecteur sécurité<br/>- Administrateur de sécurité<br/>- Administrateur général<br/><br/>Pour en savoir plus, consultez [Rôles et autorisations dans Microsoft Defender entreprise (prévisualisation).](mdb-roles-permissions.md) |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation | Pour gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation), vos appareils doivent être en cours d’exécution sur l’un des systèmes d’exploitation suivants : <br/>- Windows 10 Business ou ultérieure <br/>- Windows 10 Professional ou ultérieure <br/>- Windows 10 Entreprise ou ultérieure <br/><br/>Assurez-vous [que la KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) est installée. <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune (ou Microsoft Endpoint Manager), ou si vous utilisez une solution de gestion des appareils autre que Microsoft, vos appareils doivent utiliser l’un des systèmes d’exploitation pris en charge dans [Microsoft Defender pour Endpoint](../defender-endpoint/minimum-requirements.md). |
| Intégration à Microsoft Endpoint Manager  |  **Pendant la prévisualisation, vous pouvez intégrer des appareils à l’aide d’un script local, qui ne nécessite pas d’intégration avec Microsoft Endpoint Manager**. Toutefois, si vous envisagez d’intégrer manuellement des appareils à Defender for Business (prévisualisation) à l’aide de packages téléchargeables pour Microsoft Endpoint Manager, stratégie de groupe, System Center Configuration Manager ou Gestion des appareils mobiles, les conditions suivantes doivent être remplies : <br/><br/>Les appareils doivent être Windows 10 ou 11 Professional/Enterprise (avec l’application [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541)). <br/><br/>Les conditions préalables doivent être remplies [pour la gestion de la sécurité pour Microsoft Defender pour le point de terminaison](/mem/intune/protect/mde-security-integration).<br/>- Azure AD doivent être configurées de telle manière que l’relation d’confiance soit créée entre les appareils de votre organisation et les Azure AD. <br/>- La gestion de la sécurité doit être activée dans Defender for Business (prévisualisation) dans Microsoft Endpoint Manager.<br/><br/>Les appareils doivent pouvoir se connecter aux URL suivantes :<br/>- `enterpriseregistration.windows.net`(pour l’inscription dans Azure AD)<br/>- `login.microsoftonline.com`(pour l’inscription dans Azure AD)<br/>- `*.dm.microsoft.com` (Le caractère générique (*) prend en charge les points de terminaison du service cloud qui sont utilisés pour l’inscription, l’enregistrement et les rapports, et peut changer à mesure que le service est à l’échelle.) |

> [!NOTE]
> [Azure Active Directory (Azure AD) permet](/azure/active-directory/fundamentals/active-directory-whatis) de gérer les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender entreprise (prévisualisation). 
> - Si vous n’avez pas d’abonnement Microsoft 365 avant de commencer votre version d’évaluation, Azure AD sera mise en service pendant le processus d’activation. 
> - Si vous avez un autre abonnement Microsoft 365 lorsque vous démarrez votre version d’essai de Defender pour Entreprise (prévisualisation), vous pouvez utiliser votre service Azure AD existant. 
> - Si vous [utilisez Microsoft 365 Business Premium lorsque](../../business/index.yml) vous démarrez votre version d’essai de Defender pour Entreprise (prévisualisation), vous avez la possibilité de gérer les appareils dans Microsoft Intune. 

## <a name="next-steps"></a>Prochaines étapes

Procédez comme il se doit pour :

- [Étape 2 : Attribuer des rôles et des autorisations dans Microsoft Defender entreprise (prévisualisation)](mdb-roles-permissions.md) 
 
