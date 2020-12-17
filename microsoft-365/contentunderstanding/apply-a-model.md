---
title: Appliquer un modèle de présentation de document à une bibliothèque de documents
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
localization_priority: Priority
description: Découvrir comment appliquer un modèle publié à une bibliothèque de documents SharePoint
ms.openlocfilehash: 9c99ede49633b5ae70cbb67c30d83c111084df95
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49701140"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Appliquer un modèle de présentation de document dans Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Une fois que vous avez publié votre modèle de présentation de document, vous pouvez l’appliquer à une ou plusieurs bibliothèques de documents SharePoint dans votre client Microsoft 365.

> [!NOTE]
> Vous pouvez uniquement appliquer le modèle aux bibliothèques de documents auxquelles vous avez accès.


## <a name="apply-your-model-to-a-document-library"></a>Appliquez votre modèle à une bibliothèque de documents.

Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. Sur la page d’accueil du modèle, dans la vignette **Appliquer le modèle aux bibliothèques** , sélectionnez **Publier le modèle**. Vous pouvez également sélectionner **+ Ajouter une bibliothèque** dans la section **Bibliothèques avec ce modèle**. </br>

    ![Ajouter un modèle à la bibliothèque](../media/content-understanding/apply-to-library.png)</br>

2. Vous pouvez ensuite sélectionner le site SharePoint contenant la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Si le site n’apparaît pas dans la liste, utilisez la zone de recherche pour le trouver.</br>

    ![Sélection d’un site](../media/content-understanding/site-search.png)</br>

    > [!NOTE]
    > Vous devez disposer d’autorisations *Gérer la liste* ou de droits *Modifier* sur la bibliothèque de documents à laquelle vous appliquez le modèle.</br>

3. Une fois le site sélectionné, sélectionnez la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Dans l’exemple, sélectionnez la bibliothèque de documents *Documents* à partir du site de *Suivi de cas contoso*.</br>

    ![Sélectionner une bibliothèque de documents](../media/content-understanding/select-doc-library.png)</br>

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, le type de contenu et son affichage sont ajoutés aux étiquettes que vous avez extraites sous forme de colonnes. Cet affichage est l’affichage par défaut de la bibliothèque par défaut, mais vous pouvez choisir de ne pas l’utiliser par défaut en sélectionnant **Paramètres avancés** et en désactivant la case à cocher **Définir cette nouvelle vue comme par défaut**.</br>

    ![Vue de la bibliothèque](../media/content-understanding/library-view.png)</br>

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque. 
6. Dans la page d’accueil du modèle, dans la section **Bibliothèques avec ce modèle**, l’URL du site SharePoint doit apparaître.</br>

    ![Bibliothèque sélectionnée](../media/content-understanding/selected-library.png)</br>

7. Accédez à votre bibliothèque de documents et vérifiez que vous êtes dans la vue bibliothèque de documents du modèle. Notez que si vous sélectionnez le bouton informations en regard du nom de la bibliothèque de documents, un message indique que votre modèle a été appliqué à la bibliothèque de documents.

    ![Vue informations](../media/content-understanding/info-du.png)</br> 


Une fois le modèle appliqué à la bibliothèque de documents, vous pouvez commencer à télécharger des documents sur le site et afficher les résultats.

Le modèle identifie les fichiers avec le type de contenu associé au modèle et les répertorie dans votre affichage. Si votre modèle inclut des extracteurs, l’affichage affiche les colonnes des données que vous extrayez à partir de chaque fichier.

### <a name="apply-the-model-to-files-already-in-the-document-library"></a>Appliquer le modèle aux fichiers figurant déjà dans la bibliothèque de documents

Lorsqu’un modèle appliqué traite tous les fichiers téléchargés vers la bibliothèque de documents une fois qu’il est appliqué, vous pouvez également effectuer les opérations suivantes pour exécuter le modèle sur des fichiers qui existent déjà dans la bibliothèque de documents avant l’application du modèle :

1. Dans votre bibliothèque de documents, sélectionnez les fichiers que vous voulez traiter par votre modèle.
2. Une fois que vous avez sélectionné vos fichiers, **Classer et extraire** s’affiche dans le ruban de la bibliothèque de documents. Sélectionnez **Classer et extraire**.
3. Les fichiers que vous avez sélectionnés sont ajoutés à la file d’attente à traiter.

      ![Classer et extraire](../media/content-understanding/extract-classify.png)</br> 

> [!NOTE]
> Vous pouvez copier des fichiers individuels dans une bibliothèque et les appliquer à un modèle, mais pas des dossiers.

## <a name="see-also"></a>Voir aussi
[Créer un classificateur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)


