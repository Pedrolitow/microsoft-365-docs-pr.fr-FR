---
title: Table IdentityInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de compte d’utilisateur dans la table IdentityInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, AccountInfo, IdentityInfo, compte
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
ms.openlocfilehash: 90a108c0c4d85fa3335191998815d0441f723832
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68640717"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La `IdentityInfo` table du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les comptes d’utilisateur obtenus à partir de différents services, notamment Azure Active Directory. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!NOTE]
>Cette table a été renommée de `AccountInfo`. Pendant les renommations, toutes les requêtes enregistrées dans le portail sont automatiquement mises à jour. Vérifiez les requêtes que vous avez enregistrées ailleurs.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `AccountObjectId` | `string` | Identificateur unique du compte dans Azure AD |
| `AccountUpn` | `string` | Nom d’utilisateur principal (UPN) du compte |
| `OnPremSid` | `string` | Identificateur de sécurité local (SID) du compte |
| `CloudSid` | `string` | Identificateur de sécurité cloud du compte |
| `GivenName` | `string` | Nom donné ou prénom de l’utilisateur du compte |
| `Surname` | `string` | Nom de famille, nom de famille ou nom de l’utilisateur du compte |
| `AccountDisplayName` | `string` | Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiation intermédiaire et d’un nom ou d’un nom de famille. |
| `Department` | `string` | Nom du service auquel appartient l’utilisateur du compte |
| `JobTitle` | `string` | Titre du travail de l’utilisateur du compte |
| `AccountName` | `string` | Nom d’utilisateur du compte |
| `AccountDomain` | `string` | Domaine du compte |
| `EmailAddress` | `string` | Adresse SMTP du compte |
| `SipProxyAddress` | `string` | Adresse SIP (Voice over IP) du compte |
| `City` | `string` | Ville où se trouve l’utilisateur du compte |
| `Country` | `string` | Pays/région où se trouve l’utilisateur du compte |
| `IsAccountEnabled` | `boolean` | Indique si le compte est activé ou non |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
