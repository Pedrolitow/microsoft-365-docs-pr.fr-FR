---
title: Table EmailAttachmentInfo dans le schéma de repérage avancé
description: En savoir plus sur les informations sur les pièces jointes dans la table EmailAttachmentInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, EmailAttachmentInfo, ID de message réseau, expéditeur, destinataire, ID de pièce jointe, nom de pièce jointe, verdict de logiciel malveillant
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
ms.openlocfilehash: e787f79b5af90f45dd2823f53402830c7fc287db
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664037"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Le `EmailAttachmentInfo` tableau du schéma [de chasse avancé](advanced-hunting-overview.md) contient des informations sur les pièces jointes sur les e-mails traités par Microsoft Defender pour Office 365. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `NetworkMessageId` | `string` | Identificateur unique de l’e-mail, généré par Microsoft 365 |
| `SenderFromAddress` | `string` | Adresse e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `SenderDisplayName` | `string` | Nom de l’expéditeur affiché dans le carnet d’adresses, généralement une combinaison d’un prénom ou d’un prénom donné, d’une initiale intermédiaire et d’un nom ou d’un nom de famille |
| `SenderObjectId` | `string` | Identificateur unique du compte de l’expéditeur dans Azure AD |
| `RecipientEmailAddress` | `string` | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `RecipientObjectId` | `string` | Identificateur unique du destinataire de l’e-mail dans Azure AD |
| `FileName` | `string` | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FileType` | `string` | Type d’extension de fichier |
| `SHA256` | `string` | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `ThreatTypes` | `string` | Verdict de la pile de filtrage d’e-mail indiquant si l’e-mail contient des programmes malveillants, du hameçonnage ou d’autres menaces |
| `ThreatNames` | `string` | Nom de détection des programmes malveillants ou autres menaces détectées |
| `DetectionMethods` | `string` | Méthodes utilisées pour détecter les programmes malveillants, le hameçonnage ou d’autres menaces détectées dans l’e-mail |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `FileSize` | `string` | Taille du fichier en octets |

## <a name="related-topics"></a>Voir aussi

- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
