---
title: Obtenir des informations pertinentes sur une entité avec go hunt
description: Découvrez comment utiliser l’outil go hunt pour interroger rapidement des informations pertinentes sur une entité ou un événement à l’aide de la chasse avancée.
keywords: repérage avancé, incident, tableau croisé dynamique, entité, chasse, événements pertinents, chasse aux menaces, repérage de cybermenaces, recherche, requête, télémétrie, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
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
ms.openlocfilehash: 7c1e4153afb7f279b5d31cce29a86f42bdc93832
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67483385"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Rechercher rapidement des informations d’entité ou d’événement avec go hunt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Avec l’action *go hunt* , vous pouvez examiner rapidement les événements et les différents types d’entités à l’aide de puissantes fonctionnalités [avancées de chasse](advanced-hunting-overview.md) basées sur des requêtes. Cette action exécute automatiquement une requête de chasse avancée pour rechercher des informations pertinentes sur l’événement ou l’entité sélectionné.

L’action *go hunt* est disponible dans différentes sections de Defender pour cloud. Cette action est disponible pour afficher une fois que les détails de l’événement ou de l’entité sont affichés. Par exemple, vous pouvez utiliser l’option *go hunt* dans les sections suivantes :

- Dans la [page d’incident](investigate-incidents.md#summary), vous pouvez consulter des détails sur les utilisateurs, les appareils et de nombreuses autres entités associées à un incident. Lorsque vous sélectionnez une entité, vous obtenez des informations supplémentaires et les différentes actions que vous pouvez effectuer sur cette entité. Dans l’exemple ci-dessous, une boîte aux lettres est sélectionnée, affichant des détails sur la boîte aux lettres et l’option permettant de rechercher plus d’informations sur la boîte aux lettres.

    :::image type="content" source="../../media/go-hunt-1-incident.png" alt-text="Page Boîtes aux lettres avec l’option Go hunt dans le portail Microsoft 365 Defender" lightbox="../../media/go-hunt-1-incident.png":::

- Dans la page d’incident, vous pouvez également accéder à une liste d’entités sous l’onglet **Preuve** . La sélection de l’une de ces entités permet de rechercher rapidement des informations sur cette entité.

    :::image type="content" source="../../media/go-hunt-2-entity.png" alt-text="Option Go hunt pour un élément de preuve dans la page Incident dans Microsoft 365 Defender portail" lightbox="../../media/go-hunt-2-entity.png":::


- Lorsque vous affichez la chronologie d’un appareil, vous pouvez sélectionner un événement dans la chronologie pour afficher des informations supplémentaires sur cet événement. Une fois qu’un événement est sélectionné, vous avez la possibilité de rechercher d’autres événements pertinents dans la chasse avancée.

    :::image type="content" source="../../media/go-hunt-3-event.png" alt-text="Option Rechercher les événements connexes dans la page d’un événement sous l’onglet Chronologies du portail Microsoft 365 Defender" lightbox="../../media/go-hunt-3-event.png":::

La sélection de **Go Hunt** ou **Hunt pour les événements associés** transmet différentes requêtes, selon que vous avez sélectionné une entité ou un événement.

## <a name="query-for-entity-information"></a>Requête pour les informations d’entité
Vous pouvez utiliser *go hunt* pour rechercher des informations sur un utilisateur, un appareil ou tout autre type d’entité ; la requête vérifie toutes les tables de schéma pertinentes pour tout événement impliquant cette entité afin de retourner des informations. Pour que les résultats restent gérables, la requête est la suivante :
- d’environ la même période que la première activité des 30 derniers jours qui implique l’entité
- associé à l’incident.

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
Vous pouvez utiliser l’option *go hunt* après avoir sélectionné l’un de ces types d’entités :

- Fichiers
- Messages électroniques
- clusters Email
- Boîtes aux lettres
- Utilisateurs
- Appareils
- Adresses IP
- URL

## <a name="query-for-event-information"></a>Requête d’informations sur les événements
Lorsque vous utilisez *go hunt* pour rechercher des informations sur un événement de chronologie, la requête vérifie toutes les tables de schémas pertinentes pour les autres événements au moment de l’événement sélectionné. Par exemple, la requête suivante répertorie les événements dans différentes tables de schéma qui se sont produits autour de la même période sur le même appareil :

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
Avec une certaine connaissance du [langage de requête](advanced-hunting-query-language.md), vous pouvez ajuster la requête à votre préférence. Par exemple, vous pouvez ajuster cette ligne, qui détermine la taille de la fenêtre de temps :

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

En plus de modifier la requête pour obtenir des résultats plus pertinents, vous pouvez également :
- [Afficher les résultats sous forme de graphiques](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Créer une règle de détection personnalisée](custom-detection-rules.md)

>[!NOTE]
>Certaines tables de cet article peuvent ne pas être disponibles dans Microsoft Defender pour point de terminaison. [Activez Microsoft 365 Defender](m365d-enable.md) pour rechercher des menaces à l’aide de sources de données supplémentaires. Vous pouvez déplacer vos flux de travail de chasse avancés de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender en suivant les étapes de migration [des requêtes de chasse avancées à partir de Microsoft Defender pour point de terminaison](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Règles de détection personnalisée](custom-detection-rules.md)
