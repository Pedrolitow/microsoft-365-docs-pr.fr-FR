---
title: Table AccountInfo dans le schéma de chasse avancé
description: En savoir plus sur les informations de compte d’utilisateur dans la table AccountInfo du schéma de chasse avancé
keywords: chasse avancée, recherche de menace, recherche dans les menaces informatiques, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, AlertInfo, alerte, entités, preuve, fichier, adresse IP, appareil, ordinateur, utilisateur, compte
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
ms.openlocfilehash: 9e4503ab297c7a584a548faa36ca6102c1b8dda6
ms.sourcegitcommit: 3b2fdf159d7dd962493a3838e3cf0cf429ee2bf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "42929527"
---
# <a name="accountinfo"></a>AccountInfo

**S’applique à :**
- Protection Microsoft contre les menaces

Le `AccountInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les comptes d’utilisateur obtenus à partir de différents services, notamment Azure Active Directory. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

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
