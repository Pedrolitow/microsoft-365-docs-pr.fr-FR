---
title: Table DeviceFileEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements liés aux fichiers dans la table DeviceFileEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, filecreationevents, DeviceFileEvents, fichiers, chemin, hachage, sha1, sha256, md5
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: 64962d5a6bfb3a051e64cb2658a073d9100c2b6b
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67466918"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

La `DeviceFileEvents` table du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur la création, la modification et d’autres événements du système de fichiers. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `DeviceId` | `string` | Identificateur unique de la machine dans le service |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, consultez la référence du schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) |
| `FileName` | `string`| Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | `string` | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | `string` | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | `string` | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MD5` | `string` | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `FileOriginUrl` | `string` | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginReferrerUrl` | `string` | URL de la page web qui est liée au fichier téléchargé |
| `FileOriginIP` | `string` | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `PreviousFolderPath` | `string` | Dossier d’origine contenant le fichier avant l’application de l’action enregistrée |
| `PreviousFileName` | `string` | Nom d’origine du fichier qui a été renommé à la suite de l’action |
| `FileSize` | `long` | Taille du fichier en octets |
| `InitiatingProcessAccountDomain` | `string` | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | `string` | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountObjectId` | `string` | ID d’objet Azure AD du compte d’utilisateur qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessMD5` | `string` | Hachage MD5 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessSHA1` | `string` | SHA-1 du processus (fichier image) qui a initié l’événement |
| `InitiatingProcessSHA256` | `string` | SHA-256 du processus (fichier image) qui a initié l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessFolderPath` | `string` | Dossier contenant le processus (fichier image) qui a initié l’événement |
| `InitiatingProcessFileName` | `string` | Nom du processus à l’origine de l’événement |
| `InitiatingProcessFileSize` | `long` | Taille du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessVersionInfoCompanyName` | `string` | Nom de la société à partir des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoProductName` | `string` | Nom du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
|` InitiatingProcessVersionInfoProductVersion` | `string` | Version du produit à partir des informations de version du processus (fichier image) responsable de l’événement |
|` InitiatingProcessVersionInfoInternalFileName` | `string` | Nom de fichier interne des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoOriginalFileName` | `string` | Nom de fichier d’origine des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessVersionInfoFileDescription` | `string` | Description des informations de version du processus (fichier image) responsable de l’événement |
| `InitiatingProcessId` | `int` | ID de processus (PID) du processus qui a initié l’événement |
| `InitiatingProcessCommandLine` | `string` | Ligne de commande utilisée pour exécuter le processus qui a lancé l’événement |
| `InitiatingProcessCreationTime` | `datetime` | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessIntegrityLevel` | `string` | Niveau d’intégrité du processus qui a initié l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | `string` | Type de jeton indiquant la présence ou l’absence d’élévation de privilèges Access Control utilisateur (UAC) appliquée au processus qui a initié l’événement |
| `InitiatingProcessParentId` | `int` | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | `string` | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | `datetime` | Date et heure de démarrage du parent du processus responsable de l’événement |
| `RequestProtocol` | `string` | Protocole réseau, le cas échéant, utilisé pour lancer l’activité : Inconnu, Local, SMB ou NFS |
| `RequestSourceIP` | `string` | Adresse IPv4 ou IPv6 de l’appareil distant qui a lancé l’activité |
| `RequestSourcePort` | `string` | Port source sur l’appareil distant à l’origine de l’activité |
| `RequestAccountName` | `string` | Nom d’utilisateur du compte utilisé pour lancer à distance l’activité |
| `RequestAccountDomain` | `string` | Domaine du compte utilisé pour lancer à distance l’activité |
| `RequestAccountSid` | `string` | Identificateur de sécurité (SID) du compte utilisé pour lancer à distance l’activité |
| `ShareName` | `string` | Nom du dossier partagé contenant le fichier |
| `InitiatingProcessFileSize` | `long` | Taille du fichier qui a exécuté le processus responsable de l’événement |
| `SensitivityLabel` | `string` | Étiquette appliquée à un e-mail, un fichier ou tout autre contenu pour la classer pour la protection des informations |
| `SensitivitySubLabel` | `string` | Sous-étiquette appliquée à un e-mail, un fichier ou tout autre contenu pour la classer pour la protection des informations ; les sous-étiquettes de sensibilité sont regroupées sous des étiquettes de confidentialité, mais sont traitées indépendamment |
| `IsAzureInfoProtectionApplied` | `boolean` | Indique si le fichier est chiffré par Azure Information Protection |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `AppGuardContainerId` | `string` | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’entité ou l’événement |
>[!NOTE]
> Les informations de hachage de fichier sont toujours affichées lorsqu’elles sont disponibles. Toutefois, il existe plusieurs raisons possibles pour lesquelles un SHA1, SHA256 ou MD5 ne peut pas être calculé. Par exemple, le fichier peut se trouver dans un stockage distant, verrouillé par un autre processus, compressé ou marqué comme virtuel. Dans ces scénarios, les informations de hachage de fichier apparaissent vides.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
