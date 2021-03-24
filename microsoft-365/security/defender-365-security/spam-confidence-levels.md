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
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur le niveau de confiance du courrier indésirable (SCL) appliqué aux messages dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 951bbcb5fcbcc7b7916ee1c34c4ab489d54b6667
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51064457"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Niveau de confiance du courrier indésirable (SCL) dans EOP

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les messages entrants sont filtrés par le filtrage du courrier indésirable dans EOP et un score de courrier indésirable leur est attribué. Ce score est mappé à un niveau de confiance de courrier indésirable (SCL) individuel qui est ajouté au message dans un en-tête X. Un SCL plus élevé indique qu’un message est plus susceptible d’être du courrier indésirable. EOP prend des mesures sur le message en fonction du SCL.

Ce que signifie le SCL et les actions par défaut qui sont prises sur les messages sont décrits dans le tableau suivant. Pour plus d’informations sur les actions que vous pouvez prendre sur les messages en fonction du verdict de filtrage du courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

****

|SCL|Définition|Action par défaut|
|:---:|---|---|
|-1|Le message a ignoré le filtrage du courrier indésirable. Par exemple, le message est provenant d’un expéditeur fiable, a été envoyé à un destinataire fiable ou à partir d’un serveur source de messagerie sur la liste d’adresses IP permises. Pour plus d’informations, voir [Créer des listes d’expéditeurs sûrs dans EOP.](create-safe-sender-lists-in-office-365.md)|Le message est remis dans la boîte aux lettres des destinataires.|
|0, 1|Le filtrage du courrier indésirable a déterminé que le message n’était pas du courrier indésirable.|Le message est remis dans la boîte aux lettres des destinataires.|
|5, 6|Le filtrage du courrier indésirable a marqué le message comme **courrier indésirable**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|9 |Le filtrage du courrier indésirable a marqué le message comme courrier indésirable **à niveau de confiance élevé**|Le message est envoyé vers le dossier Courrier indésirable des destinataires.|
|

Vous remarquerez que les SCL 2, 3, 4, 7 et 8 ne sont pas utilisés par le filtrage du courrier indésirable.

Vous pouvez utiliser des règles de flux de messagerie (également appelées règles de transport) pour marquer le SCL sur les messages. Si vous utilisez une règle de flux de messagerie pour définir le SCL, les valeurs 5 ou 6 déclenchent l’action de filtrage du courrier indésirable **et** les valeurs 7, 8 ou 9 déclenchent l’action de filtrage du courrier indésirable pour le courrier indésirable à niveau de confiance **élevé.** Pour plus d’informations, voir Utiliser des règles de flux de messagerie pour définir le niveau de confiance du courrier indésirable [(SCL) dans les messages.](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)

Comme pour le SCL, le niveau de réclamation en bloc (BCL) identifie les messages électroniques en masse (également appelés _messages gris)._ Un niveau BCL supérieur indique qu’un courrier en nombre est susceptible de générer des plaintes (et par conséquent plus susceptible d’être du courrier indésirable). Vous configurez le seuil BCL dans les stratégies anti-courrier indésirable. Pour plus d’informations, voir [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md), [Bulk complaint level (BCL) in EOP)](bulk-complaint-level-values.md)et [What’s the difference between junk email and bulk email?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![L’icône courte pour LinkedIn Learning ](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **New to Microsoft 365 ?** Découvrez les cours vidéo gratuits pour les **administrateurs Microsoft 365** et les professionnels de l’informatique, présentés par LinkedIn Learning.
