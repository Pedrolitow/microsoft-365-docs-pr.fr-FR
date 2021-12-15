---
title: Tableau EmailEvents dans le schéma de repérage avancé
description: En savoir plus sur les événements associés Microsoft 365 courriers électroniques dans la table EmailEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, Microsoft 365 Defender, microsoft 365, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, EmailEvents, network message id, sender, recipient, attachment id, attachment id, attachment name, malware verdict, phishing verdict, attachment count, link count, url count
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
ms.openlocfilehash: baf6e8d6d896e31b5092f7d2b8948bb7771382bd
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2021
ms.locfileid: "61531527"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les événements impliquant le traitement des e-mails sur `EmailEvents` Microsoft Defender Office 365. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par un tableau, utilisez la référence de schéma intégrée disponible dans `ActionType` Defender for Cloud.

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
| `SenderDisplayName` | `string` | Nom de l’expéditeur affiché dans le carnet d’adresses, généralement une combinaison d’un prénom ou d’un prénom donné, d’une initiale du deuxième prénom et d’un nom ou d’un nom de famille |
| `SenderObjectId` | `string` |Identificateur unique du compte de l’expéditeur dans Azure AD |
| `SenderMailFromDomain` | `string` | Domaine de l’expéditeur dans l’en-tête MAIL FROM, également appelé expéditeur d’enveloppe ou adresse de retour |
| `SenderFromDomain` | `string` | Domaine e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderIPv4` | `string` | Adresse IPv4 du dernier serveur de messagerie détecté qui a relayé le message |
| `SenderIPv6` | `string` | Adresse IPv6 du dernier serveur de messagerie détecté qui a relayé le message |
| `RecipientEmailAddress` | `string` | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `RecipientObjectId` | `string` | Identificateur unique du destinataire de l’e-mail Azure AD |
| `Subject` | `string` | Objet de l’e-mail |
| `EmailClusterId` | `string` | Identificateur du groupe des e-mails similaires ordonnés en fonction de l’analyse heuristique de leur contenu. |
| `EmailDirection` | `string` | Direction de l'e-mail  par rapport à votre réseau : entrant, sortant, intra-organisationnel |
| `DeliveryAction` | `string` | Action de livraison de l'e-mail : remis, courrier indésirable, bloqué ou remplacé |
| `DeliveryLocation` | `string` | Emplacement de remise du courrier électronique : boîte de réception/dossier, local/externe, courrier indésirable, quarantaine, échec, supprimé, éléments supprimés |
| `ThreatTypes` | `string` | Verdict de la pile de filtrage du courrier électronique selon que l’e-mail contient des programmes malveillants, du hameçonnage ou d’autres menaces |
| `ThreatNames` | `string` |Nom de détection des programmes malveillants ou autres menaces détectées |
| `DetectionMethods` | `string` | Méthodes utilisées pour détecter les programmes malveillants, le hameçonnage ou d’autres menaces détectées dans l’e-mail |
| `ConfidenceLevel` | `string` | Liste des niveaux de confiance des verdicts de courrier indésirable ou de hameçonnage. Pour le courrier indésirable, cette colonne indique le niveau de confiance du courrier indésirable (SCL), indiquant si le courrier a été ignoré (-1), s’il a été trouvé comme non indésirable (0,1), s’il a été trouvé comme courrier indésirable avec un niveau de confiance modéré (5,6) ou s’il a été trouvé comme courrier indésirable avec un niveau de confiance élevé (9). Pour le hameçonnage, cette colonne indique si le niveau de confiance est « Élevé » ou « Faible ». |
| `EmailAction` | `string` | Action finale effectuée sur l’e-mail sur la base du verdict du filtre, des stratégies et des actions des utilisateurs : déplacer le message vers le dossier courrier indésirable, ajouter l’en-tête X, modifier l’objet, rediriger le message, supprimer le message, envoyer à la quarantaine, aucune action entreprise |
| `EmailActionPolicy` | `string` | Stratégie d’action appliquée : antispam hautement fiable, anti-courrier indésirable, antispam, courrier indésirable de courrier indésirable, emprunt d’identité de domaine anti-hameçonnage, emprunt d’identité d’utilisateur anti-hameçonnage, usurpation d’identité anti-hameçonnage, emprunt d’identité de graphe anti-hameçonnage, anti-programme malveillant, sécurité pièces jointes, règles de transport d’entreprise (ETR) |
| `EmailActionPolicyGuid` | `string` | Identificateur unique de la stratégie qui a déterminé l’action de courrier finale |
| `AttachmentCount` | `int` | Nombre de pièces jointes dans l’e-mail. |
| `UrlCount` | `int` | Nombre d’URL incorporées dans l’e-mail |
| `EmailLanguage` | `string` | Langue détectée du contenu de l’e-mail |
| `Connectors` | `string` | Instructions personnalisées qui définissent le flux de messagerie de l’organisation et la façon dont le courrier a été acheminé |
| `OrgLevelAction` | `string` | Action entreprise sur le courrier électronique en réponse à des correspondances à une stratégie définie au niveau de l’organisation |
| `OrgLevelPolicy` | `string` | Stratégie organisationnelle qui a déclenché l’action entreprise sur le courrier électronique |
| `UserLevelAction` | `string` | Action prise sur le courrier électronique en réponse à des correspondances à une stratégie de boîte aux lettres définie par le destinataire |
| `UserLevelPolicy` | `string` | Stratégie de boîte aux lettres d’utilisateur final qui a déclenché l’action sur le courrier électronique |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `AuthenticationDetails` | `string` | Liste des verdicts d’échec ou de passage par protocoles d’authentification de messagerie tels que DMARC, DKIM, SPF ou une combinaison de plusieurs types d’authentification (CompAuth) |

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
