---
title: Table DeviceProcessEvents dans le schéma de recherche avancé
description: En savoir plus sur le processus de création ou d’événements de création dans DeviceProcessEventstable du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, processcreationevents, DeviceProcessEvents, process id, command line, DeviceProcessEvents
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e7ca7d70d867b623692d2eb0d87b178e528acf285fb32cf274c68837408c8f24
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863450"
---
# <a name="deviceprocessevents"></a>DeviceProcessEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison



Le tableau du schéma de recherche avancée contient des informations sur `DeviceProcessEvents` la création de processus et les événements connexes. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MD5` | string | Hachage MD5 du fichier à l’application de l’action enregistrée |
| `FileSize` | long | Taille du fichier en octets |
| `ProcessVersionInfoCompanyName` | string | Nom de la société à partir des informations de version du processus nouvellement créé |
| `ProcessVersionInfoProductName` | string | Nom du produit à partir des informations de version du processus nouvellement créé |
| `ProcessVersionInfoProductVersion` | string | Version du produit à partir des informations de version du processus nouvellement créé |
| `ProcessVersionInfoInternalFileName` | string | Nom de fichier interne à partir des informations de version du processus nouvellement créé |
| `ProcessVersionInfoOriginalFileName` | string | Nom de fichier d’origine à partir des informations de version du processus nouvellement créé |
| `ProcessVersionInfoFileDescription` | string | Description à partir des informations de version du processus nouvellement créé |
| `ProcessId` | int | ID de processus (PID) du processus nouvellement créé |
| `ProcessCommandLine` | string | Ligne de commande utilisée pour créer le nouveau processus |
| `ProcessIntegrityLevel` | string | Niveau d’intégrité du processus nouvellement créé. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Sur Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `ProcessTokenElevation` | string | Indique le type d’élévation de jeton appliqué au processus nouvellement créé. Valeurs possibles : TokenElevationTypeLimited (restreint), TokenElevationTypeDefault (standard) et TokenElevationTypeFull (élevé) |
| `ProcessCreationTime` | DateHeure | Date et heure de création du processus |
| `AccountDomain` | string | Domaine du compte |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `LogonId` | string | Identificateur d’une session d’ouverture de session. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | string | Nom d’utilisateur principal (UPN) du compte qui a lancé le processus responsable de l’événement |
| `InitiatingProcessAccountObjectId` | string | ID d’objet Azure AD du compte d’utilisateur qui a tenu le processus responsable de l’événement |
| `InitiatingProcessLogonId` | string | Identificateur d’une session d’ouverture de session du processus à l’origine de l’événement. Cet identificateur est unique sur le même ordinateur uniquement entre les redémarrages. |
| `InitiatingProcessIntegrityLevel` | string | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple, si elles ont été lancées à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus à l’origine de l’événement |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | long | Taille du fichier qui a tenu le processus responsable de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | string | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | string | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductVersion` | string | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoInternalFileName` | string | Nom de fichier interne à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | string | Nom de fichier d’origine à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | string | Description à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `InitiatingProcessSignerType` | string | Type de signataire de fichier du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSignatureStatus` | string | Informations sur l’état de signature du processus (fichier image) à l’origine de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |
| `AdditionalFields` | string | Informations supplémentaires sur l’événement au format de tableau JSON |


## <a name="related-topics"></a>Sujets connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
