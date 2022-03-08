---
title: Créer des documents à l’aide de l’assembly de contenu dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer automatiquement des documents et d’autres contenus à l’aide de l’assembly de contenu dans Microsoft SharePoint Syntex.
ms.openlocfilehash: f2e8c601e8a7242524cb323d099975f6600cce05
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318884"
---
# <a name="create-documents-using-content-assembly-in-microsoft-sharepoint-syntex"></a>Créer des documents à l’aide de l’assembly de contenu dans Microsoft SharePoint Syntex

Vous pouvez utiliser SharePoint Syntex pour vous aider à générer automatiquement des documents d’entreprise répétitifs standard, tels que des contrats, des déclarations de travail, des contrats de service, des lettres de consentement, des pas de vente et des correspondances. Vous pouvez faire tout cela plus rapidement, de manière plus cohérente et moins sujette aux erreurs à l’aide de l’assembly de contenu SharePoint Syntex.

Avec l’assembly de contenu, vous pouvez utiliser un document existant pour créer un modèle *moderne, puis* utiliser ce modèle pour générer automatiquement du contenu à l’aide de listes SharePoint ou d’entrées utilisateur en tant que source de données.

> [!NOTE]
> Vous devez être titulaire d’une licence SharePoint Syntex utilisateur pour accéder aux fonctionnalités d’assembly de contenu et les utiliser. Vous devez également avoir les autorisations pour gérer SharePoint listes.

## <a name="create-a-modern-template"></a>Créer un modèle moderne

Suivez ces étapes pour créer un modèle moderne.

1. Dans une bibliothèque de documents SharePoint, **sélectionnez Modèle** **moderne NewCreate** > . 
 
   ![Capture d’écran de la bibliothèque de documents avec l’option Créer un modèle moderne mise en évidence.](../media/content-understanding/content-assembly-create-template-1.png)

2. Choisissez un document Word existant que vous souhaitez utiliser comme base pour la création d’un modèle moderne, puis sélectionnez **Ouvrir**. 
 
   ![Capture d’écran de la page de téléchargement dans laquelle vous sélectionnez un document.](../media/content-understanding/content-assembly-create-template-2.png)

   > [!NOTE]
   > Actuellement, vous pouvez télécharger uniquement des documents Word (.docx extension) pour créer des modèles. Télécharger documents Word à partir de votre stockage local ou de votre bureau.

3. Une fois que vous avez téléchargé le document, celui-ci s’affiche dans l’atelier de modèles où vous pouvez convertir le document en modèle.
 
   ![Capture d’écran du document dans la visionneuse de modèles.](../media/content-understanding/content-assembly-create-template-3.png)

4. Dans le coin supérieur gauche du studio de modèles, sélectionnez le nom du modèle. Le nom par défaut est le nom du document utilisé pour créer le modèle. Si vous souhaitez renommer le modèle, sélectionnez le nom par défaut ou l’icône de crayon à côté du nom, tapez le nouveau nom, puis sélectionnez **Entrée**.
 
   ![Capture d’écran de la visionneuse de modèles affichant le nom du document à renommer.](../media/content-understanding/content-assembly-create-template-3a.png)

