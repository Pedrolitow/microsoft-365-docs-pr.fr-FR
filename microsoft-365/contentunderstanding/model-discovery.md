---
title: Publier et découvrir des modèles dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment mettre des modèles entraînés à la disposition d’autres utilisateurs et comment appliquer d’autres modèles formés dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 758f6886af6606c57c50c5c4c88e35f7aeeaefe4
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916268"
---
# <a name="publish-and-discover-models-in-microsoft-sharepoint-syntex"></a>Publier et découvrir des modèles dans Microsoft SharePoint Syntex

Vous pouvez rendre vos modèles de compréhension de documents entraînés disponibles pour que d’autres personnes les voient et les utilisent directement à partir de la SharePoint de documents. 

Vous pouvez également rechercher et évaluer des modèles entraînés dans d’autres centres de contenu créés par d’autres membres de votre organisation. Sélectionnez le modèle le plus utile pour classer vos fichiers ou en extraire des informations spécifiques. 

> [!NOTE]
> Cette fonctionnalité n’est pas encore disponible pour les modèles de traitement de formulaire.

## <a name="make-your-model-discoverable-to-others"></a>Rendre votre modèle accessible à d’autres personnes

Pour rendre votre modèle entraîné disponible pour d’autres personnes à utiliser :

1. Dans la page **Modèles** de votre modèle, sélectionnez **Paramètres du modèle.**

2. Dans le **volet Paramètres du modèle,** dans la section **Sites où** ce modèle est disponible, sélectionnez **Modifier**.

3. À ce stade, le panneau Sélectionner les **sites** où ce modèle est disponible sera différent selon que vous êtes administrateur ou non. 

    Si vous êtes administrateur SharePoint, cette vue s’affiche.

    ![Capture d'écran du panneau Sélectionner les sites où ce modèle est disponible montrant les options d'où vous voulez que le modèle soit disponible pour les autres.](../media/content-understanding/select-sites.png)

    - **Non disponible sur les sites** : le modèle ne sera pas disponible pour d’autres personnes.
    - **Tous les sites** : le modèle sera disponible dans la galerie de types de contenu que d’autres utilisateurs pourront utiliser.
    - **Seuls les sites** sélectionnés : vous pouvez choisir le ou les sites dans lesquels le modèle sera disponible. Cliquez dans la zone de texte pour rechercher et choisir les sites sur lesquels vous souhaitez appliquer le modèle. Vous ne verrez que les sites pour lesquels vous avez accès.

    Si vous *n’êtes pas* administrateur SharePoint, cette vue s’affiche.

    ![Capture d'écran du panneau Sélectionner les sites où ce modèle est disponible montrant les options pour les utilisateurs finaux qui n'ont que quelques sites disponibles.](../media/content-understanding/select-site-user.png)

    Vous pouvez uniquement ajouter ou supprimer la disponibilité des sites spécifiques à lesquels vous avez déjà accès.

4. Sélectionnez les sites où vous souhaitez que le modèle soit disponible pour les autres utilisateurs à appliquer, puis sélectionnez **Enregistrer**.

## <a name="discover-other-trained-models"></a>Découvrir d’autres modèles entraînés

Pour trouver des modèles entraînés qui peuvent convenir à votre contenu :

1. Dans la bibliothèque de documents de votre modèle, **sélectionnez**  >  **Automatiser l’affichage des modèles de compréhension du document.**

2. Dans la page Examiner les modèles et en appliquer de nouveaux, vous pouvez passer en revue les **modèles appliqués** et les modèles disponibles pour être appliqués à votre bibliothèque de documents.

    ![Capture d’écran des modèles de révision et application de nouvelles pages affichant les onglets Appliqué et Disponible.](../media/content-understanding/review-models-apply-new-ones.png)

   - Sous **l’onglet** Appliqué, consultez les modèles qui ont été appliqués à votre bibliothèque. Sélectionnez **Afficher les détails du modèle** pour afficher des informations sur le modèle, telles que la description, les extracteurs et d’autres paramètres.
   
   - Sous **l’onglet** Disponible, consultez les modèles entraînés qui peuvent être appliqués à votre bibliothèque.


