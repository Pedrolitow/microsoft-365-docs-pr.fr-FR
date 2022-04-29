---
title: Aperçu des messages transférés automatiquement
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Les administrateurs peuvent en savoir plus sur le rapport des messages transférés automatiquement dans le tableau de bord de flux de courrier du Centre de sécurité & conformité.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 2f102f4fbea558f0972fbd4f3e8f4a4bea257bf4
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131039"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Informations sur les messages transférés automatiquement dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’insight sur les **messages transférés automatiquement** dans le [tableau de bord](mail-flow-insights-v2.md) flux de courrier du [Centre de sécurité & conformité](https://protection.office.com) affiche des informations sur les messages qui sont automatiquement transférés de votre organisation aux destinataires dans des domaines externes.

:::image type="content" source="../../media/mfi-auto-forwarded-messages.png" alt-text="Widget nommé messages transférés automatiquement dans le Centre de sécurité & conformité" lightbox="../../media/mfi-auto-forwarded-messages.png":::

## <a name="auto-forwarded-messages-details"></a>Détails des messages transférés automatiquement

Lorsque vous cliquez sur le nombre de messages dans le widget, un volet volant s’affiche pour afficher plus d’informations sur les messages transférés automatiquement :

- **Messages transférés automatiquement par les méthodes de transfert** :

  - **Par règles de flux de messagerie**
  - **Par règles de boîte de réception**
  - **Par transfert SMTP** : cette méthode indique le transfert automatique que les administrateurs peuvent configurer sur une boîte aux lettres, comme décrit dans [Configurer le transfert de courrier pour une boîte aux lettres](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding).
  - Lien vers le [rapport de transfert](view-mail-flow-reports.md#forwarding-report) pour plus d’informations.

- **Messages transférés automatiquement par domaines et utilisateurs** :

  - **5 domaines principaux transférés vers**
  - **Nouveaux domaines (la semaine dernière)**
  - **5 principaux utilisateurs de transfert**
  - **Nouveaux utilisateurs (la semaine dernière)**
  - Lien vers le [rapport des modifications de transfert](mfi-new-users-forwarding-email.md#forwarding-modifications-report) pour plus d’informations.

:::image type="content" source="../../media/mfi-auto-forwarded-messages-details.png" alt-text="Widget messages transférés automatiquement dans le Centre de sécurité & conformité" lightbox="../../media/mfi-auto-forwarded-messages-details.png":::

## <a name="insights"></a>Informations

Deux insights sont générés en fonction des données du rapport :

- [Nouveaux utilisateurs transférant des e-mails](mfi-new-users-forwarding-email.md)
- [Nouveaux domaines transférés par e-mail](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
