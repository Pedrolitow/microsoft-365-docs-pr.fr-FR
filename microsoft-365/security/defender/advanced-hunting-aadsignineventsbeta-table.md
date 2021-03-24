---
title: Table AADSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur les informations associées à la table des événements de sign-in Azure Active Directory du schéma de recherche avancée
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, file, IP address, device, machine, user, account, identity, AAD
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
ms.openlocfilehash: 7b595496c28710bfa25fc88653425242770bf57f
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063617"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

>[!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de passer par les événements de signature `AADSignInEventsBeta` Azure Active Directory (AAD). Nous finirons par déplacer toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.<br><br>
> Les clients qui peuvent accéder à Microsoft 365 Defender par le biais de la solution Microsoft Defender pour point de terminaison intégrée du Centre de sécurité Azure, mais qui n’ont pas de licences pour Microsoft Defender pour Office, Microsoft Defender pour l’identité ou Microsoft Cloud App Security, ne pourront pas afficher ce schéma. 

 

Le tableau du schéma de recherche avancée contient des informations sur les cartes de visite interactives et `AADSignInEventsBeta` non interactives Azure Active Directory. En savoir plus sur les sign-ins dans les rapports [d’activité de sign-in Azure Active Directory - aperçu](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.
Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

 

 

| Nom de colonne                 | Type de données | Description          |
|---------------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Timestamp`                       | DateHeure      | Date et heure de génération de l’enregistrement                                                                                                                                         |
| `Application`                     | string        | Application qui a effectué l’action enregistrée                                                                                                                                       |
| `ApplicationId`                   | string        | Identificateur unique de l’application                                                                                                                                               |
| `LogonType`                       | string        | Type de session d’ouverture de session, spécifiquement interactive, interactive à distance (RDP), réseau, lot et service                                                                              |
| `ErrorCode`                       | entier        | Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> .                                     |
| `CorrelationId`                   | string        | Identificateur unique de l’événement de signature                                                                                                                                              |
| `SessionId`                       | string        | Numéro unique attribué à un utilisateur par le serveur d’un site web pour la durée de la visite ou de la session                                                                                     |
| `AccountDisplayName`              | string        | Nom de l’utilisateur du compte affiché dans le carnet d’adresses. En règle générale, une combinaison d’un prénom ou d’un prénom donné, d’une initiale du deuxième prénom et d’un nom ou d’un nom de famille.                             |
| `AccountObjectId`                 | string        | Identificateur unique du compte dans Azure AD                                                                                                                                       |
| `AccountUpn`                      | string        | Nom d’utilisateur principal (UPN) du compte                                                                                                                                            |
| `IsExternalUser`                  | entier        | Indique si l’utilisateur qui s’est inscrit est externe. Valeurs possibles : -1 (non définie) , 0 (non externe), 1 (externe).                                                                   |
| `IsGuestUser`                     | booléen       | Indique si l’utilisateur qui s’est inscrit est un invité dans le client                                                                                                                  |
| `AlternateSignInName`             | string        | Nom d’utilisateur principal (UPN) local de l’utilisateur se signant à Azure AD                                                                                                            |
| `LastPasswordChangeTimestamp`     | DateHeure        | Date et heure de la dernière fois où l’utilisateur qui s’est inscrit a modifié son mot de passe                                                                                                              |
| `ResourceDisplayName`             | string        | Nom d’affichage de la ressource accessible                                                                                                                                               |
| `ResourceId`                      | string        | Identificateur unique de la ressource accessible                                                                                                                                          |
| `ResourceTenantId`                | string        | Identificateur unique du client de la ressource à accès                                                                                                                            |
| `DeviceName`                      | string        | Nom de domaine complet (FQDN) de la machine                                                                                                                                   |
| `AadDeviceId`                     | string   |      Identificateur unique de l’appareil dans Azure AD                                                                                                                                                                               |
| `OSPlatform`                      | string        | Plateforme du système d’exploitation client s’exécutant sur la machine. Cela indique des systèmes d’exploitation spécifiques, y compris des variantes au sein d’une même famille, telles que Windows 10 et Windows 7.  |
| `DeviceTrustType`                 | string        | Indique le type d’confiance de l’appareil qui s’est connecté. Pour les scénarios d’appareil géré uniquement. Les valeurs possibles sont Workplace, AzureAd et ServerAd.                                     |
| `IsManaged`                       | entier       | Indique si l’appareil à l’origine de la connectez-vous est un appareil géré (1) ou non un appareil géré (0)                                                                         |
| `IsCompliant`                     | entier       | Indique si l’appareil à l’origine de la signature est conforme (1) ou non conforme (0)                                                                                       |
| `AuthenticationProcessingDetails` | string        | Détails sur le processeur d’authentification                                                                                                                                          |
| `AuthenticationRequirement`       | string        | Type d’authentification requis pour la signature. Valeurs possibles : multiFactorAuthentication (l’authentification multifacteur était requise) et singleFactorAuthentication (aucune authentification multifacteur n’était requise).                |
| `TokenIssuerType`                 | entier        | Indique si l’émetteur de jeton est Azure Active Directory (0) ou services de fédération Active Directory (1)                                                                             |
| `RiskLevelAggregated`                       | entier        | Niveau de risque agrégé lors de la signature. Valeurs possibles : 0 (niveau de risque agrégé non définie), 1 (aucun), 10 (faible), 50 (moyen) ou 100 (élevé).                               |
| `RiskDetails`                      | entier        | Détails sur l’état à risque de l’utilisateur qui s’est inscrit                                                                                                                            |
| `RiskState`                       | entier        | Indique l’état de l’utilisateur à risque. Valeurs possibles : 0 (aucun), 1 (sécurisé confirmé), 2 (corrigé), 3 (rejeté), 4 (à risque) ou 5 (confirmé compromis).                                |
| `UserAgent`                       | string        | Informations sur l’agent utilisateur à partir du navigateur web ou d’une autre application cliente                                                                                                             |
| `ClientAppUsed`                   | string        | Indique l’application cliente utilisée                                                                                                                                                       |
| `Browser`                         | string        | Détails sur la version du navigateur utilisé pour se connecter                                                                                                                            |
| `ConditionalAccessPolicies`       | string        | Détails des stratégies d’accès conditionnel appliquées à l’événement de signature                                                                                                             |
| `ConditionalAccessStatus`         | entier        | État des stratégies d’accès conditionnel appliquées à la signature. Les valeurs possibles sont 0 (stratégies appliquées), 1 (échec de tentative d’application des stratégies) ou 2 (stratégies non appliquées).      |
| `IPAddress`                       | string        | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées                                                                                                  |
| `Country`                     | string        | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé                                                                                                    |
| `State`                           | string        | État où la se connecte s’est produite, si disponible                                                                                                                                      |
| `City`                            | string        | Ville où se trouve l’utilisateur du compte                                                                                                                                              |
| `Latitude`                        | string        | Coordonnées nord à sud de l’emplacement de la signature                                                                                                                              |
| `Longitude`                       | string        | Coordonnées est à ouest de l’emplacement de la signature                                                                                                                                |
| `NetworkLocationDetails`          | string        | Détails de l’emplacement réseau du processeur d’authentification de l’événement de authentification                                                                                                       |
| `RequestId`                       | string        |  Identificateur unique de la demande                                                                                                                                                   |
|`ReportId` | string | Identificateur unique de l’événement |

 

 

## <a name="related-articles"></a>Articles connexes

-   [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
-   [Vue d’ensemble du repérage avancé](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
-   [Apprendre le langage de requête](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
-   [Comprendre le schéma](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)

 