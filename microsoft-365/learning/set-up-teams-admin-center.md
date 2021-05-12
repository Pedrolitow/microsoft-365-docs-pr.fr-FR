---
title: Configurer Microsoft Learning (prévisualisation) dans le Centre d’administration Teams
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 05/12/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer Microsoft Learning (prévisualisation) dans le Centre d’administration Teams.
ms.openlocfilehash: 40e659796b22097f42515c0cbb704bdaa4ccc972
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52333517"
---
# <a name="set-up-microsoft-viva-learning-preview-in-the-teams-admin-center"></a>Configurer Microsoft Learning (prévisualisation) dans le Centre d’administration Teams

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. 

L’administrateur Teams installe Learning (prévisualisation) et applique des stratégies d’autorisation par le biais du Centre d’administration Teams.

## <a name="manage-settings-for-viva-learning-preview"></a>Gérer les paramètres de Learning Learning (prévisualisation)

Vous devez être administrateur dans le Centre d’administration Teams pour effectuer ces tâches.

Pour mettre à disposition des utilisateurs de votre organisation la version d’avant-première de l’apprentissage, suivez les étapes suivantes :

1. Dans le navigation de gauche du Centre d’administration Teams, allez à **Applications Teams Gérer** les  >  **applications.**

   ![Navigation gauche dans le Centre d’administration Teams affichant la section Applications Teams et Gérer les applications.](../media/learning/learning-app-teams-manage-apps-nav.png)

2. Dans la page **Gérer les applications,** dans la zone de recherche, tapez *Learning,* puis **sélectionnez Learning (Prévisualisation).**

   ![Page Gérer les applications dans le Centre d’administration Teams affichant la zone de recherche.](../media/learning/learning-app-teams-manage-apps-page.png)

3. Dans la page **Learning (Prévisualisation)** :

   1. Sous **État,** **sélectionnez Autorisé** à activer Learning (Prévisualisation).

   2. Sous **l’onglet Paramètres,** sous **Paramètres** de l’application, allez dans le Centre d’administration Microsoft 365 pour configurer les sources de [contenu d’apprentissage.](content-sources-365-admin-center.md)

   ![Page d’apprentissage dans le Centre d’administration Teams affichant la section Paramètres de l’état et de l’application.](../media/learning/learning-app-teams-learning-page.png)

4. Après avoir gérer les  paramètres  de l’application, accédez aux stratégies d’autorisation et de configuration pour accorder des autorisations aux employés qui doivent avoir accès à Learning (Preview) dans le cadre de la participation de votre organisation à la prévisualisation. 

> [!NOTE]
>  Si votre organisation est dans Ring 4.0 dans le cadre du programme TAP100 teams, vous devrez peut-être permettre aux utilisateurs approuvés de Ring 3.0 d’accéder à Learning (Prévisualisation). <br><br>Dans le cadre de la prévisualisation, Learning (Preview) est publié dans Ring 3.0. Si votre organisation est dans l’anneau 4.0, vous ne verrez pas Learning (Prévisualisation) sur la page Gérer **les applications.** Pour tester l’application, vous devez créer une stratégie d’autorisation d’application personnalisée, la définir sur Autoriser toutes les applications et l’affecter aux utilisateurs approuvés par Ring 3.0. <br><br>   ![Page TAP-AppsPermission-Plcy affichant Autoriser toutes les applications sélectionnées.](../media/learning/learning-app-tap-appspermission-plcy.png)

## <a name="next-step"></a>Étape suivante

[Configurer des sources de contenu d’apprentissage pour Learning Learning (prévisualisation) dans le Centre d’administration Microsoft 365](content-sources-365-admin-center.md)