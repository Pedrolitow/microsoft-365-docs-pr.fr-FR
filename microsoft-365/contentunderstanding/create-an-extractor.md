---
title: Créer un extracteur
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez comment créer un extracteur dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 740df6769b3a1675e4e1691f84d164312b15567c
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295455"
---
# <a name="create-an-extractor-preview"></a>Créer un extracteur (aperçu)

Le contenu de cet article est destiné à la préversion privée du projet cortex. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL2G]

</br> 

Avant ou après avoir créé un modèle de classifieur pour automatiser l’identification et la classification de types de documents spécifiques, vous pouvez choisir d’ajouter des extracteurs à votre modèle pour extraire des informations spécifiques de ces documents. Par exemple, vous souhaiterez peut-être que votre modèle identifie tous les documents de *renouvellement de contrats* ajoutés à votre bibliothèque de documents, mais également d’afficher la date de *début du service* pour chaque document sous forme de colonne dans la bibliothèque de documents.

Vous devez créer un extracteur pour chaque entité dans le document que vous souhaitez extraire. Dans l’exemple, vous souhaitez extraire la *Date de début du service* pour chaque document de renouvellement de *contrat* identifié par le modèle. Cela doit se produire lorsque vous souhaitez afficher une vue dans la bibliothèque de documents de tous les documents de *renouvellement de contrat* avec une colonne indiquant la valeur de date de début du service pour chaque document.

