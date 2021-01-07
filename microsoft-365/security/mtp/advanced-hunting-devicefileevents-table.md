---
title: Table DeviceFileEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements liés aux fichiers dans le tableau DeviceFileEvents du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, filecreationevents, DeviceFileEvents, fichiers, chemin, hachage, SHA1, SHA256, MD5
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
ms.openlocfilehash: 9b48321693f883e40a100e29e5e1ec3c5203caa2
ms.sourcegitcommit: ddfb4f3e34deb733e8625e845e4dfd1fcc066ceb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49771858"
---
# <a name="devicefileevents"></a>DeviceFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le `DeviceFileEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur la création de fichiers, la modification et d’autres événements de système de fichiers. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

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
| `FileOriginUrl` | chaîne | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginReferrerUrl` | chaîne | URL de la page Web liée au fichier téléchargé |
| `FileOriginIP` | chaîne | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `InitiatingProcessAccountDomain` | chaîne | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | chaîne | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | chaîne | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessMD5` | chaîne | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA1` | chaîne | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | chaîne | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | chaîne | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | chaîne | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessIntegrityLevel` | chaîne | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influent sur les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | chaîne | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus ayant initié l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | chaîne | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `RequestProtocol` | chaîne | Protocole réseau, le cas échéant, utilisé pour lancer l’activité : inconnu, local, SMB ou NFS |
| `ShareName` | chaîne | Nom du dossier partagé contenant le fichier |
| `RequestSourceIP` | chaîne | Adresse IPv4 ou IPv6 du périphérique distant qui a initié l’activité |
| `RequestSourcePort` | chaîne | Port source sur l’appareil distant qui a initié l’activité |
| `RequestAccountName` | chaîne | Nom d’utilisateur du compte utilisé pour lancer à distance l’activité |
| `RequestAccountDomain` | chaîne | Domaine du compte utilisé pour lancer à distance l’activité |
| `RequestAccountSid` | chaîne | Identificateur de sécurité (SID) du compte utilisé pour lancer à distance l’activité. |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | chaîne | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |
| `SensitivityLabel` | chaîne | Étiquette appliquée à un message électronique, à un fichier ou à un autre contenu afin de le classer pour la protection des informations |
| `SensitivitySubLabel` | chaîne | Sous-étiquette appliquée à un message électronique, à un fichier ou à un autre contenu pour le classer pour la protection des informations ; les sous-étiquettes de sensibilité sont regroupées sous les étiquettes de confidentialité mais traitées indépendamment |
| `IsAzureInfoProtectionApplied` | valeur booléenne | Indique si le fichier est chiffré par Azure information protection |

>[!NOTE]
> Les informations de hachage de fichier s’affichent toujours lorsqu’elles sont disponibles. Toutefois, il existe plusieurs raisons possibles pour lesquelles un SHA1, un SHA256 ou un MD5 ne peuvent pas être calculés. Par exemple, il se peut que le fichier se trouve dans le stockage distant, verrouillé par un autre processus, compressé ou marqué comme virtuel. Dans ces scénarios, les informations de hachage de fichier sont vides.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
