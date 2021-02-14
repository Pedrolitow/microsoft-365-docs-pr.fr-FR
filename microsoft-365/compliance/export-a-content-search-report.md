---
title: Exporter un rapport de recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.CustomizeExportReport
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 5c8c1db6-d8ac-4dbb-8a7a-f65d452169b9
description: Au lieu d’exporter les résultats réels d’une recherche de contenu dans le Centre de sécurité & conformité dans Office 365, vous pouvez exporter un rapport de résultats de recherche. Le rapport contient un résumé des résultats de la recherche et un document contenant des informations détaillées sur chaque élément qui serait exporté.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de27e25945f14f6a6119b4c1776eebca5e84d8ce
ms.sourcegitcommit: 9ce9001aa41172152458da27c1c52825355f426d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "47358300"
---
# <a name="export-a-content-search-report"></a>Exporter un rapport de recherche de contenu

Au lieu d’exporter l’ensemble complet des résultats de recherche à partir d’une recherche de contenu dans le Centre de sécurité & conformité (et à partir d’une recherche de contenu associée à un cas eDiscovery), vous pouvez exporter les rapports générés lors de l’exportation des résultats de recherche.
  
Lorsque vous exportez un rapport, il est téléchargé vers un dossier qui a le même nom que la recherche de contenu, mais qui est également _ReportsOnly *.* Par exemple, si la recherche de contenu est nommée  *ContosoCase0815*, le rapport est téléchargé dans un dossier nommé *ContosoCase0815_ReportsOnly*. Pour obtenir la liste des documents inclus dans le rapport, voir Ce qui [est inclus dans le rapport.](#whats-included-in-the-report)

## <a name="assign-roles-and-check-system-requirements"></a>Attribuer des rôles et vérifier la exigences système

- Pour exporter un rapport de recherche de contenu, vous devez avoir le rôle de gestion recherche de conformité dans le Centre de sécurité & conformité. Ce rôle est attribué par défaut au Gestionnaire eDiscovery intégré et aux groupes de rôles Gestion de l’organisation. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- Lorsque vous exportez un rapport, les données sont stockées temporairement dans une zone de stockage Azure unique dans le cloud Microsoft avant d’être téléchargées sur votre ordinateur local. Assurez-vous que votre organisation peut se connecter au point de terminaison dans Azure, qui est **\* .blob.core.windows.net** (le caractère générique représente un identificateur unique pour votre exportation). Les données des résultats de la recherche sont supprimées de la zone de stockage Azure deux semaines après sa création. 
    
- L’ordinateur que vous utilisez pour exporter les résultats de recherche doit répondre aux exigences système suivantes :
    
  - Versions 32 bits ou 64 bits de Windows 7 et versions ultérieures
    
  - Microsoft .NET Framework 4.7
    
- Vous devez utiliser l’un des navigateurs pris en charge suivants pour exécuter l’outil d’exportation eDiscovery<sup>1</sup>:

  - Microsoft Edge <sup>2</sup>

    Ou

  - Microsoft Internet Explorer 10 et versions ultérieures

  > [!NOTE]
  > <sup>1</sup> Microsoft ne fabrique pas d’extensions ou d’extensions tierces pour ClickOnce applications. L’exportation des résultats de recherche à l’aide d’un navigateur non pris en charge avec des extensions ou extensions tierces n’est pas prise en charge.<br/>
  > <sup>2</sup> Suite aux modifications récentes apportées à Microsoft Edge, la prise en charge ClickOnce’est plus activée par défaut. Pour obtenir des instructions sur l’activation ClickOnce prise en charge dans Edge, voir Utiliser l’outil d’exportation [eDiscovery dans Microsoft Edge.](configure-edge-to-export-search-results.md)

- Si la taille totale estimée des résultats renvoyés par une recherche de contenu dépasse 2 To, l’exportation du rapport échoue. Pour exporter correctement le rapport, essayez de restreindre l’étendue et réexécutez la recherche afin que la taille estimée des résultats soit inférieure à 2 To.

- L’exportation de rapports de recherche de contenu est comptabilisée par rapport au nombre maximal d’exportations en cours d’exécution en même temps et au nombre maximal d’exportations qu’un seul utilisateur peut exécuter. Pour plus d’informations sur les limites d’exportation, voir Exporter les résultats [de la recherche de contenu.](export-search-results.md#export-limits)

## <a name="generate-and-download-a-content-search-report"></a>Générer et télécharger un rapport de recherche de contenu

Les étapes de générer et de télécharger un rapport de recherche de contenu sont similaires à l’exportation des résultats de recherche.
  
## <a name="step-1-generate-the-report-for-export"></a>Étape 1 : Générer le rapport pour l’exportation

La première étape consiste à préparer le rapport pour le téléchargement vers l’exportation de votre ordinateur. Lorsque vous publiez le rapport, les documents de rapport sont chargés vers une zone de stockage Azure dans le cloud Microsoft.
  
1. Accédez à [https://protection.office.com](https://protection.office.com).
    
2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.
    
3. Dans le volet gauche du Centre de sécurité & conformité, cliquez sur **Recherche de** contenu \> **de recherche.**
    
4. Dans la page **de recherche de** contenu, sélectionnez une recherche. 
    
5. Dans le volet d’informations, sous **Exporter le rapport sur un ordinateur,** cliquez sur Générer un **rapport.**
    
    > [!NOTE]
    > Si les résultats d’une recherche datent d’il y a plus de 7 jours, vous êtes invité à mettre à jour les résultats. Si cela se produit,  annulez l’exportation, cliquez sur Mettre à jour les résultats de recherche dans le volet d’informations de la recherche sélectionnée, puis recommencez l’exportation du rapport après la mise à jour des résultats. 
  
6. Dans la page **Exporter un rapport,** sous Inclure ces éléments à partir de la **recherche,** choisissez l’une des options suivantes :
    
    - exporter uniquement les éléments indexés ;
    
    - exporter les éléments indexés et non indexés ;
    
    - exporter uniquement les éléments non indexés.
    
    Pour plus d’informations sur les éléments non indexés, voir [Éléments partiellement indexés dans la recherche de contenu.](partially-indexed-items-in-content-search.md)
    
7. Choisissez d’inclure des statistiques de recherche pour toutes les versions des documents SharePoint. Cette option apparaît uniquement si les sources de contenu de la recherche incluent des sites SharePoint ou OneDrive Entreprise.
    
8. Cliquez **sur Générer un rapport.**
    
    Le rapport des résultats de la recherche est préparé pour le téléchargement, ce qui signifie que les documents du rapport seront téléchargés vers l’espace de stockage Azure dans le cloud Microsoft. Lorsque le rapport est prêt  à être téléchargé, le lien du rapport de téléchargement s’affiche sous **Rapport** d’exportation vers un ordinateur dans le volet d’informations. 
    
> [!NOTE]
> Vous pouvez également exporter un rapport pour une recherche de contenu associée à un cas eDiscovery. Pour ce faire, allez à **eDiscovery eDiscovery,** sélectionnez un cas, puis cliquez sur \>   ![ Modifier l’icône ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) Modifier. Dans la page **Recherches,** sélectionnez une  recherche, puis cliquez sur Exporter les résultats de la recherche icône Exporter un ![ ](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) \> **rapport.** 
  
## <a name="step-2-download-the-report"></a>Étape 2 : Télécharger le rapport

L’étape suivante consiste à télécharger le rapport à partir de la zone de stockage Azure sur votre ordinateur local.
  
1. Dans le volet d’informations de la recherche pour qui vous avez généré le rapport, sous **Exporter** le rapport sur un ordinateur, cliquez sur **Télécharger le rapport.**
    
    La page **Télécharger** le rapport s’affiche et contient les informations suivantes sur le rapport téléchargé sur votre ordinateur. 
    
    - Le nombre d’éléments à télécharger.
    
    - La taille totale estimée des éléments à télécharger.
    
    - Si les éléments indexés ou non indexés seront exportés. Les éléments non indexés sont des éléments qui ont un format reconnu, qui sont chiffrés ou qui n’ont pas été indexés pour d’autres raisons.
    
    - Si les versions des documents SharePoint seront téléchargées.
    
    - État du processus d’exportation de rapport. Vous pouvez commencer à télécharger le rapport même si sa préparation n’est pas terminée.
    
2. Sous **Clé d’exportation**, cliquez sur **Copier dans le Presse-papiers**. Vous utilisez cette clé à l’étape 5 pour télécharger le rapport.
    
    > [!IMPORTANT]
    > Étant donné que tout le monde peut installer et démarrer l’outil d’exportation eDiscovery, puis utiliser cette clé pour télécharger le rapport de recherche, prenez toutes les précautions nécessaires pour protéger cette clé comme vous le feriez pour protéger les mots de passe ou d’autres informations de sécurité. 
  
3. Cliquez **sur Télécharger le rapport.**
    
4. Si vous êtes invité à installer l’outil **d’exportation eDiscovery,** cliquez sur **Installer.**
    
5. Dans l’**outil d’exportation de découverte électronique**, collez la clé d’exportation que vous avez copiée à l’étape 2 dans la zone appropriée. 
    
6. Cliquez **sur Parcourir** pour spécifier l’emplacement où vous souhaitez télécharger le rapport. 
    
7. Cliquez sur **Démarrer** pour télécharger les résultats de recherche sur votre ordinateur. 
    
    L’**outil d’exportation de découverte électronique** affiche l’état du processus d’exportation, ainsi qu’une estimation du nombre (et de la taille) d’éléments qui doivent encore être téléchargés. Une fois le processus d’exportation terminé, vous pouvez accéder aux fichiers à l’emplacement où ils ont été téléchargés. 
    
> [!NOTE]
> Vous pouvez télécharger le rapport pour une recherche de contenu associée à un cas eDiscovery. Pour ce faire, allez à **eDiscovery eDiscovery,** sélectionnez un cas, puis cliquez sur \>   ![ Modifier l’icône ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) Modifier. Dans la page **Exportation,** sélectionnez une exportation de rapport, puis cliquez sur Télécharger le rapport **dans** le volet d’informations. 
  
## <a name="whats-included-in-the-report"></a>Ce qui est inclus dans le rapport

Lorsque vous générez et exportez un rapport sur les résultats d’une recherche de contenu, les documents suivants sont téléchargés :
  
- **Résumé de l’exportation :** Document Excel qui contient un résumé de l’exportation. Cela inclut des informations telles que le nombre de sources de contenu qui ont fait l’objet d’une recherche, le nombre de résultats de recherche à partir de chaque emplacement de contenu, le nombre estimé d’éléments, le nombre réel d’éléments à exporter et la taille estimée et réelle des éléments à exporter. 
    
    > [!NOTE]
    > Si vous incluez des éléments nonndex lors de l’exportation du rapport, le nombre d’éléments nonndex est inclus dans le nombre total d’estimations de résultats de recherche et dans le nombre total de résultats de recherche téléchargés (si vous de étiez pour exporter les résultats de la recherche) répertoriés dans le rapport récapitulatif de l’exportation. En d’autres termes, le nombre total d’éléments à télécharger est égal au nombre total de résultats estimés et au nombre total d’éléments nonndex. 
  
- **Manifeste :** Fichier manifeste (au format XML) qui contient des informations sur chaque élément inclus dans les résultats de la recherche. 
    
- **Résultats :** Document Excel qui contient une ligne contenant des informations sur chaque élément indexé qui serait exporté avec les résultats de la recherche. Pour le courrier électronique, le journal des résultats contient des informations sur chaque message, y compris : 
    
  - l’emplacement du message dans la boîte aux lettres source (notamment si le message est dans la boîte aux lettres principale ou d’archivage) ;
    
  - la date à laquelle le message a été envoyé ou reçu ;
    
  - l’objet du message ;
    
  - l’expéditeur et les destinataires du message.
    
    Pour les documents provenant de sites SharePoint et OneDrive Entreprise, le journal des résultats contient des informations sur chaque document, notamment :
    
  - l’URL du document ;
    
  - l’URL de la collection de sites qui héberge le document ;
    
  - la date à laquelle le document a été modifié pour la dernière fois ;
    
  - le nom du document (qui se trouve dans la colonne Objet du journal des résultats).
    
    > [!NOTE]
    > Le nombre de lignes  dans le rapport résultats doit être égal au nombre total de résultats de recherche moins le nombre total d’éléments répertoriés dans le rapport Éléments **nonndes.** 
  
- **Éléments nonndexés :** Document Excel qui contient des informations sur les éléments nonndes inclus dans les résultats de la recherche. Si vous n’incluez pas d’éléments nonndex lorsque vous générez le rapport de résultats de recherche, ce rapport sera toujours téléchargé, mais il sera vide.
