---
title: Fonction FileProfile () dans la chasse avancée pour Microsoft 365 Defender
description: Découvrez comment utiliser le FileProfile () pour enrichir les informations sur les fichiers dans les résultats de la recherche avancée de la chasse
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 31959ed146df52aa6568f7aa60617b74ab8dd4db
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48847451"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `FileProfile()` fonction est une fonction d’enrichissement dans la [chasse avancée](advanced-hunting-overview.md) qui ajoute les données suivantes aux fichiers trouvés par la requête.

| Colonne | Type de données | Description |
|------------|-------------|-------------|
| Algorithm | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| SHA256 | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée |
| MD5 | string | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| FileSize | int | Taille du fichier en octets |
| GlobalPrevalence | int | Nombre d’instances de l’entité observées par Microsoft globalement |
| GlobalFirstSeen | DateHeure | Date et heure auxquelles l’entité a été observée pour la première fois par Microsoft de manière globale |
| GlobalLastSeen | DateHeure | Date et heure auxquelles l’entité a été observée pour la dernière fois par Microsoft globalement |
| Signataire | string | Informations sur le signataire du fichier |
| Issuer | string | Informations sur l’autorité de certification émettrice |
| SignerHash | string | Valeur de hachage unique identifiant le signataire |
| IsCertificateValid | valeur booléenne | Si le certificat utilisé pour signer le fichier est valide |
| IsRootSignerMicrosoft | valeur booléenne | Indique si le signataire du certificat racine est Microsoft |
| IsExecutable | valeur booléenne | Indique si le fichier est un fichier exécutable portable (PE) |
| ThreatName | string | Nom de détection pour tout programme malveillant ou autre menace détectée |
| Éditeur | string | Nom de l’organisation qui a publié le fichier |
| SoftwareName | string | Nom du produit logiciel |

## <a name="syntax"></a>Syntaxe

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Arguments

- **x** — colonne d’ID de fichier à utiliser : `SHA1` , `SHA256` , `InitiatingProcessSHA1` , ou `InitiatingProcessSHA256` ; la fonction est utilisée `SHA1` si elle n’est pas spécifiée
- **y** : limiter le nombre d’enregistrements à enrichir, 1-1000 ; la fonction utilise 100 si elle n’est pas spécifiée

## <a name="examples"></a>範例

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Projet uniquement la colonne SHA1 et enrichir celle-ci

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Enrichir les premiers 500 enregistrements et répertorier les fichiers à faible prévalence

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
- [Obtenir d’autres exemples de requêtes](advanced-hunting-shared-queries.md)
