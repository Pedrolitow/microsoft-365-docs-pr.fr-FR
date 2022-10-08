---
title: Microsoft 365 Defender types d’événements de streaming pris en charge dans l’API Event Streaming
description: Découvrez quels types d’événements de diffusion en continu (tables) sont pris en charge par l’API de diffusion en continu
keywords: exportation de données brutes, API de streaming, API, hubs d’événements, stockage Azure, compte de stockage, chasse, partage de données brutes
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
ms.topic: article
ms.openlocfilehash: 223f8a3c544a0f0f31781e3dbbf123bb6e600bd0
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082964"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Prise en charge Microsoft 365 Defender types d’événements de streaming dans l’API de streaming d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


L’API Event Streaming est constamment développée pour prendre en charge davantage de types d’événements. Découvrez quelles tables de chasse sont généralement disponibles, actuellement en préversion publique ou non encore prises en charge. 
**Nouveau : Email types d’événements/tables sont désormais en disponibilité générale**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Les tables de chasse prennent en charge l’état dans l’API De streaming d’événements

Le tableau suivant inclut uniquement la liste des tables prises en charge dans l’API de diffusion en continu et n’inclut pas tous les schémas AH. Pour obtenir la liste complète de l’API, consultez [les tables de schéma](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Nom du tableau | État<br>(Commercial) | GCC | GCC High | DoD |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Disponible | Disponible | Disponibilité générale | Disponibilité générale |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponible |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Disponibilité générale |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Disponible |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Disponible |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Disponibilité générale |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|Disponibilité générale|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
