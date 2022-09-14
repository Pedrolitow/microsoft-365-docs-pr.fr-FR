---
title: Planification du plan de lancement de votre portail dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
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
description: Cet article décrit comment planifier le lancement de votre portail dans SharePoint Online et les étapes à suivre pour un lancement réussi
ms.openlocfilehash: bcf5db7a1a91a04229bdb366380a7146c8243f96
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67672290"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planification du plan de lancement de votre portail dans SharePoint Online

Un portail est un site SharePoint sur votre intranet avec de nombreux visiteurs de site qui consomment du contenu sur le site. Les grandes organisations peuvent avoir plusieurs portails. Par exemple, un portail d’entreprise et un portail RH. En règle générale, les portails ont peu de personnes qui créent le site et son contenu. La plupart des visiteurs du portail se content de lire et de consommer le contenu.

Cet article explique comment planifier votre déploiement et votre plan de déploiement vers SharePoint Online. Il fournit également des approches à suivre, car les tests de charge traditionnels ne sont pas autorisés sur SharePoint Online. SharePoint Online est un service cloud et les fonctionnalités de charge, l’intégrité et l’équilibre global de la charge dans le service sont gérés par Microsoft.

Pour faciliter la création d’un portail réussi, suivez les principes, pratiques et recommandations de base détaillés dans le [portail Création, lancement et maintenance d’un portail sain](/sharepoint/portal-health)

L’approche de déploiement est mise en évidence ci-dessous.

## <a name="portal-launch-scheduler"></a>Planificateur de lancement du portail

Utilisez le planificateur de lancement du portail pour libérer votre portail pour les utilisateurs de votre organisation dans les phases planifiées. En savoir plus :

![Icône calendrier.](../media/calendar.png) [Planificateur de lancement du portail](/microsoft-365/enterprise/portallaunchscheduler)

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Vue d’ensemble de la planification de la capacité dans SharePoint Online

Afin d’utiliser efficacement la capacité et de faire face à une croissance inattendue, dans n’importe quelle batterie de serveurs, nous avons une automatisation qui suit certains scénarios d’utilisation. Bien que la croissance exacte soit imprévisible pour n’importe quel locataire dans une batterie de serveurs, la somme agrégée des demandes est prévisible au fil du temps. En identifiant les tendances de croissance dans SharePoint Online, nous pouvons planifier l’expansion future. Pour plus d’informations sur [la planification de la capacité et le test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md).

Une partie essentielle d’un lancement réussi est l’approche « vague » ou « déploiement par phases » détaillée ci-dessous.

## <a name="can-i-load-test-sharepoint-online"></a>Puis-je tester la charge de SharePoint Online ?

SharePoint Online est un environnement mutualisé partagé qui est équilibré entre les batteries de serveurs et l’échelle est ajustée en continu. Le test de charge d’un environnement, comme SharePoint Online, dont les modifications de mise à l’échelle continue ne vous donneront pas seulement des résultats inattendus, mais il n’est pas autorisé.

