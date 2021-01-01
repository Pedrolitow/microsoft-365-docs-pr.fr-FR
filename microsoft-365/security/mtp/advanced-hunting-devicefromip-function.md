---
title: Fonction DeviceFromIP () dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser la fonction DeviceFromIP () pour obtenir les périphériques auxquels une adresse IP spécifique a été attribuée.
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, appareil, devicefromIP, fonction, enrichissement
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 65409dd93f3703f1af115178c4cd9fa470fb7497
ms.sourcegitcommit: 25ac2736a66bb72c0d574c3fbde7472ac98d5321
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2020
ms.locfileid: "49741107"
---
# <a name="devicefromip"></a>DeviceFromIP()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender


[!INCLUDE [Prerelease information](../includes/prerelease.md)]


Utilisez la `DeviceFromIP()` fonction dans vos requêtes de [chasse avancée](advanced-hunting-overview.md) pour obtenir rapidement la liste des périphériques affectés à une adresse IP spécifique à un moment donné. 

Cette fonction renvoie une table avec les colonnes suivantes :

| Colonne | Type de données | Description |
|------------|-------------|-------------|
| `IP` | string | Adresse IP  |
| `DeviceId` | chaîne | Identificateur unique de l’appareil dans le service |


## <a name="syntax"></a>Syntaxe

```kusto
invoke DeviceFromIP()
```

## <a name="arguments"></a>Arguments

Cette fonction est appelée dans le cadre d’une requête.

- **x**— le premier paramètre est généralement déjà une colonne dans la requête. Dans ce cas, il s’agit de la colonne nommée `IP` , de l’adresse IP pour laquelle vous souhaitez afficher la liste des périphériques qui lui ont été attribués. Il doit s’agir d’une adresse IP locale. Les adresses IP externes ne sont pas prises en charge.
- **y**— un deuxième paramètre facultatif est l' `Timestamp` , qui demande à la fonction d’obtenir les appareils affectés les plus récents à un moment donné. Si ce n’est pas spécifié, la fonction renvoie les derniers enregistrements disponibles.

## <a name="example"></a>Exemple


### <a name="get-the-latest-devices-that-have-been-assigned-specific-ip-addresses"></a>Obtenir les derniers appareils auxquels des adresses IP spécifiques ont été affectées

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
