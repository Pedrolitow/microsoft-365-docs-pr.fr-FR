---
title: Personnaliser le thème de votre organisation
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 8275da91-7a48-4591-94ab-3123a3f79530
description: 'Découvrez comment modifier le thème par défaut de Microsoft 365 et le personnaliser pour qu’il corresponde au logo ou à la couleur de votre entreprise. '
ms.openlocfilehash: 3674c26be50d622364a4dc077a85eaa974d71fcd
ms.sourcegitcommit: 22e9f54d0d3ead2be91a38d49325308c70f43f90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "44262328"
---
# <a name="customize-the-microsoft-365-theme-for-your-organization"></a>Personnaliser le thème Microsoft 365 de votre organisation

Découvrez comment personnaliser votre thème dans le centre d’administration 365 de Microsoft. En tant qu’administrateur de votre abonnement Microsoft 365 pour les entreprises, vous pouvez modifier le thème par défaut qui s’affiche dans la barre de navigation supérieure pour tous les membres de l’organisation. Vous pouvez ajouter le logo de votre entreprise et modifier les couleurs pour qu’elles correspondent au reste de votre marque. Vous pouvez même ajouter un lien de destination pour les utilisateurs auxquels ils peuvent accéder lorsqu’ils sélectionnent votre logo. Vous pouvez voir ici le thème par défaut et le résultat de thème personnalisé dans Microsoft 365.
  
![Thème Microsoft 365 par défaut et thème Microsoft 365 personnalisé](../../media/e2cbc922-b424-4683-8c5c-fdbcbd0ce844.png)
  
## <a name="customize-your-theme-in-the-admin-center"></a>Personnaliser votre thème dans le centre d’administration

1. Dans le centre d’administration, accédez à paramètres d’organisation **paramètres** \> **Org Settings**, puis cliquez sur l’onglet Profil de l' **organisation** .

2. Sous l’onglet Profil de l' **organisation** , sélectionnez **thèmes personnalisés**.

3. Dans le panneau **thèmes de douane** , modifiez les éléments de thème souhaités pour votre organisation :
    
    - **Utiliser une image de logo personnalisée**: indiquez si vous souhaitez utiliser une image à partir d’une URL ou pour télécharger une image. Si vous utilisez une URL, vérifiez que l’URL utilise le protocole HTTPs et qu’il s’agit de 200 x 30 pixels de n’importe quel format de n’importe quelle taille. Vous pouvez télécharger un logo de moins de 10 Ko, 200 x 30 pixels au format JPG, PNG, GIF ou SVG.

      > [!NOTE]
      > Pour que le logo apparaisse dans l’application mobile SharePoint, utilisez uniquement des images SVG. Les images téléchargées dans n’importe quel autre format ne sont pas affichées dans l’application. Les logos ne sont pas cliquables dans l’application mobile SharePoint.

    - **Faire un clic sur le logo**: vous pouvez utiliser votre logo dans la barre de navigation en tant que lien vers toute ressource de la société. Vous pouvez entrer l’URL du logo ici, en commençant par http://ou https://. Cette étape est facultative.

    - **Sélectionnez image d’arrière-plan**: sélectionnez l’image et téléchargez votre propre fichier jpg, png ou gif avec une résolution de 1366 x 50 pixels, ne dépassant pas 15 Ko. l'image d'arrière-plan s'affiche dans la barre de navigation supérieure de chaque page.

      > [!NOTE]
      > Il se peut que les images qui contiennent du texte ne s’affichent pas comme prévu. Les éléments intégrés qui apparaissent à gauche et à droite de la barre de navigation peuvent varier d’un service à l’autre et votre texte peut être dissimulé par ces éléments. En raison de la nature dynamique de la barre de navigation, nous ne sommes pas en mesure à l’heure actuelle de fournir des instructions de remplissage d’image qui offriraient une expérience cohérente. 

    - **Couleur**de la barre de navigation : sélectionnez une couleur à utiliser pour l’arrière-plan de la barre de navigation. Celle-ci apparaît en haut de chaque page.

    - **Texte et icônes** : Sélectionnez la couleur à utiliser pour le texte et les icônes de la barre de navigation supérieure.

    - **Couleur d’accentuation**: sélectionnez une couleur à utiliser pour le bouton de la barre de navigation, la couleur de pointage et les accents comme les boutons et le texte de certaines applications.

     - **Empêcher les utilisateurs de remplacer le thème**: inverser ce bouton pour empêcher les utilisateurs de choisir leur propre thème à partir de notre sélection de thème. Cela n’empêche pas les utilisateurs de définir un thème à contraste élevé.

    - **Afficher le nom d’utilisateur**: choisissez d’afficher ou non le nom complet d’un utilisateur au niveau du point d’entrée au responsable de compte dans le coin supérieur droit de la page lorsque l’utilisateur est connecté. Par défaut, les utilisateurs verront leur photo ou leurs initiales si une photo n’a pas été téléchargée.
    
