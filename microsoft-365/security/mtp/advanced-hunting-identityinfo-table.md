---
title: Table IdentityInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de compte d’utilisateur dans la table IdentityInfo du schéma de chasse avancé
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, AccountInfo, IdentityInfo, compte
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
ms.openlocfilehash: 12f8d0995d00daffe8a1ca1c2c8d9dfe25a11581
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209774"
---
# <a name="identityinfo"></a>IdentityInfo

**S’applique à :**
- Protection Microsoft contre les menaces

Le `IdentityInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les comptes d’utilisateur obtenus à partir de différents services, notamment Azure Active Directory. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!NOTE]
>Cette table a été renommée de `AccountInfo` . Lors du changement de nom, toutes les requêtes enregistrées dans le portail sont automatiquement mises à jour. Vérifier les requêtes que vous avez enregistrées ailleurs.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `AccountObjectId` | string | Identificateur unique du compte dans Azure AD |
| `AccountUpn` | string | Nom d’utilisateur principal (UPN) du compte |
| `OnPremSid` | string | Identificateur de sécurité (SID) sur site du compte |
| `CloudSid` | string | Identificateur de sécurité du Cloud du compte |
| `GivenName` | string | Prénom ou prénom de l’utilisateur du compte |
| `Surname` | string | Nom, nom de famille ou nom de famille de l’utilisateur du compte |
| `AccountDisplayName` | string | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. Il s’agit généralement d’une combinaison d’un nom donné, d’une initiation au milieu et d’un nom de famille ou nom. |
| `Department` | string | Nom du service auquel appartient l’utilisateur du compte |
| `JobTitle` | string | Fonction de l’utilisateur du compte |
| `AccountName` | string | Nom d’utilisateur du compte |
| `AccountDomain` | string | Domaine du compte |
| `EmailAddress` | string | Adresse SMTP du compte |
| `SipProxyAddress` | string | Adresse SIP (Session Initiation Protocol) voix sur IP (VOIP) du compte |
| `City` | string | Ville où se trouve l’utilisateur du compte |
| `Country` | string | Pays/région où se trouve l’utilisateur du compte |
| `IsAccountEnabled` | booléen | Indique si le compte est activé ou non. |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