En savoir plus :  [Planification de la capacité et test de charge SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimiser les pages en suivant les instructions recommandées

Les pages d’un déploiement local ne doivent pas simplement être déplacées, car elles sont sur SharePoint Online sans les examiner par rapport aux instructions recommandées pour SharePoint Online. La meilleure approche consiste à toujours optimiser n’importe quelle page d’accueil pour n’importe quel site ou portail dans SharePoint, car c’est là que la plupart des utilisateurs de votre organisation accèderont en tant que point de départ pour votre ou vos sites.

Quelques facteurs de base doivent être pris en compte :

- Les déploiements locaux peuvent utiliser des caches côté serveur traditionnels tels que le cache d’objets, le cache de sortie et le cache d’objets blob. Avec les différences de topologie dans le cloud, ces options ne sont pas nécessairement disponibles, car les différences d’échelle les rendent moins viables.
- Toutes les pages/ fonctionnalités/personnalisations utilisées pour la consommation cloud doivent être optimisées pour une latence plus élevée et les emplacements distribués des utilisateurs, afin que les utilisateurs de différentes zones ou régions bénéficient d’une expérience plus cohérente. Le cloud offre des optimisations telles que les réseaux de distribution de contenu (CDN) afin d’optimiser pour une base d’utilisateurs distribués et pour SharePoint moderne, le dernier bien connu (LKG) est utilisé par nos composants WebPart OOTB.

**Que faire** :

- Pour toutes les pages de site dans SharePoint Online, utilisez [l’outil Diagnostics](./page-diagnostics-for-spo.md) de page, qui est une extension Chromium qui permet d’analyser et de fournir des conseils. Cet outil peut être utilisé par les propriétaires de sites, les éditeurs, les administrateurs et les développeurs, car il est conçu pour être un point de départ pour l’analyse et l’optimisation.
- Les développeurs doivent également utiliser des outils de développement tels que l’outil de développement du navigateur F12 et CTRL-F12 dans le navigateur sur les pages modernes. [Fiddler](https://www.telerik.com/download/fiddler) peut également être utilisé pour passer en revue le poids de la taille (la taille de la page en mégaoctets) de la page et le nombre d’appels et d’éléments ayant un impact sur le chargement global de la page.

Cette section était un bref résumé de l’optimisation des pages.  Pour en savoir plus, consultez :  [Création, lancement et maintenance d’un portail sain](/sharepoint/portal-health).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Suivre une approche de déploiement par vague/par phases

L’approche traditionnelle du Big Bang pour les lancements de sites n’autorise pas la vérification que les personnalisations, les sources externes, les services ou les processus ont été testés à l’échelle appropriée. Cette approche ne signifie pas que le lancement prendra des mois, mais il est recommandé sur au moins plusieurs jours en fonction de la taille de votre organisation. Le fait de suivre un plan de déploiement par vagues vous donne donc la possibilité de suspendre et de résoudre les problèmes avant de passer à la phase suivante et, par conséquent, de réduire le nombre potentiel d’utilisateurs concernés par les problèmes. SharePoint en tant que service met à l’échelle votre capacité en fonction de l’utilisation et de l’utilisation prédite et, bien que nous n’ayons pas besoin que vous nous informiez de votre lancement, vous devez suivre les instructions pour garantir la réussite.

Comme illustré dans l’image suivante, le nombre d’utilisateurs invités est souvent beaucoup plus élevé que celui qui utilise réellement le site. Cette image montre une stratégie sur la façon de déployer une version. Cette méthode permet d’identifier les moyens d’améliorer le site SharePoint avant que la plupart des utilisateurs ne le voient.

![Graphique montrant les utilisateurs invités et actifs.](../media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)

Dans la phase pilote, il est bon d’obtenir des commentaires des utilisateurs auxquels l’organisation fait confiance et sait qu’ils seront engagés. De cette façon, il est possible d’évaluer la façon dont le système est utilisé et comment il fonctionne.

Au cours de chacune des vagues, recueillez les commentaires des utilisateurs sur les fonctionnalités et les performances pendant chaque vague de déploiement. La collecte de commentaires a l’avantage d’introduire lentement le système et d’apporter des améliorations à mesure que le système est plus utilisé. Cela nous permet également de réagir à l’augmentation de la charge à mesure que le site est déployé pour un plus grand nombre d’utilisateurs et combiné avec le suivi des instructions pour l’optimisation des pages garantit une expérience positive pour vos utilisateurs.

**Que faire** :

- Déterminez le moment de chaque phase et assurez-vous que vous disposez d’une opportunité d’urgence/de pause, si vous devez apporter des ajustements avant de continuer
- Planifiez votre premier groupe d’utilisateurs que vous souhaitez activer pour vous assurer de recevoir les commentaires dont vous avez besoin pour aller de l’avant.  Si possible, sélectionnez un groupe actif d’utilisateurs qui fournira des commentaires en temps opportun
- Lorsque vous planifiez chaque vague, essayez de commencer par une petite base d’utilisateurs (moins de 5 000 utilisateurs). Augmentez les tailles de groupe à mesure que vous passez à chaque vague. En créant une approche décalée, elle permet de suspendre plus facilement les opportunités en fonction des besoins.
