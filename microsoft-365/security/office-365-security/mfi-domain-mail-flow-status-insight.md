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
ms.openlocfilehash: 457675e7f32cd513f5593ede53a64aaef9d54904
ms.sourcegitcommit: 537e513a4a232a01e44ecbc76d86a8bcaf142482
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50029905"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>Informations sur l’état du flux de messagerie du domaine dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**L’aperçu de** l’état [](mail-flow-insights-v2.md) du flux de messagerie de domaine supérieur dans le tableau de bord flux de messagerie dans le Centre de sécurité [&](https://protection.office.com) conformité vous donne l’état actuel du flux de messagerie pour votre organisation.

Cette information vous permet d’identifier et de résoudre les problèmes de domaines qui rencontrent * problèmes de *_flux_* de messagerie. Par exemple, le domaine ne peut pas recevoir de courrier externe car le domaine a expiré ou le domaine a un enregistrement MX incorrect.

![Widget d’état de flux de domaine supérieur dans le tableau de bord de flux de messagerie dans le Centre de sécurité & conformité](../../media/mfi-top-domain-mail-flow-status-widget.png)

Lorsque vous cliquez sur _ Afficher les  *détails** dans le widget, un flyout d’état du domaine s’affiche, qui affiche plus de détails sur l’état de chaque domaine :

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
