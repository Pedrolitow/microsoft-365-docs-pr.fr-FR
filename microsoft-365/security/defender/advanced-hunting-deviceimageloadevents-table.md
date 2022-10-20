---
title: Table DeviceImageLoadEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements de chargement DLL dans la table DeviceImageLoadEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, imageloadevents, DeviceImageLoadEvents, chargement DLL, bibliothèque, image de fichier
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
ms.openlocfilehash: ea920d35f155609cc777e231ecbd0f744e986c15
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625498"
---
# <a name="deviceimageloadevents"></a>DeviceImageLoadEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

La `DeviceImageLoadEvents` table du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les événements de chargement DLL. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, consultez la référence du schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) |
| `FileName` | `string` | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | `string` | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | `string` | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | `string` | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MD5` | `string` | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `FileSize` | `long` | Taille du fichier en octets |
| `InitiatingProcessAccountDomain` | `string` | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | `string` | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | `string` | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountObjectId` | `string` | ID d’objet Azure AD du compte d’utilisateur qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | `string` | Niveau d’intégrité du processus qui a initié l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | `string` | Type de jeton indiquant la présence ou l’absence d’élévation de privilèges Access Control utilisateur (UAC) appliquée au processus qui a initié l’événement |
| `InitiatingProcessSHA1` | `string` | SHA-1 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessSHA256` | `string` | SHA-256 du processus (fichier image) qui a initié l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessMD5` | `string` | Hachage MD5 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessFileName` | `string` | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | `long` | Taille du fichier qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | `string` | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductVersion`| `string` | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoInternalFileName` | `string` | Nom de fichier interne des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Nom de fichier d’origine des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Description des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessId` | `int` | ID de processus (PID) du processus qui a initié l’événement |
| `InitiatingProcessCommandLine` | `string` | Ligne de commande utilisée pour exécuter le processus qui a lancé l’événement |
| `InitiatingProcessCreationTime` | `datetime` | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | `string` | Dossier contenant le processus (fichier image) qui a initié l’événement |
| `InitiatingProcessParentId` | `int` | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | `string` | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | `datetime` | Date et heure de démarrage du parent du processus responsable de l’événement |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `AppGuardContainerId` | `string` | Identificateur du conteneur virtualisé utilisé par Protection d'application pour isoler l’activité du navigateur |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
