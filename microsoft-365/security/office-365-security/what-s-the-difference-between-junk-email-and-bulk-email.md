---
title: Quelle &apos; est la différence entre le courrier indésirable et le courrier en masse ?
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
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les différences entre le courrier indésirable (courrier indésirable) et le courrier en masse (courrier gris) dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c656ed1807b451ae03ecfeb0f220f5d7b902c7ac
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50290644"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Quelle est la différence entre le courrier indésirable et le courrier en masse dans EOP ?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou dans des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, les clients se demandent parfois : « Quelle est la différence entre le courrier indésirable et le courrier en masse ? » Cette rubrique explique la différence et décrit les contrôles disponibles dans EOP.

- **Le courrier indésirable** est du courrier indésirable, qui est un message non sollicité et universellement indésirable (s’il est correctement identifié). Par défaut, EOP rejette le courrier indésirable en fonction de la réputation du serveur de messagerie source. Si un message réussit l’inspection de l’adresse IP source, il est envoyé au filtrage du courrier indésirable. Si le message est classé comme courrier indésirable par filtrage du courrier indésirable, le message est remis (par défaut) aux destinataires prévus et déplacé vers son dossier Courrier indésirable.

  - Vous pouvez configurer les actions à prendre sur les verdicts de filtrage du courrier indésirable. Pour obtenir des instructions, voir [Configurer des stratégies anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

  - Si vous n’êtes pas d’accord avec le verdict de filtrage du courrier indésirable, vous pouvez signaler les messages que vous considérez comme courrier indésirable ou non indésirable à Microsoft de plusieurs manières, comme décrit dans Signaler les messages et les fichiers à [Microsoft.](report-junk-email-messages-to-microsoft.md)

- **Les messages électroniques** en nombre (également appelés _messages_ gris) sont plus difficiles à classer. Alors que le courrier indésirable est une menace constante, les courriers électroniques en masse sont souvent des publicités ou des messages marketing. Certains utilisateurs souhaitent des messages électroniques en nombre (et en fait, ils se sont délibérément inscrits pour les recevoir), tandis que d’autres considèrent les messages électroniques en masse comme du courrier indésirable. Par exemple, certains utilisateurs souhaitent recevoir des messages publicitaires de Contoso Corporation ou des invitations à une conférence à venir sur la cybersécurité, tandis que d’autres considèrent ces mêmes messages comme du courrier indésirable.

  Pour plus d’informations sur la façon dont les messages électroniques en nombre sont identifiés, voir Le niveau de réclamation en bloc [(BCL) dans EOP.](bulk-complaint-level-values.md)

## <a name="how-to-manage-bulk-email"></a>Gestion des messages électroniques en masse

En raison de la réaction mixte aux messages électroniques en masse, il n’existe pas d’instructions universelles qui s’appliquent à chaque organisation.

Les polices anti-courrier indésirable ont un seuil BCL par défaut qui est utilisé pour identifier les messages électroniques en masse comme courrier indésirable. Les administrateurs peuvent augmenter ou diminuer le seuil. Pour plus d’informations, voir les rubriques suivantes :

- [Configurer des stratégies anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

- [Paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365-atp.md#eop-anti-spam-policy-settings)

Une autre option facile à ignorer : si un utilisateur se plaindra de recevoir des messages électroniques en masse, mais que les messages sont des expéditeurs dignes de confiance qui passent le filtrage du courrier indésirable dans EOP, l’utilisateur doit vérifier qu’une option de désabonnement est disponible dans le message électronique en masse.
