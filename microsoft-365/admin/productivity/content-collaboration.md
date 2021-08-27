---
title: 'Score de productivité Microsoft : collaboration de contenu'
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
monikerRange: o365-worldwide
search.appverid:
- MET150
- MOE150
description: 'Détails de la collaboration de contenu : les utilisateurs peuvent obtenir un score de productivité.'
ms.openlocfilehash: fa4e84f0cf454e28cd773292f2a4065cb1252acf
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58566927"
---
# <a name="content-collaboration--people-experiences"></a>Collaboration de contenu : expériences de personnes

Le Score de productivité fournit des informations sur la transformation numérique de votre organisation tout au long de son utilisation des Microsoft 365 et des expériences technologiques qui la supportent. Le score de votre organisation reflète les mesures de l’expérience des personnes et des technologies et peut être comparé aux critères d’organisations similaires aux vôtres. La catégorie de collaboration de contenu fait partie des mesures de l’expérience utilisateur. Pour en savoir plus, consultez la vue [d’ensemble](https://privacy.microsoft.com/privacystatement)du Score [de](productivity-score.md) productivité et lisez la déclaration de confidentialité de Microsoft.

## <a name="prerequisites"></a>Configuration requise

Pour commencer à obtenir des informations sur la collaboration de contenu, les membres de votre organisation doivent être titulaires d’une licence pour :

- OneDrive Entreprise
- SharePoint
- Exchange Online

Pour plus d’informations, voir [attribuer des licences aux utilisateurs.](../manage/assign-licenses-to-users.md)

 Une fois que les utilisateurs ont été actifs dans les produits ci-dessus au moins une fois au cours des 28 derniers jours, vous commencez à voir les informations.

## <a name="why-your-organization39s-content-collaboration-score-matters"></a>Importance du score de collaboration&#39;contenu de votre organisation

Un aspect clé de la transformation numérique est la façon dont les personnes collaborent dans des fichiers. Avec votre contenu sur Microsoft 365, les utilisateurs accèdent, créent, modifient et collaborent sur du contenu avec d’autres personnes à partir de n’importe quel emplacement. Les recherches montrent que lorsque des personnes collaborent avec des fichiers en ligne, chaque personne enregistre en moyenne 100 minutes par semaine.

## <a name="how-we-calculate-the-content-collaboration-score"></a>Calcul du score de collaboration de contenu

Nous fournissons un aperçu principal qui contient les mesures clés pour la collaboration de contenu dans votre organisation. Ensuite, une infrastructure de notation détaillée ci-dessous est utilisée pour calculer le score de votre organisation.

> [!NOTE]
> Le 22 avril 2021, nous avons modifié le calcul de la mesure collaborateurs. Cela affecte l’aperçu [principal,](#primary-insight)l’aperçu [de la collaboration](#number-of-files-collaborated-on)sur les fichiers et la façon dont le score de collaboration de contenu est mesuré. Cette modification permet de réduire le bruit dans les données provenant d’agents non humains (ou bots) de Microsoft et d’autres applications tierces, ce qui permet d’obtenir un score plus précis et plus actionnable.

### <a name="primary-insight"></a>Informations principales

Microsoft OneDrive entreprise et SharePoint aider les utilisateurs à créer, lire et découvrir facilement leur contenu individuel et partagé dans Microsoft 365 sur différents appareils et applications. Ils permettent également aux utilisateurs de partager et de collaborer en toute sécurité sur du contenu. Les informations principales contiennent des informations de toutes les personnes qui peuvent OneDrive Entreprise et SharePoint. En outre, il décompose les détails sur le nombre de personnes qui lisent, créent et collaborent sur le contenu stocké dans OneDrive Entreprise et SharePoint.

:::image type="content" source="../../media/collabscore_primary.jpg" alt-text="Informations principales du score de collaboration sur les communications.":::


Les types pris en compte pour ces informations incluent les fichiers Word, Excel, PowerPoint, OneNote et PDF.

1. **En-tête :** Indique le pourcentage de personnes de votre organisation qui ont accès OneDrive ou SharePoint qui collaborent sur du contenu.
2. **Corps :** Fournit plus d’informations sur la façon dont les comportements de lecture et de création de fichiers en ligne sont liés à la collaboration sur des fichiers.
3. **Visualisation (état actuel) :**
    - Barres horizontales où les parties bleues représentent le pourcentage de personnes activées pour la collaboration de fichiers via OneDrive ou SharePoint qui ont été **lecteurs,** créateurs ou collaborateurs sur des fichiers en ligne au cours des 28 **derniers** jours.

        Elles sont définies comme suit :</br>
        **Lecteurs :** Les personnes qui accèdent aux fichiers en ligne ou les téléchargent dans OneDrive ou SharePoint.</br>
        **Créateurs :** Personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers OneDrive ou SharePoint en ligne.</br>
        **Collaborateurs :** Personnes qui collaborent avec des fichiers en ligne à l’aide OneDrive ou SharePoint. Deux personnes sont des collaborateurs si l’un d’eux lit ou modifie un application Office en ligne ou pdf après que l’autre personne l’a créé ou modifié, dans une fenêtre de 28 jours.

        > [!NOTE]
        > Les fichiers pris en compte dans la visualisation sont les fichiers Word, Excel, PowerPoint, OneNote ou PDF qui sont en ligne et enregistrés dans OneDrive ou SharePoint. 

    - La surbrillnce (numérateur/dénominateur) de la fraction est utilisée pour calculer le pourcentage exprimé dans chacune des barres horizontales.
    
      - **Lecteurs :**</br>
          - Numérateur : nombre de personnes qui accèdent ou téléchargent des fichiers en ligne OneDrive ou SharePoint au cours des 28 derniers jours</br>
          - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours</br>
      - **Créateurs :**</br>
        - Numérateur : nombre de personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours. </br> 
      - **Collaborateurs :**</br>
        - Numérateur : nombre de personnes qui ont travaillé sur des fichiers en ligne OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours

    - La valeur de référence homologue pour chacun des lecteurs, créateurs et collaborateurs est également affichée sous la mesure d’un pourcentage. En d’autres termes, la valeur du nombre de créateurs s’affiche sous la forme d’un pourcentage du nombre de personnes ayant accès à des OneDrive ou SharePoint.
    
1. **Lien vers des ressources :** Sélectionnez ce lien pour afficher des vidéos compilées et d’autres contenus d’aide connexes.


#### <a name="trend-visualization-of-primary-insight"></a>Visualisation de la tendance de l’aperçu principal

Le graphique des visualisations de tendance présente la courbe de tendance des principales mesures clés d’informations pour les lecteurs, les créateurs et les collaborateurs au cours des 180 derniers jours. Chaque point de données du graphique est un agrégat de l’activité des 28 derniers jours. Chaque point de données créateur fournit un décompte de toutes les personnes qui ont été marquées comme créateurs au cours des 28 derniers jours pour chaque date sur l’axe x.

:::image type="content" source="../../media/trendvisualization.jpg" alt-text="Graphique avec tendances pour l’aperçu principal de la collaboration.":::

### <a name="scoring-framework"></a>Infrastructure de notation

Le score de collaboration de contenu de votre organisation mesure au niveau de l’agrégation (organisation) si les utilisateurs lisent, créent ou collaborent de manière cohérente sur des fichiers Office en ligne tels que Word, Excel, PowerPoint, OneNote ou pdf, ou dans OneDrive ou SharePoint.

Les scores ne sont pas fournis au niveau de l’utilisateur individuel.

## <a name="explore-how-your-organization-collaborates"></a>Découvrir comment votre organisation collabore

Nous vous fournissons également des informations qui vous aident à gagner en visibilité sur la façon dont votre organisation collabore sur du contenu. Ces mesures supplémentaires ne contribuent pas directement à votre score de productivité, mais vous aident à créer un plan d’action dans le cadre de votre transformation numérique afin d’optimiser le mode de travail des personnes.

### <a name="creating-files-in-onedrive-or-sharepoint"></a>Création de fichiers dans OneDrive ou SharePoint

:::image type="content" source="../../media/sharepointonedrivefiles.jpg" alt-text="Graphique shows number of people who create files in OneDrive or SharePoint.":::

1. **En-tête :** Met en évidence le pourcentage de personnes actives sur Microsoft 365 Office applications qui créent des fichiers sur OneDrive ou SharePoint.
2. **Corps :** Fournit des informations sur la valeur de la création de contenu dans OneDrive et SharePoint.
3. **Visualisation :** La répartition dans la visualisation représente la mesure dans laquelle les personnes qui utilisent des applications Microsoft Office pour créer des fichiers dans OneDrive et SharePoint, comme suit :
      - **OneDrive :** La partie bleue (colorée) de la barre et la fraction de la barre représentent le pourcentage de personnes actives sur des applications Office créant du contenu sur OneDrive comme suit :
        - Numérateur : nombre de personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne dans OneDrive au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes ayant accès à des OneDrive ou SharePoint des fichiers Office au cours des 28 derniers jours.
      - **SharePoint :** La partie bleue (couleur) de la barre et la fraction de la barre représentent le pourcentage de personnes actives sur les applications Office et créent du contenu sur SharePoint comme :</br>
         - Numérateur : nombre de personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers de Office en ligne (fichiers Microsoft Word, Excel, PowerPoint ou OneNote) sur SharePoint au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes ayant accès à OneDrive ou SharePoint et ayant accédé à Office fichiers au cours des 28 derniers jours.

4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="use-of-attachments-in-email"></a>Utilisation de pièces jointes dans le courrier électronique

**Utilisation de pièces jointes dans le courrier électronique** Comprenez le nombre d’utilisateurs qui attachent des fichiers physiques par courrier électronique plutôt que des liens vers du contenu dans le cloud et surveillez la réduction de ce nombre au fil du temps.

:::image type="content" source="../../media/emailattachments.png" alt-text="Utilisation de pièces jointes de courrier électronique.":::

1. **En-tête :** Met en évidence le pourcentage de personnes qui utilisent des pièces jointes dans des e-mails qui n’ont pas été enregistrées dans des fichiers en ligne.
2. **Corps :** Fournit des informations sur la valeur du partage de liens vers des fichiers en ligne du point de vue de la collaboration et de la sécurité.
3. **Visualisation :** La répartition de la visualisation est destinée à représenter la mesure dans laquelle les personnes qui attachent du contenu dans des e-mails utilisent différents modes (fichiers non enregistrés dans des fichiers en ligne, liens vers des fichiers en ligne) :
      - **Joindre des fichiers :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes utilisant des pièces jointes dans les e-mails.
        - Numérateur : nombre de personnes qui attachent des fichiers à un e-mail qui n’ont pas été enregistrés dans un fichier en ligne au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes ayant eu accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
      - **Liens vers des fichiers en ligne :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes utilisant des pièces jointes et attachant des liens vers des fichiers dans les e-mails.
        - Numérateur : nombre de personnes qui attachent des liens vers des fichiers en ligne à des messages électroniques au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes ayant accès à Exchange et OneDrive, SharePoint ou les deux au cours des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="sharing-of-online-files"></a>Partage de fichiers en ligne

:::image type="content" source="../../media/sharingonlinefiles.png" alt-text="Graphique qui indique le nombre de personnes partageant des fichiers en ligne.":::

1. **En-tête :** Met en évidence le pourcentage de personnes qui ont accès OneDrive ou SharePoint partagent des fichiers en externe.
2. **Corps :** Fournit des informations sur les administrateurs&#39; la possibilité de modifier les paramètres de partage de fichiers dans l’organisation afin d’activer le niveau de collaboration le mieux adapté à votre organisation.
3. **Visualisation :** Représente la mesure dans laquelle les personnes qui ont accès à OneDrive ou SharePoint partagent des fichiers en interne ou en externe :
      - **En externe :** La partie bleue (colorée) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en externe.
        -  Numérateur : nombre de personnes avec qui des fichiers ont été partagés en externe au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
      - **En interne uniquement :** La partie bleue (couleur) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes qui ont accès à OneDrive ou SharePoint et partagent des fichiers en interne uniquement.
        - Numérateur : nombre de personnes qui ont partagé des fichiers en interne uniquement au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="number-of-files-collaborated-on"></a>Nombre de fichiers sur

:::image type="content" source="../../media/intensityofcollab.png" alt-text="Graphique montrant le nombre de fichiers sur qui la collaboration a été la plus importante.":::

1. **En-tête :** Met en évidence le pourcentage de personnes qui ont accès OneDrive ou SharePoint qui collaborent sur 4 fichiers ou plus.
2. **Corps :** Fournit des informations sur la façon dont les personnes peuvent tirer parti des fichiers en ligne pour une meilleure collaboration.
3. **Visualisation :** Indique une distribution des personnes qui ont accès à OneDrive ou SharePoint, en fonction du nombre de fichiers sur qui elles collaborent. Cela s’affiche dans les 4 catégories suivantes (pour chacune, la partie bleue de la barre et la fraction représentent le pourcentage de personnes ayant accès à des OneDrive ou des SharePoint qui font partie de cette catégorie) :
      - **Aucune collaboration :**
        - Numérateur : nombre de personnes qui ne collaborent sur aucun fichier au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
      - **Collaboration sur 1 à 3 fichiers :**
        - Numérateur : nombre de personnes collaborant sur 1 à 3 fichiers au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
      - **Collaboration sur 4 à 10 fichiers :**
        - Numérateur : nombre de personnes collaborant sur 4 à 10 fichiers au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
      - **Collaboration sur 11 fichiers ou plus :**
        - Numérateur : nombre de personnes collaborant sur 11 fichiers ou plus au cours des 28 derniers jours.
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou SharePoint au moins 1 des 28 derniers jours.
        
4. **Lien vers des ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="network-performance-strength-for-onedrive-and-sharepoint"></a>Niveau de performances réseau pour OneDrive et SharePoint

:::image type="content" source="../../media/networkperfstrength.png" alt-text="Graphique montrant les performances réseau pour OneDrive et SharePoint.":::

1. **En-tête :** Met en évidence le pourcentage d’appareils sur tous les appareils testés qui ont une connexion réseau médiocre OneDrive et SharePoint. 
2. **Corps :** Fournit des informations sur l’importance des performances de connexion réseau pour la collaboration. 
3. **Visualisation :** Indique un pourcentage d’appareils avec différents niveaux de performances de connectivité réseau liés aux OneDrive et SharePoint :
      - **81-100 (meilleur)**: la partie vert foncé (couleur) de la barre représente le pourcentage d’appareils avec les meilleures performances.
      - **61-80**: la partie verte (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau entre 60 et 80. 
      - **41-60**: la partie orange (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau entre 40 et 60. 
      - **21-40**: la partie rouge (colorée) de la barre représente le pourcentage d’appareils avec un score de performances réseau entre 20 et 40. 
      - **0-20**: la partie rouge foncé (couleur) de la barre représente le pourcentage d’appareils avec le pire score de performances réseau entre 0 et 20. 

## <a name="related-content"></a>Contenu associé

[Microsoft 365'état des applications : expériences technologiques](apps-health.md) (article)\
[Communication – Expériences des personnes](communication.md) (article)\
[Réunions : expériences de personnes](meetings.md) (article)\
[Mobilité : expériences utilisateur](mobility.md) (article)\
[Contrôles de confidentialité pour le Score de productivité](privacy.md) (article)\
[Travail d’équipe : expériences de](teamwork.md) personnes (article)
