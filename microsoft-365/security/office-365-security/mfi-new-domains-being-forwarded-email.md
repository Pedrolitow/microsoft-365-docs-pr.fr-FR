---
title: Informations sur les nouveaux domaines transmis par courrier électronique
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Les administrateurs peuvent apprendre à utiliser les nouveaux domaines transférés dans le tableau de bord flux de courrier du Centre de sécurité & conformité pour déterminer quand leurs utilisateurs transfèrent des messages vers des domaines externes qui n’ont jamais été transférés.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.collection: m365-security
search.appverid: met150
ms.openlocfilehash: 2ed2d5d258fc95271eeedabbb11f794ea63f77ce
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68083976"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>Informations sur les nouveaux domaines transférés par e-mail dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Il existe des raisons commerciales valides pour transférer des messages électroniques à des destinataires externes dans des domaines spécifiques. Toutefois, il est suspect lorsque les utilisateurs de votre organisation commencent soudainement à transférer des messages vers un domaine où aucun membre de votre organisation n’a jamais transféré de messages vers (un nouveau domaine).

Cette condition peut indiquer que les comptes d’utilisateur sont compromis. Si vous pensez que les comptes ont été compromis, consultez [Répondre à un compte de messagerie compromis](responding-to-a-compromised-email-account.md).

Les **nouveaux domaines transférés** dans le [Centre de sécurité & conformité](https://protection.office.com) vous avertit lorsque les utilisateurs de votre organisation transfèrent des messages vers de nouveaux domaines.

Cet aperçu s’affiche uniquement lorsque le problème est détecté et s’affiche sur la page [du rapport de transfert](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="Informations sur les nouveaux domaines transférés par e-mail" lightbox="../../media/mfi-new-domains-being-forwarded.png":::

Lorsque vous cliquez sur le widget, un menu volant s’affiche, dans lequel vous pouvez trouver plus de détails sur les messages transférés, y compris un lien vers le [rapport de transfert](view-mail-flow-reports.md#forwarding-report).

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="Menu volant Détails qui s’affiche après avoir cliqué sur les nouveaux domaines transférés par e-mail" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

Vous pouvez également accéder à cette page de détails lorsque vous sélectionnez l’insight après avoir cliqué sur **Afficher tout** dans la zone **Informations principales & recommandations** (**Tableau de bord** **des rapports** \> ou <https://protection.office.com/insightdashboard>).

Pour empêcher le transfert automatique de messages vers des domaines externes, configurez un domaine distant pour certains ou tous les domaines externes. Pour plus d’informations, consultez [Gérer les domaines distants dans Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
