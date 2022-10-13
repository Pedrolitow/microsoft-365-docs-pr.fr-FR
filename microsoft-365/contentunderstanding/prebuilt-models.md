---
title: Utiliser un modèle prédéfini pour extraire des informations à partir de factures ou de reçus dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer et configurer un modèle prédéfini dans Microsoft Syntex.
ms.openlocfilehash: 7ec51b86bc6645e2ebe13923969155e1b6b309b7
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68563271"
---
# <a name="use-a-prebuilt-model-to-extract-info-from-invoices-or-receipts-in-microsoft-syntex"></a>Utiliser un modèle prédéfini pour extraire des informations à partir de factures ou de reçus dans Microsoft Syntex

Les modèles prédéfinis sont préentraînés pour reconnaître les documents et les informations structurées dans les documents. Au lieu de devoir créer un modèle personnalisé à partir de zéro, vous pouvez itérer sur un modèle préentraîné existant pour ajouter des champs spécifiques qui répondent aux besoins de votre organisation. 

Actuellement, deux modèles prédéfinis sont disponibles : facture et reçu.

- Le *modèle prédéfini de facture* analyse et extrait les informations clés des factures de vente. L’API analyse les factures dans différents formats et [extrait les informations de facture clés](/azure/applied-ai-services/form-recognizer/concept-invoice#field-extraction) telles que le nom du client, l’adresse de facturation, la date d’échéance et le montant dû.

- Le *modèle prédéfini de reçu* analyse et extrait les informations clés des reçus de ventes. L’API analyse les reçus imprimés et manuscrits et [extrait les informations de reçu clés](/azure/applied-ai-services/form-recognizer/concept-receipt#field-extraction) telles que le nom du commerçant, le numéro de téléphone du commerçant, la date de transaction, la taxe et le total des transactions.

D’autres modèles prédéfinis seront disponibles dans les versions ultérieures.

## <a name="create-a-prebuilt-model"></a>Créer un modèle prédéfini

Suivez ces étapes pour créer un modèle prédéfini pour classifier des documents dans Syntex.

1. Dans la page **Modèles** , sélectionnez **Créer un modèle**.

    ![Capture d’écran de la page Modèles montrant le bouton Créer un modèle.](../media/content-understanding/prebuilt-create-model-button.png) 

2. Dans le panneau **Créer un modèle** , dans le champ **Nom** , tapez le nom du modèle.

    ![Capture d’écran du panneau Nouveau modèle de compréhension de document montrant les types de modèles disponibles.](../media/content-understanding/prebuilt-create-panel.png) 

3. Dans la section **Type de modèle** , sélectionnez l’un des modèles prédéfinis :
   - **Traitement de facture prédéfini**
   - **Traitement du reçu prédéfini**

   Si vous souhaitez créer un modèle de compréhension de document traditionnel et non entraîné au lieu d’un modèle prédéfini, sélectionnez **Compréhension de document personnalisée**.

4. Si vous souhaitez modifier le type de contenu ou ajouter une étiquette de rétention, sélectionnez **Paramètres avancés**.

    > [!NOTE]
    > Les étiquettes de sensibilité ne sont pas disponibles pour les modèles prédéfinis pour l’instant.

5. Sélectionnez **Créer**. Le modèle est enregistré dans la bibliothèque **Models** .

## <a name="add-a-file-to-analyze"></a>Ajouter un fichier à analyser

1. Dans la page **Modèles** , dans la section **Ajouter un fichier à analyser** , sélectionnez **Ajouter un fichier**.

    ![Capture d’écran de la page nouveaux modèles montrant la section Ajouter un fichier à analyser.](../media/content-understanding/prebuilt-add-file-to-analyze.png) 

2. Dans la page **Fichiers pour analyser le modèle** , sélectionnez **Ajouter** pour rechercher le fichier que vous souhaitez utiliser.

    ![Capture d’écran des fichiers pour analyser la page de modèle montrant le bouton Ajouter.](../media/content-understanding/prebuilt-add-file-button.png) 

3. Dans la page **Ajouter un fichier à partir de la page bibliothèque de fichiers d’apprentissage** , sélectionnez le fichier, puis **sélectionnez Ajouter**.

    ![Capture d’écran de l’ajout d’un fichier à partir de la page bibliothèque de fichiers d’entraînement.](../media/content-understanding/prebuilt-add-file-from-training-library.png) 

6. Dans la page **Fichiers pour analyser le modèle** , sélectionnez **Suivant**.

## <a name="select-extractors-for-your-model"></a>Sélectionner des extracteurs pour votre modèle

Dans la page des détails de l’extracteur, vous verrez la zone de document à droite et le panneau **Extracteurs** à gauche. Le panneau **Extracteurs** affiche la liste des extracteurs qui ont été identifiés dans le document.

   ![Capture d’écran de la page détails de l’extracteur et du panneau Extracteur.](../media/content-understanding/prebuilt-extractor-details-page.png) 

Les champs d’entité mis en surbrillance en vert dans la zone de document sont les éléments détectés par le modèle lors de l’analyse du fichier. Lorsque vous sélectionnez une entité à extraire, le champ mis en surbrillance passe au bleu. Si vous décidez ultérieurement de ne pas inclure l’entité, le champ mis en surbrillance passe au gris. Les surbrillances facilitent l’affichage de l’état actuel des extracteurs que vous avez sélectionnés.

> [!TIP]
> Vous pouvez utiliser la roulette de défilement sur votre souris ou les contrôles situés en bas de la zone de document pour effectuer un zoom avant ou arrière en fonction des besoins pour lire les champs d’entité.

### <a name="select-an-extractor-entity"></a>Sélectionner une entité d’extracteur

Vous pouvez sélectionner un extracteur dans la zone de document ou dans le panneau **Extracteurs** , en fonction de vos préférences.
 
- Pour sélectionner un extracteur dans la zone de document, sélectionnez le champ d’entité.

    ![Capture d’écran de la zone de document montrant comment sélectionner un champ d’entité.](../media/content-understanding/prebuilt-document-area-select-field.png) 

- Pour sélectionner un extracteur dans le panneau **Extracteurs** , cochez la case à droite du nom de l’entité.

    ![Capture d’écran du panneau Extracteurs montrant comment sélectionner un champ d’entité.](../media/content-understanding/prebuilt-extractors-panel-select-field.png) 

Lorsque vous sélectionnez un extracteur, une zone **Sélectionner un extracteur s’affiche** dans la zone de document. La zone affiche le nom de l’extracteur, la valeur d’origine et l’option permettant de le sélectionner en tant qu’extracteur. Pour certains types de données tels que les nombres ou les dates, il affiche également une valeur extraite.

   ![Capture d’écran de la zone Sélectionner un extracteur dans la page de détails de l’extracteur.](../media/content-understanding/prebuilt-select-distractor-box.png) 

La valeur d’origine correspond à ce qui se trouve réellement dans le document. La valeur extraite correspond à ce qui sera écrit dans la colonne dans SharePoint. Lorsque le modèle est appliqué à une bibliothèque, vous pouvez utiliser la mise en forme de colonne pour spécifier son apparence dans le document.

Continuez à sélectionner d’autres extracteurs que vous souhaitez utiliser. Vous pouvez également ajouter d’autres fichiers pour analyser cette configuration de modèle.

## <a name="rename-an-extractor"></a>Renommer un extracteur

Vous pouvez renommer un extracteur à partir de la page d’accueil du modèle ou du panneau **Extracteurs** . Vous pouvez envisager de renommer les extracteurs sélectionnés, car ces noms seront utilisés comme noms de colonnes lorsque le modèle est appliqué à la bibliothèque.

Pour renommer un extracteur à partir de la page d’accueil du modèle :

1. Dans la section **Extracteurs** , sélectionnez l’extracteur à renommer, puis **sélectionnez Renommer**.

    ![Capture d’écran de la section Extracteurs avec l’option Renommer mise en évidence.](../media/content-understanding/prebuilt-model-page-rename-extractor.png) 

2. Dans le panneau **Renommer l’extracteur d’entité** , entrez le nouveau nom de l’extracteur, puis sélectionnez **Renommer**.

Pour renommer un extracteur à partir du panneau **Extracteurs** :

1. Sélectionnez l’extracteur que vous souhaitez renommer, puis sélectionnez **Renommer**.

    ![Capture d’écran du panneau Extracteurs montrant comment renommer un extracteur.](../media/content-understanding/prebuilt-extractors-panel-rename-field.png) 

2. Dans la zone **Renommer l’extracteur** , entrez le nouveau nom de l’extracteur, puis sélectionnez **Renommer**.

## <a name="apply-the-model"></a>Appliquer le modèle

- Pour enregistrer les modifications et revenir à la page d’accueil du modèle, dans le volet **Extracteurs** , **sélectionnez Enregistrer et quitter**.

- Si vous êtes prêt à appliquer le modèle à une bibliothèque, dans la zone de document, sélectionnez **Suivant**. Dans le panneau **Ajouter à la bibliothèque** , choisissez la bibliothèque à laquelle vous souhaitez ajouter le modèle, puis sélectionnez **Ajouter**.

## <a name="change-the-view-in-a-document-library"></a>Modifier la vue dans une bibliothèque de documents

[!INCLUDE [Change the view in a document library](../includes/change-library-view.md)]

