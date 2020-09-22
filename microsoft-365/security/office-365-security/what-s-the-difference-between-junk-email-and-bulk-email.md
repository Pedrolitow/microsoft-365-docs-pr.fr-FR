---
title: Quelle est &apos; la différence entre le courrier indésirable et le courrier électronique en masse ?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les différences entre le courrier indésirable (courrier indésirable) et le courrier électronique en masse (courrier gris) dans Exchange Online Protection (EOP).
ms.openlocfilehash: 1e11f897a145f7b34acc81e1d132d6babac08979
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48195474"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Quelle est la différence entre courrier indésirable et courrier électronique en masse dans EOP ?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, les clients se demandent parfois : « quelle est la différence entre le courrier indésirable et le courrier électronique en masse ? » Cette rubrique explique la différence et décrit les contrôles disponibles dans EOP.

- Le courrier **indésirable** est du courrier indésirable, qui sont des messages non sollicités et universellement indésirables (lorsqu’ils sont identifiés correctement). Par défaut, EOP rejette le courrier indésirable en fonction de la réputation du serveur de messagerie source. Si un message passe l’inspection IP source, il est envoyé au filtrage du courrier indésirable. Si le message est classé comme courrier indésirable par filtrage du courrier indésirable, le message est remis (par défaut) aux destinataires concernés et déplacé vers le dossier courrier indésirable.

  - Vous pouvez configurer les actions à effectuer sur le filtrage du courrier indésirable. Pour obtenir des instructions, consultez la rubrique [configurer des stratégies de blocage du courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

  - Si vous n’êtes pas d’accord avec le filtrage du courrier indésirable, vous pouvez signaler à Microsoft les messages que vous considérez comme courrier indésirable ou non indésirables, comme décrit dans la section [rapports de messages et de fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Le **courrier en masse** (également appelé _courrier gris_) est plus difficile à classer. Tandis que le courrier indésirable est une menace constante, les messages électroniques en masse sont souvent des publicités à usage unique ou des messages marketing. Certains utilisateurs veulent des messages électroniques en nombre (et en fait, ils se sont délibérément inscrits pour les recevoir), tandis que d’autres utilisateurs considèrent le courrier en masse comme du courrier indésirable. Par exemple, certains utilisateurs souhaitent recevoir des messages publicitaires de la société Contoso Corporation ou des invitations à une conférence à venir sur la cyber sécurité, tandis que d’autres utilisateurs considèrent ces mêmes messages comme du courrier indésirable.

  Pour plus d’informations sur la façon dont le courrier en masse est identifié, voir [Bulk Complaint Level (BCL) in EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Gestion des messages électroniques en masse

En raison de la réaction mixte au courrier en masse, il n’existe pas de conseils universels qui s’appliquent à chaque organisation.

Les stratégies de blocage du courrier indésirable ont un seuil BCL par défaut qui est utilisé pour identifier le courrier en nombre comme du courrier indésirable. Les administrateurs peuvent augmenter ou diminuer le seuil. Pour plus d’informations, voir les rubriques suivantes :

- [Configurez les stratégies de blocage du courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- [Paramètres de la stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365-atp.md#eop-anti-spam-policy-settings)

Une autre option facile à oublier : si un utilisateur se plaint de recevoir du courrier en masse, mais que les messages proviennent d’expéditeurs dignes de réputation qui passent le filtrage du courrier indésirable dans EOP, demandez à l’utilisateur de vérifier une option de désinscription dans le message électronique en masse.
