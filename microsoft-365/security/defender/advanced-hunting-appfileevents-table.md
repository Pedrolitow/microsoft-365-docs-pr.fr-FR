---
title: Table AppFileEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements liés aux fichiers associés aux applications et services cloud dans la table AppFileEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AppFileEvents, Cloud App Security, MCAS
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
ms.openlocfilehash: b8b3b34e1b8535772d19f8ddd9f52c5c0a89292b
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51499348"
---
# <a name="appfileevents"></a>AppFileEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les activités liées aux fichiers dans les applications et services cloud surveillés par `AppFileEvents` Microsoft Cloud App Security. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!WARNING]
>Cette table sera bientôt retirée. Depuis le 7 mars 2021, la table ne `AppFileEvents` journalisation plus les enregistrements. Les utilisateurs qui recherchent des activités liées aux fichiers dans les services cloud à la date et au-delà de cette date doivent utiliser la table [CloudAppEvents](advanced-hunting-cloudappevents-table.md) à la place. <br><br>Veillez à rechercher des requêtes et des règles de détection personnalisées qui utilisent toujours la table et modifiez-les `AppFileEvents` pour utiliser le `CloudAppEvents` tableau. Pour plus d’informations sur la conversion des requêtes affectées, voir La recherche dans les activités d’application cloud avec la recherche avancée [Microsoft 365 Defender.](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857)


Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FolderPath` | string | Dossier contenant le fichier à lequel l’action enregistrée a été appliquée |
| `PreviousFileName` | string | Nom d’origine du fichier qui a été renommé à la suite de l’action |
| `PreviousFolderPath` | string | Dossier d’origine contenant le fichier avant l’application de l’action enregistrée |
| `Protocol` | string | Protocole réseau utilisé |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `DeviceType` | string | Type d’appareil | 
| `OSPlatform` | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées |
| `Port` | string | Port TCP utilisé pendant la communication  |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationPort` | string | Port de destination des communications réseau associées |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | string | Fournisseur de services Internet (ISP) associé à l’adresse IP du point de terminaison |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité.


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
