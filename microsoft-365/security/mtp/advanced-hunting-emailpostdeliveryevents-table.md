---
title: Table EmailPostDeliveryEvents dans le schéma de recherche avancé
description: En savoir plus sur les actions de post-remise prises sur les e-mails Microsoft 365 dans la table EmailPostDeliveryEvents du schéma de recherche avancé
keywords: advanced hunting, threat hunting, cyber threat hunting, microsoft threat protection, microsoft 365, mtp, m365, search, query, telemetry, schema reference, kusto, table, column, data type, description, EmailPostDeliveryEvents, network message id, sender, recipient, attachment id, attachment id, attachment name, malware verdict, phishing verdict, attachment count, link count, url count
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
ms.technology: m365d
ms.openlocfilehash: 774676e15e9018b13674149b6a2e147a91000814
ms.sourcegitcommit: 005028af7c5a6b2e95f17a0037958131484d9e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "50145498"
---
# <a name="emailpostdeliveryevents"></a>EmailPostDeliveryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Le tableau du schéma de recherche avancée contient des informations sur les actions de post-remise prises sur les messages électroniques traitées `EmailPostDeliveryEvents` par Microsoft [](advanced-hunting-overview.md) 365. Utilisez cette référence pour créer des requêtes qui renvoient des informations de cette table.

>[!TIP]
> Pour plus d’informations sur les types d’événements (valeurs) pris en charge par une table, utilisez la référence de schéma intégrée disponible `ActionType` dans le centre de sécurité. [](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center)

Pour obtenir plus d’informations sur les messages électroniques individuels, vous pouvez également utiliser les tableaux , et les [`EmailEvents`](advanced-hunting-emailevents-table.md) [`EmailAttachmentInfo`](advanced-hunting-emailattachmentinfo-table.md) [`EmailUrlInfo`](advanced-hunting-emailurlinfo-table.md) tableaux. Pour plus d’informations sur les autres tables du schéma de repérage avancé, [consultez la référence de repérage avancé](advanced-hunting-schema-tables.md).

| Nom de colonne | Type de données | Description |
|-------------|-----------|-------------|
| `Timestamp` | DateHeure | Date et heure d’enregistrement de l’événement |
| `NetworkMessageId` | string | Identificateur unique de l’e-mail, généré par Microsoft 365 |
| `InternetMessageId` | chaîne | Identificateur public de l’e-mail défini par le système de courrier d’envoi |
| `Action` | chaîne | Action entreprise sur l’entité |
| `ActionType` | string | Type d’activité qui a déclenché l’événement : correction manuelle, HAMEÇON ZAP, Programme malveillant ZAP |
| `ActionTrigger` | string | Indique si une action a été déclenchée par un administrateur (manuellement ou par le biais de l’approbation d’une action automatisée en attente) ou par un mécanisme spécial, tel qu’une ZAP ou une remise dynamique |
| `ActionResult` | string | Résultat de l’action |
| `RecipientEmailAddress` | string | Adresse e-mail du destinataire ou adresse e-mail du destinataire après extension de la liste de distribution |
| `DeliveryLocation` | chaîne | Emplacement de remise du courrier électronique : boîte de réception/dossier, local/externe, courrier indésirable, quarantaine, échec, supprimé, éléments supprimés |
| `ReportId` | long | Identificateur d’événement basé sur un compteur extensible. Pour identifier des événements uniques, cette colonne doit être utilisée conjointement avec les colonnes DeviceName et Timestamp. |

## <a name="supported-event-types"></a>Types d’événements pris en charge
Ce tableau capture les événements avec les valeurs `ActionType` suivantes :

- **Correction manuelle** : un administrateur a manuellement pris des mesures sur un message électronique après sa remise à la boîte aux lettres de l’utilisateur. Cela inclut les actions entreprises manuellement via [l’Explorateur](../office-365-security/threat-explorer.md) de menaces ou les approbations d’actions d’investigation et de [réponse automatisées (AIR).](mtp-autoir-actions.md)
- **ZAP d’hameçonnage** : la purge automatique d’heure zéro [(ZAP)](../office-365-security/zero-hour-auto-purge.md) a pris des mesures sur un e-mail de hameçonnage après la remise.
- **ZAP anti-programme** malveillant : la purge automatique d’heure zéro (ZAP) a pris des mesures sur un message électronique détecté contenant un programme malveillant après la remise.

## <a name="related-topics"></a>Rubriques connexes
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser des requêtes partagées](advanced-hunting-shared-queries.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
