---
title: Microsoft 365 Defender conditions préalables
description: Découvrez les licences, la configuration matérielle et logicielle requise et d’autres paramètres de configuration pour Microsoft 365 Defender
keywords: requirements, prerequisites, hardware, software, browser, Microsoft 365 Defender, M365, license, E5, A5, EMS, purchase
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 3b56d407381633853ea683b50ac969f88f15ff45
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61373439"
---
# <a name="microsoft-365-defender-prerequisites"></a>Microsoft 365 Defender conditions préalables

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Découvrez les licences et autres conditions requises pour l’approvisionnement et [l’utilisation Microsoft 365 Defender](microsoft-365-defender.md).

## <a name="licensing-requirements"></a>Conditions d'octroi de licence
L’une de ces licences vous donne accès aux fonctionnalités Microsoft 365 Defender via le portail Microsoft 365 Defender sans frais supplémentaires :

- Microsoft 365 E5 ou A5
- Microsoft 365 E3 l’Microsoft 365 E5 Sécurité de module
- Microsoft 365 A3 avec le module Microsoft 365 A5 sécurité de l’Microsoft 365 A5
- Windows 10 Entreprise E5 ou A5
- Windows 11 Entreprise E5 ou A5
- Enterprise Mobility + Security (EMS) E5 ou A5 
- Office 365 E5 ou A5
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité 
- Microsoft Defender for Cloud Apps
- Defender pour Office 365 (Plan 2)

Pour plus d’informations, [consultez les plans Microsoft 365 Entreprise service.](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise)

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](../../commerce/try-or-buy-microsoft-365.md)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Go to Centre d'administration Microsoft 365 ([admin.microsoft.com](https://admin.microsoft.com/)) to view your existing licenses. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Vous devez avoir le  rôle  d’administrateur de facturation ou de lecteur global [dans Azure AD](/azure/active-directory/roles/permissions-reference) pour pouvoir voir les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être administrateur **général ou** **administrateur** de sécurité dans Azure Active Directory pour activer Microsoft 365 Defender. Pour obtenir la liste des rôles requis pour utiliser Microsoft 365 Defender et des informations sur la façon dont l’accès aux données est réglementé, consultez la liste des rôles nécessaires pour gérer [l’accès Microsoft 365 Defender](m365d-permissions.md).

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez Microsoft 365 Defender le portail Microsoft 365 Defender à l’aide de Microsoft Edge, d’Internet Explorer 11 ou de tout navigateur web conforme HTML 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité pour les Cloud de la communauté du secteur public américains, Cloud de la communauté du secteur public High et d’autres institutions gouvernementales américaines

Pour plus d’informations sur les clients du gouvernement des États-Unis, [voir Microsoft 365 Defender pour les clients du gouvernement des États-Unis.](usgov.md)

Actuellement, l’intégration de Microsoft Defender for Office 365 dans les fonctionnalités de Microsoft 365 Defender unifiée n’est pas disponible pour les clients dans les emplacements Office 365 de centre de données suivants :

- Brésil 
- Allemagne 
- Norvège 
- Singapour 
- Afrique du Sud
- Suisse 
- Émirats arabes unis 


## <a name="related-topics"></a>Voir aussi
- [Microsoft 365 Defender vue d’ensemble](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Gérer l’accès et les autorisations](m365d-permissions.md)
