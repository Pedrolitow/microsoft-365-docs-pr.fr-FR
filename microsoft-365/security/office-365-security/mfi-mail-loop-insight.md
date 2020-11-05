---
title: Résoudre les problèmes de boucles de courrier possibles
f1.keywords:
- NOCSH
ms.author: siosulli
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: cb801985-3c89-4979-9c18-17829a4cb563
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser la fonction de résolution des problèmes possibles dans le tableau de bord de flux de messagerie dans le centre de sécurité & Compliance pour identifier et corriger les boucles de messagerie au sein de leur organisation.
ms.openlocfilehash: 1d49fd93b2ea068986e003b36077672215a2dd57
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920563"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Corriger les éventuelles boucles de courrier dans le centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Les boucles de messagerie sont incorrectes car :

- Ils perdent des ressources système.
- Ils consomment le quota de volume de messagerie de votre organisation.
- Ils envoient des notifications d’échec de remise confus (également appelées notifications de non-remise) aux expéditeurs des messages d’origine.

La **fonctionnalité corriger la boucle de courrier possible** dans la zone **recommandé pour vous** du [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de [sécurité & conformité](https://protection.office.com) vous avertit lorsqu’une boucle de courrier est détectée dans votre organisation.

Cette vue ne s’affiche qu’une fois la condition détectée (si vous n’avez pas de boucles de courrier, vous ne verrez pas la vue d’ensemble).

![Réparer le ralentissement des règles de flux de messagerie dans la zone recommandé pour vous du tableau de bord flux de messagerie](../../media/mfi-fix-possible-mail-loop.png)

Lorsque vous cliquez sur **afficher les détails** dans le widget, un lanceur apparaît avec davantage d’informations :

- **Domaine**
- **Nombre de messages** : vous pouvez cliquer sur **afficher les exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un exemple de messages qui ont été affectés par la boucle.
- **Type de domaine** «par exemple, faisant autorité ou ne faisant pas autorité.
- **Enregistrement MX** : l’hôte ( **serveur de messagerie** ) et les valeurs de **priorité** de l’enregistrement MX pour le domaine.
- **Raison** de la boucle et **Comment corriger** : nous allons identifier les scénarios de boucle de courrier les plus courants et fournir les actions recommandées pour la résolution de la boucle.

![Fenêtre volante de détails qui apparaît après avoir cliqué sur Afficher les détails dans la boîte de message de correction possible](../../media/mfi-fix-possible-mail-loop-details.png)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
