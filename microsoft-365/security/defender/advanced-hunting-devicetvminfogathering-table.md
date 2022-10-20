---
title: Table DeviceTvmInfoGathering dans le schéma de chasse avancé
description: Découvrez les événements d’évaluation, notamment l’état des différentes configurations et les états de la surface d’attaque des appareils dans la table DeviceTvmInfoGathering du schéma de chasse avancé.
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, threat & vulnerability management, TVM, device management, software, inventory, vulnerabilities, CVE ID, OS DeviceTvmSoftwareInventoryVulnerabilities, Gestion des vulnérabilités Microsoft Defender
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
ms.openlocfilehash: 9021b592b346516e1b2ee958582f0c68775a816d
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68645866"
---
# <a name="devicetvminfogathering"></a>DeviceTvmInfoGathering

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
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

## <a name="related-topics"></a>Voir aussi
- [DeviceTvmInfoGatheringKB](advanced-hunting-devicetvminfogatheringkb-table.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
- [Vue d’ensemble de la gestion des vulnérabilités Defender](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
- [Découvrez comment gérer la vulnérabilité Log4Shell dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/tvm-manage-log4shell-guidance)