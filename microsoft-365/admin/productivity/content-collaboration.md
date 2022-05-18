---
title: Insights sur la collaboration de contenu Microsoft Productivity Score
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
description: 'Détails de la collaboration de contenu : les utilisateurs obtiennent un score de productivité.'
ms.openlocfilehash: db747819b4c6a6599d1d7919c2a36f34204779a1
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466435"
---
# <a name="content-collaboration--people-experiences"></a>Collaboration de contenu – Expériences de contacts

Le score de productivité fournit des insights sur le parcours de transformation numérique de votre organisation par le biais de son utilisation de Microsoft 365 et des expériences technologiques qui le prennent en charge. Le score de votre organisation reflète les mesures des personnes et de l’expérience technologique et peut être comparé aux points de référence d’organisations similaires à la vôtre. La catégorie de collaboration de contenu fait partie des mesures de l’expérience des personnes. Pour en savoir plus, consultez la [vue d’ensemble du score de productivité](productivity-score.md) et lisez la [déclaration de confidentialité de Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="prerequisites"></a>Prerequisites

Pour commencer à utiliser les insights de collaboration de contenu, les membres de votre organisation doivent disposer d’une licence pour :

- OneDrive Entreprise
- SharePoint
- Exchange Online

Pour plus d’informations, consultez [Attribuer des licences aux utilisateurs](../manage/assign-licenses-to-users.md).

 Une fois que les personnes ont été actives dans les produits ci-dessus au moins une fois au cours des 28 derniers jours, vous commencerez à voir les insights.

## <a name="why-your-organization39s-content-collaboration-score-matters"></a>Pourquoi votre organisation&#39;le score de collaboration de contenu est important

L’un des aspects clés de la transformation numérique est la façon dont les utilisateurs collaborent dans des fichiers. Avec votre contenu sur Microsoft 365, les utilisateurs accèdent, créent, modifient et collaborent sur du contenu avec d’autres personnes à partir de n’importe quel emplacement. La recherche montre que lorsque les gens collaborent avec des fichiers en ligne, chaque personne économise en moyenne 100 minutes par semaine.

## <a name="how-we-calculate-the-content-collaboration-score"></a>Comment calculer le score de collaboration de contenu

Nous fournissons un insight principal qui contient les métriques clés pour la collaboration de contenu dans votre organisation. Ensuite, une infrastructure de scoring détaillée ci-dessous est utilisée pour ces métriques afin de calculer le score de votre organisation.

> [!NOTE]
> Le 22 avril 2021, nous avons modifié le mode de calcul de la métrique des collaborateurs. Cela affecte [l’insight principal](#primary-insight), l’insight de [collaboration de fichiers](#number-of-files-collaborated-on) et la façon dont le score de collaboration de contenu est mesuré. Cette modification permet de réduire le bruit des données provenant d’agents non humains (ou de bots) provenant de Microsoft et d’autres applications tierces, ce qui donne un score plus précis et plus exploitable.

### <a name="primary-insight"></a>Insight principal

Microsoft OneDrive Entreprise et SharePoint aident les utilisateurs à créer, lire et découvrir facilement leur contenu individuel et partagé dans Microsoft 365 à partir de différents appareils et applications. Ils permettent également aux utilisateurs de partager et de collaborer en toute sécurité sur du contenu. L’insight principal contient les informations de toutes les personnes qui peuvent utiliser OneDrive Entreprise et SharePoint. En outre, il détaille le nombre de personnes qui lisent, créent et collaborent sur du contenu stocké dans OneDrive Entreprise et SharePoint.

:::image type="content" source="../../media/collabscore_primary.jpg" alt-text="Principaux insights du score de collaboration de communication.":::


Les types pris en compte pour ces informations incluent les fichiers Word, Excel, PowerPoint, OneNote et PDF.

1. **En-tête:** Affiche le pourcentage de personnes de votre organisation qui ont accès à OneDrive ou SharePoint qui collaborent sur du contenu.
2. **Corps:** Fournit plus d’informations sur la façon dont les comportements de lecture et de création de fichiers en ligne sont liés à la collaboration sur des fichiers.
3. **Visualisation (état actuel) :**
    - Barres horizontales où les parties de couleur bleue représentent le pourcentage de personnes activées pour la collaboration de fichiers via OneDrive ou SharePoint qui ont été **lecteurs, créateurs** ou **collaborateurs sur des** fichiers en ligne au cours des 28 derniers jours.

        Elles sont définies comme suit :</br>
        **Lecteurs:** Les personnes qui accèdent ou téléchargent des fichiers en ligne dans OneDrive ou SharePoint.</br>
        **Créateurs:** Les personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers OneDrive ou SharePoint en ligne.</br>
        **Collaborateurs:** Les personnes qui collaborent avec des fichiers en ligne à l’aide de OneDrive ou de SharePoint. Deux personnes sont des collaborateurs si l’une d’elles lit ou modifie un application Office ou PDF en ligne après que l’autre personne l’a créée ou modifiée, dans une fenêtre de 28 jours.

        > [!NOTE]
        > Les fichiers pris en compte dans la visualisation sont les fichiers Word, Excel, PowerPoint, OneNote ou PDF qui sont en ligne et enregistrés dans OneDrive ou SharePoint. 

    - La surbrillance (numérateur/dénominateur) de la fraction est utilisée pour calculer le pourcentage exprimé dans chacune des barres horizontales.
    
      - **Lecteurs:**</br>
          - Numérateur : nombre de personnes qui ont accédé ou téléchargé des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
          - Dénominateur : Nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours</br>
      - **Créateurs:**</br>
        - Numérateur : nombre de personnes qui ont créé, modifié, chargé, synchronisé, archivé, copié ou déplacé des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : Nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours. </br> 
      - **Collaborateurs:**</br>
        - Numerator : Nombre de personnes ayant collaboré sur des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : Nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours

    - La valeur d’évaluation d’homologue pour chacun des lecteurs, créateurs et collaborateurs est également indiquée sous forme de pourcentage. En d’autres termes, la valeur du nombre de créateurs est indiquée sous la forme d’un pourcentage du nombre de personnes qui ont accès à OneDrive ou SharePoint.
    
1. **Lien vers des ressources :** Sélectionnez ce lien pour afficher les vidéos compilées et d’autres contenus d’aide connexes.


#### <a name="trend-visualization-of-primary-insight"></a>Visualisation des tendances de l’insight principal

Le graphique des visualisations de tendances montre la courbe de tendance des principales métriques clés d’insight pour les lecteurs, les créateurs et les collaborateurs au cours des 180 derniers jours. Chaque point de données du graphique est un agrégat d’activité pour les 28 derniers jours. Chaque point de données de créateur fournit un nombre de toutes les personnes qui ont été marquées comme créateurs au cours des 28 derniers jours pour chaque date sur l’axe x.

:::image type="content" source="../../media/trendvisualization.jpg" alt-text="Graphique avec des tendances pour l’insight principal de collaboration.":::

### <a name="scoring-framework"></a>Framework de scoring

Le score de collaboration de contenu pour votre organisation mesure au niveau de l’agrégation (organisation) si les utilisateurs lisent, créent ou collaborent régulièrement sur des fichiers Office en ligne tels que Word, Excel, PowerPoint, OneNote ou pdf, ou dans OneDrive ou SharePoint.

Les scores ne sont pas fournis au niveau de l’utilisateur individuel.

## <a name="explore-how-your-organization-collaborates"></a>Explorer la façon dont votre organisation collabore

Nous vous fournissons également des informations qui vous aident à obtenir une visibilité sur la façon dont votre organisation collabore sur du contenu. Ces métriques supplémentaires ne contribuent pas directement à votre score de productivité, mais vous aident à créer un plan d’action dans le cadre de votre transformation numérique afin d’optimiser la façon dont les gens travaillent.

### <a name="creating-files-in-onedrive-or-sharepoint"></a>Création de fichiers dans OneDrive ou SharePoint

:::image type="content" source="../../media/sharepointonedrivefiles.jpg" alt-text="Graphique montrant le nombre de personnes qui créent des fichiers dans OneDrive ou SharePoint.":::

1. **En-tête:** Met en évidence le pourcentage de personnes actives sur Microsoft 365 Office applications qui créent des fichiers sur OneDrive ou SharePoint.
2. **Corps:** Fournit des informations sur la valeur de la création de contenu dans OneDrive et SharePoint.
3. **Visualisation:** La répartition dans la visualisation représente la mesure dans laquelle les personnes qui utilisent Microsoft Office applications pour créer des fichiers dans OneDrive et SharePoint, comme suit :
      - **OneDrive :** la partie bleue (colorée) de la barre et la fraction de la barre représentent le pourcentage de personnes actives sur Office applications créant du contenu sur OneDrive comme suit :
        - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne dans OneDrive au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes qui ont accès à OneDrive ou SharePoint et qui accèdent aux fichiers office au cours des 28 derniers jours.
      - **SharePoint :** la partie bleue (colorée) de la barre et la fraction de la barre représentent le pourcentage de personnes actives sur Office applications et créent du contenu sur SharePoint comme suit :</br>
         - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne (Microsoft Word, Excel, PowerPoint ou OneNote fichiers) sur SharePoint au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes ayant accès à OneDrive ou SharePoint et ayant accédé à Office fichiers au cours des 28 derniers jours.

4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="use-of-attachments-in-email"></a>Utilisation des pièces jointes dans l’e-mail

**Utilisation des pièces jointes dans l’e-mail** Découvrez le nombre d’utilisateurs qui joignent des fichiers physiques dans l’e-mail plutôt que des liens vers du contenu dans le cloud, et surveillez la réduction de ce nombre au fil du temps.

:::image type="content" source="../../media/emailattachments.png" alt-text="Utilisation des pièces jointes de messagerie.":::

1. **En-tête:** Met en évidence le pourcentage de personnes qui utilisent des pièces jointes dans des e-mails qui n’ont pas été enregistrés dans des fichiers en ligne.
2. **Corps:** Fournit des informations sur la valeur du partage de liens vers des fichiers en ligne du point de vue de la collaboration et de la sécurité.
3. **Visualisation:** La répartition dans la visualisation est destinée à représenter la mesure dans laquelle les personnes qui joignent du contenu dans des e-mails utilisent différents modes (fichiers non enregistrés dans des fichiers en ligne, liens vers des fichiers en ligne) :
      - **Joindre des fichiers :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes utilisant des pièces jointes dans les e-mails.
        - Numérateur : nombre de personnes qui joignent des fichiers à un e-mail qui n’ont pas été enregistrés dans un fichier en ligne au cours des 28 derniers jours.
        - Dénominateur : Nombre de personnes ayant eu accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
      - **Liens vers des fichiers en ligne :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes utilisant des pièces jointes et attachant des liens à des fichiers dans les e-mails.
        - Numérateur : nombre de personnes qui joignent des liens à des fichiers en ligne à des e-mails au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes ayant accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="sharing-of-online-files"></a>Partage de fichiers en ligne

:::image type="content" source="../../media/sharingonlinefiles.png" alt-text="Graphique montrant le nombre de personnes partageant des fichiers en ligne.":::

1. **En-tête:** Met en évidence le pourcentage de personnes qui ont accès à des OneDrive ou SharePoint qui partagent des fichiers en externe.
2. **Corps:** Fournit des informations sur les administrateurs&#39; possibilité de modifier les paramètres de partage de fichiers dans l’organisation afin d’activer le niveau de collaboration le mieux adapté à votre organisation.
3. **Visualisation:** Représente la mesure dans laquelle les personnes qui ont accès à OneDrive ou SharePoint partagent des fichiers en interne ou en externe :
      - **Externe:** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en externe.
        -  Numerator : nombre de personnes avec lesquelles des fichiers ont été partagés en externe au cours des 28 derniers jours
        - Dénominateur : Nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **En interne uniquement :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en interne uniquement.
        - Numerator : nombre de personnes qui ont partagé des fichiers en interne uniquement au cours des 28 derniers jours
        - Dénominateur : Nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="number-of-files-collaborated-on"></a>Nombre de fichiers sur lequel la collaboration a été effectuée

:::image type="content" source="../../media/intensityofcollab.png" alt-text="Graphique montrant le nombre de fichiers sur lequel le plus de fichiers ont été collaborés.":::

1. **En-tête:** Met en évidence le pourcentage de personnes ayant accès à OneDrive ou SharePoint qui collaborent sur 4 fichiers ou plus.
2. **Corps:** Fournit des informations sur la façon dont les utilisateurs peuvent tirer parti des fichiers en ligne pour une meilleure collaboration.
3. **Visualisation:** Affiche une distribution des personnes qui ont accès à OneDrive ou SharePoint, en fonction du nombre de fichiers sur lesquels elles collaborent. Cela s’affiche dans les 4 catégories suivantes (pour chacune d’elles, la partie bleue de la barre et la fraction représentent le pourcentage de personnes ayant accès à OneDrive ou SharePoint qui appartiennent à cette catégorie) :
      - **Aucune collaboration :**
        - Numérateur : nombre de personnes qui n’ont pas collaboré sur des fichiers au cours des 28 derniers jours.
        - Dénominateur : Nombre total de personnes ayant accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur 1 à 3 fichiers :**
        - Numérateur : nombre de personnes qui ont collaboré sur 1 à 3 fichiers au cours des 28 derniers jours.
        - Dénominateur : Nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur 4 à 10 fichiers :**
        - Numérateur : nombre de personnes qui ont collaboré sur 4 à 10 fichiers au cours des 28 derniers jours.
        - Dénominateur : Nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur 11 fichiers ou plus :**
        - Numérateur : nombre de personnes qui collaborent sur 11 fichiers ou plus au cours des 28 derniers jours.
        - Dénominateur : Nombre total de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours.
        
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="network-performance-strength-for-onedrive-and-sharepoint"></a>Puissance des performances réseau pour les OneDrive et les SharePoint

:::image type="content" source="../../media/networkperfstrength.png" alt-text="Graphique montrant les performances réseau des OneDrive et des SharePoint.":::

1. **En-tête:** Met en évidence le pourcentage d’appareils sur tous les appareils testés qui ont une connexion réseau médiocre à OneDrive et SharePoint. 
2. **Corps:** Fournit des informations sur la raison pour laquelle les performances de connexion réseau sont importantes pour la collaboration. 
3. **Visualisation:** Affiche un pourcentage d’appareils avec différents niveaux de performances de connectivité réseau liés aux OneDrive et aux SharePoint :
      - **81-100 (meilleur)** : la partie vert foncé (en couleur) de la barre représente le pourcentage d’appareils présentant les meilleures performances.
      - **61-80** : La partie verte (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau compris entre 60 et 80. 
      - **41-60** : La partie orange (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau compris entre 40 et 60. 
      - **21-40** : La partie rouge (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau compris entre 20 et 40. 
      - **0-20** : La partie rouge foncé (couleur) de la barre représente le pourcentage d’appareils dont le score de performance réseau est le plus mauvais entre 0 et 20. 

## <a name="related-content"></a>Contenu connexe

[Microsoft 365'intégrité des applications – Expériences technologiques](apps-health.md) (article)\
[Communication – Expériences de personnes](communication.md) (article)\
[Réunions – Expériences de personnes](meetings.md) (article)\
[Mobilité – Expériences de personnes](mobility.md) (article)\
[Contrôles de confidentialité pour le score de productivité](privacy.md) (article)\
[Travail d’équipe – Expériences de personnes](teamwork.md) (article)
