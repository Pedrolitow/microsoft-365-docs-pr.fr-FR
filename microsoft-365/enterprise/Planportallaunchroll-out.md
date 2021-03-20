---
title: Planification de votre plan de déploiement de lancement de portail dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Cet article décrit comment planifier le lancement de votre portail dans SharePoint Online et les étapes à suivre pour un lancement réussi
ms.openlocfilehash: d77baac6209a4002bb1c27513d5ccfdf5c4ac28a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50905691"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planification de votre plan de déploiement de lancement de portail dans SharePoint Online

Un portail est un site SharePoint sur votre intranet et qui comporte un grand nombre d’internautes qui utilisent du contenu sur le site. Il peut y en avoir plusieurs dans les grandes organisations, par exemple avec un portail d’entreprise et un portail pour les ressources humaines. En règle générale, les portails ont peu de personnes qui créent le site et son contenu. La plupart des visiteurs du portail se content de lire et de consommer le contenu.

Cet article explique comment planifier votre déploiement et votre plan de déploiement sur SharePoint Online. Il fournit également des approches à suivre, car les tests de charge classiques ne sont pas autorisés sur SharePoint Online. SharePoint Online est un service cloud et les fonctionnalités de charge, l’état d’état et l’équilibre global de la charge dans le service sont gérés par Microsoft.

Pour faciliter la création d’un portail réussi, suivez les principes, pratiques et recommandations de base détaillés dans la [création,](/sharepoint/portal-health) le lancement et la maintenance d’un portail sain 

L’approche de déploiement est mise en évidence ci-dessous.

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Vue d’ensemble de la planification de la capacité dans SharePoint Online
Afin d’utiliser efficacement la capacité et de gérer une croissance inattendue, dans n’importe quelle batterie de serveurs, nous avons une automatisation qui suit certains scénarios d’utilisation. Bien que la croissance exacte soit imprévisible pour un client dans une batterie de serveurs, la somme agrégée des demandes est prévisible au fil du temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier une expansion future. Pour plus d’informations sur la [planification de la capacité et le test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md).

Un élément clé d’un lancement réussi est l’approche « vague » ou « déploiement par phases » détaillée ci-dessous. 

## <a name="can-i-load-test-sharepoint-online"></a>Puis-je charger le test SharePoint Online ?
SharePoint Online est un environnement partagé à plusieurs locataires qui est équilibré entre les batteries de serveurs et l’échelle est ajustée de manière continue. Charger le test d’un environnement, tel que SharePoint Online, dont l’échelle change en permanence vous donne non seulement des résultats inattendus, mais il n’est pas autorisé. 

