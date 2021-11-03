---
title: Table IdentityInfo dans le schéma de recherche avancé
description: En savoir plus sur les informations de compte d’utilisateur dans la table IdentityInfo du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AccountInfo, IdentityInfo, account
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 3b961990d7826a7e1d58586fcc5bf2e016fa5d37
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60704300"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les comptes d’utilisateurs obtenus à partir de différents services, notamment `IdentityInfo` Azure Active Directory. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!NOTE]
>Cette table a été renommée à partir `AccountInfo` de . Pendant les changements de nom, toutes les requêtes enregistrées dans le portail sont automatiquement mises à jour. Vérifiez les requêtes que vous avez enregistrées ailleurs.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountUpn` | chaîne | Nom d’utilisateur principal (UPN) du compte |
| `OnPremSid` | chaîne | Identificateur de sécurité local (SID) du compte |
| `CloudSid` | chaîne | Identificateur de sécurité cloud du compte |
| `GivenName` | chaîne | Prénom ou nom de l’utilisateur du compte |
| `Surname` | chaîne | Nom de famille, nom de famille ou nom de l’utilisateur du compte |
| `AccountDisplayName` | chaîne | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `Department` | chaîne | Nom du service à qui appartient l’utilisateur du compte |
| `JobTitle` | chaîne | Fonction de l’utilisateur du compte |
| `AccountName` | chaîne | Nom d’utilisateur du compte |
| `AccountDomain` | chaîne | Domaine du compte |
| `EmailAddress` | chaîne | Adresse SMTP du compte |
| `SipProxyAddress` | chaîne | Adresse SIP (Session Initiation Protocol) VOIP (Voice over IP) du compte |
| `City` | chaîne | Ville où se trouve l’utilisateur du compte |
| `Country` | chaîne | Pays/région où se trouve l’utilisateur du compte |
| `IsAccountEnabled` | valeur booléenne | Indique si le compte est activé ou non |

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
