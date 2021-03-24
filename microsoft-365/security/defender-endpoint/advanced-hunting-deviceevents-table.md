---
title: Table DeviceEvents dans le schéma de recherche avancé
description: En savoir plus sur l’antivirus, le pare-feu et d’autres types d’événements dans le tableau Divers événements de périphérique (DeviceEvents) du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, search, query, telemetry, schema reference, kusto, table, column, data type, security events, antivirus, firewall, exploit guard, MiscEvents
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 49a0b608caa6d759f58889e6f831f84d2b4b90d3
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064385"
---
# <a name="deviceevents"></a>DeviceEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le tableau ou les événements divers de périphérique dans le schéma de recherche avancée contient des informations sur différents types d’événements, y compris les événements déclenchés par des contrôles de sécurité, tels que l’Antivirus Microsoft Defender et `DeviceEvents` Exploit Protection. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir la référence de schéma [de chasse avancée.](advanced-hunting-schema-reference.md)

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `MD5` | string | Hachage MD5 du fichier à l’application de l’action enregistrée |
| `AccountDomain` | string | Domaine du compte |
| `AccountName` |string | Nom d’utilisateur du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `RemoteUrl` | string | URL ou nom de domaine complet (FQDN) à laquelle/auquel la connexion était en cours |
| `RemoteDeviceName` | string | Nom de l’appareil qui a effectué une opération à distance sur l’appareil concerné. Selon l’événement signalé, ce nom peut être un nom de domaine complet (FQDN), un nom NetBIOS ou un nom d’hôte sans informations de domaine. |
| `ProcessId` | entier | ID de processus (PID) du processus nouvellement créé |
| `ProcessCommandLine` | string | Ligne de commande utilisée pour créer le nouveau processus |
| `ProcessCreationTime` | DateHeure | Date et heure de création du processus |
| `ProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus nouvellement créé |
| `LogonId` | string | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même appareil uniquement entre les redémarrages |
| `RegistryKey` | string | Clé de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueName` | string | Nom de la valeur de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueData` | string | Données de la valeur de Registre à l’application de l’action enregistrée |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemotePort` | entier | Port TCP sur l’appareil distant connecté |
| `LocalIP` | string | Adresse IP attribuée à l’appareil local utilisé lors de la communication |
| `LocalPort` | entier | Port TCP sur l’appareil local utilisé lors de la communication |
| `FileOriginUrl` | string | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginIP` | string | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessId` | entier | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessParentId` | entier | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a tenu le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a tenu le processus responsable de l’événement |
| `InitiatingProcessLogonId` | string | Identificateur d’une session d’ouverture de session du processus à l’origine de l’événement. Cet identificateur est unique sur le même appareil uniquement entre les redémarrages |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les `DeviceName` colonnes et les `Timestamp` événements |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
