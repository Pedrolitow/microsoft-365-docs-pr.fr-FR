---
title: Table AADSignInEventsBeta dans le schéma de chasse avancé
description: En savoir plus sur la table des événements de connexion Azure Active Directory du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, fichier, adresse IP, appareil, ordinateur, utilisateur, compte, identité, AAD
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
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: 90d275264c93736e1219488ecd4ae03e66a62af1
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67469138"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> La `AADSignInEventsBeta` table est actuellement en version bêta et est proposée à court terme pour vous permettre de rechercher des événements de connexion Azure Active Directory (AAD). Les clients doivent disposer d’une licence Azure Active Directory Premium P2 pour collecter et afficher les activités de cette table. Toutes les informations de schéma de connexion seront éventuellement déplacées vers la `IdentityLogonEvents` table.

La `AADSignInEventsBeta` table du schéma de repérage avancé contient des informations sur les connexions interactives et non interactives Azure Active Directory. En savoir plus sur les connexions dans les [rapports d’activité de connexion Azure Active Directory - préversion](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table. Pour plus d’informations sur les autres tables du schéma de chasse avancé, consultez la [référence de chasse avancée](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nom de colonne|Type de données|Description|
|---|---|---|
|`Timestamp`|`datetime`|Date et heure de génération de l’enregistrement|
|`Application`|`string`|Application qui a effectué l’action enregistrée|
|`ApplicationId`|`string`|Identificateur unique de l’application|
|`LogonType`|`string`|Type de session d’ouverture de session, interactif, interactif à distance (RDP), réseau, lot et service|
|`ErrorCode`|`int`|Contient le code d’erreur en cas d’erreur de connexion. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|Identificateur unique de l’événement de connexion|
|`SessionId`|`string`|Numéro unique attribué à un utilisateur par le serveur d’un site web pendant la visite ou la session|
|`AccountDisplayName`|`string`|Nom de l’utilisateur de compte affiché dans le carnet d’adresses. En règle générale, il s’agit d’une combinaison d’un prénom ou d’un prénom donné, d’une initiale intermédiaire et d’un nom ou d’un nom de famille.|
|`AccountObjectId`|`string`|Identificateur unique du compte dans Azure AD|
|`AccountUpn`|`string`|Nom d’utilisateur principal (UPN) du compte|
|`IsExternalUser`|`int`|Indique si l’utilisateur qui s’est connecté est externe. Valeurs possibles : -1 (non défini), 0 (non externe), 1 (externe).|
|`IsGuestUser`|`boolean`|Indique si l’utilisateur qui s’est connecté est un invité dans le locataire|
|`AlternateSignInName`|`string`|Nom d’utilisateur principal local (UPN) de l’utilisateur qui se connecte à Azure AD|
|`LastPasswordChangeTimestamp`|`datetime`|Date et heure auxquelles l’utilisateur qui s’est connecté a modifié son mot de passe pour la dernière fois|
|`ResourceDisplayName`|`string`|Nom d’affichage de la ressource consultée|
|`ResourceId`|`string`|Identificateur unique de la ressource consultée|
|`ResourceTenantId`|`string`|Identificateur unique du locataire de la ressource consultée|
|`DeviceName`|`string`|Nom de domaine complet (FQDN) de la machine|
|`AadDeviceId`|`string`|Identificateur unique de l’appareil dans Azure AD|
|`OSPlatform`|`string`|Plateforme du système d’exploitation client s’exécutant sur la machine. Indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7.|
|`DeviceTrustType`|`string`|Indique le type d’approbation de l’appareil qui s’est connecté. Pour les scénarios d’appareil managé uniquement. Les valeurs possibles sont Workplace, AzureAd et ServerAd.|
|`IsManaged`|`int`|Indique si l’appareil qui a initié la connexion est un appareil managé (1) ou non un appareil managé (0)|
|`IsCompliant`|`int`|Indique si l’appareil qui a initié la connexion est conforme (1) ou non conforme (0)|
|`AuthenticationProcessingDetails`|`string`|Détails sur le processeur d’authentification|
|`AuthenticationRequirement`|`string`|Type d’authentification requis pour la connexion. Valeurs possibles : multiFactorAuthentication (MFA était obligatoire) et singleFactorAuthentication (aucune authentification multifacteur n’était requise).|
|`TokenIssuerType`|`int`|Indique si l’émetteur de jeton est Azure Active Directory (0) ou Services ADFS (1)|
|`RiskLevelAggregated`|`int`|Niveau de risque agrégé pendant la connexion. Valeurs possibles : 0 (niveau de risque agrégé non défini), 1 (aucun), 10 (faible), 50 (moyen) ou 100 (élevé).|
|`RiskDetails`|`int`|Détails sur l’état à risque de l’utilisateur qui s’est connecté|
|`RiskState`|`int`|Indique l’état utilisateur à risque. Valeurs possibles : 0 (aucun), 1 (sécurisé confirmé), 2 (corrigé), 3 (ignoré), 4 (à risque) ou 5 (compromis confirmé).|
|`UserAgent`|`string`|Informations de l’agent utilisateur à partir du navigateur web ou d’une autre application cliente|
|`ClientAppUsed`|`string`|Indique l’application cliente utilisée|
|`Browser`|`string`|Détails sur la version du navigateur utilisée pour se connecter|
|`ConditionalAccessPolicies`|`string`|Détails des stratégies d’accès conditionnel appliquées à l’événement de connexion|
|`ConditionalAccessStatus`|`int`|État des stratégies d’accès conditionnel appliquées à la connexion. Les valeurs possibles sont 0 (stratégies appliquées), 1 (échec de la tentative d’application des stratégies) ou 2 (stratégies non appliquées).|
|`IPAddress`|`string`|Adresse IP affectée au point de terminaison et utilisée lors des communications réseau associées|
|`Country`|`string`|Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisée|
|`State`|`string`|État où la connexion s’est produite, le cas échéant|
|`City`|`string`|Ville où se trouve l’utilisateur du compte|
|`Latitude`|`string`|Coordonnées nord-sud de l’emplacement de connexion|
|`Longitude`|`string`|Coordonnées est à ouest de l’emplacement de connexion|
|`NetworkLocationDetails`|`string`|Détails de l’emplacement réseau du processeur d’authentification de l’événement de connexion|
|`RequestId`|`string`|Identificateur unique de la requête|
|`ReportId`|`string`|Identificateur unique de l’événement|

## <a name="related-articles"></a>Articles connexes

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
