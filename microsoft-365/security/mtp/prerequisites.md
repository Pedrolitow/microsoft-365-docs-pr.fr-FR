---
title: Conditions préalables pour Microsoft 365 Defender
description: En savoir plus sur la gestion des licences, la configuration matérielle et logicielle requise, ainsi que d’autres paramètres de configuration pour Microsoft 365 Defender
keywords: conditions requises, configuration matérielle, logicielle, navigateur, MTP, M365, licence, E5, a5, EMS, acheter
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 415cdb79a6aa9371ee2f07de579cfb2f873f1acb
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844775"
---
# <a name="microsoft-365-defender-prerequisites"></a>Conditions préalables pour Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Découvrez les licences et autres conditions requises pour la mise en service et l’utilisation de [Microsoft 365 Defender](microsoft-threat-protection.md).

## <a name="licensing-requirements"></a>Critères de licence
L’une de ces licences vous donne accès aux fonctionnalités de Microsoft 365 Defender dans le centre de sécurité Microsoft 365 sans frais supplémentaires :

- Microsoft 365 E5 ou a5
- Microsoft 365 E5 sécurité ou a5 sécurité
- Windows 10 entreprise E5 ou a5
- Enterprise Mobility + Security (EMS) E5 ou a5 
- Office 365 E5 ou a5
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité 
- Microsoft Cloud App Security
- Defender pour Office 365 (plan 2)

> [!NOTE]
> Les licences d’évaluation pour Office 365 ne fournissent actuellement pas d’accès à Microsoft 365 Defender.

Pour plus d’informations, [consultez les plans de services d’entreprise Microsoft 365](https://www.microsoft.com/licensing/product-licensing/microsoft-365-enterprise).

> Vous n’avez pas encore de licence ? [Essayez ou achetez un abonnement Microsoft 365](https://docs.microsoft.com/microsoft-365/commerce/try-or-buy-microsoft-365?view=o365-worldwide)

### <a name="check-your-existing--licenses"></a>Vérifiez vos licences existantes
Accédez au centre d’administration Microsoft 365 ([admin.Microsoft.com](https://admin.microsoft.com/)) pour afficher vos licences existantes. Dans le Centre d'administration, accédez à **Facturation** > **Licences**.

>[!NOTE]
> Vous devez disposer du rôle d' **administrateur de facturation** ou de **lecteur global** [dans Azure ad](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles) pour être en mesure d’afficher les informations de licence. Si vous rencontrez des problèmes d’accès, veuillez contacter un administrateur général.

## <a name="required-permissions"></a>Autorisations requises
Vous devez être **administrateur général** ou administrateur de **sécurité** dans Azure Active Directory pour activer Microsoft 365 Defender. Pour obtenir la liste des rôles requis pour utiliser Microsoft 365 Defender et des informations sur la façon dont l’accès aux données est réglementé, consultez la rubrique [Managing Access to microsoft 365 Defender](mtp-permissions.md).

## <a name="browser-requirements"></a>Configuration requise pour le navigateur
Accédez à Microsoft 365 Defender dans le centre de sécurité Microsoft 365 à l’aide de Microsoft Edge, d’Internet Explorer 11 ou de n’importe quel navigateur Web HTML 5.

## <a name="availability-to-us-gcc-gcc-high-and-other-us-government-institutions"></a>Disponibilité aux États-Unis GCC, GCC High et d’autres établissements gouvernementaux américains
Actuellement, Microsoft 365 Defender n’est *pas* disponible pour :
- Cloud communautaire pour le gouvernement américain (GCC)
- Niveau supérieur du Cloud communautaire pour le gouvernement américain (GCC High)
- Ministère américain de la défense
- Tous les établissements gouvernementaux américains avec des licences commerciales

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble de Microsoft 365 Defender](microsoft-threat-protection.md)
- [Activer Microsoft 365 Defender](mtp-enable.md)
- [Gérer l’accès et les autorisations](mtp-permissions.md)
