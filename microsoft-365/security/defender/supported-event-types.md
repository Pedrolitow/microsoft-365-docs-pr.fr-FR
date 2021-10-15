---
title: Microsoft 365 Defender types d’événements de diffusion en continu pris en charge dans l’API de diffusion en continu d’événements
description: Découvrez les types d’événements de diffusion en continu (tableaux) pris en charge par l’API de diffusion en continu
keywords: exportation de données brutes, API de diffusion en continu, API, hubs d’événements, stockage Azure, compte de stockage, recherche, partage de données brutes
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
ms.openlocfilehash: e8264ccb9e3181f6b58a6206417eb2b842bec6e7
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2021
ms.locfileid: "60364795"
---
# <a name="supported-microsoft-365-defender-streaming-event-types-in-event-streaming-api"></a>Types d Microsoft 365 Defender de diffusion en continu pris en charge dans l’API de diffusion en continu d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


L’API de diffusion en continu d’événements est constamment étendue pour prendre en charge davantage de types d’événements. Découvrez quelles tables de chasse sont généralement disponibles, actuellement en prévisualisation publique ou non encore pris en charge. 
**Nouveau : les types/tables d’événements de messagerie électronique sont désormais ga**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>L’état de prise en charge des tables de recherche dans l’API de diffusion en continu des événements

Le tableau suivant inclut uniquement la liste des tableaux pris en charge dans l’API de diffusion en continu et n’est pas inclus dans tout le schéma DE LAS. Pour obtenir la liste complète de l’API, [consultez les tableaux de schéma.](advanced-hunting-schema-tables.md#learn-the-schema-tables)


| Nom du tableau | Statut |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Disponible |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Généralement disponible  |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |Généralement disponible |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |Généralement disponible |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Généralement disponible |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Généralement disponible |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Généralement disponible |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Disponible |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |Généralement disponible |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Généralement disponible |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Généralement disponible |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Disponible |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Disponible |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Disponible |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Disponible |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Généralement disponible |