4. Sélectionnez **Enregistrer les modifications**.
    
Vous verrez immédiatement votre nouveau thème sur le centre d’administration et après un court délai, vous le verrez dans Microsoft 365, y compris les pages dans Outlook, SharePoint, l' [application mobile SharePoint pour iOS](https://support.office.com/article/SharePoint-mobile-app-for-iOS-339402ce-16bb-4c97-9475-0c5375ccef7a)et l' [application mobile SharePoint pour Android](https://support.office.com/article/SharePoint-mobile-app-for-Android-d875654b-fb0a-4dbe-a17a-a676cf936284). Pour obtenir un exemple d’emplacement où vous pouvez personnaliser les modifications apportées au thème à partir du centre d’administration, consultez l’image suivante.

![M365-admin-client-Theme-Conceptual](../../media/m365-admin-tenant-theme-conceptual.png)

Vous pouvez supprimer votre icône ou vos couleurs personnalisées à tout moment. Retournez simplement sur la page du thème et sélectionnez **Supprimer les thèmes personnalisés**.
  
## <a name="best-practices"></a>Meilleures pratiques

Lors du choix d’une **image de logo**, nous vous recommandons d’utiliser un type de fichier SVG, de sorte que votre logo dispose d’une haute résolution sur tous les écrans et tous les niveaux de zoom.

Lors du choix des couleurs personnalisées, choisissez une **couleur d’arrière-plan** de la barre de navigation dont le taux de contraste est élevé avec l' **image du logo** que vous avez choisie. Choisissez également une couleur de **texte et d’icônes** avec un taux de contraste élevé à la **couleur d’arrière-plan** de la barre de navigation pour vous assurer que tout le texte et les icônes sont facilement visibles.

Lorsque vous choisissez des couleurs personnalisées, choisissez une **couleur d’accentuation** qui s’affiche bien sur un arrière-plan blanc ou clair. La **couleur d’accentuation** permet de colorer certains liens et boutons qui apparaissent sur un arrière-plan blanc ou clair. Par exemple, la **couleur d’accentuation** est utilisée pour colorier des éléments dans la boîte de réception d’un utilisateur et sur sa page de portail Office.com. 
  
Le rapport de contraste recommandé entre la couleur de texte, d’icône ou de bouton et la couleur d’arrière-plan est 4,5:1.

Voici un organigramme simple pour vous aider à configurer rapidement un thème Microsoft 365 personnalisé visuellement attrayant pour votre organisation :
  - Je souhaite utiliser une version colorée de notre logo.
    - Nous vous recommandons d’utiliser les paramètres suivants :
      - **Image du logo**: logo coloré de votre organisation.
      - **Couleur**de la barre de navigation : couleur neutre. Nous vous recommandons de #FAF9F7 pour une couleur claire et une #252423 pour une couleur foncée.
      - **Couleur du texte et**de l’icône : couleur de contraste de la couleur de la **barre de navigation**. Nous vous recommandons de #FAF9F7 pour une couleur claire et une #252423 pour une couleur foncée.
      - **Couleur d’accentuation**: couleur de marque foncée. Avec certaines applications, cette couleur doit être visible sur un arrière-plan clair.
  - Je souhaite utiliser une version neutre de notre logo et représenter la couleur dans la barre de navigation.
    - Nous vous recommandons d’utiliser les paramètres suivants :
      - **Image du logo**: logo neutre de votre organisation.
      - **Couleur**de la barre de navigation : une couleur qui contraste avec votre logo.
      - **Couleur du texte et de l’icône**: choisissez une couleur qui contraste avec la couleur de la marque choisie pour la couleur de la **barre de navigation**. Nous vous recommandons de #252423 pour une couleur foncée et #FAF9F7 pour une couleur claire.
      - **Couleur d’accentuation**: couleur de marque foncée. Avec certaines applications, cette couleur doit être visible sur un arrière-plan clair.
  
## <a name="related-articles"></a>Articles connexes

[Ajouter des vignettes personnalisées à la page Mes applications et au lanceur d'applications](../manage/customize-the-app-launcher.md)
  
  
