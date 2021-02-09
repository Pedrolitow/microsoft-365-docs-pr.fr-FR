---
title: Table IdentityLogonEvents dans le schéma de recherche avancé
description: En savoir plus sur les événements d’authentification enregistrés par Active Directory dans la table IdentityLogonEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, IdentityLogonEvents, Azure AD, Active Directory, Azure ATP, identities
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 87ac6194374e8e042cf9d00271b17dd8bb785d64
ms.sourcegitcommit: 005028af7c5a6b2e95f17a0037958131484d9e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "50145348"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les activités d’authentification réalisées via votre annuaire Active Directory local capturé par Microsoft Defender pour les activités d’identité et d’authentification liées aux services en ligne Microsoft capturés par `IdentityLogonEvents` Microsoft Cloud App Security. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité. [](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center)

>[!NOTE]
>Ce tableau couvre les activités d’authentification Azure Active Directory (AD) suivis par Cloud App Security, en particulier les activités de authentification et de authentification interactives à l’aide d’ActiveSync et d’autres protocoles hérités. Les connexions non interactives qui ne sont pas disponibles dans cette table peuvent être vues dans le journal d’audit Azure AD. [En savoir plus sur la connexion de Cloud App Security à Microsoft 365](https://docs.microsoft.com/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, voir](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) la référence du schéma dans le portail |
| `LogonType` | string | Type de session d’ouverture de session, en particulier :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Connexions RDP (Remote Interactive)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services Terminal Services, de l’Assistance à distance ou d’autres clients RDP<br><br> - **Réseau** : session initiée lorsque l’ordinateur est accessible à l’aide de PsExec ou lorsque les ressources partagées sur l’ordinateur, telles que les imprimantes et les dossiers partagés, sont accessibles<br><br> - **Batch** : session initiée par des tâches programmées<br><br> - **Service** : session initiée par les services au démarrage |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `Protocol` | string | Protocole réseau utilisé |
| `FailureReason` | string | Informations expliquant pourquoi l’action enregistrée a échoué |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | string | Nom de domaine complet (FQDN) de l’appareil |
| `DeviceType` | string | Type d’appareil |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées |
| `Port` | string | Port TCP utilisé pendant la communication |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traitée l’action enregistrée |
| `DestinationPort` | string | Port de destination des communications réseau associées |
| `TargetDeviceName` | string | Nom de domaine complet (FQDN) de l’appareil à qui l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | string | Nom complet du compte à qui l’action enregistrée a été appliquée |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | string | Fournisseur de services Internet (ISP) associé à l’adresse IP du point de terminaison |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
