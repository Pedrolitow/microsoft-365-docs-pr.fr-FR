---
title: Table AADSpnSignInEventsBeta dans le schéma de recherche avancé
description: En savoir plus sur les informations associées au principal de service Azure Active Directory et à la table des événements de signature d’identité gérée du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, AlertInfo, alert, entities, evidence, file, IP address, device, machine, user, account, identity, AAD
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
ms.openlocfilehash: 42acf24ce9b941fffb1ce0ed4b67216bd8c1de47
ms.sourcegitcommit: 4482c174e0e68e0fbbc7ad9ef6b0e78dc34ac85a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "49784298"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**S’applique à :**

- Microsoft 365 Defender

>[!IMPORTANT]
> Le tableau est actuellement en version bêta et est proposé à court terme pour vous permettre de faire la recherche dans les événements de compte de principal de `AADSpnSignInEventsBeta` service Azure Active Directory (AAD) et d’identité gérée. Nous finirons par déplacer toutes les informations de schéma de signature vers la `IdentityLogonEvents` table.<br><br>
> Les clients qui peuvent accéder à Microsoft 365 Defender par le biais de la solution Microsoft Defender pour point de terminaison intégrée du Centre de sécurité Azure, mais qui n’ont pas de licences pour Microsoft Defender pour Office, Microsoft Defender pour l’identité ou Microsoft Cloud App Security, ne pourront pas afficher ce schéma. 



Le tableau du schéma de recherche avancée contient des informations sur le principal de service Azure Active Directory et les signatures d’identité `AADSpnSignInEventsBeta` gérée. Vous pouvez en savoir plus sur les différents types de sign-ins dans les rapports d’activité de [sign-in Azure Active Directory - aperçu](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-all-sign-ins).

Utilisez cette référence pour créer des requêtes qui renvoient des informations de la table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, consultez [la référence de repérage avancé](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).





| Nom de colonne     | Type de données | Description   |
| ----- | ----- | ---- |
| `Timestamp` | DateHeure      | Date et heure de génération de l’enregistrement                                                                                                     |
| `Application`          | string        | Application qui a effectué l’action enregistrée                                                                                                   |
| `ApplicationId`        | chaîne        | Identificateur unique de l’application                                                                                                           |
| `IsManagedIdentity`    | valeur booléenne       | Indique si la connectez-vous a été initiée par une identité gérée                                                                               |
| `ErrorCode`            | int        | Contient le code d’erreur si une erreur de se connecte se produit. Pour trouver une description d’un code d’erreur spécifique, visitez <https://aka.ms/AADsigninsErrorCodes> . |
| `CorrelationId`        | chaîne        | Identificateur unique de l’événement de signature                                                                                                          |
| `ServicePrincipalName` | chaîne        | Nom du principal de service à l’origine de la signature                                                                                        |
| `ServicePrincipalId`   | chaîne        | Identificateur unique du principal de service à l’origine de la signature                                                                           |
| `ResourceDisplayName`  | chaîne        | Nom d’affichage de la ressource accessible                                                                                                           |
| `ResourceId`           | chaîne        | Identificateur unique de la ressource accessible                                                                                                      |
| `ResourceTenantId`     | chaîne        | Identificateur unique du client de la ressource à accès                                                                                        |
| `IPAddress`            | chaîne        | Adresse IP attribuée au point de terminaison et utilisée lors des communications réseau associées                                                              |
| `CountryCode`          | chaîne        | Code à deux lettres indiquant le pays où l’adresse IP du client est géolocalisé                                                                |
| `State`                | chaîne        | État où la se connecte s’est produite, si disponible                                                                                                  |
| `City`                 | chaîne        | Ville où se trouve l’utilisateur du compte                                                                                                          |
| `Latitude`             | chaîne        | Coordonnées nord à sud de l’emplacement de la signature                                                                                          |
| `Longitude`            | chaîne        | Coordonnées est à ouest de l’emplacement de la signature                                                                                            |
| `RequestId`            | chaîne        | Identificateur unique de la demande                                                                                                                |
|`ReportId` | chaîne | Identificateur unique de l’événement | 

 

## <a name="related-articles"></a>Articles connexes

-   [AADSignInEventsBeta](https://docs.microsoft.com/microsoft-365/security/mtp/advanced-hunting-aadsignineventsbeta-table)
-   [Vue d’ensemble du repérage avancé](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
-   [Apprendre le langage de requête](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
-   [Comprendre le schéma](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)

