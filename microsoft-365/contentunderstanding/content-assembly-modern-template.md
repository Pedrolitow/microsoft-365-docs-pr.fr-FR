---
title: Créer un modèle moderne dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: anrasto, shrganguly
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez comment créer un modèle moderne dans Microsoft Syntex.
ms.openlocfilehash: b0056e9ebc5dfe69e99c40abaccaea0cd6725e39
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68566263"
---
# <a name="create-a-modern-template-in-microsoft-syntex"></a>Créer un modèle moderne dans Microsoft Syntex

## <a name="upload-a-document-to-create-a-modern-template"></a>Charger un document pour créer un modèle moderne

Suivez ces étapes pour créer un modèle moderne.

1. Dans une bibliothèque de documents SharePoint, sélectionnez **Créer** > **un modèle moderne**.

   ![Capture d’écran de la bibliothèque de documents avec l’option Créer un modèle moderne mise en évidence.](../media/content-understanding/content-assembly-create-template-1.png)

2. Sélectionnez un document Word à charger à partir de SharePoint ou OneDrive de votre organisation, ou à partir de votre stockage local.

   ![Capture d’écran de la page de chargement où vous sélectionnez un document.](../media/content-understanding/content-assembly-pick-a-file.png)

3. Une fois le document chargé, le document s’affiche dans le studio de modèles, où vous pouvez convertir le document en modèle en ajoutant des champs.

   ![Capture d’écran du document dans la visionneuse de modèles.](../media/content-understanding/content-assembly-create-template-3.png)

4. Dans le coin supérieur gauche du studio de modèles, sélectionnez le nom du modèle. Le nom par défaut est le nom du document utilisé pour créer le modèle. Si vous souhaitez renommer le modèle, sélectionnez le nom par défaut ou l’icône de crayon en regard du nom, tapez le nouveau nom, puis **sélectionnez Entrée**.

   ![Capture d’écran de la visionneuse de modèles montrant le nom du document à sélectionner pour renommer.](../media/content-understanding/content-assembly-create-template-3a.png)

