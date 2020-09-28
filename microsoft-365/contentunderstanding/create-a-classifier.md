---
title: Créer un classifieur
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
description: En savoir plus sur la création d’un classifieur
ms.openlocfilehash: 29b2a4775bec12649c66b4cb4a07fe5f0fc93ae2
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48294901"
---
# <a name="create-a-classifier-in-microsoft-sharepoint-syntex"></a>Créer un classifieur dans Microsoft SharePoint Syntex

Le contenu de cet article est destiné à la préversion privée du projet cortex. Pour [plus d’informations sur le projet cortex](https://aka.ms/projectcortex).

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CL0R]  

</br>

Un classifieur est un type de modèle que vous pouvez utiliser pour automatiser l’identification et la classification d’un type de document. Par exemple, vous pouvez identifier tous les documents de *renouvellement de contrat* ajoutés à votre bibliothèque de documents, comme illustré dans l’illustration suivante.

![Document de renouvellement de contrat](../media/content-understanding/contract-renewal.png)

La création d’un classifieur vous permet de créer un nouveau [type de contenu SharePoint](https://docs.microsoft.com/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) qui sera associé au modèle.

Lors de la création du classifieur, vous devez créer des *explications* pour définir le modèle. Cela vous permet de noter les données communes que vous devriez voir toujours trouver ce type de document. 

Utilisez des exemples de type de document (« exemples de fichiers ») pour « former » votre modèle afin d’identifier les fichiers qui ont le même type de contenu.

Pour créer un classifieur, vous devez :
1. Nommez votre modèle.
2. Ajoutez vos exemples de fichiers.
3. Étiquetez vos exemples de fichiers.
4. Créer une explication.
5. Testez votre modèle.

> [!NOTE]
> Bien que votre modèle utilise un classifieur pour identifier et classer les types de documents, vous pouvez également choisir d’extraire des informations spécifiques de chaque fichier identifié par le modèle. Pour ce faire, créez un **extracteur** à ajouter à votre modèle. Consultez la rubrique [créer un extracteur](create-an-extractor.md).

## <a name="name-your-model"></a>Nommer votre modèle

La première étape pour créer votre modèle consiste à lui attribuer un nom :

1. Dans le centre de contenu, sélectionnez **nouveau**, puis **créez un modèle**.
2. Dans le volet **nouveau modèle de présentation des documents** , dans le champ **nom** , tapez le nom du modèle. Par exemple, si vous souhaitez identifier les documents de renouvellement de contrat, vous pouvez nommer le modèle *renouvellement de contrat*.
3. Sélectionnez **Créer**. Cela crée une page d’accueil pour le modèle.</br>

    ![Page d’accueil du modèle de classifieur](../media/content-understanding/model-home.png)

Lorsque vous créez un modèle, vous créez également un nouveau type de contenu SharePoint. Un type de contenu SharePoint représente une catégorie de documents qui ont des caractéristiques communes et qui partagent une collection de colonnes ou de propriétés de métadonnées pour ce contenu particulier. Les types de contenu SharePoint sont gérés via la [Galerie de types de contenu](https://support.microsoft.com/office/create-or-customize-a-site-content-type-27eb6551-9867-4201-a819-620c5658a60f). Pour cet exemple, lorsque vous créez le modèle, vous créez un nouveau type de contenu de *renouvellement de contrat* .

Sélectionnez **Paramètres avancés** si vous souhaitez mapper ce modèle à un type de contenu existant dans la Galerie de types de contenu SharePoint pour utiliser son schéma. Notez que si vous pouvez utiliser un type de contenu existant pour tirer parti de son schéma afin de faciliter l’identification et la classification, vous devez tout de même former votre modèle pour extraire des informations des fichiers qu’il identifie.</br>

![Paramètres avancés](../media/content-understanding/advanced-settings.png)

## <a name="add-your-example-files"></a>Ajouter vos exemples de fichiers

Sur la page d’accueil du modèle, ajoutez vos exemples de fichiers dont vous aurez besoin pour former le modèle afin d’identifier votre type de document. </br>
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4D0iX] 

</br>

> [!NOTE]
> Vous devez utiliser les mêmes fichiers pour la formation des classifieurs et de l' [extracteur](create-an-extractor.md). Vous avez toujours la possibilité de l’ajouter plus tard, mais vous ajoutez généralement un ensemble complet de fichiers d’exemple. Étiquetez une partie pour former votre modèle et testez les autres pour évaluer la pertinence du modèle. 

Pour votre jeu de formation, vous voulez utiliser des exemples positifs et négatifs :
- Exemple positif : documents qui représentent le type de document. Elles contiennent des chaînes et des informations qui seraient toujours dans ce type de document.
- Exemple négatif : documents qui ne représentent pas le type de document. Il manque des chaînes et des informations qui doivent être présentes dans ce type de document.

Veillez à utiliser au moins cinq exemples positifs et au moins un exemple négatif pour former votre modèle.  Vous souhaitez en créer d’autres pour tester votre modèle après le processus de formation.

Pour ajouter des fichiers d’exemple :

1. À partir de la page d’accueil du modèle, dans la vignette **créer un exemple de bibliothèque** , cliquez sur Ajouter des **fichiers**.
2. Sur la page **Sélectionner des fichiers d’exemple pour votre modèle** , sélectionnez vos exemples de fichiers dans la bibliothèque fichiers d’exemple dans le centre de contenu. Si vous ne les avez pas déjà téléchargées, choisissez de les télécharger maintenant en cliquant sur **charger** pour les déplacer dans l’exemple de bibliothèque de fichiers.
3. Après avoir sélectionné vos exemples de fichiers à utiliser pour former le modèle, cliquez sur **Ajouter**.

    ![Sélectionner des exemples de fichiers](../media/content-understanding/select-sample.png) 

## <a name="label-your-example-files"></a>Étiqueter vos exemples de fichiers

Après avoir ajouté vos fichiers d’exemple, vous devez les étiqueter en tant qu’exemples positifs ou négatifs.

1. À partir de la page d’accueil du modèle, dans la vignette **classer les fichiers et exécuter la formation** , cliquez sur organiser le **classificateur**.
   Ceci affiche la page étiquette qui affiche la liste de vos exemples de fichiers, avec le premier fichier visible dans la visionneuse.
2. Dans la visionneuse en haut du premier fichier d’exemple, vous devriez voir un texte vous demandant si le fichier est un exemple de modèle que vous venez de créer. S’il s’agit d’un exemple positif, sélectionnez **Oui**. S’il s’agit d’un exemple négatif, sélectionnez **non**.
3. Dans la liste des **exemples étiquetés** à gauche, sélectionnez les fichiers supplémentaires que vous souhaitez utiliser comme exemples, puis étiquetez-les. 

    ![Page d’accueil du classifieur](../media/content-understanding/classifier-home-page.png) 


> [!NOTE]
> Étiquetez au moins cinq exemples positifs et un exemple négatif. 

## <a name="create-an-explanation"></a>Créer une explication

L’étape suivante consiste à créer une explication sur la page de formation. Une explication aide le modèle à comprendre comment reconnaître le document. Par exemple, les documents de renouvellement de contrat contiennent toujours une *demande de chaîne de texte de divulgation supplémentaire* .

> [!Note]
> Lorsqu’il est utilisé avec des extracteurs, une explication identifie la chaîne que vous souhaitez extraire du document. 

Pour créer une explication :

1. À partir de la page d’accueil du modèle, sélectionnez l’onglet **train (apprentissage** ) pour accéder à la page de formation.
2. Sur la page de formation, dans la section **fichiers formés** , vous devriez voir une liste des fichiers d’exemple que vous avez précédemment étiquetés. Sélectionnez un des fichiers positifs dans la liste et affichez-le dans la visionneuse.
3. Dans la section explication, sélectionnez **nouveau** , puis **vide**.
4. Sur la page **créer une explication** :</br>
    a. Tapez le **nom** (par exemple, « bloc de divulgation »).</br>
    b. Sélectionnez le **type**. Pour l’exemple, sélectionnez **liste des expressions**, étant donné que vous ajoutez une chaîne de texte.</br>
    c. Dans la zone **Tapez ici** , tapez la chaîne. Pour l’exemple, ajoutez « demande d’informations supplémentaires ». Vous **pouvez sélectionner respecter la casse si** la chaîne doit respecter la casse.</br>
    d. Cliquez sur **Enregistrer**.

    ![Créer une explication](../media/content-understanding/explanation.png) 
    
 
5. Le modèle vérifie désormais si l’explication que vous avez créée était suffisante pour identifier correctement les fichiers d’exemple étiquetés restants, comme des exemples positifs et négatifs. Dans la section fichiers formés, vérifiez la colonne **évaluation** une fois la formation terminée pour afficher les résultats. Les fichiers affichent une valeur de **correspondance**, si les explications que vous avez créées étaient suffisantes pour correspondre à ce que vous avez étiqueté positif ou négatif.

    ![Valeur de la correspondance](../media/content-understanding/match.png) 

Si vous recevez une **incompatibilité** sur les fichiers étiquetés, vous devrez peut-être créer une explication supplémentaire pour fournir au modèle plus d’informations afin d’identifier le type de document. Dans ce cas, cliquez sur le fichier pour obtenir plus d’informations sur la raison de l’incompatibilité.

## <a name="test-your-model"></a>Tester votre modèle

Si vous avez reçu une correspondance sur vos fichiers d’exemple étiquetés, vous pouvez maintenant tester votre modèle sur vos fichiers d’exemple sans étiquette restants.

1. À partir de la page d’accueil du modèle, sélectionnez l’onglet **test** .  Cela exécute le modèle sur vos fichiers d’exemple non labellisés.
2. Dans la liste des **fichiers test** , vos exemples de fichiers affichent et indiquent si le modèle a déterminé qu’il soit positif ou négatif. Utilisez ces informations pour vous aider à déterminer l’efficacité de votre classifieur lors de l’identification de vos documents.

    ![Test des fichiers non labellisés](../media/content-understanding/test-on-files.png) 

## <a name="see-also"></a>Voir aussi
[Créer un extracteur](create-an-extractor.md)</br>
[Présentation de l’explication des documents](document-understanding-overview.md)</br>
[Créer un modèle de traitement de formulaire](create-a-form-processing-model.md)</br>
[Appliquer un modèle](apply-a-model.md) 
