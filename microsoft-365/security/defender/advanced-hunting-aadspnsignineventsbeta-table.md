---
title: Table AADSpnSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur les informations associées au principal Azure Active Directory service et à la table des événements de signature d’identité gérée du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AlertInfo, alert, entities, evidence, file, IP address, device, machine, user, account, identity, AAD
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
ms.openlocfilehash: b1cb2b9f7a9f3feddc86fdd5eda5323f5459b427412e334044433f589a85f594
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53833386"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

>[!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de chercher des événements de signature d’identité gérée et de principal de `AADSpnSignInEventsBeta` service Azure Active Directory (AAD). Nous finirons par déplacer toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.



Le tableau dans le schéma de recherche avancée contient des informations sur Azure Active Directory principal de service et les `AADSpnSignInEventsBeta` sign-ins d’identité gérée. Vous pouvez en savoir plus sur les différents types de Azure Active Directory dans les rapports d’activité de Azure Active Directory de la signature [- aperçu.](/azure/active-directory/reports-monitoring/concept-all-sign-ins)

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).





| Nom de colonne | Type de données | Description |
|-----|-----|-----|
| `Timestamp` | DateHeure | Date et heure de génération de l’enregistrement |
| `Application` | string | Application qui a effectué l’action enregistrée |
| `ApplicationId` | string | Identificateur unique de l’application |
| `IsManagedIdentity`    | valeur booléenne       | Indique si la connectez-vous a été initiée par une identité gérée |
| `ErrorCode`    | int | Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> . |
| `CorrelationId`        | string        | Identificateur unique de l’événement de signature |
| `ServicePrincipalName` | string        | Nom du principal de service à l’origine de la signature  |
| `ServicePrincipalId`   | string        | Identificateur unique du principal de service à l’origine de la signature  |
| `ResourceDisplayName`  | string        | Nom d’affichage de la ressource accessible  |
| `ResourceId`           | string        | Identificateur unique de la ressource à accès  |
| `ResourceTenantId`     | string        | Identificateur unique du client de la ressource à accès |
| `IPAddress`            | string        | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées  |
| `Country`          | string        | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé |
| `State`                | string        | État où la connectez-vous s’est produite, si disponible |
| `City`                 | string        | Ville où se trouve l’utilisateur du compte  |
| `Latitude`             | string        | Coordonnées nord à sud de l’emplacement de la signature |
| `Longitude`            | string        | Coordonnées est à ouest de l’emplacement de la signature |
| `RequestId`            | string        | Identificateur unique de la demande |
|`ReportId` | string | Identificateur unique de l’événement |

 

## <a name="related-articles"></a>Articles connexes

-   [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
-   [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
-   [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
-   [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
