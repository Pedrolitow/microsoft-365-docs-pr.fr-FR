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
ms.openlocfilehash: bcd3f1f086af3982cb4a3ecc5fe754cf82f09a70
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535379"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>Créer un modèle sur un site SharePoint local avec Microsoft SharePoint Syntex

SharePoint Syntex offre désormais la possibilité de créer et d’entraîner des modèles localement sur votre propre site SharePoint. Ces modèles peuvent être utilisés uniquement sur le site où ils sont créés. 

En activant la classification et l’extraction de documents sur votre site SharePoint, SharePoint Syntex vous permet de classifier des fichiers dans des bibliothèques de documents, d’extraire des informations de nouveaux fichiers et d’automatiser les activités en fonction des informations extraites.

Lorsque vous activez la création de modèle local, les listes et bibliothèques suivantes sont ajoutées à votre site :

- Modèles de bibliothèque de documents
- Bibliothèque de documents des fichiers d’apprentissage
- Liste des modèles d’explication
- Liste d’utilisation du modèle

Cette fonctionnalité est disponible uniquement pour la création de [modèles de compréhension de document](apply-a-model.md) et [de modèles prédéfinis](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>Créer un modèle sur un site local

1. Dans une bibliothèque de documents SharePoint, sélectionnez les fichiers à analyser, puis **sélectionnez Classifier et extraire**.

    ![Capture d’écran d’une bibliothèque de documents SharePoint avec l’option Classifier et extraire mise en évidence.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. La première fois que vous utilisez cette fonctionnalité, vous activez SharePoint Syntex sur votre site. Le message suivant s’affiche.

    ![Capture d’écran de la page Activer la classification et l’extraction de documents.](../media/content-understanding/local-model-first-run-activate-message.png) 

    > [!NOTE]
    > Vous devez disposer de l’autorisation Gérer le site web pour effectuer des tâches d’administration et gérer le contenu du site. Il s’agit d’un propriétaire de site. Une fois la fonctionnalité activée, toute personne disposant de l’autorisation Gérer les listes peut créer et gérer des modèles.

3. Sélectionnez **Activer** pour continuer. Le message suivant s’affiche.

    ![Capture d’écran du message de classification et d’extraction de document activé avec l’option Créer un modèle.](../media/content-understanding/local-model-activated-message.png) 

4. Sélectionnez **Créer un modèle**.

5. Dans le volet **Créer un modèle** , tapez le nom du modèle, sélectionnez le type de modèle, puis **sélectionnez Créer**.

    ![Capture d’écran du panneau Créer un modèle.](../media/content-understanding/local-model-create-a-model.png) 

6. Effectuez [l’apprentissage de votre modèle de compréhension de document](apply-a-model.md) ou [configurez votre modèle prédéfini](prebuilt-models.md) à l’aide des fichiers que vous avez sélectionnés.

7. Lorsque vous avez terminé, le panneau **Ajouter à la bibliothèque s’ouvre** .

    ![Capture d’écran du panneau Ajouter à la bibliothèque montrant le site et les bibliothèques appliquées.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. Dans le panneau **Ajouter à la bibliothèque**, vous verrez le nom de votre site SharePoint et la bibliothèque de documents à laquelle le modèle sera appliqué. Si vous souhaitez appliquer le modèle à une autre bibliothèque, sélectionnez **Revenir aux bibliothèques**, puis choisissez la bibliothèque que vous souhaitez utiliser. Puis sélectionnez **Ajouter**.

9. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué dans cette** section de site, vous pouvez voir les bibliothèques pour lesquelles le modèle est appliqué. Pour appliquer le modèle à d’autres bibliothèques sur le site, **sélectionnez Appliquer le modèle**. 

    ![Capture d’écran de la page d’accueil du modèle montrant l’emplacement où le modèle est appliqué dans la section du site.](../media/content-understanding/local-model-home-page.png) 

