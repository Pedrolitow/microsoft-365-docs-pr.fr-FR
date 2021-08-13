---
title: Aperçu de l’état du flux de messagerie de domaine supérieur dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’aperçu de l’état du flux de messagerie de domaine supérieur dans le tableau de bord de flux de messagerie du Centre de sécurité & conformité pour résoudre les problèmes de flux de messagerie liés à leurs enregistrements MX.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e0258aeb57f9821091f29f884a42266da47e63dee4adf44a99b3f22154549d19
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "56770468"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Informations sur l’état du flux de messagerie du domaine dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**L’aperçu de** l’état [](mail-flow-insights-v2.md) du flux de messagerie de domaine supérieur dans le tableau de bord flux de messagerie dans le Centre de sécurité [&](https://protection.office.com) conformité vous donne l’état actuel du flux de messagerie pour votre organisation.

Cette information vous permet d’identifier et de dépanner les domaines qui rencontrent des problèmes de ***flux*** de messagerie. Par exemple, le domaine ne peut pas recevoir de courrier externe car le domaine a expiré ou le domaine a un enregistrement MX incorrect.

![Widget d’état de flux de domaine supérieur dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité](../../media/mfi-top-domain-mail-flow-status-widget.png)

Lorsque vous cliquez sur Afficher les  **détails** dans le widget, un flyout d’état de domaine s’affiche pour vous fournir plus de détails sur l’état de chaque domaine :

- **Domaine**
- **Enregistrement MX précédent**
- **Enregistrement MX actuel**
- **État de réception des messages électroniques**
- État **du** domaine : une coche verte indique que l’enregistrement MX actuel (au moment où vous avez cliqué sur le widget) correspond à la valeur que nous avons sur l’enregistrement et que le domaine a reçu des messages électroniques au cours des deux dernières heures.

  Un X rouge indique que l’enregistrement MX a été modifié et que le domaine n’a reçu aucun message électronique au cours des 6 dernières heures. Cela indique probablement que votre domaine a expiré ou que l’enregistrement MX a été mis à jour de manière incorrecte. Vérifiez auprès de votre bureau d’enregistrement de domaines ou de votre service d’hébergement DNS si le domaine a expiré ou si l’enregistrement MX du domaine est incorrect.

Vous pouvez cliquer **sur Afficher plus** pour afficher les mêmes informations pour d’autres domaines.

![Volant d’informations dans l’aperçu de l’état du flux de messagerie du domaine Supérieur](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)
