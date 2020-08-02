---
title: Créer un modèle de traitement de formulaire (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/1/2020
audience: admin
ms.topic: article
ms.service: ''
search.appverid: ''
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
description: Créez un modèle de traitement de formulaire dans le projet cortex.
ms.openlocfilehash: d3ca64ff5923e95704b72fd748884549a18624a3
ms.sourcegitcommit: 3a47efcbdf3d2b39caa2798ea5be806839b05ed1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2020
ms.locfileid: "46540141"
---
# <a name="create-a-form-processing-model-preview"></a>Créer un modèle de traitement de formulaire (aperçu)

> [!Note] 
> Le contenu de cet article est destiné à Project cortex privé preview. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

Utilisation de l’outil [ai Builder](https://docs.microsoft.com/ai-builder/overview) -une fonctionnalité de Microsoft PowerApp-Project cortex les utilisateurs peuvent créer un [modèle de traitement de formulaire](form-processing-overview.md) directement à partir d’une bibliothèque de documents SharePoint. 

La création d’un modèle de traitement de formulaire implique les opérations suivantes :
 - Étape 1 : créer le modèle de traitement pour créer le type de contenu
 - Étape 2 : ajouter et analyser des exemples de fichiers
 - Étape 3 : sélection de vos champs de formulaire
 - Étape 4 : formation et test de votre modèle
 - Étape 5 : publier votre modèle
 - Étape 6 : utiliser votre modèle


## <a name="requirements"></a>Conditions préalables

Vous pouvez uniquement créer un modèle de traitement de formulaire dans les bibliothèques de documents SharePoint dans lesquelles il est activé. Si le traitement des formulaires est activé, vous pouvez voir le **Générateur d’ai** **« créer un modèle de traitement de formulaire »** dans le menu **automatiser** de votre bibliothèque de documents.  Si vous avez besoin d’un traitement activé dans votre bibliothèque de documents, contactez votre administrateur.

 ![Créer un modèle de générateur AI](../media/content-understanding/create-ai-builder-model.png)</br>


## <a name="step-1-create-a-form-processing-model"></a>Étape 1 : créer un modèle de traitement de formulaire

La première étape de la création d’un modèle de traitement de formulaire consiste à le nommer de façon à créer le nouveau type de contenu et à créer une nouvelle vue de bibliothèque de documents.

1. Dans votre bibliothèque de documents, sélectionnez le menu **automatiser** , sélectionnez **générateur ai**, puis sélectionnez **créer un modèle de traitement de formulaire**.

    ![Créer un modèle de générateur AI](../media/content-understanding/create-ai-builder-model.png)</br>
2. Dans le volet **nouveau modèle de traitement de formulaire** , dans le champ **nom** , tapez un nom pour votre modèle (par exemple, *bons de commande*).

    ![Nouveau modèle de traitement de formulaire](../media/content-understanding/new-form-model.png)</br> 

3. Lorsque vous créez un modèle de traitement de formulaire, vous créez un nouveau type de contenu SharePoint. Un type de contenu SharePoint représente une catégorie de documents qui ont des caractéristiques communes et qui partagent une collection de colonnes ou de propriétés de métadonnées pour ce contenu particulier. Les types de contenu SharePoint sont gérés via la [Galerie de types de contenu]().

    Sélectionnez **Paramètres avancés** si vous souhaitez mapper ce modèle à un type de contenu existant dans la Galerie de types de contenu SharePoint pour utiliser son schéma. 

4. Votre modèle crée un nouvel affichage dans votre bibliothèque de documents pour vos données extraites. Si vous ne souhaitez pas que l’affichage par défaut s’affiche, désélectionnez **définir l’affichage comme mode par défaut**.
5. Sélectionnez **Créer**.


## <a name="step-2-add-and-analyze-documents"></a>Étape 2 : ajouter et analyser des documents

Une fois que vous avez créé votre nouveau modèle de traitement de formulaire, votre navigateur ouvre une nouvelle page de modèle de traitement des formulaires du générateur AI PowerApp. Sur cette page, vous pouvez ajouter et analyser vos exemples de documents. </br>

> [!Note]
> Lorsque vous recherchez des exemples de fichiers à utiliser, voir le [modèle de traitement de formulaire exigences en matière de document d’entrée et conseils d’optimisation](https://docs.microsoft.com/ai-builder/form-processing-model-requirements). 

   ![Générateur d’applications d’alimentation](../media/content-understanding/powerapps.png)</br> 
 

1. Cliquez sur **Ajouter des documents** pour commencer à ajouter des exemples de documents analysés afin de déterminer les paires de valeurs nommées pouvant être extraites. Vous pouvez choisir **Télécharger à partir du stockage local**, **SharePoint**ou le **stockage BLOB Azure**. Vous devrez utiliser au moins cinq fichiers pour la formation.
2. Après avoir ajouté vos fichiers, sélectionnez **analyser** pour vérifier les informations courantes : tous les fichiers. Notez que cette opération peut prendre plusieurs minutes.</br> 
 
    ![Analyser les fichiers](../media/content-understanding/analyze.png)</br> 

3. Une fois qu’ils ont été analysés, dans la page **sélectionnez les champs de formulaire que vous souhaitez enregistrer** , cliquez sur le fichier pour afficher les champs qui ont été détectés.</br>

    ![Sélectionner les champs de formulaire](../media/content-understanding/select-form-fields.png)</br> 

## <a name="step-3-select-your-form-fields"></a>Étape 3 : sélection de vos champs de formulaire

Après avoir analysé vos documents pour les champs, vous pouvez voir les champs trouvés et ceux que vous souhaitez enregistrer. Les champs enregistrés s’affichent sous forme de colonnes dans la vue bibliothèque de documents de votre modèle et affichent les valeurs extraites de chaque document.

1. La page suivante affiche l’un de vos fichiers d’exemple et met en surbrillance tous les champs communs détectés automatiquement par le système. </br>

    ![Sélectionner les champs de formulaire](../media/content-understanding/select-fields-page.png)</br> 

2. Sélectionnez les champs que vous souhaitez enregistrer, puis activez la case à cocher pour confirmer votre sélection. Par exemple, dans le modèle bon de commande, vous pouvez choisir de sélectionner les champs *Date*, *op*et *total* .  Notez que vous pouvez également choisir de renommer un champ si vous le souhaitez. </br>

    ![Sélectionnez cf #](../media/content-understanding/po.png)</br> 

3. Si un champ n’a pas été détecté par l’analyse, vous pouvez toujours choisir de l’ajouter. Mettez en surbrillance les informations que vous souhaitez extraire, et dans la zone Nom, tapez le nom que vous voulez lui attribuer. Ensuite, sélectionnez la case à cocher. Notez que vous devrez confirmer les champs non détectés dans vos fichiers restants.
4. Cliquez sur **confirmer les champs** après avoir sélectionné les champs que vous souhaitez enregistrer. </br>
 
    ![Confirmer les champs](../media/content-understanding/confirm-fields.png)</br> 
 
5. Dans la page **sélectionnez les champs de formulaire que vous souhaitez enregistrer** , le nombre de champs que vous avez sélectionnés est affiché. Sélectionnez **Terminé**.

## <a name="step-4-train-and-test-your-model"></a>Étape 4 : formation et test de votre modèle

Après avoir sélectionné les champs que vous souhaitez enregistrer, la page de **Résumé du modèle** vous permettra de former et de tester votre modèle.

1. Sur la page **Résumé du modèle** , les champs enregistrés s’affichent dans la section **champs sélectionnés** . Sélectionnez **train** pour commencer la formation sur vos exemples de fichiers. Notez que cette opération peut prendre quelques minutes.</br>
    ![Confirmer les champs](../media/content-understanding/select-fields-train.png)</br> 
2. Lorsque vous voyez la notification indiquant que la formation est terminée, sélectionnez **accéder à la page Détails**. 
3. Sur la page **Détails du modèle** , vous pouvez choisir de tester le fonctionnement de votre modèle en sélectionnant **test rapide**. Cela vous permet de glisser-déplacer des fichiers vers la page et de voir si les champs sont détectés.

## <a name="step-5-publish-your-model"></a>Étape 5 : publier votre modèle



1. Si vous êtes satisfait des résultats de votre modèle, sélectionnez **publier** pour le mettre à disposition.
2. Une fois le modèle publié, sélectionnez **utiliser le modèle**. Cela crée un flux PowerAutomate qui s’exécutera dans votre bibliothèque de documents SharePoint et extraira les champs identifiés dans le modèle. Sélectionnez **créer un flux**.  
3. Une fois l’opération terminée, vous verrez le message que **votre flux a été créé avec succès**.
 
 
## <a name="step-6-use-your-model"></a>Étape 6 : utiliser votre modèle

Après avoir publié votre modèle et créé son flux PowerAutomate, vous pouvez utiliser votre modèle dans votre bibliothèque de documents SharePoint.

1. Après avoir publié votre modèle, sélectionnez **accéder à SharePoint** pour accéder à votre bibliothèque de documents.
2. Dans votre vue de modèle de bibliothèque de documents, Notez que les champs que vous avez sélectionnés s’affichent désormais sous forme de colonnes.</br>

    ![Bibliothèque de documents avec modèle appliqué](../media/content-understanding/doc-lib-view.png)</br> 

    Notez également que le lien d’informations en regard de **documents** indique qu’un modèle de traitement des formulaires est appliqué à cette bibliothèque de documents.

    ![Compressé](../media/content-understanding/info-button.png)</br>  

3. Charger des fichiers dans votre bibliothèque de documents. Tous les fichiers que le modèle identifie comme étant le type de contenu répertorient les fichiers dans votre affichage et affichent les données extraites dans les colonnes.</br>

    ![Compressé](../media/content-understanding/doc-lib-done.png)</br>  



## <a name="see-also"></a>Voir aussi
  
[Mise à l’arrêt de la documentation](https://docs.microsoft.com/power-automate/)</br>
[Formation : améliorer les performances d’entreprise avec le générateur AI](https://docs.microsoft.com/learn/paths/improve-business-performance-ai-builder/?source=learn)</br>




