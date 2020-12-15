---
title: Découvrez les formations à la simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Les administrateurs peuvent découvrir comment la formation à la simulation d’attaque dans le centre de sécurité Microsoft 365 affecte les employés et peut obtenir des informations sur les résultats de la simulation et de la formation.
ms.openlocfilehash: 6fc109469f8a9a3cf6aa87e9b8f9e3a024fed6e3
ms.sourcegitcommit: 1a9f0f878c045e1ddd59088ca2a94397605a242a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "49667594"
---
# <a name="gain-insights-through-attack-simulation-training"></a>Découvrez les formations à la simulation d’attaque

Lors de la formation à la simulation d’attaque, Microsoft vous fournit des informations sur les résultats des simulations et des formations que les employés ont passé. Ces informations vous permettront de vous tenir informé de la progression de la préparation aux menaces de vos employés, ainsi que de vous recommander les étapes suivantes pour mieux préparer vos employés et votre environnement pour les attaques.

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Nous travaillons en permanence sur l’élargissement des connaissances disponibles. L’impact du comportement et les actions recommandées sont actuellement disponibles. Pour commencer, reportez-vous à [la formation simulation d’attaque dans le centre de sécurité Microsoft 365](https://security.microsoft.com/attacksimulator?viewid=overview).

## <a name="behavior-impact-on-compromise-rate"></a>Impact du comportement sur le taux de compromission

Sous l’onglet **vue d’ensemble** de la formation à la simulation d’attaque, vous trouverez l' **impact sur** la carte de taux de compromission. Cette carte montre comment les employés ont traité les simulations que vous avez exécutées en contraste avec le **taux de compromission prévu**. Vous pouvez utiliser ces informations pour suivre la progression de la préparation des menaces pour les employés en exécutant plusieurs simulations sur les mêmes groupes d’employés.

Dans le graphique, vous pouvez voir :

- **Taux de compromission prévu** qui reflète le taux de compromission moyen pour les simulations utilisant le même type de charge pour d’autres clients Microsoft 365 qui utilisent la formation à la simulation d’attaque.
- Le **taux réel de compromission** reflète le pourcentage d’employés qui a perdu la simulation.

En outre, `<number> less susceptible to phishing` reflète la différence entre le nombre réel d’employés compromis par l’attaque et le taux de compromission prévu. Ce nombre d’employés est moins susceptible d’être compromis par des attaques similaires à l’avenir, tandis que la `<percent%> better than predicted rate` manière dont les employés étaient globalement en contraste avec le taux de compromission prévu.

> [!div class="mx-imgBorder"]
> ![Carte d’impact de comportement sur la présentation de la formation à la simulation d’attaque](../../media/attack-sim-preview-behavior-impact-card.png)

Pour afficher un rapport plus détaillé, cliquez sur **afficher les simulations et le rapport d’efficacité de formation**. Ce rapport fournit les mêmes informations avec un contexte supplémentaire à partir de la simulation proprement dite (par exemple, la technique de simulation et le nombre total d’utilisateurs ciblés).

## <a name="recommended-actions"></a>Actions recommandées

Dans l' [onglet **simulations**](https://security.microsoft.com/attacksimulator?viewid=simulations), la sélection d’une simulation vous permet d’accéder aux détails de la simulation, où vous trouverez la section **actions recommandées** .

La section actions recommandées décrit en détail les recommandations disponibles dans [Microsoft Secure score](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score). Ces recommandations sont basées sur la charge utile utilisée dans la simulation et vous aideront à protéger vos employés et votre environnement. Cliquez sur chaque action d’amélioration pour accéder à ses détails.

> [!div class="mx-imgBorder"]
> ![Section actions de recommandation sur la formation à la simulation d’attaque](../../media/attack-sim-preview-recommended-actions.png)

## <a name="related-links"></a>Liens connexes

**Simulateur d’attaque** [créer une simulation d’attaque par hameçonnage](attack-simulation-training.md) et [créer une charge utile pour la formation de vos collaborateurs](attack-simulation-training-payloads.md)
