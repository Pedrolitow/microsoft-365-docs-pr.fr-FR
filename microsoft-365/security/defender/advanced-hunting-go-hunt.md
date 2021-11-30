---
title: Obtenir des informations pertinentes sur une entité avec go hunt
description: Découvrez comment utiliser l’outil de recherche pour rapidement interroger des informations pertinentes sur une entité ou un événement à l’aide d’un recherche avancée.
keywords: advanced hunting, incident, pivot, entity, go hunt, relevant events, threat hunting, cyber threat hunting, search, query, telemetry, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e14f2d5e35585cf5b0edfe433084fa7c8a1d5280
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2021
ms.locfileid: "61221063"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Recherche rapide des informations sur l’entité ou les événements avec la recherche de go

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Avec *l’action de recherche* go, vous pouvez rapidement examiner les événements et différents types d’entités à l’aide de puissantes fonctionnalités de recherche avancée [basées](advanced-hunting-overview.md) sur des requêtes. Cette action exécute automatiquement une requête de recherche avancée pour rechercher des informations pertinentes sur l’événement ou l’entité sélectionné.

*L’action de recherche* est disponible dans différentes sections de Defender for Cloud chaque fois que les détails de l’événement ou de l’entité sont affichés. Par exemple, vous pouvez utiliser *la recherche dans* les sections suivantes :

- Dans la [page Incident,](investigate-incidents.md#summary)vous pouvez consulter les détails sur les utilisateurs, les appareils et de nombreuses autres entités associées à un incident. Lorsque vous sélectionnez une entité, vous obtenez des informations supplémentaires ainsi que différentes actions que vous pouvez prendre sur cette entité. Dans l’exemple ci-dessous, une boîte aux lettres est sélectionnée, affichant des détails sur la boîte aux lettres ainsi que l’option de recherche pour plus d’informations sur la boîte aux lettres.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Page **Boîtes aux lettres** avec l’option **Go hunt** dans le portail Microsoft 365 Defender web" lightbox="../../media/go-hunt-1-incident.png":::

- Dans la page Incident, vous pouvez également accéder à une liste d’entités sous l’onglet **Preuves.** La sélection de l’une de ces entités permet de trouver rapidement des informations sur cette entité.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="L’option Aller à la recherche d’un élément de preuve dans la page **Incident** dans Microsoft 365 Defender portail" lightbox="../../media/go-hunt-2-entity.png":::


- Lorsque vous affichez la chronologie d’un appareil, vous pouvez sélectionner un événement dans la chronologie pour afficher des informations supplémentaires sur cet événement. Une fois qu’un événement est sélectionné, vous avez la possibilité de chercher d’autres événements pertinents dans le hunting avancé.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="L’option **Recherche d’événements connexes** sur la page d’un événement dans l’onglet **Chronologies** dans Microsoft 365 Defender portail" lightbox="../../media/go-hunt-3-event.png":::

La sélection **de la** fonction De recherche ou de recherche pour les événements connexes transmet différentes requêtes, selon que vous avez sélectionné une entité ou un événement. 

## <a name="query-for-entity-information"></a>Requête d’informations sur l’entité
Lorsque vous utilisez *go hunt* to query for information about a user, device, or any other type of entity, the query checks all relevant schema tables for any events involving that entity. Pour que les résultats restent gérables, la requête est limitée à la même période que l’activité la plus tôt au cours des 30 derniers jours qui implique l’entité et est associée à l’incident.

Voici un exemple de requête go hunt pour un appareil :

```kusto
let selectedTimestamp = datetime(2020-06-02T02:06:47.1167157Z);
let deviceName = "fv-az770.example.com";
let deviceId = "device-guid";
search in (DeviceLogonEvents, DeviceProcessEvents, DeviceNetworkEvents, DeviceFileEvents, DeviceRegistryEvents, DeviceImageLoadEvents, DeviceEvents, DeviceImageLoadEvents, IdentityLogonEvents, IdentityQueryEvents)
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
and DeviceName == deviceName
// or RemoteDeviceName == deviceName
// or DeviceId == deviceId
| take 100
```
### <a name="supported-entity-types"></a>Types d’entités pris en charge
Vous pouvez utiliser *la recherche après* avoir sélectionné l’un des types d’entités ci-après :

- Fichiers
- Messages électroniques
- Clusters de messagerie
- Boîtes aux lettres
- Utilisateurs
- Appareils
- Adresses IP
- URL

## <a name="query-for-event-information"></a>Requête d’informations sur les événements
Lorsque vous *utilisez go hunt* to query pour obtenir des informations sur un événement de chronologie, la requête vérifie toutes les tables de schéma pertinentes pour les autres événements à l’heure de l’événement sélectionné. Par exemple, la requête suivante répertorie les événements dans différentes tables de schéma qui se sont produits autour de la même période sur le même appareil :

```kusto
// List relevant events 30 minutes before and after selected LogonAttempted event
let selectedEventTimestamp = datetime(2020-06-04T01:29:09.2496688Z);
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
    Timestamp between ((selectedEventTimestamp - 30m) .. (selectedEventTimestamp + 30m))
    and DeviceId == "079ecf9c5798d249128817619606c1c47369eb3e"
| sort by Timestamp desc
| extend Relevance = iff(Timestamp == selectedEventTimestamp, "Selected event", iff(Timestamp < selectedEventTimestamp, "Earlier event", "Later event"))
| project-reorder Relevance
```

## <a name="adjust-the-query"></a>Ajuster la requête
Avec une certaine connaissance du langage [de requête,](advanced-hunting-query-language.md)vous pouvez ajuster la requête à votre préférence. Par exemple, vous pouvez ajuster cette ligne, qui détermine la taille de la fenêtre de temps :

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

En plus de modifier la requête pour obtenir des résultats plus pertinents, vous pouvez également :
- [Afficher les résultats en tant que graphiques](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Créer une règle de détection personnalisée](custom-detection-rules.md)

>[!NOTE]
>Certains tableaux de cet article peuvent ne pas être disponibles dans Microsoft Defender pour endpoint. [Activer Microsoft 365 Defender](m365d-enable.md) pour la recherche de menaces à l’aide de sources de données plus nombreuses. Vous pouvez déplacer vos flux de travail de recherche avancée de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de la procédure de migration des requêtes de recherche avancée à partir de Microsoft Defender pour le point de [terminaison.](advanced-hunting-migrate-from-mde.md)

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Règles de détection personnalisée](custom-detection-rules.md)
