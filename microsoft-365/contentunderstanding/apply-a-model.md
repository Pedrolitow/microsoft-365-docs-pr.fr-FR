---
title: Appliquer un modèle de présentation de document à une bibliothèque de documents
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment appliquer un modèle publié à une bibliothèque de documents SharePoint
ms.openlocfilehash: c693fa08bf3103eca01e01774e8f8b1d9e783b07
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295489"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Appliquer un modèle de présentation de documents dans Microsoft SharePoint Syntex

Le contenu de cet article est destiné à la préversion privée du projet cortex. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Après avoir publié votre modèle de présentation de document, vous pouvez l’appliquer à une bibliothèque de documents SharePoint dans votre client Microsoft 365.

> [!NOTE]
> Vous ne pouvez appliquer le modèle qu’aux bibliothèques de documents auxquelles vous avez accès.


## <a name="apply-your-model-to-a-document-library"></a>Appliquer votre modèle à une bibliothèque de documents.

Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. À partir de la page d’accueil du modèle, dans la vignette **appliquer le modèle aux bibliothèques** , sélectionnez **publier le modèle**. Ou vous pouvez sélectionner l’option  **+ Ajouter une bibliothèque** dans la section **bibliothèques avec ce modèle** . </br>

    ![Ajouter un modèle à la bibliothèque](../media/content-understanding/apply-to-library.png)</br>

2. Sélectionnez le site SharePoint qui contient la bibliothèque de documents à laquelle vous souhaitez appliquer le modèle. Si le site ne s’affiche pas dans la liste, utilisez la zone de recherche pour le trouver.</br>

    ![Sélectionner un site](../media/content-understanding/site-search.png)</br>

    > [!NOTE]
    > Vous devez disposer des autorisations *gérer les listes* ou *modifier* les droits sur la bibliothèque de documents à laquelle vous appliquez le modèle.</br>

3. Une fois le site sélectionné, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer le modèle. Dans l’exemple, sélectionnez la bibliothèque de documents *documents* à partir du site de *suivi des cas contoso* .</br>

    ![Sélectionner une bibliothèque de documents](../media/content-understanding/select-doc-library.png)</br>

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, il crée un affichage pour le type de contenu avec les étiquettes extraites sous forme de colonnes. Cet affichage est l’affichage par défaut de la bibliothèque, mais vous pouvez choisir de ne pas l’afficher par défaut en sélectionnant **Paramètres avancés** et en désélectionnant **définir cette nouvelle vue comme valeur par défaut**.</br>

    ![Affichage de la bibliothèque](../media/content-understanding/library-view.png)</br>

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque. 
6. Sur la page d’accueil du modèle, dans la section **bibliothèques avec ce modèle** , l’URL du site SharePoint doit apparaître.</br>

    ![Bibliothèque sélectionnée](../media/content-understanding/selected-library.png)</br>

7. Accédez à votre bibliothèque de documents et assurez-vous que vous êtes dans la vue bibliothèque de documents du modèle. Notez que si vous sélectionnez le bouton informations en regard du nom de la bibliothèque de documents, un message indique que votre modèle a été appliqué à la bibliothèque de documents.

    ![Vue d’informations](../media/content-understanding/info-du.png)</br> 


Après avoir appliqué le modèle à la bibliothèque de documents, vous pouvez commencer à télécharger des documents sur le site et voir les résultats.

Le modèle identifie les fichiers dont le type de contenu est associé et les répertorie dans votre vue. Si votre modèle possède des extracteurs, l’affichage affiche des colonnes pour les données que vous extrayez de chaque fichier.

### <a name="apply-the-model-to-files-already-in-the-document-library"></a>Appliquer le modèle aux fichiers figurant déjà dans la bibliothèque de documents

Lorsqu’un modèle appliqué traite tous les fichiers téléchargés vers la bibliothèque de documents après son application, vous pouvez également effectuer les opérations suivantes pour exécuter le modèle sur des fichiers qui existent déjà dans la bibliothèque de documents avant l’application du modèle :

1. Dans votre bibliothèque de documents, sélectionnez les fichiers que vous souhaitez traiter par votre modèle.
2. Une fois que vous avez sélectionné vos fichiers, **classifier et extraire** apparaît dans le ruban de la bibliothèque de documents. Sélectionnez **classifier et extraire**.
3. Les fichiers que vous avez sélectionnés seront ajoutés à la file d’attente pour être traités.

      ![Classer et extraire](../media/content-understanding/extract-classify.png)</br> 

## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Présentation de l’explication des documents](document-understanding-overview.md)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)  
