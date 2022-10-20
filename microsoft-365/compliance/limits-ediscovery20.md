---
title: Limites eDiscovery (Premium)
description: Découvrez les limites de cas, les limites d’indexation et les limites de recherche en vigueur pour la solution eDiscovery (Premium) dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
ms.openlocfilehash: 011cbf99aaebd7c459d5431ee03bd491028b5f86
ms.sourcegitcommit: cf3811117bf20cdd27c43390cb2f10c6afc525c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68648357"
---
# <a name="limits-in-ediscovery-premium"></a>Limites dans eDiscovery (Premium)

Cet article décrit les limites de la solution Microsoft Purview eDiscovery (Premium) dans Microsoft Purview.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="case-and-review-set-limits"></a>Limites définies pour les cas et les révisions

Le tableau suivant répertorie les limites des cas et examine les ensembles dans eDiscovery (Premium).

|Description de la limite|Limite de cas classique|Nouvelle limite de cas|
|:---|:---|:---|
|Nombre total de documents qui peuvent être ajoutés à un cas (pour tous les ensembles de révision dans un cas).|3 millions|40 millions|
|Taille totale du fichier par jeu de charge. Cela inclut le chargement de non-Office 365 dans un jeu de révision.|300 Go|1 To|
|Nombre maximal de jeux de charge par cas.|200 |200 |
|Nombre maximal d’ensembles de révision par cas.|20|20|
|Nombre maximal de groupes de balises par cas.|1 000|1 000|
|Nombre maximal de balises uniques par cas.|1 000<sup>1</sup>|1 000<sup>1</sup>|

## <a name="hold-limits"></a>Maintenir les limites

Le tableau suivant répertorie les limites des conservations associées à un cas eDiscovery (Premium).

| Description de la limite | Limite |
|:-----|:-----|
|Nombre maximal de stratégies de conservation pour une organisation. Cette limite inclut le total combiné des stratégies de conservation dans les cas Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium). <br/> |10 000<sup>2</sup> |
|Nombre maximal de boîtes aux lettres en conservation unique. Cette limite inclut le total combiné des boîtes aux lettres utilisateur et les boîtes aux lettres associées aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer. <br/> |1 000 |
|Nombre maximal de sites dans une conservation unique. Cette limite inclut le total combiné des sites OneDrive Entreprise, des sites SharePoint et des sites associés aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer. | 100 |

## <a name="indexing-limits"></a>Limites d’indexation

Le tableau suivant répertorie les limites d’indexation dans eDiscovery (Premium).

|Description de la limite|Limite|
|:---|:---|
|Nombre maximal de caractères extraits d’un seul fichier.|10 millions<sup>3</sup>|
|Taille maximale d’un fichier unique.|150 Mo<sup>3</sup>|
|Profondeur maximale des éléments incorporés dans un document.|25<sup>3</sup>|
|Taille maximale des fichiers traités par reconnaissance optique de caractères (OCR).|24 Mo<sup>3</sup> |
|Débit d’indexation avancé maximal | 2 Go par heure |

## <a name="jobs-limits"></a>Limites des travaux

|Description de la limite|Limite|
|---|---|
|Nombre maximal de travaux simultanés dans votre organisation.|100|
|Nombre maximal de travaux simultanés qu’un seul utilisateur peut démarrer à la fois.|50|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, recherches à l’échelle du locataire) dans votre organisation.|50|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, les recherches à l’échelle du locataire) qu’un seul utilisateur peut démarrer à la fois.|25|

## <a name="search-limits"></a>Limites de la recherche

Les limites décrites dans cette section sont liées à l’utilisation de l’outil de recherche sous l’onglet **Recherches** pour collecter des données pour un cas. Pour plus d’informations, consultez [Collecter des données pour un cas dans eDiscovery (Premium).](collecting-data-for-ediscovery.md)

|Description de la limite|Limite|
|:---|:---|
|Nombre maximal de boîtes aux lettres ou de sites pouvant faire l’objet d’une recherche unique.|Aucune limite|
|Nombre maximal de recherches qui peuvent s’exécuter en même temps.|Aucune limite|
|Nombre maximal de caractères pour une requête de recherche (y compris les opérateurs et les conditions).|10 000<sup>4</sup>|
|Nombre maximal de caractères pour une requête de recherche pour SharePoint et OneDrive Entreprise sites (y compris les opérateurs et les conditions).|10 000<br>4 000 avec des caractères génériques<sup>4</sup>|
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple, **one\**_ ou _* set\***.|3|
|Nombre maximal de variantes retournées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur **BOOLEAN NEAR** .|10 000<sup>5</sup>|
|Nombre maximal d’éléments par boîte aux lettres utilisateur affichés sur la page d’aperçu pour les recherches. Les éléments les plus récents sont affichés.|100|
|Nombre maximal d’éléments de toutes les boîtes aux lettres affichées sur la page d’aperçu pour les recherches.|1 000|
|Nombre maximal de boîtes aux lettres pouvant être affichées en préversion pour les résultats de la recherche.  Si plus de 1 000 boîtes aux lettres contiennent des éléments correspondant à la requête de recherche, seules les 1 000 boîtes aux lettres les plus élevées avec le plus de résultats sont disponibles en préversion.|1 000|
|Nombre maximal d’éléments de SharePoint et de sites OneDrive Entreprise affichés sur la page d’aperçu pour les recherches. Les éléments les plus récents sont affichés.|200 |
|Nombre maximal de sites SharePoint et OneDrive Entreprise qui peuvent être prévisualisés pour les résultats de la recherche. S’il existe plus de 200 sites contenant des éléments qui correspondent à la requête de recherche, seuls les 200 premiers sites avec le plus de résultats sont disponibles en préversion.|200 |
|Nombre maximal d’éléments par boîte aux lettres de dossier public affichée sur la page d’aperçu pour les recherches.|100|
|Nombre maximal d’éléments trouvés dans tous les éléments de boîte aux lettres de dossier public affichés sur la page d’aperçu pour les recherches.|200 |
|Nombre maximal de boîtes aux lettres de dossiers publics qui peuvent être affichées en préversion pour les résultats de la recherche. Si plus de 500 boîtes aux lettres de dossiers publics contiennent des éléments correspondant à la requête de recherche, seules les 500 boîtes aux lettres les plus élevées avec le plus de résultats sont disponibles en préversion.|500|
|Taille maximale d’un élément qui peut être affiché sur la page d’exemple d’une collection brouillon.|10 000 000 octets (environ 9,5 Mo)|