<!---
5. Create placeholders for all dynamic text in the document that users might want to change from one document to another. For example, you might want to create a placeholder for input such as company name, client name, address, phone number, or date.

    To create a placeholder, select the text (such as the date). The **All placeholders** panel will open, where you'll give the placeholder a relevant name and choose the type of input you want to associate with the placeholder.
 
   ![Screenshot of the template viewer showing a field highlighted and the All placeholders panel.](../media/content-understanding/content-assembly-create-template-4b.png)

   Currently, there are three ways for users to fill in a placeholder:

   - [Enter text or select a date](#associate-a-placeholder-by-entering-text-or-selecting-a-date)
   - [Select from choices in a column of a list or library](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)
   - [Select from managed metadata term set or term](#associate-a-placeholder-by-selecting-from-managed-metadata-term-set-or-term)

   > [!NOTE]
   > You can create placeholders for text, and also placeholders for text within cells in a table. However, images, smart art, complete tables, and bulleted lists are currently not supported.   
--->

## <a name="associate-fields-with-different-data-sources"></a>Associer des champs à différentes sources de données

Vous pouvez associer des champs et des espaces réservés en :

- [Saisie de texte ou sélection d’une date](#associate-a-placeholder-by-entering-text-or-selecting-a-date)

- [Sélection parmi les choix dans une colonne d’une liste ou d’une bibliothèque](#associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library)

- [Sélection à partir d’un ensemble ou d’un terme de termes de métadonnées managées](#associate-a-placeholder-by-selecting-from-a-managed-metadata-term-set-or-term)

### <a name="associate-a-placeholder-by-entering-text-or-selecting-a-date"></a>Associer un espace réservé en entrant du texte ou en sélectionnant une date

Dans le panneau **Tous les espaces réservés** :

1. Dans le champ **Nom** , entrez un nom approprié pour l’espace réservé.

   ![Capture d’écran de la visionneuse de modèles montrant le panneau Tous les espaces réservés pour une entrée manuelle.](../media/content-understanding/content-assembly-create-template-5a.png)

2. Dans la **section Comment les auteurs remplissent cette section d’espace réservé** , **sélectionnez Entrée de texte ou sélectionnez une date**.

3. Dans le champ **Type d’informations** , sélectionnez le type de données que vous souhaitez associer à l’espace réservé. Actuellement, six options sont disponibles : **une seule ligne de texte**, **plusieurs lignes de texte**, **nombre**, **date et heure**, **Email** et **lien hypertexte**.

4. Sélectionnez **Ajouter**.

   > [!NOTE]
   > Vous pouvez configurer plusieurs formateurs de dates tels que MM/JJ/AAAA, JJ/MM/AAAA, AAAA/AAAA/MM/JJ et JJ du mois, y compris définir l’heure au format 12 heures et 24 heures. 

### <a name="associate-a-placeholder-by-selecting-from-choices-in-a-column-of-a-list-or-library"></a>Associer un espace réservé en sélectionnant parmi les choix dans une colonne d’une liste ou d’une bibliothèque

Dans le panneau **Tous les espaces réservés** :

1. Dans le champ **Nom** , entrez un nom approprié pour l’espace réservé.

   ![Capture d’écran de la visionneuse de modèles montrant le panneau Tous les espaces réservés pour l’entrée à partir d’une liste SharePoint.](../media/content-understanding/content-assembly-create-template-6a.png)

2. Dans la section **Comment les auteurs remplissent cette section d’espace réservé** , **choisissez Sélectionner parmi les choix dans une colonne d’une liste ou d’une bibliothèque**, puis **sélectionnez Sélectionner**.

3. Dans la **liste Sélectionner une liste pour ajouter une page de colonne source** , sélectionnez la liste que vous souhaitez utiliser, puis sélectionnez **Suivant**.

   ![Capture d’écran de la page Sélectionner une liste pour l’ajout d’une colonne source montrant des listes.](../media/content-understanding/content-assembly-create-template-7.png)

4. Dans la **page Sélectionner une colonne source à partir de la page de liste existante** , sélectionnez le nom de colonne que vous souhaitez associer à l’espace réservé, puis **sélectionnez Enregistrer**.

   ![Capture d’écran de la page Sélectionner une colonne source à partir de la page de liste existante montrant les noms des colonnes.](../media/content-understanding/content-assembly-create-template-8.png)

    Si vous souhaitez voir à nouveau la page d’origine des listes, sélectionnez **Le lien Atteindre (nom de la liste)** en bas de la liste.

5. Lorsque vous avez terminé, vous verrez que le champ de liste a été associé à l’espace réservé.

   ![Capture d’écran du panneau Tous les espaces réservés montrant le champ de liste associé à l’espace réservé.](../media/content-understanding/content-assembly-create-template-9.png)

6. Si vous souhaitez que les utilisateurs puissent ajouter des entrées manuellement, en plus de choisir dans une liste, sélectionnez **Autoriser les auteurs à ajouter de nouveaux choix**. Dans ce cas, la valeur par défaut du type de données d’entrée manuelle est *Une seule ligne de texte*. En outre, les valeurs entrées par les auteurs seront utilisées uniquement pour générer le document. Ils ne seront pas ajoutés à la liste SharePoint.

### <a name="associate-a-placeholder-by-selecting-from-a-managed-metadata-term-set-or-term"></a>Associer un espace réservé en sélectionnant à partir d’un ensemble de termes ou d’un terme de métadonnées managées

Dans le panneau **Tous les espaces réservés** :

1. Dans le champ **Nom** , entrez un nom approprié pour l’espace réservé.

   ![Capture d’écran de la visionneuse de modèles montrant le panneau Tous les espaces réservés pour l’entrée d’un ensemble de termes ou de termes.](../media/content-understanding/content-assembly-create-template-term.png)

2. Dans la section **Comment les auteurs remplissent cette section d’espace réservé** , **choisissez Sélectionner parmi un ensemble de termes ou un terme de métadonnées managés**, puis **sélectionnez Sélectionner**.

3. Dans la page **Sélectionner des ensembles de termes ou des termes** , recherchez ou sélectionnez l’ensemble de termes ou le terme à associer à l’espace réservé, puis **sélectionnez Enregistrer**.

   ![Capture d’écran de la page Sélectionner des ensembles de termes ou des termes.](../media/content-understanding/content-assembly-select-term.png)

4. Lorsque vous avez terminé, vous verrez que l’ensemble de termes sélectionné ou le terme a été associé à l’espace réservé. 

   ![Capture d’écran du panneau Tous les espaces réservés montrant l’ensemble de termes ou le terme associé.](../media/content-understanding/content-assembly-associated-term.png)

5. Si vous souhaitez que les utilisateurs puissent ajouter plusieurs valeurs correspondant à l’ensemble de termes ou au terme, sélectionnez **Autoriser plusieurs valeurs**. En outre, si l’ensemble de termes est configuré en tant qu’ensemble de termes ouvert, vous pouvez sélectionner **Autoriser les nouvelles valeurs**. Si vous activez cette option, les utilisateurs qui génèrent des documents à partir du modèle moderne peuvent ajouter de nouveaux termes à l’ensemble de termes et les ajouter en tant que valeurs d’espace réservé.

   > [!TIP]
   > Lorsque vous activez l’option **Autoriser les nouvelles valeurs** (uniquement autorisée pour les ensembles de termes ouverts), les utilisateurs sont plus susceptibles d’ajouter des termes redondants dans le magasin de termes. Les termes redondants peuvent compliquer la gestion d’un ensemble de termes par les administrateurs.

## <a name="save-a-modern-template-as-a-draft"></a>Enregistrer un modèle moderne en tant que brouillon

Vous pouvez créer autant de champs que vous le pensez nécessaire. Lorsque vous avez terminé, vous pouvez choisir d’enregistrer le modèle sous forme de brouillon.

1. Sélectionnez **Enregistrer le brouillon** pour enregistrer le modèle en tant que brouillon et vous y accéderez ultérieurement.

2. Pour afficher, modifier ou publier des brouillons enregistrés à partir du menu déroulant **Modèles brouillons** dans **les modèles modernes**, sélectionnez **Nouveau** > **menu Modifier nouveau** dans la bibliothèque de documents.

## <a name="publish-a-modern-template"></a>Publier un modèle moderne

Une fois que vous avez terminé d’ajouter tous les champs pertinents au modèle et que vous souhaitez le rendre disponible pour une utilisation par d’autres utilisateurs dans la bibliothèque de documents, vous pouvez publier le modèle.

1. Sélectionnez **Publier** pour publier le modèle à utiliser par d’autres utilisateurs de l’organisation pour créer des documents.

2. Pour afficher, modifier ou annuler la *publication* des modèles publiés dans le menu déroulant **Modèles publiés** de la section **Modèles modernes** , sélectionnez **Nouveau** > **menu Modifier nouveau** dans la bibliothèque de documents. 

## <a name="edit-a-modern-template"></a>Modifier un modèle moderne

Si vous devez modifier un modèle existant ou supprimer ou annuler la publication d’un modèle, procédez comme suit.

1. Dans une bibliothèque de documents SharePoint, sélectionnez **Nouveau** > **menu Modifier nouveau**.

   ![Capture d’écran de la bibliothèque de documents avec l’option Modifier le nouveau menu mise en évidence.](../media/content-understanding/content-assembly-edit-template-1.png)

2. Dans le panneau **Modifier un nouveau menu** , dans la section **Modèles modernes** , sélectionnez le modèle publié ou brouillon que vous souhaitez modifier.

   ![Capture d’écran du panneau Modifier le nouveau menu montrant la section Modèles modernes.](../media/content-understanding/content-assembly-edit-template-2.png)

3. Pour modifier un modèle publié ou un brouillon de modèle :

   - Pour **les modèles publiés**, **sélectionnez Modifier** pour ouvrir le studio de modèles dans lequel vous pouvez modifier le modèle publié. Vous pouvez également choisir de supprimer ou d’annuler la publication du modèle.

      ![Capture d’écran de la section Modèles modernes montrant les modèles publiés.](../media/content-understanding/content-assembly-edit-published.png)

   - Pour **les modèles Brouillon,** **sélectionnez Modifier** pour ouvrir le studio de modèles dans lequel vous pouvez modifier le modèle brouillon. Vous pouvez également choisir de supprimer ou de publier le modèle.

      ![Capture d’écran de la section Modèles modernes montrant les modèles brouillons.](../media/content-understanding/content-assembly-edit-draft.png)

> [!div class="nextstepaction"]
> [Étape suivante > Créer un document à partir d’un modèle moderne](content-assembly-create-document.md)