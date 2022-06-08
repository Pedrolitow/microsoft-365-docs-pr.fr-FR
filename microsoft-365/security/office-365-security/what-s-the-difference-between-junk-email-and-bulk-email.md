---
title: Quelle est la différence entre courrier indésirable et message électronique en masse ?
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
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent découvrir les différences entre le courrier indésirable (courrier indésirable) et le courrier en bloc (courrier gris) dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dd876b522a0d565b84e8bb9043e277cd3bc34495
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940445"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Quelle est la différence entre le courrier indésirable et le courrier électronique en bloc dans EOP ?

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, les clients demandent parfois : « Quelle est la différence entre le courrier indésirable et le courrier en bloc ? » Cette rubrique explique la différence et décrit les contrôles disponibles dans EOP.

- **Le courrier indésirable** est un courrier indésirable, qui sont des messages non sollicités et universellement indésirables (lorsqu’ils sont identifiés correctement). Par défaut, l’EOP rejette le courrier indésirable en fonction de la réputation du serveur de messagerie source. Si un message réussit l’inspection IP source, il est envoyé au filtrage du courrier indésirable. Si le message est classé comme courrier indésirable par filtrage du courrier indésirable, le message est (par défaut) remis aux destinataires prévus et déplacé vers son dossier Courrier indésirable.

  - Vous pouvez configurer les actions à prendre pour les verdicts de filtrage du courrier indésirable. Pour obtenir des instructions, consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

  - Si vous n’êtes pas d’accord avec le verdict de filtrage du courrier indésirable, vous pouvez signaler des messages que vous considérez comme du courrier indésirable ou non indésirable à Microsoft de plusieurs façons, comme décrit dans les [messages et fichiers du rapport à Microsoft](report-junk-email-messages-to-microsoft.md).

- **L’e-mail en bloc** (également appelé _courrier gris_) est plus difficile à classer. Alors que le courrier indésirable est une menace constante, le courrier électronique en bloc est souvent des publicités ponctuelles ou des messages marketing. Certains utilisateurs veulent des messages électroniques en bloc (et en fait, ils se sont volontairement inscrits pour les recevoir), tandis que d’autres utilisateurs considèrent le courrier électronique en bloc comme du courrier indésirable. Par exemple, certains utilisateurs souhaitent recevoir des messages publicitaires de Contoso Corporation ou des invitations à une prochaine conférence sur la cybersécurité, tandis que d’autres utilisateurs considèrent ces mêmes messages comme du courrier indésirable.

  Pour plus d’informations sur la façon dont le courrier électronique en bloc est identifié, consultez le [niveau de réclamation en bloc (BCL) dans EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Gestion des messages électroniques en masse

En raison de la réaction mixte à l’e-mail en bloc, il n’existe pas de conseils universels qui s’appliquent à chaque organisation.

Les stratégies anti-courrier indésirable ont un seuil BCL par défaut qui est utilisé pour identifier les courriers électroniques en bloc comme courrier indésirable. Les administrateurs peuvent augmenter ou diminuer le seuil. Pour plus d’informations, voir les rubriques suivantes :

- [Configurez des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- [Paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Une autre option facile à ignorer : si un utilisateur se plaint de recevoir des e-mails en bloc, mais que les messages proviennent d’expéditeurs réputés qui transmettent le filtrage du courrier indésirable dans EOP, faites vérifier par l’utilisateur une option de désabonnement dans le message électronique en bloc.
