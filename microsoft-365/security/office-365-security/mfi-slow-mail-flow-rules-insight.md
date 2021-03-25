---
title: Résoudre les règles de flux de messagerie lent
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
ms.assetid: 37125cdb-715d-42d0-b669-1a8efa140813
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à utiliser l’aperçu corriger les règles de flux de messagerie lent dans le Centre de sécurité & conformité pour identifier et corriger les règles de flux de messagerie inefficaces ou rompues (également appelées règles de transport) dans leur organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 51ffa92402fd3e7c9e76115642426d3cce0a9e19
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204133"
---
# <a name="fix-slow-mail-flow-rules-insight-in-the-security--compliance-center"></a>Résoudre les problèmes de règles de flux de messagerie dans le Centre de sécurité & conformité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Des règles de flux de messagerie inefficaces (également appelées règles de transport) peuvent entraîner des retards de flux de messagerie pour votre organisation. Cette information signale les règles de flux de messagerie qui ont un impact sur le flux de messagerie de votre organisation. Voici quelques exemples de ces types de règles :

- Conditions qui **utilisent est membre de pour** les grands groupes.
- Conditions qui utilisent une correspondance complexe de modèle d’expression régulière (regex).
- Conditions qui utilisent la vérification du contenu dans les pièces jointes.

L’aperçu des règles de  correction du flux [](mail-flow-insights-v2.md) de messagerie lent dans la zone Recommandé pour vous du tableau de bord de flux de messagerie dans le Centre de sécurité [&](https://protection.office.com) conformité vous avertit lorsqu’une règle de flux de messagerie prend trop de temps. 

Cette information apparaît uniquement après la détection de la condition (si vous n’avez pas de boucles de messagerie, vous ne verrez pas l’aperçu).

Vous pouvez utiliser cette notification pour vous aider à identifier et affiner les règles de flux de messagerie afin de réduire les retards de flux de messagerie.

![Résoudre les problèmes de règles de flux de messagerie dans la zone Recommandé pour vous du tableau de bord de flux de messagerie](../../media/mfi-fix-slow-mail-flow-rules.png)

Lorsque vous cliquez **sur Afficher les détails** sur le widget, un flyout s’affiche avec plus d’informations :

- **Règle**: vous pouvez pointer sur le résumé pour voir toutes les conditions, les exceptions et les actions de la règle. Vous pouvez cliquer sur le résumé pour modifier la règle dans le Centre d’administration Exchange (EAC).
- **Nombre de messages évalués**: vous pouvez [](message-trace-scc.md) cliquer sur Afficher les exemples de **messages** pour afficher les résultats du suivi des messages pour un échantillon des messages affectés par la règle.
- **Temps moyen passé sur chaque message**
- **Temps moyen passé sur un message**: valeur intermédiaire qui sépare la moitié supérieure de la moitié inférieure des données de temps.

![Volant de détails qui s’affiche après avoir cliqué sur Afficher les détails sur l’aperçu des règles de flux de messagerie lent fix](../../media/mfi-fix-slow-mail-flow-rules-details.png)

Pour plus d’informations sur les conditions et les exceptions dans les règles de flux de messagerie, voir Conditions et exceptions des règles de flux de messagerie [(prédicats) dans Exchange Online.](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

## <a name="see-also"></a>Voir aussi

Pour plus d’informations sur d’autres informations dans le tableau de bord de flux de messagerie, voir Informations sur le flux de messagerie dans le Centre de sécurité [& conformité.](mail-flow-insights-v2.md)