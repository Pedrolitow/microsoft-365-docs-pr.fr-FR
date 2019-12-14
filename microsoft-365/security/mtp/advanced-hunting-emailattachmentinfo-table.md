---
title: Table EmailAttachmentInfo dans le schéma de repérage avancé
description: En savoir plus sur les informations sur les pièces jointes dans la table EmailAttachmentInfo du schéma de repérage avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, EmailAttachmentInfo, ID de message réseau, expéditeur, destinataire, ID pièce jointe, nom de la pièce jointe, classement des programmes malveillants
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 9f6a4aa68826133bee0437116b2fbf3fde4e7e00
ms.sourcegitcommit: 0c9c28a87201c7470716216d99175356fb3d1a47
ms.translationtype: MT + HT Review
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2019
ms.locfileid: "39911023"
---
# <a name="emailattachmentinfo"></a>EmailAttachmentInfo

**S’applique à :**
- Protection Microsoft contre les menaces

[!include[Prerelease information](prerelease.md)]

La table `EmailAttachmentInfo` dans le schéma de [repérage avancé](advanced-hunting-overview.md) contient des informations sur les pièces jointes des e-mails traités par Office 365 - Protection avancée contre les menaces. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `EventTime` | DateHeure | Date et heure d’enregistrement de l’événement |
| `AttachmentId` | string | Identificateur de pièces jointes uniques à un e-mail |
| `NetworkMessageId` | string | Identificateur unique d’e-mail, généré par Office 365 |
| `SenderFromAddress` | string | Adresse e-mail de l’expéditeur dans l’en-tête DE, visible par les destinataires de l’e-mail sur leurs clients de messagerie |
| `RecipientEmailAddress` | string | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `FileName` | string | Nom du fichier auquel l’action enregistrée a été appliquée |
| `FileType` | string | Type d’extension de fichier |
| `SHA256` | string | SHA-256 du fichier auquel l’action enregistrée a été appliquée. Ce champ n’est généralement pas rempli. Utilisez la colonne SHA1 lorsque celle-ci est disponible. |
| `MalwareFilterVerdict` | string | Verdict de la pile de filtrage d’e-mails selon que l’e-mail contient des programmes malveillants : programme malveillant, programme non malveillant |
| `MalwareDetectionMethod` | string | Méthode utilisée pour détecter les programmes malveillants dans le courrier électronique : moteur anti-programme malveillant, réputation de fichier, pièces jointes fiables ATP |

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)