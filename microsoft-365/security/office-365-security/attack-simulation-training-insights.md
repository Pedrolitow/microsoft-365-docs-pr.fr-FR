---
title: Découvrez les formations à la simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent découvrir comment la formation sur la simulation d’attaques dans le portail Microsoft 365 Defender affecte les employés et peut obtenir des informations sur les résultats de la simulation et de la formation.
ms.technology: mdo
ms.openlocfilehash: 725b5c0310d4412f0901526a8111c686f69898a2
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59163538"
---
# <a name="gain-insights-through-attack-simulation-training"></a>Découvrez les formations à la simulation d’attaque

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans le cadre d’une formation sur la simulation d’attaques, Microsoft vous fournit des informations sur les résultats des simulations et des formations que les employés ont réalisées. Ces informations vous aideront à vous tenir informé de la progression de la préparation aux menaces de vos employés, ainsi que les étapes suivantes pour mieux préparer vos employés et votre environnement aux attaques.

Nous travaillons en permanence sur l’extension des informations disponibles. L’impact sur le comportement et les actions recommandées sont actuellement disponibles. Pour commencer, commencez par vous entraîner à [la simulation d’attaques dans Microsoft 365 Defender portail.](https://security.microsoft.com/attacksimulator?viewid=overview)

## <a name="behavior-impact-on-compromise-rate"></a>Impact du comportement sur le taux de compromission

Sous **l’onglet Vue d’ensemble** de la formation sur la simulation d’attaque, vous trouverez l’impact du **comportement sur la carte de taux de** compromission. Cette carte montre comment les employés traitent les simulations que vous avez réalisées par opposition au **taux de compromission prévu.** Vous pouvez utiliser ces informations pour suivre l’avancement de la préparation des menaces des employés en exécutant plusieurs simulations sur les mêmes groupes d’employés.

Dans le graphique, vous pouvez voir :

- **Taux de compromission** prévu qui reflète le taux moyen de compromission pour les simulations utilisant le même type de charge utile pour d’autres locataires Microsoft 365 qui utilisent une formation sur la simulation d’attaques.
- **Le taux de compromission** réel reflète le pourcentage d’employés qui ont diminué pour la simulation.

En outre, reflète la différence entre le nombre réel d’employés compromis par l’attaque et le `<number> less susceptible to phishing` taux de compromission prévu. Ce nombre d’employés est moins susceptible d’être compromis par des attaques similaires à l’avenir, tout en indique la façon dont les employés ont globalement fait, contrairement au taux de `<percent%> better than predicted rate` compromission prévu.

> [!div class="mx-imgBorder"]
> ![Vue d’ensemble de la carte d’impact sur le comportement sur la formation de simulation d’attaque.](../../media/attack-sim-preview-behavior-impact-card.png)

Pour afficher un rapport plus détaillé, cliquez sur **Afficher les simulations et le** rapport d’efficacité de formation. Ce rapport fournit les mêmes informations avec un contexte supplémentaire de la simulation proprement dite (par exemple, la technique de simulation et le nombre total d’utilisateurs ciblés).

## <a name="recommended-actions"></a>Actions recommandées

Sous [ **l’onglet Simulations,**](https://security.microsoft.com/attacksimulator?viewid=simulations)la sélection d’une simulation vous permet d’obtenir les détails de la simulation, où se trouve la section **Actions recommandées.**

La section Actions recommandées détaille les recommandations telles que disponibles dans [Le Score de sécurité Microsoft.](../defender/microsoft-secure-score.md) Ces recommandations sont basées sur la charge utile utilisée dans la simulation et vous aideront à protéger vos employés et votre environnement. Le fait de cliquer sur chaque action d’amélioration vous permet d’obtenir ses détails.

> [!div class="mx-imgBorder"]
> ![Section Actions de recommandation sur la formation à la simulation d’attaques.](../../media/attack-sim-preview-recommended-actions.png)

## <a name="related-links"></a>Liens connexes

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[créer une charge utile pour former vos employés](attack-simulation-training-payloads.md)
