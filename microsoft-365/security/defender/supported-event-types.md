---
title: Microsoft 365 Defender types d’événements pris en charge dans l’API de diffusion en continu d’événements
description: Découvrez les types d’événements de recherche (tableaux) pris en charge par l’API de diffusion en continu
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
ms.openlocfilehash: 780cac298206127d52e14b3888a0a8d7f05ae0c5
ms.sourcegitcommit: afee35210f8d68a7f20676ff2a829464b0b0adb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2021
ms.locfileid: "60216969"
---
# <a name="supported-microsoft-365-defender-event-types-in-event-streaming-api"></a>Types d’Microsoft 365 Defender pris en charge dans l’API de diffusion en continu d’événements

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]


L’API de diffusion en continu des événements est constamment étendue pour prendre en charge d’autres types d’événements. Découvrez quelles tables de recherche sont généralement disponibles, actuellement en prévisualisation publique ou non encore pris en charge. 
**Nouveau : les types/tables d’événements de messagerie électronique sont désormais ga**

## <a name="hunting-tables-support-status-in-event-streaming-api"></a>L’état de prise en charge des tables de recherche dans l’API de diffusion en continu des événements

| Nom du tableau | Statut |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Généralement disponible |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Généralement disponible  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Pas encore pris en charge |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** |Généralement disponible |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** |Généralement disponible |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Généralement disponible |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | Généralement disponible |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Disponible |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Généralement disponible |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** |Disponible |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Généralement disponible |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Généralement disponible |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Généralement disponible |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Généralement disponible |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Généralement disponible |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Généralement disponible |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Généralement disponible |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Pas encore pris en charge |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Pas encore pris en charge |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Pas encore pris en charge |

