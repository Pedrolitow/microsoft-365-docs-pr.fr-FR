---
title: Aperçu des messages transférés automatiquement
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: b5543faa-44fa-44c5-8180-fb835e7e452d
description: Les administrateurs peuvent en savoir plus sur le rapport des messages transmis automatiquement dans le tableau de bord flux de messagerie du Centre de sécurité & conformité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 94700aa4fc08d0c462aa186a0f0847d73151a82a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204383"
---
# <a name="auto-forwarded-messages-insight-in-the-security--compliance-center"></a>Informations sur les messages transmis automatiquement dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les informations sur les **messages** transmis automatiquement dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité affichent des informations sur les messages qui sont automatiquement transmis à partir de votre organisation à des destinataires dans des [domaines](https://protection.office.com) externes. [](mail-flow-insights-v2.md)

![Widget de messages transmis automatiquement dans le Centre de sécurité & conformité.](../../media/mfi-auto-forwarded-messages.png)

## <a name="auto-forwarded-messages-details"></a>Détails des messages automatiquement transmis

Lorsque vous cliquez sur le nombre de messages dans le widget, un volet volant s’affiche, qui affiche plus d’informations sur les messages transmis automatiquement :

- **Les messages transmis automatiquement par les méthodes de forwarding**:

  - **Par règles de flux de messagerie**
  - **Par règles de boîte de réception**
  - **Par le forwarding SMTP**: cette méthode indique le forwarding automatique que les administrateurs peuvent configurer sur une boîte aux lettres comme décrit dans Configurer le forwarding de courrier pour [une boîte aux lettres.](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding)
  - Lien vers le rapport [de report pour](view-mail-flow-reports.md#forwarding-report) plus d’informations.

- **Messages transmis automatiquement par les domaines et les utilisateurs**:

  - **5 principaux domaines vers**
  - **Nouveaux domaines (dernière semaine)**
  - **5 principaux utilisateurs de forwarding**
  - **Nouveaux utilisateurs (semaine dernière)**
  - Lien vers le rapport [de modifications de forwarding](mfi-new-users-forwarding-email.md#forwarding-modifications-report) pour plus d’informations.

![Volant de détails pour le rapport des messages transmis automatiquement dans le Centre de sécurité & conformité.](../../media/mfi-auto-forwarded-messages-details.png)

## <a name="insights"></a>Informations

Deux informations sont générées en fonction des données du rapport :

- [Nouveaux utilisateurs qui envoient du courrier électronique](mfi-new-users-forwarding-email.md)
- [Nouveaux domaines en cours de envoi de courrier électronique](mfi-new-domains-being-forwarded-email.md)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)