---
title: Table CloudAppEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements des applications et services cloud dans la table CloudAppEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, CloudAppEvents, Defender pour les applications cloud
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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 8892a672cb9fc77b4cf606f32581c1928decc45f
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67470140"
---
# <a name="cloudappevents"></a>CloudAppEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Le `CloudAppEvents` tableau du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les activités dans différentes applications et services cloud couverts par Microsoft Defender for Cloud Apps. Pour obtenir la liste complète, accédez à [Applications et services couverts](#apps-and-services-covered). Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

> [!IMPORTANT]
> Ce tableau inclut des informations qui auparavant sont disponibles dans la `AppFileEvents` table. À compter du 7 mars 2021, les utilisateurs qui chassent par le biais d’activités liées aux fichiers dans les services cloud à cette date et au-delà doivent utiliser la table à la `CloudAppEvents` place. <br><br>Veillez à rechercher des requêtes et des règles de détection personnalisées qui utilisent toujours la `AppFileEvents` table et modifiez-les pour utiliser la `CloudAppEvents` table. Vous trouverez plus d’instructions sur la conversion des requêtes affectées dans [Hunt dans les activités d’application cloud avec Microsoft 365 Defender chasse avancée](https://techcommunity.microsoft.com/t5/microsoft-365-defender/hunt-across-cloud-app-activities-with-microsoft-365-defender/ba-p/1893857).

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `ApplicationId` | `string` | Identificateur unique de l’application |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure Active Directory |
| `AccountId` | `string` | Identificateur du compte trouvé par Microsoft Defender for Cloud Apps. Il peut s’agir de l’ID Azure Active Directory, du nom d’utilisateur principal ou d’autres identificateurs. |
| `AccountDisplayName` | `string` | Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `IsAdminOperation` | `string` | Indique si l’activité a été effectuée par un administrateur |
| `DeviceType` | `string` | Type d’appareil basé sur l’objectif et les fonctionnalités, tels que « Périphérique réseau », « Station de travail », « Serveur », « Mobile », « Console de jeu » ou « Imprimante » |
| `OSPlatform` | `string` | Plateforme du système d’exploitation en cours d’exécution sur l’appareil. Cette colonne indique des systèmes d’exploitation spécifiques, y compris des variations au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `IPAddress` | `string` | Adresse IP affectée au point de terminaison et utilisée lors des communications réseau associées |
| `IsAnonymousProxy` | `string` | Indique si l’adresse IP appartient à un proxy anonyme connu |
| `CountryCode` | `string` | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisée |
| `City` | `string` | Ville où l’adresse IP du client est géolocalisée |
| `Isp` | `string` | Fournisseur de services Internet (ISP) associé à l’adresse IP |
| `UserAgent` | `string` | Informations de l’agent utilisateur à partir du navigateur web ou d’une autre application cliente |
| `ActivityType` | `string` | Type d’activité qui a déclenché l’événement |
| `ActivityObjects` | `dynamic` | Liste d’objets, tels que des fichiers ou des dossiers, qui ont été impliqués dans l’activité enregistrée |
| `ObjectName` | `string` | Nom de l’objet auquel l’action enregistrée a été appliquée |
| `ObjectType` | `string` | Type d’objet, tel qu’un fichier ou un dossier, auquel l’action enregistrée a été appliquée |
| `ObjectId` | `string` | Identificateur unique de l’objet auquel l’action enregistrée a été appliquée |
| `ReportId` | `string` | Identificateur unique de l’événement |
| `RawEventData` | `string` | Informations sur les événements bruts de l’application ou du service source au format JSON |
| `AdditionalFields` | `dynamic` | Informations supplémentaires sur l’entité ou l’événement |
| `AccountType` | `string` | Type de compte d’utilisateur, indiquant son rôle général et ses niveaux d’accès, tels que Regular, System, Administration, DcAdmin, System, Application |
| `IsExternalUser` | `boolean` | Indique si un utilisateur à l’intérieur du réseau n’appartient pas au domaine de l’organisation |
| `IsImpersonated` | `boolean` | Indique si l’activité a été effectuée par un utilisateur pour un autre utilisateur (emprunt d’identité) |
| `IPTags` | `dynamic` | Informations définies par le client appliquées à des adresses IP et plages d’adresses IP spécifiques |
| `IPCategory` | `string` | Informations supplémentaires sur l’adresse IP |
| `UserAgentTags` | `dynamic` | Informations supplémentaires fournies par Microsoft Defender for Cloud Apps dans une balise dans le champ de l’agent utilisateur. Peut avoir l’une des valeurs suivantes : client natif, navigateur obsolète, système d’exploitation obsolète, Robot |

## <a name="apps-and-services-covered"></a>Applications et services couverts

- Dropbox
- Dynamics 365
- Exchange Online
- Microsoft Teams
- OneDrive Entreprise
- Power Automate
- Power BI
- SharePoint Online
- Skype Entreprise
- Office 365
- Yammer

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
