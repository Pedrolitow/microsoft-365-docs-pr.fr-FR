---
title: Principaux insights sur l’état du flux de messagerie de domaine dans le tableau de bord flux de messagerie
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: m365-security
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’insight d’état du flux de messagerie du domaine supérieur dans le tableau de bord flux de messagerie du Centre de sécurité & conformité pour résoudre les problèmes de flux de courrier liés à leurs enregistrements MX.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: c87262d79211f1a67b5268e56876252fc61054ab
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68054949"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Principaux insights sur l’état du flux de messagerie de domaine dans le Centre de sécurité & conformité

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

L’aperçu **de l’état du flux de messagerie de domaine supérieur** dans le [tableau de bord flux de](mail-flow-insights-v2.md) messagerie du [Centre de sécurité & conformité](https://protection.office.com) vous donne l’état actuel du flux de courrier pour votre organisation.

Cet insight vous aide à identifier et à résoudre les domaines qui rencontrent des problèmes de ***flux de messagerie*** . Par exemple, le domaine ne peut pas recevoir d’e-mail externe, car le domaine a expiré ou le domaine a un enregistrement MX incorrect.

:::image type="content" source="../../media/mfi-top-domain-mail-flow-status-widget.png" alt-text="Widget d’état du flux de domaine supérieur dans le tableau de bord Flux de courrier du Centre de sécurité & conformité" lightbox="../../media/mfi-top-domain-mail-flow-status-widget.png":::

Lorsque vous cliquez sur **Afficher les détails** dans le widget, un menu volant d’état de **domaine** s’affiche pour afficher plus de détails sur l’état de chaque domaine :

- **Domaine**
- **Enregistrement MX précédent**
- **Enregistrement MX actuel**
- **Email l’état de réception**
- **État du domaine** : une coche verte indique que l’enregistrement MX actuel (au moment où vous avez cliqué sur le widget) correspond à la valeur que nous avons sur l’enregistrement et que le domaine a reçu un e-mail au cours des deux dernières heures.

  Un X rouge indique que l’enregistrement MX a été modifié et que le domaine n’a reçu aucun e-mail au cours des 6 dernières heures. Cela indique probablement que votre domaine a expiré ou que l’enregistrement MX a été mis à jour de manière incorrecte. Vérifiez auprès de votre bureau d’enregistrement de domaine ou du service d’hébergement DNS si le domaine a expiré ou si l’enregistrement MX du domaine est incorrect.

Vous pouvez cliquer sur **Afficher plus** pour afficher les mêmes informations pour d’autres domaines.

:::image type="content" source="../../media/mfi-top-domain-mail-flow-status-view-details.png" alt-text="Menu volant Détails dans l’insight d’état du flux de messagerie du domaine supérieur" lightbox="../../media/mfi-top-domain-mail-flow-status-view-details.png":::

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, consultez [les insights de flux de courrier dans le Centre de sécurité & conformité](mail-flow-insights-v2.md).
