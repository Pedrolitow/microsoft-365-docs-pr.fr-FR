---
title: Fonction DeviceFromIP() dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser la fonction DeviceFromIP() pour obtenir les appareils auxquels une adresse IP spécifique a été attribuée
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, appareil, devicefromIP, fonction, enrichissement
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
ms.openlocfilehash: 4d8c60e9323b7260ab73635753bea5a4ad5079ab
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68087231"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Utilisez la `DeviceFromIP()` fonction dans vos requêtes de [repérage avancées](advanced-hunting-overview.md) pour obtenir rapidement la liste des appareils qui ont été affectés à une certaine adresse IP à un moment donné. 

Cette fonction retourne une table avec les colonnes suivantes :

| Column | Type de données | Description |
|------------|-------------|-------------|
| `IP` | `string` | Adresse IP  |
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |


## <a name="syntax"></a>Syntaxe

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Arguments

Cette fonction est appelée dans le cadre d’une requête.

- **x** : le premier paramètre est généralement déjà une colonne dans la requête. Dans ce cas, il s’agit de la colonne nommée `IP`, l’adresse IP pour laquelle vous souhaitez afficher la liste des appareils qui lui ont été affectés. Il doit s’agir d’une adresse IP locale. Les adresses IP externes ne sont pas prises en charge.
- **y** : un deuxième paramètre facultatif est le `Timestamp`, qui indique à la fonction d’obtenir les appareils affectés les plus récents à partir d’un moment spécifique. Si elle n’est pas spécifiée, la fonction retourne les derniers enregistrements disponibles.

## <a name="example"></a>Exemple


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Obtenir les derniers appareils auxquels des adresses IP spécifiques ont été attribuées

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
