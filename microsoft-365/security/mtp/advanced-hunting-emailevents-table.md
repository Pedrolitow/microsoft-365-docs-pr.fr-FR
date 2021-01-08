---
title: Tableau EmailEvents dans le schéma de repérage avancé
description: En savoir plus sur les événements associés aux e-mails Microsoft 365 dans la table EmailEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, EmailEvents, network message id, sender, recipient, attachment id, attachment id, attachment name, malware verdict, phishing verdict, attachment count, link count, url count
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 6dbd7473074212c6bc257e683288040056426048
ms.sourcegitcommit: ec293978e951b09903b79e6642aa587824935e0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "49780271"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Le tableau du schéma de recherche avancée contient des informations sur les événements impliquant le traitement des `EmailEvents` e-mails sur Microsoft Defender pour Office 365. [](advanced-hunting-overview.md) Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité. [](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center)

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `EmailId` | chaîne | E-mail et Identificateur de destinataire uniques |
| `NetworkMessageId` | chaîne | Identificateur unique de l’e-mail, généré par Microsoft 365 |
| `InternetMessageId` | chaîne | Identificateur public de l’e-mail défini par le système de courrier d’envoi |
| `SenderMailFromAddress` | chaîne | Adresse e-mail de l’expéditeur dans l’en-tête MAIL FROM, également appelé expéditeur d’enveloppe ou adresse de retour |
| `SenderFromAddress` | chaîne | Adresse e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderMailFromDomain` | chaîne | Domaine de l’expéditeur dans l’en-tête MAIL FROM, également appelé expéditeur d’enveloppe ou adresse de retour |
| `SenderFromDomain` | chaîne | Domaine e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderIPv4` | chaîne | Adresse IPv4 du dernier serveur de messagerie détecté qui a relayé le message |
| `SenderIPv6` | chaîne | Adresse IPv6 du dernier serveur de messagerie détecté qui a relayé le message |
| `RecipientEmailAddress` | chaîne | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `Subject` | chaîne | Objet de l’e-mail |
| `EmailClusterId` | chaîne | Identificateur du groupe des e-mails similaires ordonnés en fonction de l’analyse heuristique de leur contenu. |
| `EmailDirection` | chaîne | Direction de l'e-mail  par rapport à votre réseau : entrant, sortant, intra-organisationnel |
| `DeliveryAction` | chaîne | Action de livraison de l'e-mail : remis, courrier indésirable, bloqué ou remplacé |
| `DeliveryLocation` | chaîne | Emplacement de remise du courrier électronique : boîte de réception/dossier, local/externe, courrier indésirable, quarantaine, échec, supprimé, éléments supprimés |
| `PhishFilterVerdict` | chaîne | Verdict de la pile de filtrage d’e-mails selon que l’e-mail is est phish : Phish ou non Phish |
| `PhishDetectionMethod` | chaîne | Méthode utilisée pour détecter l’e-mail comme un hameçonnage : réputation d’URL malveillante, détonation d’URL de liens sûrs, filtre de hameçonnage avancé, filtre anti-hameçonnage général, anti-usurpation d’identité : intra-organisation, usurpation d’identité : domaine externe, emprunt d’identité de domaine, emprunt d’identité d’utilisateur, emprunt d’identité de marque |
| `MalwareFilterVerdict` | chaîne | Verdict de la pile de filtrage d’e-mails selon que l’e-mail contient des programmes malveillants : programme malveillant, programme non malveillant |
| `MalwareDetectionMethod` | chaîne | Méthode utilisée pour détecter les programmes malveillants dans le courrier électronique : moteur anti-programme malveillant, réputation du fichier, pièces jointes sécurisées |
| `EmailAction` | chaîne | Action finale effectuée sur l’e-mail sur la base du verdict du filtre, des stratégies et des actions des utilisateurs : déplacer le message vers le dossier courrier indésirable, ajouter l’en-tête X, modifier l’objet, rediriger le message, supprimer le message, envoyer à la quarantaine, aucune action entreprise |
| `EmailActionPolicy` | chaîne | Stratégie d’action appliquée : antispam hautement fiable, anti-courrier indésirable, antispam, courrier indésirable de courrier indésirable, emprunt d’identité de domaine anti-hameçonnage, emprunt d’identité d’utilisateur anti-hameçonnage, usurpation d’identité anti-hameçonnage, emprunt d’identité de graphe anti-hameçonnage, anti-programme malveillant, sécurité pièces jointes, règles de transport d’entreprise (ETR) |
| `EmailActionPolicyGuid` | chaîne | Identificateur unique de la stratégie qui a déterminé l’action de courrier finale |
| `AttachmentCount` | int | Nombre de pièces jointes dans l’e-mail. |
| `UrlCount` | int | Nombre d’URL incorporées dans l’e-mail |
| `EmailLanguage` | chaîne | Langue détectée du contenu de l’e-mail |
| `OrgLevelAction` | chaîne | Action entreprise sur le courrier électronique en réponse à des correspondances à une stratégie définie au niveau de l’organisation |
| `OrgLevelPolicy` | chaîne | Stratégie organisationnelle qui a déclenché l’action entreprise sur le courrier électronique |
| `UserLevelAction` | chaîne | Action prise sur le courrier électronique en réponse à des correspondances à une stratégie de boîte aux lettres définie par le destinataire |
| `UserLevelPolicy` | chaîne | Stratégie de boîte aux lettres d’utilisateur final qui a déclenché l’action sur le courrier électronique |
| `Connectors` | chaîne | Instructions personnalisées qui définissent le flux de messagerie de l’organisation et la façon dont le courrier a été acheminé |
| `SenderDisplayName` | chaîne | Nom de l’expéditeur affiché dans le carnet d’adresses, généralement une combinaison d’un prénom ou d’un prénom donné, d’une initiale du deuxième prénom et d’un nom ou d’un nom de famille |
| `SenderObjectId` | chaîne |Identificateur unique du compte de l’expéditeur dans Azure AD |
| `ThreatTypes` | chaîne | Verdict de la pile de filtrage du courrier électronique selon que l’e-mail contient des programmes malveillants, du hameçonnage ou d’autres menaces |
| `ThreatNames` | chaîne |Nom de détection des programmes malveillants ou autres menaces détectées |
| `DetectionMethods` | chaîne | Méthodes utilisées pour détecter les programmes malveillants, le hameçonnage ou d’autres menaces détectées dans l’e-mail |


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
