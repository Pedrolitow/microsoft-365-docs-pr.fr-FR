---
title: Limites eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez les limites de cas, les limites d’indexation et les limites de recherche en vigueur pour la solution eDiscovery (Premium) dans Microsoft 365.
ms.openlocfilehash: 3d0204eb452b669937d30fe5519e5af073b64d6d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099210"
---
# <a name="limits-in-ediscovery-premium"></a>Limites dans eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article décrit les limites de la solution Microsoft Purview eDiscovery (Premium) dans Microsoft 365.

## <a name="case-and-review-set-limits"></a>Limites définies pour les cas et les révisions

Le tableau suivant répertorie les limites des cas et examine les ensembles dans eDiscovery (Premium).

|Description de la limite|Limite|
|---|---|
|Nombre total de documents qui peuvent être ajoutés à un cas (pour tous les ensembles de révision dans un cas).|3 millions|
|Taille totale du fichier par jeu de charge. Cela inclut le chargement de non-Office 365 dans un jeu de révision.|300 Go|
|Quantité totale de données chargées dans tous les ensembles de révision de l’organisation par jour.<br/>|2 To|
|Nombre maximal de jeux de charge par cas.|200|
|Nombre maximal d’ensembles de révision par cas.|20|
|Nombre maximal de groupes de balises par cas.|1 000|
|Nombre maximal de balises uniques par cas.|1 <sup>0001</sup>|
|Nombre maximal de travaux simultanés dans votre organisation pour ajouter du contenu à un ensemble de révisions. Ces travaux sont nommés **Ajout de données à un jeu de révision** et sont affichés sous l’onglet **Travaux** dans un cas.|<sup>102</sup>|
|Nombre maximal de travaux simultanés pour ajouter du contenu à un jeu de révisions par utilisateur. Ces travaux sont nommés **Ajout de données à un jeu de révision** et sont affichés sous l’onglet **Travaux** dans un cas.|3|

## <a name="hold-limits"></a>Maintenir les limites

Le tableau suivant répertorie les limites des conservations associées à un cas eDiscovery (Premium).

| Description de la limite | Limite |
|:-----|:-----|
|Nombre maximal de stratégies de conservation pour une organisation. Cette limite inclut le total combiné des stratégies de conservation dans les cas de découverte électronique Microsoft Purview (Standard) et microsoft Purview eDiscovery (Premium). <br/> |10 000<sup>3</sup>  <br/> |
|Nombre maximal de boîtes aux lettres dans une conservation unique. Cette limite inclut le total combiné des boîtes aux lettres utilisateur et les boîtes aux lettres associées aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer. <br/> |1 000  <br/> |
|Nombre maximal de sites dans une conservation unique. Cette limite inclut le total combiné des sites OneDrive Entreprise, des sites SharePoint et des sites associés aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Limites d’indexation

Le tableau suivant répertorie les limites d’indexation dans eDiscovery (Premium).

|Description de la limite|Limite|
|---|---|
|Nombre maximal de caractères extraits d’un seul fichier.|10 <sup>millions4</sup>|
|Taille maximale d’un fichier unique.|150 <sup>Mo4</sup>|
|Profondeur maximale des éléments incorporés dans un document.|<sup>254</sup>|
|Taille maximale des fichiers traités par reconnaissance optique de caractères (OCR).|24 <sup>Mo4</sup> <br/>  

## <a name="search-limits"></a>Limites de la recherche

Les limites décrites dans cette section sont liées à l’utilisation de l’outil de recherche sous l’onglet **Recherches** pour collecter des données pour un cas. Pour plus d’informations, consultez [Collecter des données pour un cas dans eDiscovery (Premium).](collecting-data-for-ediscovery.md)

|Description de la limite|Limite|
|---|---|
|Nombre maximal de boîtes aux lettres ou de sites pouvant faire l’objet d’une recherche unique.|Aucune limite|
|Nombre maximal de recherches qui peuvent s’exécuter en même temps.|Sans limite|
|Nombre maximal de recherches qu’un seul utilisateur peut démarrer en même temps.|10|
|Nombre maximal de caractères pour une requête de recherche (y compris les opérateurs et les conditions).|10 <sup>0005</sup>|
|Nombre maximal de caractères pour une requête de recherche pour les sites SharePoint et OneDrive Entreprise (y compris les opérateurs et les conditions).|10 000<br>4 000 avec des caractères <sup>génériques5</sup>|
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple, **one\**_ ou _* set\***.|3|
|Nombre maximal de variantes retournées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur **BOOLEAN NEAR** .|10 <sup>0006</sup>|
|Nombre maximal d’éléments par boîte aux lettres utilisateur affichés sur la page d’aperçu pour les recherches. Les éléments les plus récents sont affichés.|100|
|Nombre maximal d’éléments de toutes les boîtes aux lettres affichées sur la page d’aperçu pour les recherches.|1 000|
|Nombre maximal de boîtes aux lettres pouvant être affichées en préversion pour les résultats de la recherche.  Si plus de 1 000 boîtes aux lettres contiennent des éléments correspondant à la requête de recherche, seules les 1 000 boîtes aux lettres les plus élevées avec le plus de résultats sont disponibles en préversion.|1 000|
|Nombre maximal d’éléments des sites SharePoint et OneDrive Entreprise affichés sur la page d’aperçu pour les recherches. Les éléments les plus récents sont affichés.|200|
|Nombre maximal de sites SharePoint et OneDrive Entreprise qui peuvent être mis en aperçu pour les résultats de la recherche. S’il existe plus de 200 sites contenant des éléments qui correspondent à la requête de recherche, seuls les 200 premiers sites avec le plus de résultats sont disponibles en préversion.|200|
|Nombre maximal d’éléments par boîte aux lettres de dossier public affichée sur la page d’aperçu pour les recherches.|100|
|Nombre maximal d’éléments trouvés dans tous les éléments de boîte aux lettres de dossier public affichés sur la page d’aperçu pour les recherches.|200|
|Nombre maximal de boîtes aux lettres de dossiers publics qui peuvent être affichées en préversion pour les résultats de la recherche. Si plus de 500 boîtes aux lettres de dossiers publics contiennent des éléments correspondant à la requête de recherche, seules les 500 boîtes aux lettres les plus élevées avec le plus de résultats sont disponibles en préversion.|500|
|Taille maximale d’un élément qui peut être affiché sur la page d’exemple d’une collection brouillon.|10 000 000 octets (environ 9,5 Mo)|

