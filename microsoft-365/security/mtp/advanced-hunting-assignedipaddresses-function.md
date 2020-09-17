---
title: Fonction AssignedIPAddresses () pour la protection avancée contre les menaces Microsoft
description: Découvrez comment utiliser la fonction AssignedIPAddresses () pour obtenir les dernières adresses IP affectées à un appareil
keywords: chasse aux menaces, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, FileProfile, profil de fichier, fonction, enrichissement
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 4ee07abe7ce1432921a843d713d0f9b914631174
ms.sourcegitcommit: dffb9b72acd2e0bd286ff7e79c251e7ec6e8ecae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "47949311"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

**S’applique à :**
- Protection Microsoft contre les menaces

Utilisez la `AssignedIPAddresses()` fonction pour obtenir rapidement les dernières adresses IP qui ont été affectées à un appareil. Si vous spécifiez un argument timestamp, cette fonction obtient les adresses IP les plus récentes à l’heure spécifiée. 

Cette fonction renvoie une table avec les colonnes suivantes :

| Colonne | Type de données | Description |
|------------|-------------|-------------|
| `Timestamp` | DateHeure | Dernière heure à laquelle l’appareil a été observé à l’aide de l’adresse IP |
| `IPAddress` | string | Adresse IP utilisée par l’appareil |
| `IPType` | string | Indique si l’adresse IP est une adresse publique ou privée |
| `NetworkAdapterType` | int | Type de carte réseau utilisé par l’appareil auquel l’adresse IP a été attribuée. Pour les valeurs possibles, reportez-vous à [cette énumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.networkinterfacetype) |
| `ConnectedNetworks` | int | Réseaux auxquels est connectée la carte à laquelle l’adresse IP est attribuée. Chaque tableau JSON contient le nom de réseau, la catégorie (public, privé ou domaine), une description et un indicateur qui indique s’il est connecté publiquement à Internet. |

## <a name="syntax"></a>Syntaxe

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Arguments

- **x**— `DeviceId` ou `DeviceName` valeur identifiant l’appareil
- **y**— `Timestamp` valeur (DateTime) indiquant à la fonction d’obtenir les adresses IP affectées les plus récentes à partir d’un certain temps. Si ce n’est pas spécifié, la fonction renvoie les dernières adresses IP.

## <a name="examples"></a>Exemples

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Obtenir la liste des adresses IP utilisées par un périphérique il y a 24 heures

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Obtenir des adresses IP utilisées par un appareil et trouver des périphériques communiquant avec celui-ci
Cette requête utilise la `AssignedIPAddresses()` fonction pour obtenir des adresses IP attribuées pour l’appareil ( `example-device-name` ) au plus tard à une date spécifique ( `example-date` ). Il utilise ensuite les adresses IP pour rechercher les connexions à l’appareil initié par d’autres appareils. 

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