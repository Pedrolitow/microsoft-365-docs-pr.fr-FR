---
title: Table IdentityLogonEvents dans le schéma de chasse avancé
description: En savoir plus sur les événements d’authentification enregistrés par Active Directory dans la table IdentityLogonEvents du schéma de chasse avancé
keywords: recherche avancée, recherche de menace, recherche de menace informatique, protection de Microsoft contre les menaces, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, IdentityLogonEvents, Azure AD, Active Directory, Azure ATP, identités
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
- m365-initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 2ecf6de79f5eab4aca7bc928ea64b780a257b908
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48412729"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

Le `IdentityLogonEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les activités d’authentification effectuées via votre environnement Active Directory local capturées par Azure ATP et les activités d’authentification liées à Microsoft Online Services capturées par Microsoft Cloud App Security. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements ( `ActionType` valeurs) pris en charge par un tableau, utilisez la [référence de schéma intégrée](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) disponible dans le centre de sécurité.

>[!NOTE]
>Ce tableau couvre les activités d’ouverture de session Azure Active Directory (AD) suivies par la sécurité des applications Cloud, en particulier les ouvertures de session interactives et les activités d’authentification à l’aide d’ActiveSync et d’autres protocoles hérités. Les ouvertures de sessions non interactives qui ne sont pas disponibles dans ce tableau peuvent être affichées dans le journal d’audit Azure AD. [En savoir plus sur la connexion de la sécurité des applications Cloud à Microsoft 365](https://docs.microsoft.com/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | string | Type d’activité qui a déclenché l’événement. Pour plus d’informations, consultez la [référence de schéma dans le portail](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) . |
| `LogonType` | string | Type de session de connexion, notamment :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Ouvertures de session interactives (RDP)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services Terminal Server, de l’assistance à distance ou d’autres clients RDP<br><br> - Session **réseau** initiée lorsque l’accès à l’ordinateur est effectué à l’aide de PsExec ou lorsque des ressources partagées sur l’ordinateur, telles que des imprimantes et des dossiers partagés, sont accessibles<br><br> - Session de **traitement par lots** initiée par les tâches planifiées<br><br> - **Service** -session initialisée par les services au démarrage |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `Protocol` | string | Protocole réseau utilisé |
| `FailureReason` | string | Informations expliquant pourquoi l’action enregistrée a échoué |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | string | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `DeviceName` | string | Nom de domaine complet (FQDN) du périphérique |
| `DeviceType` | string | Type de périphérique |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP affectée au point de terminaison et utilisée pendant les communications réseau associées |
| `DestinationDeviceName` | string | Nom de l’appareil exécutant l’application serveur qui a traité l’action enregistrée. |
| `DestinationIPAddress` | string | Adresse IP de l’appareil exécutant l’application serveur qui a traité l’action enregistrée |
| `TargetDeviceName` | string | Nom de domaine complet (FQDN) de l’appareil sur lequel l’action enregistrée a été appliquée. |
| `TargetAccountDisplayName` | string | Nom d’affichage du compte auquel l’action enregistrée a été appliquée |
| `Location` | string | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | string | Fournisseur de services Internet associé à l’adresse IP du point de terminaison |
| `ReportId` | long | Identificateur unique de l’événement |
| `AdditionalFields` | string | Informations supplémentaires sur l’entité ou l’événement |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
