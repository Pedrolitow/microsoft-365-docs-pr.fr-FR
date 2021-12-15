---
title: Table AADSpnSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur les informations associées Azure Active Directory du principal de service et de la table des événements de la signature d’identité gérée de l’entreprise.
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
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 6d9c0c215d37458eab1deaf19f5818f07c1a9f3a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531494"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de chercher des événements de Azure Active Directory `AADSpnSignInEventsBeta` (AAD). Les clients doivent avoir une licence Azure Active Directory Premium P2 pour collecter et afficher les activités de ce tableau. Microsoft déplacera finalement toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.

Le tableau du schéma de recherche avancée contient des informations sur Azure Active Directory principal de service et les `AADSpnSignInEventsBeta` sign-ins d’identité gérée. Vous pouvez en savoir plus sur les différents types de Azure Active Directory dans les rapports d’activité de Azure Active Directory de la signature [- aperçu](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nom de colonne|Type de données|Description|
|---|---|---|
|`Timestamp`|`datetime`|Date et heure de génération de l’enregistrement|
|`Application`|`string`|Application qui a effectué l’action enregistrée|
|`ApplicationId`|`string`|Identificateur unique de l’application|
|`IsManagedIdentity`|`boolean`|Indique si la connectez-vous a été démarrée par une identité gérée|
|`ErrorCode`|`int`|Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> .|
|`CorrelationId`|`string`|Identificateur unique de l’événement de signature|
|`ServicePrincipalName`|`string`|Nom du principal de service qui a démarré la signature|
|`ServicePrincipalId`|`string`|Identificateur unique du principal de service qui a démarré la signature|
|`ResourceDisplayName`|`string`|Nom d’affichage de la ressource accessible|
|`ResourceId`|`string`|Identificateur unique de la ressource accessible|
|`ResourceTenantId`|`string`|Identificateur unique du client de la ressource à accès|
|`IPAddress`|`string`|Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées|
|`Country`|`string`|Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé|
|`State`|`string`|État où la se connecte s’est produite, si disponible|
|`City`|`string`|Ville où se trouve l’utilisateur du compte|
|`Latitude`|`string`|Coordonnées nord à sud de l’emplacement de la signature|
|`Longitude`|`string`|Coordonnées est à ouest de l’emplacement de la signature|
|`RequestId`|`string`|Identificateur unique de la demande|
|`ReportId`|`string`|Identificateur unique de l’événement|
||||

## <a name="related-articles"></a>Articles connexes

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
