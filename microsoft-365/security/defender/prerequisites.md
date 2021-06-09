---
title: Microsoft 365 Conditions préalables de Defender
description: En savoir plus sur les licences, la configuration matérielle et logicielle requise et les autres paramètres de configuration pour Microsoft 365 Defender
keywords: configuration requise, conditions préalables, matériel, logiciel, navigateur, Microsoft 365 Defender, M365, licence, E5, A5, EMS, achat
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: f3fd597181d73c1768057ea7740ab111e5af2068
ms.sourcegitcommit: 82a4d74020cd93ba444006317cfecc178c6d41dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52689156"
---
# <a name="microsoft-365-defender-prerequisites"></a>Microsoft 365 Conditions préalables de Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Découvrez les licences et autres conditions requises pour l’approvisionnement et [l’utilisation Microsoft 365 Defender.](microsoft-365-defender.md)

## <a name="licensing-requirements"></a>Conditions d'octroi de licence
L’une de ces licences vous permet d’accéder aux fonctionnalités Microsoft 365 Defender dans Microsoft 365 centre de sécurité sans frais supplémentaires :

- Microsoft 365 E5 ou A5
- Microsoft 365 E3 l’Microsoft 365 E5 Sécurité de module
- Microsoft 365 A3 avec le module Microsoft 365 sécurité A5
- Windows 10 Entreprise E5 ou A5
- Enterprise Mobility + Security (EMS) E5 ou A5 
- Office 365 E5 ou A5
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité 
- Microsoft Cloud App Security
- Defender pour Office 365 (Plan 2)

Pour plus d’informations, [consultez les plans Microsoft 365 Entreprise service.](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise)

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](../../commerce/try-or-buy-microsoft-365.md)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Go to Microsoft 365 admin center ([admin.microsoft.com](https://admin.microsoft.com/)) to view your existing licenses. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Le rôle d’administrateur  de facturation ou de lecteur **global** dans [Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) doit vous être attribué pour pouvoir voir les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être administrateur **général ou** **administrateur** de sécurité dans Azure Active Directory pour activer Microsoft 365 Defender. Pour obtenir la liste des rôles requis pour utiliser Microsoft 365 Defender et des informations sur la façon dont l’accès aux données est réglementé, voir la gestion de l’accès [à Microsoft 365 Defender.](m365d-permissions.md)

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez Microsoft 365 Defender dans le centre de sécurité Microsoft 365 à l’aide de Microsoft Edge, d’Internet Explorer 11 ou d’un navigateur web html 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité aux états-Unis Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et à d’autres institutions gouvernementales américaines
Actuellement, Microsoft 365 Defender *n’est pas* disponible pour :
- États-Unis Cloud de la communauté du secteur public (Cloud de la communauté du secteur public)
- États-Unis Cloud de la communauté du secteur public élevé (Cloud de la communauté du secteur public élevé)
- Département de la Défense des États-Unis
- Toutes les institutions gouvernementales américaines titulaires de licences commerciales


Actuellement, l’intégration de Microsoft Defender pour Office 365 dans les fonctionnalités Microsoft 365 Defender unifiées n’est pas disponible pour les clients dans les emplacements Office 365 de centre de données suivants :

- Brésil 
- Allemagne 
- Norvège 
- Singapour 
- Afrique du Sud
- Suisse 
- Émirats arabes unis 


## <a name="related-topics"></a>Voir aussi
- [Microsoft 365 Vue d’ensemble de Defender](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Gérer l’accès et les autorisations](m365d-permissions.md)
