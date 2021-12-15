---
title: Table DeviceTvmSoftwareVulnerabilities dans le schéma de recherche avancé
description: Découvrez les vulnérabilités logicielles trouvées sur les appareils et la liste des mises à jour de sécurité disponibles qui adressent chaque vulnérabilité dans la table DeviceTvmSoftwareVulnerabilities du schéma de recherche avancée.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & gestion des vulnérabilités, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: a6588134ba2cdf166a465998cd0b1a4fd7134dbb
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531522"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

>[!IMPORTANT]
> Certaines informations concernent des produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Le tableau du schéma de recherche avancée contient la liste des vulnérabilités de gestion des menaces & vulnérabilités dans les `DeviceTvmSoftwareVulnerabilities` produits logiciels [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) installés. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités. Vous pouvez utiliser ce tableau, par exemple, pour chercher les événements impliquant des appareils qui ont des vulnérabilités graves dans leur logiciel. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

>[!NOTE]
> Les `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` tableaux et les tables ont remplacé `DeviceTvmSoftwareInventoryVulnerabilities` le tableau. Ensemble, les deux premiers tableaux incluent d’autres colonnes que vous pouvez utiliser pour vous aider à gestion des vulnérabilités activités ou à la recherche d’appareils vulnérables.

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
| `RecommendedSecurityUpdateId` | `string` | Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou d’aide correspondants |



## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)