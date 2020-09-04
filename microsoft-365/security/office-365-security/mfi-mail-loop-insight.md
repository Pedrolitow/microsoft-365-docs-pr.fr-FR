---
title: Résoudre les problèmes de boucles de courrier possibles
f1.keywords:
- NOCSH
ms.author: chrisda
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
ms.openlocfilehash: 063906195488aa7d65093c538d9045002448e181
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358269"
---
# <a name="fix-possible-mail-loop-insight-in-the-security--compliance-center"></a>Corriger les éventuelles boucles de courrier dans le centre de sécurité & conformité

Une boucle de courrier est incorrecte car elle gaspille des ressources système, consomme le quota de volume de courrier de votre organisation et envoie des notifications d’échec de remise confuses (également appelées notifications de non-remise) aux expéditeurs d’origine.

La **fonctionnalité corriger la boucle de courrier possible** dans la zone **recommandé pour vous** du [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de [sécurité & conformité](https://protection.office.com) vous avertit lorsqu’une boucle de courrier est détectée dans votre organisation. Cette vue ne s’affiche qu’une fois la condition détectée (si vous n’avez pas de boucles de courrier, vous ne verrez pas la vue d’ensemble).

![Réparer le ralentissement des règles de flux de messagerie dans la zone recommandé pour vous du tableau de bord flux de messagerie](../../media/mfi-fix-possible-mail-loop.png)

Lorsque vous cliquez sur **afficher les détails** dans le widget, un lanceur apparaît avec davantage d’informations :

- **Domaine**
- **Nombre de messages**: vous pouvez cliquer sur **afficher les exemples de messages** pour afficher les résultats du [suivi](message-trace-scc.md) des messages pour un exemple de messages qui ont été affectés par la boucle.
- **Type de domaine**«par exemple, faisant autorité ou ne faisant pas autorité.
- **Enregistrement MX**: l’hôte (**serveur de messagerie**) et les valeurs de **priorité** de l’enregistrement MX pour le domaine.
- **Raison** de la boucle et **Comment résoudre**: nous allons essayer d’identifier les scénarios de boucle de courrier les plus courants et de fournir les actions recommandées (le cas échéant) pour corriger la boucle.

![Fenêtre volante de détails qui apparaît après avoir cliqué sur Afficher les détails dans la boîte de message de correction possible](../../media/mfi-fix-possible-mail-loop-details.png)

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
