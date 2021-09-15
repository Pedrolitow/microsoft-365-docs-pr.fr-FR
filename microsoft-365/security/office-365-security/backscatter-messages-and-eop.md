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
ms.openlocfilehash: 31af8d1467d1e38287c8308dcbac5e55fb7478bf
ms.sourcegitcommit: f88a0ec621e7d9bc5f376eeaf70c8a9800711f88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2021
ms.locfileid: "59356112"
---
# <a name="backscatter-in-eop"></a>Rétrodiffusion dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*La backscatter* est des rapports de non-remise (également appelés rapports de non-remise ou de non-remise) que vous recevez pour les messages que vous n’avez pas envoyés. La backscatter est causée par les expéditeurs de courrier indésirable qui ont usurpé (usurpation) l’adresse de l’expéditeur (également appelée adresse `5322.From` P2) dans leurs messages. Les expéditeurs de courrier indésirable utilisent souvent des adresses e-mail réelles comme adresse de provenance pour donner de la crédit à leurs messages. Lorsque du courrier indésirable est envoyé à un destinataire inexistant, le serveur de messagerie de destination est essentiellement dupliché de renvoyer le message non transmis dans une NDR à l’expéditeur falsifié dans l’adresse de provenance.

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP s’évouille d’identifier et de déposer silencieusement des messages à partir de sources fictives sans générer de rapport de non-réception. Toutefois, en fonction de la quantité de messages électroniques en volume qui circulent dans le service, il est toujours possible qu’EOP envoie involontairement une copie d’erreur.

Backscatterer.org conserve une liste de blocage (également appelée liste d’adresses DNS ou DNSBL) des serveurs de messagerie qui étaient chargés de l’envoi de la copie de retour, et les serveurs EOP peuvent apparaître dans cette liste. Toutefois, nous n’essayons pas de nous supprimer de la liste de blocage Backscatterer.org car (de leur propre admission) leur liste n’est pas une liste d’expéditeurs de courrier indésirable.

> [!TIP]
> Le Backscatterer.org web () recommande d’utiliser son service en mode Coffre plutôt qu’en mode de rejet, car les services de courrier de grande taille envoient presque toujours des messages de <http://www.backscatterer.org/?target=usage> secours.
