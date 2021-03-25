---
title: Conditions préalables de Microsoft 365 Defender
description: En savoir plus sur les licences, la configuration matérielle et logicielle requise et d’autres paramètres de configuration pour Microsoft 365 Defender
keywords: configuration requise, conditions préalables, matériel, logiciel, navigateur, MTP, M365, licence, E5, A5, EMS, achat
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
ms.openlocfilehash: f9904ecb5b9ab0a0f634903a5dc0ee3049d06b38
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066745"
---
# <a name="microsoft-365-defender-prerequisites"></a>Conditions préalables de Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Découvrez les licences et autres conditions requises pour l’approvisionnement et l’utilisation [de Microsoft 365 Defender.](microsoft-365-defender.md)

## <a name="licensing-requirements"></a>Critères de licence
L’une de ces licences vous donne accès aux fonctionnalités de Microsoft 365 Defender dans le Centre de sécurité Microsoft 365 sans frais supplémentaires :

- Microsoft 365 E5 ou A5
- Microsoft 365 E5 Sécurité ou A5 Sécurité
- Windows 10 Entreprise E5 ou A5
- Enterprise Mobility + Security (EMS) E5 ou A5 
- Office 365 E5 ou A5
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité 
- Microsoft Cloud App Security
- Defender pour Office 365 (Plan 2)

Pour plus d’informations, consultez les plans de [service Microsoft 365 Entreprise.](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise)

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](../../commerce/try-or-buy-microsoft-365.md?view=o365-worldwide)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Go to Microsoft 365 admin center ([admin.microsoft.com](https://admin.microsoft.com/)) to view your existing licenses. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Le rôle d’administrateur  de facturation ou de lecteur **global** dans [Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) doit vous être attribué pour pouvoir voir les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être administrateur **général ou** **administrateur** de sécurité dans Azure Active Directory pour activer Microsoft 365 Defender. Pour obtenir la liste des rôles requis pour utiliser Microsoft 365 Defender et des informations sur la façon dont l’accès aux données est réglementé, voir la gestion de l’accès à [Microsoft 365 Defender.](m365d-permissions.md)

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez à Microsoft 365 Defender dans le Centre de sécurité Microsoft 365 à l’aide de Microsoft Edge, d’Internet Explorer 11 ou de tout navigateur web conforme HTML 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité pour LES ÉTATS-UNIS GCC, GCC High et d’autres institutions gouvernementales des États-Unis
Actuellement, Microsoft 365 Defender *n’est pas* disponible pour :
- Cloud communautaire du gouvernement américain (GCC)
- Cloud communautaire du gouvernement américain élevé (GCC High)
- Département de la Défense des États-Unis
- Toutes les institutions gouvernementales américaines titulaires de licences commerciales

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)
- [Activer Microsoft 365 Defender](m365d-enable.md)
- [Gérer l’accès et les autorisations](m365d-permissions.md)
