---
title: Table DeviceTvmInfoGathering dans le schéma de chasse avancé
description: Découvrez les événements d’évaluation, notamment l’état des différentes configurations et les états de la surface d’attaque des appareils dans la table DeviceTvmInfoGathering du schéma de chasse avancé.
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, gestion des vulnérabilités & menaces, TVM, gestion des appareils, logiciels, inventaire, vulnérabilités, ID CVE, OS DeviceTvmSoftwareInventoryVulnerabilities
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
ms.openlocfilehash: 738168153738f8bf4e12220829114efc0cc8beb2
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66532731"
---
# <a name="devicetvminfogathering"></a>DeviceTvmInfoGathering

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

La `DeviceTvmInfoGathering` table du schéma de chasse avancé contient [Gestion des vulnérabilités Microsoft Defender](/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management) événements d’évaluation, notamment l’état des différentes configurations et les états de la surface d’attaque des appareils. Vous pouvez utiliser ce tableau pour rechercher les événements d’évaluation liés à l’atténuation pendant zéro jour, l’évaluation de la posture pour les menaces émergentes prenant en charge les rapports d’état d’atténuation de l’analyse des menaces, les versions de protocole TLS activées sur les serveurs, etc. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `LastSeenTime` | `datetime` | Date et heure de la dernière fois que le service a vu l’appareil |
| `DeviceId` | `string` | Identificateur unique de l’appareil dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `OSPlatform` | `string` | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’événement  |

Par exemple, pour afficher les appareils affectés par la [vulnérabilité Log4Shell](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/) où l’atténuation de la solution de contournement n’a pas encore été appliquée ou a été appliquée et est en attente de redémarrage, vous pouvez utiliser la requête suivante.

```kusto
DeviceTvmInfoGathering
| where AdditionalFields.Log4JEnvironmentVariableMitigation in ("RebootRequired", "false")
| join kind=inner (
    DeviceTvmSoftwareVulnerabilities
    | where CveId == "CVE-2021-44228"
) on DeviceId
| summarize any(DeviceName), any(AdditionalFields.Log4JEnvironmentVariableMitigation) by DeviceId
```

## <a name="related-topics"></a>Sujets associés
- [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de la gestion des vulnérabilités Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Découvrez comment gérer la vulnérabilité Log4Shell dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/tvm-manage-log4shell-guidance)