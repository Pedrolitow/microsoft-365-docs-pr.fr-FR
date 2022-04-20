---
title: Exporter et télécharger du contenu à partir d’un cas eDiscovery (Standard)
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
ms.custom: admindeeplinkCOMPLIANCE
description: Décrit comment exporter et télécharger du contenu à partir d’un cas eDiscovery (Standard) dans Microsoft 365.
ms.openlocfilehash: 2a63d22c8b4cb20e2c0f1317a8496e1cf517b2da
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64995445"
---
# <a name="export-content-from-a-ediscovery-standard-case"></a>Exporter du contenu à partir d’un cas eDiscovery (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Une fois qu’une recherche associée à un cas Microsoft Purview eDiscovery (Standard) est exécutée, vous pouvez exporter les résultats de la recherche. Lorsque vous exportez des résultats de recherche, les éléments de boîte aux lettres sont téléchargés dans des fichiers PST ou en tant que messages individuels. Lorsque vous exportez du contenu à partir de sites SharePoint et OneDrive Entreprise, des copies de documents Office natifs et d’autres documents sont exportées. Un fichier Results.csv qui contient des informations sur chaque élément exporté et un fichier manifeste (au format XML) qui contient des informations sur chaque résultat de recherche est également exporté.
  
## <a name="export-search-results"></a>Exporter les résultats de la recherche

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité Microsoft Purview</a> et connectez-vous à l’aide des informations d’identification du compte d’utilisateur qui a reçu les autorisations eDiscovery appropriées.

2. Dans le volet de navigation gauche du portail de conformité, **sélectionnez Afficher tout**, puis **sélectionnez eDiscoveryCore** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

3. Dans la page **eDiscovery (Standard),** cliquez sur le nom du cas dans lequel vous souhaitez créer la conservation.

4. Dans la page **d’accueil** du cas, cliquez sur l’onglet **Recherches** .

5. Dans le menu **Actions** en bas de la page de menu volant, cliquez sur **Exporter les résultats**.

   ![Option Exporter les résultats dans le menu Actions.](../media/ActionMenuExportResults.png)

   Le flux de travail permettant d’exporter les résultats d’une recherche associée à un cas eDiscovery (Standard) est identique à l’exportation des résultats de recherche pour une recherche sur la page **Recherche** de contenu. Pour obtenir des instructions pas à pas, consultez [Exporter les résultats de la recherche de contenu](export-search-results.md).

   > [!NOTE]
   > Lorsque vous exportez des résultats de recherche, vous avez la possibilité d’activer la dédoublement afin qu’une seule copie d’un e-mail soit exportée, même si plusieurs instances du même message ont pu être trouvées dans les boîtes aux lettres qui ont fait l’objet d’une recherche. Pour plus d’informations sur la déduplication et la façon dont les éléments en double sont identifiés, consultez [Déduplication dans les résultats de la recherche eDiscovery](de-duplication-in-ediscovery-search-results.md).

   Une fois que vous avez démarré l’exportation, les résultats de la recherche sont préparés pour le téléchargement, ce qui signifie qu’ils sont transférés vers un emplacement de stockage Azure fourni par Microsoft dans le cloud Microsoft.
  
6. Cliquez sur l’onglet **Exportations** dans le cas pour afficher la liste des travaux d’exportation.
  
   ![Exporter des travaux sous l’onglet Exporter dans le cas eDiscovery (Standard).](../media/CoreeDiscoveryExport.png)

   Vous devrez peut-être cliquer sur **Actualiser** pour mettre à jour la liste des travaux d’exportation afin qu’elle affiche le travail d’exportation que vous avez créé. Les travaux d’exportation portent le même nom que la recherche correspondante avec **_Export** ajoutées au nom de recherche.

7. Cliquez sur le travail d’exportation que vous avez créé pour afficher les informations d’état dans la page de menu volant. Ces informations incluent le pourcentage d’éléments qui ont été transférés vers l’emplacement de stockage Azure.

8. Une fois tous les éléments transférés, cliquez sur **Télécharger les résultats** pour télécharger les résultats de la recherche sur votre ordinateur local. Pour plus d’informations sur le téléchargement des résultats de la recherche, consultez l’étape 2 dans [Exporter les résultats de la recherche de contenu](export-search-results.md#step-2-download-the-search-results)

> [!NOTE]
> Les résultats de recherche exportés doivent être téléchargés dans les 14 jours suivant la création du travail d’exportation.

### <a name="more-information-about-exporting-searches-from-a-case"></a>Plus d’informations sur l’exportation de recherches à partir d’un cas

- Pour plus d’informations sur les fichiers d’exportation inclus lors de l’exportation des résultats de recherche, consultez [Exporter un rapport de recherche de contenu](export-a-content-search-report.md#whats-included-in-the-report).

- Si vous redémarrez l’exportation, les modifications apportées aux requêtes des recherches qui composent le travail d’exportation n’affecteront pas les résultats de recherche récupérés. Lorsque vous redémarrez une exportation, le même travail de requête de recherche combiné qui a été exécuté lors de la création du travail d’exportation est réexécuté.

- En outre, si vous redémarrez une exportation, les résultats de recherche copiés vers l’emplacement stockage Azure remplacent les résultats précédents. Les résultats précédents qui ont été copiés ne seront pas disponibles pour être téléchargés.
