---
title: Table CloudAppEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements des applications et services cloud dans la table CloudAppEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, CloudAppEvents, Sécurité des applications cloud, MCAS
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: eff066610d87dd637a861906b8f6a4a4c73ae2ae
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60162397"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Le tableau du schéma de recherche avancée contient des informations sur les activités dans diverses applications et services cloud couverts par `CloudAppEvents` Microsoft Cloud App Security. [](advanced-hunting-overview.md) Pour obtenir la liste complète, voir [Applications et services couverts.](#apps-and-services-covered) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table. 

>[!IMPORTANT]
>Ce tableau inclut des informations qui étaient disponibles dans le `AppFileEvents` tableau. À compter du 7 mars 2021, les utilisateurs qui recherchent des activités liées aux fichiers dans les services cloud et au-delà de cette date doivent utiliser le `CloudAppEvents` tableau à la place. <br><br>Veillez à rechercher les requêtes et les règles de détection personnalisées qui utilisent toujours le tableau et à les `AppFileEvents` modifier pour utiliser le `CloudAppEvents` tableau. Pour plus d’informations sur la conversion des requêtes affectées, voir La recherche dans les activités d’application [cloud avec Microsoft 365 Defender de recherche avancée.](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857)


Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ApplicationId` | string | Identificateur unique de l’application |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure Active Directory |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `IsAdminOperation` | string | Indique si l’activité a été effectuée par un administrateur |
| `DeviceType` | string | Type d’appareil en fonction de l’objectif et des fonctionnalités, tels que « Périphérique réseau », « Station de travail », « Serveur », « Mobile », « Console de jeu » ou « Imprimante » | 
| `OSPlatform` | string | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cette colonne indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées |
| `IsAnonymousProxy` | string | Indique si l’adresse IP appartient à un proxy anonyme connu |
| `CountryCode` | string | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé |
| `City` | string | Ville où l’adresse IP du client est géolocalisé |
| `Isp` | string | Fournisseur de services Internet (ISP) associé à l’adresse IP |
| `UserAgent` | string | Informations sur l’agent utilisateur à partir du navigateur web ou d’une autre application cliente |
| `ActivityType` | string | Type d’activité qui a déclenché l’événement |
| `ActivityObjects` | string | Liste des objets, tels que des fichiers ou des dossiers, qui ont été impliqués dans l’activité enregistrée |
| `ObjectName` | string | Nom de l’objet à qui l’action enregistrée a été appliquée |
| `ObjectType` | string | Type d’objet, tel qu’un fichier ou un dossier, à qui l’action enregistrée a été appliquée |
| `ObjectId` | string | Identificateur unique de l’objet à qui l’action enregistrée a été appliquée |
| `ReportId` | string | Identificateur unique de l’événement |
| `RawEventData` | string | Informations d’événement brutes de l’application ou du service source au format JSON |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="apps-and-services-covered"></a>Applications et services couverts

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive Entreprise
- Power Automate
- Power BI
- SharePoint Online
- Skype Entreprise
- Office 365
- Yammer 

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