## <a name="search-times"></a>Heures de recherche

Microsoft collecte des informations sur les performances pour les recherches exécutées par toutes les organisations. Bien que la complexité de la requête de recherche puisse avoir un impact sur les heures de recherche, le facteur le plus important qui détermine la durée de la recherche est le nombre de boîtes aux lettres recherchées. Bien que Microsoft ne fournisse pas de contrat de niveau de service pour les temps de recherche, le tableau suivant répertorie les temps de recherche moyens pour les recherches de regroupement en fonction du nombre de boîtes aux lettres incluses dans la recherche.
  
|Nombre de boîtes aux lettres|Temps moyen de recherche|
|---|---|
|100|30 secondes|
|1 000|45 secondes|
|10 000|4 minutes|
|25 000|10 minutes|
|50 000|20 minutes|
|100 000|25 minutes|

## <a name="viewer-limits"></a>Limites de la visionneuse

|Description de la limite|Limite|
|---|---|
|Taille maximale de Excel fichier qui peut être affiché dans la visionneuse native.|4 Mo|

## <a name="export-limits---final-export-out-of-review-set"></a>Limites d’exportation - Exportation finale hors du jeu de révision

Les limites décrites dans cette section sont liées à l’exportation de documents hors d’un ensemble de révisions.

|Description de la limite|Limite|
|---|---|
|Taille maximale d’une seule exportation.|5 millions de documents ou 500 Go, selon la taille la plus petite|
|Nombre maximal d’exportations simultanées par jeu de révision.|1|

## <a name="review-set-download-limits"></a>Passer en revue les limites de téléchargement définies

|Description de la limite|Limite|
|---|---|
|Taille totale du fichier ou nombre maximal de documents téléchargés à partir d’un ensemble de révisions.|3 Mo ou 50 <sup>documents7</sup>|

## <a name="notes"></a>Remarques

> [!NOTE]
> <sup>1</sup> Il s’agit du nombre maximal de balises que vous pouvez créer dans un cas. Cette limite n’est pas liée au nombre de documents qui peuvent être marqués.
>
> <sup>2</sup> Cette limite est partagée avec l’exportation de contenu dans d’autres outils eDiscovery. Cela signifie que les exportations simultanées dans la recherche de contenu et eDiscovery (Standard) (et l’ajout de contenu pour passer en revue les ensembles dans eDiscovery (Premium)) sont toutes appliquées à cette limite.
>
> <sup>3</sup> Lorsque vous mettez plus de 1 000 boîtes aux lettres ou 100 sites en attente dans une stratégie de conservation unique, le système met automatiquement à l’échelle la conservation en fonction des besoins. Cela signifie que le système ajoute automatiquement des emplacements de données à plusieurs stratégies de conservation, au lieu de les ajouter à une stratégie de conservation unique. Toutefois, la limite de 10 000 stratégies de conservation des cas par organisation s’applique toujours.
>
> <sup>4</sup> Tout élément qui dépasse une limite de fichier unique s’affiche en tant qu’erreur de traitement.
>
> <sup>5</sup> Lors de la recherche SharePoint et OneDrive Entreprise emplacements, les caractères dans les URL des sites recherchés sont comptabilisés par rapport à cette limite. Le nombre total de caractères se compose des éléments suivants :
>
> - Tous les caractères dans les champs Utilisateurs et Filtres.
> - Tous les filtres d’autorisations de recherche qui s’appliquent à l’utilisateur.
> - Caractères de toutes les propriétés d’emplacement dans la recherche ; cela inclut ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion, OneDriveLocationExclusion.
>   Par exemple, l’inclusion de tous les sites SharePoint et des comptes OneDrive dans la recherche comptera six caractères, car le mot « ALL » apparaîtra à la fois pour le champ SharePointLocation et OneDriveLocation.
>
> <sup>6</sup> Pour les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela nous indique qu’un mot se produit dans un document, mais pas là où il se produit dans le document. Pour effectuer une requête d’expression (valeur de mot clé avec guillemets doubles), nous devons comparer la position dans le document pour les mots de l’expression. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expression. Dans ce cas, nous étendons en interne la requête avec tous les mots possibles auxquels le préfixe se développe ; par exemple,  **time\**_ peut se développer sur _*"time OR timer OR times OR timex OR timeboxed OR ... »**. La limite de 10 000 est le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête. Il n’existe aucune limite supérieure pour les termes autres que les termes d’expression.
>
> <sup>7</sup> Cette limite s’applique au téléchargement de documents sélectionnés à partir d’un ensemble de révisions. Elle ne s’applique pas à l’exportation de documents à partir d’un ensemble de révisions. Pour plus d’informations sur le téléchargement et l’exportation de documents, consultez [Exporter les données de cas dans eDiscovery (Premium)](exporting-data-ediscover20.md).
