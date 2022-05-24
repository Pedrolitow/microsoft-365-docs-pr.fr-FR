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
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous allez découvrir backscatter et Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d132ed56c02989987da9e0ce32e7d4593e85e651
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648214"
---
# <a name="backscatter-in-eop"></a>Rétrodiffusion dans EOP

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*La rétrodiffusion* est un rapport de non-remise (également appeléS NDR ou messages de rebond) que vous recevez pour les messages que vous n’avez pas envoyés. La rétrodiffusion est causée par le fait que `5322.From` les spammeurs falsifient (usurpation d’identité) l’adresse From (également appelée adresse P2) dans leurs messages. Les spammeurs utilisent souvent des adresses e-mail réelles comme adresse De pour donner de la crédibilité à leurs messages. Lorsque le courrier indésirable est envoyé à un destinataire inexistant, le serveur de messagerie de destination est essentiellement invité à retourner le message non remis dans une DNR à l’expéditeur falsifié dans l’adresse From.

Dans Microsoft 365 organisations avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, EOP s’efforce d’identifier et de supprimer silencieusement les messages provenant de sources douteuses sans générer de DNR. Toutefois, en fonction du volume de courrier électronique qui transite par le service, il est toujours possible qu’EOP envoie involontairement la rétrodiffusion.

Backscatterer.org gère une liste de blocage (également appelée liste de blocage DNS ou DNSBL) des serveurs de messagerie responsables de l’envoi de backscatter, et les serveurs EOP peuvent apparaître dans cette liste. Mais nous n’essayons pas de nous retirer de la liste de blocage Backscatterer.org, car (de leur propre aveu) leur liste n’est pas une liste de spammeurs.

> [!TIP]
> Le site web Backscatterer.org (<http://www.backscatterer.org/?target=usage>) recommande d’utiliser son service en mode Coffre au lieu du mode Rejeter, car les services de messagerie volumineux envoient presque toujours une rétrodiffusion.
