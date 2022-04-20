---
title: Thèmes dans Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez thèmes dans eDiscovery (Premium) pour organiser les ensembles de révision en recherchant le thème dominant dans chaque document.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 49605d2d7fb3103c672fd5ae4d2249956d52b6a0
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934509"
---
# <a name="themes-in-ediscovery-premium"></a>Thèmes dans eDiscovery (Premium)

Comment une personne écrit-elle un document ? Ils commencent généralement par une ou plusieurs idées qu’ils souhaitent transmettre dans le document et composent à l’aide de mots qui s’alignent sur les idées. Plus une idée est répandue, plus les mots associés à cette idée sont fréquents. Cela indique également comment les utilisateurs consomment des documents. La chose importante à comprendre de la lecture d’un document est les idées que le document tente de transmettre, quelles idées apparaissent où, et quelles sont les relations entre les idées.

Cela peut être étendu à la façon dont une personne souhaite consommer un ensemble de documents. Ils veulent voir quelles idées sont présentes dans les ensembles et quels documents parlent de ces idées. En outre, s’ils trouvent un document particulier d’intérêt, ils veulent pouvoir voir des documents qui discutent d’idées similaires.

La fonctionnalité Thèmes dans eDiscovery (Premium) tente d’imiter la façon dont les humains raisonnent sur les documents, en analysant les *thèmes abordés* dans un jeu de révision et en attribuant un thème aux documents du jeu de révision. Dans eDiscovery (Premium), Themes va plus loin et identifie le *thème dominant* dans chaque document. Le thème dominant est celui qui apparaît le plus souvent dans un document.

## <a name="how-does-themes-work"></a>Comment fonctionnent les thèmes ?

La fonctionnalité Thèmes analyse les documents d’un jeu à réviser qui incluent du texte afin d’identifier les thèmes communs qui apparaissent dans tous les documents du jeu à réviser. eDiscovery (Premium) affecte ces thèmes aux documents dans lesquels ils apparaissent. Il associe par ailleurs les thèmes aux mots utilisés dans les documents représentatifs du thème. Étant donné qu’un document peut contenir différents types d’objet, eDiscovery (Premium) affecte souvent plusieurs thèmes aux documents. Le thème le plus évident dans un document est désigné comme thème dominant.