> [!NOTE]
> Avant de créer un extracteur, vous devez [ajouter vos exemples de fichiers](https://docs.microsoft.com/microsoft-365/contentunderstanding/create-a-classifier#add-your-example-files) pour former le modèle afin d’identifier les informations que vous souhaitez extraire. Utilisez les mêmes exemples de fichiers que ceux utilisés pour créer votre classifieur.

## <a name="name-your-extractor"></a>Nommer votre extracteur

1. À partir de la page d’accueil du modèle, dans la vignette **créer et former** des **extracteurs**, cliquez sur extracteur de train.
2. Sur l’écran **nouvel extracteur d’entités** , tapez le nom de votre extracteur dans le nouveau champ nom de l' **extracteur** . Par exemple, nommez la **Date de début du service** si vous souhaitez extraire la date de début du service de chaque document de renouvellement de contrat.
3. Cliquez sur **Créer**.

## <a name="add-a-label"></a>Ajouter une étiquette

L’étape suivante consiste à étiqueter les informations que vous souhaitez extraire dans vos exemples de fichiers de formation.

La création de l’extracteur ouvre la page extracteur. Cette section affiche la liste de vos fichiers d’exemple, avec le premier fichier de la liste affichée dans la visionneuse.

1. À partir de la visionneuse, sélectionnez les données que vous souhaitez extraire des fichiers. Par exemple, si vous souhaitez extraire la *date du service de démarrage*, sélectionnez la valeur date dans le premier fichier (*lundi 14 octobre 2019*). puis cliquez sur **Enregistrer**.  La valeur s’affiche à partir du fichier dans la liste des exemples étiquetés, sous la colonne **étiquette** .
2. Sélectionnez **fichier suivant** pour l’enregistrement automatique et ouvrez le fichier suivant dans la liste de la visionneuse. Ou sélectionnez **Enregistrer** , puis un autre fichier dans la liste d' **exemples étiquetés** .
3. Dans la visionneuse, répétez les étapes 1 et 2, puis répétez l’opération jusqu’à ce que vous enregistriez l’étiquette dans les cinq fichiers.

    ![Paramètres avancés](../media/content-understanding/select-service-start-date.png) 

### <a name="add-a-negative-example"></a>Ajouter un exemple négatif

De la même manière que vous ajoutez un fichier d’exemple négatif lors de la création d’un classifieur, vous devez ajouter un échantillon négatif pour l’extracteur. Il doit s’agir d’un fichier qui ne contient pas la valeur de date « start of service ».

1. Dans la liste des **exemples étiquetés** , sélectionnez un exemple négatif.
2. Dans la visionneuse en haut de l’article, sélectionnez **aucune étiquette présente**.
3. Cliquez sur **Enregistrer**.
 
Une fois que vous avez étiqueté cinq fichiers, une bannière de notification s’affiche pour vous informer de la formation. Vous pouvez choisir un plus grand nombre de documents ou passer à la formation. 

## <a name="add-an-explanation"></a>Ajouter une explication

Pour l’exemple, vous créez une explication qui fournit une indication sur le format d’entité lui-même et les variantes qu’il peut avoir dans les exemples de documents. Par exemple, une valeur de date peut être dans différents formats, par exemple :
- 10/14/2019
- 14 octobre 2019
- Lundi 14 octobre 2019
 

Pour vous aider à identifier la *Date de début du service* , vous devez créer une explication de modèle.

1. Dans la section explication, sélectionnez **nouveau** , puis tapez un nom (par exemple, *Date*).
2. Pour type, sélectionnez **liste de motifs**.
3. Pour valeur, indiquez la variation de date telle qu’elle apparaît dans les fichiers d’exemple. Par exemple, si des formats de date s’affichent sous la forme 0/00/0000, vous entrez les variations qui apparaissent dans vos documents, telles que :
    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000
4. Sélectionnez **Enregistrer**.

### <a name="use-the-explanation-library"></a>Utiliser la bibliothèque d’explication

Pour créer des explications pour des éléments tels que des dates, il est plus facile d’utiliser la bibliothèque d’explications que d’entrer manuellement toutes les variantes. La bibliothèque d’explications est un ensemble d’explications prégénérées d’expressions et de modèles. La bibliothèque fournit tous les formats pour les listes d’expressions ou de modèles courantes, telles que les dates, les numéros de téléphone, le code postal, etc. 

Pour l’exemple de *Date de démarrage du service* , il est plus efficace d’utiliser l’explication prédéfinie pour la *Date* dans la bibliothèque d’explication :

1. Dans la **section Explication**, sélectionnez **nouveau**, puis sélectionnez **à partir de la bibliothèque d’explication**.
2. Dans la bibliothèque d’explication, sélectionnez **Date**. Vous pouvez afficher toutes les variantes de date reconnues.
3. Sélectionnez **Ajouter**.</br>

    ![Bibliothèque d’explications](../media/content-understanding/explanation-library.png) 

4. Sur la page **créer une explication** , les informations de *Date* de la bibliothèque d’explication remplissent automatiquement les champs. Sélectionnez **Enregistrer**.</br>

    ![Date](../media/content-understanding/date-explanation-library.png) 

## <a name="train-the-model"></a>Former le modèle 

Enregistrement de votre explication démarrez la formation. Si votre modèle dispose de suffisamment d’informations pour extraire les données de vos fichiers d’exemple étiquetés, vous verrez chaque fichier étiqueté avec **match**.  

![Match](../media/content-understanding/match2.png) 

Si l’explication ne contient pas suffisamment d’informations pour rechercher les données que vous souhaitez extraire, chaque fichier sera étiqueté sans **correspondance**. Vous pouvez cliquer sur les fichiers qui ne **correspondent** pas pour obtenir plus d’informations sur les raisons d’une incompatibilité.


## <a name="add-another-explanation"></a>Ajouter une autre explication

En règle générale, l’incompatibilité est une indication que l’explication que nous avons fournie n’a pas fourni suffisamment d’informations pour extraire la valeur de la date de début du service pour qu’elle corresponde à nos fichiers étiquetés. Vous devrez peut-être le modifier ou ajouter une autre explication.

Pour l’exemple, Notez que la *Date de début de* la chaîne de texte de Always précède la valeur réelle. Pour vous aider à identifier la date de début du service, vous devez créer une explication de l’expression.

1. Dans la section explication, sélectionnez **nouveau**, puis tapez un nom (par exemple, *chaîne de préfixe*).
2. Pour le type, sélectionnez **liste des expressions**.
3. Utiliser la *Date de début du service* comme valeur.
4. Sélectionnez **Enregistrer**.

    ![Chaîne de préfixe](../media/content-understanding/prefix-string.png) 

## <a name="train-the-model-again"></a>Former de nouveau le modèle

En enregistrant l’explication, vous redémarrez la formation, cette fois en utilisant les explications de l’exemple. Si votre modèle dispose de suffisamment d’informations pour extraire les données des exemples de fichiers étiquetés, vous voyez chaque fichier étiqueté avec **match**. 

Si vous recevez une nouvelle fois une **incompatibilité** avec vos fichiers étiquetés, vous devez probablement créer une autre explication pour fournir au modèle plus d’informations afin d’identifier le type de document ou envisager d’apporter des modifications à votre modèle.

## <a name="test-your-model"></a>Tester votre modèle

Si vous recevez une correspondance sur vos fichiers d’exemple étiquetés, vous pouvez maintenant tester votre modèle sur les fichiers d’exemple non labellisés restants.

1. À partir de la page d’accueil du modèle, cliquez sur l’onglet **test** .  Cela exécute le modèle sur vos fichiers d’exemple non labellisés.
2. Dans la liste des **fichiers test** , vos exemples de fichiers affichent pour indiquer si le modèle peut extraire les informations dont vous avez besoin. Utilisez ces informations pour vous aider à déterminer l’efficacité de votre classifieur lors de l’identification de vos documents.

    ![Tester vos fichiers](../media/content-understanding/test-filies-extractor.png) 
