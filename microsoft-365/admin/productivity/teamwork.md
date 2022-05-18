---
title: Score de productivité Microsoft et insights sur le travail d’équipe
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
monikerRange: o365-worldwide
search.appverid:
- MET150
- MOE150
description: 'Détails du travail d’équipe : les personnes obtiennent un score de productivité.'
ms.openlocfilehash: b7291ec2a4bf0e97c0bc8b3558c2cdc17d86a19a
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466391"
---
# <a name="teamwork--people-experiences"></a>Travail d’équipe – Expériences de personnes

Le score de productivité fournit des insights sur le parcours de transformation numérique de votre organisation par le biais de son utilisation de Microsoft 365 et des expériences technologiques qui le prennent en charge. Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé aux points de référence d’organisations similaires à la vôtre. La catégorie travail d’équipe fait partie des mesures qui relèvent des expériences des personnes. Pour en savoir plus, consultez la [vue d’ensemble du score de productivité](productivity-score.md) et lisez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Prerequisites

Pour bien démarrer avec les insights sur le travail d’équipe, les membres de votre organisation doivent disposer d’une licence pour :

- Microsoft Teams
- SharePoint
- Exchange Online

Pour plus d’informations, consultez [Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md).

Une fois que les personnes ont été actives dans les produits ci-dessus au moins une fois au cours des 28 derniers jours, vous commencerez à voir les insights.

## <a name="why-your-orgs-teamwork-score-matters"></a>Pourquoi le score de travail d’équipe de votre organisation est important

