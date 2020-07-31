---
title: Threading de courrier électronique-eDiscovery
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
ms.assetid: ''
description: Lors de la réalisation d’une analyse eDiscovery avancée, le Threading de messagerie analyse une conversation électronique et sépare chaque message en différentes catégories.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e6072650a07f634b8dc19a013907eb36469c443b
ms.sourcegitcommit: 6501e01a9ab131205a3eef910e6cea7f65b3f010
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2020
ms.locfileid: "46527672"
---
# <a name="email-threading"></a>Threading de messagerie

Considérez une conversation par courrier électronique qui s’est en cours pendant un certain temps. Dans la plupart des cas, le dernier courrier électronique sur le thread inclura le contenu de tous les messages électroniques précédents ; en examinant le dernier courrier électronique, vous obtiendrez un contexte complet de la conversation qui s’est produite dans le fil de discussion. Le Threading de messagerie identifie ces messages afin que les réviseurs puissent examiner une partie des documents collectés sans perdre de contexte.

## <a name="what-does-email-threading-do"></a>Qu’est-ce que le Threading du courrier électronique ?

Le Threading de messagerie analyse chaque message électronique et les construit sur des messages individuels ; chaque message électronique est une chaîne de messages individuels. Ensuite, il analyse tous les messages électroniques de l’ensemble de vérification pour déterminer si un e-mail a un contenu unique ou si la chaîne est entièrement contenue dans un autre message électronique. Dans les messages électroniques finaux se répartissent en quatre catégories :

- **Conversation complète** : le dernier message présente un contenu unique. Le courrier inclut toutes les pièces jointes ajoutées aux autres messages dont le contenu est entièrement disponible dans ce courrier.

- **Conversation complète moins pièce jointe** : le dernier message présente un contenu unique. Toutefois, le courrier n’inclut pas certaines pièces jointes ajoutées aux autres messages dont le contenu est entièrement disponible dans ce courrier.

- **Copie complète** : copie exacte d’une conversation complète ou conversation complète moins pièce jointe.

- **Aucune** : le contenu du message est inclus entièrement dans au moins un courrier marqué comme conversation complète ou conversation complète moins pièce jointe.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>Quelle est la différence entre les conversations dans Outlook ?

En un clin d’œil, cela ressemble aux groupements de conversation dans Outlook. Toutefois, il existe des distinctions importantes. Considérez une conversation par courrier électronique qui a été divisée en deux conversations ; par exemple, quelqu’un a répondu à un message électronique qui n’est pas le dernier de la conversation, les deux derniers messages de la conversation ont un contenu unique.

Outlook regroupera les messages électroniques en une seule conversation ; la lecture du dernier courrier électronique ne signifie pas qu’il manque le contexte de l’avant-dernier e-mail, qui contient également du contenu unique. Étant donné que le Threading de messagerie analyse chaque courrier électronique dans des composants individuels et les compare, le Threading de messagerie marque les deux derniers courriers électroniques en s’assurant que vous ne manquez pas de contexte tant que vous lisez tous les messages électroniques marqués comme inclus.
