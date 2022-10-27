---
title: Score d’adoption Microsoft - Collaboration de contenu
f1.keywords:
- NOCSH
ms.author: camillepack
author: camillepack
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
monikerRange: o365-worldwide
search.appverid:
- MET150
- MOE150
description: 'Détails de la collaboration de contenu : les utilisateurs rencontrent le score d’adoption.'
ms.openlocfilehash: 6db8ea417919ba176023a692d26c8083a5b902a2
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726902"
---
# <a name="content-collaboration--people-experiences"></a>Collaboration de contenu : expériences Personnes

Le score d’adoption fournit des insights sur le parcours de transformation numérique de votre organisation grâce à son utilisation de Microsoft 365 et aux expériences technologiques qui le prennent en charge. Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé à des points de référence d’organisations similaires à la vôtre. La catégorie de collaboration de contenu fait partie des mesures des expériences de personnes. Pour en savoir plus, consultez la [vue d’ensemble du score d’adoption](adoption-score.md) et lisez la [Déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Configuration requise

Pour commencer à utiliser les insights de collaboration de contenu, les membres de votre organisation doivent disposer d’une licence pour :

- OneDrive Entreprise
- SharePoint
- Exchange Online

Pour plus d’informations, consultez [Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md).

 Une fois que les personnes ont été actives dans les produits ci-dessus au moins une fois au cours des 28 derniers jours, vous commencez à voir les insights.

## <a name="why-your-organization39s-content-collaboration-score-matters"></a>Pourquoi votre organisation&#39;le score de collaboration de contenu est important

L’un des aspects clés de la transformation numérique est la façon dont les gens collaborent dans les fichiers. Avec votre contenu sur Microsoft 365, les utilisateurs accèdent au contenu, créent, modifient et collaborent avec d’autres personnes à partir de n’importe quel emplacement. Les recherches montrent que lorsque des personnes collaborent avec des fichiers en ligne, chaque personne enregistre en moyenne 100 minutes par semaine.

## <a name="how-we-calculate-the-content-collaboration-score"></a>Comment nous calculons le score de collaboration de contenu

Nous fournissons un insight principal qui contient les métriques clés pour la collaboration de contenu dans votre organisation. Ensuite, une infrastructure de scoring détaillée ci-dessous est utilisée pour ces métriques afin de calculer le score de votre organisation.

> [!NOTE]
> Le 22 avril 2021, nous avons modifié la façon dont la métrique collaborateurs est calculée. Cela affecte [l’insight principal](#primary-insight), l’insight de [collaboration de fichiers](#number-of-files-collaborated-on) et la façon dont le score de collaboration de contenu est mesuré. Cette modification permet de réduire le bruit dans les données provenant d’agents non humains (ou de bots) de Microsoft et d’autres applications tierces, ce qui aboutit à un score plus précis et exploitable.

### <a name="primary-insight"></a>Insights principaux

Microsoft OneDrive Entreprise et SharePoint aident les utilisateurs à créer, lire et découvrir facilement leur contenu individuel et partagé dans Microsoft 365 à partir d’appareils et d’applications. Ils permettent également aux utilisateurs de partager et de collaborer en toute sécurité sur du contenu. L’insight principal contient les informations de toutes les personnes qui peuvent utiliser OneDrive Entreprise et SharePoint. En outre, il détaille le nombre de personnes qui lisent, créent et collaborent sur du contenu stocké dans OneDrive Entreprise et SharePoint.

:::image type="content" source="../../media/collabscore_primary.png" alt-text="Insights principaux du score de collaboration de communication.":::

Les types pris en compte pour ces informations incluent les fichiers Word, Excel, PowerPoint, OneNote et PDF.

1. **En-tête:** Affiche le pourcentage de personnes de votre organisation qui ont accès à OneDrive ou SharePoint qui collaborent sur du contenu.
2. **Corps:** Fournit plus d’informations sur la façon dont les comportements de lecture et de création de fichiers en ligne sont liés à la collaboration sur des fichiers.
3. **Visualisation (état actuel) :**
    - Barres horizontales où les parties bleues représentent le pourcentage de personnes activées pour la collaboration de fichiers via OneDrive ou SharePoint qui ont été **lecteurs, créateurs** ou **collaborateurs sur des** fichiers en ligne au cours des 28 derniers jours.

        Elles sont définies comme suit :</br>
        **Lecteurs :** Personnes qui accèdent à des fichiers en ligne ou les téléchargent dans OneDrive ou SharePoint.</br>
        **Créateurs :** Personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent en ligne des fichiers OneDrive ou SharePoint.</br>
        **Collaborateurs :** Personnes qui collaborent avec des fichiers en ligne à l’aide de OneDrive ou SharePoint. Deux personnes sont des collaborateurs si l’une d’elles lit ou modifie une application Office en ligne ou un fichier PDF après que l’autre personne l’a créée ou modifiée, dans une fenêtre de 28 jours.

        > [!NOTE]
        > Les fichiers pris en compte dans la visualisation sont des fichiers Word, Excel, PowerPoint, OneNote ou PDF qui sont en ligne et enregistrés dans OneDrive ou SharePoint.

    - La mise en surbrillance (numérateur/dénominateur) de la fraction est utilisée pour calculer le pourcentage exprimé dans chacune des barres horizontales.
      - **Lecteurs:**</br>
          - Numérateur : nombre de personnes qui accèdent à des fichiers en ligne ou les téléchargent dans OneDrive ou SharePoint au cours des 28 derniers jours 
          - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours</br>
      - **Créateurs:**</br>
        - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours. </br>
      - **Collaborateurs:**</br>
        - Numérateur : nombre de personnes qui ont collaboré sur des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours </br>
        - Dénominateur : nombre de personnes ayant eu accès à pour OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours

    - La valeur du benchmark de pair pour chacun des lecteurs, créateurs et collaborateurs est également indiquée sous la forme d’un pourcentage. En d’autres termes, la valeur du nombre de créateurs est indiquée sous la forme d’un pourcentage du nombre de personnes ayant accès à OneDrive ou SharePoint.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher les vidéos compilées et d’autres contenus d’aide associés.

#### <a name="trend-visualization-of-primary-insight"></a>Visualisation des tendances de l’insight principal

Le graphique des visualisations de tendances montre la courbe de tendance des métriques clés d’insight primaires pour les lecteurs, les créateurs et les collaborateurs au cours des 180 derniers jours. Chaque point de données du graphique est un agrégat de l’activité des 28 derniers jours. Chaque point de données du créateur fournit le nombre de toutes les personnes qui ont été étiquetées comme créateurs au cours des 28 derniers jours pour chaque date sur l’axe X.

:::image type="content" source="../../media/trendvisualization.jpg" alt-text="Graphique avec des tendances pour les insights principaux de collaboration.":::

### <a name="scoring-framework"></a>Infrastructure de scoring

Le score de collaboration de contenu pour votre organisation mesure au niveau d’un agrégat (organisation) si les utilisateurs lisent, créent ou collaborent de manière cohérente sur des fichiers Office en ligne tels que Word, Excel, PowerPoint, OneNote ou PDF, ou dans OneDrive ou SharePoint.

Les scores ne sont pas fournis au niveau de l’utilisateur individuel.

## <a name="explore-how-your-organization-collaborates"></a>Explorer la façon dont votre organisation collabore

Nous vous fournissons également des informations qui vous aident à obtenir une visibilité sur la façon dont votre organisation collabore sur le contenu. Ces métriques supplémentaires ne contribuent pas directement à votre score d’adoption, mais vous aident à créer un plan d’action dans le cadre de votre transformation numérique afin d’optimiser la façon dont les gens travaillent.

### <a name="creating-files-in-onedrive-or-sharepoint"></a>Création de fichiers dans OneDrive ou SharePoint

:::image type="content" source="../../media/sharepointonedrivefiles.jpg" alt-text="Graphique montrant le nombre de personnes qui créent des fichiers dans OneDrive ou SharePoint.":::

1. **En-tête:** Met en évidence le pourcentage de personnes actives sur les applications Microsoft 365 Office qui créent des fichiers sur OneDrive ou SharePoint.
2. **Corps:** Fournit des informations sur la valeur de la création de contenu dans OneDrive et SharePoint.
3. **Visualisation:** La répartition dans la visualisation représente la mesure dans laquelle les personnes qui utilisent les applications Microsoft Office pour créer des fichiers dans OneDrive et SharePoint, comme suit :
      - **OneDrive :** La partie bleue (colorée) de la barre et la fraction sur la barre représentent le pourcentage de personnes actives sur les applications Office qui créent du contenu sur OneDrive comme suit :
        - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne dans OneDrive au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes ayant accès à OneDrive ou SharePoint et ayant accès aux fichiers office au cours des 28 derniers jours.
      - **Sharepoint:** La partie bleue (colorée) de la barre et la fraction sur la barre représentent le pourcentage de personnes qui sont actives sur les applications Office et qui créent du contenu sur SharePoint comme suit :</br>
         - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne (fichiers Microsoft Word, Excel, PowerPoint ou OneNote) sur SharePoint au cours des 28 derniers jours. </br>
         - Dénominateur : nombre de personnes qui ont accès à OneDrive ou SharePoint et qui ont accédé à des fichiers Office au cours des 28 derniers jours.

4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="use-of-attachments-in-email"></a>Utilisation des pièces jointes dans les e-mails

**Utilisation des pièces jointes dans les e-mails** Comprenez le nombre d’utilisateurs qui joignent des fichiers physiques dans des e-mails plutôt que des liens vers du contenu dans le cloud, et surveillez la réduction de ce nombre au fil du temps.

:::image type="content" source="../../media/emailattachments.png" alt-text="Utilisation de pièces jointes d’e-mail.":::

1. **En-tête:** Met en évidence le pourcentage de personnes qui utilisent des pièces jointes dans des e-mails qui n’ont pas été enregistrés dans des fichiers en ligne.
2. **Corps:** Fournit des informations sur la valeur du partage de liens vers des fichiers en ligne du point de vue de la collaboration et de la sécurité.
3. **Visualisation:** La répartition de la visualisation est destinée à représenter la mesure dans laquelle les personnes qui joignent du contenu dans des e-mails utilisent différents modes (fichiers non enregistrés dans des fichiers en ligne, liens vers des fichiers en ligne) :
      - **Joindre des fichiers :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) sur la barre représentent le pourcentage de personnes utilisant des pièces jointes dans les e-mails.
        - Numérateur : nombre de personnes qui joignent des fichiers à un e-mail qui n’ont pas été enregistrés dans un fichier en ligne au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes ayant eu accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
      - **Liens vers des fichiers en ligne :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) sur la barre représentent le pourcentage de personnes qui utilisent des pièces jointes et joignent des liens vers des fichiers dans des e-mails.
        - Numérateur : nombre de personnes joignant des liens vers des fichiers en ligne vers des e-mails au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes ayant accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="sharing-of-online-files"></a>Partage de fichiers en ligne

