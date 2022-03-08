---
title: Créer un modèle sur un site SharePoint local avec Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer un modèle local sur un site SharePoint local avec SharePoint Syntex.
ms.openlocfilehash: f6eab2d081dda379d8eb2c88d762661d374a1db6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319062"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>Créer un modèle sur un site SharePoint local avec Microsoft SharePoint Syntex

SharePoint Syntex offre désormais la possibilité de créer et d’entraîner des modèles localement sur votre propre site SharePoint site. Ces modèles ne peuvent être utilisés que sur le site où ils sont créés. 

En activant la classification et l’extraction des documents sur votre site SharePoint, SharePoint Syntex vous permet de classifier des fichiers dans des bibliothèques de documents, d’extraire des informations de nouveaux fichiers et d’automatiser les activités en fonction des informations extraites.

Lorsque vous activez la création de modèles locaux, les listes et bibliothèques suivantes sont ajoutées à votre site :

- Bibliothèque de documents Modèles
- Bibliothèque de documents fichiers de formation
- Liste des modèles d’explication
- Liste d’utilisation des modèles

Cette fonctionnalité est disponible uniquement pour la création de [modèles de](apply-a-model.md) compréhension de documents et [de modèles pré-créés](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>Créer un modèle sur un site local

1. Dans une SharePoint de documents, sélectionnez les fichiers que vous souhaitez analyser, puis classez et **extrayez**.

    ![Capture d’écran d SharePoint bibliothèque de documents avec l’option Classer et extraire mise en évidence.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. La première fois que vous utilisez cette fonctionnalité, vous activez SharePoint Syntex sur votre site. Vous verrez le message suivant.

    ![Capture d’écran de la page Activer la classification des documents et les informations d’extraction.](../media/content-understanding/local-model-first-run-activate-message.png) 

3. **Sélectionnez Activer** pour continuer. Vous verrez le message suivant.

    ![Capture d’écran du message activé pour la classification et l’extraction du document avec l’option Créer un modèle.](../media/content-understanding/local-model-activated-message.png) 

4. **Sélectionnez Créer un modèle**.

5. Dans le **panneau Créer un modèle** , tapez le nom du modèle, sélectionnez le type de modèle, puis sélectionnez **Créer**.

    ![Capture d’écran du panneau Créer un modèle.](../media/content-understanding/local-model-create-a-model.png) 

6. Continuez [à former votre modèle de compréhension de document](apply-a-model.md) ou [à configurer](prebuilt-models.md) votre modèle pré-pré-projet à l’aide des fichiers que vous avez sélectionnés.

7. Lorsque vous avez terminé, le **panneau Ajouter à la** bibliothèque s’ouvre.

    ![Capture d’écran du panneau Ajouter à la bibliothèque montrant le site et les bibliothèques appliqués.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. Dans le **panneau Ajouter à** la bibliothèque, vous verrez le nom de votre site SharePoint et la bibliothèque de documents à appliquer au modèle. Si vous souhaitez appliquer le modèle à une autre bibliothèque, sélectionnez **Retour** aux bibliothèques et choisissez la bibliothèque que vous souhaitez utiliser. Puis sélectionnez **Ajouter**.

9. Dans la page d’accueil du modèle, dans l’emplacement où le modèle est appliqué sur cette section **de site** , vous pouvez voir les bibliothèques pour laquelle le modèle est appliqué. Pour appliquer le modèle à d’autres bibliothèques sur le site, sélectionnez **Appliquer le modèle**. 

    ![Capture d’écran de la page d’accueil du modèle montrant l’emplacement où le modèle est appliqué à la section du site.](../media/content-understanding/local-model-home-page.png) 

