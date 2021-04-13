---
title: Événement Stream Microsoft Defender for Endpoint
description: Découvrez comment configurer Microsoft Defender pour le point de terminaison pour diffuser des événements de recherche avancée vers des hubs d'événements ou un compte de stockage Azure
keywords: exportation de données brutes, API de diffusion en continu, API, hubs d'événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: f6a45629d610ea3cc3ca7d517021a215b72b1439
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51688752"
---
# <a name="raw-data-streaming-api"></a>API de diffusion de données brutes

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vous souhaitez faire l'expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-configuresiem-abovefoldlink) 

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Diffusez des événements de recherche avancée sur des hubs d'événements et/ou un compte de stockage Azure.

Defender pour le point de terminaison prend en charge la diffusion en continu de tous les événements disponibles via la recherche avancée vers un hub [d'événements](https://docs.microsoft.com/azure/event-hubs/) et/ou un [compte de stockage Azure.](https://docs.microsoft.com/azure/event-hubs/) [](advanced-hunting-overview.md)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga]


## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Diffuser des événements Microsoft Defender for Endpoint vers des Hubs d'événements Azure](raw-data-export-event-hub.md)| En savoir plus sur l'activation de l'API de diffusion en continu dans votre client et configurer Defender pour le point de terminaison pour diffuser en continu [la](advanced-hunting-overview.md) recherche avancée vers les hubs d'événements.
[Événements Stream Defender for Endpoint sur votre compte de stockage Azure](raw-data-export-storage.md)| En savoir plus sur l'activation de l'API de diffusion en continu dans votre client et configurer Defender pour le point de terminaison pour diffuser en continu la recherche [avancée](advanced-hunting-overview.md) sur votre compte de stockage Azure.


## <a name="related-topics"></a>Voir aussi
- [Vue d'ensemble du chasse avancée](advanced-hunting-overview.md)
- [Documentation Azure Event Hubs](https://docs.microsoft.com/azure/event-hubs/)
- [Documentation du compte de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview)
