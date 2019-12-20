---
title: Table DeviceLogonEvents dans le schéma de chasse avancé
description: En savoir plus sur l’authentification ou les événements de connexion dans la table DeviceLogonEvents du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche de menace informatique, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, logonevents, DeviceLogonEvents, authentification, connexion, connexion
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
ms.openlocfilehash: 5e694bb58952acb0e6cd0b436c72ed3cf170a5c5
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40809272"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le `DeviceLogonEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les ouvertures de session de l’utilisateur et d’autres événements d’authentification. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | chaîne | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | string |Type d’activité qui a déclenché l’événement |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `LogonType` | chaîne | Type de session de connexion, notamment :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Ouvertures de session interactives (RDP)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services Terminal Server, de l’assistance à distance ou d’autres clients RDP<br><br> - Session **réseau** initiée lorsque l’accès à l’ordinateur est effectué à l’aide de PsExec ou lorsque des ressources partagées sur l’ordinateur, telles que des imprimantes et des dossiers partagés, sont accessibles<br><br> - Session de **traitement par lots** initiée par les tâches planifiées<br><br> - **Service** -session initialisée par les services au démarrage<br> |
| `LogonId` | chaîne | Identificateur d’une ouverture de session. Cet identificateur est unique sur le même ordinateur qu’entre les redémarrages |
| `RemoteDeviceName` | chaîne | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur affecté. En fonction de l’événement signalé, il peut s’agir d’un nom de domaine complet (FQDN), d’un nom NetBIOS ou d’un nom d’hôte sans informations sur le domaine. |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteIPType` | chaîne | Type d’adresse IP, par exemple public, Private, reserved, Loopback, Teredo, FourToSixMapping et Broadcast |
| `RemotePort` | int | Port TCP sur l’appareil distant auquel il était connecté |
| `AdditionalFields` | chaîne | Informations supplémentaires sur l’événement au format de tableau JSON |
| `InitiatingProcessAccountDomain` | chaîne | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | chaîne | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | chaîne | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | chaîne | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influent sur les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | chaîne | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus ayant initié l’événement |
| `InitiatingProcessSHA1` | chaîne | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | chaîne | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `InitiatingProcessMD5` | chaîne | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | chaîne | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | chaîne | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | chaîne | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | chaîne | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | chaîne | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |
| `IsLocalAdmin` | booléen | Indicateur booléen indiquant si l’utilisateur est un administrateur local sur l’ordinateur |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
