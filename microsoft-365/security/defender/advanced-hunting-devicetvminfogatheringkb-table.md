---
title: Table DeviceTvmInfoGatheringKB dans le schéma de chasse avancé
description: Découvrez les métadonnées des événements d’évaluation dans la table DeviceTvmInfoGathering du schéma de chasse avancé.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities, MDVM
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
ms.openlocfilehash: e83ff6391e40f015bfeda48d429d50ae9cc9f9fc
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67329462"
---
# <a name="devicetvminfogatheringkb"></a>DeviceTvmInfoGatheringKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

La `DeviceTvmInfoGatheringKB` table du schéma de chasse avancé contient des métadonnées pour [Gestion des vulnérabilités Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) données d’événements d’évaluation collectées dans la `DeviceTvmInfoGathering` table. Le `DeviceTvmInfoGatheringKB` tableau contient la liste des différentes évaluations de la surface d’attaque et de configuration utilisées par la collecte d’informations sur la gestion des vulnérabilités Defender pour évaluer les appareils. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `IgId` | `string` | Identificateur unique pour la partie d’informations collectées |
| `FieldName` | `string` | Nom du champ dans lequel ces informations apparaissent dans la colonne AdditionalFields de la table DeviceTvmInfoGathering |
| `Description` | `string` | Description des informations collectées |
| `Categories` | `string` | Liste des catégories auxquelles les informations appartiennent, au format tableau JSON  |
| `DataStructure` | `string` | Structure des données des informations collectées  |

Vous pouvez utiliser ce tableau pour explorer les types d’informations disponibles `DeviceTvmInfoGathering` afin de pouvoir affiner ultérieurement votre requête de chasse.

Par exemple, pour afficher la liste des informations collectées, vous pouvez essayer la requête suivante :

```kusto
// Check out what is being collected 
DeviceTvmInfoGatheringKB  
```

À partir des résultats, supposons que vous vous intéressiez aux catégories disponibles, vous pouvez utiliser la requête suivante :

```kusto
// Return all available categories 
DeviceTvmInfoGatheringKB 
| mv-expand Categories to typeof(string) 
| distinct Categories 
```

Supposons ensuite que vous souhaitez voir les catégories d’évaluation impliquant le protocole TLS :

```kusto
// Return all findings for a specified category 
DeviceTvmInfoGatheringKB 
| where Categories contains "tls" 
```

À l’aide des champs résultants, vous pouvez ensuite utiliser le `DeviceTvmInfoGathering` tableau pour obtenir la liste des appareils à l’aide du client TLS version 1.0.

```kusto
// Return all devices on which the TLS version 1.0 is enabled 
DeviceTvmInfoGathering 
| where AdditionalFields.TlsClient10 == "Enabled" or AdditionalFields.TlsServer10 == "Enabled" 
```

## <a name="related-topics"></a>Voir aussi

- [DeviceTvmInfoGathering](advanced-hunting-devicetvminfogathering-table.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de la gestion des vulnérabilités defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
