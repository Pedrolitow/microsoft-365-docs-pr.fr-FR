---
title: Appliquer une étiquette de rétention à un modèle dans Microsoft Syntex
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
description: Découvrez comment appliquer une étiquette de rétention à un modèle dans Microsoft Syntex.
ms.openlocfilehash: 7fb57fa2e33bde1a3534ffbb6c4541587072b730
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68661630"
---
# <a name="apply-a-retention-label-to-a-model-in-microsoft-syntex"></a>Appliquer une étiquette de rétention à un modèle dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; traitement &ensp; | &ensp; de document non structuré &#10003; traitement &ensp;| &ensp; de document structuré &#10003; Tous les modèles prédéfinis</sup>

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>
--->

Vous pouvez facilement appliquer une [étiquette de rétention](../compliance/retention.md) à un modèle dans Microsoft Syntex.

> [!Note]
> Les étiquettes de rétention ne sont pas encore disponibles pour les modèles de traitement de documents freeform.

Les étiquettes de rétention vous permettent d’appliquer des paramètres de rétention aux documents identifiés par vos modèles.  Par exemple, vous souhaitez que votre modèle identifie non seulement les documents *d’avis d’assurance* qui sont chargés dans votre bibliothèque de documents, mais qu’il leur applique également une étiquette de rétention *Business* afin que ces documents ne puissent pas être supprimés de la bibliothèque de documents pendant la période spécifiée (les cinq mois suivants, par exemple).

Vous pouvez appliquer une étiquette de rétention préexistante à votre modèle via les paramètres du modèle sur la page d’accueil de celui-ci. 

## <a name="add-a-retention-label-to-an-unstructured-document-processing-model-or-a-prebuilt-model"></a>Ajouter une étiquette de rétention à un modèle de traitement de document non structuré ou à un modèle prédéfini

