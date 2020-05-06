---
title: Thèmes-eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez des thèmes dans Advanced eDiscovery pour organiser les ensembles de révision en recherchant le thème dominant dans chaque document.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: eb008e091cd8c8330d1cdd5b388e252af70922da
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44034518"
---
# <a name="themes"></a>Thèmes

Comment une personne écrit-t-elle un document ? Elles commencent généralement par une ou plusieurs idées qu’elles souhaitent transférer dans le document, et composent des mots qui s’alignent sur les idées. Plus l’idée est fréquente, plus le nombre de mots liés à cette idée est important. Cela indique le mode d’utilisation des documents par les utilisateurs. Il est important de comprendre la lecture d’un document, à savoir les idées que le document tente de transmettre, les idées qui apparaissent où et les relations entre les idées.

Cela peut être étendu à la manière dont une personne souhaite utiliser un ensemble de documents. Ils veulent voir quelles idées sont présentes dans les ensembles et quels documents parlent de ces idées. En outre, si elle trouve un document d’intérêt particulier, elle souhaite pouvoir consulter des documents qui abordent des idées similaires.

La fonctionnalité de thèmes dans Advanced eDiscovery tente de reproduire la raison pour les êtres humains des documents en analysant les *thèmes* présentés dans un jeu de révision et en affectant un thème aux documents dans l’ensemble de révision. Dans Advanced eDiscovery, les thèmes se déplacent d’une étape supplémentaire et identifient le *thème dominant* dans chaque document. Le thème dominant est celui qui apparaît le plus souvent dans un document.

## <a name="how-does-themes-work"></a>Comment fonctionne le thème ?

La fonctionnalité de thèmes analyse les documents avec du texte dans un ensemble de révision pour analyser les thèmes communs qui apparaissent dans tous les documents de l’ensemble de révision. Advanced eDiscovery affecte ces thèmes aux documents dans lesquels ils apparaissent. Il étiquette également chaque thème avec les mots utilisés dans les documents représentatifs du thème. Étant donné qu’un document peut contenir différents types d’objets, Advanced eDiscovery affecte souvent plusieurs thèmes à des documents. Le thème qui apparaît le plus en évidence dans un document est désigné comme son thème dominant.
