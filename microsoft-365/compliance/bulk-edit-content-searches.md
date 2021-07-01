---
title: Modification en bloc des recherches de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 12/29/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 39e4654a-9588-41f6-892b-c33ab57bfbe2
ms.custom:
- seo-marvel-apr2020
description: Utilisez l’Éditeur de recherche en bloc dans le centre de sécurité et conformité pour modifier rapidement les emplacements de requête et de contenu pour une ou plusieurs recherches de contenu.
ms.openlocfilehash: f6331bad19e95fd1d7039d5da72349906d3614b8
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53227386"
---
# <a name="bulk-edit-content-searches"></a>Modification en bloc des recherches de contenu

Vous pouvez utiliser l’Éditeur de recherche en bloc dans l’outil de recherche de contenu pour modifier plusieurs recherches en même temps. Cet outil vous permet de modifier rapidement les emplacements de requête et de contenu pour une ou plusieurs recherches. Vous pouvez ensuite réexécuter les recherches et obtenir de nouveaux résultats de recherche estimés pour les recherches révisées. L’éditeur vous permet également de copier et coller des requêtes et des emplacements de contenu à partir d Microsoft Excel fichier texte ou d’un fichier texte. Cela signifie que vous pouvez utiliser l’outil Statistiques de recherche pour afficher les statistiques d’une ou plusieurs recherches, exporter les statistiques dans un fichier CSV, où vous pouvez modifier les requêtes et les emplacements de contenu dans Excel. Ensuite, vous utilisez l’Éditeur de recherche en bloc pour ajouter les requêtes révisées et les emplacements de contenu aux recherches. Après avoir révisé une ou plusieurs recherches, vous pouvez les redémarrer et obtenir de nouveaux résultats de recherche estimés.

Pour plus d’informations sur l’utilisation de l’outil Statistiques de recherche, voir Afficher les statistiques de mot clé [pour les résultats de recherche de contenu.](view-keyword-statistics-for-content-search.md)

## <a name="use-the-bulk-search-editor-to-change-queries"></a>Utiliser l’Éditeur de recherche en bloc pour modifier les requêtes

1. Go <https://protection.office.com> to, and then select **Search** \> **Content search**.

2. Dans la liste des recherches, sélectionnez une ou  plusieurs recherches, puis sélectionnez le bouton Éditeur de recherche en bloc Éditeur de ![ recherche en ](../media/1ddb3d18-2f00-4a7b-98a6-817ca5ec7014.png) bloc.

    ![Sélectionnez une ou plusieurs recherches, puis sélectionnez Éditeur de recherche en bloc](../media/600c9716-89a2-4451-b111-fa7cfaad2006.png)

    Les informations suivantes s’affichent sur la page **Requêtes** de l’Éditeur de recherche en bloc.

    ![La page Éditeur de recherche en bloc affiche les requêtes pour les recherches sélectionnées](../media/189659af-cc78-4479-b0bc-a93decad2f6c.png)

    a. La **colonne Recherche** affiche le nom de la recherche de contenu. Comme indiqué précédemment, vous pouvez modifier la requête pour plusieurs recherches.

    b. La **colonne Requête** affiche la requête pour la recherche de contenu répertoriée dans la **colonne** Recherche. Si la requête a été créée à l’aide de la fonctionnalité de liste de mots clés, les mots clés sont séparés par le texte **`(c:s)`** . Cela indique que les mots clés sont connectés par **l’opérateur OR.** En outre, si la requête inclut des conditions, les mots clés et les conditions sont séparés par le texte **`(c:c)`** . Cela indique que les mots clés (ou phases de mots clés) sont connectés aux conditions par **l’opérateur AND.** Par exemple, dans la capture d’écran précédente, la requête KQL équivalente à la recherche ContosoSearch1 serait `customer (c:s) pricing(c:c)(date=2000-01-01..2016-09-30)`  `(customer OR pricing) AND (date=2002-01-01..2016-09-30)` .

3. Pour modifier une requête, sélectionnez dans la cellule de la requête que vous souhaitez modifier et en faisant l’une des choses suivantes. La cellule est encadrée d’une zone bleue lorsque vous la sélectionnez.

   - Tapez la nouvelle requête dans la cellule. Vous ne pouvez pas modifier une partie de la requête. Vous devez taper l’intégralité de la requête.

      Ou

   - Collez une nouvelle requête dans la cellule. Cela suppose que vous avez copié le texte de la requête à partir d’un fichier, tel qu’un fichier texte ou Excel fichier.

4. Une fois que vous avez modifié une ou plusieurs requêtes sur la **page** Requêtes, sélectionnez **Enregistrer**.

    La requête révisée s’affiche dans la colonne **Requête** pour la recherche sélectionnée.

5. Sélectionnez **Fermer** pour fermer l’Éditeur de recherche en bloc.

6. Dans la page **Recherche de** contenu, sélectionnez  la recherche que vous avez modifiée, puis sélectionnez Démarrer la recherche pour redémarrer la recherche à l’aide de la requête révisée.

Voici quelques conseils pour modifier des requêtes à l’aide de l’Éditeur de recherche en bloc :

- Copiez la requête existante (à l’aide **de Ctrl C)** dans un fichier texte. Modifiez la requête dans le fichier texte, puis copiez la requête révisée et collez-la (à l’aide de **Ctrl V**) dans la cellule de la page **Requêtes.**