### <a name="apply-a-trained-model-to-your-library"></a>Appliquer un modèle entraîné à votre bibliothèque

Vous pouvez évaluer les modèles entraînés par rapport à votre contenu pour vous aider à trouver le modèle le plus approprié. Pour sélectionner un modèle à appliquer à votre bibliothèque :

1. Dans la page **Examiner les modèles** et en appliquer de nouveaux, **sélectionnez l’onglet** Disponible pour passer en revue les modèles de la liste.

    ![Capture d'écran de la page "Revoir les modèles et en appliquer de nouveaux" montrant les modèles de l'onglet « Disponible ».](../media/content-understanding/available-models-to-apply.png)

2. Choisissez le modèle qui, selon vous, vous permettra d’obtenir les meilleurs résultats, sélectionnez Afficher les **détails** du modèle, puis sélectionnez Appliquer **à la bibliothèque.**

### <a name="get-a-recommendation-for-a-trained-model"></a>Obtenir une recommandation pour un modèle entraîné

Si vous ne savez pas quel modèle convient le mieux à vos fichiers, vous pouvez demander une recommandation. Votre recommandation peut inclure jusqu’à 10 modèles.

1. Dans la page **Examiner les modèles et en** appliquer de nouveaux, sélectionnez **l’onglet** Disponible.

2. Sur la première vignette, sélectionnez **Obtenir une recommandation.**

    ![Capture d'écran de la page Réviser les modèles et en appliquer de nouveaux, montrant l'option Obtenir une recommandation dans l'onglet Disponible.](../media/content-understanding/get-recommendation.png)

3. Dans la page **Sélectionner un ou plusieurs** modèles d’analyse, sélectionnez les modèles qui, selon vous, sont les plus adaptés, puis sélectionnez **Suivant.**

    ![Capture d’écran de la page Sélectionner un ou plusieurs modèles affichant les modèles recommandés avec deux modèles sélectionnés.](../media/content-understanding/recommendation-results.png)

4. Dans la page **Sélectionner un fichier à analyser,** sélectionnez un fichier du même type ou d’un type similaire qui sera stocké dans votre bibliothèque. Ensuite, choisissez **Sélectionner.**

    ![Capture d’écran de la page Sélectionner un fichier à analyser affichant les fichiers disponibles avec un fichier sélectionné.](../media/content-understanding/file-to-analyze.png)

5. Dans les **résultats de l’examen et sélectionnez une** page de modèle, sous Notre **recommandation,** vous verrez le fichier recommandé. Vous n’avez pas besoin d’appliquer le modèle recommandé. Vous pouvez choisir d’appliquer un autre modèle si vous pensez qu’il est plus adapté.

    ![Capture d’écran des résultats de la révision et sélection d’une page de modèle affichant les modèles recommandés.](../media/content-understanding/review-results.png)

6. Pour le modèle que vous pensez obtenir les meilleurs résultats, sélectionnez Afficher les **détails** du modèle, puis sélectionnez Appliquer **à la bibliothèque.**

7. S’il n’existe aucun modèle recommandé basé sur le fichier sélectionné, vous pouvez revenir en arrière et sélectionner un autre fichier ou sélectionner différents modèles.

### <a name="remove-an-applied-model"></a>Supprimer un modèle appliqué

Pour supprimer un modèle appliqué de votre bibliothèque de documents :

1. Dans la page Révision des modèles et application de nouveaux **modèles,** sous l’onglet **Appliqué, consultez les modèles qui ont été appliqués à votre bibliothèque**.

2. Sur le modèle que vous souhaitez supprimer, sélectionnez Afficher les **détails** du modèle, puis **sélectionnez Supprimer de la bibliothèque.**


## <a name="see-also"></a>Voir aussi

[Appliquer un modèle de compréhension de document](apply-a-model.md)

[Vue d’ensemble de la compréhension de document](document-understanding-overview.md)
