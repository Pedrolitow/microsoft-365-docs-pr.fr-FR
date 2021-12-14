---
title: Conditions requises pour Microsoft Defender pour les entreprises (prévisualisation)
description: Configuration requise pour la licence, le matériel et les logiciels microsoft Defender pour les entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/10/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 416f0041e6da00fbf277e2281fb26519da3b34f2
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61422038"
---
# <a name="microsoft-defender-for-business-preview-requirements"></a>Conditions requises pour Microsoft Defender pour les entreprises (prévisualisation)

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Cet article décrit les conditions requises pour Microsoft Defender entreprise (prévisualisation).

## <a name="what-to-do"></a>Procédure

1. [Examinez les conditions requises et assurez-vous que vous les respectez.](#review-the-requirements)

2. [Procédez comme vous le faire pour les étapes suivantes.](#next-steps)

## <a name="review-the-requirements"></a>Consultez la configuration requise

Le tableau suivant répertorie les conditions de base requises pour configurer et utiliser Microsoft Defender pour les entreprises (prévisualisation). <br/><br/>

| Conditions requises | Description |
|:---|:---|
| Abonnement | Microsoft Defender pour Les Entreprises (actuellement en prévisualisation !). Découvrez [comment obtenir Microsoft Defender pour les entreprises (prévisualisation).](get-defender-business.md)<br/><br/>Vous n’êtes pas obligé d’avoir un autre abonnement Microsoft 365 pour essayer Microsoft Defender entreprise (prévisualisation). |
| Datacenter | L’un des emplacements de centre de données suivants : <br/>- Union européenne <br/>- Royaume-Uni <br/>- États-Unis |
| Azure Active Directory Domain Services (Azure AD) | Azure AD est nécessaire pour les autorisations utilisateur et les groupes d’appareils. Azure AD est inclus dans votre abonnement Defender entreprise (prévisualisation). Pour en savoir plus, [consultez La Azure AD ?](/azure/active-directory/fundamentals/active-directory-whatis) |
| Comptes d’utilisateur | Les comptes d’utilisateur sont créés<br/><br/>Des licences Microsoft Defender pour Les Entreprises (prévisualisation) sont affectées <br/><br/>Pour obtenir de l’aide, voir [Ajouter des utilisateurs et attribuer des licences.](../../admin/add-users/add-users.md) |
| Autorisations  | Pour vous inscrire à Microsoft Defender pour les entreprises (prévisualisation), vous devez être administrateur global du client de votre entreprise.<br/><br/>Pour accéder au portail Microsoft 365 Defender, les utilisateurs doivent avoir l’un des rôles suivants [Azure AD](mdb-roles-permissions.md) affectés : <br/>- Lecteur sécurité<br/>- Administrateur de sécurité<br/>- Administrateur général<br/><br/>Pour en savoir plus, consultez [Rôles et autorisations dans Microsoft Defender entreprise (prévisualisation).](mdb-roles-permissions.md) |
| Configuration requise pour le navigateur | Microsoft Edge ou Google Chrome |
| Système d’exploitation | Pour gérer les appareils dans Microsoft Defender pour Entreprises (prévisualisation), vos appareils doivent être en cours d’exécution Windows 10 Professional/Enterprise ou version ultérieure (avec [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541)). <br/><br/>Si vous gérez déjà des appareils dans Microsoft Intune (ou Microsoft Endpoint Manager), ou si vous utilisez une solution de gestion des appareils autre que Microsoft, vos appareils doivent utiliser l’un des systèmes d’exploitation pris en charge dans [Microsoft Defender pour Endpoint.](../defender-endpoint/minimum-requirements.md) |
| Intégration à Microsoft Endpoint Manager  |  **Pendant la prévisualisation, vous pouvez intégrer des appareils à l’aide d’un script local. Dans ce cas, les conditions préalables à l’intégration avec les Microsoft Endpoint Manager** répertoriées ici ne sont pas requises. Toutefois, si vous envisagez d’intégrer manuellement des appareils à Defender for Business (prévisualisation) à l’aide de packages téléchargeables pour Microsoft Endpoint Manager, stratégie de groupe, System Center Configuration Manager ou Gestion des appareils mobiles, les conditions suivantes doivent être remplies : <br/><br/>Les appareils doivent être Windows 10 ou 11 Professional/Enterprise (avec l’application [KB5006738).](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) <br/><br/>Les conditions préalables doivent être remplies [pour la gestion de la sécurité pour Microsoft Defender pour le point de terminaison.](/mem/intune/protect/mde-security-integration)<br/>- Azure AD doivent être configurées de telle manière que l’relation d’confiance soit créée entre les appareils de votre entreprise et les Azure AD. <br/>- La gestion de la sécurité doit être activée dans Defender for Business (prévisualisation) dans Microsoft Endpoint Manager.<br/><br/>Les appareils doivent pouvoir se connecter aux URL suivantes :<br/>- `enterpriseregistration.windows.net`(pour l’inscription dans Azure AD)<br/>- `login.microsoftonline.com`(pour l’inscription dans Azure AD)<br/>- `*.dm.microsoft.com` (Le caractère générique (*) prend en charge les points de terminaison du service cloud qui sont utilisés pour l’inscription, l’enregistrement et les rapports, et peut changer à mesure que le service est à l’échelle.) |


## <a name="next-steps"></a>Prochaines étapes

Procédez comme il se doit pour :

- [Étape 2 : Attribuer des rôles et des autorisations dans Microsoft Defender entreprise (prévisualisation)](mdb-roles-permissions.md) 
 