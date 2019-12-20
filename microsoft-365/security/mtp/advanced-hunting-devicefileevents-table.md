---
title: Table DeviceFileEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements liés aux fichiers dans le tableau DeviceFileEvents du schéma de chasse avancé
keywords: recherche avancée, recherche de menace, recherche de menace informatique, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, filecreationevents, DeviceFileEvents, fichiers, chemin, hachage, SHA1, SHA256, MD5
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
ms.openlocfilehash: ed0ccbaaf6b06f29eb241d8ddcc38361d1e802bb
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40809288"
---
# <a name="devicefileevents"></a>DeviceFileEvents

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Le `DeviceFileEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur la création de fichiers, la modification et d’autres événements de système de fichiers. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | chaîne | Identificateur unique de la machine dans le service |
| `DeviceName` | chaîne | Nom de domaine complet (FQDN) de la machine |
| `ActionType` | chaîne | Type d’activité qui a déclenché l’événement |
| `FileName` | chaîne | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | chaîne | Dossier contenant le fichier auquel l’action enregistrée a été appliquée |
| `SHA1` | string | SHA-1 du fichier auquel l’action enregistrée a été appliquée |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli : utilisez la colonne SHA1 quand elle est disponible. |
| `MD5` | chaîne | Hachage MD5 du fichier auquel l’action enregistrée a été appliquée |
| `FileOriginUrl` | chaîne | URL à partir de laquelle le fichier a été téléchargé |
| `FileOriginReferrerUrl` | chaîne | URL de la page Web liée au fichier téléchargé |
| `FileOriginIP` | chaîne | Adresse IP à partir de laquelle le fichier a été téléchargé |
| `InitiatingProcessAccountDomain` | chaîne | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | chaîne | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | chaîne | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessMD5` | chaîne | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA1` | chaîne | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFolderPath` | chaîne | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | chaîne | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | chaîne | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessIntegrityLevel` | chaîne | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influent sur les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | chaîne | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus ayant initié l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | chaîne | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | chaîne | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |
| `SensitivityLabel` | chaîne | Étiquette appliquée à un message électronique, à un fichier ou à un autre contenu afin de le classer pour la protection des informations |
| `SensitivitySubLabel` | chaîne | Sous-étiquette appliquée à un message électronique, à un fichier ou à un autre contenu pour le classer pour la protection des informations ; les sous-étiquettes de sensibilité sont regroupées sous les étiquettes de confidentialité mais traitées indépendamment |
| `IsAzureInfoProtectionApplied` | booléen | Indique si le fichier est chiffré par Azure information protection |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
