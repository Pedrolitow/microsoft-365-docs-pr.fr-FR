---
title: Thèmes - eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez des thèmes dans Advanced eDiscovery pour organiser les ensembles de révision en trouvant le thème dominant dans chaque document.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 3dfc0dca0c6ed62e3ce8384efa2fd3ea407c3ce8
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48285530"
---
# <a name="themes-in-advanced-ediscovery"></a>Thèmes dans Advanced eDiscovery

Comment une personne écrit-elle un document ? Ils commencent généralement par une ou plusieurs idées qu’ils souhaitent transmettre dans le document et composent à l’aide de mots qui s’alignent sur les idées. Plus une idée est répandue, plus les mots associés à cette idée sont fréquents. Cela vous informe également sur la façon dont les personnes utilisent des documents. L’élément important à comprendre lors de la lecture d’un document est les idées que le document tente de transmettre, les idées qui apparaissent où et quelles sont les relations entre les idées.

Cela peut être étendu à la façon dont une personne souhaite consommer un ensemble de documents. Ils souhaitent voir quelles idées sont présentes dans les ensembles et quels documents les présentent. En outre, s’ils trouvent un document particulier intéressant, ils souhaitent être en mesure de voir des documents qui discutent d’idées similaires.

La fonctionnalité Thèmes dans Advanced eDiscovery tente d’imiter la  raison humaine des documents, en analysant les thèmes abordés dans un jeu à réviser et en attribuant un thème aux documents du jeu à réviser. Dans Advanced eDiscovery, les thèmes vont plus loin et identifient le *thème dominant* dans chaque document. Le thème dominant est celui qui apparaît le plus souvent dans un document.

## <a name="how-does-themes-work"></a>Comment fonctionnent les thèmes ?

La fonctionnalité Thèmes analyse les documents d’un jeu à réviser qui incluent du texte afin d’identifier les thèmes communs qui apparaissent dans tous les documents du jeu à réviser. Advanced eDiscovery attribue les thèmes identifiés aux documents dans lesquels ils apparaissent. Il associe par ailleurs les thèmes aux mots utilisés dans les documents représentatifs du thème. Les documents pouvant contenir différents types de sujets, Advanced eDiscovery leur attribue souvent plusieurs thèmes. Le thème le plus évident dans un document est désigné comme thème dominant.
