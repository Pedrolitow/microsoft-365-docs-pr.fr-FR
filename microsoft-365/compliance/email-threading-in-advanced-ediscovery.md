---
title: Thread d’e-mail dans eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Lors d’une analyse eDiscovery (Premium), le thread de messagerie analyse une conversation e-mail et sépare chaque message en différentes catégories.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e35ffa901bb1b90b0ac5d572b6a7ee05cce31d89
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65086806"
---
# <a name="email-threading-in-ediscovery-premium"></a>Thread d’e-mail dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Envisagez une conversation par e-mail qui se passe depuis un certain temps. Dans la plupart des cas, le dernier message du thread d’e-mail inclut le contenu de tous les messages précédents. Par conséquent, l’examen du dernier message donne un contexte complet de la conversation qui s’est produite dans le thread. Le threading d’e-mail identifie ces messages afin que les réviseurs puissent passer en revue une fraction des documents collectés sans perdre de contexte.

## <a name="what-does-email-threading-do"></a>Que fait le thread d’e-mail ?

Le thread d’e-mail analyse chaque thread de messagerie et le décompose en messages individuels. Chaque thread de messagerie est une chaîne de messages individuels. Microsoft Purview eDiscovery (Premium) analyse tous les messages électroniques dans l’ensemble de révision pour déterminer si un message électronique a un contenu unique ou si la chaîne (messages parents) est entièrement contenue dans le message final dans le thread de messagerie. Les messages électroniques sont divisés en quatre valeurs inclusives :

- **Inclusif** : un e-mail *inclusif* est le dernier message électronique d’un thread de messagerie et contient tout le contenu précédent de ce thread de messagerie.

- **Inclus moins** : un message électronique est désigné comme *inclus moins* s’il existe une ou plusieurs pièces jointes associées au message spécifique dans le thread d’e-mail. Un réviseur peut utiliser la valeur Inclusive moins pour déterminer quel message électronique spécifique dans le thread a des pièces jointes associées. 

- **Copie inclusive** : un message électronique est considéré comme une *copie inclusive* s’il s’agit d’une copie exacte d’un message inclusif ou inclusif moins. 

- **Aucun** : la valeur *None* indique que le contenu du message est entièrement contenu dans au moins un autre message électronique marqué comme inclus ou inclusif moins.

## <a name="how-is-it-different-from-conversations-in-outlook"></a>En quoi est-ce différent des conversations dans Outlook ?

En un coup d’œil, cela ressemble à des regroupements de conversations dans Outlook. Toutefois, il existe des distinctions importantes. Considérez une conversation par e-mail qui a été dupliquée en deux conversations ; par exemple, une personne a répondu à un e-mail qui n’est pas le dernier de la conversation, de sorte que les deux derniers e-mails de la conversation ont tous deux un contenu unique.

Outlook regrouperait toujours les e-mails dans une conversation unique ; la lecture du dernier e-mail signifierait qu’il manque le contexte de l’avant-dernier e-mail, qui contient également du contenu unique. Étant donné que le thread d’e-mail analyse chaque e-mail dans des composants individuels et les compare, le thread d’e-mail marque les deux derniers e-mails comme inclusifs, ce qui garantit que vous ne manquerez aucun contexte tant que vous lirez tous les e-mails marqués comme inclusifs.
