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
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 2116d8f6f1006f5acf9d468006fa07a04e13087b
ms.sourcegitcommit: 11218af1d792af297b4280ca5975d139d2bbe350
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "45046027"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

**S’applique à :**
- Protection Microsoft contre les menaces

Le `IdentityLogonEvents` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les activités d’authentification effectuées via votre environnement Active Directory local capturées par Azure ATP et les activités d’authentification liées à Microsoft Online Services capturées par Microsoft Cloud App Security. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `ActionType` | chaîne | Type d’activité qui a déclenché l’événement |
| `LogonType` | chaîne | Type de session de connexion, notamment :<br><br> - **Interactif** : l’utilisateur interagit physiquement avec l’ordinateur à l’aide du clavier et de l’écran locaux<br><br> - **Ouvertures de session interactives (RDP)** : l’utilisateur interagit avec l’ordinateur à distance à l’aide du Bureau à distance, des services Terminal Server, de l’assistance à distance ou d’autres clients RDP<br><br> - Session **réseau** initiée lorsque l’accès à l’ordinateur est effectué à l’aide de PsExec ou lorsque des ressources partagées sur l’ordinateur, telles que des imprimantes et des dossiers partagés, sont accessibles<br><br> - Session de **traitement par lots** initiée par les tâches planifiées<br><br> - **Service** -session initialisée par les services au démarrage |
| `Application` | chaîne | Application qui a effectué l’action enregistrée |
| `Protocol` | chaîne | Protocole utilisé pendant la communication |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountDomain` | chaîne | Domaine du compte |
| `AccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte |
| `AccountSid` | chaîne | Identificateur de sécurité (SID) du compte |
| `AccountObjectId` | chaîne | Identificateur unique du compte dans Azure AD |
| `AccountDisplayName` | chaîne | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `DeviceName` | chaîne | Nom de domaine complet (FQDN) de la machine |
| `DeviceType` | chaîne | Type de périphérique |
| `OSPlatform` | string | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7. |
| `IPAddress` | string | Adresse IP affectée au point de terminaison et utilisée pendant les communications réseau associées |
| `Location` | chaîne | Ville, pays ou autre emplacement géographique associé à l’événement |
| `Isp` | chaîne | Fournisseur de services Internet associé à l’adresse IP du point de terminaison |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
