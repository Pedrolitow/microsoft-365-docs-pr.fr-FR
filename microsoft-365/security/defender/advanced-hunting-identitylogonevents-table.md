---
title: IdentityLogonEvents table dans le schéma de chasse avancé
description: Découvrez les événements d’authentification enregistrés par Active Directory dans le tableau IdentityLogonEvents du schéma de chasse avancé
keywords: chasse avancée, chasse aux menaces, chasse aux cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schémas, kusto, table, colonne, type de données, description, IdentityLogonEvents, Azure AD, Active Directory, Microsoft Defender for Identity, identités
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
ms.openlocfilehash: 3cd0c0f371c73a515704791e829be7266d400580
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572752"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le `IdentityLogonEvents` tableau du schéma de chasse [avancé](advanced-hunting-overview.md) contient des informations sur les activités d’authentification effectuées par l’intermédiaire de votre répertoire actif sur place capturé par Microsoft Defender pour les activités d’identité et d’authentification liées aux services en ligne Microsoft capturés par Microsoft Cloud App Security. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements `ActionType` (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans le centre de sécurité.

>[!NOTE]
>Ce tableau couvre les activités de logon Azure Active Directory (Azure AD) suivies par des Sécurité des applications cloud, en particulier des inscriptions interactives et des activités d’authentification à l’aide d’ActiveSync et d’autres protocoles hérités. Les journaux non interactifs qui ne sont pas disponibles dans ce tableau peuvent être consultés dans le journal d’audit Azure AD. [En savoir plus sur la connexion Sécurité des applications cloud à Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Voir la [référence du schéma du portail pour plus de](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) détails |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `LogonType` | string | Type de session logon, en particulier:<br><br> - **Interactif** - L’utilisateur interagit physiquement avec la machine à l’aide du clavier et de l’écran locaux<br><br> - **Journaux interactifs à distance (RDP)** - L’utilisateur interagit avec la machine à distance à l’aide de remote desktop, terminal services, assistance à distance, ou d’autres clients RDP<br><br> - **Réseau** - Session initiée lorsque la machine est accessible à l’aide de PsExec ou lorsque des ressources partagées sur la machine, telles que des imprimantes et des dossiers partagés, sont consultées<br><br> - **Lot** - Session initiée par les tâches planifiées<br><br> - **Service** - Session initiée par les services au début |
| `Protocol` | string | Protocole réseau utilisé |
| `FailureReason` | string | Informations expliquant pourquoi l’action enregistrée a échoué |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom principal de l’utilisateur (UPN) du compte |
| `AccountSid` | string | Identifiant de sécurité (SID) du compte |
| `AccountObjectId` | string | Identifiant unique pour le compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Généralement une combinaison d’un prénom ou d’un prénom, d’une initiation moyenne et d’un nom de famille ou d’un nom de famille. |
| `DeviceName` | string | Nom de domaine entièrement qualifié (FQDN) de l’appareil |
| `DeviceType` | string | Type d’appareil |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP attribuée au point de terminaison et utilisée lors de communications réseau connexes |
| `Port` | string | Port TCP utilisé lors de la communication |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `DestinationPort` | string | Port de destination des communications réseau connexes |
| `TargetDeviceName` | string | Nom de domaine entièrement qualifié (FQDN) de l’appareil à qui l’action enregistrée a été appliquée |
| `TargetAccountDisplayName` | string | Afficher le nom du compte à qui l’action enregistrée a été appliquée |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | string | Fournisseur de services Internet (FAI) associé à l’adresse IP du point de terminaison |
| `ReportId` | long | Identificateur unique pour l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)