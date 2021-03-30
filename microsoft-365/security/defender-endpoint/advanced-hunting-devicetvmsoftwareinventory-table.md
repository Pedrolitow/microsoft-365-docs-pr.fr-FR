---
title: Table DeviceTvmSoftwareInventory dans le schéma de recherche avancé
description: Découvrez l’inventaire des logiciels sur vos appareils dans la table DeviceTvmSoftwareInventory du schéma de recherche avancée.
keywords: advanced hunting, threat hunting, cyber threat hunting, mdatp, microsoft defender atp, wdatp search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.technology: mde
ms.openlocfilehash: 18e43d8e38c24a8aa28c6455dc1a769b8da0df2b
ms.sourcegitcommit: c75aac39ee8d93218a79585113ef6b36f47c9ddf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2021
ms.locfileid: "51408622"
---
# <a name="devicetvmsoftwareinventory"></a>DeviceTvmSoftwareInventory

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Le tableau du schéma de recherche avancée contient l’inventaire de gestion des menaces et des vulnérabilités des logiciels actuellement installés sur les appareils de votre réseau, y compris les informations de fin `DeviceTvmSoftwareInventory` de support. [](next-gen-threat-and-vuln-mgt.md) Vous pouvez, par exemple, chercher des événements impliquant des appareils qui sont installés avec une version logicielle actuellement vulnérable. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

DeviceTVMSoftwareInventory contient tous les logiciels dont la gestion des menaces et des vulnérabilités a pu correspondre à une CPE (Common Platform Enumeration), qu’elle soit vulnérable ou non.

>[!NOTE]
>Les `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` tableaux et les tables ont remplacé `DeviceTvmSoftwareInventoryVulnerabilities` le tableau. Ensemble, les deux premiers tableaux incluent d’autres colonnes que vous pouvez utiliser pour vous aider à informer vos activités de gestion des vulnérabilités.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `DeviceId` | string | Identificateur unique de l’appareil dans le service. |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil. |
| `OSPlatform` | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `OSVersion` | string | Version du système d’exploitation en cours d’exécution sur l’appareil. |
| `OSArchitecture` | string | Architecture du système d’exploitation en cours d’exécution sur l’appareil. |
| `SoftwareVendor` | string | Nom du fournisseur de logiciels. |
| `SoftwareName` | string | Nom du produit logiciel. |
| `SoftwareVersion` | string | Numéro de version du produit logiciel. |
| `EndOfSupportStatus` | string | Indique l’étape de cycle de vie du produit logiciel par rapport à sa date de fin de prise en charge (EOS) ou de fin de vie (EOL) spécifiée. |
| `EndOfSupportDate` | string | Date de fin de support (EOS) ou de fin de vie (EOL) du produit logiciel. |

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
- [Présentation de la fonction Gestion des menaces et des vulnérabilités](next-gen-threat-and-vuln-mgt.md)
