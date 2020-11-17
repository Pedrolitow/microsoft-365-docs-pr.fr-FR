---
title: Score de productivité Microsoft-collaboration sur le contenu
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
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
description: Détails de la collaboration de contenu-score de productivité des personnes.
ms.openlocfilehash: 99f5a897dc372a45be31a8c01379c6fe4c980de9
ms.sourcegitcommit: 2d3e85173c65a9e0ce92624a80ed7a9839f5b8bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49123445"
---
# <a name="content-collaboration--people-experiences"></a>Collaboration de contenu : expériences de personnes

Le score de productivité vous permet de transformer le travail réalisé avec des mesures concernant la façon dont les utilisateurs utilisent les applications Microsoft 365 et les expériences technologiques qui les prennent en charge. Le score reflète les performances de votre organisation&#39;s pour les expériences des personnes et des technologies et compare votre score avec des organisations comme les vôtres. La collaboration de contenu est l’une des mesures qui relève de l’expérience des personnes. Consultez la [rubrique vue d’ensemble du score de productivité](productivity-score.md).

## <a name="why-your-organization39s-content-collaboration-score-matters"></a>Pourquoi les résultats de la collaboration de contenu de votre organisation&#39;s.

Un pilier fondamental de la productivité de l’organisation est la manière dont les utilisateurs collaborent dans des fichiers. Avec votre contenu sur Microsoft 365, les utilisateurs accèdent, créent, modifient et collaborent sur du contenu avec d’autres personnes depuis n’importe quel emplacement. Des recherches montrent que lorsque des personnes collaborent avec des fichiers en ligne, chaque personne enregistre une moyenne de 100 minutes par semaine. [Consultez la rubrique Evidence](https://vc2prod.blob.core.windows.net/vc-resources/TEIStudies/TEI%20of%20Microsoft%20365%20E5%20-%20Oct%202018.pdf).

## <a name="how-we-calculate-the-content-collaboration-score"></a>Comment nous calculons le score de collaboration de contenu

Nous fournissons une vue principale qui contient les mesures clés pour la collaboration de contenu. Ensuite, une infrastructure de score détaillée ci-dessous est utilisée pour que ces mesures calculent votre score.

### <a name="primary-insight"></a>Vue d’analyse

Microsoft OneDrive entreprise et SharePoint permettent aux utilisateurs de créer, lire et découvrir facilement leurs contenus individuels et partagés dans Microsoft 365 à partir d’appareils et d’applications. Ils permettent également aux utilisateurs de partager et de collaborer en toute sécurité sur le contenu. Le principal aperçu contient des informations sur les personnes qui peuvent utiliser OneDrive entreprise et SharePoint. En outre, il détaille les détails du nombre de personnes à lire, créer et collaborer sur le contenu stocké dans OneDrive entreprise et SharePoint.

:::image type="content" source="../../media/collabscore_primary.jpg" alt-text="Perspectives principales du score de collaboration de communication.":::


Les types pris en compte pour ces informations incluent les fichiers Word, Excel, PowerPoint, OneNote et PDF.

1. **En-tête :** Indique le pourcentage de personnes qui ont accès à OneDrive ou SharePoint collaborant sur le contenu.
2. **Body :** Fournit plus d’informations sur la façon dont les comportements de lecture et de création de fichiers en ligne sont liés à la collaboration sur des fichiers.
3. **Visualisation (état actuel) :**
    - Barres horizontales où les parties de couleur bleue représentent le pourcentage de personnes activées pour la collaboration de fichiers via OneDrive ou SharePoint qui sont des **lecteurs, créateurs** ou **collaborateurs** sur des fichiers en ligne au cours des 28 derniers jours.

        Elles sont définies comme suit :</br>
        **Lecteurs :** Personnes qui accèdent à ou téléchargent des fichiers en ligne dans OneDrive ou SharePoint.</br>
        **Créateurs :** Les personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers OneDrive ou SharePoint en ligne.</br>
        **Collaborateurs :** Personnes qui collaborent avec des fichiers en ligne à l’aide de OneDrive ou de SharePoint. Deux personnes sont des collaborateurs, si l’une d’elles lit ou modifie une application ou un fichier PDF Office Online après que l’autre personne l’a créée ou modifié, dans une fenêtre de 28 jours.

        > [!NOTE]
        > Les fichiers considérés dans la visualisation sont des fichiers Word, Excel, PowerPoint, OneNote ou PDF qui sont en ligne et enregistrés dans OneDrive ou SharePoint. 

    - Mettez en surbrillance le (numérateur/dénominateur) de la fraction utilisée pour calculer le pourcentage exprimé dans chacune des barres horizontales.
    
      - **Tirer**</br>
          - Numérateur : nombre de personnes qui accèdent ou téléchargent des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
          - Dénominateur : nombre de personnes ayant accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours</br>
      - **Créateurs**</br>
        - Numérateur : nombre de personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours. </br> 
      - **Collaborateurs**</br>
        - Numérateur : nombre de personnes qui ont collaboré sur des fichiers en ligne dans OneDrive ou SharePoint au cours des 28 derniers jours</br>
        - Dénominateur : nombre de personnes ayant eu accès à OneDrive ou SharePoint pendant au moins 1 des 28 derniers jours

    - La valeur de test de l’homologue pour chacun des lecteurs, créateurs et collaborateurs est également indiquée sous la forme d’un pourcentage. En d’autres termes, la valeur du nombre de créateurs est affichée sous la forme d’un pourcentage du nombre de personnes ayant accès à OneDrive ou à SharePoint.
    
1. **Lien vers les ressources :** Sélectionnez ce lien pour afficher les vidéos assemblées et d’autres contenus d’aide connexes.


#### <a name="trend-visualization-of-primary-insight"></a>Visualisation des tendances du principal aperçu

Le graphique de visualisations de tendances affiche la ligne de tendance des mesures principales de l’analyse des lecteurs, créateurs et collaborateurs au cours des 180 derniers jours. Chaque point de données du graphique est un agrégat des activités pendant les 28 derniers jours. Chaque point de données du créateur fournit le décompte de toutes les personnes qui ont été marquées comme créateurs au cours des 28 derniers jours pour chaque date de l’axe x.

:::image type="content" source="../../media/trendvisualization.jpg" alt-text="Graphique présentant des tendances pour la collaboration principale.":::

### <a name="scoring-framework"></a>Infrastructure de score

Le score de collaboration de contenu mesure si les utilisateurs lisent, créent ou collaborent constamment sur des fichiers Office en ligne, tels que Word, Excel, PowerPoint, OneNote ou PDF, dans OneDrive ou SharePoint.

## <a name="explore-how-your-organization-collaborates"></a>Exploration du mode de collaboration de votre organisation

Nous vous proposons également des informations qui vous aideront à mieux comprendre comment les personnes de votre organisation collaborent sur le contenu. Ces mesures supplémentaires ne contribuent pas directement à votre score de productivité, mais vous aident à créer un plan d’action pour optimiser la manière dont les personnes travaillent.

### <a name="creating-files-to-onedrive-or-sharepoint"></a>Création de fichiers dans OneDrive ou SharePoint

:::image type="content" source="../../media/sharepointonedrivefiles.jpg" alt-text="Graphique illustrant le nombre de personnes qui créent des fichiers dans OneDrive ou SharePoint":::

1. **En-tête :** Met en surbrillance le pourcentage de personnes actives sur les applications Office 365 Microsoft qui créent des fichiers sur OneDrive ou SharePoint.
2. **Body :** Fournit des informations sur la valeur de la création de contenu dans OneDrive et SharePoint.
3. **Visualisation :** La répartition dans la visualisation représente la mesure dans laquelle les personnes qui utilisent des applications Microsoft Office peuvent créer des fichiers dans OneDrive et SharePoint, comme suit :
      - **OneDrive :** La partie bleue (en couleur) de la barre et la fraction de la barre représentent le pourcentage de personnes actives sur les applications Office qui créent du contenu sur OneDrive, comme suit :
        - Numérateur : nombre de personnes qui créent, modifient, téléchargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne dans OneDrive au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes qui ont accès à OneDrive ou à SharePoint et accèdent aux fichiers Office au cours des 28 derniers jours.
      - **SharePoint :** La partie bleue (en couleur) de la barre et la fraction sur la barre représentent le pourcentage de personnes actives sur les applications Office et créent du contenu sur SharePoint en tant que :</br>
         - Numérateur : nombre de personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers Office en ligne (fichiers Microsoft Word, Excel, PowerPoint ou OneNote) sur SharePoint au cours des 28 derniers jours.</br>
        - Dénominateur : nombre de personnes ayant accès à OneDrive ou à SharePoint et ayant accédé à des fichiers Office au cours des 28 derniers jours.

4. **Lien vers les ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="use-of-attachments-in-email"></a>Utilisation de pièces jointes dans les messages électroniques

:::image type="content" source="../../media/emailattachments.png" alt-text="Utilisation de pièces jointes de courrier électronique.":::

1. **En-tête :** Met en surbrillance le pourcentage de personnes qui utilisent des pièces jointes dans des messages électroniques qui n’ont pas été enregistrés dans OneDrive ou SharePoint.
2. **Body :** Fournit des informations sur la valeur de partage de liens vers des fichiers en ligne du point de vue de la sécurité et de la collaboration.
3. **Visualisation :** La répartition dans la visualisation est conçue pour indiquer dans quelle mesure les personnes qui joignent du contenu dans les courriers électroniques utilisent différents modes (fichiers qui ne se trouvent pas sur OneDrive ou SharePoint ; liens vers des fichiers en ligne et liens incorporés dans l’e-mail) :
      - **Joindre des fichiers :** La partie bleue (en couleur) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes qui utilisent des pièces jointes dans les courriels.
        - Numérateur : nombre de personnes qui joignent un fichier à un courrier électronique qui n’ont pas été enregistrées dans OneDrive ou SharePoint au cours des 28 derniers jours
        - Dénominateur : nombre de personnes utilisant des pièces jointes dans n’importe quel formulaire dans les messages électroniques au cours des 28 derniers jours
      - **Liens vers des fichiers en ligne :** La partie bleue (en couleur) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes utilisant des pièces jointes et la liaison de liens à des fichiers dans des courriers électroniques.
        - Numérateur : nombre de personnes qui se connectent aux fichiers en ligne (enregistrés sur OneDrive ou SharePoint) au cours des 28 derniers jours.
        - Dénominateur : nombre de personnes utilisant des pièces jointes dans n’importe quel formulaire dans les messages électroniques au cours des 28 derniers jours.
      - **Incorporer les liens dans les messages électroniques :** La partie bleue (en couleur) de la barre et la fraction sur la barre représentent le pourcentage de personnes qui incorporent les liens dans le corps des messages électroniques.
        - Numérateur : nombre de contacts incorporant des liens dans les e-mails de fichiers en ligne (enregistrés dans OneDrive ou SharePoint) avec au cours des 28 derniers jours
        - Dénominateur : nombre de personnes utilisant des pièces jointes dans n’importe quel formulaire dans les messages électroniques au cours des 28 derniers jours
4. **Lien vers les ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="sharing-of-online-files"></a>Partage de fichiers en ligne

:::image type="content" source="../../media/sharingonlinefiles.png" alt-text="Graphique illustrant le nombre de personnes partageant des fichiers en ligne.":::

1. **En-tête :** Met en surbrillance le pourcentage de personnes ayant accès à OneDrive ou SharePoint qui partagent des fichiers en externe.
2. **Body :** Fournit des informations sur les administrateurs&#39; capacité à modifier les paramètres de partage de fichiers dans l’Organisation pour activer le niveau de collaboration le mieux adapté à votre organisation.
3. **Visualisation :** Représente la mesure dans laquelle les personnes ayant accès à OneDrive ou SharePoint partagent des fichiers en interne ou en externe :
      - En **externe :** La partie bleue (en couleur) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes ayant accès à OneDrive ou à SharePoint et partageant des fichiers en externe.
        -  Numérateur : nombre de personnes ayant partagé des fichiers en externe au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours
      - **Uniquement en interne :** La partie bleue (en couleur) de la barre et la fraction (numérateur/dénominateur) de la barre représentent le pourcentage de personnes ayant accès à OneDrive ou à SharePoint et partageant des fichiers en interne uniquement.
        - Numérateur : nombre de personnes ayant partagé des fichiers en interne uniquement au cours des 28 derniers jours
        - Dénominateur : nombre total de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours
4. **Lien vers les ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="number-of-files-collaborated-on"></a>Nombre de fichiers sur lesquels la collaboration est activée

:::image type="content" source="../../media/intensityofcollab.png" alt-text="Graphique illustrant le nombre de fichiers qui ont été le plus en collaboration.":::

1. **En-tête :** Cela met en évidence le pourcentage de personnes ayant accès à OneDrive ou SharePoint collaborant sur 4 fichiers ou plus.
2. **Body :** Cela fournit des informations sur la façon dont les utilisateurs peuvent tirer parti des fichiers en ligne pour une meilleure collaboration.
3. **Visualisation :** Cela montre une distribution des personnes ayant accès à OneDrive ou SharePoint, en fonction du nombre de fichiers sur lesquels ils collaborent. Cette procédure est illustrée par les 4 catégories suivantes (pour chacune, la partie bleue de la barre et la fraction représentent le pourcentage de personnes ayant accès à OneDrive ou SharePoint qui appartiennent à cette catégorie) :
      - **Aucune collaboration :**
        - **Numérateur :** Nombre de personnes ne collaborant pas sur les fichiers au cours des 28 derniers jours
        - **Dénominateur :** Nombre total de personnes ayant accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur les fichiers 1-3 :**
        - **Numérateur :** Nombre de personnes collaborant sur 1-3 fichiers au cours des 28 derniers jours
        - **Dénominateur :** Nombre total de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur les fichiers 4-10 :**
        - **Numérateur :** Nombre de personnes collaborant sur 4-10 fichiers au cours des 28 derniers jours
        - **Dénominateur :** nombre total de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours.
      - **Collaboration sur 11 fichiers ou plus :**
        - **Numérateur :** Nombre de personnes collaborant sur 11 ou plusieurs fichiers au cours des 28 derniers jours
        - **Dénominateur :** Nombre total de personnes ayant eu accès à OneDrive ou à SharePoint pendant au moins 1 des 28 derniers jours.
        
4. **Lien vers les ressources :** Sélectionnez ce lien pour afficher le contenu de l’aide.

### <a name="network-performance-strength-for-onedrive-and-sharepoint"></a>Performances réseau pour OneDrive et SharePoint

:::image type="content" source="../../media/networkperfstrength.png" alt-text="Graphique illustrant les performances réseau pour OneDrive et SharePoint.":::

1. **En-tête :** Met en surbrillance le pourcentage d’appareils sortants de tous les tests ayant une mauvaise connexion réseau à OneDrive et SharePoint. 
2. **Body :** Fournit des informations sur la raison pour laquelle les performances de connexion réseau sont importantes pour la collaboration. 
3. **Visualisation :** indique un pourcentage d’appareils avec différents niveaux de performances de connectivité réseau en ce qui concerne OneDrive et SharePoint :
      - **80-100 (recommandé)**: la partie vert foncé (coloré) de la barre représente le pourcentage d’appareils avec les meilleures performances.
      - **60-80**: la partie verte (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 60-80. 
      - **40-60**: la partie orange (colorée) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 40-60. 
      - **20-40**: la partie rouge (en couleur) de la barre représente le pourcentage d’appareils dont le score de performances réseau est compris entre 20-40. 
      - **0-20**: la partie rouge foncé (en couleur) de la barre représente le pourcentage d’appareils dont le score de performances réseau est le pire entre 0-20. 

### <a name="people-in-your-organization"></a>Personnes de votre organisation

Cette section vous aide à agir sur les mesures que vous souhaitez mettre en évidence en fournissant des détails au niveau de l’utilisateur sur les activités pertinentes à toutes les informations affichées.

Les colonnes suivantes sont présentées dans le tableau au niveau de l’utilisateur :

- **Username**  est l’adresse de messagerie de l’utilisateur.
- **Nom d’affichage**  est le nom complet de l’utilisateur.
- La date de la **dernière activité** correspond à la dernière fois que l’utilisateur a effectué une activité relative à l’un des Insights de la collaboration de contenu au cours des 28 derniers jours.
- **Service :** L’utilisateur&#39;service s, comme défini dans Azure Active Directory (AAD).
- **Société :** L’utilisateur&#39;la société, comme défini dans AAD.
- **Pays :** Pays de&#39;de l’utilisateur, tel que défini dans AAD.
- **État :** L’utilisateur&#39;État s, comme défini dans AAD.
- **Ville :** L’utilisateur&#39;City, comme défini dans AAD.
- **OneDrive :** Valeur booléenne indiquant si la personne a accès à OneDrive pendant au moins 1 des 28 derniers jours.
- **SharePoint :** Valeur booléenne indiquant si la personne a eu accès toSharePoint pendant au moins 1 des 28 derniers jours.
- **Accès aux fichiers Office :** Valeur booléenne indiquant si la personne a accédé à des fichiers via Microsoft Word, Excel, PowerPoint ou OneNote au cours des 28 derniers jours.
- **Fichiers créés sur OneDrive :** Valeur booléenne indiquant si la personne a créé, modifié, chargé, synchronisé, archivé, archivé ou déplacé des fichiers en ligne (dans Microsoft Word, Excel, PowerPoint ou OneNote) sur OneDrive au cours des 28 derniers jours.
- **Fichiers créés sur SharePoint :** Valeur booléenne indiquant si la personne a créé, modifié, chargé, synchronisé, archivé, archivé ou déplacé des fichiers en ligne (dans Microsoft Word, Excel, PowerPoint ou OneNote) sur SharePoint au cours des 28 derniers jours.
- **Jours en tant que lecteur :** Nombre de jours pendant lesquels la personne a accédé ou téléchargé des fichiers en ligne (dans Microsoft Word, Excel, PowerPoint, OneNote ou PDF) sur OneDrive ou SharePoint au cours des 28 derniers jours.
- **Jours en tant que créateur :** Nombre de jours pendant lesquels la personne a créé, modifié, chargé, synchronisé, archivé, archivé ou déplacé des fichiers en ligne (dans Microsoft Word, Excel, PowerPoint, OneNote ou PDF) dans OneDrive ou SharePoint au cours des 28 derniers jours.
- **Fichiers sur lesquels la collaboration est activée :** Nombre de fichiers en ligne sur OneDrive ou SharePoint sur lesquels la personne a collaboré au cours des 28 derniers jours.
- **Fichiers partagés en interne :** Nombre de fichiers en ligne sur OneDrive ou SharePoint que la personne a partagée avec d’autres personnes au sein de votre organisation au cours des 28 derniers jours.
- **Fichiers partagés en externe :** Nombre de fichiers en ligne sur OneDrive ou SharePoint que la personne a partagée avec d’autres personnes en dehors de votre organisation au cours des 28 derniers jours.
- **Pièces jointes par courrier électronique :** Valeur booléenne indiquant si la personne a envoyé le courrier électronique avec des fichiers (pas sur OneDrive ou SharePoint) en tant que pièces jointes au cours des 28 derniers jours.
- **Pièces jointes de fichiers électroniques en ligne :** Valeur booléenne indiquant si la personne a envoyé un message électronique avec des liens vers des fichiers en ligne (sur OneDrive ou SharePoint) en tant que pièces jointes au cours des 28 derniers jours.
- **Incorporer le lien vers le fichier en ligne :** Valeur booléenne indiquant si la personne a envoyé un message électronique avec des liens vers des fichiers en ligne (sur OneDrive ou SharePoint) incorporés dans le corps du message au cours des 28 derniers jours.

## <a name="related-content"></a>Contenu connexe

[Microsoft 365 Apps Health – expériences technologiques](apps-health.md) (article) \
[Communication – expériences des personnes](communication.md) (article) \
[Réunions – expériences des personnes](meetings.md) (article) \
[Mobilité – expériences de personnes](mobility.md) (article) \
[Contrôles de confidentialité du score de productivité](privacy.md) (article) \
[Travail d’équipe – expériences des personnes](teamwork.md) (article)
