---
title: Rétrodiffusion dans EOP
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
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez découvrir la protection contre la Microsoft Exchange Online (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3d9556c69e5db460933b355e8bf12903d56f21b5
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50286968"
---
# <a name="backscatter-in-eop"></a>Rétrodiffusion dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

*La backscatter* est une non-remise (également appelées rapports de non-remise ou messages de non-remise) que vous recevez pour les messages que vous n’avez pas envoyés. Les expéditeurs de courrier indésirable falsifient (usurpent) l’adresse From: de leurs messages. Ils utilisent souvent des adresses de messagerie réelles pour donner de la confiance à leurs messages. Ainsi, lorsque les expéditeurs de courrier indésirable envoient inévitablement des messages à des destinataires inexistants (le courrier indésirable est une opération à volume élevé), le serveur de messagerie de destination est essentiellement dupliqué pour renvoyer le message non remettre dans une NDR à l’expéditeur falsifié dans l’adresse De: .

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou dans des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP s’évouille d’identifier et de déposer silencieusement des messages à partir de sources fictives sans générer de rapport de non-retour. Toutefois, en fonction de la quantité de messages électroniques en volume qui circulent dans le service, il est toujours possible qu’EOP envoie involontairement une copie d’erreur.

Backscatterer.org conserve une liste d’adresses (également appelée liste d’adresses DNS bloqués ou DNSBL) des serveurs de messagerie qui étaient chargés de l’envoi de la backscatter, et les serveurs EOP peuvent apparaître dans cette liste. Toutefois, nous n’essayons pas de nous supprimer de la liste d’Backscatterer.org bloqués, car il ne s’agit pas d’une liste d’expéditeurs de courrier indésirable (de leur propre admission).

> [!TIP]
> Le Backscatter.org web () recommande d’utiliser son service pour vérifier le courrier entrant en mode sans échec plutôt qu’en mode de rejet (les services de courrier de grande taille envoient presque toujours des <http://www.backscatterer.org/?target=usage> retours).
