---
title: Prise en charge de la validation des messages signés DKIM (Domain Keys Identified Mail)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: En savoir plus sur la validation des messages signés DKIM dans Exchange Online Protection et Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5ea98add5ebe860f756d645909366a1f5502832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60203848"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Prise en charge de la validation des messages signés DKIM

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) et Exchange Online la validation entrante des messages[DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)(Domain Keys Identified Mail).

DKIM confirme qu’un message  électronique n’a pas été usurpé par  une autre personne et qu’il a été envoyé à partir du domaine dont il indique qu’il est issu. Il lie un message électronique à l’organisation qui l’a envoyé. La vérification DKIM est utilisée automatiquement pour tous les messages envoyés avec IPv6. Microsoft 365 prend également en charge DKIM lorsque le courrier est envoyé sur IPv4. (Pour plus d'informations sur la prise en charge d'IPv6, voir [Prise en charge des messages entrants anonymes sur IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

DKIM valide un message signé numériquement qui apparaît dans l'DKIM-Signature'en-tête des en-têtes de message. Les résultats d’une validation DKIM-Signature sont marqués dans l’en-tête Authentication-Results'un autre. Le texte de l'en-tête du message ressemble à peu près à ce qui suit (où contoso.com correspond à l'expéditeur) :

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Pour plus d’informations sur Authentication-Results'en-tête, voir RFC 7001 ([Message Header Field for Indicating Message Authentication Status](https://www.rfc-editor.org/rfc/rfc7001.txt). L’implémentation DKIM de Microsoft est conforme à cette RFC.

Les administrateurs peuvent créer des Exchange [de flux](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) de messagerie (également appelées règles de transport) sur les résultats de la validation DKIM. Ces règles de flux de messagerie permettront aux administrateurs de filtrer ou d’router les messages selon les besoins.