---
title: Microsoft 365 Defender prérequis
description: Découvrez les licences, les exigences matérielles et logicielles, ainsi que d’autres paramètres de configuration pour Microsoft 365 Defender
keywords: configuration requise, conditions préalables, matériel, logiciel, navigateur, Microsoft 365 Defender, M365, licence, E5, A5, EMS, achat
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: f7977ba847036350747347063ab1bba8f8866f53
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479729"
---
# <a name="microsoft-365-defender-prerequisites"></a>Microsoft 365 Defender prérequis

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Découvrez les licences et d’autres conditions requises pour l’approvisionnement et l’utilisation [de Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="licensing-requirements"></a>Conditions d'octroi de licence
L’une de ces licences vous donne accès à Microsoft 365 Defender fonctionnalités via le portail Microsoft 365 Defender sans frais supplémentaires :

- Microsoft 365 E5 ou A5
- Microsoft 365 E3 avec le module complémentaire Microsoft 365 E5 Sécurité
- Microsoft 365 E3 avec le module complémentaire Enterprise Mobility + Security E5
- Microsoft 365 A3 avec le module complémentaire sécurité Microsoft 365 A5
- Windows 10 Entreprise E5 ou A5
- Windows 11 Entreprise E5 ou A5
- Enterprise Mobility + Security (EMS) E5 ou A5 
- Office 365 E5 ou A5
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité 
- Microsoft Defender for Cloud Apps
- Defender pour Office 365 (Plan 2)

Pour plus d’informations, [consultez les plans de service Microsoft 365 Entreprise](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](../../commerce/try-or-buy-microsoft-365.md)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Accédez à Centre d'administration Microsoft 365 ([admin.microsoft.com](https://admin.microsoft.com/)) pour afficher vos licences existantes. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Vous devez disposer du rôle **d’administrateur de facturation** ou de **lecteur général** [dans Azure AD](/azure/active-directory/roles/permissions-reference) pour pouvoir voir les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être **administrateur général** ou **administrateur de sécurité** dans Azure Active Directory pour activer Microsoft 365 Defender. Pour obtenir la liste des rôles requis pour utiliser Microsoft 365 Defender et des informations sur la façon dont l’accès aux données est réglementé, consultez la [gestion de l’accès à Microsoft 365 Defender](m365d-permissions.md).

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez Microsoft 365 Defender dans le portail Microsoft 365 Defender à l’aide de Microsoft Edge, d’Internet Explorer 11 ou de tout navigateur web compatible HTML 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité pour le GCC, GCC High et d’autres institutions gouvernementales des États-Unis

Pour plus d’informations sur les clients du gouvernement des États-Unis, consultez [Microsoft 365 Defender pour les clients du gouvernement des États-Unis](usgov.md).

Actuellement, l’intégration Microsoft Defender pour Office 365 aux fonctionnalités de Microsoft 365 Defender unifiées n’est pas disponible pour les clients dans les emplacements de centre de données Office 365 suivants :

- Norvège 
- Afrique du Sud 
- Émirats arabes unis 
- Suède 
- Singapour 


## <a name="related-topics"></a>Voir aussi
- [vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Gérer l’accès et les autorisations](m365d-permissions.md)
