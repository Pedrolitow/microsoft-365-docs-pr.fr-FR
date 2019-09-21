---
title: Thèmes
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
description: ''
ms.openlocfilehash: b26b031b767f23504294880f4424be5042350c71
ms.sourcegitcommit: 1162d676b036449ea4220de8a6642165190e3398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "37080348"
---
# <a name="themes"></a>Thèmes
Comment une personne écrit-t-elle un document ? Elles commencent généralement par une ou plusieurs idées qu’elles souhaitent transférer dans le document, et composent des mots qui s’alignent sur les idées. Plus l’idée est fréquente, plus le nombre de mots liés à cette idée est important. Cela indique le mode d’utilisation des documents par les utilisateurs ; l’essentiel de la lecture d’un document est l’idée des idées que le document tente de transmettre, et les idées qui apparaissent où et les relations entre les idées.

Cela peut être étendu à la manière dont une personne souhaite utiliser un ensemble de documents. Ils veulent voir quelles idées sont présentes dans les ensembles et quels documents parlent de ces idées. En outre, si elle trouve un document d’intérêt particulier, elle souhaite pouvoir consulter des documents qui abordent des idées similaires.

Le module themes tente de reproduire la raison pour les êtres humains des documents en analysant les « thèmes » présentés dans un jeu de révision et en les affectant à des documents. Les thèmes se déplacent d’une étape et identifient par document le « thème dominant »; autrement dit, le thème qui apparaît le plus.

## <a name="how-does-themes-work"></a>Comment fonctionne le thème ?
Themes analyse les documents avec du texte dans un ensemble de révision pour analyser les thèmes communs qui apparaissent dans les documents. Ensuite, il affecte ces thèmes aux documents dans lesquels ils apparaissent. Il s’étiquette également avec des mots utilisés dans les documents représentatifs du thème. Dans la mesure où un document peut être associé à plusieurs sujets, dans de nombreux cas, un document comporte plusieurs thèmes. Le thème qui apparaît le plus en évidence dans un document est désigné comme son thème dominant.