> [!Important]
> Pour que les étiquettes de rétention soient disponibles pour s’appliquer à vos modèles prédéfinis ou de traitement de documents non structurés, elles doivent être [créées](../compliance/file-plan-manager.md#create-retention-labels) et [publiées](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) dans le portail de conformité Microsoft Purview.

1. Sur la page d’accueil du modèle, sélectionnez **Paramètres du modèle**.

2. Dans **Paramètres du modèle**, dans la section **Sécurité et conformité** , sélectionnez le menu **Étiquette de rétention** pour afficher la liste des étiquettes de rétention que vous pouvez appliquer au modèle.

 ![Menu Étiquette de rétention.](../media/content-understanding/retention-labels-menu.png)

3. Sélectionnez l’étiquette de rétention que vous souhaitez appliquer au modèle, puis **Enregistrer**.

Après avoir appliqué l’étiquette de rétention à votre modèle, vous pouvez l’appliquer à un :

- nouvelle bibliothèque de documents
- bibliothèque de documents à laquelle le modèle est déjà appliqué
 
### <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Appliquer l’étiquette de rétention à une bibliothèque de documents à laquelle le modèle est déjà appliqué

Si votre modèle de traitement de document non structuré ou votre modèle prédéfini a déjà été appliqué à une bibliothèque de documents, vous pouvez effectuer les opérations suivantes pour synchroniser la mise à jour de votre étiquette de rétention afin de l’appliquer à la bibliothèque de documents :

1. Sur la page d’accueil de votre modèle, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer la mise à jour de l’étiquette de rétention.

2. Sélectionnez **Synchroniser**.

   ![Modèle de synchronisation.](../media/content-understanding/sync-model.png)</br> 

Après avoir appliqué la mise à jour et l’avoir synchronisée avec votre modèle, vous pouvez confirmer qu’elle a été appliquée en procédant comme suit :

1. Dans le centre de contenu, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque à laquelle votre modèle mis à jour a été appliqué.

2. Dans l’affichage de votre bibliothèque de documents, sélectionnez l’icône Information pour vérifier les propriétés du modèle.

3. Dans la liste **Modèles actifs**, sélectionnez votre modèle mis à jour.

4. Dans la section **Étiquette de rétention** , vous verrez le nom de l’étiquette de rétention appliquée.

Sur la page d’affichage de votre modèle, dans votre bibliothèque de documents, une nouvelle colonne **Étiquette de rétention** s’affiche.  Comme votre modèle classifie les fichiers qu’il identifie comme appartenant à son type de contenu et les répertorie dans la vue bibliothèque, la colonne **Étiquette de** rétention affiche également le nom de l’étiquette de rétention qui lui a été appliquée via le modèle.

Par exemple, tous les documents d’*avis d’assurance* que votre modèle identifie auront également l’étiquette de rétention *Entreprise* qui leur sera appliquée, ce qui fait qu’ils ne pourront pas être supprimés de la bibliothèque de documents pendant cinq mois. Si une tentative de suppression du fichier de la bibliothèque de documents est effectuée, une erreur s’affiche indiquant qu’il n’est pas autorisé en raison de l’étiquette de rétention appliquée.

## <a name="add-a-retention-label-to-a-structured-document-processing-model"></a>Ajouter une étiquette de rétention à un modèle de traitement de document structuré

> [!Important]
> Pour que les étiquettes de rétention soient disponibles pour s’appliquer à vos modèles de traitement de documents structurés, elles doivent être [créées](../compliance/file-plan-manager.md#create-retention-labels) et [publiées](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) dans le portail de conformité Microsoft Purview.

Vous pouvez appliquer une étiquette de rétention à un modèle de traitement de document structuré lorsque vous créez un modèle, ou l’appliquer à un modèle existant.

### <a name="to-add-a-retention-label-when-you-create-a-structured-document-processing-model"></a>Pour ajouter une étiquette de rétention lorsque vous créez un modèle de traitement de document structuré

1. Lorsque vous [créez un modèle de traitement de document structuré](./create-a-form-processing-model.md), sélectionnez **Paramètres avancés**.

2. Dans **Paramètres avancés**, dans la section **Étiquette de rétention**, sélectionnez le menu, puis l’étiquette de rétention que vous voulez appliquer au modèle.
 
     ![Ajouter à un nouveau modèle de traitement de document structuré.](../media/content-understanding/retention-label-forms.png)

3.  Une fois que vous avez terminé vos paramètres de modèle restants, sélectionnez **Créer** pour créer votre modèle.

### <a name="to-add-a-retention-label-to-an-existing-structured-document-processing-model"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de document structuré existant

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de document structuré existant de différentes manières :

- Via le menu **Automatiser** dans la bibliothèque de documents
- Via les paramètres **de modèle actif** dans la bibliothèque de documents 

#### <a name="to-add-a-retention-label-to-an-existing-structured-document-processing-model-through-the-automate-menu"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de document structuré existant via le menu Automatiser

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de document structuré existant que vous possédez via le menu **Automatiser** de la bibliothèque de documents dans laquelle le modèle est appliqué.

1. Dans votre bibliothèque de documents à laquelle le modèle est appliqué, sélectionnez les détails de l’affichage **du modèle** **Automatiser** > **AI Builder** > .

    ![Menu Automatiser.](../media/content-understanding/automate-menu.png)

2. Dans les détails du modèle, dans la section **Étiquette de rétention** , sélectionnez l’étiquette de rétention que vous souhaitez appliquer, puis sélectionnez **Enregistrer**.

    ![Ajouter à un modèle de traitement de document structuré existant.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-structured-document-processing-model-in-the-active-model-settings"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de document structuré existant dans les paramètres du modèle actif

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de document structuré existant que vous possédez via les paramètres modèle actif dans la bibliothèque de documents dans laquelle le modèle est appliqué.

1. Dans la bibliothèque de documents SharePoint dans laquelle le modèle est appliqué, sélectionnez l’icône **Afficher les modèles actifs**, puis sélectionnez **Afficher les modèles actifs**.

    ![Afficher les modèles actifs.](../media/content-understanding/info-du.png)

2. Dans **Modèles actifs**, sélectionnez le modèle auquel vous souhaitez appliquer l’étiquette de rétention.

    ![Détails du modèle.](../media/content-understanding/retention-label-model-details.png)</br> 

3. Dans les détails du modèle, dans la section **Étiquette de rétention** , sélectionnez l’étiquette de rétention que vous souhaitez appliquer, puis sélectionnez **Enregistrer**.

> [!NOTE]
> Vous devez être le propriétaire du modèle pour que le volet des paramètres du modèle soit modifiable. 

## <a name="see-also"></a>Voir aussi

[Appliquer une étiquette de confidentialité à un modèle dans Microsoft Syntex](create-a-classifier.md)



