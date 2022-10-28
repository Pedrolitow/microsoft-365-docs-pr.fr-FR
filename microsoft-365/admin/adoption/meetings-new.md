---
title: Score d’adoption Microsoft - Réunions (nouveau)
f1.keywords: NOCSH
ms.author: camillepack
author: camillepack
manager: scotv
ms.reviewer: ''
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- scotvorg
- highpri
ms.custom: ''
search.appverid: MET150
description: 'Détails du nouveau score d’insights sur les réunions : les utilisateurs rencontrent le score d’adoption.'
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 382c55e4c584a4747d822ecb3e8802725ae864c4
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68767772"
---
# <a name="meetings-insights-score--people-experiences-new"></a>Score d’insights sur les réunions – expériences Personnes (Nouveau)

Le score d’adoption fournit des insights sur le parcours de transformation numérique de votre organisation grâce à son utilisation de Microsoft 365 et aux expériences technologiques qui le prennent en charge. Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé à des points de référence d’organisations similaires à la vôtre. La catégorie réunions fait partie des mesures d’expérience des personnes. Pour en savoir plus, consultez la [vue d’ensemble du score d’adoption](adoption-score.md) et lisez la [Déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Configuration requise

Pour commencer à utiliser Meetings Insights, les membres de votre organisation doivent disposer d’une licence pour :

- Microsoft Teams

Pour plus d’informations, consultez [Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md).

Une fois que les utilisateurs ont été actifs dans Teams au moins une fois au cours des 28 derniers jours, vous commencez à voir les insights.

## <a name="why-your-organizations-meetings-score-matters"></a>Pourquoi le score des réunions de votre organisation est important

Les réunions, où les personnes explorent des idées, planifient, résolvent des problèmes et prennent des décisions, constituent un pilier fondamental de la productivité organisationnelle. Les recherches indiquent que lorsque les utilisateurs utilisent efficacement les outils de réunion en ligne, ils ont tendance à économiser jusqu’à 104 minutes par semaine.

## <a name="how-we-calculate-the-meetings-score"></a>Comment nous calculons le score des réunions

Microsoft Teams s’intègre au calendrier Outlook et fournit une multitude de fonctionnalités pour rendre vos réunions plus attrayantes et plus efficaces. Nous fournissons un score global pour les réunions, puis des sous-scores pour chacune des meilleures pratiques dans les sections Configurer, Rencontrer et Suivre.

## <a name="overall-score"></a>Score global

Le score global de la réunion est calculé en calculant la moyenne des scores sur les trois phases, c’est-à-dire, Configurer, Rencontrer et Suivre. Nous prenons en compte le nombre de participants et la durée de la réunion lors du décompte des scores moyens finaux.

Pour chaque réunion :

1. Nous calculons les trois sous-scores (Pré, Pendant, Post), en calculant la moyenne des fonctionnalités, pour chaque réunion. Par exemple, Configurer : 30, Meet up : 40, Suivi : 20
1. Nous calculons ensuite la moyenne des trois sous-scores de la réunion. Dans l’exemple ci-dessus, 30+40+20/3 = 30
1. Nous calculons le poids de chaque réunion en fonction de la durée et de la taille de la réunion. Plus une réunion est longue ou plus importante, plus elle a d’impact sur le score final.
1. Nous effectuons ensuite une moyenne de somme pondérée sur les scores de toutes les réunions du locataire en fonction des pondérations de réunion pour calculer le score de réunion final pour le locataire.

:::image type="content" source="../../media/adoption-score-meetings.jpg" alt-text="Capture d’écran : Score de réunion pour les réunions Microsoft Teams":::

1. **En-tête** : affiche le score, sur 100, basé sur la moyenne des phases d’installation, de réunion et de suivi pour les réunions en ligne sur Microsoft Teams tenues au cours des 28 derniers jours.
1. **Corps** : fournit plus d’informations sur la façon dont l’utilisation efficace des outils de réunion en ligne peut rendre les réunions plus efficaces.
1. **Visualisation (état actuel)** : dans ce graphique à barres horizontales, la partie bleue (colorée) représente le score (sur 100) affiché dans l’en-tête.

## <a name="trend-visualization-of-the-score"></a>Visualisation des tendances du score

Le graphique suivant montre la courbe de tendance du score sur la période sélectionnée. Chaque point de données sur le graphique en courbes est un agrégat d’activité des 28 derniers jours.

:::image type="content" source="../../media/meetings-time-trend.jpg" alt-text="Capture d’écran : Graphique de tendance de temps pour le score de réunion":::

## <a name="what-makes-up-my-score"></a>Qu’est-ce qui compose mon score ?

Nous vous fournissons des données à l’appui sur chacune des phases de configuration, de réunion et de suivi. Le score de chaque insight est calculé sur 100.

## <a name="set-up"></a>Configurer

Il s’agit de la phase qui implique la planification et le partage des détails de la réunion et des participants qui rejoignent la réunion.

:::image type="content" source="../../media/meetings-set-up.jpg" alt-text="Capture d’écran : section Configurer la phase pour le score de réunion":::

- **Communication partagée à l’avance** : il s’agit du score pour les réunions Microsoft Teams pour lesquelles une conversation de réunion de conversation Teams a démarré avant la tenue de la réunion. Pour que cela soit suivi, un utilisateur doit accéder à la conversation de réunion avec les participants et envoyer un message aux participants, avant l’heure de la réunion planifiée.
- **Planifié avec un préavis d’au moins 24 heures** : il s’agit du score des réunions Microsoft Teams qui ont été planifiées au moins 24 heures avant leur heure de début.
- **Invitation acceptée à un taux élevé (>50 %)** : il s’agit du score pour les réunions Microsoft Teams pour lesquelles plus de 50 % des participants invités acceptent l’invitation à la réunion.
- **Rejoint dans les 5 minutes suivant l’heure de début (>50 %)** : il s’agit du score des réunions Microsoft Teams dont plus de 50 % des participants invités rejoignent la réunion dans les 5 minutes suivant l’heure de début.

## <a name="meet-up"></a>Rendez-vous

Il s’agit de la phase de participation des participants à la réunion.

:::image type="content" source="../../media/meetings-meet-up.jpg" alt-text="Capture d’écran : section de la phase de réunion pour le score de réunion":::

- **Utilisé au moins une fonctionnalité interactive** : il s’agit du score des réunions Microsoft Teams pour lesquelles les participants utilisaient au moins une fonctionnalité interactive. Ces fonctionnalités interactives incluent lever la main, envoyer un message de conversation de réunion ou envoyer une réaction à la réunion. Le score est calculé sur 100.
- **Participation avec audio ou conversation à un taux élevé (>33 %)** : cela représente le score pour les réunions Microsoft Teams où plus de 33 % des participants prennent la parole dans une réunion, envoient une conversation de réunion, ou les deux. Le score est calculé sur 100.
- **Contenu visuel partagé** : il s’agit du score pour les réunions Microsoft Teams où les participants partagent du contenu visuel dans la réunion en activant leur vidéo, leur écran de partage ou les deux. Le score est calculé sur 100.

## <a name="follow-up"></a>Suivi

:::image type="content" source="../../media/meetings-follow-up.jpg" alt-text="Capture d’écran : section De la phase de suivi pour le score de réunion":::

- **Enregistrement créé** : il s’agit du score des réunions Microsoft Teams pour lesquelles la réunion a été enregistrée. Le score est calculé sur 100.
- **Communication envoyée après la réunion** : il s’agit du score des réunions Microsoft Teams dont les participants ont partagé des messages de conversation sur le fil de conversation après la fin de cette réunion. Le score est calculé sur 100.

## <a name="how-can-i-impact-my-score"></a>Comment puis-je avoir un impact sur mon score ?

Cette section vous aide à comprendre deux insights pour l’organisation :

1. **Croissance la plus significative** : cette section décrit la partie du score qui a connu la croissance la plus élevée au cours des 28 derniers jours.
1. **Plus grand domaine d’amélioration** : cette section décrit la partie du score qui a la plus grande marge d’amélioration et d’impact sur le score d’adoption de l’organisation à l’avenir.

## <a name="dig-deeper-into-meetings"></a>Approfondir les réunions

Cette section se compose de trois sous-sections :

1. **Insights supplémentaires** : ici, nous fournissons des insights supplémentaires qui aident les organisations à identifier les tendances et les comportements des utilisateurs entre les réunions.
1. **Résultats intéressants** : Nous fournissons ici quelques faits intéressants sur les réunions tenues au sein de l’organisation.
1. **Microsoft Research** : ici, nous faisons référence aux blogs Microsoft et à la recherche publique qui fournissent des pratiques recommandées et leurs impacts pour avoir des réunions efficaces.

> [!NOTE]
> La section « Approfondir les réunions » ne contribue pas au score global de la page Réunions dans Score d’adoption Personnes Expériences, mais certains insights de cette section peuvent développer un insight principal utilisé pour calculer un score.

## <a name="related-content"></a>Contenu associé

[Intégrité des applications Microsoft 365 – Expériences technologiques](apps-health.md) (article)\
[Communication – expériences Personnes](communication.md) (article)\
[Collaboration de contenu – expériences Personnes](content-collaboration.md) (article)\
[Mobilité – expériences Personnes](mobility.md) (article)\
[Contrôles de confidentialité pour le score d’adoption](privacy.md) (article)\
[Travail d’équipe – expériences Personnes](teamwork.md) (article)