## <a name="search-times"></a>Heures de recherche

Microsoft collecte des informations sur les performances pour les recherches exécutées par toutes les organisations. Bien que la complexité de la requête de recherche puisse avoir un impact sur les heures de recherche, le facteur le plus important qui détermine la durée de la recherche est le nombre de boîtes aux lettres recherchées. Bien que Microsoft ne fournisse pas de contrat de niveau de service pour les temps de recherche, le tableau suivant répertorie les temps de recherche moyens pour les recherches de regroupement en fonction du nombre de boîtes aux lettres incluses dans la recherche.
  
|Nombre de boîtes aux lettres|Temps moyen de recherche|
|:---|:---|
|100|30 secondes|
|1 000|45 secondes|
|10 000|4 minutes|
|25 000|10 minutes|
|50 000|20 minutes|
|100 000|25 minutes|

## <a name="viewer-limits"></a>Limites de la visionneuse

|Description de la limite|Limite|
|:---|:---|
|Taille maximale du fichier Excel qui peut être affichée dans la visionneuse native.|4 Mo|

## <a name="export-limits---final-export-out-of-review-set"></a>Limites d’exportation - Exportation finale hors du jeu de révision

Les limites décrites dans cette section sont liées à l’exportation de documents hors d’un ensemble de révisions.

|Description de la limite|Limite|
|:---|:---|
|Taille maximale d’une seule exportation.|5 millions de documents ou 500 Go, selon la taille la plus petite|

## <a name="review-set-download-limits"></a>Passer en revue les limites de téléchargement définies

|Description de la limite|Limite|
|:---|:---|
|Taille totale du fichier ou nombre maximal de documents téléchargés à partir d’un ensemble de révisions.|3 Mo ou 50 documents<sup>6</sup>|

## <a name="reference-notes"></a>Notes de référence

<sup>1</sup> Il s’agit du nombre maximal de balises que vous pouvez créer dans un cas. Cette limite n’est pas liée au nombre de documents qui peuvent être marqués.

<sup>2</sup> Lorsque vous mettez plus de 1 000 boîtes aux lettres ou 100 sites en attente dans une stratégie de conservation unique, le système met automatiquement à l’échelle la conservation en fonction des besoins. Cela signifie que le système ajoute automatiquement des emplacements de données à plusieurs stratégies de conservation, au lieu de les ajouter à une stratégie de conservation unique. Toutefois, la limite de 10 000 stratégies de conservation des cas par organisation s’applique toujours.

<sup>3</sup> Tout élément qui dépasse une limite de fichier unique s’affiche en tant qu’erreur de traitement.

<sup>4</sup> Lors de la recherche dans SharePoint et OneDrive Entreprise emplacements, les caractères figurant dans les URL des sites faisant l’objet d’une recherche sont comptabilisés dans cette limite. Le nombre total de caractères se compose des éléments suivants :

  - Tous les caractères dans les champs Utilisateurs et Filtres.
  - Tous les filtres d’autorisations de recherche qui s’appliquent à l’utilisateur.
  - Caractères de toutes les propriétés d’emplacement dans la recherche, notamment ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion et OneDriveLocationExclusion. Par exemple, l’inclusion de tous les sites SharePoint et comptes OneDrive dans la recherche comptera six caractères, car le mot « ALL » apparaîtra pour le champ SharePointLocation et OneDriveLocation.

<sup>5</sup> Pour les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela nous indique qu’un mot se produit dans un document, mais pas là où il se produit dans le document. Pour effectuer une requête d’expression (valeur de mot clé avec guillemets doubles), nous devons comparer la position dans le document pour les mots de l’expression. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expression. Dans ce cas, nous étendons en interne la requête avec tous les mots possibles auxquels le préfixe se développe ; par exemple,  **time\**_ peut se développer sur _*"time OR timer OR times OR timex OR timeboxed OR ... »**. La limite de 10 000 est le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête. Il n’existe aucune limite supérieure pour les termes autres que les termes d’expression.

<sup>6</sup> Cette limite s’applique au téléchargement de documents sélectionnés à partir d’un ensemble de révisions. Elle ne s’applique pas à l’exportation de documents à partir d’un ensemble de révisions. Pour plus d’informations sur le téléchargement et l’exportation de documents, consultez [Exporter les données de cas dans eDiscovery (Premium).](exporting-data-ediscover20.md)
