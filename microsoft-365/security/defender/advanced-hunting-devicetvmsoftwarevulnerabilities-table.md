---
title: Table DeviceTvmSoftwareVulnerabilities dans le schéma de chasse avancé
description: Découvrez les vulnérabilités logicielles détectées sur les appareils et la liste des mises à jour de sécurité disponibles qui traitent chaque vulnérabilité dans la table DeviceTvmSoftwareVulnerabilities du schéma de repérage avancé.
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, gestion des vulnérabilités & menaces, TVM, gestion des appareils, logiciels, inventaire, vulnérabilités, ID CVE, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: 99a3d0a3ca730062783abd7ace664bd0bd010b18
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481479"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

>[!IMPORTANT]
> Certaines informations concernent le produit pré-publié qui peut être considérablement modifié avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

La `DeviceTvmSoftwareVulnerabilities` table du schéma de chasse avancé contient la [liste Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) des vulnérabilités dans les produits logiciels installés. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités. Vous pouvez utiliser ce tableau, par exemple, pour rechercher des événements impliquant des appareils qui présentent des vulnérabilités graves dans leurs logiciels. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

>[!NOTE]
> Les `DeviceTvmSoftwareInventory` tables et `DeviceTvmSoftwareVulnerabilities` les tables ont remplacé la `DeviceTvmSoftwareInventoryVulnerabilities` table. Ensemble, les deux premières tables incluent d’autres colonnes que vous pouvez utiliser pour vous aider à informer vos activités de gestion des vulnérabilités ou à rechercher des appareils vulnérables.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `OSPlatform` | `string` | Plateforme du système d’exploitation client s’exécutant sur la machine. Indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `OSVersion` | `string` | Version du système d’exploitation s’exécutant sur la machine |
| `OSArchitecture` | `string` | Architecture du système d’exploitation s’exécutant sur la machine |
| `SoftwareVendor` | `string` | Nom de l’éditeur de logiciels |
| `SoftwareName` | `string` | Nom du produit logiciel |
| `SoftwareVersion` | `string` | Numéro de version du produit logiciel |
| `CveId` | `string` | Identificateur unique affecté à la vulnérabilité de sécurité dans le système Common Vulnerabilities and Exposures (CVE) |
| `VulnerabilitySeverityLevel` | `string` | Niveau de gravité affecté à la vulnérabilité de sécurité sur la base du score CVSS et des facteurs dynamiques influencés par le paysage des menaces |
| `RecommendedSecurityUpdate` | `string` | Nom ou description de la mise à jour de sécurité fournie par l’éditeur de logiciels pour résoudre la vulnérabilité |
| `RecommendedSecurityUpdateId` | `string` | Identificateur des mises à jour de sécurité ou de l’identificateur applicables pour les instructions correspondantes ou les articles de base de connaissances (Ko) |



## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de Gestion des vulnérabilités Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)