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
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 9d015a0d-52a0-484d-9a08-121d04f973d3
ms.custom:
- seo-marvel-apr2020
description: Trouvez des réponses aux questions les plus fréquentes sur les messages qui ont été mis en file d’attente, différés ou retournés lors du processus de filtrage Exchange Online Protection (EOP).
ms.openlocfilehash: 76fe08f3a83321b6c0549dae5f1382ead5f0b3ae
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46827748"
---
# <a name="eop-queued-deferred-and-bounced-messages-faq"></a>Questions fréquemment posées sur les messages mis en file d’attente, différés et retournés dans EOP

Cette rubrique fournit des réponses aux questions fréquemment posées sur les messages mis en file d’attente, différés ou retournés lors du processus de filtrage Exchange Online Protection (EOP).

## <a name="why-is-mail-queuing"></a>Pourquoi le courrier électronique est-il mis en file d’attente ?

Les messages sont mis en file d'attente ou différés si le service n'est pas en mesure d'établir une connexion au serveur du destinataire en vue de la remise. Les messages ne sont pas différés si le réseau du destinataire renvoie une erreur de la série 500.

## <a name="how-does-a-message-become-deferred"></a>Dans quelles circonstances un message est-il différé ?

Les messages sont retenus s'il est impossible d'établir une connexion au serveur du destinataire et que celui-ci renvoie une « défaillance temporaire », comme une expiration de connexion, un refus de connexion ou une erreur de la série 400. En cas de défaillance permanente, comme une erreur de la série 500, le message est renvoyé à l'expéditeur.

## <a name="how-long-does-a-message-remain-in-deferral-and-what-is-the-retry-interval"></a>Combien de temps un message reste-t-il en attente et quel est l’intervalle des nouvelles tentatives ?

Les messages en différé resteront dans nos files d’attente pendant 1 jour. Les nouvelles tentatives d'envoi de message sont basées sur les erreurs que nous recevons à partir du système de messagerie du destinataire. Les premiers nombre de retards sont 15 minutes ou moins, avec les nouvelles tentatives suivantes (au cours d’une demi-douzaine ou par conséquent), ce qui augmente l’intervalle entre plusieurs tentatives et une durée maximale de 60 minutes. L’expansion de la durée de l’intervalle est dynamique, en prenant en compte plusieurs variables telles que les tailles de file d’attente et la priorité des messages internes. En standard, il faut 15 minutes (ou moins) pour commencer, puis les prochaines heures à 60 mins max.

## <a name="after-your-email-server-is-restored-how-are-queued-messages-distributed"></a>Après la restauration du serveur de messagerie, comment les messages mis en file d’attente sont-ils distribués ?

Une fois que votre serveur de messagerie est restauré, tous les messages mis en file d'attente sont automatiquement traités dans l'ordre dans lequel ils ont été reçus et mis en file d'attente lorsque le serveur est devenu indisponible.
