---
title: Événements Microsoft 365 Defender stream
description: Découvrez comment configurer des Microsoft 365 Defender pour diffuser des événements de recherche avancée vers des hubs d’événements ou un compte de stockage Azure
keywords: exportation de données brutes, API de diffusion en continu, API, hubs d’événements, stockage Azure, compte de stockage, recherche avancée, partage de données brutes
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
ms.openlocfilehash: 0b8912ee40c090522a0b6228643f37b161dbde14
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59401229"
---
# <a name="streaming-api"></a>API de diffusion en continu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Diffusez des événements de recherche avancée sur des hubs d’événements et/ou un compte de stockage Azure.

Microsoft 365 Defender prend en charge les événements de diffusion en continu via [la](../defender/advanced-hunting-overview.md) recherche avancée vers un hub [d’événements](/azure/event-hubs/) et/ou un [compte de stockage Azure.](/azure/event-hubs/)

Pour plus d’informations sur Microsoft 365 Defender API de diffusion en continu, voir la [vidéo.](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga)

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Flux d’événements dans les Hubs d’événements Azure](streaming-api-event-hub.md)| En savoir plus sur l’activation de l’API de diffusion en continu dans votre client et configurer Microsoft 365 Defender pour diffuser [en](../defender/advanced-hunting-overview.md) continu le chasse avancée aux hubs d’événements.
[Flux d’événements sur votre compte de stockage Azure](streaming-api-storage.md)| Découvrez comment activer l’API de diffusion en continu dans votre client et configurer Microsoft 365 Defender pour diffuser en continu la recherche avancée [sur](advanced-hunting-overview.md) votre compte de stockage Azure.
[Types d’événements pris en charge](supported-event-types.md) | Découvrez les types d’événements de recherche avancée que l’API de diffusion en continu prend en charge.


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du chasse avancée](../defender/advanced-hunting-overview.md)
- [Documentation Azure Event Hubs](/azure/event-hubs/)
- [stockage Azure Documentation du compte](/azure/storage/common/storage-account-overview)