5. Créez des espaces réservé pour tout le texte dynamique du document que les utilisateurs peuvent vouloir modifier d’un document à l’autre. Par exemple, vous pouvez créer un espace réservé pour une entrée telle que le nom de la société, le nom du client, l’adresse, le numéro de téléphone ou la date.

    Pour créer un espace réservé, sélectionnez le texte (par exemple, la date). Le **panneau Tous les espaces** réservé s’ouvre, où vous donnez à l’espace réservé un nom pertinent et choisissez le type d’entrée que vous souhaitez associer à l’espace réservé.
 
   ![Capture d’écran de la visionneuse de modèles affichant un champ mis en surbrillant et le panneau Tous les espaces réservé.](../media/content-understanding/content-assembly-create-template-4a.png)

   Actuellement, il existe deux façons pour les utilisateurs de remplir un espace réservé :

   - [Entrer du texte ou sélectionner une date](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Sélection parmi les choix dans une colonne d’une liste ou d’une bibliothèque](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Associer un espace réservé en entrant du texte ou en sélectionnant une date 

Dans le **panneau Tous les espaces réservé** :

1. Dans le **champ** Nom, entrez un nom pertinent pour l’espace réservé.

   ![Capture d’écran de la visionneuse de modèles affichant le panneau Tous les espaces réservé pour une entrée manuelle.](../media/content-understanding/content-assembly-create-template-5.png)

2. Dans la section **Comment les auteurs remplissent cet espace réservé** , sélectionnez **Entrer du texte ou une date**.

3. Dans le **champ Type d’informations** , sélectionnez le type de données que vous souhaitez associer à l’espace réservé. Actuellement, six options sont **disponibles : Une** seule ligne de **texte, Plusieurs** lignes de texte, **Nombre**, **Date** et heure, **Courrier** électronique et **Lien hypertexte**.

4. Sélectionnez **Ajouter**.

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Associer un espace réservé en sélectionnant dans les choix d’une colonne d’une liste ou d’une bibliothèque

Dans le **panneau Tous les espaces réservé** :

1. Dans le **champ** Nom, entrez un nom pertinent pour l’espace réservé.

   ![Capture d’écran de la visionneuse de modèles affichant le panneau Tous les espaces réservé pour une entrée à partir d SharePoint liste.](../media/content-understanding/content-assembly-create-template-6.png)

2. In the **How authors fill in this placeholder** section, choose **Select from choices in a column of a list or library**, and then choose **Select**.

3. Dans la page **Sélectionner une liste pour ajouter** une colonne source, sélectionnez la liste que vous souhaitez utiliser, puis sélectionnez **Suivant**.

   ![Capture d’écran de la page Sélectionner une liste pour ajouter une colonne source affichant des listes.](../media/content-understanding/content-assembly-create-template-7.png)

4. Dans la page Sélectionner une **colonne source** dans la liste existante, sélectionnez le nom de colonne à associer à l’espace réservé, puis sélectionnez **Enregistrer**. 

   ![Capture d’écran de la colonne Sélectionner une source dans la page de liste existante affichant les noms des colonnes.](../media/content-understanding/content-assembly-create-template-8.png)

    Si vous souhaitez voir à nouveau la page d’origine des listes, sélectionnez Le **lien Go to (list name)** en bas de la liste.

5. Lorsque vous avez terminé, vous verrez que le champ de liste a été associé à l’espace réservé.

   ![Capture d’écran du panneau Tous les espaces réservé affichant le champ de liste associé à l’espace réservé.](../media/content-understanding/content-assembly-create-template-9.png)

6. Si vous souhaitez que les utilisateurs puissent ajouter des entrées manuellement, en plus de choisir dans une liste, sélectionnez Autoriser les auteurs à **ajouter de nouveaux choix**. Dans ce cas, la valeur par défaut du type de données d’entrée manuelle est *Une seule ligne de texte*. En outre, les valeurs entrées par les auteurs ne seront utilisées que pour générer le document. Ils ne seront pas ajoutés à la SharePoint liste.
 
Vous pouvez créer autant d’espaces que nécessaire. Lorsque vous avez terminé, vous pouvez choisir d’enregistrer le modèle en tant que brouillon ou de publier le modèle.

   - **Enregistrer le brouillon** : enregistre le modèle en tant que brouillon et vous pouvez y accéder ultérieurement. Vous pouvez afficher, modifier ou publier des brouillons enregistrés à partir de la section **Modèles** modernes en sélectionnant le **menu NewEdit**  >  New dans la bibliothèque de documents. 
   - **Publier** : publie le modèle à utiliser par d’autres utilisateurs de l’organisation pour créer des documents. Vous pouvez afficher, modifier ou dépublier *des* modèles publiés à partir de la section **Modèles** modernes en sélectionnant le **menu NewEdit**  >  New dans la bibliothèque de documents. 

## <a name="edit-a-modern-template"></a>Modifier un modèle moderne

Si vous devez modifier un modèle existant ou supprimer ou supprimer un modèle, suivez ces étapes.

1. Dans une bibliothèque de documents SharePoint, **sélectionnez Le** >  **menu Nouveau.** 
 
   ![Capture d’écran de la bibliothèque de documents avec l’option Modifier le nouveau menu mise en évidence.](../media/content-understanding/content-assembly-edit-template-1.png)

2. Dans le **volet Modifier le nouveau menu** , dans la section **Modèles** modernes, sélectionnez le modèle publié ou brouillon à modifier.
 
   ![Capture d’écran du panneau De menu Modifier nouveau affichant la section Modèles modernes.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Pour modifier un modèle publié ou un modèle de brouillon :

   - Pour **les modèles publiés**,  **selectEditto**  ouvrez le studio de modèles dans lequel vous pouvez modifier le modèle publié. Vous pouvez également choisir de supprimer ou de supprimer laublish du modèle. 
 
      ![Capture d’écran de la section Modèles modernes affichant les modèles publiés.](../media/content-understanding/content-assembly-edit-published.png)

   - Pour **les modèles provisoires**,  **selectEditto**  ouvrez le studio de modèles dans lequel vous pouvez modifier le modèle de brouillon. Vous pouvez également choisir de supprimer ou de publier le modèle.
 
      ![Capture d’écran de la section Modèles modernes affichant les modèles provisoires.](../media/content-understanding/content-assembly-edit-draft.png)

## <a name="create-a-document-from-a-modern-template"></a>Créer un document à partir d’un modèle moderne

Vous pouvez utiliser un modèle *moderne publié* pour créer rapidement des documents similaires sans avoir à démarrer à partir de zéro. Pour créer un document à l’aide d’un modèle publié, suivez les étapes suivantes :

1. Dans une bibliothèque de documents SharePoint, sélectionnez **Nouveau**, puis sélectionnez le modèle moderne que vous souhaitez utiliser.
 
   ![Capture d’écran de la bibliothèque de documents montrant les choix de modèles modernes dans le menu Nouveau.](../media/content-understanding/content-assembly-create-document-1.png)

2. Le modèle s’ouvre dans le studio de modèles.

3. Dans le **panneau Créer un document à partir d’un** modèle, entrez les informations, puis **sélectionnez Créer un document**.

   ![Capture d’écran de la bibliothèque de documents montrant créer un document à partir d’un panneau de modèles.](../media/content-understanding/content-assembly-create-document-2.png)

   Pour réduire le temps et les efforts nécessaires au remplissage des valeurs pour les espaces SharePoint Syntex fournit les informations SharePoint Syntex :

      - Suggestions pour vous aider à sélectionner facilement des valeurs lors de la sélection de valeurs dans une liste.
      - Valeurs d’espace réservé de remplissage automatique si vous êtes en mesure d’identifier de manière unique un enregistrement pour les espaces réservé associés à la même liste.

> [!NOTE]
> - Actuellement, seuls Microsoft Word documents (.docx extension) sont pris en charge pour la création d’un modèle. Avant de télécharger le document, assurez-vous que le suivi des modifications n’est **pas activé ou** que les commentaires ne sont pas activés sur le document Word. Si votre document contient des espaces de texte pour les images, assurez-vous qu’ils ne sont pas wrapped texte. Pour le moment, les **contrôles de** contenu ne sont pas en charge dans Word. Si vous souhaitez créer un modèle à partir d’un document Word avec des contrôles de contenu, supprimez-les avant de créer un modèle moderne.
>- Le modèle et le document sont associés à une bibliothèque de documents. Pour utiliser le modèle dans une autre bibliothèque de documents, vous devez le créer à nouveau dans cette bibliothèque de documents.
>- Le document téléchargé utilisé pour créer le modèle moderne sera enregistré en tant que copie distincte et placé dans le répertoire /forms de la bibliothèque de documents. Le fichier d’origine sur le disque n’est pas affecté.
>- Vous pouvez créer des espaces réservé uniquement pour le texte. Actuellement, les images, les images intelligentes, les tableaux et les listes à puces ne sont pas pris en charge.
>- Une fois qu’un document est créé à partir d’un modèle, il n’est pas associé au modèle.



 
