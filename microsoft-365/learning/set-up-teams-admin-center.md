---
title: Configurer Microsoft Learning (prévisualisation) dans le Centre d Teams’administration Microsoft
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 05/24/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer Microsoft Learning (prévisualisation) dans le centre d Teams’administration Microsoft.
ms.openlocfilehash: a96a2f3ecf7d4e1ee0c136ae155868218f08aaf4
ms.sourcegitcommit: 17f0aada83627d9defa0acf4db03a2d58e46842f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52636133"
---
# <a name="set-up-microsoft-viva-learning-preview-in-the-teams-admin-center"></a>Configurer Microsoft Learning (prévisualisation) dans le Centre d Teams’administration Microsoft

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. 

L’administrateur Teams installe Learning (Prévisualisation) et applique des stratégies d’autorisation via Teams centre d’administration.

1. Pour Learning (Prévisualisation), vous devez d’abord définir la stratégie de mise à jour dans Teams. Pour plus d’informations, [voir Microsoft Teams prévisualisation publique.](/MicrosoftTeams/public-preview-doc-updates)

    1. Connectez-vous au centre Teams’administration.

    2. Sélectionnez **Teams**  >  **stratégies de mise à jour.**

    3. Sélectionnez **Ajouter**. 

    4. Nommez la stratégie de mise à jour, ajoutez une stratégie et activer **Afficher les fonctionnalités d’aperçu.**

2. L’administrateur doit informer les utilisateurs de la mise à jour de la stratégie afin qu’ils déplacent leur build dans la prévisualisation publique pour Teams. 

    1. Les utilisateurs doivent sélectionner leur image de profil > **à propos de** la  >  **prévisualisation publique.**
   
        ![Navigation supérieure dans l’application Teams montrant le profil de l’utilisateur](../media/learning/learning-app-select-profile-teams.png)
    
    2. Les utilisateurs doivent accepter les conditions générales **de la prévisualisation** publique.

        ![Basculer vers la version d’aperçu public](../media/learning/learning-app-switch-to-public-preview.png)
 
3. Pour les organisations qui ont des stratégies restrictives et qui doivent activer Learning (Prévisualisation), suivez le processus de la section suivante.

## <a name="manage-settings-for-viva-learning-preview"></a>Gérer les paramètres de Learning Learning (prévisualisation)

Vous devez être administrateur dans le Centre d Teams pour effectuer ces tâches.

Pour mettre à disposition des utilisateurs de votre organisation l’apprentissage en prévisualisation, suivez les étapes ci-après :

1. Dans le navigation gauche du centre d Teams d’administration, Teams **applications Gérer**  >  **les applications.**

   ![Navigation gauche dans le centre d Teams d’administration affichant Teams applications et la section Gérer les applications.](../media/learning/learning-app-teams-manage-apps-nav.png)

2. Dans la page **Gérer les applications,** dans la zone de recherche, tapez *Learning,* puis **sélectionnez Learning (Prévisualisation).**

   ![Page Gérer les applications dans le centre Teams’administration affichant la zone de recherche.](../media/learning/learning-app-teams-manage-apps-page.png)

3. Dans la page **Learning (Prévisualisation)** :

   1. Sous **État,** **sélectionnez Autorisé** à activer Learning (Prévisualisation).

   2. Sous **l’onglet Paramètres,** sous **Paramètres** de l’application, allez dans le centre d’administration Microsoft 365 pour configurer les sources de [contenu d’apprentissage.](content-sources-365-admin-center.md)

   ![Page d’apprentissage dans Teams centre d’administration affichant la section Paramètres de l’état et de l’application.](../media/learning/learning-app-teams-learning-page.png)

4. Après avoir gérer les  paramètres  de l’application, accédez aux stratégies d’autorisation et aux stratégies d’installation pour accorder l’autorisation aux employés qui doivent avoir accès à Learning (Preview) dans le cadre de la participation de votre organisation à la prévisualisation. 

> [!NOTE]
>  Si votre organisation est dans Ring 4.0 dans le cadre du programme Teams TAP100, vous devrez peut-être permettre aux utilisateurs approuvés de Ring 3.0 d’accéder à Learning (Preview). <br><br>Dans le cadre de la prévisualisation, Learning (Preview) est publié dans Ring 3.0. Si votre organisation est dans l’anneau 4.0, vous ne verrez pas Contrôle Learning (Prévisualisation) sur la page **Gérer les applications.** Pour tester l’application, vous devez créer une stratégie d’autorisation d’application personnalisée, la définir sur Autoriser toutes les applications et l’affecter aux utilisateurs approuvés par Ring 3.0. <br><br>   ![Page TAP-AppsPermission-Plcy affichant Autoriser toutes les applications sélectionnées.](../media/learning/learning-app-tap-appspermission-plcy.png)

## <a name="next-step"></a>Étape suivante

[Configurer des sources de contenu d’apprentissage pour Learning Learning (prévisualisation) dans le centre d Microsoft 365'administration](content-sources-365-admin-center.md)
