---
title: Table EmailAttachmentInfo dans le schéma de repérage avancé
description: En savoir plus sur les informations sur les pièces jointes dans la table EmailAttachmentInfo du schéma de repérage avancé
keywords: chasse avancée, recherche de menace, recherche dans les menaces informatiques, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, référence de schéma, Kusto, table, colonne, type de données, description, EmailAttachmentInfo, ID de message réseau, expéditeur, destinataire, ID de pièce jointe, nom de la pièce jointe, verdict de programmes malveillants
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
mms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.openlocfilehash: 6d88303b34f78abc857e9aec749bf2f58090f43a
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49667648"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Le `EmailAttachmentInfo` tableau du schéma de [chasse avancé](advanced-hunting-overview.md) contient des informations sur les pièces jointes des courriers électroniques traités par Microsoft defender pour Office 365. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AttachmentId` | string | Identificateur de pièces jointes uniques à un e-mail |
| `NetworkMessageId` | string | Identificateur unique pour le courrier électronique, généré par Microsoft 365 |
| `SenderFromAddress` | string | Adresse e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `RecipientEmailAddress` | string | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FileType` | string | Type d’extension de fichier |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MalwareFilterVerdict` | string | Verdict de la pile de filtrage d’e-mails selon que l’e-mail contient des programmes malveillants : programme malveillant, programme non malveillant |
| `MalwareDetectionMethod` | string | Méthode utilisée pour détecter les programmes malveillants dans le courrier électronique : moteur anti-programme malveillant, réputation de fichier, pièces jointes fiables |
| `SenderDisplayName` | string | Nom de l’expéditeur affiché dans le carnet d’adresses, généralement une combinaison d’un prénom, d’une initiale de deuxième prénom et d’un nom de famille ou nom. |
| `SenderObjectId` | string | Identificateur unique du compte de l’expéditeur dans Azure AD |
| `ThreatTypes` | string | Verdict de la pile de filtrage du courrier électronique indiquant si l’e-mail contient des programmes malveillants, le hameçonnage ou d’autres menaces |
| `ThreatNames` | string | Nom de détection pour les programmes malveillants ou autres menaces détectées |

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
