---
title: Fonction FileProfile () pour la protection avancée contre les menaces Microsoft
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: d0fd359bb6f56f7c20b0a39b7fd45ec551e7e49e
ms.sourcegitcommit: 445b249a6f0420b32e49742fd7744006c7090b2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "46797781"
---
# <a name="fileprofile"></a>FileProfile()

**S’applique à :**
- Protection Microsoft contre les menaces

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
| Publisher | string | Nom de l’organisation qui a publié le fichier |
| SoftwareName | string | Nom du produit logiciel |

## <a name="syntax"></a>Syntaxe

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Arguments

- **x** — colonne ID de fichier à utiliser : `SHA1` , `SHA256` , `InitiatingProcessSHA1` ou ; la `InitiatingProcessSHA256` fonction utilise `SHA1` si elle n’est pas spécifiée
- **y** : limiter le nombre d’enregistrements à enrichir, 1-1000 ; la fonction utilise 100 si elle n’est pas spécifiée

## <a name="examples"></a>Exemples

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

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Obtenir d’autres exemples de requêtes](advanced-hunting-shared-queries.md)