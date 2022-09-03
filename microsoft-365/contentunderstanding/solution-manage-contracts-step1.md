---
title: Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Découvrez comment utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données à l’aide d’une solution Microsoft 365.
ms.openlocfilehash: 115c1e3fbcd18bcc766132afaff308d25cf989fe
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67582491"
---
# <a name="step-1-use-sharepoint-syntex-to-identify-contract-files-and-extract-data"></a>Étape 1. Utiliser SharePoint Syntex pour identifier les fichiers de contrat et extraire des données

Votre organisation a besoin d’un moyen d’identifier et de classer tous les documents de contrat à partir des nombreux fichiers que vous recevez. Vous souhaitez également être en mesure d’afficher rapidement plusieurs éléments clés dans chacun des fichiers de contrat identifiés (par exemple, *client*, *entrepreneur* et *montant des frais*). Pour ce faire, vous pouvez utiliser [SharePoint Syntex](index.md) pour créer un modèle de compréhension de document et l’appliquer à une bibliothèque de documents.

## <a name="overview-of-the-process"></a>Vue d’ensemble du processus

[La compréhension](document-understanding-overview.md) des documents utilise des modèles d’intelligence artificielle (IA) pour automatiser la classification des fichiers et l’extraction des informations. Les modèles de compréhension des documents sont également optimaux dans l’extraction d’informations à partir de documents non structurés et semi-structurés où les informations dont vous avez besoin ne sont pas contenues dans des tables ou des formulaires, tels que des contrats. 

Les modèles de compréhension des documents utilisent la technologie OCR (Optical Character Recognition) pour analyser les fichiers PDF, images et TIFF, à la fois lorsque vous entraînez un modèle avec des exemples de fichiers et lorsque vous l’exécutez sur des fichiers dans une bibliothèque de documents.

1. Tout d’abord, vous devez trouver au moins cinq exemples de fichiers que vous pouvez utiliser pour « entraîner » le modèle afin de rechercher des caractéristiques spécifiques au type de contenu que vous essayez d’identifier (un contrat). 

