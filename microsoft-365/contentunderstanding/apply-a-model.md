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
description: Découvrez comment appliquer un modèle publié à une bibliothèque de documents SharePoint dans Microsoft SharePoint Syntex.
ms.openlocfilehash: a3c1ca971853234bb4b203d8b1b3e40aec7c1d7d
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882393"
---
# <a name="apply-a-document-understanding-model-in-microsoft-sharepoint-syntex"></a>Appliquer un modèle de présentation de document dans Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Après avoir publié votre modèle de compréhension de document, vous pouvez l’appliquer à une ou plusieurs bibliothèques de documents SharePoint dans votre locataire Microsoft 365.

> [!NOTE]
> Vous pouvez uniquement appliquer le modèle aux bibliothèques de documents auxquelles vous avez accès.


## <a name="apply-your-model-to-a-document-library"></a>Appliquer votre modèle à une bibliothèque de documents

Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. Dans la page d’accueil du modèle, dans la vignette **Appliquer le modèle aux bibliothèques** , **sélectionnez Appliquer le modèle**. Ou, dans la section **Où le modèle est appliqué** , sélectionnez **+Ajouter une bibliothèque**.

    ![Capture d’écran de la section Où le modèle est appliqué avec l’option Ajouter une bibliothèque mise en surbrillance.](../media/content-understanding/apply-to-library.png)

2. Vous pouvez ensuite sélectionner le site SharePoint contenant la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Si le site n’apparaît pas dans la liste, utilisez la zone de recherche pour la trouver.

    ![Sélectionnez un site.](../media/content-understanding/site-search.png)

    > [!NOTE]
    > Vous devez disposer d’autorisations *Gérer la liste* ou de droits *Modifier* sur la bibliothèque de documents à laquelle vous appliquez le modèle.

