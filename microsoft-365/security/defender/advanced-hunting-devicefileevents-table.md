---
title: Table DeviceFileEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements liés aux fichiers dans la table DeviceFileEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, filecreationevents, DeviceFileEvents, files, path, hash, sha1, sha256, md5
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
ms.openlocfilehash: 40663a06e380377ccfa33dcb41a69c42e729704d
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935508"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur la création, la modification et d'autres événements `DeviceFileEvents` de système de fichiers. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d'informations sur les types d'événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de la machine dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | string | Type d'activité qui a déclenché l'événement. Pour plus [d'informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l'action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MD5` | string | Hachage MD5 du fichier à l'application de l'action enregistrée |
| `FileOriginUrl` | string | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginReferrerUrl` | string | URL de la page web qui est lié au fichier téléchargé |
| `FileOriginIP` | string | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `PreviousFolderPath` | string | Dossier d'origine contenant le fichier avant l'application de l'action enregistrée |
| `PreviousFileName` | string | Nom d'origine du fichier qui a été renommé à la suite de l'action |
| `FileSize` | long | Taille du fichier en octets |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a dirigé le processus responsable de l'événement |
| `InitiatingProcessAccountName` | string | Nom d'utilisateur du compte qui a dirigé le processus responsable de l'événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a dirigé le processus responsable de l'événement |
| `InitiatingProcessAccountUpn` | string | Nom d'utilisateur principal (UPN) du compte qui a lancé le processus responsable de l'événement |
| `InitiatingProcessAccountObjectId` | string | ID d'objet Azure AD du compte d'utilisateur qui a tenu le processus responsable de l'événement |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | long | Taille du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | string | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | string | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
|` InitiatingProcessVersionInfoProductVersion` | string | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
|` InitiatingProcessVersionInfoInternalFileName` | string | Nom de fichier interne à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | string | Nom de fichier d’origine à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | string | Description à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessId` | entier | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessIntegrityLevel` | string | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité à des processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus à l’origine de l’événement |
| `InitiatingProcessParentId` | entier | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `RequestProtocol` | string | Protocole réseau, le cas échéant, utilisé pour lancer l’activité : Inconnu, Local, SMB ou NFS |
| `RequestSourceIP` | string | Adresse IPv4 ou IPv6 de l’appareil distant à l’origine de l’activité |
| `RequestSourcePort` | string | Port source sur l’appareil distant à l’origine de l’activité |
| `RequestAccountName` | string | Nom d’utilisateur du compte utilisé pour lancer l’activité à distance |
| `RequestAccountDomain` | string | Domaine du compte utilisé pour lancer l’activité à distance |
| `RequestAccountSid` | string | Identificateur de sécurité (SID) du compte utilisé pour lancer l’activité à distance |
| `ShareName` | string | Nom du dossier partagé contenant le fichier |
| `InitiatingProcessFileSize` | long | Taille du fichier qui a tenu le processus responsable de l’événement |
| `SensitivityLabel` | string | Étiquette appliquée à un e-mail, un fichier ou tout autre contenu pour la classer pour la protection des informations |
| `SensitivitySubLabel` | string | Sous-bel appliquée à un e-mail, un fichier ou tout autre contenu pour le classer pour la protection des informations ; les sous-étiquettes de sensibilité sont regroupées sous des étiquettes de sensibilité, mais sont traitées indépendamment |
| `IsAzureInfoProtectionApplied` | valeur booléenne | Indique si le fichier est chiffré par Azure Information Protection |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |
>[!NOTE]
> Les informations de hachage de fichier sont toujours affichées lorsqu’elles sont disponibles. Toutefois, il existe plusieurs raisons possibles pour lesquelles un SHA1, SHA256 ou MD5 ne peut pas être calculé. Par exemple, le fichier peut se trouver dans un stockage à distance, verrouillé par un autre processus, compressé ou marqué comme virtuel. Dans ces scénarios, les informations de hachage de fichier apparaissent vides.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
