---
title: Changements de nom dans le schéma Microsoft 365 Defender de recherche avancée
description: Suivre et passer en revue les tables et colonnes de modifications d’attribution de noms dans le schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, data, naming changes, rename
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
ms.openlocfilehash: 4082dbe9964c115df279f04d4a25ce5fbeb2cec2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60159113"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Schéma de recherche avancé : modifications d’attribution de noms

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le [schéma de recherche avancée est mis à jour](advanced-hunting-schema-tables.md) régulièrement pour ajouter de nouvelles tables et colonnes. Dans certains cas, les noms des colonnes existantes sont renommés ou remplacés pour améliorer l’expérience utilisateur. Reportez-vous à cet article pour passer en revue les modifications d’attribution de noms qui peuvent avoir un impact sur vos requêtes.

Les modifications d’attribution de noms sont automatiquement appliquées aux requêtes enregistrées dans le centre de sécurité, y compris les requêtes utilisées par les règles de détection personnalisées. Vous n’avez pas besoin de mettre à jour ces requêtes manuellement. Toutefois, vous devrez mettre à jour les requêtes suivantes :
- Requêtes qui sont exécutés à l’aide de l’API
- Requêtes enregistrées ailleurs en dehors du centre de sécurité

## <a name="december-2020"></a>Décembre 2020

| Nom du tableau | Nom de colonne d’origine | Nouveau nom de colonne | Raison du changement
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Commentaires des clients. |

## <a name="january-2021"></a>Janvier 2021

| Nom de colonne | Nom de la valeur d’origine | Nouveau nom de valeur | Raison du changement
|--|--|--|--|
| `DetectionSource` | MCAS | Microsoft Cloud App Security | Changement de nom |
| `DetectionSource` | WindowsDefenderAtp| PEPT| Changement de nom |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Changement de nom |
| `DetectionSource` | WindowsDefenderSmartScreen |  SmartScreen | Changement de nom |
| `DetectionSource` | CustomerTI | Ti personnalisée | Changement de nom |
| `DetectionSource` | OfficeATP | Microsoft Defender pour Office 365 | Changement de nom |
| `DetectionSource` | MTP | Microsoft 365 Defender | Changement de nom |
| `DetectionSource` | AzureATP | Microsoft Defender pour l’identité | Changement de nom |
| `DetectionSource` | CustomDetection | Détection personnalisée | Changement de nom |
| `DetectionSource` | AutomatedIgoigation |Examen automatisé | Changement de nom |
| `DetectionSource` | ThreatExperts | Spécialistes des menaces Microsoft | Changement de nom |
| `DetectionSource` | Ti tiers | Capteurs tiers | Changement de nom |
| `ServiceSource` | Microsoft Defender ATP| Microsoft Defender pour point de terminaison | Changement de nom |
|`ServiceSource` |Protection Microsoft contre les menaces | Microsoft 365 Defender | Changement de nom |
| `ServiceSource` | Office 365 – Protection avancée contre les menaces |Microsoft Defender pour Office 365 | Changement de nom |
| `ServiceSource` |Azure ATP |Microsoft Defender pour l’identité | Changement de nom |

`DetectionSource`est disponible dans la table [AlertInfo.](advanced-hunting-alertinfo-table.md) `ServiceSource`est disponible dans les tables [AlertEvidence](advanced-hunting-alertevidence-table.md) et [AlertInfo.](advanced-hunting-alertinfo-table.md) 

## <a name="february-2021"></a>Février 2021

1. Dans les tables [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) et [EmailEvents,](advanced-hunting-emailevents-table.md) les colonnes et les colonnes ont été remplacées `MalwareFilterVerdict` par la `PhishFilterVerdict` `ThreatTypes` colonne. Les `MalwareDetectionMethod` `PhishDetectionMethod` colonnes et les colonnes ont également été remplacées par la `DetectionMethods` colonne. Cette simplification nous permet de fournir plus d’informations sous les nouvelles colonnes. Le mappage est fourni ci-dessous.

    | Nom du tableau | Nom de colonne d’origine | Nouveau nom de colonne | Raison du changement
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Inclure d’autres méthodes de détection |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Inclure d’autres types de menaces |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Inclure d’autres méthodes de détection |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Inclure d’autres types de menaces |


2. Dans les `EmailAttachmentInfo` `EmailEvents` tableaux et les tableaux, la colonne a été ajoutée pour fournir plus `ThreatNames` d’informations sur la menace de messagerie. Cette colonne contient des valeurs telles que le courrier indésirable ou le hameçonnage.

3. Dans la table [DeviceInfo,](advanced-hunting-deviceinfo-table.md) la colonne a été remplacée par la colonne en fonction `DeviceObjectId` des commentaires des `AadDeviceId` clients.

4. Dans la table [DeviceEvents,](advanced-hunting-deviceevents-table.md) plusieurs noms ActionType ont été modifiés pour mieux refléter la description de l’action. Vous trouverez plus d’informations sur les modifications ci-dessous.

    | Nom du tableau | Nom ActionType d’origine | Nouveau nom ActionType | Raison du changement
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | Commentaires des clients. |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | Commentaires des clients. |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | Commentaires des clients. |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | Commentaires des clients. |

## <a name="march-2021"></a>mars 2021

La `DeviceTvmSoftwareInventoryVulnerabilities` table a été dépréciée. Les tables et les tables le `DeviceTvmSoftwareInventory` `DeviceTvmSoftwareVulnerabilities` remplacent.

## <a name="may-2021"></a>Mai 2021

La `AppFileEvents` table a été dépréciée. Le tableau inclut des informations qui seraient dans le tableau, ainsi que d’autres `CloudAppEvents` activités dans les services `AppFileEvents` cloud.

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)