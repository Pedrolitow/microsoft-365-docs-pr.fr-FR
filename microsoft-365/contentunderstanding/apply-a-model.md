---
title: Appliquer un modèle de présentation de document dans Microsoft SharePoint Syntex
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
description: Découvrez comment appliquer un modèle publié à une bibliothèque SharePoint documents dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 23a885194a1bfa6c0f468188944dd00d309f3a09
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60194404"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Appliquer un modèle de présentation de document dans Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Après avoir publié votre modèle de compréhension des documents, vous pouvez l’appliquer à une ou plusieurs SharePoint de documents dans votre Microsoft 365 client.

> [!NOTE]
> Vous pouvez uniquement appliquer le modèle aux bibliothèques de documents auxquelles vous avez accès.


## <a name="apply-your-model-to-a-document-library"></a>Appliquer votre modèle à une bibliothèque de documents

Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. Sur la page d’accueil du modèle, sur la vignette Appliquer le **modèle aux bibliothèques,** **sélectionnez Appliquer le modèle.** Ou, dans la section **Où le modèle est appliqué,**  **sélectionnez +Ajouter une bibliothèque** .

    ![Capture d’écran de la section Où le modèle est appliqué avec l’option Ajouter une bibliothèque mise en évidence.](../media/content-understanding/apply-to-library.png)

2. Vous pouvez ensuite sélectionner le site SharePoint contenant la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Si le site n’apparaît pas dans la liste, utilisez la zone de recherche pour le trouver.

    ![Sélectionnez un site.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Vous devez disposer d’autorisations *Gérer la liste* ou de droits *Modifier* sur la bibliothèque de documents à laquelle vous appliquez le modèle.

3. Une fois le site sélectionné, sélectionnez la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Dans l’exemple, sélectionnez la bibliothèque de documents *Documents* à partir du site de *Suivi de cas contoso*.

    ![Sélectionnez une bibliothèque de documents.](../media/content-understanding/select-doc-library.png)

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, il ajoute le type de contenu et son affichage avec les étiquettes que vous avez extraites en tant que colonnes. Par défaut, cet affichage est l’affichage par défaut de la bibliothèque. Toutefois, vous pouvez éventuellement choisir de ne pas en faire l’affichage par défaut en sélectionnant **Paramètres** avancés et en effasant la case à cocher définir cette nouvelle vue comme **case à** cocher par défaut.

    ![Affichage Bibliothèque.](../media/content-understanding/library-view.png)

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque.

6. Dans la page d’accueil du modèle, dans la **section** Où le modèle est appliqué, vous devez voir le nom du site SharePoint répertorié.

7. Accédez à votre bibliothèque de documents et vérifiez que vous êtes dans la vue bibliothèque de documents du modèle. Sélectionnez   >  **Automatiser l’affichage des modèles de compréhension du document.**

8. Dans la page **Examiner les modèles**  et en appliquer de nouvelles, sélectionnez l’onglet Appliqué pour voir les modèles qui sont appliqués à la bibliothèque de documents.

    ![Capture d’écran montrant l’onglet Appliqué sélectionné et les modèles appliqués.](../media/content-understanding/applied-models.png) 

9. Sélectionnez les détails du modèle d’affichage pour afficher des informations sur un modèle, telles qu’une description du modèle, qui a publié le modèle, et si le modèle applique des **étiquettes** de rétention ou de sensibilité aux fichiers qu’il classifie.

Une fois le modèle appliqué à la bibliothèque de documents, vous pouvez commencer à télécharger des documents sur le site et afficher les résultats.

Le modèle identifie les fichiers et dossiers associés au type de contenu associé au modèle et les répertorie dans votre affichage. Si votre modèle possède des extracteurs, l’affichage affiche des colonnes pour les données que vous extrayez à partir de chaque fichier ou dossier.

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Appliquer le modèle aux fichiers et au contenu de dossiers déjà présents dans la bibliothèque de documents

Bien qu’un modèle appliqué traite tous les fichiers et le contenu des dossiers chargés dans la bibliothèque de documents après son application, vous pouvez également exécuter le modèle sur les fichiers et le contenu de dossier qui existent déjà dans la bibliothèque de documents avant que le modèle soit appliqué :

1. Dans votre bibliothèque de documents, sélectionnez les fichiers et dossiers que vous souhaitez traiter par votre modèle.

2. Après avoir sélectionné vos fichiers et dossiers, classifier et **extraire** s’affiche dans le ruban de la bibliothèque de documents. Sélectionnez **Classer et extraire**.

      ![Capture d’écran montrant l’option Classifier et extraire.](../media/content-understanding/extract-classify.png) 

3. Les fichiers et dossiers que vous avez sélectionnés seront ajoutés à la file d’attente à traiter.

    > [!NOTE]
    > Vous recevrez un message indiquant la durée possible de la classification. Si vous avez sélectionné uniquement des fichiers, la classification peut prendre jusqu’à 30 minutes. Si vous avez sélectionné un ou plusieurs dossiers, la classification peut prendre jusqu’à 24 heures.

### <a name="classification-date-field"></a>Champ Date de classification

Lorsqu’un SharePoint Syntex de document ou un modèle de traitement de formulaire est appliqué à une bibliothèque de documents, le champ **Date** de classification est inclus dans le schéma de bibliothèque. Par défaut, ce champ est vide. Toutefois, lorsque des documents sont traitées et classées par un modèle, ce champ est mis à jour avec un horodat de fin. 

   ![Capture d’écran d’une bibliothèque de documents affichant la colonne Date de classification.](../media/content-understanding/class-date-column.png) 

Le champ **Date** de [](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) classification est utilisé par le déclencheur lorsqu’un fichier est classé par un déclencheur de modèle de compréhension du contenu pour exécuter un flux Power Automate une fois qu’un modèle de compréhension du contenu Syntex a terminé le traitement d’un fichier ou d’un dossier et mis à jour le champ **Date** de classification.

   ![Flow déclencheur.](../media/content-understanding/trigger.png)

**Lorsqu’un fichier est** classé par un déclencheur de modèle de compréhension du contenu, il peut être utilisé pour démarrer un autre flux de travail à l’aide des informations extraites du fichier ou du dossier.



## <a name="see-also"></a>Voir aussi

[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)
