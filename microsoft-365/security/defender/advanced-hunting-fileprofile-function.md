---
title: FileProfile() fonction dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser FileProfile() pour enrichir des informations sur les fichiers dans vos résultats de requête de repérage avancés
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, FileProfile, profil de fichier, fonction, enrichissement
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
ms.openlocfilehash: 3e530bd9c1e6af58c83a88fc16b5ac4f9aee60e0
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2022
ms.locfileid: "66797926"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `FileProfile()` fonction est une fonction d’enrichissement dans la [chasse avancée](advanced-hunting-overview.md) qui ajoute les données suivantes aux fichiers trouvés par la requête.

| Column | Type de données | Description |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | `string` | SHA-256 du fichier auquel l’action enregistrée a été appliquée |
| `MD5` | `string` | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `FileSize` | `int` | Taille du fichier en octets |
| `GlobalPrevalence` | `int` | Nombre d’instances de l’entité observées par Microsoft globalement |
| `GlobalFirstSeen` | `datetime` | Date et heure auxquelles l’entité a été observée pour la première fois par Microsoft globalement |
| `GlobalLastSeen` | `datetime` | Date et heure de la dernière observation de l’entité par Microsoft à l’échelle mondiale |
| `Signer` | `string` | Informations sur le signataire du fichier |
| `Issuer` | `string` | Informations sur l’autorité de certification émettrice |
| `SignerHash` | `string` | Valeur de hachage unique identifiant le signataire |
| `IsCertificateValid` | `boolean` | Indique si le certificat utilisé pour signer le fichier est valide |
| `IsRootSignerMicrosoft` | `boolean` | Indique si le signataire du certificat racine est Microsoft et si le fichier est intégré au système d’exploitation Windows |
| `SignatureState` | `string` | État de la signature de fichier : SignedValid - le fichier est signé avec une signature valide, SignedInvalid - le fichier est signé, mais le certificat n’est pas valide, Non signé - le fichier n’est pas signé, Inconnu - les informations sur le fichier ne peuvent pas être récupérées
| `IsExecutable` | `boolean` | Indique si le fichier est un fichier exécutable portable (PE) |
| `ThreatName` | `string` | Nom de détection des programmes malveillants ou autres menaces détectées |
| `Publisher` | `string` | Nom de l’organisation qui a publié le fichier |
| `SoftwareName` | `string` | Nom du produit logiciel |

## <a name="syntax"></a>Syntaxe

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Arguments

- **x** : colonne d’ID de fichier à utiliser : `SHA1`, `SHA256`, `InitiatingProcessSHA1`ou `InitiatingProcessSHA256`; fonction utilise `SHA1` si elle n’est pas spécifiée
- **y**— limite au nombre d’enregistrements à enrichir, de 1 à 1 000; la fonction utilise 100 si elle n’est pas spécifiée


>[!TIP]
> Les fonctions d’enrichissement affichent des informations supplémentaires uniquement lorsqu’elles sont disponibles. La disponibilité de l’information varie et dépend de nombreux facteurs. Veillez à prendre cela en compte lors de l’utilisation de FileProfile() dans vos requêtes ou lors de la création de détections personnalisées. Pour de meilleurs résultats, nous vous recommandons d’utiliser la fonction FileProfile() avec SHA1.

## <a name="examples"></a>Exemples

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Projeter uniquement la colonne SHA1 et l’enrichir

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Enrichir les 500 premiers enregistrements et répertorier les fichiers à faible prévalence

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Obtenir d’autres exemples de requête](advanced-hunting-shared-queries.md)
