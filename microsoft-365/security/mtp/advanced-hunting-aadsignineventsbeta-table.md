---
title: Table AADSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur les informations associées à la table des événements de sign-in Azure Active Directory du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, file, IP address, device, machine, user, account, identity, AAD
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
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
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 1830eeec674c4948bd6492780ef8a0a8039111b8
ms.sourcegitcommit: 4482c174e0e68e0fbbc7ad9ef6b0e78dc34ac85a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "49784286"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

>[!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de passer par les événements de signature `AADSignInEventsBeta` Azure Active Directory (AAD). Nous finirons par déplacer toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.<br><br>
> Les clients qui peuvent accéder à Microsoft 365 Defender par le biais de la solution Microsoft Defender pour point de terminaison intégrée du Centre de sécurité Azure, mais qui n’ont pas de licences pour Microsoft Defender pour Office, Microsoft Defender pour l’identité ou Microsoft Cloud App Security, ne pourront pas afficher ce schéma. 

 

Le tableau du schéma de recherche avancée contient des informations sur les cartes de visite interactives et `AADSignInEventsBeta` non interactives Azure Active Directory. En savoir plus sur les sign-ins dans les rapports [d’activité de sign-in Azure Active Directory - aperçu](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.
Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

 

 

| Nom de colonne                 | Type de données | Description          |
|---------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Timestamp`                       | DateHeure      | Date et heure de génération de l’enregistrement                                                                                                                                         |
| `Application`                     | string        | Application qui a effectué l’action enregistrée                                                                                                                                       |
| `ApplicationId`                   | chaîne        | Identificateur unique de l’application                                                                                                                                               |
| `LogonType`                       | chaîne        | Type de session d’ouverture de session, spécifiquement interactive, interactive à distance (RDP), réseau, lot et service                                                                              |
| `ErrorCode`                       | int        | Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> .                                     |
| `CorrelationId`                   | chaîne        | Identificateur unique de l’événement de signature                                                                                                                                              |
| `SessionId`                       | chaîne        | Numéro unique attribué à un utilisateur par le serveur d’un site web pour la durée de la visite ou de la session                                                                                     |
| `AccountDisplayName`              | chaîne        | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiale du deuxième prénom et d’un nom ou d’un nom de famille.                             |
| `AccountObjectId`                 | chaîne        | Identificateur unique du compte dans Azure AD                                                                                                                                       |
| `AccountUpn`                      | chaîne        | Nom d’utilisateur principal (UPN) du compte                                                                                                                                            |
| `IsExternalUser`                  | int        | Indique si l’utilisateur qui s’est inscrit est externe. Valeurs possibles : -1 (non définie) , 0 (non externe), 1 (externe).                                                                   |
| `IsGuestUser`                     | valeur booléenne       | Indique si l’utilisateur qui s’est inscrit est un invité dans le client                                                                                                                  |
| `AlternateSignInName`             | chaîne        | Nom d’utilisateur principal (UPN) local de l’utilisateur se signant à Azure AD                                                                                                            |
| `LastPasswordChangeTimestamp`     | DateHeure        | Date et heure de la dernière fois où l’utilisateur qui s’est inscrit a modifié son mot de passe                                                                                                              |
| `ResourceDisplayName`             | chaîne        | Nom d’affichage de la ressource accessible                                                                                                                                               |
| `ResourceId`                      | chaîne        | Identificateur unique de la ressource accessible                                                                                                                                          |
| `ResourceTenantId`                | chaîne        | Identificateur unique du client de la ressource à accès                                                                                                                            |
| `DeviceName`                      | string        | Nom de domaine complet (FQDN) de la machine                                                                                                                                   |
| `AadDeviceId`                     | string   |      Identificateur unique de l’appareil dans Azure AD                                                                                                                                                                               |
| `OSPlatform`                      | string        | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7.  |
| `DeviceTrustType`                 | string        | Indique le type d’confiance de l’appareil qui s’est connecté. Pour les scénarios d’appareil géré uniquement. Les valeurs possibles sont Workplace, AzureAd et ServerAd.                                     |
| `IsManaged`                       | int       | Indique si l’appareil à l’origine de la connectez-vous est un appareil géré (1) ou non un appareil géré (0)                                                                         |
| `IsCompliant`                     | int       | Indique si l’appareil à l’origine de la signature est conforme (1) ou non conforme (0)                                                                                       |
| `AuthenticationProcessingDetails` | chaîne        | Détails sur le processeur d’authentification                                                                                                                                          |
| `AuthenticationRequirement`       | chaîne        | Type d’authentification requis pour la signature. Valeurs possibles : multiFactorAuthentication (l’authentification multifacteur était requise) et singleFactorAuthentication (aucune authentification multifacteur n’était requise).                |
| `TokenIssuerType`                 | int        | Indique si l’émetteur de jeton est Azure Active Directory (0) ou services de fédération Active Directory (1)                                                                             |
| `RiskLevelAggregated`                       | int        | Niveau de risque agrégé lors de la signature. Valeurs possibles : 0 (niveau de risque agrégé non définie), 1 (aucun), 10 (faible), 50 (moyen) ou 100 (élevé).                               |
| `RiskDetails`                      | int        | Détails sur l’état à risque de l’utilisateur qui s’est inscrit                                                                                                                            |
| `RiskState`                       | int        | Indique l’état de l’utilisateur à risque. Valeurs possibles : 0 (aucun), 1 (sécurisé confirmé), 2 (corrigé), 3 (rejeté), 4 (à risque) ou 5 (confirmé compromis).                                |
| `UserAgent`                       | chaîne        | Informations sur l’agent utilisateur à partir du navigateur web ou d’une autre application cliente                                                                                                             |
| `ClientAppUsed`                   | chaîne        | Indique l’application cliente utilisée                                                                                                                                                       |
| `Browser`                         | chaîne        | Détails sur la version du navigateur utilisé pour se connecter                                                                                                                            |
| `ConditionalAccessPolicies`       | chaîne        | Détails des stratégies d’accès conditionnel appliquées à l’événement de signature                                                                                                             |
| `ConditionalAccessStatus`         | int        | État des stratégies d’accès conditionnel appliquées à la signature. Les valeurs possibles sont 0 (stratégies appliquées), 1 (échec de tentative d’application des stratégies) ou 2 (stratégies non appliquées).      |
| `IPAddress`                       | chaîne        | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées                                                                                                  |
| `CountryCode`                     | chaîne        | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé                                                                                                    |
| `State`                           | chaîne        | État où la se connecte s’est produite, si disponible                                                                                                                                      |
| `City`                            | chaîne        | Ville où se trouve l’utilisateur du compte                                                                                                                                              |
| `Latitude`                        | chaîne        | Coordonnées nord à sud de l’emplacement de la signature                                                                                                                              |
| `Longitude`                       | chaîne        | Coordonnées est à ouest de l’emplacement de la signature                                                                                                                                |
| `NetworkLocationDetails`          | chaîne        | Détails de l’emplacement réseau du processeur d’authentification de l’événement de authentification                                                                                                       |
| `RequestId`                       | chaîne        |  Identificateur unique de la demande                                                                                                                                                   |
|`ReportId` | chaîne | Identificateur unique de l’événement |

 

 

## <a name="related-articles"></a>Articles connexes

-   [AADSpnSignInEventsBeta](https://docs.microsoft.com/microsoft-365/security/mtp/advanced-hunting-aadspnsignineventsbeta-table)
-   [Vue d’ensemble du repérage avancé](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
-   [Apprendre le langage de requête](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
-   [Comprendre le schéma](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)

 
