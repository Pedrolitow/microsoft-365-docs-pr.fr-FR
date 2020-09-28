---
title: Application d’une étiquette de rétention à un modèle de présentation des documents
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Cet article explique comment appliquer une étiquette de rétention à un modèle de présentation des documents
ms.openlocfilehash: 26ad64906c0e2a311d8b244e8e1596a8b975cc15
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48294917"
---
# <a name="apply-a-retention-label-to-a-document-understanding-model"></a>Application d’une étiquette de rétention à un modèle de présentation des documents

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Vous pouvez facilement appliquer une [étiquette de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention) à un modèle de présentation des documents dans Microsoft SharePoint Syntex.

Les étiquettes de rétention permettent d’appliquer des paramètres de rétention aux documents identifiés par vos modèles de document.  Par exemple, vous souhaitez que votre modèle identifie non seulement les documents d' *avis d’assurance* téléchargés vers votre bibliothèque de documents, mais aussi lui appliquer une balise de rétention de l' *entreprise* afin que ces documents ne puissent pas être supprimés de la bibliothèque de documents pendant la période spécifiée (les cinq prochains mois, par exemple).

Vous pouvez appliquer une étiquette de rétention préexistante à votre modèle de compréhension de document par le biais de vos paramètres de modèle sur la page d’accueil de votre modèle. 

> [!Important]
> Pour que les étiquettes de rétention puissent être appliquées à votre modèle de compréhension de contenu, elles doivent être [créées et publiées dans le centre de conformité Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/create-apply-retention-labels#how-to-create-and-publish-retention-labels).

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Pour ajouter une étiquette de rétention à un modèle de présentation de document

1. À partir de la page d’accueil du modèle, sélectionnez **paramètres du modèle**.</br>
2. Dans **paramètres du modèle**, dans la section **sécurité et conformité** , sélectionnez le menu **étiquette** de rétention pour afficher la liste des étiquettes de rétention disponibles pour que votre s’applique au modèle.</br>
 ![Menu étiquette de rétention](../media/content-understanding/retention-labels-menu.png)</br> 
3. Sélectionnez l’étiquette de rétention que vous souhaitez appliquer au modèle, puis sélectionnez **Enregistrer**.</br>

Après avoir appliqué l’étiquette de rétention à votre modèle, vous pouvez l’appliquer à un :
- Nouvelle bibliothèque de documents
- Bibliothèque de documents à laquelle le modèle est déjà appliqué
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Appliquer l’étiquette de rétention à une bibliothèque de documents à laquelle le modèle est déjà appliqué

Si votre modèle de présentation de document a déjà été appliqué à une bibliothèque de documents, vous pouvez effectuer les opérations suivantes pour synchroniser la mise à jour de l’étiquette de rétention afin de l’appliquer à la bibliothèque de documents :</br>

1. Sur la page d’accueil de votre modèle, dans la section **bibliothèques avec ce modèle** , sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer la mise à jour des étiquettes de rétention. </br> 
2. Sélectionnez **synchroniser**. </br>
 ![Modèle de synchronisation](../media/content-understanding/sync-model.png)</br> 


Après avoir appliqué la mise à jour et la synchronisation avec votre modèle, vous pouvez vérifier qu’elle a été appliquée en procédant comme suit :

1. Dans le centre de contenu, dans la section **bibliothèques avec ce modèle** , cliquez sur la bibliothèque à laquelle le modèle mis à jour a été appliqué. </br>
2. Dans la vue de votre bibliothèque de documents, sélectionnez l’icône des informations pour vérifier les propriétés du modèle.</br>  
3. Dans la liste **modèles actifs** , sélectionnez votre modèle mis à jour.</br>
4. Dans la section **étiquette de rétention** , vous verrez le nom de l’étiquette de rétention appliquée.</br>


Sur la page d’affichage de votre modèle dans votre bibliothèque de documents, une nouvelle colonne **étiquette de rétention** s’affiche.  Comme votre modèle classifie les fichiers qu’il identifie comme appartenant à son type de contenu et les répertorie dans la vue de la bibliothèque, la colonne de l’étiquette de rétention affichera également le nom de l’étiquette de rétention qui lui a été appliquée par le biais du modèle.


Par exemple, tous les documents d' *avis d’assurance* que votre modèle identifie ont également l’étiquette de rétention de l' *entreprise* appliquée, ce qui les empêche de se supprimer de la bibliothèque de documents pendant cinq mois. Si vous tentez de supprimer le fichier de la bibliothèque de documents, une erreur s’affiche indiquant qu’il n’est pas autorisé en raison de l’étiquette de rétention appliquée.

## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Présentation de l’explication des documents](document-understanding-overview.md)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)  
