---
title: Appliquer un modèle à une bibliothèque de documents dans Microsoft Syntex
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
description: Découvrez comment appliquer un modèle publié à une bibliothèque de documents SharePoint dans Microsoft Syntex.
ms.openlocfilehash: b0aed07a5a530b06b04fe78775d49373daae290f
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659234"
---
# <a name="apply-a-model-to-a-document-library-in-microsoft-syntex"></a>Appliquer un modèle à une bibliothèque de documents dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; Tous les modèles &ensp; | &ensp; personnalisés &#10003; Tous les modèles prédéfinis</sup>

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>
--->

Après avoir entraîné un modèle de traitement de document non structuré, entraîné et publié un modèle de traitement de document structuré ou de forme libre, ou créé un modèle prédéfini, vous pouvez l’appliquer à une ou plusieurs bibliothèques de documents SharePoint dans votre client Microsoft 365.

Cet article s’applique aux *modèles d’entreprise* et *aux modèles locaux*. Un modèle d’entreprise est créé et entraîné dans le [centre de contenu](create-a-content-center.md) et peut être découvert par d’autres personnes à utiliser. Un [modèle local](create-local-model.md) est créé et entraîné localement sur votre propre site SharePoint.  

> [!NOTE]
> Vous pouvez appliquer le modèle uniquement aux bibliothèques de documents auxquelles vous avez accès.

## <a name="apply-your-model-to-a-document-library"></a>Appliquer votre modèle à une bibliothèque de documents

Vous pouvez appliquer un modèle à différents emplacements, y compris la page d’accueil du modèle ou à partir de la liste des modèles disponibles. Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. Dans la page d’accueil du modèle, dans la vignette **Appliquer le modèle aux bibliothèques** , sélectionnez **Appliquer le modèle**. Ou, dans la section **Où le modèle est appliqué** , sélectionnez **Ajouter une bibliothèque**.

    ![Capture d’écran de la section Où le modèle est appliqué avec l’option Ajouter une bibliothèque mise en évidence.](../media/content-understanding/apply-to-library.png)

