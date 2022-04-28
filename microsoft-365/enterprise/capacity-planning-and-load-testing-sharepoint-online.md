---
title: Planification de la capacité et test de charge SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
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
description: Cet article explique comment déployer sur SharePoint Online sans effectuer de tests de charge traditionnels, car il n’est pas autorisé.
ms.openlocfilehash: 1d1714bbcdefdbc41ff3ac5d038c6b59a7043a26
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101092"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planification de la capacité et test de charge SharePoint Online
Cet article explique comment déployer sur SharePoint Online sans test de charge traditionnel, car le test de charge n’est pas autorisé sur SharePoint Online. SharePoint Online est un service cloud et les fonctionnalités de charge, l’intégrité et l’équilibre global de la charge dans le service sont gérés par Microsoft.
  
La meilleure approche pour garantir la réussite du lancement de votre site consiste à suivre les principes, pratiques et recommandations de base mis en évidence dans le [plan de lancement de votre portail](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Vue d’ensemble de la façon dont SharePoint Online effectue la planification de la capacité 
L’un des principaux avantages de SharePoint Online sur un déploiement local est l’élasticité du cloud et les optimisations pour les utilisateurs des régions distribuées. Notre environnement à grande échelle est configuré pour servir des millions d’utilisateurs quotidiennement. Il est donc important de gérer efficacement la capacité en équilibrant et en développant des batteries de serveurs.
  
Bien que la croissance soit souvent imprévisible pour un locataire dans une batterie de serveurs, la somme agrégée des demandes est prévisible au fil du temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier l’expansion future.
  
Afin d’utiliser efficacement la capacité et de faire face à une croissance inattendue, dans n’importe quelle batterie de serveurs, nous avons une automatisation qui suit et surveille différents éléments du service. Plusieurs métriques sont utilisées, l’une des principales étant la charge du processeur, qui est utilisée comme signal pour mettre à l’échelle les serveurs frontaux. En outre, nous vous recommandons une [approche par phases/vagues](planportallaunchroll-out.md), car SQL environnements seront mis à l’échelle en fonction de la charge et de la croissance au fil du temps, et le fait de suivre les phases et les vagues permet une distribution correcte de cette charge et de cette croissance. 

La capacité ne consiste pas seulement à ajouter plus de matériel sur une base continue, mais elle se rapporte également à la gestion et au contrôle de cette capacité pour s’assurer qu’elle assure la maintenance des demandes de charge valides. Nous recommandons aux clients de suivre les conseils recommandés pour s’assurer qu’ils ont la meilleure expérience. Cela signifie également que nous avons des modèles de limitation et des contrôles en place pour nous assurer que nous n’autorisons pas le comportement « abusif » dans le service. Bien que tous les « mauvais » comportements ne soient pas intentionnels, nous devons nous assurer que nous limitons l’effet de ce comportement. Pour plus d’informations sur la limitation et la façon de l’éviter, consultez l’article sur la [façon d’éviter d’être limité](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Pourquoi vous ne pouvez pas charger le test SharePoint Online
Avec les environnements locaux, le test de charge est utilisé pour valider l’hypothèse de mise à l’échelle et finalement trouver le point de rupture d’une batterie de serveurs; en le saturant de charge. 

Avec SharePoint Online, nous devons faire les choses différemment, car l’échelle est relativement fluide et ajuste, limite et contrôle la charge, en fonction de certaines heuristiques. Étant un environnement multilocataire à grande échelle, nous devons protéger tous les locataires de la même batterie de serveurs. Nous limiterons donc automatiquement tous les tests de charge. Si vous tentez toutefois de tester la charge, en plus d’être limité, vous recevrez des résultats décevants et potentiellement trompeurs, car la batterie que vous avez testée aujourd’hui aura probablement subi des modifications de mise à l’échelle pendant la fenêtre de test ou dans les heures qui suivent les tests, car les actions d’équilibrage de la batterie de serveurs et de mise à l’échelle sont effectuées sur une base continue.

Au lieu d’essayer de charger des tests SharePoint en tant que service, concentrez-vous plutôt sur le respect des pratiques recommandées et suivez les instructions relatives à la [création, au lancement et à la maintenance d’un portail sain](/sharepoint/portal-health).