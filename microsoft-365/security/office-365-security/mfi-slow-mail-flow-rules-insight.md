---
title: Résoudre les règles de flux de messagerie lent
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser le correctif lent les règles de flux de messagerie du centre de sécurité & Compliance Center pour identifier et corriger les règles de flux de messagerie inefficaces ou rompues (également appelées règles de transport) dans leur organisation.
ms.openlocfilehash: c933a6816c82161d0f4a6199ff1a339dd8a10eae
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47357343"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Réparer le ralentissement des règles de flux de messagerie dans le centre de sécurité & conformité

Des règles inefficaces de flux de messagerie (également appelées règles de transport) peuvent entraîner des retards de flux de messagerie pour votre organisation. Cette vue d’État indique les règles de flux de messagerie qui ont un impact sur le flux de messagerie de votre organisation. Voici des exemples de ces types de règles :

- Conditions utilisées par **est membre de** pour les grands groupes.
- Conditions qui utilisent des critères de correspondance des expressions régulières complexes (Regex).
- Conditions d’utilisation de l’archivage de contenu dans les pièces jointes.

Les **règles de flux de messagerie de résolution lente** dans la zone **recommandé pour vous** du [tableau de bord de flux de messagerie](mail-flow-insights-v2.md) dans le centre de [sécurité & conformité](https://protection.office.com) vous avertit lorsqu’une règle de flux de messagerie prend trop de temps pour se terminer. Cette vue ne s’affiche qu’une fois la condition détectée (si vous n’avez pas de boucles de courrier, vous ne verrez pas la vue d’ensemble).

Vous pouvez utiliser cette notification pour identifier et ajuster les règles de flux de messagerie afin de réduire les retards de flux de messagerie.

![Réparer le ralentissement des règles de flux de messagerie dans la zone recommandé pour vous du tableau de bord flux de messagerie](../../media/mfi-fix-slow-mail-flow-rules.png)

Lorsque vous cliquez sur **afficher les détails** dans le widget, un lanceur apparaît avec davantage d’informations :

- **Règle**: vous pouvez pointer sur le résumé pour afficher toutes les conditions, les exceptions et les actions de la règle. Vous pouvez cliquer sur le résumé pour modifier la règle dans le centre d’administration Exchange.
- **Nombre de messages évalués**: vous pouvez cliquer sur **afficher les exemples de messages** pour afficher les résultats de [suivi](message-trace-scc.md) des messages pour un exemple de messages qui ont été affectés par la règle.
- **Temps moyen passé sur chaque message**
- **Temps médian passé sur un message**: valeur centrale séparant la partie supérieure de la moitié inférieure des données de temps.

![Fenêtre volante de détails qui apparaît après avoir cliqué sur Afficher les détails dans la boîte de message Fix ralentissement des règles de flux de messagerie](../../media/mfi-fix-slow-mail-flow-rules-details.png)

Pour plus d’informations sur les conditions et les exceptions dans les règles de flux de messagerie dans Exchange Online, consultez la rubrique [mail Flow Rule conditions and exceptions (prédicats) in Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur les autres informations du tableau de bord de flux de messagerie, consultez [la rubrique mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
