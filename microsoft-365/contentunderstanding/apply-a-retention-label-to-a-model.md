---
title: Application d’une étiquette de rétention à un modèle dans SharePoint Syntex.
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
description: Découvrez comment appliquer une étiquette de rétention à un modèle dans SharePoint Syntex.
ms.openlocfilehash: 2176826634b1f682f86989d418b251f9706100ed
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585661"
---
# <a name="apply-a-retention-label-to-a-model-in-sharepoint-syntex"></a>Application d’une étiquette de rétention à un modèle dans SharePoint Syntex.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>

Vous pouvez facilement appliquer une [étiquette de rétention](../compliance/retention.md) à un modèle dans Microsoft SharePoint Syntex. Vous pouvez le faire pour la compréhension des documents et les modèles de traitement des formulaires.

Les étiquettes de rétention vous permettent d’appliquer des paramètres de rétention aux documents identifiés par vos modèles.  Par exemple, vous souhaitez que votre modèle identifie tous les documents d’*avis d’assurance* qui sont téléchargés dans votre bibliothèque de documents, mais également qu’il leur applique une étiquette de rétention *Entreprise*, afin que ces documents ne puissent pas être supprimés de la bibliothèque de documents pendant la période spécifiée ( les cinq prochains mois, par exemple).

Vous pouvez appliquer une étiquette de rétention préexistante à votre modèle via les paramètres du modèle sur la page d’accueil de celui-ci. 

