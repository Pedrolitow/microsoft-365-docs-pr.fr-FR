---
title: Prise en charge de la validation des messages signés DKIM (Domain Keys Identified Mail)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- m365-security
description: En savoir plus sur la validation des messages signés DKIM dans Exchange Online Protection et Exchange Online
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 410180d764d0ed96d1cb13fe3c2a39604604778a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68633127"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Prise en charge de la validation des messages signés DKIM

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) et Exchange Online prennent en charge la validation entrante des messages [DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt) (Domain Keys Identified Mail).

DKIM vérifie qu’un e-mail n’a pas été *usurpé* par une autre personne et a été envoyé à partir du domaine d’où il *indique* qu’il provient. Il lie un e-mail à l’organisation qui l’a envoyé. La vérification DKIM est utilisée automatiquement pour tous les messages envoyés avec IPv6. Microsoft 365 prend également en charge DKIM lorsque le courrier est envoyé via IPv4. (Pour plus d'informations sur la prise en charge d'IPv6, voir [Prise en charge des messages entrants anonymes sur IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md).)

DKIM valide un message signé numériquement qui apparaît dans l’en-tête DKIM-Signature des en-têtes de message. Les résultats d’une validation DKIM-Signature sont marqués dans l’en-tête Authentication-Results. Le texte de l'en-tête du message ressemble à peu près à ce qui suit (où contoso.com correspond à l'expéditeur) :

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Pour plus d’informations sur l’en-tête Authentication-Results, consultez RFC 7001 ([Champ d’en-tête de message pour indiquer l’état de l’authentification](https://www.rfc-editor.org/rfc/rfc7001.txt) des messages). L’implémentation DKIM de Microsoft est conforme à ce RFC.

Les administrateurs peuvent créer des [règles de flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Exchange (également appelées règles de transport) sur les résultats de la validation DKIM. Ces règles de flux de messagerie permettent aux administrateurs de filtrer ou d’acheminer les messages en fonction des besoins.
