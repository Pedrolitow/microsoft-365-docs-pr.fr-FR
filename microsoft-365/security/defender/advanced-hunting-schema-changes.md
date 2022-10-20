---
title: Modification du nommage dans le Microsoft 365 Defender schéma de chasse avancé
description: Suivre et passer en revue les modifications de nommage des tables et des colonnes dans le schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, données, changement de nom, renommer
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
ms.openlocfilehash: 41a46fce2c1767dc815006e0c15a0bb9b50a7706
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68622725"
---
# <a name="advanced-hunting-schema---naming-changes"></a>Schéma de chasse avancé - Modifications de nommage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le [schéma de chasse avancé](advanced-hunting-schema-tables.md) est mis à jour régulièrement pour ajouter de nouvelles tables et colonnes. Dans certains cas, les noms de colonnes existants sont renommés ou remplacés pour améliorer l’expérience utilisateur. Reportez-vous à cet article pour passer en revue les modifications de nommage susceptibles d’avoir un impact sur vos requêtes.

Les modifications de nommage sont automatiquement appliquées aux requêtes enregistrées dans Defender pour cloud, y compris les requêtes utilisées par les règles de détection personnalisées. Vous n’avez pas besoin de mettre à jour ces requêtes manuellement. Toutefois, vous devez mettre à jour les requêtes suivantes :
- Requêtes exécutées à l’aide de l’API
- Requêtes enregistrées ailleurs en dehors de Defender pour cloud

## <a name="december-2020"></a>Décembre 2020

| Nom du tableau | Nom de colonne d’origine | Nouveau nom de colonne | Raison du changement
|--|--|--|--|
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailAction` | `EmailAction` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicy` | `EmailActionPolicy` | Commentaires des clients. |
| [EmailEvents](advanced-hunting-emailevents-table.md) | `FinalEmailActionPolicyGuid` | `EmailActionPolicyGuid` | Commentaires des clients. |

## <a name="january-2021"></a>Janvier 2021

| Nom de colonne | Nom de la valeur d’origine | Nouveau nom de valeur | Raison du changement
|--|--|--|--|
| `DetectionSource` | Defender for Cloud Apps | Microsoft Defender for Cloud Apps | Rebranding |
| `DetectionSource` | WindowsDefenderAtp| EDR| Rebranding |
| `DetectionSource` | WindowsDefenderAv | Antivirus | Rebranding |
| `DetectionSource` | WindowsDefenderSmartScreen |  Smartscreen | Rebranding |
| `DetectionSource` | CustomerTI | TI personnalisée | Rebranding |
| `DetectionSource` | OfficeATP | Microsoft Defender pour Office 365 | Rebranding |
| `DetectionSource` | Mtp | Microsoft 365 Defender | Rebranding |
| `DetectionSource` | AzureATP | Microsoft Defender pour l’identité | Rebranding |
| `DetectionSource` | CustomDetection | Détection personnalisée | Rebranding |
| `DetectionSource` | AutomatedInvestigation |Investigation automatisée | Rebranding |
| `DetectionSource` | ThreatExperts | Spécialistes des menaces Microsoft | Rebranding |
| `DetectionSource` | 3e partie TI | Capteurs tiers | Rebranding |
| `ServiceSource` | Microsoft Defender ATP| Microsoft Defender pour point de terminaison | Rebranding |
|`ServiceSource` |Protection Microsoft contre les menaces | Microsoft 365 Defender | Rebranding |
| `ServiceSource` | Office 365 – Protection avancée contre les menaces |Microsoft Defender pour Office 365 | Rebranding |
| `ServiceSource` |Azure ATP |Microsoft Defender pour l’identité | Rebranding |

`DetectionSource` est disponible dans la table [AlertInfo](advanced-hunting-alertinfo-table.md) . `ServiceSource` est disponible dans les tables [AlertEvidence](advanced-hunting-alertevidence-table.md) et [AlertInfo](advanced-hunting-alertinfo-table.md) . 

## <a name="february-2021"></a>Février 2021

1. Dans les tables [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) et [EmailEvents, les colonnes](advanced-hunting-emailevents-table.md) et `PhishFilterVerdict` les `MalwareFilterVerdict`colonnes ont été remplacées par la `ThreatTypes` colonne. Les `MalwareDetectionMethod` colonnes et `PhishDetectionMethod` les colonnes ont également été remplacées par la `DetectionMethods` colonne. Cette rationalisation nous permet de fournir plus d’informations sous les nouvelles colonnes. Le mappage est fourni ci-dessous.

    | Nom du tableau | Nom de colonne d’origine | Nouveau nom de colonne | Raison du changement
    |--|--|--|--|
    | `EmailAttachmentInfo` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Inclure d’autres méthodes de détection |
    | `EmailAttachmentInfo`  | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Inclure d’autres types de menaces |
    | `EmailEvents` | `MalwareDetectionMethod` <br> `PhishDetectionMethod` | `DetectionMethods` | Inclure d’autres méthodes de détection |
    | `EmailEvents` | `MalwareFilterVerdict` <br>`PhishFilterVerdict` | `ThreatTypes` | Inclure d’autres types de menaces |


2. Dans les tables et `EmailEvents` les `EmailAttachmentInfo` tables, la `ThreatNames` colonne a été ajoutée pour fournir plus d’informations sur la menace de courrier électronique. Cette colonne contient des valeurs telles que Spam ou Phish.

3. Dans la table [DeviceInfo](advanced-hunting-deviceinfo-table.md) , la `DeviceObjectId` colonne a été remplacée par la `AadDeviceId` colonne en fonction des commentaires des clients.

4. Dans la table [DeviceEvents](advanced-hunting-deviceevents-table.md) , plusieurs noms ActionType ont été modifiés pour mieux refléter la description de l’action. Vous trouverez plus d’informations sur les modifications ci-dessous.

    | Nom du tableau | Nom ActionType d’origine | Nouveau nom ActionType | Raison du changement
    |--|--|--|--|
    | `DeviceEvents` | `DlpPocPrintJob` | `FilePrinted` | Commentaires des clients. |
    | `DeviceEvents` | `UsbDriveMount` | `UsbDriveMounted` | Commentaires des clients. |
    | `DeviceEvents` | `UsbDriveUnmount` | `UsbDriveUnmounted` | Commentaires des clients. |
    | `DeviceEvents` | `WriteProcessMemoryApiCall` | `WriteToLsassProcessMemory` | Commentaires des clients. |

## <a name="march-2021"></a>Mars 2021

La `DeviceTvmSoftwareInventoryVulnerabilities` table a été déconseillée. Les tables et `DeviceTvmSoftwareVulnerabilities` les tables le `DeviceTvmSoftwareInventory` remplacent.

## <a name="may-2021"></a>Mai 2021

La `AppFileEvents` table a été déconseillée. Le `CloudAppEvents` tableau inclut des informations qui se trouveraient dans la `AppFileEvents` table, ainsi que d’autres activités dans les services cloud.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
