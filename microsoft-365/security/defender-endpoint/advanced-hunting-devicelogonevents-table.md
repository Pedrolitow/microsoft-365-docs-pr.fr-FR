---
title: Table DeviceLogonEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements d’authentification ou de authentification dans la table DeviceLogonEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, search, query, telemetry, schema reference, kusto, table, column, data type, description, devicelogonevents, authentication, logon, sign in, LogonEvents
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c270f54c856c1ed504533c826ca884786c784549
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499150"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le tableau du schéma de recherche avancée contient des informations sur les connexions utilisateur `DeviceLogonEvents` et d’autres [](advanced-hunting-overview.md) événements d’authentification. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

> [!NOTE]
> La collection de DeviceLogonEvents n’est pas prise en charge sur Windows 7 ou Windows Server 2008 R2.
> Nous vous recommandons de mettre à niveau vers Windows 10 ou Windows Server 2019 pour une visibilité optimale de l’activité de l’utilisateur.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir [la référence du schéma de chasse avancé.](advanced-hunting-schema-reference.md)

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `ActionType` | string |Type d’activité qui a déclenché l’événement |
| `AccountDomain` | string | Domaine du compte |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `LogonType` | string | Type de session d’ouverture de session, en particulier :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’appareil à l’aide du clavier et de l’écran locaux<br><br> - **Connexions RDP (Remote Interactive)** : l’utilisateur interagit avec l’appareil à distance à l’aide du Bureau à distance, des services Terminal Services, de l’Assistance à distance ou d’autres clients RDP<br><br> - **Réseau** : session initiée lorsque l’appareil est accessible à l’aide de PsExec ou lorsque les ressources partagées sur l’appareil, telles que les imprimantes et les dossiers partagés, sont accessibles<br><br> - **Batch** : session initiée par des tâches programmées<br><br> - **Service** : session initiée par les services au démarrage<br> |
| `LogonId` | string | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même appareil uniquement entre les redémarrages |
| `RemoteDeviceName` | string | Nom de l’appareil qui a effectué une opération à distance sur l’appareil concerné. Selon l’événement signalé, ce nom peut être un nom de domaine complet (FQDN), un nom NetBIOS ou un nom d’hôte sans informations de domaine. |
| `RemoteIP` | string | Adresse IP à laquelle la connexion était en cours |
| `RemoteIPType` | string | Type d’adresse IP, par exemple Public, Privé, Réservé, Loopback, Teredo, FourToSixMapping et Diffusion |
| `RemotePort` | entier | Port TCP sur l’appareil distant connecté |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | string | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité à des processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus à l’origine de l’événement |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli ; utilisez la colonne SHA1 lorsqu’elle est disponible. |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | entier | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | entier | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les `DeviceName` colonnes et les `Timestamp` événements |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |
| `IsLocalAdmin` | booléen | Indicateur booléen pour savoir si l’utilisateur est un administrateur local sur l’appareil |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
