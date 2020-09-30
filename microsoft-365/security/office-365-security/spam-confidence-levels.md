---
title: Spam confidence level
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur le seuil de probabilité de courrier indésirable (SCL) appliqué aux messages dans Exchange Online Protection (EOP).
ms.openlocfilehash: 51d00b36ae826676f436c0a74617ddbbadf7a30a
ms.sourcegitcommit: 61ef32f802a1fb6d1e3a3aa005764ead32a7951e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "48318239"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Seuil de probabilité de courrier indésirable dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, les messages entrants passent par le filtrage du courrier indésirable dans EOP et reçoivent un score de courrier indésirable. Ce score est mappé à un seuil de probabilité de courrier indésirable (SCL) individuel ajouté au message dans un en-tête X. Un SCL supérieur indique qu’un message est plus susceptible d’être du courrier indésirable. EOP entreprend une action sur le message en fonction de la valeur SCL.

Ce que signifie le SCL et les actions par défaut effectuées sur les messages sont décrites dans le tableau suivant. Pour plus d’informations sur les actions que vous pouvez effectuer sur les messages en fonction du verdict de filtrage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in EOP](configure-your-spam-filter-policies.md).

****

|SCL|Définition|Action par défaut|
|:---:|---|---|
|-1|Le message a ignoré le filtrage du courrier indésirable. Par exemple, le message provient d’un expéditeur approuvé, a été envoyé à un destinataire approuvé ou provient d’un serveur de source de messagerie de la liste verte IP. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans EOP](create-safe-sender-lists-in-office-365.md).|Le message est remis dans la boîte aux lettres des destinataires.|
|0, 1|Filtrage du courrier indésirable déterminé le message n’était pas du courrier indésirable.|Le message est remis dans la boîte aux lettres des destinataires.|
|5, 6|Filtrage du courrier indésirable marqué comme **courrier indésirable**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|9 |Filtrage du courrier indésirable marqué comme message en tant que **courrier de confiance élevée**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|

Vous remarquerez que les seuils SCL 2, 3, 4, 7 et 8 ne sont pas utilisés par le filtrage du courrier indésirable.

Vous pouvez utiliser des règles de flux de messagerie (également appelées règles de transport) pour marquer la valeur SCL des messages. Si vous utilisez une règle de flux de messagerie pour définir le SCL, les valeurs 5 ou 6 déclenchent l’action de filtrage du courrier indésirable pour le courrier **indésirable**, et les valeurs 7, 8 ou 9 déclenchent l’action de filtrage du courrier indésirable pour le courrier indésirable à **confiance élevée**. Pour plus d’informations, consultez [la rubrique utiliser des règles de flux de messagerie pour définir le seuil de probabilité de courrier indésirable (SCL) dans les messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).

À l’instar du SCL, le niveau de réclamation en masse (BCL) identifie un message électronique en masse incorrect (également appelé _courrier gris_). Un niveau BCL supérieur indique qu’un courrier en nombre est susceptible de générer des plaintes (et par conséquent plus susceptible d’être du courrier indésirable). Vous configurez le seuil BCL dans les stratégies anti-courrier indésirable. Pour plus d’informations, reportez-vous à la rubrique [configure anti-spam Policies in EOP](configure-your-spam-filter-policies.md), [Bulk Complaint Level (BCL) in EOP)](bulk-complaint-level-values.md)et [quelle est la différence entre courrier indésirable et courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![Icône rapide pour LinkedIn Learning ](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **New de Microsoft 365 ?** Découvrez les cours vidéo gratuits pour les **administrateurs et les professionnels de Microsoft 365**, qui vous ont été proposés par LinkedIn Learning.
