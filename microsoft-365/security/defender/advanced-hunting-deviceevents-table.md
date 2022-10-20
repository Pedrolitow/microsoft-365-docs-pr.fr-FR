---
title: Table DeviceEvents dans le schéma de chasse avancé
description: En savoir plus sur l’antivirus, le pare-feu et d’autres types d’événements dans la table d’événements d’appareil divers (DeviceEvents) du schéma de chasse avancé
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, événements de sécurité, antivirus, pare-feu, exploit guard, DeviceEvents
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
ms.openlocfilehash: 6f27f6a3a72be07388491b5968371ddde43b43df
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68625520"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

La table ou `DeviceEvents` les événements divers de l’appareil dans le schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur différents types d’événements, y compris les événements déclenchés par les contrôles de sécurité, tels que Microsoft Defender Antivirus et exploit protection. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

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
| `AccountDomain` | `string` | Domaine du compte |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `RemoteUrl` | `string` | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `RemoteDeviceName` | `string` | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur concerné. Selon l’événement signalé, ce nom peut être un nom de domaine complet (FQDN), un nom NetBIOS ou un nom d’hôte sans informations de domaine |
| `ProcessId` | `int` | ID de processus (PID) du processus nouvellement créé |
| `ProcessCommandLine` | `string` | Ligne de commande utilisée pour créer le nouveau processus |
| `ProcessCreationTime` | `datetime` | Date et heure de création du processus |
| `ProcessTokenElevation` | `string` | Type de jeton indiquant la présence ou l’absence d’élévation de privilèges Access Control utilisateur (UAC) appliquée au processus nouvellement créé |
| `LogonId` | `string` | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages |
| `RegistryKey` | `string` | Clé de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueName` | `string` | Nom de la valeur de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueData` | `string` | Données de la valeur de Registre à laquelle l’action enregistrée a été appliquée |
| `RemoteIP` | `string` | Adresse IP à laquelle la connexion était en cours |
| `RemotePort` | `int` | Port TCP sur l’appareil distant auquel il était connecté |
| `LocalIP` | `string` | Adresse IP affectée à l’ordinateur local utilisé pendant la communication |
| `LocalPort` | `int` | Port TCP sur l’ordinateur local utilisé pendant la communication |
| `FileOriginUrl` | `string` | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginIP` | `string` | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `InitiatingProcessSHA1` | `string` | SHA-1 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessSHA256` | `string` | SHA-256 du processus (fichier image) qui a initié l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessMD5` | `string` | Hachage MD5 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessFileName` | `string` | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | `long` | Taille du fichier qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessFolderPath` | `string` | Dossier contenant le processus (fichier image) qui a initié l’événement |
| `InitiatingProcessId` | `int` | ID de processus (PID) du processus qui a initié l’événement |
| `InitiatingProcessCommandLine` | `string` | Ligne de commande utilisée pour exécuter le processus qui a lancé l’événement |
| `InitiatingProcessCreationTime` | `datetime` | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessAccountDomain` | `string` | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | `string` | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | `string` | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountObjectId` | `string` | ID d’objet Azure AD du compte d’utilisateur qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | `string` | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Nom de fichier interne des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Nom de fichier d’origine des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Description des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessParentId` | `int` | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | `string` | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | `datetime` | Date et heure de démarrage du parent du processus responsable de l’événement |
| `InitiatingProcessLogonId` | `string` | Identificateur d’une session d’ouverture de session du processus à l’origine de l’événement. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `AppGuardContainerId` | `string` | Identificateur du conteneur virtualisé utilisé par Protection d'application pour isoler l’activité du navigateur |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’événement au format tableau JSON |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
