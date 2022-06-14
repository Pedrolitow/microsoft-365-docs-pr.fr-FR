---
title: Microsoft 365 Defender types d’événements de streaming pris en charge dans l’API Event Streaming
description: Découvrez quels types d’événements de diffusion en continu (tables) sont pris en charge par l’API de diffusion en continu
keywords: exportation de données brutes, API de streaming, API, hubs d’événements, stockage Azure, compte de stockage, chasse, partage de données brutes
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4f6f098c9d2ec09a777110955b8acb1663e102ed
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057848"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Prise en charge Microsoft 365 Defender types d’événements de streaming dans l’API de streaming d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


L’API Event Streaming est constamment développée pour prendre en charge davantage de types d’événements. Découvrez quelles tables de chasse sont généralement disponibles, actuellement en préversion publique ou non encore prises en charge. 
**Nouveau : les types/tables d’événements e-mail sont désormais en disponibilité générale**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>Les tables de chasse prennent en charge l’état dans l’API De streaming d’événements

Le tableau suivant inclut uniquement la liste des tables prises en charge dans l’API de diffusion en continu et n’inclut pas tous les schémas AH. Pour obtenir la liste complète de l’API, consultez [les tables de schéma](advanced-hunting-schema-tables.md#learn-the-schema-tables).

| Nom du tableau | État<br>(Commercial) | GCC | GCC High | DoD |
|----|----|----|----|----|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Disponible | Disponible | Disponible | Disponibilité générale |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Disponibilité générale | Disponible | Disponible | Disponibilité générale |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |Disponible | Disponibilité générale | Disponible | Disponible |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponibilité générale |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |Disponible | Disponible | Disponible | Disponible |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Disponibilité générale | Disponibilité générale | Disponible | Disponible |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Disponibilité générale | Disponibilité générale | Disponibilité générale | Disponible |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Disponibilité générale | Disponible | Disponibilité générale | Disponible |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Disponibilité générale |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Disponible |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Disponible |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Disponibilité générale |![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)**|Disponibilité générale|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)**|Disponible|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|![Non](../defender-endpoint/images/svg/check-no.svg)|
