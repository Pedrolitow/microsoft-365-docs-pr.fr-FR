---
title: Table DeviceEvents dans le schéma de chasse avancé
description: En savoir plus sur l’antivirus, le pare-feu et d’autres types d’événements dans la table événements d’appareils divers (DeviceEvents) du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche de menace pour la cybercriminalité, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, événements de sécurité, antivirus, pare-feu, exploit Guard, DeviceEvents
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: aec5751cf400f94abaf259aaa5fe2238b4b91311
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40809274"
---
# <a name="deviceevents"></a>DeviceEvents

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

La table ou `DeviceEvents` les événements de périphérique divers dans le schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les différents types d’événements, notamment les événements déclenchés par les contrôles de sécurité, tels que l’antivirus Windows Defender et la protection contre les attaques. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).


| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | chaîne | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | chaîne | Type d’activité qui a déclenché l’événement |
| `FileName` | chaîne | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | chaîne | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | chaîne | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | chaîne | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `MD5` | chaîne | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `RemoteUrl` | chaîne | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `RemoteDeviceName` | string | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur affecté. En fonction de l’événement signalé, il peut s’agir d’un nom de domaine complet (FQDN), d’un nom NetBIOS ou d’un nom d’hôte sans informations sur le domaine. |
| `ProcessId` | int | ID de processus (PID) du processus nouvellement créé |
| `ProcessCommandLine` | chaîne | Ligne de commande utilisée pour créer le nouveau processus |
| `ProcessCreationTime` | DateHeure | Date et heure de création du processus |
| `ProcessTokenElevation` | chaîne | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus nouvellement créé |
| `LogonId` | chaîne | Identificateur d’une ouverture de session. Cet identificateur est unique sur le même ordinateur qu’entre les redémarrages |
| `RegistryKey` | chaîne | Clé de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueName` | chaîne | Nom de la valeur de Registre à laquelle l’action enregistrée a été appliquée. |
| `RegistryValueData` | chaîne | Données de la valeur de Registre auxquelles l’action enregistrée a été appliquée |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemotePort` | int | Port TCP sur l’appareil distant auquel il était connecté |
| `LocalIP` | chaîne | Adresse IP affectée à l’ordinateur local utilisée pendant la communication |
| `LocalPort` | int | Port TCP sur l’ordinateur local utilisé pendant la communication |
| `FileOriginUrl` | chaîne | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginIP` | chaîne | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `AdditionalFields` | chaîne | Informations supplémentaires sur l’événement au format de tableau JSON |
| `InitiatingProcessSHA1` | chaîne | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | chaîne | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `InitiatingProcessFileName` | chaîne | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | chaîne | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | chaîne | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | chaîne | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `InitiatingProcessMD5` | chaîne | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessAccountDomain` | chaîne | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | chaîne | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | chaîne | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessLogonId` | chaîne | Identificateur pour une session de connexion du processus ayant initié l’événement. Cet identificateur est unique sur le même ordinateur qu’entre les redémarrages |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | chaîne | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
