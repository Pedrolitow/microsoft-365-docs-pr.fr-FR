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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a9a17c6e336704cfe09e1c864e9700a4492e8c87
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328020"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.


Le `DeviceTvmSoftwareInventory` tableau du schéma de recherche avancée contient l’inventaire de gestion des menaces [&](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) vulnérabilités des logiciels actuellement installés sur les appareils de votre réseau, y compris les informations de fin de support. Vous pouvez, par exemple, chercher des événements impliquant des appareils installés avec une version logicielle actuellement vulnérable. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

>[!NOTE]
> Les tableaux `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` et les tables ont remplacé le `DeviceTvmSoftwareInventoryVulnerabilities` tableau. Ensemble, les deux premiers tableaux incluent d’autres colonnes que vous pouvez utiliser pour vous aider à informer vos activités de gestion de la vulnerablity ou à la recherche d’appareils vulnérables.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `OSPlatform` | `string` | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `OSVersion` | `string` | Version du système d’exploitation s’exécutant sur la machine |
| `OSArchitecture` | `string` | Architecture du système d’exploitation s’exécutant sur la machine |
| `SoftwareVendor` | `string` | Nom du fournisseur de logiciels |
| `SoftwareName` | `string` | Nom du produit logiciel |
| `SoftwareVersion` | `string` | Numéro de version du produit logiciel |
| `EndOfSupportStatus` | `string` | Indique l’étape de cycle de vie du produit logiciel par rapport à sa date de fin de prise en charge (EOS) ou de fin de vie (EOL) spécifiée |
| `EndOfSupportDate` | `string` | Date de fin de support (EOS) ou de fin de vie (EOL) du produit logiciel |
| `ProductCodeCpe` | `string` | CPE du produit logiciel ou « non disponible » lorsqu’il n’y a pas de CPE |


## <a name="related-topics"></a>Sujets associés

- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)