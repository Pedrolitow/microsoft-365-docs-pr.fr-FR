---
title: Appliquer une étiquette de rétention à un modèle de compréhension de document
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: Cet article vous explique comment appliquer une étiquette de rétention à un modèle de compréhension de document
ms.openlocfilehash: 6dcd81b580b7bf0801641bbd019e1b99ecfe7338
ms.sourcegitcommit: 162c01dfaa2fdb3225ce4c24964c1065ce22ed5d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "49976554"
---
# <a name="apply-a-retention-label-to-a-document-understanding-model"></a>Appliquer une étiquette de rétention à un modèle de compréhension de document

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GydO]  

</br>


Vous pouvez facilement appliquer une [étiquette de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention) à un modèle de compréhension de document dans Microsoft SharePoint Syntex.

Les étiquettes de rétention vous permettent d’appliquer des paramètres de rétention aux documents identifiés par vos modèles de compréhension de document.  Par exemple, vous souhaitez que votre modèle identifie tous les documents d’*avis d’assurance* qui sont téléchargés dans votre bibliothèque de documents, mais également qu’il leur applique une étiquette de rétention *Entreprise*, afin que ces documents ne puissent pas être supprimés de la bibliothèque de documents pendant la période spécifiée ( les cinq prochains mois, par exemple).

Vous pouvez appliquer une étiquette de rétention préexistante à votre modèle de compréhension de document via les paramètres du modèle sur la page d’accueil de celui-ci. 

> [!Important]
> Pour que les étiquettes de rétention soient disponibles et s’appliquent à votre modèle de compréhension de contenu, elles doivent être [créées et publiées dans le Centre de conformité Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/create-apply-retention-labels#how-to-create-and-publish-retention-labels).

## <a name="to-add-a-retention-label-to-a-document-understanding-model"></a>Pour ajouter une étiquette de rétention à un modèle de compréhension de document

1. Sur la page d’accueil du modèle, sélectionnez **Paramètres du modèle**.</br>
2. Dans **Paramètres du modèle**, dans la section **Sécurité et conformité**, sélectionnez le menu **Étiquette de rétention** pour afficher une liste des étiquettes de rétention que vous pouvez appliquer au modèle.</br>
 ![Menu Étiquette de rétention](../media/content-understanding/retention-labels-menu.png)</br> 
3. Sélectionnez l’étiquette de rétention que vous souhaitez appliquer au modèle, puis **Enregistrer**.</br>

Après avoir appliqué l’étiquette de rétention à votre modèle, vous pouvez l’appliquer à une :
- nouvelle bibliothèque de documents
- bibliothèque de documents à laquelle le modèle est déjà appliqué
 
## <a name="apply-the-retention-label-to-a-document-library-to-which-the-model-is-already-applied"></a>Appliquer l’étiquette de rétention à une bibliothèque de documents à laquelle le modèle est déjà appliqué

Si votre modèle de compréhension de document a déjà été appliqué à une bibliothèque de documents, vous pouvez effectuer les opérations suivantes pour synchroniser la mise à jour de votre étiquette de rétention afin de l’appliquer à la bibliothèque de documents :</br>

1. Sur la page d’accueil de votre modèle, dans la section **Bibliothèques avec ce modèle**, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer la mise à jour de l’étiquette de rétention. </br> 
2. Sélectionnez **Synchroniser**. </br>
 ![Modèle de synchronisation](../media/content-understanding/sync-model.png)</br> 


Après avoir appliqué la mise à jour et l’avoir synchronisée avec votre modèle, vous pouvez vérifier si elle a été appliquée en procédant comme suit :

1. Dans le centre de contenu, dans la section **Bibliothèques avec ce modèle**, cliquez sur la bibliothèque à laquelle votre modèle mis à jour a été appliqué. </br>
2. Dans l’affichage de votre bibliothèque de documents, sélectionnez l’icône Information pour vérifier les propriétés du modèle.</br>  
3. Dans la liste **Modèles actifs**, sélectionnez votre modèle mis à jour.</br>
4. Dans la section **Étiquette de rétention**, vous verrez le nom de l’étiquette de rétention appliquée.</br>


Sur la page d’affichage de votre modèle, dans votre bibliothèque de documents, une nouvelle colonne **Étiquette de rétention** s’affiche.  Lorsque votre modèle classe les fichiers qu’il identifie comme appartenant à son type de contenu et les répertorie dans l’affichage de la bibliothèque, la colonne Étiquette de rétention affiche également le nom de l’étiquette de rétention qui lui a été appliquée via le modèle.


Par exemple, tous les documents d’*avis d’assurance* que votre modèle identifie auront également l’étiquette de rétention *Entreprise* qui leur sera appliquée, ce qui fait qu’ils ne pourront pas être supprimés de la bibliothèque de documents pendant cinq mois. Si vous tentez de supprimer le fichier de la bibliothèque de documents, une erreur s’affiche indiquant que l’opération n’est pas autorisée en raison de l’étiquette de rétention appliquée.

## <a name="see-also"></a>Voir aussi
[Créer un classifieur](create-a-classifier.md)

[Créer un extracteur](create-an-extractor.md)

[Présentation de la compréhension de document](document-understanding-overview.md)


