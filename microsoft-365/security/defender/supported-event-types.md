---
title: Microsoft 365 Defender types d’événements de streaming pris en charge dans l’API de diffusion en continu d’événements
description: Découvrez les types d’événements de streaming (tables) pris en charge par l’API de streaming
keywords: exportation de données brutes, API de streaming, API, Event Hubs, stockage Azure, compte de stockage, chasse, partage de données brutes
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.openlocfilehash: 32c65808ea0c27dcb60fde8bdab17a447283ba08
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660222"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Types d’événements de streaming Microsoft 365 Defender pris en charge dans l’API de streaming d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


L’API Event Streaming est constamment développée pour prendre en charge d’autres types d’événements. Découvrez quelles tables de chasse sont généralement disponibles, actuellement en préversion publique ou pas encore prises en charge. 

**Nouveau : les tables/types d’événements Identity et CloudApp sont désormais en disponibilité générale**.

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Les tables de chasse prennent en charge l’état dans l’API De streaming d’événements

Le tableau suivant inclut uniquement la liste des tables prises en charge dans l’API de diffusion en continu et n’inclut pas tous les schémas AH. Pour obtenir la liste complète de l’API, consultez [Découvrir les tables de schéma](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Nom du tableau | État<br>(Commercial) | GCC | GCC High | DoD |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Disponible | Disponible | Disponible | Disponible |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Disponibilité générale | Disponible | Disponible | Disponible |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Disponible | Disponibilité générale | Disponible | Disponibilité générale |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Disponible | Disponible | Disponible | Disponible |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Disponibilité générale | Disponible | Disponible | Disponible |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |Disponibilité générale | Disponible | Disponible | Disponible |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Disponibilité générale | Disponible | Disponible | Disponible |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Disponibilité générale |Préversion publique|Préversion publique|Préversion publique|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Disponibilité générale |Préversion publique|Préversion publique|Préversion publique|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Disponibilité générale |Préversion publique|Préversion publique|Préversion publique|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Disponibilité générale |Préversion publique|Préversion publique|Préversion publique|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|Disponibilité générale|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[UrlClickEvents](advanced-hunting-urlclickevents-table.md)**|Préversion publique|Préversion publique|Préversion publique|Préversion publique|
