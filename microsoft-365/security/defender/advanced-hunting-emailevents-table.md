---
title: Tableau EmailEvents dans le schéma de repérage avancé
description: En savoir plus sur les événements associés aux e-mails Microsoft 365 dans la table EmailEvents du schéma de repérage avancé
keywords: repérage avancé, chasse aux menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, EmailEvents, ID de message réseau, expéditeur, destinataire, ID de pièce jointe, nom de pièce jointe, verdict de logiciel malveillant, verdict de hameçonnage, nombre de pièces jointes, nombre de liens, nombre d’URL
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
ms.openlocfilehash: 5ac64dfbfd42d76e350d27a5d7a1594e6c055cba
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67482051"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender
- Microsoft Defender pour Office 365

La `EmailEvents` table du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les événements impliquant le traitement des e-mails sur Microsoft Defender pour Office 365. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

> [!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `NetworkMessageId` | `string` | Identificateur unique de l’e-mail, généré par Microsoft 365 |
| `InternetMessageId` | `string` | Identificateur public de l’e-mail défini par le système de courrier d’envoi |
| `SenderMailFromAddress` | `string` | Adresse e-mail de l’expéditeur dans l’en-tête MAIL FROM, également appelé expéditeur d’enveloppe ou adresse de retour |
| `SenderFromAddress` | `string` | Adresse e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderDisplayName` | `string` | Nom de l’expéditeur affiché dans le carnet d’adresses, généralement une combinaison d’un prénom ou d’un prénom donné, d’une initiale intermédiaire et d’un nom ou d’un nom de famille |
| `SenderObjectId` | `string` |Identificateur unique du compte de l’expéditeur dans Azure AD |
| `SenderMailFromDomain` | `string` | Domaine de l’expéditeur dans l’en-tête MAIL FROM, également appelé expéditeur d’enveloppe ou adresse de retour |
| `SenderFromDomain` | `string` | Domaine e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderIPv4` | `string` | Adresse IPv4 du dernier serveur de messagerie détecté qui a relayé le message |
| `SenderIPv6` | `string` | Adresse IPv6 du dernier serveur de messagerie détecté qui a relayé le message |
| `RecipientEmailAddress` | `string` | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `RecipientObjectId` | `string` | Identificateur unique du destinataire de l’e-mail dans Azure AD |
| `Subject` | `string` | Objet de l’e-mail |
| `EmailClusterId` | `string` | Identificateur du groupe des e-mails similaires ordonnés en fonction de l’analyse heuristique de leur contenu. |
| `EmailDirection` | `string` | Direction de l'e-mail  par rapport à votre réseau : entrant, sortant, intra-organisationnel |
| `DeliveryAction` | `string` | Action de livraison de l'e-mail : remis, courrier indésirable, bloqué ou remplacé |
| `DeliveryLocation` | `string` | Emplacement de remise du courrier électronique : boîte de réception/dossier, local/externe, courrier indésirable, quarantaine, échec, supprimé, éléments supprimés |
| `ThreatTypes` | `string` | Verdict de la pile de filtrage d’e-mail indiquant si l’e-mail contient des programmes malveillants, du hameçonnage ou d’autres menaces |
| `ThreatNames` | `string` |Nom de détection des programmes malveillants ou autres menaces détectées |
| `DetectionMethods` | `string` | Méthodes utilisées pour détecter les programmes malveillants, le hameçonnage ou d’autres menaces détectées dans l’e-mail |
| `ConfidenceLevel` | `string` | Liste des niveaux de confiance des verdicts de courrier indésirable ou de hameçonnage. Pour le courrier indésirable, cette colonne affiche le niveau de confiance du courrier indésirable (SCL), indiquant si l’e-mail a été ignoré (-1), s’il s’est avéré qu’il ne s’agissait pas de courrier indésirable (0,1), s’il s’agissait de courrier indésirable avec une confiance modérée (5,6) ou s’il s’agissait de courrier indésirable avec une confiance élevée (9). Pour le hameçonnage, cette colonne indique si le niveau de confiance est « Élevé » ou « Faible ». |
| `EmailAction` | `string` | Action finale effectuée sur l’e-mail sur la base du verdict du filtre, des stratégies et des actions des utilisateurs : déplacer le message vers le dossier courrier indésirable, ajouter l’en-tête X, modifier l’objet, rediriger le message, supprimer le message, envoyer à la quarantaine, aucune action entreprise |
| `EmailActionPolicy` | `string` | Stratégie d’action appliquée : antispam hautement fiable, anti-courrier indésirable, antispam, courrier indésirable de courrier indésirable, emprunt d’identité de domaine anti-hameçonnage, emprunt d’identité d’utilisateur anti-hameçonnage, usurpation d’identité anti-hameçonnage, emprunt d’identité de graphe anti-hameçonnage, anti-programme malveillant, sécurité pièces jointes, règles de transport d’entreprise (ETR) |
| `EmailActionPolicyGuid` | `string` | Identificateur unique de la stratégie qui a déterminé l’action de courrier finale |
| `AttachmentCount` | `int` | Nombre de pièces jointes dans l’e-mail. |
| `UrlCount` | `int` | Nombre d’URL incorporées dans l’e-mail |
| `EmailLanguage` | `string` | Langue détectée du contenu de l’e-mail |
| `Connectors` | `string` | Instructions personnalisées qui définissent le flux de messagerie de l’organisation et la façon dont l’e-mail a été routée |
| `OrgLevelAction` | `string` | Action effectuée sur l’e-mail en réponse aux correspondances à une stratégie définie au niveau de l’organisation |
| `OrgLevelPolicy` | `string` | Stratégie organisationnelle qui a déclenché l’action effectuée sur l’e-mail |
| `UserLevelAction` | `string` | Action effectuée sur l’e-mail en réponse aux correspondances avec une stratégie de boîte aux lettres définie par le destinataire |
| `UserLevelPolicy` | `string` | Stratégie de boîte aux lettres de l’utilisateur final qui a déclenché l’action effectuée sur l’e-mail |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `AuthenticationDetails` | `string` | Liste des verdicts de réussite ou d’échec par protocoles d’authentification par e-mail tels que DMARC, DKIM, SPF ou une combinaison de plusieurs types d’authentification (CompAuth) |

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
