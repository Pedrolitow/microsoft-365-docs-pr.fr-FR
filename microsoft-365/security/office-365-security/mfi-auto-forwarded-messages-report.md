---
title: Aperçu des messages transférés automatiquement
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Les administrateurs peuvent en savoir plus sur le rapport de messages transférés automatiquement dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité.
ms.openlocfilehash: b5255a95718fa6624c85e93a19c8accf9c3dcdb2
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48199358"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Aperçu des messages transmis automatiquement dans le centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


La vue **messages transmis automatiquement** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de [sécurité & conformité](https://protection.office.com) affiche des informations sur les messages qui sont automatiquement transférés de votre organisation à des destinataires dans des domaines externes.

![Widget messages transférés automatiquement dans le centre de sécurité & conformité](../../media/mfi-auto-forwarded-messages.png)

## <a name="auto-forwarded-messages-details"></a>Détails des messages transférés automatiquement

Lorsque vous cliquez sur le nombre de messages dans le widget, un volet flyout apparaît et affiche des informations supplémentaires sur les messages transférés automatiquement :

- **Messages transférés automatiquement par les méthodes de transfert**:

  - **Par les règles de flux de messagerie**
  - **Par les règles de boîte de réception**
  - **Par le transfert SMTP**
  - Un lien vers le [rapport de transfert](view-mail-flow-reports.md#forwarding-report) pour plus de détails.

- **Messages transférés automatiquement par les domaines et les utilisateurs**:

  - **5 principaux domaines transférés vers**
  - **Nouveaux domaines (semaine dernière)**
  - **Les 5 principaux utilisateurs de transfert**
  - **Nouveaux utilisateurs (semaine dernière)**
  - Un lien vers le [rapport des modifications de transfert](mfi-new-users-forwarding-email.md#forwarding-modifications-report) pour plus de détails.

![Fenêtre mobile des détails pour le rapport de messages transférés automatiquement dans le centre de sécurité & conformité](../../media/mfi-auto-forwarded-messages-details.png)

## <a name="insights"></a>Informations

Deux analyses sont générées en fonction des données de rapport :

- [Nouveaux utilisateurs transférant le courrier électronique](mfi-new-users-forwarding-email.md)
- [Nouveaux domaines en cours de transmission de courrier électronique](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
