---
title: Diffuser en continu des événements Microsoft 365 Defender
description: Découvrez comment configurer Microsoft 365 Defender pour diffuser en continu des événements Advanced Hunting vers Event Hubs ou un compte de stockage Azure
keywords: exportation de données brutes, API de streaming, API, hubs d’événements, stockage Azure, compte de stockage, repérage avancé, partage de données brutes
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
ms.openlocfilehash: e0066d33aa0066b01e32a1f5ad02dfc7f780dce1
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68084460"
---
# <a name="streaming-api"></a>API de diffusion en continu

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Diffusez en continu des événements de repérage avancé vers Event Hubs et/ou un compte de stockage Azure.

Microsoft 365 Defender prend en charge la diffusion en continu d’événements via [La chasse avancée](../defender/advanced-hunting-overview.md) vers un [event Hubs](/azure/event-hubs/) et/ou un [compte de stockage Azure](/azure/event-hubs/).

Pour plus d’informations sur Microsoft 365 Defender API de streaming, consultez la [vidéo](https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga).

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
:---|:---
[Diffuser en continu des événements vers Azure Event Hubs](streaming-api-event-hub.md)| Découvrez comment activer l’API de streaming dans votre locataire et configurer Microsoft 365 Defender pour diffuser en continu [Advanced Hunting](../defender/advanced-hunting-overview.md) vers Event Hubs.
[Diffuser en continu des événements vers votre compte de stockage Azure](streaming-api-storage.md)| Découvrez comment activer l’API de diffusion en continu dans votre locataire et configurer Microsoft 365 Defender pour diffuser en continu [Advanced Hunting](advanced-hunting-overview.md) vers votre compte de stockage Azure.
[Types d’événements pris en charge](supported-event-types.md) | Découvrez les types d’événements Advanced Hunting pris en charge par l’API de streaming.

Regardez cette courte vidéo pour découvrir comment configurer l’API de diffusion en continu afin d’envoyer des informations d’événement directement à Azure Event Hubs à des fins de consommation par les services de visualisation, les moteurs de traitement des données ou le stockage Azure pour la conservation des données à long terme.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4ga]

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble de la chasse avancée](../defender/advanced-hunting-overview.md)
- [documentation Azure Event Hubs](/azure/event-hubs/)
- [Documentation sur le compte de stockage Azure](/azure/storage/common/storage-account-overview)
