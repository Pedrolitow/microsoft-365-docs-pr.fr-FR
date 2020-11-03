---
title: Table DeviceEvents dans le schéma de chasse avancé
description: En savoir plus sur l’antivirus, le pare-feu et d’autres types d’événements dans la table événements d’appareils divers (DeviceEvents) du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, événements de sécurité, antivirus, pare-feu, exploit Guard, DeviceEvents
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: d3f00e506d34b4c82137f368c8c8f24e52b0247a
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48843039"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



La table ou les événements `DeviceEvents` de périphérique divers dans le schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les différents types d’événements, notamment les événements déclenchés par les contrôles de sécurité, tels que l’antivirus Windows Defender et la protection contre les attaques. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements ( `ActionType` valeurs) pris en charge par un tableau, utilisez la [référence de schéma intégrée](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) disponible dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).


| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus d’informations, consultez la [référence de schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) . |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MD5` | string | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `AccountDomain` | string | Domaine du compte |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `RemoteDeviceName` | string | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur affecté. En fonction de l’événement signalé, il peut s’agir d’un nom de domaine complet (FQDN), d’un nom NetBIOS ou d’un nom d’hôte sans informations sur le domaine. |
| `ProcessId` | int | ID de processus (PID) du processus nouvellement créé |
| `ProcessCommandLine` | string | Ligne de commande utilisée pour créer le nouveau processus |
| `ProcessCreationTime` | DateHeure | Date et heure de création du processus |
| `ProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus nouvellement créé |
| `LogonId` | string | Identificateur d’une ouverture de session. Cet identificateur est unique sur le même ordinateur qu’entre les redémarrages |
| `RegistryKey` | string | Clé de Registre à laquelle l’action enregistrée a été appliquée |
| `RegistryValueName` | string | Nom de la valeur de Registre à laquelle l’action enregistrée a été appliquée. |
| `RegistryValueData` | string | Données de la valeur de Registre auxquelles l’action enregistrée a été appliquée |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemotePort` | int | Port TCP sur l’appareil distant auquel il était connecté |
| `LocalIP` | string | Adresse IP affectée à l’ordinateur local utilisée pendant la communication |
| `LocalPort` | int | Port TCP sur l’ordinateur local utilisé pendant la communication |
| `FileOriginUrl` | string | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginIP` | string | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessLogonId` | string | Identificateur pour une session de connexion du processus ayant initié l’événement. Cet identificateur est unique sur le même ordinateur qu’entre les redémarrages |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
