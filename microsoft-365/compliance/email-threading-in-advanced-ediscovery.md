---
title: Threads de messagerie dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Lorsque vous effectuez une analyse Advanced eDiscovery, le thread de messagerie analyse une conversation par courrier électronique et sépare chaque message en différentes catégories.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: feb0294b47e01eae6849835e92e390a912558c71
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59357449"
---
# <a name="email-threading-in-advanced-ediscovery"></a>Threads de messagerie dans Advanced eDiscovery

Envisagez une conversation par courrier électronique qui se passe depuis un certain temps. Dans la plupart des cas, le dernier message du thread de messagerie inclut le contenu de tous les messages précédents. Par conséquent, la révision du dernier message donne un contexte complet de la conversation qui s’est produite dans le thread. Le thread de messagerie identifie ces messages afin que les réviseurs peuvent examiner une fraction des documents collectés sans perdre de contexte.

## <a name="what-does-email-threading-do"></a>Que fait le thread de messagerie ?

Le thread de messagerie électronique parse chaque thread de messagerie et le déconstruit en messages individuels. Chaque thread de messagerie est une chaîne de messages individuels. Advanced eDiscovery analyse tous les courriers indésirables dans le jeu à réviser pour déterminer si un message électronique a un contenu unique ou si la chaîne (messages parents) est entièrement contenue dans le message final dans le thread de messagerie. Les messages électroniques sont divisés en quatre valeurs inclusives :

- **Inclusive**: un message *électronique inclus* est le dernier message électronique d’un thread de messagerie et contient tout le contenu précédent de ce thread de messagerie.

- **Inclus moins :** un message électronique est désigné comme étant inclus *moins* s’il existe une ou plusieurs pièces jointes associées au message spécifique dans le thread de messagerie. Un réviseur peut utiliser la valeur moins inclusive pour déterminer quel message électronique spécifique au sein du thread a des pièces jointes associées. 

- **Copie inclusive :** un message  électronique est considéré comme une copie inclusive s’il s’agit d’une copie exacte d’un message inclusive ou inclusive moins. 

- **Aucun**: la valeur *None* indique que le contenu du message est entièrement contenu dans au moins un autre message électronique marqué comme inclusive ou inclusive moins.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>En quoi cela est-il différent des conversations Outlook ?

En un coup d’œil, cela ressemble aux regroupements de conversation Outlook. Toutefois, il existe certaines distinctions importantes. Envisagez une conversation par courrier électronique qui a été transformée en deux conversations ; Par exemple, quelqu’un a répondu à un e-mail qui n’est pas le dernier de la conversation, de sorte que les deux derniers e-mails de la conversation ont tous deux un contenu unique.

Outlook grouperait toujours les e-mails dans une seule conversation . lire uniquement le dernier e-mail signifierait qu’il manque le contexte de l’avant-dernier e-mail, qui contient également un contenu unique. Étant donné que le thread de courrier électronique pare chaque message électronique en composants individuels et les compare, le thread de messagerie marque les deux derniers messages comme étant inclus, ce qui garantit que vous ne manquez aucun contexte tant que vous lisez tous les messages marqués comme étant inclus.
