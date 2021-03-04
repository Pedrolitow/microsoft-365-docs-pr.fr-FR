---
title: Fonction FileProfile() dans le recherche avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser FileProfile() pour enrichir des informations sur les fichiers dans vos résultats de requête de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, FileProfile, file profile, function, enrichment
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: f2e92967b8951cd0f5a3c394a537404db1d53819
ms.sourcegitcommit: 355bd51ab6a79d5c36a4e4f57df74ae6873eba19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50424022"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La fonction est une fonction d’enrichissement dans le recherche avancée qui ajoute les données suivantes aux `FileProfile()` fichiers trouvés par la requête. [](advanced-hunting-overview.md)

| Colonne | Type de données | Description |
|------------|-------------|-------------|
| SHA1 | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| SHA256 | string | SHA-256 du fichier à qui l’action enregistrée a été appliquée |
| MD5 | string | Hachage MD5 du fichier à l’application de l’action enregistrée |
| FileSize | int | Taille du fichier en octets |
| GlobalPrevalence | int | Nombre d’instances de l’entité observées globalement par Microsoft |
| GlobalFirstSeen | DateHeure | Date et heure à laquelle l’entité a été observée pour la première fois par Microsoft globalement |
| GlobalLastSeen | DateHeure | Date et heure de la dernière observation de l’entité par Microsoft au niveau global |
| Signataire | string | Informations sur le signataire du fichier |
| Issuer | string | Informations sur l’autorité de certification émettrice |
| SignerHash | string | Valeur de hachage unique identifiant le signataire |
| IsCertificateValid | booléen | Si le certificat utilisé pour signer le fichier est valide |
| IsRootSignerMicrosoft | booléen | Indique si le signataire du certificat racine est Microsoft |
| IsExecutable | booléen | Si le fichier est un fichier Exécutable portable (PE) |
| ThreatName | string | Nom de détection des programmes malveillants ou autres menaces détectés |
| Éditeur | string | Nom de l’organisation qui a publié le fichier |
| SoftwareName | string | Nom du produit logiciel |

## <a name="syntax"></a>Syntaxe

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Arguments

- **x**— colonne d’ID de fichier à utiliser : `SHA1` , , ou ; fonction utilise si non `SHA256` `InitiatingProcessSHA1` `InitiatingProcessSHA256` `SHA1` spécifié
- **y**— limite au nombre d’enregistrements à enrichir, de 1 à 1 000 ; utilise 100 si non spécifié


>[!TIP]
> Les fonctions d’enrichissement afficheront des informations supplémentaires uniquement lorsqu’elles sont disponibles. La disponibilité des informations varie et dépend d’un grand nombre de facteurs. Veillez à prendre cela en compte lors de l’utilisation de FileProfile() dans vos requêtes ou lors de la création de détections personnalisées. Pour de meilleurs résultats, nous vous recommandons d’utiliser la fonction FileProfile() avec SHA1.

## <a name="examples"></a>Exemples

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Projeter uniquement la colonne SHA1 et l’enrichir

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Enrichir les 500 premiers enregistrements et lister les fichiers à faible prévalence

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Obtenir d’autres exemples de requête](advanced-hunting-shared-queries.md)
