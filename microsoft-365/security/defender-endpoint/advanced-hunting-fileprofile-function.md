---
title: Fonction FileProfile() dans le recherche avancée de Microsoft Defender pour point de terminaison
description: Découvrez comment utiliser FileProfile() pour enrichir des informations sur les fichiers dans vos résultats de requête de recherche avancée
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
ms.openlocfilehash: 6c828418d27db24cbd6e87f040486b3abc45e6c6
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499551"
---
# <a name="fileprofile"></a>FileProfile()

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

La fonction est une fonction d’enrichissement dans le recherche avancée qui ajoute les données suivantes `FileProfile()` aux fichiers trouvés par la requête. [](advanced-hunting-overview.md)

Column | Type de données | Description
-|-|-
SHA1 | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée
SHA256 | string | SHA-256 du fichier à qui l’action enregistrée a été appliquée
MD5 | string | Hachage MD5 du fichier à l’application de l’action enregistrée
FileSize | entier | Taille du fichier en octets
GlobalPrevalence | entier | Nombre d’instances de l’entité observées globalement par Microsoft
GlobalFirstSeen | DateHeure | Date et heure à laquelle l’entité a été observée pour la première fois par Microsoft globalement
GlobalLastSeen | DateHeure | Date et heure de la dernière observation de l’entité par Microsoft au niveau global
Signataire | string | Informations sur le signataire du fichier
Issuer | string | Informations sur l’autorité de certification émettrice
SignerHash | string | Valeur de hachage unique identifiant le signataire
IsCertificateValid | booléen | Si le certificat utilisé pour signer le fichier est valide
IsRootSignerMicrosoft | booléen | Indique si le signataire du certificat racine est Microsoft
IsExecutable | booléen | Si le fichier est un fichier PE (Portable Executable)
ThreatName | string | Nom de détection des programmes malveillants ou autres menaces détectés
Éditeur | string | Nom de l’organisation qui a publié le fichier
SoftwareName | string | Nom du produit logiciel

## <a name="syntax"></a>Syntaxe

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>Arguments

- **x** — colonne d’ID de fichier à utiliser `SHA1` : , ou ; fonction utilise si non `SHA256` `InitiatingProcessSHA1` `InitiatingProcessSHA256` `SHA1` spécifié
- **y** — limite au nombre d’enregistrements à enrichir, de 1 à 1 000 ; utilise 100 si non spécifié

## <a name="examples"></a>Exemples

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Projeter uniquement la colonne SHA1 et l’enrichir

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>Enrichir les 500 premiers enregistrements et lister les fichiers de faible prévalence

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
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
