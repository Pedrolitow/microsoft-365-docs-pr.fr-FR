---
title: Table DeviceTvmSoftwareInventory dans le schéma de recherche avancé
description: Découvrez l’inventaire des logiciels sur vos appareils dans la table DeviceTvmSoftwareInventory du schéma de recherche avancée.
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dfaf1e6346a3747b0f8a41d1d9fe806ce307f9f3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60210744"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.


Le tableau du schéma de recherche avancée contient l’inventaire de gestion des menaces & vulnérabilités des logiciels actuellement installés sur les appareils de votre réseau, y compris les informations de fin `DeviceTvmSoftwareInventory` de support. [](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) Vous pouvez, par exemple, chercher des événements impliquant des appareils qui sont installés avec une version logicielle actuellement vulnérable. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

>[!NOTE]
> Les `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` tableaux et les tables ont remplacé `DeviceTvmSoftwareInventoryVulnerabilities` le tableau. Ensemble, les deux premiers tableaux incluent d’autres colonnes que vous pouvez utiliser pour vous aider à informer vos activités de gestion de la vulnerablity ou à la recherche d’appareils vulnérables.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `OSVersion` | string | Version du système d’exploitation s’exécutant sur la machine |
| `OSArchitecture` | string | Architecture du système d’exploitation s’exécutant sur la machine |
| `SoftwareVendor` | string | Nom du fournisseur de logiciels |
| `SoftwareName` | string | Nom du produit logiciel |
| `SoftwareVersion` | string | Numéro de version du produit logiciel |
| `EndOfSupportStatus` | string | Indique l’étape de cycle de vie du produit logiciel par rapport à sa date de fin de support (EOS) ou de fin de vie (EOL) spécifiée |
| `EndOfSupportDate` | string | Date de fin de support (EOS) ou de fin de vie (EOL) du produit logiciel |



## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)