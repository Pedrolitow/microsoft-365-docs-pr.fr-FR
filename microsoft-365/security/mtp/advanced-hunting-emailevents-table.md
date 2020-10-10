---
title: Tableau EmailEvents dans le schéma de repérage avancé
description: En savoir plus sur les événements associés aux courriers électroniques Microsoft 365 dans le tableau EmailEvents du schéma de chasse avancé
keywords: chasse aux menaces, recherche de menace, recherche sur les menaces informatiques, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, EmailEvents, ID de message réseau, expéditeur, destinataire, ID pièce jointe, nom de la pièce jointe, nombre d’URL
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
- m365-initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 17a7e2ed8e2124bc3ca820cedee7c4f89403d717
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413137"
---
# <a name="emailevents"></a>EmailEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces



Le tableau `EmailEvents` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les événements impliquant le traitement d'e-mails sur Office 365 - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements ( `ActionType` valeurs) pris en charge par un tableau, utilisez la [référence de schéma intégrée](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) disponible dans le centre de sécurité.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `EmailId` | chaîne | E-mail et Identificateur de destinataire uniques |
| `NetworkMessageId` | chaîne | Identificateur unique pour le courrier électronique, généré par Microsoft 365 |
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
| `PhishDetectionMethod` | chaîne | Méthode utilisée pour détecter l'e-mail en tant que Phish : réputation d’URL malveillante, détonation URL de liens fiables ATP, filtre d’hameçonnage avancé, filtre de hameçonnage général, anti-spoof : intra-organisationnel, anti-spoof : domaine externe, emprunt d’identité de domaine, emprunt d’identité d’utilisateur, marque emprunt d’identité |
| `MalwareFilterVerdict` | chaîne | Verdict de la pile de filtrage d’e-mails selon que l’e-mail contient des programmes malveillants : programme malveillant, programme non malveillant |
| `MalwareDetectionMethod` | string | Méthode utilisée pour détecter les programmes malveillants dans le courrier électronique : moteur anti-programme malveillant, réputation de fichier, pièces jointes fiables ATP |
| `FinalEmailAction` | chaîne | Action finale effectuée sur l’e-mail sur la base du verdict du filtre, des stratégies et des actions des utilisateurs : déplacer le message vers le dossier courrier indésirable, ajouter l’en-tête X, modifier l’objet, rediriger le message, supprimer le message, envoyer à la quarantaine, aucune action entreprise |
| `FinalEmailActionPolicy` | chaîne | Stratégie d’action appliquée : antispam hautement fiable, anti-courrier indésirable, antispam, courrier indésirable de courrier indésirable, emprunt d’identité de domaine anti-hameçonnage, emprunt d’identité d’utilisateur anti-hameçonnage, usurpation d’identité anti-hameçonnage, emprunt d’identité de graphe anti-hameçonnage, anti-programme malveillant, sécurité pièces jointes, règles de transport d’entreprise (ETR) |
| `FinalEmailActionPolicyGuid` | chaîne | Identificateur unique de la stratégie qui a déterminé l’action de courrier finale |
| `AttachmentCount` | int | Nombre de pièces jointes dans l’e-mail. |
| `UrlCount` | int | Nombre d’URL incorporées dans l’e-mail |
| `EmailLanguage` | chaîne | Langue détectée du contenu de l’e-mail |

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Rechercher sur les appareils, les emails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