En savoir plus : Planification  [de la capacité et test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimiser les pages en suivant les recommandations
Les pages d’un déploiement local ne doivent pas simplement être déplacées telles qu’elles sont sur SharePoint Online sans les consulter par rapport aux recommandations pour SharePoint Online. La meilleure approche consiste à toujours optimiser n’importe quelle page d’accueil pour n’importe quel site ou portail dans SharePoint, car c’est là que la plupart des utilisateurs de votre organisation accèderont comme point de départ pour vos sites.

Quelques facteurs de base doivent être pris en compte :
- Les déploiements locaux peuvent tirer parti des caches côté serveur traditionnels tels que le cache d’objets, le cache de sortie et le cache blob. Avec les différences de topologie dans le cloud, ces options ne sont pas nécessairement disponibles, car les différences d’échelle les rendent moins viables.
- Toutes les pages/fonctionnalités/personnalisations utilisées pour la consommation cloud doivent être optimisées pour une latence plus élevée ainsi que pour les emplacements distribués des utilisateurs, afin que les utilisateurs de différentes zones ou régions disposent d’une expérience plus cohérente. Le cloud offre des optimisations telles que les réseaux de distribution de contenu (CDN) pour optimiser une base d’utilisateurs distribués, ainsi que pour SharePoint moderne, le dernier bon connu (LKG) est utilisé par nos composants Web Parts OOTB ( out-of-the-box).

### <a name="what-to-do"></a>Que faire :
 - Pour toutes les pages de site dans SharePoint Online, utilisez l’outil Diagnostic des pages, qui est une extension Chromium qui vous aidera à analyser et à fournir des [conseils.](./page-diagnostics-for-spo.md) Il peut être utilisé par les propriétaires de site, les éditeurs, les administrateurs et les développeurs, car il est conçu pour être un point de départ pour l’analyse et l’optimisation.
 - Les développeurs doivent également utiliser des outils de développement tels que l’outil de développement de navigateur F12, ainsi que Ctrl-F12 dans le navigateur sur les pages modernes. [Fiddler](https://www.telerik.com/download/fiddler) peut également être utilisé pour passer en revue le poids de la taille (en mégaoctets) de la page et le nombre d’appels et d’éléments qui ont un impact sur la charge globale de la page. 

Cette section a été un bref résumé pour l’optimisation des pages.  Pour plus d’informations, voir : [Création, lancement et maintenance d’un portail sain.](/sharepoint/portal-health)

## <a name="follow-a-wave--phased-roll-out-approach"></a>Suivre une approche de déploiement wave/progressive
L’approche traditionnelle du big bang pour les lancements de site ne permet pas de vérifier que les personnalisations, les sources externes, les services ou les processus ont été testés à l’échelle de droite. Cela ne signifie pas que le lancement prendra des mois, mais il est recommandé sur au moins plusieurs jours en fonction de la taille de votre organisation. Le fait de suivre un plan de déploiement de vague vous permet de suspendre et de résoudre les problèmes avant de poursuivre la phase suivante, ce qui réduit le nombre potentiel d’utilisateurs touchés par les problèmes. SharePoint as a service scales your capacity based on usage and predicted usage and while we don’t need you to notify us of your launch, you should follow the guidelines to ensure success.
  
Comme illustré dans l’image suivante, le nombre d’utilisateurs invités est souvent beaucoup plus élevé que celui des utilisateurs qui utilisent réellement le site. Cette image illustre une stratégie de déploiement d’une version. Cette méthode permet d’identifier les moyens d’améliorer le site SharePoint avant que la majorité des utilisateurs ne le voient.
  
![Graphique présentant les utilisateurs invités et actifs](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
Lors de la phase pilote, il est bon d’obtenir des commentaires des utilisateurs que l’organisation a confiance et sait qu’elles seront ent resserr. Ainsi, il est possible d’évaluer la façon dont le système est utilisé, ainsi que son fonctionnement.
  
Pendant chacune des vagues, rassemblez les commentaires des utilisateurs autour des fonctionnalités, ainsi que des performances pendant chaque vague de déploiement. Cela présente l’avantage d’introduire lentement le système et d’apporter des améliorations à mesure que le système est de plus en plus utilisé. Cela nous permet également de réagir à la charge accrue à mesure que le site est déployé pour de plus en plus d’utilisateurs et combiné avec les instructions d’optimisation des pages garantit une expérience positive pour vos utilisateurs.

### <a name="what-to-do"></a>Que faire :
- Déterminez le calendrier de chaque phase et assurez-vous que vous avez une opportunité d’urgence/de pause, si vous devez effectuer des ajustements avant de continuer
- Planifiez votre premier groupe d’utilisateurs que vous souhaitez activer, pour vous assurer que vous recevez les commentaires dont vous avez besoin pour aller de l’avant. Cela signifie que, dans la mesure du possible, sélectionnez un groupe actif d’utilisateurs qui fournira des commentaires en temps voulu.
- Lorsque vous planifiez chaque vague, essayez de commencer avec une petite base d’utilisateurs (moins de 5 000 utilisateurs), puis augmentez la taille des groupes au cours de chaque vague. Cela permet de créer une approche échelonnée et de faciliter les opportunités de pause qui peuvent être nécessaires.