Un pilier fondamental de la productivité organisationnelle est lorsqu’un groupe de personnes ayant un objectif commun travaille les unes avec les autres et avec des ressources communes pour la réussite collective. Les recherches indiquent que lorsque des personnes partagent des informations et collaborent dans des espaces de travail partagés, elles économisent jusqu’à 4 heures par semaine. Ils peuvent trouver des documents connexes, trouver le contexte des discussions précédentes et atteindre des objectifs partagés. Voir [theevidence](https://www.microsoft.com/microsoft-365/blog/wp-content/uploads/sites/2/2019/04/Total-Economic-Impact-Microsoft-Teams.pdf)

## <a name="how-we-calculate-the-teamwork-score"></a>Comment calculer le score de travail d’équipe

Nous fournissons un aperçu principal de l’expérience qui contient les métriques clés pour cette catégorie dans votre organisation. Ensuite, une infrastructure de scoring, détaillée ci-dessous, est utilisée pour ces métriques afin de calculer le score de votre organisation.

### <a name="primary-insight"></a>Insight principal

L’insight principal examine toutes les personnes qui communiquent à l’aide de courriers électroniques et de messages sur Microsoft Teams, et qui interagissent avec du contenu sur le cloud dans des espaces de travail partagés. Dans Microsoft 365, Groupes Microsoft 365 constituent la base pour que les personnes se réunissent dans un espace de travail partagé avec la possibilité d’envoyer des e-mails à la boîte aux lettres de groupe, de partager des fichiers sur le site d’équipe SharePoint et d’envoyer des messages de canal via Microsoft Teams.

:::image type="content" source="../../media/teamwork-score.png" alt-text="Graphique montrant les principaux insights sur le score de travail d’équipe.":::

1. **En-tête:** Fournit la métrique clé des personnes de votre organisation effectuant l’une des activités suivantes :
      - Envoi d’e-mails à une boîte aux lettres de groupe via Exchange.
      - Envoi de messages de canal via Teams
      - Lecture et création de contenu (ce que nous appelons collectivement interaction de contenu) dans SharePoint sites d’équipe.

        En pourcentage de toutes les personnes de votre organisation qui effectuent l’une des activités suivantes (à l’intérieur ou à l’extérieur d’espaces de travail partagés) :
        - Envoi d’e-mails via Exchange.
        - Envoi de messages (messages de conversation ou de canal) sur Microsoft Teams.
        - Lecture et création de contenu sur OneDrive ou SharePoint.

            Et avoir accès à au moins l’un des services suivants : Exchange, Microsoft Teams ou SharePoint

1. **Corps:** Fournit plus d’informations sur la façon dont la communication et l’interaction avec le contenu, lorsqu’elles sont effectuées dans un espace de travail partagé, peuvent avoir des résultats positifs pour la productivité au sein de votre organisation.
2. **Visualisation (état actuel) :**
      - Barre horizontale où la partie bleue représente le pourcentage exprimé dans l’en-tête
      - Met en surbrillance la fraction (numerator/dénominateur) utilisée pour calculer le pourcentage affiché dans l’en-tête
        - Numérateur : nombre de personnes de votre organisation qui envoient des e-mails à une boîte aux lettres de groupe via Exchange, OU qui envoient des messages de canal via Teams, OU qui lisent et créent du contenu dans SharePoint sites d’équipe.
        - Dénominateur : nombre de personnes de votre organisation qui envoient des e-mails via Exchange, ou envoient des messages (messages de conversation ou de canal) sur Microsoft Teams, ou qui lisent et créent du contenu sur OneDrive ou SharePoint, ET ont accès à au moins l’un des services suivants : Exchange, Microsoft Teams ou SharePoint.
   - La valeur d’évaluation d’homologue de la métrique clé est également affichée sous la forme d’un pourcentage.
3. **Afficher les ressources sur le travail d’équipe :** Sélectionnez ce lien pour afficher le contenu de l’aide.

#### <a name="trend-visualization-of-the-primary-insight"></a>Visualisation des tendances de l’insight principal

Le graphique suivant fournit la tendance du numérateur et le dénominateur de la métrique clé dans l’insight principal. Il indique le nombre de personnes impliquées dans des espaces de travail partagés et le nombre de personnes qui communiquent ou interagissent avec du contenu au cours des 180 derniers jours. Chaque point de données du graphique en courbes est un agrégat d’activité pour les 28 derniers jours.

:::image type="content" source="../../media/trend-peopleiinsharedworkspaces.png" alt-text="Graphique montrant le nombre de personnes impliquées dans des espaces de travail partagés.":::

### <a name="scoring-framework"></a>Framework de scoring

Le score de travail d’équipe de votre organisation mesure au niveau agrégé (organisationnel) si les utilisateurs communiquent de manière cohérente ou s’engagent dans une activité de fichier dans des espaces de travail partagés au cours des 28 derniers jours.

Les scores ne sont pas fournis au niveau de l’utilisateur individuel.

## <a name="explore-more-about-teamwork-in-your-organization"></a>En savoir plus sur le travail d’équipe dans votre organisation

Nous fournissons également des informations supplémentaires sur la façon dont les membres de votre organisation travaillent ensemble. Ces métriques supplémentaires ne contribuent pas directement à votre score de productivité, mais elles sont pertinentes pour vous aider à créer un plan d’action dans le cadre de votre transformation numérique.

### <a name="breakdown-of-how-people-engage-in-shared-workspaces"></a>Répartition de la façon dont les personnes s’impliquent dans des espaces de travail partagés

:::image type="content" source="../../media/people-sharedworkspace-engagement.png" alt-text="Graphique qui montre comment les membres de votre organisation sont engagés dans des espaces de travail partagés.":::

1. **En-tête:** Affiche une répartition détaillée des différents types de travail d’équipe mesurés.
2. **Corps:** Fournit des informations sur la valeur de travailler dans des espaces de travail partagés pour aider les équipes à être plus efficaces.
3. **Visualisation:** La visualisation montre dans quelle mesure les personnes qui communiquent ou interagissent avec du contenu le font dans des espaces de travail partagés, comme suit :
      - **Envoi d’e-mails** : la partie colorée et la fraction représentent le pourcentage de personnes qui envoient des e-mails aux boîtes aux lettres de groupe. La fraction est composée de :
        - Numerator : Personnes qui envoient des e-mails à des boîtes aux lettres de groupe au cours des 28 derniers jours.
        - Dénominateur : Les personnes qui envoient des e-mails au cours des 28 derniers jours. Il s’agit du même groupe de personnes qui sont marquées comme ayant envoyé des messages électroniques dans l’aperçu principal du score de productivité des communications.
      - **Envoi de messages** : la partie colorée et la fraction représentent le pourcentage de personnes qui envoient des messages dans des canaux dans Microsoft Teams. La fraction est composée de :
        - Numerator : Personnes qui envoient des messages de canal au cours des 28 derniers jours.
        - Dénominateur : personnes qui envoient des messages de conversation ou de canal au cours des 28 derniers jours. Il s’agit du même groupe de personnes qui sont marquées comme envoyant des messages dans Microsoft Teams dans l’insight principal de la catégorie de communication dans le score de productivité.
    - **Création de contenu** : la partie colorée et la fraction représentent le pourcentage de personnes qui lisent ou créent du contenu sur Microsoft 365 SharePoint sites d’équipe.
        - Numérateur : nombre de personnes qui lisent ou créent du contenu sur Microsoft 365 sites d’équipe connectés à un groupe.
        - Dénominateur : nombre de personnes ayant accès à SharePoint, qui ont lu ou créé du contenu de tout type dans OneDrive ou SharePoint sites au cours des 28 derniers jours.
4. **Afficher le contenu associé :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="breakdown-of-workspace-engagement-by-size-and-age"></a>Répartition de l’engagement de l’espace de travail par taille et par âge

:::image type="content" source="../../media/workspace-engagement-bysizeage.png" alt-text="Graphique montrant l’engagement dans l’espace de travail, classé par taille et par âge.":::

1. **En-tête:** Affiche la catégorisation de l’engagement dans les espaces de travail, répartie par taille pour le nombre de membres dans l’espace de travail et l’âge de l’espace de travail en mois.
2. **Corps:** Fournit des informations sur la valeur d’encourager les membres de votre organisation à conserver uniquement les espaces de travail nécessaires pour promouvoir un travail d’équipe plus efficace.
3. **Visualisation:** La répartition de l’engagement s’affiche sous la forme d’une carte thermique sur deux dimensions.

      - **Taille de l’espace de travail :** Les espaces de travail sont répartis en trois catégories en fonction du nombre de membres : 2 à 10 personnes, 11 à 100 personnes et plus de 100 personnes. La &quot;catégorie Tous&quot; inclut toutes les catégories de taille.
      - **Âge de l’espace de travail :** Les espaces de travail sont classés selon le nombre de mois écoulés depuis la création de l’espace de travail. La &quot;catégorie Tous&quot; comprend toutes les catégories d’âge.

        Chaque cellule du graphique a un nombre et une couleur en fonction du pourcentage d’espaces de travail engagés qui appartiennent à cette catégorie. Les catégories d’espace de travail sont basées sur l’âge et la taille indiqués dans l’intersection de cette cellule. Par exemple, si la cellule située à l’intersection de 11 à 100 personnes et de 4 à 12 mois a une valeur de 52 %, cela signifie que 52 % des espaces de travail de 11 à 100 membres âgés de 4 à 12 mois ont une forme d’engagement. Le pourcentage est calculé comme suit :

        - **Numérateur:** Espaces de travail qui ont un engagement sous forme de communication (e-mail et messages de canal) ou d’interaction de contenu au cours des 28 derniers jours
        - **Dénominateur :** tous les espaces de travail disponibles dans votre organisation au cours des 28 derniers jours

1. **Afficher le contenu associé :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="breakdown-of-workspaces-by-level-of-engagement"></a>Répartition des espaces de travail par niveau d’engagement

:::image type="content" source="../../media/workspace-by-engagement.png" alt-text="Graphique qui montre la répartition des espaces de travail par engagement par groupes.":::

1. **En-tête:** Fournit une répartition des espaces de travail par niveau d’engagement, à l’aide de la messagerie de groupe, des messages de canal et de l’interaction de contenu.
2. **Corps:** Fournit des informations sur la valeur d’un engagement cohérent dans les espaces de travail partagés pour les rendre plus efficaces au travail d’équipe.
3. **Visualisation:** Fournit une vue des espaces de travail de votre organisation en fonction de l’intensité de l’engagement par semaine. La vue inclut des distributions pour différents types d’activités mesurés dans le travail d’équipe, en plus de tout engagement, qui couvre les catégories suivantes :
      - **E-mail de groupe :** Pourcentage d’espaces de travail qui n’ont pas de jours/1 jour/2-3 jours/4+ jours d’activité de messagerie de groupe par semaine au cours des 28 derniers jours.
      - **Messages de canal :** Pourcentage d’espaces de travail qui n’ont pas de jours/1 jour/2-3 jours/4+ jours de messages de canal par semaine au cours des 28 derniers jours.
      - **Lecture ou création de contenu :** Pourcentage d’espaces de travail qui n’ont pas de jours/1 jour/2-3 jours/4+ jours de lecture ou de création de contenu par semaine au cours des 28 derniers jours.
4. **Afficher le contenu associé :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="use-of-teams-within-microsoft-teams"></a>Utilisation d’équipes dans Microsoft Teams

:::image type="content" source="../../media/useof-teams-within-teams.png" alt-text="Graphique qui indique le nombre d’espaces de travail de partage utilisés par Microsoft Teams.":::

1. **En-tête:** Affiche le nombre d’espaces de travail partagés auxquels une équipe Microsoft Teams est associée.
2. **Corps:** Fournit des informations sur l’utilité d’avoir une équipe Microsoft Teams attachée aux espaces de travail partagés, afin de rendre les personnes associées plus efficaces au travail d’équipe.
3. **Visualisation:** La partie colorée du graphique en anneau reflète le pourcentage d’espaces de travail auxquels une équipe Microsoft Teams est attachée. Le pourcentage est calculé comme suit :

      - Numerator : nombre d’espaces de travail partagés dans votre organisation auxquels une équipe Microsoft Teams leur a été associée au cours des 28 derniers jours
      - Dénominateur : nombre d’espaces de travail partagés dans votre organisation au cours des 28 derniers jours

        Le nombre au centre du graphique en anneau représente le nombre total d’espaces de travail partagés auxquels une équipe Microsoft Teams est associée.
4. **Afficher le contenu associé :** Sélectionnez ce lien pour afficher le contenu de l’aide.

## <a name="related-content"></a>Contenu connexe

[Microsoft 365'intégrité des applications – Expériences technologiques](apps-health.md) (article)\
[Communication – Expériences de personnes](communication.md) (article)\
[Collaboration de contenu – Expériences de personnes](content-collaboration.md) (article)\
[Réunions – Expériences de personnes](meetings.md) (article)\
[Mobilité – Expériences de personnes](mobility.md) (article)\
[Contrôles de confidentialité pour le score de productivité](privacy.md) (article)