:::image type="content" source="../../media/sharingonlinefiles.png" alt-text="Graphique montrant le nombre de personnes partageant des fichiers en ligne.":::

1. **En-tête:** Met en surbrillance le pourcentage de personnes qui ont accès à pour OneDrive ou SharePoint qui partagent des fichiers en externe.
2. **Corps:** Fournit des informations sur les administrateurs&#39; possibilité de modifier les paramètres de partage de fichiers dans l’organisation pour activer le niveau de collaboration le mieux adapté à votre organisation.
3. **Visualisation:** Représente la mesure dans laquelle les personnes qui ont accès à OneDrive ou SharePoint partagent des fichiers en interne ou en externe :
      - **Externe:** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) sur la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en externe.
        - Numérateur : nombre de personnes qui ont partagé des fichiers en externe avec au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **En interne uniquement :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) sur la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en interne uniquement.
        - Numérateur : nombre de personnes qui ont partagé des fichiers en interne uniquement au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="number-of-files-collaborated-on"></a>Nombre de fichiers sur 2000

:::image type="content" source="../../media/intensityofcollab.png" alt-text="Graphique montrant le nombre de fichiers sur montrant le plus grand nombre de collaboration.":::

1. **En-tête:** Met en évidence le pourcentage de personnes qui ont accès à OneDrive ou SharePoint qui collaborent sur 4 fichiers ou plus.
2. **Corps:** Fournit des informations sur la façon dont les utilisateurs peuvent tirer parti des fichiers en ligne pour une meilleure collaboration.
3. **Visualisation:** Affiche une distribution des personnes qui ont accès à OneDrive ou SharePoint, en fonction du nombre de fichiers sur lesquels elles collaborent. Ceci est illustré par les 4 catégories suivantes (pour chacune, la partie bleue de la barre et la fraction représente le pourcentage de personnes qui ont accès à OneDrive ou SharePoint qui appartiennent à cette catégorie) :
      - **Aucune collaboration :**
        - Numérateur : nombre de personnes qui ne collaborent sur aucun fichier au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur les fichiers 1-3 :**
        - Numérateur : nombre de personnes qui collaborent sur 1 à 3 fichiers au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur les fichiers 4-10 :**
        - Numérateur : nombre de personnes qui collaborent sur 4 à 10 fichiers au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur 11 fichiers ou plus :**
        - Numérateur : nombre de personnes qui collaborent sur au moins 11 fichiers au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="network-performance-strength-for-onedrive-and-sharepoint"></a>Puissance des performances réseau pour OneDrive et SharePoint

