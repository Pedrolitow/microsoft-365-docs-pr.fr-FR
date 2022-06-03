---
title: Cloner un package existant
description: Comment cloner un package existant
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 05/27/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 1e0f4ca8939a965347126076f5fef7e85a103c9c
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863700"
---
# <a name="clone-an-existing-package"></a>Cloner un package existant

Dans cette section, vous allez apprendre à créer un package en dupliquer votre package précédemment publié comme point de départ. Il existe plusieurs entrées sur le portail de base de test pour vous permettre de démarrer le parcours du package clone.

> [!IMPORTANT]
> Pour utiliser la fonction de package clone, vous devez disposer d’au moins un package correctement chargé sur la base de test. 

## <a name="starting-from-the-new-package-page"></a>À partir de la page Nouveau package

> [!div class="mx-imgBorder"]
> [![Guide de](Media/clonepackage01_guidance.png) clonage ](Media/clonepackage01_guidance.png#lightbox)

1. Dans la page **Nouveau package** , vous pouvez sélectionner le **package clone existant**. Sélectionnez ensuite un package dans la liste des packages existants, puis cliquez sur **« Cloner** ». 

   > [!div class="mx-imgBorder"]
   > [![Cloner un package](Media/clonepackage02_clone_package.png) existant ](Media/clonepackage02_clone_package.png#lightbox)

2. Vous serez dirigé vers les étapes de création du nouveau package avec toutes les informations et la configuration préremplies comme le package que vous avez cloné. Les seules informations que vous devez modifier sont la **version du package** sous la section **Informations de base** . 

   > [!NOTE]
   > La combinaison du nom et de la version du package doit être unique dans votre compte de base de test. 

   > [!div class="mx-imgBorder"]
   > [![Informations de base sur](Media/clonepackage03_basic_information.png) le package ](Media/clonepackage03_basic_information.png#lightbox)

3. Vous pouvez :

   - afficher un aperçu de toutes les informations de paramètre de package prérempli du package de clonage. 
   - apporter des modifications de l’étape 1 à l’étape 4 (voir Chargement d’un package zip prédéffagé pour obtenir des instructions plus détaillées). 
   - vérifier et publier dans la base de test. 


## <a name="starting-from-the-manage-packages-page"></a>À partir de la page Gérer les packages

Dans la page **Gérer les packages** , vous pouvez cloner un package en sélectionnant l’icône **« Cloner »** sous la colonne Actions rapides. 

> [!div class="mx-imgBorder"]
> [![Page Gérer les packages](Media/clonepackage04_manage_packages.png) ](Media/clonepackage04_manage_packages.png#lightbox)

Vous pouvez également accéder à la page **Vue d’ensemble** du package spécifique que vous avez sélectionné dans la page **Gérer les packages** , puis sélectionner l’icône **Cloner le package** dans le menu d’action supérieur.

> [!div class="mx-imgBorder"]
> [![Cloner à partir de la page](Media/clonepackage05_overview.png) vue d’ensemble ](Media/clonepackage05_overview.png#lightbox)