> [!Important]
> Pour que les étiquettes de rétention soient disponibles pour s’appliquer à vos modèles de compréhension de document, elles doivent être [créées](../compliance/file-plan-manager.md#create-retention-labels) et [publiées](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) dans le portail de conformité Microsoft Purview.

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Pour ajouter une étiquette de rétention à un modèle de compréhension de document

1. Sur la page d’accueil du modèle, sélectionnez **Paramètres du modèle**.</br>
2. Dans **Paramètres du modèle**, dans la section **Sécurité et conformité**, sélectionnez le menu **Étiquette de rétention** pour afficher une liste des étiquettes de rétention que vous pouvez appliquer au modèle.</br>
 ![Menu Étiquette de rétention.](../media/content-understanding/retention-labels-menu.png)</br> 
3. Sélectionnez l’étiquette de rétention que vous souhaitez appliquer au modèle, puis **Enregistrer**.</br>

Après avoir appliqué l’étiquette de rétention à votre modèle, vous pouvez l’appliquer à une :
- nouvelle bibliothèque de documents
- bibliothèque de documents à laquelle le modèle est déjà appliqué
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Appliquer l’étiquette de rétention à une bibliothèque de documents à laquelle le modèle est déjà appliqué

Si votre modèle de compréhension de document a déjà été appliqué à une bibliothèque de documents, vous pouvez effectuer les opérations suivantes pour synchroniser la mise à jour de votre étiquette de rétention afin de l’appliquer à la bibliothèque de documents :</br>

1. Sur la page d’accueil de votre modèle, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer la mise à jour de l’étiquette de rétention. </br> 
2. Sélectionnez **Synchroniser**. </br>
 ![Modèle de synchronisation.](../media/content-understanding/sync-model.png)</br> 


Après avoir appliqué la mise à jour et l’avoir synchronisée avec votre modèle, vous pouvez vérifier si elle a été appliquée en procédant comme suit :

1. Dans le centre de contenu, dans la section **Bibliothèques avec ce modèle**, cliquez sur la bibliothèque à laquelle votre modèle mis à jour a été appliqué. </br>
2. Dans l’affichage de votre bibliothèque de documents, sélectionnez l’icône Information pour vérifier les propriétés du modèle.</br>  
3. Dans la liste **Modèles actifs**, sélectionnez votre modèle mis à jour.</br>
4. Dans la section **Étiquette de rétention**, vous verrez le nom de l’étiquette de rétention appliquée.</br>


Sur la page d’affichage de votre modèle, dans votre bibliothèque de documents, une nouvelle colonne **Étiquette de rétention** s’affiche.  Lorsque votre modèle classe les fichiers qu’il identifie comme appartenant à son type de contenu et les répertorie dans l’affichage de la bibliothèque, la colonne Étiquette de rétention affiche également le nom de l’étiquette de rétention qui lui a été appliquée via le modèle.


Par exemple, tous les documents d’*avis d’assurance* que votre modèle identifie auront également l’étiquette de rétention *Entreprise* qui leur sera appliquée, ce qui fait qu’ils ne pourront pas être supprimés de la bibliothèque de documents pendant cinq mois. Si vous tentez de supprimer le fichier de la bibliothèque de documents, une erreur s’affiche indiquant que l’opération n’est pas autorisée en raison de l’étiquette de rétention appliquée.

## <a name="to-add-a-retention-label-to-a-form-processing-model"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de formulaire

> [!Important]
> Pour que les étiquettes de rétention soient disponibles pour s’appliquer à votre modèle de traitement de formulaire, elles doivent être [créées](../compliance/file-plan-manager.md#create-retention-labels) et [publiées](../compliance/create-apply-retention-labels.md#how-to-publish-retention-labels) dans le portail de conformité Microsoft Purview.

Vous pouvez appliquer une étiquette de rétention à un modèle de traitement de formulaires lorsque vous créez un modèle ou l’appliquer à un modèle existant.

### <a name="to-add-a-retention-label-when-you-create-a-form-processing-model"></a>Pour ajouter une étiquette de rétention lorsque vous créez un modèle de traitement de formulaire

1. Lorsque vous [créez un modèle de traitement de formulaires,](./create-a-form-processing-model.md)sélectionnez <b>Paramètres avancés.</b>
2. Dans <b>Paramètres avancés</b>, dans la section <b>Étiquette de rétention</b>, sélectionnez le menu, puis l’étiquette de rétention que vous voulez appliquer au modèle.</b>

 
     ![Ajouter à un nouveau modèle de traitement de formulaire.](../media/content-understanding/retention-label-forms.png)</br>

3.  Une fois que vous avez terminé vos paramètres de modèle restants, sélectionnez <b>Créer</b> pour créer votre modèle.

### <a name="to-add-a-retention-label-to-an-existing-form-processing-model"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de formulaire existant

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de formulaire existant de différentes manières :
- Via le menu Automatiser de la bibliothèque de documents
- Via les paramètres de modèle actif dans la bibliothèque de documents 


#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-through-the-automate-menu"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de formulaire existant via le menu Automatiser

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de formulaires que vous possédez via le menu Automatiser de la bibliothèque de documents dans laquelle le modèle est appliqué.


1. Dans la bibliothèque de documents à laquelle le modèle de traitement de formulaire est appliqué, sélectionnez le menu <b>Automatiser</b>, sélectionnez <b>Générateur IA</b>, puis sélectionnez <b>Afficher les détails du modèle de traitement de formulaire</b>.

   ![Menu Automatiser.](../media/content-understanding/automate-menu.png)</br>

2. Dans les détails du modèle, dans la section <b>Étiquette de rétention</b> , sélectionnez l’étiquette de rétention que vous voulez appliquer.  Sélectionnez <b>Enregistrer</b>.

     ![Ajouter à un modèle de traitement de formulaire existant.](../media/content-understanding/retention-label-model-details.png)</br> 

#### <a name="to-add-a-retention-label-to-an-existing-form-processing-model-in-the-active-model-settings"></a>Pour ajouter une étiquette de rétention à un modèle de traitement de formulaire existant dans les paramètres du modèle actif

Vous pouvez ajouter une étiquette de rétention à un modèle de traitement de formulaires que vous possédez via les paramètres du modèle actif de la bibliothèque de documents dans laquelle le modèle est appliqué.

1. Dans la bibliothèque de documents SharePoint dans laquelle le modèle est appliqué, sélectionnez l’icône <b>Afficher les modèles actifs</b>, puis sélectionnez <b>Afficher les modèles actifs</b>.</b>

   ![Afficher les modèles actifs.](../media/content-understanding/info-du.png)</br> 

2. Dans <b>Modèles actifs</b>, sélectionnez le modèle de traitement de formulaire auquel vous voulez appliquer l’étiquette de rétention.

     ![Détails du modèle.](../media/content-understanding/retention-label-model-details.png)</br> 


3. Dans les détails du modèle, dans la section <b>Étiquette de rétention</b> , sélectionnez l’étiquette de rétention que vous voulez appliquer.  Sélectionnez <b>Enregistrer</b>.

> [!NOTE]
> Vous devez être le propriétaire du modèle pour que le volet des paramètres du modèle soit modifiable. 


## <a name="see-also"></a>Voir aussi

[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)
