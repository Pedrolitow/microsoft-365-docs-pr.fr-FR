---
title: Fonction AssignedIPAddresses() dans le recherche avancée de Microsoft Defender pour point de terminaison
description: Découvrez comment utiliser la fonction AssignedIPAddresses() pour obtenir les dernières adresses IP attribuées à un appareil
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, Microsoft Defender ATP, Microsoft Defender for Endpoint, Windows Defender, Windows Defender ATP, Windows Defender Advanced Threat Protection, search, query, telemetry, schema reference, kusto, FileProfile, file profile, function, enrichment
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 09/20/2020
ms.technology: mde
ms.openlocfilehash: 5dcc41302d797b4084c36d020908ba59131c90d4
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499284"
---
# <a name="assignedipaddresses"></a>AssignedIPAddresses()

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedfeats-abovefoldlink)

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Utilisez la fonction dans vos requêtes de recherche avancées pour obtenir rapidement les dernières adresses IP qui ont été `AssignedIPAddresses()` attribuées à un appareil. Si vous spécifiez un argument d’timestamp, cette fonction obtient les adresses IP les plus récentes à l’heure spécifiée.

Cette fonction renvoie un tableau avec les colonnes suivantes :

Column | Type de données | Description
-|-|-
`Timestamp` | DateHeure | Heure de la dernière observation de l’appareil à l’aide de l’adresse IP
`IPAddress` | string | Adresse IP utilisée par l’appareil
`IPType` | string | Indique si l’adresse IP est une adresse publique ou privée
`NetworkAdapterType` | entier | Type de carte réseau utilisé par l’appareil à qui l’adresse IP a été attribuée. Pour les valeurs possibles, reportez-vous [à cette éumération](https://docs.microsoft.com/dotnet/api/system.net.networkinformation.networkinterfacetype)
`ConnectedNetworks` | entier | Réseaux à qui la carte avec l’adresse IP affectée est connectée. Chaque tableau JSON contient le nom du réseau, la catégorie (public, privé ou domaine), une description et un indicateur indiquant s’il est connecté publiquement à Internet

## <a name="syntax"></a>Syntaxe

```kusto
AssignedIPAddresses(x, y)
```

## <a name="arguments"></a>Arguments

- **x** ou `DeviceId` valeur identifiant `DeviceName` l’appareil
- **y**— valeur (date/heure) qui indique à la fonction d’obtenir les adresses IP attribuées les plus `Timestamp` récentes à partir d’une heure spécifique. Si elle n’est pas spécifiée, la fonction renvoie les dernières adresses IP.

## <a name="examples"></a>Exemples

### <a name="get-the-list-of-ip-addresses-used-by-a-device-24-hours-ago"></a>Obtenir la liste des adresses IP utilisées par un appareil il y a 24 heures

```kusto
AssignedIPAddresses('example-device-name', ago(1d))
```

### <a name="get-ip-addresses-used-by-a-device-and-find-devices-communicating-with-it"></a>Obtenir les adresses IP utilisées par un appareil et trouver les appareils qui communiquent avec lui

Cette requête utilise la fonction pour obtenir des adresses IP attribuées pour l’appareil ( ) à une date spécifique `AssignedIPAddresses()` `example-device-name` ou avant ( `example-date` ). Il utilise ensuite les adresses IP pour rechercher les connexions à l’appareil initiées par d’autres appareils. 

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
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
