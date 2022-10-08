---
title: Table EmailPostDeliveryEvents dans le schéma de chasse avancé
description: En savoir plus sur les actions post-remise effectuées sur les e-mails Microsoft 365 dans la table EmailPostDeliveryEvents du schéma de chasse avancé
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, référence de schéma, kusto, table, colonne, type de données, description, EmailPostDeliveryEvents, ID de message réseau, expéditeur, destinataire, ID de pièce jointe, nom de pièce jointe, verdict de logiciel malveillant, verdict de hameçonnage, nombre de pièces jointes, nombre de liens, nombre d’URL
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
ms.collection:
- m365-security
- tier3
ms.topic: article
ms.openlocfilehash: 6fc2e43b0e7be9534b9065420f017af678ea4d31
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091364"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour Office 365

Le `EmailPostDeliveryEvents` tableau du schéma [de repérage avancé](advanced-hunting-overview.md) contient des informations sur les actions post-remise effectuées sur les messages électroniques traités par Microsoft 365. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (`ActionType` valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible dans Defender pour cloud.

Pour obtenir plus d’informations sur les messages électroniques individuels, vous pouvez également utiliser les [`EmailEvents`](advanced-hunting-emailevents-table.md)tables , [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md)et les [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) tables. Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Date et heure d’enregistrement de l’événement |
| `NetworkMessageId` | `string` | Identificateur unique de l’e-mail, généré par Microsoft 365 |
| `InternetMessageId` | `string` | Identificateur public de l’e-mail défini par le système de courrier d’envoi |
| `Action` | `string` | Action effectuée sur l’entité |
| `ActionType` | `string` | Type d’activité qui a déclenché l’événement : Correction manuelle, Phish ZAP, Malware ZAP |
| `ActionTrigger` | `string` | Indique si une action a été déclenchée par un administrateur (manuellement ou par le biais de l’approbation d’une action automatisée en attente) ou par un mécanisme spécial, tel qu’un ZAP ou une livraison dynamique |
| `ActionResult` | `string` | Résultat de l’action |
| `RecipientEmailAddress` | `string` | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `DeliveryLocation` | `string` | Emplacement de remise du courrier électronique : boîte de réception/dossier, local/externe, courrier indésirable, quarantaine, échec, supprimé, éléments supprimés |
| `ReportId` | `long` | Identificateur d’événement basé sur un compteur extensible. Pour identifier les événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |
| `ThreatTypes` | `string` | Verdict de la pile de filtrage d’e-mail indiquant si l’e-mail contient des programmes malveillants, du hameçonnage ou d’autres menaces |
| `DetectionMethods` | `string` | Méthodes utilisées pour détecter les programmes malveillants, le hameçonnage ou d’autres menaces détectées dans l’e-mail |

## <a name="supported-event-types"></a>Types d’événements pris en charge
Ce tableau capture les événements avec les valeurs suivantes :`ActionType`

- **Correction manuelle** : un administrateur a pris manuellement des mesures sur un e-mail une fois qu’il a été remis à la boîte aux lettres de l’utilisateur. Cela inclut les actions effectuées manuellement par le biais de [l’Explorateur de menaces](../office-365-security/threat-explorer.md) ou des approbations [d’actions d’investigation et de réponse automatisées (AIR](m365d-autoir-actions.md)).
- **Phish ZAP** – [Le vidage automatique de zéro heure (ZAP)](../office-365-security/zero-hour-auto-purge.md) a pris des mesures sur un e-mail de hameçonnage après la remise.
- **Programme malveillant ZAP** – Le vidage automatique de zéro heure (ZAP) a pris des mesures sur un e-mail trouvé contenant des programmes malveillants après la remise.

## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
