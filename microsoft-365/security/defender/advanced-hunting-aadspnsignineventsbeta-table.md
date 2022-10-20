---
title: Table AADSpnSignInEventsBeta dans le schéma de chasse avancé
description: Découvrez les informations associées à la table des événements de connexion au principal de service et à l’identité managée d’Azure Active Directory.
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
ms.openlocfilehash: d24a67f6323e0f556e25021470d808b2fc67d918
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637043"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**S’applique à :**
- Microsoft 365 Defender

> [!IMPORTANT]
> La `AADSpnSignInEventsBeta` table est actuellement en version bêta et est proposée à court terme pour vous permettre de rechercher des événements de connexion Azure Active Directory (AAD). Les clients doivent disposer d’une licence Azure Active Directory Premium P2 pour collecter et afficher les activités de cette table. Microsoft finira par déplacer toutes les informations de schéma de connexion vers la `IdentityLogonEvents` table.

La `AADSpnSignInEventsBeta` table du schéma de repérage avancé contient des informations sur le principal de service Azure Active Directory et les connexions d’identité managée. Vous pouvez en savoir plus sur les différents types de connexions dans les [rapports d’activité de connexion Azure Active Directory - préversion](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nom de colonne|Type de données|Description|
|---|---|---|
|`Timestamp`|`datetime`|Date et heure de génération de l’enregistrement|
|`Application`|`string`|Application qui a effectué l’action enregistrée|
|`ApplicationId`|`string`|Identificateur unique de l’application|
|`IsManagedIdentity`|`boolean`|Indique si la connexion a été démarrée par une identité managée|
|`ErrorCode`|`int`|Contient le code d’erreur en cas d’erreur de connexion. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Identificateur unique de l’événement de connexion|
|`ServicePrincipalName`|`string`|Nom du principal de service qui a démarré la connexion|
|`ServicePrincipalId`|`string`|Identificateur unique du principal de service qui a démarré la connexion|
|`ResourceDisplayName`|`string`|Nom d’affichage de la ressource consultée|
|`ResourceId`|`string`|Identificateur unique de la ressource consultée|
|`ResourceTenantId`|`string`|Identificateur unique du locataire de la ressource consultée|
|`IPAddress`|`string`|Adresse IP affectée au point de terminaison et utilisée lors des communications réseau associées|
|`Country`|`string`|Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisée|
|`State`|`string`|État où la connexion s’est produite, le cas échéant|
|`City`|`string`|Ville où se trouve l’utilisateur du compte|
|`Latitude`|`string`|Coordonnées nord-sud de l’emplacement de connexion|
|`Longitude`|`string`|Coordonnées est à ouest de l’emplacement de connexion|
|`RequestId`|`string`|Identificateur unique de la requête|
|`ReportId`|`string`|Identificateur unique de l’événement|
||||

## <a name="related-articles"></a>Articles connexes

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
