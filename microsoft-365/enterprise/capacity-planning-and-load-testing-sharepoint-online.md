---
title: Planification de la capacité et test de charge SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Cet article explique comment effectuer un déploiement sur SharePoint Online sans effectuer de test de charge traditionnel, car il n’est pas autorisé.
ms.openlocfilehash: a20ed3b5f9b3108d90ec912ec78efa348d4281b1
ms.sourcegitcommit: 79065e72c0799064e9055022393113dfcf40eb4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2020
ms.locfileid: "46690062"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planification de la capacité et test de charge SharePoint Online
Cet article explique comment déployer sur SharePoint Online sans les tests de charge traditionnels, car le test de charge n’est pas autorisé sur SharePoint Online. SharePoint Online est un service cloud et les fonctionnalités de charge, l’état d’état et l’équilibre global de la charge dans le service sont gérés par Microsoft.
  
La meilleure approche pour garantir la réussite du lancement de votre site consiste à suivre les principes, pratiques et recommandations de base qui sont mis en évidence dans le plan de lancement de votre [portail.](planportallaunchroll-out.md)

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Vue d’ensemble de la façon dont SharePoint Online effectue la planification de la capacité 
L’un des principaux avantages de SharePoint Online par rapport à un déploiement local est l’flexibilité du cloud, ainsi que les optimisations pour les utilisateurs dans les régions distribuées. Notre environnement à grande échelle est mis en place pour servir quotidiennement des millions d’utilisateurs. Il est donc important de gérer efficacement la capacité en équilibrant et en agrandissant les batteries de serveurs.
  
Bien que la croissance soit souvent imprévisible pour un client dans une batterie de serveurs, la somme agrégée des demandes est prévisible au fil du temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier une expansion future.
  
Afin d’utiliser efficacement la capacité et de gérer une croissance inattendue, dans n’importe quelle batterie de serveurs, nous avons une automatisation qui suit et surveille divers éléments du service. Plusieurs mesures sont utilisées, l’une des principales étant la charge processeur, qui est utilisée comme signal pour monter en charge les serveurs frontaux. En outre, nous vous recommandons une approche par [phases/vagues,](planportallaunchroll-out.md)car les environnements SQL s’échellent en fonction de la charge et de la croissance au fil du temps, et le fait de suivre les phases et les vagues permet une répartition correcte de cette charge et de cette croissance. 

La capacité n’est pas seulement l’ajout continu de matériel, mais elle se rapporte également à la gestion et au contrôle de cette capacité pour s’assurer qu’elle gère les demandes de charge valides. Nous recommandons aux clients de suivre les instructions recommandées pour s’assurer qu’ils ont la meilleure expérience possible. Cela signifie également que nous avons des modèles de limitation et des contrôles en place pour nous assurer que nous n’autorisez pas le comportement « abusif » dans le service. Bien que tous les comportements « mauvais » ne sont pas intentionnels, nous devons nous assurer que nous limitons l’effet de ce comportement. Pour plus d’informations sur la limitation et comment l’éviter, voir l’article d’aide sur la façon d’éviter [d’être](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) limitée.

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Pourquoi vous ne pouvez pas charger sharePoint Online de test
Avec les environnements locaux, le test de charge est utilisé pour valider l’hypothèse d’échelle et, finalement, trouver le point de rupture d’une batterie de serveurs . en le saturent avec charge. 

Avec SharePoint Online, nous devons faire les choses différemment, car l’échelle est relativement fluide et ajuste, les limitations et les contrôles se chargent, en fonction de certaines heuristiques. Étant un environnement à grande échelle à plusieurs locataires, nous devons protéger tous les locataires dans la même batterie de serveurs, afin de limiter automatiquement les tests de charge. Toutefois, si vous tentez de charger le test, en plus d’être limitée, vous recevrez des résultats erronés et potentiellement erronés, car la batterie de serveurs que vous avez testée aujourd’hui aura probablement connu des modifications d’échelle au cours de la fenêtre de test ou dans les heures qui s’après le test, car les actions d’équilibrage d’échelle et de batterie de serveurs sont effectuées de manière continue.

Au lieu d’essayer de charger le test SharePoint en tant que service, concentrez-vous plutôt sur le suivi des pratiques recommandées et suivez les instructions de [création,](https://go.microsoft.com/fwlink/?linkid=2105838) de lancement et de maintenance d’un portail sain.
