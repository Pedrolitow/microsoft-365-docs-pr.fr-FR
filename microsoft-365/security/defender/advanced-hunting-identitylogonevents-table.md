---
title: Table IdentityLogonEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements d’authentification enregistrés par Active Directory dans la table IdentityLogonEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, IdentityLogonEvents, Azure AD, Active Directory, Microsoft Defender pour Identity, identités
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
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.openlocfilehash: 0d315ecfdb5895d3492f1af823dd06ce99025474
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68639684"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `IdentityLogonEvents` table du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les activités d’authentification effectuées via votre Active Directory local capturées par Microsoft Defender pour Identity et les activités d’authentification liées à Microsoft services en ligne capturées par Microsoft Defender for Cloud Apps. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

>[!NOTE]
>Ce tableau couvre les activités d’ouverture de session Azure Active Directory (Azure AD) suivies par Defender pour Cloud Apps, en particulier les connexions interactives et les activités d’authentification à l’aide d’ActiveSync et d’autres protocoles hérités. Les journaux d’activité non interactifs qui ne sont pas disponibles dans ce tableau peuvent être affichés dans le journal d’audit Azure AD. [En savoir plus sur la connexion de Defender pour Cloud Apps à Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement. Pour plus [d’informations, consultez la référence du schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) |
| `Application` | `string` | Application qui a effectué l’action enregistrée |
| `LogonType` | `string` | Type de session d’ouverture de session, en particulier :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Journaux d’activité interactifs à distance (RDP)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services terminal, de l’assistance à distance ou d’autres clients RDP<br><br> - **Réseau** : session lancée lorsque l’ordinateur est accessible à l’aide de PsExec ou lorsque des ressources partagées sur l’ordinateur, telles que des imprimantes et des dossiers partagés, sont accessibles<br><br> - **Batch** - Session initiée par des tâches planifiées<br><br> - **Service** - Session initiée par les services au démarrage |
| `Protocol` | `string` | Protocole réseau utilisé |
| `FailureReason` | `string` | Informations expliquant pourquoi l’action enregistrée a échoué |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | `string` | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | `string` | Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `DeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil |
| `DeviceType` | `string` | Type d’appareil |
| `OSPlatform` | `string` | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variations au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7. |
| `IPAddress` | `string` | Adresse IP affectée au point de terminaison et utilisée lors des communications réseau associées |
| `Port` | `string` | Port TCP utilisé pendant la communication |
| `DestinationDeviceName` | `string` | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationIPAddress` | `string` | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationPort` | `string` | Port de destination des communications réseau associées |
| `TargetDeviceName` | `string` | Nom de domaine complet (FQDN) de l’appareil auquel l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | `string` | Nom d’affichage du compte auquel l’action enregistrée a été appliquée |
| `Location` | `string` | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | `string` | Fournisseur de services Internet (ISP) associé à l’adresse IP du point de terminaison |
| `ReportId` | `long` | Identificateur unique de l’événement |
| `AdditionalFields` | `string` | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
