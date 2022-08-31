---
title: Fonction SeenBy() dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser la fonction SeenBy() pour rechercher quels appareils intégrés ont découvert un certain appareil
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, SeenBy, découverte d’appareil, fonction, enrichissement
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: c44288276431d5a479f47a46289dfaad8089448f
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67477184"
---
# <a name="seenby"></a>SeenBy()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `SeenBy()` fonction est appelée pour afficher la liste des appareils intégrés qui ont vu un certain appareil à l’aide de la fonctionnalité de découverte d’appareil.

Cette fonction retourne une table qui contient la colonne suivante :

| Column | Type de données | Description |
|------------|---------------|-------------|
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |


## <a name="syntax"></a>Syntaxe

```kusto
invoke SeenBy(x)
```

- où **x** est l’ID d’appareil qui vous intéresse

>[!TIP]
> Les fonctions d’enrichissement affichent des informations supplémentaires uniquement lorsqu’elles sont disponibles. La disponibilité de l’information varie et dépend de nombreux facteurs. Veillez à prendre cela en compte lors de l’utilisation de SeenBy() dans vos requêtes ou lors de la création de détections personnalisées. Pour de meilleurs résultats, nous vous recommandons d’utiliser la fonction SeenBy() avec la table DeviceInfo.

### <a name="example-obtain-list-of-onboarded-devices-that-have-seen-a-device"></a>Exemple : Obtenir la liste des appareils intégrés qui ont vu un appareil

```kusto
DeviceInfo 
| where OnboardingStatus <> "Onboarded" 
| limit 100 | invoke SeenBy()
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Obtenir d’autres exemples de requête](advanced-hunting-shared-queries.md)
