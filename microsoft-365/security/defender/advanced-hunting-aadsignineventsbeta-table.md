---
title: Table AADSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur la Azure Active Directory des événements de Azure Active Directory du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, file, IP address, device, machine, user, account, identity, AAD
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
ms.openlocfilehash: 8fa111b636026de49c854eb5ec8c17f1aad5c3eb
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60700336"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

> [!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de chercher des événements de Azure Active Directory `AADSignInEventsBeta` (AAD) de signature. Les clients doivent avoir une licence Azure Active Directory Premium P2 pour collecter et afficher les activités de ce tableau. Nous finirons par déplacer toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.

Le tableau dans le schéma de recherche avancé contient des informations sur Azure Active Directory des `AADSignInEventsBeta` sign-ins interactives et non interactives. En savoir plus sur les sign-ins dans Azure Active Directory des rapports d’activité de la [sign-in - aperçu](/azure/active-directory/reports-monitoring/concept-all-sign-ins). 

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table. Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|Nom de colonne|Type de données|Description|
|---|---|---|
|`Timestamp`|DateHeure|Date et heure de génération de l’enregistrement|
|`Application`|string|Application qui a effectué l’action enregistrée|
|`ApplicationId`|chaîne|Identificateur unique de l’application|
|`LogonType`|chaîne|Type de session d’ouverture de session, interactive, interactive, interactive à distance (RDP), réseau, lot et service|
|`ErrorCode`|int|Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> .|
|`CorrelationId`|chaîne|Identificateur unique de l’événement de signature|
|`SessionId`|chaîne|Numéro unique attribué à un utilisateur par le serveur d’un site web pendant la visite ou la session|
|`AccountDisplayName`|chaîne|Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiale du deuxième prénom et d’un nom ou d’un nom de famille.|
|`AccountObjectId`|chaîne|Identificateur unique du compte dans Azure AD|
|`AccountUpn`|chaîne|Nom d’utilisateur principal (UPN) du compte|
|`IsExternalUser`|int|Indique si l’utilisateur qui s’est inscrit est externe. Valeurs possibles : -1 (non définie), 0 (non externe), 1 (externe).|
|`IsGuestUser`|valeur booléenne|Indique si l’utilisateur qui s’est inscrit est un invité dans le client|
|`AlternateSignInName`|chaîne|Nom d’utilisateur principal (UPN) local de l’utilisateur qui se Azure AD|
|`LastPasswordChangeTimestamp`|DateHeure|Date et heure de la dernière fois où l’utilisateur qui s’est inscrit a modifié son mot de passe|
|`ResourceDisplayName`|chaîne|Nom d’affichage de la ressource accessible|
|`ResourceId`|chaîne|Identificateur unique de la ressource à accès|
|`ResourceTenantId`|chaîne|Identificateur unique du client de la ressource à accès|
|`DeviceName`|string|Nom de domaine complet (FQDN) de la machine|
|`AadDeviceId`|string|Identificateur unique de l’appareil dans Azure AD|
|`OSPlatform`|string|Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein de la même famille, telles que Windows 11, Windows 10 et Windows 7.|
|`DeviceTrustType`|chaîne|Indique le type d’confiance de l’appareil qui s’est connecté. Pour les scénarios d’appareil géré uniquement. Les valeurs possibles sont Workplace, AzureAd et ServerAd.|
|`IsManaged`|int|Indique si l’appareil à l’origine de la connectez-vous est un appareil géré (1) ou non un appareil géré (0)|
|`IsCompliant`|int|Indique si l’appareil à l’origine de la signature est conforme (1) ou non (0)|
|`AuthenticationProcessingDetails`|chaîne|Détails sur le processeur d’authentification|
|`AuthenticationRequirement`|chaîne|Type d’authentification requis pour la signature. Valeurs possibles : multiFactorAuthentication (l’authentification multifacteur était requise) et singleFactorAuthentication (aucune authentification multifacteur n’était requise).|
|`TokenIssuerType`|int|Indique si l’émetteur de jeton est Azure Active Directory (0) ou les services de fédération Active Directory (1)|
|`RiskLevelAggregated`|int|Niveau de risque agrégé lors de la signature. Valeurs possibles : 0 (niveau de risque agrégé non définie), 1 (aucun), 10 (faible), 50 (moyen) ou 100 (élevé).|
|`RiskDetails`|int|Détails sur l’état à risque de l’utilisateur qui s’est inscrit|
|`RiskState`|int|Indique l’état de l’utilisateur à risque. Valeurs possibles : 0 (aucun), 1 (sécurisé confirmé), 2 (corrigé), 3 (rejeté), 4 (à risque) ou 5 (confirmé compromis).|
|`UserAgent`|chaîne|Informations sur l’agent utilisateur à partir du navigateur web ou d’une autre application cliente|
|`ClientAppUsed`|chaîne|Indique l’application cliente utilisée|
|`Browser`|chaîne|Détails sur la version du navigateur utilisé pour se connecter|
|`ConditionalAccessPolicies`|chaîne|Détails des stratégies d’accès conditionnel appliquées à l’événement de signature|
|`ConditionalAccessStatus`|int|État des stratégies d’accès conditionnel appliquées à la signature. Les valeurs possibles sont 0 (stratégies appliquées), 1 (échec de tentative d’application des stratégies) ou 2 (stratégies non appliquées).|
|`IPAddress`|chaîne|Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées|
|`Country`|chaîne|Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé|
|`State`|chaîne|État où la se connecte s’est produite, si disponible|
|`City`|chaîne|Ville où se trouve l’utilisateur du compte|
|`Latitude`|chaîne|Coordonnées nord à sud de l’emplacement de la signature|
|`Longitude`|chaîne|Coordonnées est à ouest de l’emplacement de la signature|
|`NetworkLocationDetails`|chaîne|Détails de l’emplacement réseau du processeur d’authentification de l’événement de authentification|
|`RequestId`|chaîne|Identificateur unique de la demande|
|`ReportId`|chaîne|Identificateur unique de l’événement|

## <a name="related-articles"></a>Articles connexes

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
