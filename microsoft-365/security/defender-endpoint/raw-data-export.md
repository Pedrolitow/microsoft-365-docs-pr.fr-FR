---
title: Événements Stream Microsoft 365 Defender
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser des événements de recherche avancée vers des hubs d’événements ou un compte de stockage Azure
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
ms.openlocfilehash: 0c25ec8bc88a2714fb2f02ef8641c3eae700efe0
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "52730689"
---
# <a name="streaming-api"></a>API de diffusion en continu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Diffusez des événements de recherche avancée sur des hubs d’événements et/ou un compte de stockage Azure.

Microsoft 365 Defender prend en charge la diffusion en continu de tous les événements disponibles via [la](../defender/advanced-hunting-overview.md) recherche avancée vers un hub [d’événements](/azure/event-hubs/) et/ou un [compte de stockage Azure.](/azure/event-hubs/)



## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Flux d’événements dans les Hubs d’événements Azure](raw-data-export-event-hub.md)| En savoir plus sur l’activation de l’API de diffusion en continu dans votre client et configurer Microsoft 365 Defender pour diffuser en continu la recherche avancée vers [les](../defender/advanced-hunting-overview.md) hubs d’événements.
[Flux d’événements sur votre compte de stockage Azure](raw-data-export-storage.md)| Découvrez comment activer l’API de diffusion en continu dans votre client et configurer Microsoft 365 Defender pour diffuser en continu la recherche avancée [sur](../defender/advanced-hunting-overview.md) votre compte de stockage Azure.


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du chasse avancée](../defender/advanced-hunting-overview.md)
- [Documentation Azure Event Hubs](/azure/event-hubs/)
- [stockage Azure Documentation du compte](/azure/storage/common/storage-account-overview)
