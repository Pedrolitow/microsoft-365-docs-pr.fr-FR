---
title: Événement stream Microsoft Defender pour point de terminaison
description: Découvrez comment configurer Microsoft Defender pour point de terminaison pour diffuser en continu des événements Advanced Hunting vers Event Hubs ou un compte de stockage Azure
keywords: exportation de données brutes, API de streaming, API, hubs d’événements, stockage Azure, compte de stockage, repérage avancé, partage de données brutes
ms.service: microsoft-365-security
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
ms.subservice: mde
ms.custom: api
search.appverid: met150
ms.openlocfilehash: 8a985a6f5f4a0dee96cc37e2a16c9947abf8a2e6
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67704125"
---
# <a name="raw-data-streaming-api"></a>API de streaming de données brutes

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="stream-advanced-hunting-events-to-event-hubs-andor-azure-storage-account"></a>Diffuser en continu des événements de repérage avancé vers Event Hubs et/ou un compte de stockage Azure

Microsoft Defender pour point de terminaison prend en charge les événements de diffusion en continu disponibles via [La chasse avancée](../defender/advanced-hunting-overview.md) à un [event Hubs](/azure/event-hubs/) et/ou un [compte de stockage Azure](/azure/storage/common/storage-account-overview).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4r4ga]

## <a name="in-this-section"></a>Dans cette section

Rubrique|Description
:---|:---
[Diffuser en continu des événements Microsoft Defender pour point de terminaison vers Azure Event Hubs](raw-data-export-event-hub.md)|Découvrez comment activer l’API de streaming dans votre locataire et configurer Defender pour point de terminaison pour diffuser [en continu advanced hunting](advanced-hunting-overview.md) vers Event Hubs.
[Diffuser en continu des événements Defender pour point de terminaison vers votre compte de stockage Azure](raw-data-export-storage.md)|Découvrez comment activer l’API de streaming dans votre locataire et configurer Defender pour point de terminaison pour diffuser en continu [Advanced Hunting](advanced-hunting-overview.md) vers votre compte de stockage Azure.

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de la chasse avancée](advanced-hunting-overview.md)
- [documentation Azure Event Hubs](/azure/event-hubs/)
- [Documentation sur le compte de stockage Azure](/azure/storage/common/storage-account-overview)