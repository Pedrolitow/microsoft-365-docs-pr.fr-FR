---
title: Renommer un extracteur dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment et pourquoi renommer un extracteur dans Microsoft Syntex.
ms.openlocfilehash: 15da5f905a622173758b4d8f1ac2b4c2de219014
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68661256"
---
# <a name="rename-an-extractor-in-microsoft-syntex"></a>Renommer un extracteur dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; traitement de documents non structurés</sup>

À un moment donné, vous devrez peut-être renommer un extracteur si vous souhaitez faire référence à un champ de données extrait par un nom différent. Par exemple, votre organisation décide d'apporter des modifications à ses documents contractuels et désigne les «clients» par le terme «clients» dans ses documents. Si vous extrayez un champ «Client» dans votre modèle, vous pouvez choisir de le renommer en «Client».

Lorsque vous synchronisez votre modèle mis à jour avec votre bibliothèque de documents SharePoint, vous verrez une nouvelle colonne «Client» dans la vue de votre bibliothèque de documents. Votre vue conservera la colonne «Client» pour les activités passées, mais mettra à jour la nouvelle colonne «Client» pour tous les nouveaux documents traités par votre modèle. 

> [!IMPORTANT]
>  Assurez-vous de synchroniser votre modèle mis à jour avec les bibliothèques de documents où vous l'aviez précédemment appliqué pour que le nouveau nom de colonne s'affiche. 

## <a name="rename-an-extractor"></a>Renommer un extracteur

Suivez ces étapes pour renommer un extracteur d'entité.

1. Dans le centre de contenu, sélectionnez **Modèles** pour afficher votre liste de modèles.

2. Sur la page **Modèles**, dans la colonne **Nom**, sélectionnez le modèle pour lequel vous souhaitez renommer un extracteur.

3. Sous **'entité**, sélectionnez le nom de l’extracteur que vous voulez renommer, puis sélectionnez **Renommer**.

    ![Capture d'écran de la section Extracteurs d'entités montrant un extracteur sélectionné avec l'option Renommer en surbrillance.](../media/content-understanding/entity-extractor-rename.png) 

4. Sur **le panneau de l'extracteur** d'entité Renommer :

   a. Sous **Nouveau nom**, saisissez le nouveau nom de l'extracteur.

    ![Capture d'écran montrant le panneau de l'extracteur d'entités.](../media/content-understanding/rename-entity-extractor-panel.png) 

   b. (Facultatif) Sous **Paramètres avancés**, sélectionnez si vous voulez associer une colonne de site existante.

5. Sélectionnez **Renommer**.

## <a name="see-also"></a>Voir aussi

[Créer un extracteur](create-an-extractor.md)


