---
title: Table DeviceTvmSoftwareVulnerabilitiesKB dans le schéma de repérage avancé
description: Découvrez les vulnérabilités logicielles suivies par la fonction Gestion des menaces et des vulnérabilités dans la table DeviceTvmSoftwareVulnerabilitiesKB du schéma de repérage avancé.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema, reference, kusto, table, column, data type, description, threat & gestion des vulnérabilités, TVM, device management, software, inventory, vulnerabilities, CVE ID, CVSS, DeviceTvmSoftwareVulnerabilitiesKB
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 41d05f4e4e3d234d605c32dfbf6adc29594f345d4a4655331d0296a1b0c0fc42
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53884198"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



La table `DeviceTvmSoftwareVulnerabilitiesKB` du schéma de repérage avancé contient la liste des vulnérabilités pour lesquelles la fonction [Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) évalue les appareils. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `CveId` | string | Identificateur unique affecté à la vulnérabilité de sécurité dans le système Common Vulnerabilities and Exposures (CVE) |
| `CvssScore` | string | Score de gravité attribué à la vulnérabilité de sécurité dans le cadre du système Common Vulnerability Scoring System (CVSS) |
| `IsExploitAvailable` | booléen | Indique si un code d’exploitation pour la vulnérabilité est disponible publiquement |
| `VulnerabilitySeverityLevel` | string | Niveau de gravité affecté à la vulnérabilité de sécurité sur la base du score CVSS et des facteurs dynamiques influencés par le paysage des menaces |
| `LastModifiedTime` | DateHeure | Date et heure de la dernière modification de l’élément ou des métadonnées associées |
| `PublishedDate` | DateHeure | La vulnérabilité de la date a été divulguée au public |
| `VulnerabilityDescription` | string | Description de la vulnérabilité et risques associés |
| `AffectedSoftware` | string | Liste de tous les produits logiciels concernés par la vulnérabilité |

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)