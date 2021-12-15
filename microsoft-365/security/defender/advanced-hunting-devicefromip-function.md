---
title: Fonction DeviceFromIP() dans le recherche avancée d’Microsoft 365 Defender
description: Découvrez comment utiliser la fonction DeviceFromIP() pour obtenir les appareils affectés à une adresse IP spécifique
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, device, devicefromIP, function, enrichment
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 4a1f1198c247aefbcbb093d1a5f5105704255692
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531578"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Utilisez la fonction dans vos requêtes de recherche avancées pour obtenir rapidement la liste des appareils qui ont été affectés à une certaine adresse IP à `DeviceFromIP()` un moment donné dans le temps. [](advanced-hunting-overview.md) 

Cette fonction renvoie un tableau avec les colonnes suivantes :

| Colonne | Type de données | Description |
|------------|-------------|-------------|
| `IP` | `string` | Adresse IP  |
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |


## <a name="syntax"></a>Syntaxe

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Arguments

Cette fonction est invoquée dans le cadre d’une requête.

- **x**— Le premier paramètre est généralement déjà une colonne dans la requête. Dans ce cas, il s’agit de la colonne nommée , l’adresse IP pour laquelle vous souhaitez voir la liste des appareils qui lui ont `IP` été affectés. Il doit s’agit d’une adresse IP locale. Les adresses IP externes ne sont pas pris en charge.
- **y**— Un deuxième paramètre facultatif est le , qui indique à la fonction d’obtenir les appareils affectés les plus `Timestamp` récents à partir d’un moment spécifique. Si elle n’est pas spécifiée, la fonction renvoie les derniers enregistrements disponibles.

## <a name="example"></a>Exemple


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Obtenir les appareils les plus récents qui ont été affectés à des adresses IP spécifiques

```kusto
DeviceNetworkEvents 
| limit 100 
| project IP = LocalIP 
| invoke DeviceFromIP()
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