- Vous pouvez également copier des requêtes à partir d’autres applications (telles que Microsoft Word ou Microsoft Excel). Toutefois, vous pouvez ajouter par inadvertance des caractères non pris en aide à une requête à l’aide de l’Éditeur de recherche en bloc. La meilleure façon d’éviter les caractères non pris en place consiste à taper simplement la requête dans une cellule de la page **Requêtes.** Vous pouvez également copier une requête à partir de Word ou Excel puis la coller dans un éditeur de texte simple, tel que Microsoft Bloc-notes. Enregistrez ensuite le fichier texte, puis sélectionnez **ANSI** dans la liste déroulante **Encodage**. Cette opération supprime les caractères de mise en forme et non pris en place. Vous pouvez ensuite copier et coller la requête à partir du fichier texte dans la page **Requêtes.**

## <a name="use-the-bulk-search-editor-to-change-content-locations"></a>Utiliser l’Éditeur de recherche en bloc pour modifier les emplacements de contenu

1. Dans l’Éditeur de recherche en bloc pour une ou plusieurs recherches  sélectionnées, sélectionnez Activer l’éditeur d’emplacements en **bloc,** puis sélectionnez le lien Emplacements qui s’affiche sur la page.

    Les informations suivantes s’affichent dans la page **Emplacements** de l’Éditeur de recherche en bloc.

    ![Sélectionnez Activer l’éditeur d’emplacements en bloc, puis sélectionnez Emplacements pour ajouter ou supprimer des emplacements de contenu](../media/a5a468ce-bd63-4c53-bc37-ff64cf769e59.png)

    a. **Boîtes aux lettres à rechercher** Cette section affiche une colonne pour chaque recherche de contenu sélectionnée et une ligne pour chaque boîte aux lettres incluse dans la recherche. Une coche indique que la boîte aux lettres est incluse dans la recherche. Vous pouvez ajouter des boîtes aux lettres à une recherche en tapant l’adresse de messagerie de la boîte aux lettres sur une ligne vide, puis en élecant la case à cocher pour la recherche de contenu à ajouter. Vous pouvez également supprimer une boîte aux lettres d’une recherche en ôtant la case à cocher.

    b. **SharePoint sites à rechercher** Cette section affiche une ligne pour chaque site SharePoint et OneDrive qui est inclus dans chaque recherche de contenu sélectionnée. Une coche indique que le site est inclus dans la recherche. Vous pouvez ajouter des sites à une recherche en tapant l’URL du site sur une ligne vide, puis en élecant la case à cocher pour la recherche de contenu à ajouter. Vous pouvez également supprimer un site d’une recherche en ôtant la case à cocher.

    c. **Autres options de recherche** Cette section indique si les éléments nonndex et les dossiers publics sont inclus dans la recherche. Pour les inclure, assurez-vous que la case à cocher est cocher. Pour les supprimer, cochez la case.

2. Après avoir modifié une ou plusieurs des sections de la page **Emplacements,** sélectionnez **Enregistrer.**

    Les emplacements de contenu révisés sont affichés dans la section appropriée pour les recherches sélectionnées.

3. Sélectionnez **Fermer** pour fermer l’Éditeur de recherche en bloc.

4. Dans la page **Recherche de** contenu, sélectionnez  la recherche que vous avez modifiée, puis sélectionnez Démarrer la recherche pour redémarrer la recherche à l’aide des emplacements de contenu révisés.

Voici quelques conseils pour modifier les emplacements de contenu à l’aide de l’Éditeur de recherche en bloc :

- Vous pouvez modifier les recherches de contenu pour effectuer des  recherches dans toutes  les boîtes aux lettres ou tous les sites de l’organisation en tapant Tout sur une ligne vide dans les boîtes aux lettres pour rechercher ou **SharePoint sites** à rechercher, puis en élecant la case à cocher.

- Vous pouvez ajouter plusieurs emplacements de contenu à une ou plusieurs recherches en copiant plusieurs lignes à partir d’un fichier texte ou d’un fichier Excel, puis en les coller dans une section de la page **Emplacements.** Après avoir ajouté de nouveaux emplacements, n’oubliez pas de cocher la case pour chaque recherche à ajouter à l’emplacement.

    > [!TIP]
    > Pour générer une liste d’adresses de messagerie pour tous les utilisateurs de votre organisation, exécutez la commande PowerShell à l’étape 2 de l’étape 2 : Générer une liste [d’utilisateurs.](search-the-mailbox-and-onedrive-for-business-for-a-list-of-users.md#step-2-generate-a-list-of-users) Vous pouvez également suivre les étapes de la procédure Obtenir la liste de toutes les URL OneDrive [utilisateurs](/onedrive/list-onedrive-urls) de votre organisation pour générer une liste de tous les sites OneDrive Entreprise de votre organisation. Notez que vous devez y appender l’URL du domaine Mon site de votre organisation (par exemple, aux sites OneDrive Entreprise créés par https://contoso-my.sharepoint.com) le script. Une fois que vous avez une liste d’adresses e-mail ou OneDrive Entreprise sites, vous pouvez les copier et les coller dans la **page** Emplacements dans l’Éditeur de recherche en bloc.

- Une fois que vous avez sélectionné **Enregistrer** pour enregistrer les modifications dans l’Éditeur de recherche en bloc, l’adresse de messagerie des boîtes aux lettres que vous avez ajoutées à une recherche est validée. Si l’adresse de messagerie n’existe pas, un message d’erreur s’affiche pour dire que la boîte aux lettres ne peut pas être localisée. Les URL des sites ne sont pas validées.
