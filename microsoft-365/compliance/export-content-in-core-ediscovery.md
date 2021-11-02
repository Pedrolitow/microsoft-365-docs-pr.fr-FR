---
title: Exporter et télécharger du contenu à partir d’un cas core eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Décrit comment exporter et télécharger du contenu à partir d’un cas core eDiscovery dans Microsoft 365.
ms.openlocfilehash: 5e7d17c7ddb9060417812cccd45437c30b70e9f3
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60647365"
---
# <a name="export-content-from-a-core-ediscovery-case"></a>Exporter le contenu à partir d'une affaire d' eDiscovery de base

Une fois qu’une recherche associée à un cas core eDiscovery a été correctement exécuté, vous pouvez exporter les résultats de la recherche. Lorsque vous exportez des résultats de recherche, les éléments de boîte aux lettres sont téléchargés dans des fichiers PST ou sous la mesure de messages individuels. Lorsque vous exportez du contenu à SharePoint sites OneDrive Entreprise sites, des copies de documents Office et d’autres documents sont exportées. Un Results.csv qui contient des informations sur chaque élément exporté et un fichier manifeste (au format XML) qui contient des informations sur chaque résultat de recherche est également exporté.
  
## <a name="export-search-results"></a>Exporter les résultats de la recherche

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com) and sign in using the credentials for user account that has been assigned the appropriate eDiscovery permissions.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur Afficher **tout,** puis sur **eDiscovery > Core**.

3. Dans la page **Core eDiscovery,** cliquez sur le nom du cas où vous souhaitez créer la attente.

4. Dans la page **d’accueil** du cas, cliquez sur **l’onglet Recherches.**

5. Dans le menu **Actions** en bas de la page volante, cliquez sur **Exporter les résultats.**

   ![Option Exporter les résultats dans le menu Actions.](../media/ActionMenuExportResults.png)

   Le flux de travail pour exporter les résultats d’une recherche associée à un cas core eDiscovery est identique à l’exportation des résultats de recherche pour une recherche sur la page de recherche **de** contenu. Pour obtenir des instructions détaillées, voir Exporter les résultats [de recherche de contenu.](export-search-results.md)

   > [!NOTE]
   > Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’activer la dédoplication afin qu’une seule copie d’un message électronique soit exportée, même si plusieurs instances du même message ont pu être trouvées dans les boîtes aux lettres qui ont fait l’être. Pour plus d’informations sur la dédoplication et la façon dont les éléments dupliqués sont identifiés, voir Dédoplication dans les résultats de recherche [eDiscovery](de-duplication-in-ediscovery-search-results.md).

   Une fois l’exportation commencée, les résultats de la recherche sont préparés pour le téléchargement, ce qui signifie qu’ils sont transférés vers un emplacement fourni par Microsoft stockage Azure dans le cloud Microsoft.
  
6. Cliquez sur **l’onglet Exports** dans le cas pour afficher la liste des travaux d’exportation.
  
   ![Exporter des travaux sous l’onglet Exportation dans le cas core eDiscovery.](../media/CoreeDiscoveryExport.png)

   Vous de devez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des tâches d’exportation afin qu’elle affiche la tâche d’exportation que vous avez créée. Les travaux d’exportation ont le même nom que la recherche correspondante avec **_Export** au nom de recherche.

7. Cliquez sur la tâche d’exportation que vous avez créée pour afficher les informations d’état sur la page volante. Ces informations incluent le pourcentage d’éléments qui ont été transférés vers stockage Azure’emplacement.

8. Une fois tous les éléments transférés, cliquez sur **Télécharger** les résultats pour télécharger les résultats de la recherche sur votre ordinateur local. Pour plus d’informations sur le téléchargement des résultats de recherche, voir l’étape 2 de [l’exportation des résultats de recherche de contenu](export-search-results.md#step-2-download-the-search-results)

> [!NOTE]
> Les résultats de recherche exportés doivent être téléchargés dans les 14 jours suivant la création de la tâche d’exportation.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Plus d’informations sur l’exportation de recherches à partir d’un cas

- Pour plus d’informations sur les fichiers d’exportation inclus lorsque vous exportez des résultats de recherche, voir [Exporter un rapport de recherche de contenu.](export-a-content-search-report.md#whats-included-in-the-report)

- Si vous redémarrez l’exportation, les modifications apportées aux requêtes des recherches qui font la tâche d’exportation n’affecteront pas les résultats de recherche récupérés. Lorsque vous redémarrez une exportation, le même travail de requête de recherche combiné qui a été exécuté lors de la création de la tâche d’exportation est ré-exécuté.

- En outre, si vous redémarrez une exportation, les résultats de la recherche qui sont copiés vers l’emplacement stockage Azure de recherche ont la valeur par rapport aux résultats précédents. Les résultats précédents qui ont été copiés ne pourront pas être téléchargés.
