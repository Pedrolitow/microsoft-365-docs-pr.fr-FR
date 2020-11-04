---
title: Vue d’État du flux de messagerie de domaine supérieur dans le tableau de bord de flux de messagerie
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’état du flux de messagerie du domaine le plus pertinent dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité pour résoudre les problèmes de flux de messagerie liés aux enregistrements MX dans leurs domaines de messagerie.
ms.openlocfilehash: d4abc311e96df87894d5f059328f1a16a00190b8
ms.sourcegitcommit: b64f36d3873fa0041b24bec029deb73ccfdfdbac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877506"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>État du flux de messagerie du domaine le plus approfondi dans le centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


L' **État du flux de messagerie du domaine le plus visible** dans le [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de [sécurité & conformité](https://protection.office.com) vous donne l’état actuel des domaines de votre organisation en termes de flux de messagerie. Cette vue vous permet d’identifier et de dépanner les domaines rencontrant des problèmes liés à l' *_impact du flux de messagerie_* (par exemple, l’impossibilité de recevoir des messages électroniques externes), notamment les expirations de domaine ou les domaines avec des enregistrements MX incorrects.

![Widget État du flux de domaine supérieur dans le tableau de bord de flux de messagerie dans le centre de sécurité & conformité](../../media/mfi-top-domain-mail-flow-status-widget.png)

Lorsque vous cliquez sur _ *afficher les détails* * dans le widget, un menu volant d’état de **domaine** s’affiche pour vous afficher des détails supplémentaires sur l’état de chaque domaine :

- **Domaine**
- **Enregistrement MX précédent**
- **Enregistrement MX actuel**
- **État de réception du courrier électronique**
- **État du domaine** : une coche verte indique que l’enregistrement MX actuel (au moment où vous avez cliqué sur le widget) correspond à la valeur que nous avons sur l’enregistrement et que le domaine a reçu la messagerie au cours des deux dernières heures.

  Un X rouge indique que l’enregistrement MX a été modifié et que le domaine n’a pas reçu de courrier au cours des 6 dernières heures. Cela indique probablement que votre domaine a expiré ou que l’enregistrement MX a été mis à jour de manière incorrecte. Vérifiez auprès de votre bureau d’enregistrement de domaines ou de votre service d’hébergement DNS si le domaine a expiré ou si l’enregistrement MX du domaine est incorrect.

Vous pouvez cliquer sur **afficher plus** pour afficher les mêmes informations pour plus de domaines.

![Fenêtre mobile détails dans l’état du flux de messagerie du domaine supérieur](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="related-topics"></a>Rubriques connexes

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
