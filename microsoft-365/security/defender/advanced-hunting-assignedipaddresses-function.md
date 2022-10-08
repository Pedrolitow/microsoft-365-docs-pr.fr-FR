---
title: AssignedIPAddresses() fonction dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser la fonction AssignedIPAddresses() pour obtenir les dernières adresses IP affectées à un appareil
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, FileProfile, profil de fichier, fonction, enrichissement
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
- m365-security
- tier3
ms.topic: article
ms.openlocfilehash: b93bcd80021055820f093b3ba52941b8a944781d
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68073006"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Utilisez la `AssignedIPAddresses()` fonction dans vos requêtes de [repérage avancées](advanced-hunting-overview.md) pour obtenir rapidement les dernières adresses IP qui ont été affectées à un appareil. Si vous spécifiez un argument d’horodatage, cette fonction obtient les adresses IP les plus récentes à l’heure spécifiée. 

Cette fonction retourne une table avec les colonnes suivantes :

| Column | Type de données | Description |
|------------|-------------|-------------|
| `Timestamp` | `datetime` | Heure la plus récente à laquelle l’appareil a été observé à l’aide de l’adresse IP |
| `IPAddress` | `string` | Adresse IP utilisée par l’appareil |
| `IPType` | `string` | Indique si l’adresse IP est une adresse publique ou privée |
| `NetworkAdapterType` | `int` | Type de carte réseau utilisé par l’appareil auquel l’adresse IP a été attribuée. Pour connaître les valeurs possibles, reportez-vous à [cette énumération](/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | `int` | Réseaux auxquels l’adaptateur avec l’adresse IP affectée est connecté. Chaque tableau JSON contient le nom du réseau, la catégorie (public, privé ou domaine), une description et un indicateur indiquant s’il est connecté publiquement à Internet |

## <a name="syntax"></a>Syntaxe

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Arguments

- **x** —`DeviceId` ou `DeviceName` valeur identifiant l’appareil
- **y**:`Timestamp` valeur (datetime) indiquant à la fonction d’obtenir les adresses IP attribuées les plus récentes à partir d’une heure spécifique. Si elle n’est pas spécifiée, la fonction retourne les dernières adresses IP.

## <a name="examples"></a>Exemples

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Obtenir la liste des adresses IP utilisées par un appareil il y a 24 heures

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Obtenir les adresses IP utilisées par un appareil et rechercher les appareils qui communiquent avec lui
Cette requête utilise la `AssignedIPAddresses()` fonction pour obtenir les adresses IP affectées pour l’appareil () à une date spécifique (`example-device-name``example-date`ou avant). Il utilise ensuite les adresses IP pour rechercher des connexions à l’appareil initié par d’autres appareils. 

```kusto
let Date = datetime(example-date);
let DeviceName = "example-device-name";
// List IP addresses used on or before the specified date
AssignedIPAddresses(DeviceName, Date)
| project DeviceName, IPAddress, AssignedTime = Timestamp 
// Get all network events on devices with the assigned IP addresses as the destination addresses
| join kind=inner DeviceNetworkEvents on $left.IPAddress == $right.RemoteIP
// Get only network events around the time the IP address was assigned
| where Timestamp between ((AssignedTime - 1h) .. (AssignedTime + 1h))
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)