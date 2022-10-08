---
title: Table DeviceTvmSoftwareEvidenceBeta dans le schéma de chasse avancé
description: Découvrez comment utiliser la table DeviceTvmSoftwareEvidenceBeta dans le schéma de chasse avancé.
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, gestion des vulnérabilités & menaces, preuve, preuves logicielles, TVM, gestion des appareils, logiciels, inventaire, vulnérabilités, ID CVE, OS DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 89a7e0636dc603f048b12511b1f3b37e88ed4002
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072940"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

> [!IMPORTANT]
> La `DeviceTvmSoftwareEvidenceBeta` table est actuellement en version bêta. Une fois qu’il quitte la version bêta, le nom de la table finale change et les noms de colonnes peuvent également changer. Les modifications interrompent alors probablement les requêtes qui utilisent encore des noms précédents. Il est recommandé aux utilisateurs d’examiner et d’ajuster leurs requêtes lorsque cette table est finalisée. 

La `DeviceTvmSoftwareEvidenceBeta` table du schéma de chasse avancé contient des données de [Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) liées à la [section de preuves logicielles](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence). Ce tableau vous permet d’afficher des preuves de l’emplacement où un logiciel spécifique a été détecté sur un appareil. Vous pouvez utiliser ce tableau, par exemple, pour identifier les chemins d’accès aux fichiers de logiciels spécifiques. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `SoftwareVendor` | `string` | Nom de l’éditeur de logiciels |
| `SoftwareName` | `string` | Nom du produit logiciel |
| `SoftwareVersion` | `string` | Numéro de version du produit logiciel |
| `RegistryPaths` | `dynamic` | Chemins d’accès au Registre où des preuves indiquant l’existence du logiciel sur un appareil ont été détectées |
| `DiskPaths` | `dynamic` | Chemins de disque où des preuves au niveau du fichier indiquant l’existence du logiciel sur un appareil ont été détectées |
| `LastSeenTime` | `string` | Date et heure de la dernière consultation de l’appareil par ce service |

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble de Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
