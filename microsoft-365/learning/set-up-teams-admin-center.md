---
title: Configurer Microsoft Learning (prévisualisation) dans le Centre d Teams'administration Microsoft
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: chrisarnoldmsft
ms.date: 04/30/2021
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-learning
localization_priority: None
description: Découvrez comment configurer Microsoft Learning (prévisualisation) dans le centre d Teams'administration Microsoft.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: c1427ae9fceab38046b53b31540e08d726815bda
ms.sourcegitcommit: d3f8c69519c593b1580cfa7187ce085a99b8a846
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52100964"
---
# <a name="set-up-microsoft-viva-learning-preview-in-the-teams-admin-center"></a>Configurer Microsoft Learning (prévisualisation) dans le Centre d Teams'administration Microsoft

> [!NOTE]
> Les informations de cet article concernent un produit d'aperçu qui peut être considérablement modifié avant sa publication commerciale. 

L'administrateur Teams installe Learning (Prévisualisation) et applique des stratégies d'autorisation par le biais Teams centre d'administration.

## <a name="manage-settings-for-viva-learning-preview"></a>Gérer les paramètres de Learning Learning (prévisualisation)

Vous devez être administrateur dans le Centre d Teams pour effectuer ces tâches.

Pour mettre à disposition des utilisateurs de votre organisation la version d'avant-première de l'apprentissage, suivez les étapes suivantes :

1. Dans le navigation gauche du centre d Teams d'administration, Teams **applications Gérer**  >  **les applications.**

   ![Navigation gauche dans le centre d Teams d'administration affichant Teams applications et la section Gérer les applications.](../media/learning/learning-app-teams-manage-apps-nav.png)

2. Dans la page **Gérer les applications,** dans la zone de recherche, tapez *Learning,* puis **sélectionnez Learning (Prévisualisation).**

   ![Page Gérer les applications dans le centre Teams'administration affichant la zone de recherche.](../media/learning/learning-app-teams-manage-apps-page.png)

3. Dans la page **Learning (Prévisualisation)** :

   1. Sous **État,** **sélectionnez Autorisé** à activer Learning (Prévisualisation).

   2. Sous **l'onglet Paramètres,** sous **Paramètres** de l'application, allez dans le centre d'administration Microsoft 365 pour configurer les sources de [contenu d'apprentissage.](content-sources-365-admin-center.md)

   ![Page d'apprentissage dans Teams centre d'administration affichant la section Paramètres de l'état et de l'application.](../media/learning/learning-app-teams-learning-page.png)

4. Après avoir gérer les  paramètres  de l'application, accédez aux stratégies d'autorisation et de configuration pour accorder des autorisations aux employés qui doivent avoir accès à Learning (Preview) dans le cadre de la participation de votre organisation à la prévisualisation. 

> [!NOTE]
>  Si votre organisation est dans l'anneau 4.0 dans le cadre du programme Teams TAP100, vous devrez peut-être permettre aux utilisateurs approuvés de Ring 3.0 d'accéder à Learning (Prévisualisation). <br><br>Dans le cadre de la prévisualisation, Learning (Preview) est publié dans Ring 3.0. Si votre organisation est dans l'anneau 4.0, vous ne verrez pas Contrôle Learning (Prévisualisation) sur la page **Gérer les applications.** Pour tester l'application, vous devez créer une stratégie d'autorisation d'application personnalisée, la définir sur Autoriser toutes les applications et l'affecter aux utilisateurs approuvés par Ring 3.0. <br><br>   ![Page TAP-AppsPermission-Plcy affichant Autoriser toutes les applications sélectionnées.](../media/learning/learning-app-tap-appspermission-plcy.png)

## <a name="next-step"></a>Étape suivante

[Configurer des sources de contenu d'apprentissage pour Learning Learning (prévisualisation) dans le centre d Microsoft 365'administration](content-sources-365-admin-center.md)