---
title: Créer un modèle sur un site SharePoint local avec Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer un modèle local sur un site SharePoint local avec Microsoft Syntex.
ms.openlocfilehash: dcd514b0d6656f7a4ce4d181aca348016e7ada53
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660245"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-syntex"></a>Créer un modèle sur un site SharePoint local avec Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles entraînés</sup>

Microsoft Syntex offre une option permettant de créer et d’entraîner des modèles localement sur votre propre site SharePoint. Ces modèles peuvent être utilisés uniquement sur le site où ils sont créés. 

> [!NOTE]
> Si vous souhaitez rendre votre modèle détectable et disponible pour d’autres utilisateurs, vous devez créer un *modèle d’entreprise*. Un modèle d’entreprise est un modèle créé et entraîné dans le [centre de contenu](create-a-content-center.md).  

En activant la classification et l’extraction de documents sur votre site SharePoint, Syntex vous permet de classifier des fichiers dans des bibliothèques de documents, d’extraire des informations à partir de nouveaux fichiers et d’automatiser les activités en fonction des informations extraites.

Lorsque vous activez la création de modèles locaux, les listes et bibliothèques suivantes sont ajoutées à votre site :

- Bibliothèque de documents models
- Bibliothèque de documents de fichiers d’apprentissage
- Liste des modèles d’explication
- Liste d’utilisation du modèle

Un modèle est automatiquement promu vers le site actuel uniquement lorsque le modèle a été appliqué pour la première fois à n’importe quelle bibliothèque du site. Cela rend le modèle détectable dans la liste des modèles de site disponibles et disponible pour toute autre bibliothèque du site. Tant que le modèle n’est pas appliqué à une bibliothèque dans le site, il n’est pas disponible. De même, lorsqu’un modèle est supprimé de toutes les bibliothèques du site, il est également supprimé de la liste des modèles de site disponibles. 

Cette fonctionnalité est disponible pour tous les [types de modèles](model-types-overview.md). 

## <a name="create-a-model-on-a-local-site"></a>Créer un modèle sur un site local

1. Dans une bibliothèque de documents SharePoint, sélectionnez les fichiers que vous souhaitez analyser, puis sélectionnez **Classifier et extraire**.

    ![Capture d’écran d’une bibliothèque de documents SharePoint avec l’option Classifier et extraire mise en évidence.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. La première fois que vous utilisez cette fonctionnalité, vous activez Syntex sur votre site. Le message suivant s’affiche.

    ![Capture d’écran de la page Activer la classification et l’extraction des documents.](../media/content-understanding/local-model-first-run-activate-message.png) 

    > [!NOTE]
    > Vous devez disposer de l’autorisation Gérer le site web pour effectuer des tâches d’administration et gérer le contenu du site. Il s’agirait d’un propriétaire de site. Une fois la fonctionnalité activée, toute personne disposant de l’autorisation Gérer les listes peut créer et gérer des modèles.

3. Sélectionnez **Activer** pour continuer. Le message suivant s’affiche.

    ![Capture d’écran du message d’activation de la classification et de l’extraction de documents avec l’option Créer un modèle.](../media/content-understanding/local-model-activated-message.png) 

4. Sélectionnez **Créer un modèle**.

5. Dans le panneau **Créer un modèle** , tapez le nom du modèle, sélectionnez le type de modèle, puis **sélectionnez Créer**.

    ![Capture d’écran du panneau Créer un modèle.](../media/content-understanding/local-model-create-a-model.png) 

6. Procédez à [l’apprentissage de votre modèle personnalisé](apply-a-model.md) ou à [la configuration de votre modèle entraîné](prebuilt-overview.md) à l’aide des fichiers que vous avez sélectionnés.

7. Lorsque vous avez terminé, le panneau **Ajouter à la bibliothèque** s’ouvre.

    ![Capture d’écran du panneau Ajouter à la bibliothèque montrant le site et les bibliothèques appliquées.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. Dans le panneau **Ajouter à la bibliothèque** , vous verrez le nom de votre site SharePoint et la bibliothèque de documents à laquelle le modèle sera appliqué. Si vous souhaitez appliquer le modèle à une autre bibliothèque, sélectionnez **Revenir aux bibliothèques**, puis choisissez la bibliothèque que vous souhaitez utiliser. Puis sélectionnez **Ajouter**.

9. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué sur ce site** , vous pouvez voir les bibliothèques auxquelles le modèle est appliqué. Pour appliquer le modèle à d’autres bibliothèques sur le site, sélectionnez **Appliquer le modèle**. 

    ![Capture d’écran de la page d’accueil du modèle montrant la section Où le modèle est appliqué sur le site.](../media/content-understanding/local-model-home-page.png) 

> [!NOTE]
> Lorsqu’un modèle local est appliqué à une seule bibliothèque, il devient disponible pour la découverte pour l’application à d’autres bibliothèques dans le même site.