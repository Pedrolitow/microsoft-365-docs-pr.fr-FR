---
title: Messages de rétrodiffusion et EOP
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
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
description: Les messages rétrodiffusion sont des messages de retour automatique qui sont envoyés à des adresses de messagerie falsifiées. Le BACKSCATTERER d’envoi d’un nuage identifie les serveurs qui envoient des messages rétrodiffusion (qui peuvent inclure de nombreuses sources de messagerie légitimes). Étant donné qu’il ne s’agit pas d’une liste de spammeurs, nous n’essayons pas de nous retirer du BACKSCATTERER.
ms.openlocfilehash: 20ed828680dd20e82819730e6dcd509b896d8616
ms.sourcegitcommit: 1b1425142ae06deae3da10a7d30dce4db029d6d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "42313809"
---
# <a name="backscatter-messages-and-eop"></a>Messages de rétrodiffusion et EOP

Les *messages rétrodiffusion* sont des notifications d’échec de remise (également appelées notifications de non-remise) que vous recevez pour les messages que vous n’avez pas envoyés. Les expéditeurs de courrier indésirable falsifient (usurpent) l’adresse de provenance de leurs messages et utilisent souvent des adresses de messagerie réelles pour prêter une crédibilité à leurs messages. Par conséquent, lorsqu’un expéditeur de courrier indésirable envoie inévitablement des messages à des destinataires qui n’existent pas (le courrier indésirable est une opération à fort volume), le serveur de messagerie de destination renverra probablement le message non remis dans une notification d’échec de remise, qui est envoyée à l’expéditeur falsifié dans l’adresse de :.

Exchange Online Protection (EOP) permet d’identifier et de supprimer silencieusement les messages provenant de sources douteuse sans générer de notification d’inversion. Toutefois, en fonction de la quantité de courrier électronique qui transite par le service, il y a toujours la possibilité qu’EOP envoie involontairement des messages rétrodiffusion.

Backscatterer.org gère une liste rouge (également appelée liste de blocage DNS ou BACKSCATTERER) des serveurs de messagerie qui étaient responsables de l’envoi de messages rétrodiffusion, et des serveurs EOP peuvent apparaître dans cette liste. Mais nous n’essayons pas de nous supprimer de la liste rouge Backscatterer.org, car il ne s’agit pas d’une liste de spammers (par leur propre admission).

> [!TIP]
> Le site Web Backscatter.org<http://www.backscatterer.org/?target=usage>() recommande l’utilisation de son service pour vérifier le courrier électronique entrant en mode sans échec au lieu d’un mode de rejet (les services de messagerie volumineux envoient presque toujours certains messages rétrodiffusion).
