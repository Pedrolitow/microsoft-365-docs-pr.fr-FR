---
title: Table DeviceLogonEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements d’authentification ou de authentification dans la table DeviceLogonEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, logonevents, DeviceLogonEvents, authentication, logon, sign in
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
ms.openlocfilehash: b3c878c40c742c22401b9180d202da472d9e2f35
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60703272"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le tableau du schéma de recherche avancée contient des informations sur les connexions utilisateur et d’autres événements `DeviceLogonEvents` d’authentification sur les appareils. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | string |Type d’activité qui a déclenché l’événement |
| `LogonType` | chaîne | Type de session d’ouverture de session, en particulier :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Connexions RDP (Remote Interactive)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services Terminal Services, de l’Assistance à distance ou d’autres clients RDP<br><br> - **Réseau** : session initiée lorsque l’ordinateur est accessible à l’aide de PsExec ou lorsque les ressources partagées sur l’ordinateur, telles que les imprimantes et les dossiers partagés, sont accessibles<br><br> - **Batch** : session initiée par des tâches programmées<br><br> - **Service** : session initiée par les services au démarrage<br> |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `Protocol` | chaîne | Protocole utilisé pendant la communication |
| `FailureReason` | chaîne | Informations expliquant pourquoi l’action enregistrée a échoué |
| `IsLocalAdmin` | valeur booléenne | Indicateur booléen pour savoir si l’utilisateur est un administrateur local sur l’ordinateur |
| `LogonId` | chaîne | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages |
| `RemoteDeviceName` | chaîne | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur concerné. Selon l’événement signalé, ce nom peut être un nom de domaine complet (FQDN), un nom NetBIOS ou un nom d’hôte sans informations de domaine. |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteIPType` | chaîne | Type d’adresse IP, par exemple Public, Privé, Réservé, Loopback, Teredo, FourToSixMapping et Diffusion |
| `RemotePort` | int | Port TCP sur l’appareil distant connecté |
| `InitiatingProcessAccountDomain` | chaîne | Domaine du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountName` | chaîne | Nom d’utilisateur du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | chaîne | Identificateur de sécurité (SID) du compte qui a tenu le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte qui a lancé le processus responsable de l’événement |
| ` InitiatingProcessAccountObjectId` | chaîne | Azure AD’objet du compte d’utilisateur qui a tenu le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | chaîne | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple, si elles ont été lancées à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | chaîne | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus à l’origine de l’événement |
| `InitiatingProcessSHA1` | chaîne | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | chaîne | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `InitiatingProcessMD5` | chaîne | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | chaîne | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | long | Taille du fichier qui a tenu le processus responsable de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | chaîne | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | chaîne | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductVersion` | chaîne | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoInternalFileName` | chaîne | Nom de fichier interne à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | chaîne | Nom de fichier d’origine à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | chaîne | Description à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | chaîne | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | chaîne | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | chaîne | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `AppGuardContainerId` | chaîne | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |
| `AdditionalFields` | chaîne | Informations supplémentaires sur l’événement au format de tableau JSON |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
