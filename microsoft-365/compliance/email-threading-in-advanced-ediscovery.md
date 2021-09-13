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
ms.openlocfilehash: b087bfc84175f80daaf1c0d2f1394584a70757ac
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59207916"
---
# <a name="email-threading-in-advanced-ediscovery"></a>Threads de messagerie dans Advanced eDiscovery

Envisagez une conversation par courrier électronique qui se passe depuis un certain temps. Dans la plupart des cas, le dernier e-mail sur le thread inclut le contenu de tous les e-mails précédents ; La révision du dernier e-mail donne un contexte complet de la conversation qui s’est produite dans le thread. Le thread de messagerie identifie ces e-mails afin que les réviseurs peuvent examiner une fraction des documents collectés sans perdre de contexte.

## <a name="what-does-email-threading-do"></a>Que fait le thread de messagerie ?

Le thread de courrier électronique pare chaque e-mail et le déconstruit dans des messages individuels . chaque e-mail est une chaîne de messages individuels. Ensuite, il analyse tous les e-mails du jeu à réviser pour déterminer si un e-mail a un contenu unique ou si la chaîne est entièrement contenue dans un autre e-mail. Au final, les messages électroniques sont répartis en quatre catégories :

- **Conversation complète** : le dernier message présente un contenu unique. Le courrier inclut toutes les pièces jointes ajoutées aux autres messages dont le contenu est entièrement disponible dans ce courrier.

- **Conversation complète moins pièce jointe** : le dernier message présente un contenu unique. Toutefois, le courrier n’inclut pas certaines pièces jointes ajoutées aux autres messages dont le contenu est entièrement disponible dans ce courrier.

- **Copie complète** : copie exacte d’une conversation complète ou conversation complète moins pièce jointe.

- **Aucune** : le contenu du message est inclus entièrement dans au moins un courrier marqué comme conversation complète ou conversation complète moins pièce jointe.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>En quoi cela est-il différent des conversations Outlook ?

En un coup d’œil, cela ressemble aux regroupements de conversation Outlook. Toutefois, il existe certaines distinctions importantes. Envisagez une conversation par courrier électronique qui a été transformée en deux conversations ; Par exemple, quelqu’un a répondu à un e-mail qui n’est pas le dernier de la conversation, de sorte que les deux derniers e-mails de la conversation ont tous deux un contenu unique.

Outlook grouperait toujours les e-mails dans une seule conversation . lire uniquement le dernier e-mail signifierait qu’il manque le contexte de l’avant-dernier e-mail, qui contient également un contenu unique. Étant donné que le thread de courrier électronique pare chaque message électronique en composants individuels et les compare, le thread de messagerie marque les deux derniers messages comme étant inclus, ce qui garantit que vous ne manquez aucun contexte tant que vous lisez tous les messages marqués comme étant inclus.