2. À l’aide de SharePoint Syntex, créez un modèle de compréhension de document. À l’aide de vos exemples de fichiers, vous devez [créer un classifieur](create-a-classifier.md). En formant le classifieur avec vos exemples de fichiers, vous lui apprenez à rechercher des caractéristiques spécifiques à ce que vous verriez dans les contrats de votre entreprise. Par exemple, [créez une « explication »](create-a-classifier.md#create-an-explanation) qui recherche des chaînes spécifiques dans vos contrats, telles que le *Contrat de service*, les *Conditions d’accord* et la *Compensation*. Vous pouvez même entraîner votre explication à rechercher ces chaînes dans des sections spécifiques du document, ou à côté d’autres chaînes. Lorsque vous pensez avoir formé votre classifieur avec les informations dont il a besoin, vous pouvez tester votre modèle sur un exemple d’exemple de fichiers pour voir à quel point il est efficace. Après le test, si nécessaire, vous pouvez choisir d’apporter des modifications à vos explications pour les rendre plus efficaces. 

3. Dans votre modèle, vous pouvez [créer un extracteur](create-an-extractor.md) pour extraire des éléments de données spécifiques de chaque contrat. Par exemple, pour chaque contrat, les informations qui vous préoccupent le plus sont qui est le client, le nom de l’entrepreneur et le coût total.

4. Une fois que vous avez créé votre modèle, [appliquez-le à une bibliothèque de documents SharePoint](apply-a-model.md). Lorsque vous chargez des documents dans la bibliothèque de documents, votre modèle de compréhension des documents s’exécute et identifie et classifie tous les fichiers qui correspondent au type de contenu des contrats que vous avez défini dans votre modèle. Tous les fichiers classés en tant que contrats s’affichent dans une vue de bibliothèque personnalisée. Les fichiers affichent également les valeurs de chaque contrat que vous avez défini dans votre extracteur.

   ![Contrats dans la bibliothèque de documents.](../media/content-understanding/doc-lib-solution.png)

5. Si vous avez des exigences de rétention ou de sécurité pour vos contrats, vous pouvez également utiliser votre modèle pour appliquer une [étiquette de rétention](apply-a-retention-label-to-a-model.md) ou une [étiquette de confidentialité](apply-a-sensitivity-label-to-a-model.md) qui empêchera la suppression de vos contrats pendant une période donnée ou pour restreindre l’accès aux contrats.

## <a name="steps-to-create-and-train-your-model"></a>Étapes de création et d’apprentissage de votre modèle

> [!NOTE]
> Pour ces étapes, vous pouvez utiliser les exemples de fichiers dans le [référentiel des ressources de la solution de gestion des contrats](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management). Les exemples de ce référentiel contiennent à la fois les fichiers de modèle de compréhension de document et les fichiers utilisés pour entraîner le modèle.

### <a name="create-a-contract-model"></a>Créer un modèle de contrat

La première étape consiste à créer votre modèle de contrat.

1. Dans le centre de contenu, sélectionnez **Nouveau**, puis **Créer un modèle**.

2. Dans le volet **Nouveau modèle de compréhension de document** , dans le champ **Nom** , tapez le nom du modèle. Pour cette solution de gestion des contrats, vous pouvez nommer le modèle *Contrat*.

4. Sélectionnez **Créer**. Cette opération permet de créer une page d’accueil pour le modèle.</br>

    ![Capture d’écran de la page d’accueil du contrat.](../media/content-understanding/models-contract-home-page.png)


### <a name="train-your-model-to-classify-a-type-of-file"></a>Entraîner votre modèle pour classifier un type de fichier

#### <a name="add-example-files-for-your-model"></a>Ajouter des exemples de fichiers pour votre modèle

Vous devez ajouter au moins cinq exemples de fichiers qui sont des documents de contrat, et un exemple de fichier qui n’est pas un document de contrat (par exemple, une instruction de travail). 

1. Dans la page **Modèles > Contrat**, sous **Actions** >  clés **Ajouter des exemples de fichiers**, sélectionnez **Ajouter des fichiers**.

   ![Capture d’écran montrant la page Contrats avec l’option Ajouter des exemples de fichiers mise en évidence.](../media/content-understanding/key-actions-add-example-files.png)

2. Dans la page **Sélectionner des exemples de fichiers pour votre** modèle, ouvrez le dossier Contrat, sélectionnez les fichiers que vous souhaitez utiliser, puis sélectionnez **Ajouter**. Si vous n’avez pas d’exemples de fichiers, **sélectionnez Charger** pour les ajouter.

#### <a name="label-the-files-as-positive-or-negative-examples"></a>Étiqueter les fichiers en tant qu’exemples positifs ou négatifs

1. Dans la page **Modèles > Contrat**, sous **Actions** >  clés **Classifier les fichiers et exécuter l’entraînement**, sélectionnez **Former le classifieur**.

   ![Capture d’écran montrant la page Contrats avec l’option Classifier les fichiers et exécuter l’entraînement mise en évidence.](../media/content-understanding/key-actions-classify-files.png)

2. Dans la page **Models > Contract > Contract classifieur** , dans la visionneuse située en haut du premier exemple de fichier, vous verrez du texte vous demandant si le fichier est un exemple du modèle contrat que vous avez créé. Si cet exemple est positif, sélectionnez **Oui**. Si cet exemple est négatif, sélectionnez **Non**.

3. Dans la liste **des exemples étiquetés** à gauche, sélectionnez d’autres fichiers que vous souhaitez utiliser comme exemples, puis étiquetez-les. 

    ![Page d’accueil du classifieur.](../media/content-understanding/models-contract-classifier.png) 

#### <a name="add-at-least-one-explanation-to-train-the-classifier"></a>Ajouter au moins une explication pour entraîner le classifieur 

1. Dans la page **Model > Contract > Contract classifier** , sélectionnez l’onglet **Entraîner** .

2. Dans la section **Fichiers entraînés** , vous verrez une liste des exemples de fichiers que vous avez précédemment étiquetés. Sélectionnez l’un des fichiers positifs dans la liste pour l’afficher dans la visionneuse.

3. Dans la section **Explications** , sélectionnez **Nouveau** , puis **Vide**.

4. À la page **Créer une explication** :

    a. Dans le champ **Nom** , tapez le nom de l’explication (par exemple, « Contrat »).

    b. Dans le champ **Type d’explication** , sélectionnez **Liste d’expressions**, car vous ajoutez une chaîne de texte.

    c. Dans la **zone de liste d’expressions** , tapez la chaîne (par exemple, « AGREEMENT »). Vous pouvez sélectionner **Respect** de la casse si la chaîne doit respecter la casse.

    d. Sélectionnez **Enregistrer et entraîner**.

    ![Capture d’écran du panneau Créer une explication.](../media/content-understanding/contract-classifier-create-explanation.png) 

#### <a name="test-your-model"></a>Tester votre modèle

Vous pouvez tester votre modèle Contract sur des exemples de fichiers qu’il n’a pas vus auparavant. Cela est facultatif, mais il peut s’agir d’une bonne pratique utile.

1. Dans la page **Model > Contract > Contract classifier** , sélectionnez l’onglet **Test** . Cela exécute le modèle sur vos exemples de fichiers sans étiquette.

2. Dans la liste **Fichiers de test** , vos exemples de fichiers s’affichent et indiquent si le modèle les a prédits comme positifs ou négatifs. Utilisez ces informations pour déterminer plus facilement l’efficacité de votre classifieur lors de l’identification de vos documents.

    ![Capture d’écran des fichiers sans étiquette dans la liste Fichiers texte.](../media/content-understanding/test-on-files.png) 

3. Lorsque vous avez terminé, **sélectionnez Quitter l’entraînement**.

### <a name="create-and-train-an-extractor"></a>Créer et entraîner un extracteur

1. Dans la page **Modèles > Contrat**, sous **Actions** >  clés **Créer et entraîner des extracteurs**, **sélectionnez Créer un extracteur**.

   ![Capture d’écran montrant la page Contrats avec l’option Créer et entraîner des extracteurs mise en évidence.](../media/content-understanding/key-actions-create-extractors.png)

2. Dans le panneau **Nouvel extracteur d’entité** , dans le champ **Nouveau nom** , tapez le nom de votre extracteur. Par exemple, nommez-le *Client* si vous souhaitez extraire le nom du client de chaque contrat.

3. Lorsque vous avez terminé, sélectionnez **Créer**.

#### <a name="label-the-entity-you-want-to-extract"></a>Étiqueter l’entité à extraire

Lorsque vous créez l’extracteur, la page de l’extracteur s’ouvre. Cette page affiche la liste des fichiers échantillons, le premier fichier de la liste étant affiché dans la visionneuse.

![Capture d’écran de la page Exemples étiquetés de l’extracteur client.](../media/content-understanding/client-extractor-labeled-examples.png) 

Pour étiqueter l’entité :

1. Dans la visionneuse, sélectionnez les données à extraire des fichiers. Par exemple, si vous souhaitez extraire le *client*, vous mettez en surbrillance la valeur du client dans le premier fichier (dans cet exemple, *Best For You Organics*), puis **sélectionnez Enregistrer**. La valeur s’affiche à partir du fichier dans la liste **des exemples étiquetés** , sous la colonne **Étiquette** .

2. Sélectionnez **Fichier suivant** pour l’enregistrement automatique et ouvrez le fichier suivant dans la liste de la visionneuse. Vous pouvez également sélectionner **Enregistrer**, puis sélectionner un autre fichier dans la liste **des exemples étiquetés** .

3. Dans la visionneuse, répétez les étapes 1 et 2, puis répétez jusqu’à ce que vous enregistrez l’étiquette dans tous les fichiers.

Une fois que vous avez étiqueté les fichiers, une bannière de notification s’affiche pour vous informer de passer à l’entraînement. Vous pouvez choisir d’étiqueter d’autres documents ou de passer à l’entraînement.

#### <a name="add-an-explanation"></a>Ajouter une explication

Vous pouvez créer une explication qui fournit un indicateur sur le format d’entité lui-même et les variantes qu’il peut avoir dans les exemples de fichiers. Par exemple, une valeur de date peut être dans de nombreux formats différents, par exemple :

- 14/10/2019
- 14 octobre 2019
- Lundi 14 octobre 2019

Pour identifier la *date de début du contrat*, vous pouvez créer une explication.

1. Dans la section **Explications** , sélectionnez **Nouveau** , puis **Vide**.

2. À la page **Créer une explication** :

    a. Dans le champ **Nom** , tapez le nom de l’explication (par exemple *, Date*).

    b. Dans le champ **Type d’explication** , sélectionnez **Liste d’expressions**.

    c. Dans le champ **Valeur** , indiquez la variation de date tel qu’ils apparaissent dans les exemples de fichiers. Par exemple, si certaines dates apparaissent au format 0/00/0000, vous devez entrer les variations qui apparaissent dans vos documents, par exemple :

    - 0/0/0000
    - 0/00/0000
    - 00/0/0000
    - 00/00/0000

4. Sélectionnez **Enregistrer et entraîner**.

#### <a name="test-your-model-again"></a>Tester à nouveau votre modèle

Vous pouvez tester votre modèle Contract sur des exemples de fichiers qu’il n’a pas vus auparavant. Cela est facultatif, mais il peut s’agir d’une bonne pratique utile.

1. Dans la page **Model > Contract > Contract classifier** , sélectionnez l’onglet **Test** . Cela exécute le modèle sur vos exemples de fichiers sans étiquette.

2. Dans la liste **des fichiers de** test, vos exemples de fichiers s’affichent et indiquent si le modèle est en mesure d’extraire les informations dont vous avez besoin. Utilisez ces informations pour déterminer plus facilement l’efficacité de votre classifieur lors de l’identification de vos documents.

3. Lorsque vous avez terminé, **sélectionnez Quitter l’entraînement**.

### <a name="apply-your-model-to-a-document-library"></a>Appliquer votre modèle à une bibliothèque de documents

Pour appliquer votre modèle à une bibliothèque de documents SharePoint :

1. Dans la page **Modèles > Contrat**, sous **Actions** >  clés **Appliquer le modèle aux bibliothèques**, **sélectionnez Appliquer le modèle**.

   ![Capture d’écran montrant la page Contrats avec l’option Appliquer le modèle aux bibliothèques mise en évidence.](../media/content-understanding/key-actions-apply-model.png)

2. Dans le panneau **Ajouter un contrat** , sélectionnez le site SharePoint qui contient la bibliothèque de documents à laquelle vous souhaitez appliquer le modèle. Si le site n’apparaît pas dans la liste, utilisez la zone de recherche pour le trouver. Sélectionnez **Ajouter**.

    > [!NOTE]
    > Vous devez disposer d’autorisations *Gérer la liste* ou de droits *Modifier* sur la bibliothèque de documents à laquelle vous appliquez le modèle.

3. Après avoir sélectionné le site, sélectionnez la bibliothèque de documents à laquelle vous souhaitez appliquer le modèle.

4. Étant donné que le modèle est associé à un type de contenu, lorsque vous l’appliquez à la bibliothèque, il ajoute le type de contenu et son affichage avec les étiquettes que vous avez extraites en tant que colonnes. Cet affichage est l’affichage par défaut de la bibliothèque, mais vous pouvez éventuellement choisir de ne pas l’avoir comme affichage par défaut en sélectionnant **Paramètres avancés** et en désactivant la case à cocher **Définir cette nouvelle vue par défaut** .

5. Sélectionnez **Ajouter** pour appliquer le modèle à la bibliothèque.

6. Dans la page **Modèles > Contrat** , dans la section **Bibliothèques avec ce modèle** , vous verrez l’URL du site SharePoint répertoriée.

    ![Capture d’écran de la page d’accueil contrat montrant les bibliothèques avec cette section de modèle.](../media/content-understanding/contract-libraries-with-this-model.png)

7. Sous **Paramètres des paramètres** > **de la bibliothèque** :

   - Ajoutez une colonne nommée **État** et **sélectionnez Choix** comme type de colonne.
   - Appliquez les valeurs **In review**, **Approved** et **Rejected** .

Après avoir appliqué le modèle à la bibliothèque de documents, vous pouvez commencer à charger des documents sur le site et voir les résultats.

## <a name="next-step"></a>Étape suivante

[Étape 2. Utiliser Microsoft Teams pour créer votre canal de gestion des contrats](solution-manage-contracts-step2.md)
