---
title: Table DeviceLogonEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements d’authentification ou de connexion dans la table DeviceLogonEvents du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, logonevents, DeviceLogonEvents, authentification, ouverture de session, connexion
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
ms.openlocfilehash: d6c36d3e2628d9349d74d209c7fa0b7a84fc00c7
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642940"
---
# <a name="devicelogonevents"></a>DeviceLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le `DeviceLogonEvents` tableau du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les logons utilisateur et d’autres événements d’authentification sur les appareils. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | `string` |Type d’activité qui a déclenché l’événement |
| `LogonType` | `string` | Type de session d’ouverture de session, en particulier :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Journaux d’activité interactifs à distance (RDP)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services terminal, de l’assistance à distance ou d’autres clients RDP<br><br> - **Réseau** : session lancée lorsque l’ordinateur est accessible à l’aide de PsExec ou lorsque des ressources partagées sur l’ordinateur, telles que des imprimantes et des dossiers partagés, sont accessibles<br><br> - **Batch** - Session initiée par des tâches planifiées<br><br> - **Service** - Session initiée par les services au démarrage<br> |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `Protocol` | `string` | Protocole utilisé pendant la communication |
| `FailureReason` | `string` | Informations expliquant pourquoi l’action enregistrée a échoué |
| `IsLocalAdmin` | `boolean` | Indicateur booléen indiquant si l’utilisateur est un administrateur local sur l’ordinateur |
| `LogonId` | `string` | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages |
| `RemoteDeviceName` | `string` | Nom de l’ordinateur qui a effectué une opération à distance sur l’ordinateur concerné. Selon l’événement signalé, ce nom peut être un nom de domaine complet (FQDN), un nom NetBIOS ou un nom d’hôte sans informations de domaine |
| `RemoteIP` | `string` | Adresse IP de l’appareil à partir duquel la tentative d’ouverture de session a été effectuée |
| `RemoteIPType` | `string` | Type d’adresse IP, par exemple Public, Privé, Réservé, Bouclage, Teredo, FourToSixMapping et Diffusion |
| `RemotePort` | `int` | Port TCP sur l’appareil distant auquel il était connecté |
| `InitiatingProcessAccountDomain` | `string` | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | `string` | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | `string` | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte qui a exécuté le processus responsable de l’événement |
| ` InitiatingProcessAccountObjectId` | `string` | ID d’objet Azure AD du compte d’utilisateur qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | `string` | Niveau d’intégrité du processus qui a initié l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | `string` | Type de jeton indiquant la présence ou l’absence d’élévation de privilèges Access Control utilisateur (UAC) appliquée au processus qui a initié l’événement |
| `InitiatingProcessSHA1` | `string` | SHA-1 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessSHA256` | `string` | SHA-256 du processus (fichier image) qui a initié l’événement. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `InitiatingProcessMD5` | `string` | Hachage MD5 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessFileName` | `string` | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | `long` | Taille du fichier qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | `string` | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductVersion` | `string` | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
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
| `AdditionalFields` | `string` | Informations supplémentaires sur l’événement au format tableau JSON |

>[!NOTE]
>La collection de DeviceLogonEvents n’est pas prise en charge sur les appareils Windows 7 ou Windows Server 2008R2 intégrés à Defender pour point de terminaison. Nous vous recommandons de mettre à niveau vers un système d’exploitation plus récent pour une visibilité optimale de l’activité d’ouverture de session des utilisateurs.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