2. Vous pouvez ensuite sélectionner le site SharePoint contenant la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Si le site ne s’affiche pas dans la liste, utilisez la zone de recherche pour le trouver.

    ![Sélectionnez un site.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Vous devez disposer d’autorisations *Gérer la liste* ou de droits *Modifier* sur la bibliothèque de documents à laquelle vous appliquez le modèle.

3. Une fois le site sélectionné, sélectionnez la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Dans l’exemple, sélectionnez la bibliothèque de documents *Documents* à partir du site de *Suivi de cas contoso*.

    ![Sélectionnez une bibliothèque de documents.](../media/content-understanding/select-doc-library.png)

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, il ajoute le type de contenu et met à jour l’affichage par défaut avec les étiquettes que vous avez extraites affichées sous forme de colonnes. Toutefois, vous pouvez sélectionner **Paramètres avancés** pour choisir éventuellement de conserver l’affichage de la bibliothèque actuelle ou d’utiliser une nouvelle vue avec des informations de modèle et des miniatures de fichier. Si vous choisissez de conserver l’affichage de la bibliothèque actuelle, les nouveaux affichages avec des informations de modèle sont toujours disponibles dans le menu d’affichage de la bibliothèque.

    ![Capture d’écran des paramètres avancés montrant les affichages de la bibliothèque.](../media/content-understanding/library-view.png)

    Pour plus d’informations, consultez [Choisir l’affichage dans une bibliothèque de documents](choose-library-view.md).

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque.

6. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué** , vous devez voir le nom du site SharePoint répertorié.

7. Accédez à votre bibliothèque de documents et vérifiez que vous êtes dans la vue bibliothèque de documents du modèle. Sélectionnez **Automatiser les** > **modèles d’affichage**.

8. Dans la page **Vérifier les modèles et appliquer de nouveaux** modèles, sélectionnez l’onglet **Appliqué** pour afficher les modèles appliqués à la bibliothèque de documents.

    ![Capture d’écran montrant l’onglet Appliqué sélectionné et les modèles appliqués.](../media/content-understanding/applied-models.png) 

9. Sélectionnez **Afficher les détails du modèle** pour afficher des informations sur un modèle, telles qu’une description du modèle, la personne qui a publié le modèle et si le modèle applique des étiquettes de rétention ou de confidentialité aux fichiers qu’il classifie.

Une fois le modèle appliqué à la bibliothèque de documents, vous pouvez commencer à télécharger des documents sur le site et afficher les résultats.

Le modèle identifie tous les fichiers et dossiers avec le type de contenu associé au modèle et les répertorie dans votre affichage. Si votre modèle comporte des extracteurs, la vue affiche des colonnes pour les données que vous extrayez à partir de chaque fichier ou dossier.

> [!NOTE]
> Si plusieurs modèles de traitement de documents non structurés sont appliqués à la même bibliothèque, le fichier chargé est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. <br><br>Si un modèle de traitement de document de forme libre ou structuré et un modèle de traitement de document non structuré sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle de traitement de document non structuré et de tous les extracteurs formés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle de traitement de document structuré ou de forme libre, les colonnes sont remplies à l’aide de ces valeurs extraites.

## <a name="sync-changes-to-one-or-more-document-libraries"></a>Synchroniser les modifications apportées à une ou plusieurs bibliothèques de documents

Lorsque vous publiez un modèle dans plusieurs bibliothèques de documents, puis mettez à jour le modèle, par exemple en ajoutant ou en supprimant un extracteur, vous devez envoyer (push) la mise à jour à toutes les bibliothèques auxquelles le modèle a été appliqué.

Pour synchroniser les modifications apportées à toutes les bibliothèques appliquées :

1. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué** , sélectionnez **Synchroniser tout**.

    ![Capture d’écran montrant la section Où le modèle est appliqué et le bouton Synchroniser tout mis en évidence.](../media/content-understanding/sync-all-button.png) 

Pour synchroniser les modifications apportées à une ou à une seule bibliothèque sélectionnée :

1. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué** , sélectionnez la ou les bibliothèques à laquelle vous souhaitez appliquer les modifications.

2. Sélectionnez **Synchroniser**.

    ![Capture d’écran montrant la section Où le modèle est appliqué et le bouton Synchroniser mis en évidence.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Appliquer le modèle aux fichiers et au contenu des dossiers déjà présents dans la bibliothèque de documents

Un modèle appliqué traite tous les fichiers et le contenu des dossiers chargés dans la bibliothèque de documents après son application. Vous pouvez également effectuer les étapes suivantes pour exécuter le modèle sur les fichiers et le contenu des dossiers qui existent déjà dans la bibliothèque de documents avant l’application du modèle :

1. Dans votre bibliothèque de documents, sélectionnez les fichiers et dossiers que vous souhaitez traiter par votre modèle.

2. Après avoir sélectionné vos fichiers et dossiers, **Classifier et extraire** s’affiche dans le ruban de la bibliothèque de documents. Sélectionnez **Classer et extraire**.

      ![Capture d’écran montrant l’option Classifier et extraire.](../media/content-understanding/extract-classify.png) 

3. Les fichiers et dossiers que vous avez sélectionnés sont ajoutés à la file d’attente à traiter.

    > [!NOTE]
    > Si vous avez sélectionné un ou plusieurs dossiers ou si vous migrez un grand ensemble de fichiers, la classification peut prendre jusqu’à 24 heures.

### <a name="classification-date-field"></a>Champ Date de classification

Lorsqu’un personnalisé est appliqué à une bibliothèque de documents, le champ **Date de classification** est inclus dans le schéma de la bibliothèque. Par défaut, ce champ est vide. Toutefois, lorsque des documents sont traités et classés par un modèle, ce champ est mis à jour avec un horodatage d’achèvement. 

   ![Capture d’écran d’une bibliothèque de documents montrant la colonne Date de classification.](../media/content-understanding/class-date-column.png) 

Le champ **Date de classification** est utilisé par le déclencheur [**Quand un fichier est classifié par un modèle de compréhension du contenu**](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) pour exécuter un flux Power Automate une fois qu’un modèle a terminé le traitement du contenu d’un fichier ou d’un dossier et a mis à jour le champ **Date de classification** .

   ![Déclencheur de flux.](../media/content-understanding/trigger.png)

Le déclencheur **Quand un fichier est classifié par un modèle de compréhension du contenu** peut ensuite être utilisé pour démarrer un flux à l’aide des informations extraites du fichier ou du dossier.

Par exemple, lorsqu’un modèle est marqué avec la **Date de classification**, vous pouvez utiliser l’option **Envoyer un e-mail après que Syntex a traité un** flux de fichier pour informer les utilisateurs qu’un nouveau fichier a été traité et classifié par un modèle dans la bibliothèque de documents SharePoint.

Pour exécuter le flux :

1. Sélectionnez un fichier, puis **Intégrer** > **Power Automate** > **Créer un flux**.

2. Dans le panneau **Créer un flux** , sélectionnez **Envoyer un e-mail après que Syntex a traité un fichier**.

    ![Capture d’écran montrant le panneau Créer un flux et l’option de flux mises en évidence.](../media/content-understanding/integrate-create-flow.png) 

## <a name="see-also"></a>Voir aussi

[Partager un modèle d’entreprise](model-discovery.md)

[Découvrir d’autres modèles entraînés](discover-other-trained-models.md)

[Choisir l’affichage dans une bibliothèque de documents](choose-library-view.md)

