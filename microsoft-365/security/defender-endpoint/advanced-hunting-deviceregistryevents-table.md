---
title: Table DeviceRegistryEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements de Registre que vous pouvez interroger à partir de la table DeviceRegistryEvents du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, search, query, telemetry, schema reference, kusto, table, column, data type, deviceregistryevents, registry, key, subkey, value, RegistryEvents
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
ms.openlocfilehash: 31fe2bb882bc59eb516773c0c319b1f25f56a95e
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51498766"
---
# <a name="deviceregistryevents"></a>DeviceRegistryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

Le tableau du schéma de recherche avancée contient des informations sur la création et la modification des `DeviceRegistryEvents` entrées de [](advanced-hunting-overview.md) Registre. Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tableaux du schéma de chasse avancé, voir [la référence du schéma de chasse avancé.](advanced-hunting-schema-reference.md)

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `DeviceId` | string | Identificateur unique de l’appareil dans le service |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `RegistryKey` | string | Clé de Registre à l’application de l’action enregistrée |
| `RegistryValueType` | string | Type de données, tel que binaire ou chaîne, de la valeur de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueName` | string | Nom de la valeur de Registre à qui l’action enregistrée a été appliquée |
| `RegistryValueData` | string | Données de la valeur de Registre à l’application de l’action enregistrée |
| `PreviousRegistryValueName` | string | Nom d’origine de la valeur de Registre avant sa modification |
| `PreviousRegistryValueData` | string | Données d’origine de la valeur de Registre avant sa modification |
| `InitiatingProcessAccountDomain` | string | Domaine du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountName` | string | Nom d’utilisateur du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessAccountSid` | string | Identificateur de sécurité (SID) du compte qui a dirigé le processus responsable de l’événement |
| `InitiatingProcessSHA1` | string | SHA-1 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessMD5` | string | Hachage MD5 du processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessFileName` | string | Nom du processus à l’origine de l’événement |
| `InitiatingProcessId` | entier | ID de processus (PID) du processus à l’origine de l’événement |
| `InitiatingProcessCommandLine` | string | Ligne de commande utilisée pour exécuter le processus à l’origine de l’événement |
| `InitiatingProcessCreationTime` | DateHeure | Date et heure de début du processus à l’origine de l’événement |
| `InitiatingProcessFolderPath` | string | Dossier contenant le processus (fichier image) à l’origine de l’événement |
| `InitiatingProcessParentId` | entier | ID de processus (PID) du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentFileName` | string | Nom du processus parent qui a généré le processus responsable de l’événement |
| `InitiatingProcessParentCreationTime` | DateHeure | Date et heure de début du parent du processus responsable de l’événement |
| `InitiatingProcessIntegrityLevel` | string | Niveau d’intégrité du processus à l’origine de l’événement. Windows affecte des niveaux d’intégrité à des processus en fonction de certaines caractéristiques, par exemple s’ils ont été lancés à partir d’un téléchargement Internet. Ces niveaux d’intégrité influencent les autorisations sur les ressources |
| `InitiatingProcessTokenElevation` | string | Type de jeton indiquant la présence ou l’absence d’élévation de privilège du contrôle d’accès utilisateur (UAC) appliquée au processus à l’origine de l’événement |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les `DeviceName` colonnes et les `Timestamp` événements |
| `AppGuardContainerId` | string | Identificateur du conteneur virtualisé utilisé par Application Guard pour isoler l’activité du navigateur |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Comprendre le schéma](advanced-hunting-schema-reference.md)
