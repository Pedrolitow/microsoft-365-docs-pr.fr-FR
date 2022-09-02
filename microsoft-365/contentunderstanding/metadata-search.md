---
title: Rechercher des métadonnées dans les bibliothèques de documents dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: kkameth
audience: admin
ms.topic: article
ms.service: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: high
description: Découvrez comment utiliser la recherche avancée de métadonnées et la recherche de colonnes de site personnalisées pour rechercher des éléments dans des bibliothèques de documents SharePoint à l’aide SharePoint Syntex.
ms.openlocfilehash: db13be1ce22becc10d04bf7e18becc9208784844
ms.sourcegitcommit: 62368e5a48e569c8e475b07d194d7d8ff7d167ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67560172"
---
# <a name="search-for-metadata-in-document-libraries-in-microsoft-sharepoint-syntex"></a>Rechercher des métadonnées dans les bibliothèques de documents dans Microsoft SharePoint Syntex

La fonctionnalité de recherche avancée de métadonnées SharePoint Syntex vous permet d’effectuer des requêtes spécifiques basées sur des métadonnées sur SharePoint bibliothèques de documents. Vous pouvez effectuer des requêtes plus rapides et plus précises basées sur des valeurs de colonne de métadonnées spécifiques, plutôt que de simplement rechercher des mots clés.

La recherche avancée de métadonnées vous permet d’utiliser les métadonnées associées à un document pour vous aider à localiser le fichier dans SharePoint bibliothèque de documents. Cette fonctionnalité est particulièrement utile lorsque vous avez des informations spécifiques à rechercher, comme la dernière modification d’un document, une personne spécifique associée à un fichier ou un type de fichier spécifique.

> [!NOTE]
> Cette fonctionnalité est disponible uniquement pour les utilisateurs titulaires d’une licence SharePoint Syntex. 

## <a name="to-use-advanced-metadata-search"></a>Pour utiliser la recherche avancée de métadonnées

1. À partir d’une bibliothèque de documents SharePoint, dans la zone **Rechercher dans cette bibliothèque**, sélectionnez l’icône de recherche de métadonnées (![Capture d’écran de l’icône de recherche de métadonnées.](../media/content-understanding/metadata-search-icon.png)).

    ![Capture d’écran d’une page de bibliothèque de documents affichant la zone de recherche avec l’icône de recherche de métadonnées mise en évidence](../media/content-understanding/metadata-search-box.png)

2. Dans le volet de recherche de métadonnées, tapez le texte ou sélectionnez le paramètre que vous souhaitez trouver dans un ou plusieurs champs de recherche.

    ![Capture d’écran d’une page de bibliothèque de documents affichant le volet de recherche de métadonnées](../media/content-understanding/metadata-search-pane.png)

   Les champs suivants de recherche de métadonnées sont actuellement disponibles. D’autres champs seront ajoutés à l’avenir.

   |Champ    |Utilisez ce champ pour  |
   |---------|---------|
   |Mots clés |Recherchez une correspondance de chaîne dans les métadonnées ou dans le texte intégral d’un document. |
   |Nom de fichier     |Recherche dans la **colonne Nom** de la bibliothèque.          |
   |Personnes   |Recherchez une correspondance sur des personnes dans n’importe quelle colonne de la bibliothèque.   |
   |Date de modification |Recherchez par plage de dates sélectionnée dans la **colonne Modifié** de la bibliothèque.         |
   |Type de fichier     |Effectuez une recherche par type de fichier sélectionné (par exemple, document Word ou PDF).        |
   |Type de contenu  |Recherchez par type de contenu sélectionné. Cette option s’affiche uniquement si un type de contenu non par défaut est appliqué à la bibliothèque. Les types de contenu par défaut sont les *documents* et les *dossiers*.        |

3. Vous pouvez également rechercher des colonnes de site personnalisées dans l’affichage de bibliothèque actuel. Ceci est particulièrement utile si vous avez un modèle en cours d’exécution sur la bibliothèque, car les extracteurs de métadonnées remplissent automatiquement les informations dans les colonnes de site.  

    Pour ajouter une colonne de site personnalisée à votre recherche, sélectionnez **Ajouter d’autres options**, puis sélectionnez le nom de la colonne de site.

    ![Capture d’écran du menu Ajouter d’autres options dans le volet de recherche de métadonnées.](../media/content-understanding/metadata-search-add-more-options.png)

4. Sélectionnez **Rechercher**. Les documents qui correspondent à votre recherche de métadonnées sont affichés sur la page de résultats. 
