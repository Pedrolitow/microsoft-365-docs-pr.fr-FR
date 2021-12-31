---
title: Table DeviceTvmSoftwareEvidenceBeta dans le schéma de recherche avancé
description: Découvrez comment utiliser la table DeviceTvmSoftwareEvidenceBeta dans le schéma de recherche avancé.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & gestion des vulnérabilités, evidence, software evidence, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareEvidenceBeta
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
ms.openlocfilehash: 7fd064b906e4afe5e337df85d9dc6f174edc99cf
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2021
ms.locfileid: "61645837"
---
# <a name="devicetvmsoftwareevidencebeta"></a>DeviceTvmSoftwareEvidenceBeta

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

> [!IMPORTANT]
> Le `DeviceTvmSoftwareEvidenceBeta` tableau est actuellement en version bêta. Une fois qu’il quitte la version bêta, le nom de la table finale change et les noms de colonne peuvent également changer. Les modifications ruptureront probablement les requêtes qui utilisent encore des noms précédents. Il est conseillé aux utilisateurs d’examiner et d’ajuster leurs requêtes lors de la finalisation de ce tableau. 


Le tableau dans le schéma de recherche avancée contient les données de `DeviceTvmSoftwareEvidenceBeta` [threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) liées à la section preuve [logicielle.](/microsoft-365/security/defender-endpoint/tvm-software-inventory#software-evidence) Ce tableau vous permet d’afficher les preuves de l’endroit où un logiciel spécifique a été détecté sur un appareil. Vous pouvez utiliser ce tableau, par exemple, pour identifier les chemins d’accès aux fichiers de logiciels spécifiques. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `SoftwareVendor` | `string` | Nom de l’éditeur de logiciels |
| `SoftwareName` | `string` | Nom du produit logiciel |
| `SoftwareVersion` | `string` | Numéro de version du produit logiciel |
| `RegistryPaths` | `dynamic` | Chemins du Registre où des preuves indiquant l’existence du logiciel sur un appareil ont été détectées |
| `DiskPaths` | `dynamic` | Chemins d’accès aux disques où des preuves au niveau du fichier indiquant l’existence du logiciel sur un appareil ont été détectées |
| `LastSeenTime` | `string` | Date et heure de la dernière vue de l’appareil par ce service |




## <a name="related-topics"></a>Voir aussi

- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
