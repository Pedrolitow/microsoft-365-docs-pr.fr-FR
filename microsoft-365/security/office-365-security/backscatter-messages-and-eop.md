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
ms.openlocfilehash: 3dc83c303e861c8762f2276de521e1b550ae2e59
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41599731"
---
# <a name="backscatter-messages-and-eop"></a>Messages de rétrodiffusion et EOP

Les *messages rétrodiffusion* sont des notifications d’échec de remise (également appelées notifications de non-remise) que vous recevez pour les messages que vous n’avez pas envoyés. Les expéditeurs de courrier indésirable falsifient (usurpent) l’adresse de provenance de leurs messages et utilisent souvent des adresses de messagerie réelles pour prêter une crédibilité à leurs messages. Par conséquent, lorsqu’ils envoient inévitablement des messages à des destinataires qui ne sont pas existants (le courrier indésirable est une opération à fort volume), le serveur de messagerie de destination peut faire face à une notification d’échec de remise, qui est envoyée à l’expéditeur falsifié dans l’adresse de :.

Exchange Online Protection (EOP) permet d’identifier et de supprimer silencieusement les messages provenant de sources douteuse sans générer de notification d’inversion. Toutefois, en fonction de la quantité de courrier électronique qui transite par le service, il y a toujours la possibilité qu’EOP envoie involontairement des messages rétrodiffusion.

Backscatterer.org gère une liste rouge (également appelée liste de blocage DNS ou BACKSCATTERER) des serveurs de messagerie qui étaient responsables de l’envoi de messages rétrodiffusion, et des serveurs EOP peuvent apparaître dans cette liste. Mais nous n’essayons pas de nous supprimer de la liste rouge Backscatterer.org, car il ne s’agit pas d’une liste de spammers (par leur propre admission).

> [!TIP]
> En fonction du rétrodiffusion. ou du site`http://www.backscatterer.org/?target=usage`Web (), il est recommandé d’utiliser son service pour vérifier le courrier entrant en mode sans échec au lieu du mode de rejet (les services de messagerie volumineux envoient presque toujours des messages rétrodiffusion).
