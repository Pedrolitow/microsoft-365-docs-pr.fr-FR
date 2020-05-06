---
title: Rétrodiffusion et EOP
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
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous découvrirez rétrodiffusion et Microsoft Exchange Online Protection (EOP)
ms.openlocfilehash: 14460b75920b053461722b5a129d785fb6952a5a
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44035591"
---
# <a name="backscatter-and-eop"></a>Rétrodiffusion et EOP

*Rétrodiffusion* est des notifications d’échec de remise (également appelées notifications de non-remise) que vous recevez pour les messages que vous n’avez pas envoyés. Les expéditeurs de courrier indésirable falsifient (usurpent) l’adresse de provenance de leurs messages et utilisent souvent des adresses de messagerie réelles pour prêter une crédibilité à leurs messages. Par conséquent, lorsque des expéditeurs de courrier indésirable envoient inévitablement des messages à des destinataires inexistants (le courrier indésirable est une opération à fort volume), le serveur de messagerie de destination est essentiellement amené à renvoyer le message non remis dans une notification d’échec de remise à l’expéditeur falsifié dans l’adresse de :.

Exchange Online Protection (EOP) permet d’identifier et de supprimer silencieusement les messages provenant de sources douteuse sans générer de notification d’inversion. Toutefois, en fonction de la quantité de courrier électronique qui transite par le service, il y a toujours la possibilité qu’EOP envoie involontairement rétrodiffusion.

Backscatterer.org gère une liste rouge (également appelée liste de blocage DNS ou BACKSCATTERER) des serveurs de messagerie qui étaient responsables de l’envoi de rétrodiffusion, et les serveurs EOP peuvent apparaître dans cette liste. Mais nous n’essayons pas de nous supprimer de la liste rouge Backscatterer.org, car il ne s’agit pas d’une liste de spammers (par leur propre admission).

> [!TIP]
> Le site Web Backscatter.org<http://www.backscatterer.org/?target=usage>() recommande l’utilisation de son service pour vérifier le courrier électronique entrant en mode sans échec au lieu d’un mode de rejet (les services de messagerie volumineux envoient presque toujours des rétrodiffusion).