3. Une fois le site sélectionné, sélectionnez la bibliothèque de documents à laquelle vous voulez appliquer le modèle. Dans l’exemple, sélectionnez la bibliothèque de documents *Documents* à partir du site de *Suivi de cas contoso*.

    ![Sélectionnez une bibliothèque de documents.](../media/content-understanding/select-doc-library.png)

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, il ajoute le type de contenu et met à jour l’affichage par défaut avec les étiquettes que vous avez extraites en tant que colonnes. Toutefois, vous pouvez sélectionner **Paramètres avancés** pour choisir éventuellement de conserver l’affichage bibliothèque actuel ou d’utiliser une nouvelle vue avec des informations de modèle et des miniatures de fichier. Si vous choisissez de conserver l’affichage de bibliothèque actuel, les nouveaux affichages avec des informations de modèle sont toujours disponibles dans le menu d’affichage de la bibliothèque.

    ![Capture d’écran des paramètres avancés montrant les vues de bibliothèque.](../media/content-understanding/library-view.png)

    Pour plus d’informations, consultez [Modifier la vue dans une bibliothèque de documents](#change-the-view-in-a-document-library) plus loin dans cet article.

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque.

6. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué**, vous devez voir le nom du site SharePoint répertorié.

7. Accédez à votre bibliothèque de documents et vérifiez que vous êtes dans la vue bibliothèque de documents du modèle. Sélectionnez Les **modèles de compréhension de document** **AutomateView** > .

8. Dans la page **Vérifier les modèles et en appliquer de nouveaux** , sélectionnez l’onglet **Appliqué** pour afficher les modèles appliqués à la bibliothèque de documents.

    ![Capture d’écran montrant l’onglet Appliqué sélectionné et les modèles appliqués.](../media/content-understanding/applied-models.png) 

9. Sélectionnez **Afficher les détails du modèle** pour afficher des informations sur un modèle, telles qu’une description du modèle, qui a publié le modèle et si le modèle applique des étiquettes de rétention ou de confidentialité aux fichiers qu’il classifie.

Une fois le modèle appliqué à la bibliothèque de documents, vous pouvez commencer à télécharger des documents sur le site et afficher les résultats.

Le modèle identifie tous les fichiers et dossiers avec le type de contenu associé au modèle et les répertorie dans votre affichage. Si votre modèle comporte des extracteurs, la vue affiche des colonnes pour les données que vous extrayez de chaque fichier ou dossier.

> [!NOTE]
> Si deux modèles de compréhension de document ou plus sont appliqués à la même bibliothèque, le fichier chargé est classé à l’aide du modèle qui a le score de confiance moyen le plus élevé. Les entités extraites proviennent uniquement du modèle appliqué. <br><br>Si un modèle de traitement de formulaire personnalisé et un modèle de compréhension de document sont appliqués à la même bibliothèque, le fichier est classé à l’aide du modèle de compréhension de document et des extracteurs formés pour ce modèle. S’il existe des colonnes vides qui correspondent au modèle de traitement de formulaire, les colonnes sont remplies à l’aide de ces valeurs extraites.

## <a name="sync-changes-to-one-or-more-libraries"></a>Synchroniser les modifications apportées à une ou plusieurs bibliothèques

Lorsque vous publiez un modèle sur plusieurs bibliothèques de documents, puis mettez à jour le modèle, par exemple en ajoutant ou en supprimant un extracteur, vous devez envoyer (push) la mise à jour à toutes les bibliothèques appliquées au modèle.

Pour synchroniser les modifications apportées à toutes les bibliothèques appliquées :

1. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué** , sélectionnez **Synchroniser tout**.

    ![Capture d’écran montrant la section Où le modèle est appliqué et le bouton Synchroniser tout en surbrillance.](../media/content-understanding/sync-all-button.png) 

Pour synchroniser les modifications vers une ou plusieurs bibliothèques sélectionnées :

1. Dans la page d’accueil du modèle, dans la section **Où le modèle est appliqué** , sélectionnez la bibliothèque ou les bibliothèques auxquelles vous souhaitez appliquer les modifications.

2. Sélectionnez **Synchroniser**.

    ![Capture d’écran montrant la section Où le modèle est appliqué et le bouton Synchroniser mis en surbrillance.](../media/content-understanding/sync-button.png) 

## <a name="apply-the-model-to-files-and-folder-content-already-in-the-document-library"></a>Appliquer le modèle aux fichiers et au contenu des dossiers déjà présents dans la bibliothèque de documents

Bien qu’un modèle appliqué traite tous les fichiers et le contenu des dossiers chargés dans la bibliothèque de documents après son application, vous pouvez également effectuer les opérations suivantes pour exécuter le modèle sur les fichiers et le contenu des dossiers qui existent déjà dans la bibliothèque de documents avant l’application du modèle :

1. Dans votre bibliothèque de documents, sélectionnez les fichiers et dossiers que vous souhaitez traiter par votre modèle.

2. Après avoir sélectionné vos fichiers et dossiers, **Classifier et extraire** s’affiche dans le ruban de la bibliothèque de documents. Sélectionnez **Classer et extraire**.

      ![Capture d’écran montrant l’option Classifier et extraire.](../media/content-understanding/extract-classify.png) 

3. Les fichiers et dossiers que vous avez sélectionnés seront ajoutés à la file d’attente à traiter.

    > [!NOTE]
    > Vous recevrez un message indiquant la durée de la classification. Si vous avez sélectionné uniquement des fichiers, la classification peut prendre jusqu’à 30 minutes. Si vous avez sélectionné un ou plusieurs dossiers, la classification peut prendre jusqu’à 24 heures.

### <a name="classification-date-field"></a>Champ Date de classification

Lorsqu’un modèle de compréhension de document SharePoint Syntex (ou un modèle de traitement de formulaire) est appliqué à une bibliothèque de documents, le champ **Date de classification** est inclus dans le schéma de bibliothèque. Par défaut, ce champ est vide. Toutefois, lorsque les documents sont traités et classés par un modèle, ce champ est mis à jour avec un horodatage de date et heure de fin. 

   ![Capture d’écran d’une bibliothèque de documents montrant la colonne Date de classification.](../media/content-understanding/class-date-column.png) 

Le champ **Date de classification** est utilisé par le déclencheur [**When a file is classified by a content understanding model**](/connectors/sharepointonline/#when-a-file-is-classified-by-a-content-understanding-model) trigger to run a Power Automate flow after a model has finished processing the contents of a file or folder and has updated the **Classification Date** field.

   ![Flow déclencheur.](../media/content-understanding/trigger.png)

**Quand un fichier est classé par un déclencheur de modèle de compréhension du contenu** peut ensuite être utilisé pour démarrer un flux à l’aide d’informations extraites du fichier ou du dossier.

Par exemple, lorsqu’un modèle est marqué avec la **date de classification**, vous pouvez utiliser **l’option Envoyer un e-mail après SharePoint Syntex traite un** flux de fichiers pour informer les utilisateurs qu’un nouveau fichier a été traité et classifié par un modèle dans la bibliothèque de documents SharePoint.

Pour exécuter le flux :

1. Sélectionnez un fichier, puis **sélectionnez Intégrer** >  **Power Automate** >  **Créer un flux**.

2. Dans le panneau **Créer un flux**, sélectionnez **Envoyer un e-mail après SharePoint Syntex traite un fichier**.

    ![Capture d’écran montrant le panneau Créer un flux et l’option de flux mis en évidence.](../media/content-understanding/integrate-create-flow.png) 

## <a name="change-the-view-in-a-document-library"></a>Modifier la vue dans une bibliothèque de documents

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

## <a name="see-also"></a>Voir aussi

[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)
