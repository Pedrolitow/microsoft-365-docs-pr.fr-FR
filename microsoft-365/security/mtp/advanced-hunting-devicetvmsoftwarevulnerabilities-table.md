---
title: Table DeviceTvmSoftwareVulnerabilities dans le schéma de recherche avancé
description: Découvrez les vulnérabilités logicielles trouvées sur les appareils et la liste des mises à jour de sécurité disponibles qui s’adressent à chaque vulnérabilité dans la table DeviceTvmSoftwareVulnerabilities du schéma de recherche avancée.
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dfa0c74757a5403573a9300002b92e4b2b109ebb
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50907251"
---
# <a name="devicetvmsoftwarevulnerabilities"></a>DeviceTvmSoftwareVulnerabilities

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

>[!IMPORTANT]
> Certaines informations concernent des produits pré-publiés qui peuvent être considérablement modifiés avant leur commercialisation. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Le tableau du schéma de recherche avancée contient la liste des vulnérabilités de gestion des menaces & vulnérabilités dans les `DeviceTvmSoftwareVulnerabilities` produits logiciels [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) installés. Cette table inclut également des informations sur le système d’exploitation, les ID CVE et sur la gravité des vulnérabilités. Vous pouvez utiliser ce tableau, par exemple, pour chercher les événements impliquant des appareils qui ont des vulnérabilités graves dans leur logiciel. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

>[!NOTE]
> Les `DeviceTvmSoftwareInventory` tableaux `DeviceTvmSoftwareVulnerabilities` et les tables ont remplacé le `DeviceTvmSoftwareInventoryVulnerabilities` tableau. Ensemble, les deux premiers tableaux incluent d’autres colonnes que vous pouvez utiliser pour vous aider à informer vos activités de gestion de la vulnerablity ou à la recherche d’appareils vulnérables.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `OSVersion` | string | Version du système d’exploitation s’exécutant sur la machine |
| `OSArchitecture` | string | Architecture du système d’exploitation s’exécutant sur la machine |
| `SoftwareVendor` | string | Nom du fournisseur de logiciels |
| `SoftwareName` | string | Nom du produit logiciel |
| `SoftwareVersion` | string | Numéro de version du produit logiciel |
| `CveId` | string | Identificateur unique affecté à la vulnérabilité de sécurité dans le système Common Vulnerabilities and Exposures (CVE) |
| `VulnerabilitySeverityLevel` | string | Niveau de gravité affecté à la vulnérabilité de sécurité sur la base du score CVSS et des facteurs dynamiques influencés par le paysage des menaces |
| `RecommendedSecurityUpdate` | string | Nom ou description de la mise à jour de sécurité fournie par le fournisseur de logiciels pour résoudre la vulnérabilité |
| `RecommendedSecurityUpdateId` | string | Identificateur des mises à jour de sécurité applicables ou identificateur pour les articles de base de connaissances ou d’aide correspondants |



## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)