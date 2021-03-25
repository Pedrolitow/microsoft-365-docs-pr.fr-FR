---
title: Questions fréquemment posées sur les messages mis en file d'attente, différés et retournés dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: troubleshooting
localization_priority: Normal
ms.assetid: 9d015a0d-52a0-484d-9a08-121d04f973d3
ms.custom:
- seo-marvel-apr2020
description: Trouvez des réponses aux questions les plus fréquentes sur les messages mis en file d’attente, différés ou renvoyés au cours du processus de filtrage Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c7b5ba595e9a6401efd1b733c9e5a11c8a966037
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204827"
---
# <a name="eop-queued-deferred-and-bounced-messages-faq"></a>Questions fréquemment posées sur les messages mis en file d’attente, différés et retournés dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Cette rubrique fournit des réponses aux questions fréquemment posées sur les messages mis en file d’attente, différés ou renvoyés pendant le processus de filtrage Exchange Online Protection (EOP).

## <a name="why-is-mail-queuing"></a>Pourquoi le courrier électronique est-il mis en file d’attente ?

Les messages sont mis en file d'attente ou différés si le service n'est pas en mesure d'établir une connexion au serveur du destinataire en vue de la remise. Les messages ne sont pas différés si le réseau du destinataire renvoie une erreur de la série 500.

## <a name="how-does-a-message-become-deferred"></a>Dans quelles circonstances un message est-il différé ?

Les messages sont retenus s'il est impossible d'établir une connexion au serveur du destinataire et que celui-ci renvoie une « défaillance temporaire », comme une expiration de connexion, un refus de connexion ou une erreur de la série 400. En cas de défaillance permanente, comme une erreur de la série 500, le message est renvoyé à l'expéditeur.

## <a name="how-long-does-a-message-remain-in-deferral-and-what-is-the-retry-interval"></a>Combien de temps un message reste-t-il en attente et quel est l’intervalle des nouvelles tentatives ?

Les messages en attente resteront dans nos files d’attente pendant 1 jour. Les nouvelles tentatives d'envoi de message sont basées sur les erreurs que nous recevons à partir du système de messagerie du destinataire. Les premiers reports sont de 15 minutes ou moins, avec des tentatives suivantes (sur la demi-dizaine suivante) augmentant l’intervalle sur plusieurs tentatives jusqu’à un maximum de 60 minutes. L’expansion de la durée d’intervalle est dynamique, en tenant compte de plusieurs variables telles que la taille des files d’attente et la priorité des messages internes. En base, il faut 15 minutes (ou moins) pour commencer, puis développer à partir de là au cours des prochaines heures à 60 minutes max.

## <a name="after-your-email-server-is-restored-how-are-queued-messages-distributed"></a>Après la restauration du serveur de messagerie, comment les messages mis en file d’attente sont-ils distribués ?

Une fois que votre serveur de messagerie est restauré, tous les messages mis en file d'attente sont automatiquement traités dans l'ordre dans lequel ils ont été reçus et mis en file d'attente lorsque le serveur est devenu indisponible.
