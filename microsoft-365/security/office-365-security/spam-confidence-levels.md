---
title: Seuil de probabilité de courrier indésirable (SCL)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent en savoir plus sur la façon dont le seuil de probabilité de courrier indésirable détermine la probabilité ou le courrier indésirable d’un message, ainsi que les actions par défaut que le filtrage du courrier indésirable effectue sur les messages basés sur le SCL.
ms.openlocfilehash: 519bc48e7285283ad0570b8f3ac598615b132875
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43638283"
---
# <a name="spam-confidence-level-scl-in-office-365"></a>Niveau de probabilité de courrier indésirable (SCL) dans Office 365

Lorsque Microsoft 365 (Exchange Online ou une version autonome d’Exchange Online Protection (EOP) sans boîte aux lettres Exchange Online) reçoit un message électronique entrant, le message passe par le filtrage du courrier indésirable et reçoit un score de courrier indésirable. Ce score est mappé à un seuil de probabilité de courrier indésirable (SCL) individuel ajouté au message dans un en-tête X. Un SCL supérieur indique qu’un message est plus susceptible d’être du courrier indésirable. Le service entreprend une action sur le message en fonction de la valeur SCL.

Ce que signifie le SCL et les actions par défaut effectuées sur les messages sont décrites dans le tableau suivant. Pour plus d’informations sur les actions que vous pouvez effectuer sur les messages en fonction du verdict de filtrage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in Office 365](configure-your-spam-filter-policies.md).

||||
|:---:|---|---|
|**SCL**|**Définition**|**Action par défaut**|
|-1|Le message a ignoré le filtrage du courrier indésirable. Par exemple, le message provient d’un expéditeur approuvé, a été envoyé à un destinataire approuvé ou provient d’un serveur de source de messagerie de la liste verte IP. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md).|Le message est remis dans la boîte aux lettres des destinataires.|
|0, 1|Filtrage du courrier indésirable déterminé le message n’était pas du courrier indésirable.|Le message est remis dans la boîte aux lettres des destinataires.|
|5, 6|Filtrage du courrier indésirable marqué comme **courrier indésirable**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|9 |Filtrage du courrier indésirable marqué comme message en tant que **courrier de confiance élevée**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|

Vous remarquerez que les seuils SCL 2, 3, 4, 7 et 8 ne sont pas utilisés par le filtrage du courrier indésirable.

Vous pouvez utiliser des règles de flux de messagerie (également appelées règles de transport) pour marquer la valeur SCL des messages. Si vous utilisez une règle de flux de messagerie pour définir le SCL, les valeurs 5 ou 6 déclenchent l’action de filtrage du courrier indésirable pour le courrier **indésirable**, et les valeurs 7, 8 ou 9 déclenchent l’action de filtrage du courrier indésirable pour le courrier indésirable à **confiance élevée**. Pour plus d’informations, consultez [la rubrique utiliser des règles de flux de messagerie pour définir le seuil de probabilité de courrier indésirable (SCL) dans les messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).

À l’instar du SCL, le niveau de réclamation en masse (BCL) identifie un message électronique en masse incorrect (également appelé _courrier gris_). Une BCL plus élevée indique qu’un message électronique en nombre est susceptible de générer des plaintes (et, par conséquent, plus vraisemblablement un courrier indésirable). Vous configurez le seuil BCL dans les stratégies anti-courrier indésirable. Pour plus d’informations, consultez la rubrique [configure anti-spam Policies in office 365](configure-your-spam-filter-policies.md), [Bulk Complaint Level (BCL) in Office 365)](bulk-complaint-level-values.md)et [quelle est la différence entre le courrier indésirable et le courrier électronique en masse ?](what-s-the-difference-between-junk-email-and-bulk-email.md).

||
|:-----|
|![Icône rapide pour LinkedIn Learning](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Vous débutez avec Office 365 ?**         Découvrez les cours vidéo gratuits pour les **administrateurs et les professionnels de Microsoft 365**, qui vous ont été proposés par LinkedIn Learning.|
