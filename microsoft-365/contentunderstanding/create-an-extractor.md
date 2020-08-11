---
title: Créer un extracteur (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.service: ''
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment créer un extracteur
ms.openlocfilehash: 64dede9f6613da82c65ca12c6c335a25301f5b9e
ms.sourcegitcommit: a3a5dc541b0c971608cc86ef480509c25a13ca60
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "46612761"
---
# <a name="create-an-extractor-preview"></a>Créer un extracteur (aperçu)
> [!Note] 
> Le contenu de cet article est destiné à Project cortex privé preview. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

</br> 

Avant ou après avoir créé un modèle de classifieur pour automatiser l’identification et la classification de types de documents spécifiques, vous pouvez choisir d’ajouter des extracteurs à votre modèle pour extraire des informations spécifiques de ces documents. Par exemple, vous souhaiterez peut-être que votre modèle identifie tous les documents de *renouvellement de contrats* ajoutés à votre bibliothèque de documents, mais aussi afficher la date de *début du service* pour chaque document sous forme de colonne dans la bibliothèque de documents.

Vous devez créer un extracteur pour chaque entité dans le document que vous souhaitez extraire. Dans notre exemple, nous souhaitons extraire la *Date de début du service* pour chaque document de renouvellement de *contrat* identifié par le modèle. Nous souhaitons être en mesure d’afficher une vue dans la bibliothèque de documents de tous les documents de *renouvellement de contrat* , avec une colonne qui indique la valeur de date de début du service de chaque document.

> [!Note]
> Avant de créer un extracteur, vous devez [ajouter vos exemples de fichiers](https://docs.microsoft.com/microsoft-365/contentunderstanding/create-a-classifier?view=o365-worldwide#add-your-example-files) dont vous aurez besoin pour former le modèle afin d’identifier les informations que vous souhaitez extraire. Utilisez les mêmes exemples de fichiers que ceux utilisés pour créer votre classifieur.


## <a name="name-your-extractor"></a>Nommer votre extracteur

1. Sur la page d’accueil du modèle, dans la vignette **créer et former** des **extracteurs**, cliquez sur extracteur de train.
2. Sur l’écran **nouvel extracteur d’entités** , tapez le nom de votre extracteur dans le nouveau champ nom de l' **extracteur** . Par exemple, nous pouvons nommer **Date de début du service** si nous voulons extraire la date de début du service de chaque document de renouvellement de contrat.
3. Cliquez sur **Créer**.

## <a name="add-a-label"></a>Ajouter une étiquette

L’étape suivante consiste à étiqueter les informations que vous souhaitez extraire dans vos exemples de fichiers de formation.

La création de l’extracteur ouvre la page extracteur dans laquelle vous verrez une liste de vos exemples de fichiers, avec le premier fichier de la liste affichée dans la visionneuse.

1. Dans la visionneuse, sélectionnez les données que vous souhaitez extraire des fichiers. Par exemple, si vous souhaitez extraire la *date du service de démarrage*, vous devez mettre en surbrillance la valeur de date correspondant au premier fichier (*lundi 14 octobre 2019*). Puis cliquez sur **Enregistrer**.  Vous verrez l’affichage de la valeur du fichier dans la liste d’exemples étiquetée sous la colonne **étiquette** .
2. Sélectionnez **fichier suivant** pour l’enregistrement automatique et ouvrez le fichier suivant dans la liste de la visionneuse, ou sélectionnez **Enregistrer** et sélectionnez un autre fichier dans la liste **exemples étiquetés** .
3. Dans la visionneuse, répétez les étapes 1 et 2, puis faites-le jusqu’à ce que vous ayez enregistré l’étiquette dans cinq fichiers.

    ![Paramètres avancés](../media/content-understanding/select-service-start-date.png) 


### <a name="add-a-negative-example"></a>Ajouter un exemple négatif

De la même manière que vous ajoutez un fichier d’exemple négatif lors de la création d’un classifieur, vous devez ajouter un exemple négatif pour l’extracteur. Pour notre exemple, il doit s’agir d’un fichier qui ne contient pas de valeur de date de début de service.

1. Dans la liste des **exemples étiquetés** , sélectionnez un exemple négatif.
2. Dans la visionneuse, en haut de l’article, sélectionnez **aucune étiquette présente**.
3. Cliquez sur **Enregistrer**.
 
Une fois que vous avez étiqueté cinq fichiers, une bannière de notification s’affiche pour vous informer sur la formation. Vous pouvez choisir un plus grand nombre de documents ou passer à la formation. 

## <a name="add-an-explanation"></a>Ajouter une explication

Pour notre exemple, nous allons créer une explication qui fournit une indication sur le format d’entité lui-même et les variantes qu’il peut contenir dans les exemples de documents. Par exemple, une valeur de date peut être dans différents formats, par exemple :
- 10/14/2019
- 14 octobre 2019
- Lundi 14 octobre 2019
 

Pour vous aider à identifier la *Date de début du service* , vous pouvez créer une explication de modèle.

1. Dans la section explication, sélectionnez **nouveau**, puis tapez un nom (par exemple, *Date*).
2. Pour le type, sélectionnez **liste de motifs**.
3. Pour la valeur, vous devez indiquer la variation de date telle qu’elle apparaît dans les fichiers d’exemple. Par exemple, si des formats de date s’affichent sous la forme 0/00/0000, vous devez entrer les variations susceptibles d’apparaître dans vos documents, telles que :
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. Sélectionnez **Enregistrer**.


### <a name="use-the-explanation-library"></a>Utiliser la bibliothèque d’explication

Pour créer des explications pour des éléments tels que des dates, il est beaucoup plus facile d’utiliser la bibliothèque d’explications que d’entrer manuellement toutes les variantes. La bibliothèque d’explications est un ensemble d’explications prégénérées d’expressions et de modèles. La bibliothèque tente de fournir tous les formats pour les listes d’expressions ou de modèles courantes, telles que les dates, les numéros de téléphone, le code postal et bien d’autres. 

Pour notre exemple de *Date de début de service* , il est plus efficace d’utiliser l’explication prédéfinie pour la *Date* dans la bibliothèque d’explication :

1. Dans la **section Explication**, * * sélectionnez **nouveau**, puis sélectionnez **à partir de la bibliothèque d’explication**.
2. Dans la bibliothèque d’explication, sélectionnez **Date**. Vous pouvez afficher toutes les variantes de date qui seront reconnues.
3. Sélectionnez **Ajouter**.</br>

    ![Bibliothèque d’explications](../media/content-understanding/explanation-library.png) 

4. Sur la page **créer une explication** , les informations de *Date* de la bibliothèque d’explication renseignent automatiquement les champs. Sélectionnez **Enregistrer**.</br>

    ![Bibliothèque d’explications](../media/content-understanding/date-explanation-library.png) 

 
## <a name="train-the-model"></a>Former le modèle 

L’enregistrement de votre explication démarrera la formation. Si votre modèle dispose de suffisamment d’informations pour extraire les données de vos fichiers d’exemple étiquetés, vous verrez chaque fichier étiqueté avec **match**.  

![Bibliothèque d’explications](../media/content-understanding/match2.png) 

Si l’explication ne contient pas suffisamment d’informations pour rechercher les données que vous souhaitez extraire, chaque fichier sera étiqueté sans **correspondance**. Vous pouvez cliquer sur les fichiers qui ne correspondent pas pour obtenir plus d’informations sur les raisons d’une incompatibilité.


## <a name="add-another-explanation"></a>Ajouter une autre explication

En règle générale, l’incompatibilité est une indication que l’explication que nous avons fournie n’a pas fourni suffisamment d’informations pour extraire la valeur de la date de début du service pour qu’elle corresponde à nos fichiers étiquetés. Vous devrez peut-être le modifier ou ajouter une autre explication.

Pour notre exemple, nous constatons que la *Date de début de* la chaîne de texte de Always précède la valeur réelle. Pour vous aider à identifier la date de début du service, nous pouvons créer une explication de l’expression.

1. Dans la section explication, sélectionnez **nouveau**, puis tapez un nom (par exemple, *chaîne de préfixe*).
2. Pour le type, sélectionnez **liste des expressions**.
3. Utiliser la *Date de début du service* comme valeur.
4. Sélectionnez **Enregistrer**.

    ![Bibliothèque d’explications](../media/content-understanding/prefix-string.png) 


## <a name="train-the-model"></a>Former le modèle

L’enregistrement de votre explication redémarrera la formation, cette fois en utilisant les explications de notre exemple. Si votre modèle dispose de suffisamment d’informations pour extraire les données de vos fichiers d’exemple étiquetés, vous verrez chaque fichier étiqueté avec **match**. 

Si vous recevez une nouvelle fois une **incompatibilité** avec vos fichiers étiquetés, vous devrez peut-être créer une autre explication pour fournir au modèle plus d’informations afin d’identifier le type de document ou d’apporter des modifications à vos existants.

## <a name="test-your-model"></a>Tester votre modèle

Si vous avez reçu une correspondance sur vos exemples de fichiers étiquetés, vous pouvez maintenant tester votre modèle sur vos fichiers d’exemple sans étiquette restants.

1. Sur la page d’accueil du modèle, cliquez sur l’onglet **test** .  Cette opération exécutera le modèle sur vos fichiers d’exemple sans étiquette.
2. Dans la liste des **fichiers test** , vos exemples de fichiers s’affichent et s’affichent si le modèle peut extraire les informations dont vous avez besoin. Vous pouvez utiliser ces informations pour déterminer l’efficacité de votre classifieur lors de l’identification de vos documents.

    ![Tester vos fichiers](../media/content-understanding/test-filies-extractor.png) 

## <a name="see-also"></a>Voir aussi
  




