---
title: Table DeviceImageLoadEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements de chargement de DLL dans la table DeviceImageLoadEvents du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche dans les menaces de la cybercriminalité, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, imageloadevents, DeviceImageLoadEvents, chargement de DLL, bibliothèque, image de fichier
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
ms.openlocfilehash: 37c8d1a6c0ac8afd8e8cf856f573769a6245cb5a
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846031"
---
# <a name="deviceimageloadevents"></a>DeviceImageLoadEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Le `DeviceImageLoadEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les événements de chargement de dll. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

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
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a exécuté le processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | string | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité aux processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influent sur les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence de l’élévation de privilège de contrôle d’accès utilisateur appliqué au processus ayant initié l’événement |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessSHA256` | string | SHA-256 du processus (fichier image) à l’origine de l’événement. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | int | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de démarrage du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | int | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de démarrage du parent du processus responsable de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et timestamp |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par application Guard pour isoler l’activité du navigateur |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