:::image type="content" source="../../media/networkperfstrength.png" alt-text="Graphique montrant les performances réseau pour OneDrive et SharePoint.":::

1. **En-tête:** Met en évidence le pourcentage d’appareils sur tous les appareils testés qui ont une connexion réseau médiocre à OneDrive et SharePoint.
2. **Corps:** Fournit des informations sur l’importance des performances de connexion réseau pour la collaboration. 
3. **Visualisation:** Affiche un pourcentage d’appareils avec différents niveaux de performances de connectivité réseau liés à OneDrive et SharePoint :
      - **81-100 (meilleur)** : la partie vert foncé (de couleur) de la barre représente le pourcentage d’appareils présentant les meilleures performances.
      - **61-80** : la partie verte (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 60 et 80.
      - **41-60** : la partie orange (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 40 et 60.
      - **21-40** : la partie rouge (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 20 et 40.
      - **0-20** : la partie rouge foncé (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est le plus mauvais entre 0 et 20.

## <a name="view-content-collaboration-trends-over-time"></a>Afficher les tendances de la collaboration de contenu au fil du temps

Pour chacun des insights ci-dessus, vous pouvez voir la tendance des métriques au fil du temps en sélectionnant une option dans la liste déroulante ci-dessous :

![Tendances au fil du temps.](../../media/trends-over-time.png)

Une fois que vous avez sélectionné une option, les graphiques du rapport sont mis à jour pour afficher une tendance au fil du temps plutôt qu’un instantané du mois dernier.

## <a name="related-content"></a>Contenu associé

[Intégrité des applications Microsoft 365 – Expériences technologiques](apps-health.md) (article)\
[Communication – expériences Personnes](communication.md) (article)\
[Réunions – expériences Personnes](meetings.md) (article)\
[Mobilité – expériences Personnes](mobility.md) (article)\
[Contrôles de confidentialité pour le score d’adoption](privacy.md) (article)\
[Travail d’équipe – expériences Personnes](teamwork.md) (article)
