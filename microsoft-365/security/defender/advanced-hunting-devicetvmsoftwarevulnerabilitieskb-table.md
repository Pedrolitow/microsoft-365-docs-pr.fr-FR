---
title: Table DeviceTvmSoftwareVulnerabilitiesKB dans le schéma de chasse avancé
description: Découvrez les vulnérabilités logicielles suivies par Gestion des vulnérabilités Microsoft Defender dans la table DeviceTvmSoftwareVulnerabilitiesKB du schéma de chasse avancé.
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, schéma, référence, kusto, table, colonne, type de données, description, gestion des vulnérabilités & menaces, TVM, gestion des appareils, logiciels, inventaire, vulnérabilités, ID CVE, CVSS, DeviceTvmSoftwareVulnerabilitiesKB
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
ms.topic: conceptual
ms.openlocfilehash: 221684faa9106de680393767654a1ca49fa425bd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68622769"
---
# <a name="devicetvmsoftwarevulnerabilitieskb"></a>DeviceTvmSoftwareVulnerabilitiesKB

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



La `DeviceTvmSoftwareVulnerabilitiesKB` table du schéma de chasse avancé contient la liste des vulnérabilités [Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) évalue les appareils. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `CveId` | `string` | Identificateur unique affecté à la vulnérabilité de sécurité dans le système Common Vulnerabilities and Exposures (CVE) |
| `CvssScore` | `string` | Score de gravité attribué à la vulnérabilité de sécurité dans le cadre du système Common Vulnerability Scoring System (CVSS) |
| `IsExploitAvailable` | `boolean` | Indique si un code d’exploitation pour la vulnérabilité est disponible publiquement |
| `VulnerabilitySeverityLevel` | `string` | Niveau de gravité affecté à la vulnérabilité de sécurité sur la base du score CVSS et des facteurs dynamiques influencés par le paysage des menaces |
| `LastModifiedTime` | `datetime` | Date et heure de la dernière modification de l’élément ou des métadonnées associées |
| `PublishedDate` | `datetime` | La vulnérabilité de la date a été divulguée au public |
| `VulnerabilityDescription` | `string` | Description de la vulnérabilité et risques associés |
| `AffectedSoftware` | `string` | Liste de tous les produits logiciels concernés par la vulnérabilité |

## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)