---
title: Obtenir des informations pertinentes sur une entité avec la recherche de Go
description: Découvrez comment utiliser l’outil « aller-retour » pour demander rapidement des informations pertinentes sur une entité ou un événement à l’aide de la chasse avancée.
keywords: recherche avancée, incident, tableau croisé dynamique, entité, recherche de contenu, événements pertinents, recherche de menace, recherche sur les menaces informatiques, recherche, requête, télémétrie, Microsoft 365, protection contre les menaces Microsoft
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 9ddad74d179ac16a25640e2bdf4ed4906f920102
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846879"
---
# <a name="quickly-hunt-for-entity-or-event-information-with-go-hunt"></a>Recherche rapide d’informations sur les entités ou les événements avec la recherche de Go

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

L’action de *recherche aller-retour* vous permet d’examiner rapidement les événements et différents types d’entité à l’aide de puissantes fonctionnalités de recherche [avancée](advanced-hunting-overview.md) basées sur les requêtes. Cette action exécute automatiquement une requête de chasse avancée pour trouver des informations pertinentes sur l’événement ou l’entité sélectionné.

L’action aller à la *recherche* est disponible dans les différentes sections du centre de sécurité chaque fois que des détails d’événements ou d’entités sont affichés. Par exemple, vous pouvez utiliser la *recherche aller* à partir des sections suivantes :

- Dans la [page incident](investigate-incidents.md#incident-overview), vous pouvez consulter les détails relatifs aux utilisateurs, aux appareils et à de nombreuses autres entités associées à un incident. Lorsque vous sélectionnez une entité, vous obtenez des informations supplémentaires, ainsi que diverses actions que vous pouvez effectuer sur cette entitity. Dans l’exemple ci-dessous, une boîte aux lettres est sélectionnée, affichant des détails sur la boîte aux lettres, ainsi que la recherche d’informations supplémentaires sur la boîte aux lettres.

    ![Image illustrant les détails de la boîte aux lettres avec l’option aller à la recherche](../../media/mtp-ah/go-hunt-email.png)

- Dans la page incident, vous pouvez également accéder à une liste d’entités sous l’onglet preuve. La sélection de l’une de ces entités offre une option permettant de rechercher rapidement des informations sur cette entité.

    ![Image illustrant le fichier sélectionné avec l’option aller à la recherche dans l’onglet preuve](../../media/mtp-ah/go-hunt-evidence-file.png)


- Lors de l’affichage de la chronologie d’un appareil, vous pouvez sélectionner un événement dans la chronologie pour afficher des informations supplémentaires sur cet événement. Une fois qu’un événement est sélectionné, vous avez la possibilité de rechercher d’autres événements pertinents dans la recherche avancée.

    ![Image montrant les détails de l’événement avec l’option aller à la recherche](../../media/mtp-ah/go-hunt-event.png)

La sélection de l’option **aller-retour** ou **Hunt pour les événements associés** transmet des requêtes différentes, selon que vous avez sélectionné une entité ou un événement.

## <a name="query-for-entity-information"></a>Requête d’informations d’entité
Lors de l’utilisation de la *recherche aller-retour* pour obtenir des informations sur un utilisateur, un appareil ou tout autre type d’entité, la requête vérifie toutes les tables de schéma pertinentes pour les événements impliquant cette entité. Pour que les résultats soient gérables, la requête est étendue à environ la même période que l’activité la plus ancienne au cours des 30 derniers jours qui implique l’entité et qui est associée à l’incident.

Voici un exemple de la requête Go Hunt pour un appareil :

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
Vous pouvez utiliser la *recherche aller-retour* après avoir sélectionné l’un de ces types d’entité :

- Fichiers
- Messages électroniques
- Clusters de messagerie
- Boîtes aux lettres
- Utilisateurs
- Appareils
- Adresses IP
- URL

## <a name="query-for-event-information"></a>Requête d’informations sur l’événement
Lors de l’utilisation de la *recherche aller-retour* pour obtenir des informations sur un événement de chronologie, la requête vérifie toutes les tables de schéma pertinentes pour les autres événements autour de l’heure de l’événement sélectionné. Par exemple, la requête suivante répertorie les événements de différentes tables de schéma qui se sont produites sur la même période sur le même appareil :

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
Avec certaines connaissances du [langage de requête](advanced-hunting-query-language.md), vous pouvez ajuster la requête à vos préférences. Par exemple, vous pouvez ajuster cette ligne, ce qui détermine la taille de la fenêtre de temps :

```kusto
Timestamp between ((selectedTimestamp - 1h) .. (selectedTimestamp + 1h))
```

En plus de modifier la requête pour obtenir des résultats plus pertinents, vous pouvez également effectuer les opérations suivantes :
- [Afficher les résultats sous forme de graphiques](advanced-hunting-query-results.md#view-query-results-as-a-table-or-chart)
- [Créer une règle de détection personnalisée](custom-detection-rules.md)

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Travailler avec les résultats de la requête](advanced-hunting-query-results.md)
- [Règles de détection personnalisées](custom-detection-rules.md)
