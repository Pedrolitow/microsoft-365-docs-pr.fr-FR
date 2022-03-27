---
title: Limites pour la recherche de contenu et la découverte électronique principale dans le centre de conformité
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
search.appverid:
- MOE150
- MET150
ms.assetid: 78fe3147-1979-4c41-83bb-aeccf244368d
description: Découvrez les limites en vigueur pour la recherche de contenu et les fonctionnalités eDiscovery principales dans le Centre de conformité Microsoft 365.
ms.openlocfilehash: ad72dfa1d599a908a56b3b6530433ccb5ed23df4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715947"
---
# <a name="limits-for-ediscovery-search"></a>Limites pour la recherche de découverte électronique

Diverses limites sont appliquées aux outils de recherche eDiscovery dans le Centre de conformité Microsoft 365. Cela inclut les recherches qui s’exécutent sur **la page de** recherche de contenu et les recherches associées à un cas **eDiscovery sur la page Core eDiscovery** . Ces limites permettent de maintenir l’état et la qualité des services fournis aux organisations. Il existe également des limites liées à l’indexation des messages électroniques dans Exchange Online pour la recherche. Vous ne pouvez pas modifier les limites pour les recherches eDiscovery ou l’indexation du courrier électronique, mais vous devez en avoir connaissance afin de pouvoir prendre ces limites en considération lors de la planification, de l’exécution et du dépannage des recherches de découverte électronique.

Pour les limites liées à l’outil Advanced eDiscovery, voir [Limites dans Advanced eDiscovery](limits-ediscovery20.md)

## <a name="search-limits"></a>Limites de la recherche

Le tableau suivant répertorie les limites de recherche lors de l’utilisation de l’outil de recherche de contenu dans le Centre de conformité Microsoft 365 et pour les recherches associées à un cas core eDiscovery.

<br>

****

|Description de la limite|Limite|
|---|---|
|Nombre maximal de boîtes aux lettres ou de sites dans le cas d’une recherche unique|Aucune limite <sup>1</sup>|
|Nombre maximal de recherches qui peuvent s’exécuter en même temps dans votre organisation.|30|
|Nombre maximal de recherches à l’échelle de l’organisation qui peuvent être exécutés en même temps.|3|
|Nombre maximal de recherches qu’un seul utilisateur peut démarrer en même temps. Cette limite est très probablement atteint lorsque l’utilisateur tente de démarrer plusieurs recherches à l’aide de la commande **Get-ComplianceSearch \|Start-ComplianceSearch** dans le Centre de sécurité & conformité PowerShell.|10|
|Nombre maximal d’éléments par boîte aux lettres d’utilisateur qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche de contenu.|100|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres utilisateur pouvant éventuellement être affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche. Les éléments les plus récents sont affichés.|1 000 <sup>2</sup>|
|Nombre maximal de boîtes aux lettres d’utilisateur dont vous pouvez afficher un aperçu des résultats de recherche. Si plus de 1 000 boîtes aux lettres contiennent du contenu qui correspond à la requête de recherche, au maximum, seules les 1 000 boîtes aux lettres ayant le plus grand nombre de résultats de recherche seront disponibles en aperçu.|1 000|
|Nombre maximal d’éléments trouvés dans SharePoint sites OneDrive Entreprise qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche. Les éléments les plus récents sont affichés.|200|
|Nombre maximal de sites (en SharePoint et OneDrive Entreprise) qui peuvent être prévisualiser pour les résultats de recherche. Si plus de 200 sites au total contiennent du contenu qui correspond à la requête de recherche, seuls les 200 premiers sites ayant le plus grand nombre de résultats de recherche seront disponibles en aperçu.|200|
|Nombre maximal d’éléments par boîte aux lettres de dossiers publics qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche de contenu.|100|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres de dossiers publics qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche de contenu.|200|
|Nombre maximal de boîtes aux lettres de dossiers publics qui peuvent être prévisualiser pour les résultats de recherche. Si plus de 500 boîtes aux lettres de dossiers publics contiennent du contenu qui correspond à la requête de recherche, seules les 500 boîtes aux lettres de dossiers publics les plus populaires seront disponibles pour aperçu.|500|
|Taille maximale d’un élément qui peut être vue sur la page d’aperçu.|10 000 000 octets (environ 9,5 Mo)|
|Nombre maximal de caractères pour la requête de recherche (y compris les opérateurs et les conditions) d’une recherche. <p> **Remarque :** Cette limite prend effet une fois la requête étendue et inclut les caractères de la requête par mot clé, les filtres d’autorisations de recherche appliqués à l’utilisateur et les URL de tous les emplacements du site. Cela signifie que la requête est étendue par rapport à chacun des mots clés. Par exemple, si une requête de recherche a 15 mots clés et des paramètres et conditions supplémentaires, la requête est étendue 15 fois, chacune avec les autres paramètres et conditions dans la requête. Ainsi, même si le nombre de caractères dans la requête de recherche peut être inférieur à la limite, c’est la requête étendue qui peut contribuer au dépassement de cette limite.|**Boîtes aux lettres :** 10 000. <p> **Sites :** 4 000 lors de la recherche sur tous les sites ou 2 000 lors de la recherche de 20 sites au plus. <sup>3</sup>|
|Nombre maximal de variantes renvoyées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte dans une requête de recherche ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur **booléen NEAR** .|10 000 <sup>4</sup>|
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple, `time*`, `one*`ou `set*`.|3|
|Nombre maximal de boîtes aux lettres dans une recherche dans qui vous pouvez supprimer des éléments en faisant une action de « recherche et purge » (à l’aide de la commande **New-ComplianceSearchAction -Purge** ). Si le nombre de boîtes aux lettres sources de la recherche pour une action de purge est supérieur à cette limite, l’action de purge échouera. Pour plus d’informations sur la recherche et la purge, voir [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).|50 000|
|Nombre maximal d’emplacements d’une recherche à partir des emplacements à partir de qui vous pouvez exporter des éléments. Si la recherche que vous exportez a plus d’emplacements que cette limite, l’exportation échoue. Pour plus d’informations, voir [Exporter les résultats de recherche de contenu](export-search-results.md).|100 000|

> [!NOTE]
> <sup>1</sup> Bien que vous pouvez rechercher un nombre illimité de boîtes aux lettres dans une seule recherche, vous ne pouvez télécharger les résultats de recherche exportés qu’à partir d’un maximum de 100 000 boîtes aux lettres à l’aide de l’outil d’exportation eDiscovery dans le Centre de conformité Microsoft 365.
>
> <sup>2 L’objectif</sup> de la page d’aperçu est d’afficher un échantillon limité des résultats. Même pour les recherches massives avec des milliers de résultats, le nombre d’éléments affichés sur la page d’aperçu peut, et souvent, être beaucoup moins élevé que la valeur maximale possible de 1 000. Pour voir les résultats de recherche complets, vous devez exporter les résultats.
>
> <sup>3 Lors</sup> de la recherche SharePoint et OneDrive Entreprise’emplacements, les caractères dans les URL des sites recherchés sont comptabilisés dans cette limite.
>
> <sup>4 Pour</sup> les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela nous indique qu’un mot se trouve dans un document, mais pas là où il se trouve dans le document. Pour faire une requête d’expression (valeur de mot clé avec des guillemets doubles), nous devons comparer la position des mots dans l’expression dans le document. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expressions. Dans ce cas, nous étendons la requête en interne avec tous les mots possibles que le préfixe développe ; par exemple, `"time*"` peut s’étendre à `"time OR timer OR times OR timex OR timeboxed OR ..."`. Le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête, est de 10 000. Il n’existe aucune limite supérieure pour les termes autres que des expressions.

## <a name="search-times"></a>Temps de recherche

Microsoft collecte des informations de performances pour les recherches exécutés par toutes les organisations. Bien que la complexité de la requête de recherche puisse avoir un impact sur les heures de recherche, le facteur le plus important qui détermine la durée de la recherche est le nombre de boîtes aux lettres recherchées. Bien que Microsoft ne fournisse pas de contrat de niveau de service pour les heures de recherche, le tableau suivant répertorie les durées moyennes de recherche pour les recherches de collecte en fonction du nombre de boîtes aux lettres incluses dans la recherche.

<br>

****

|Nombre de boîtes aux lettres|Temps moyen de recherche|
|---|---|
|100|30 secondes|
|1 000|45 secondes|
|10 000|4 minutes|
|25 000|10 minutes|
|50 000|20 minutes|
|100 000|25 minutes|

## <a name="export-limits"></a>Limites d’exportation

Le tableau suivant répertorie les limites lors de l’exportation des résultats d’une recherche de contenu. Ces limites s’appliquent également lorsque vous exportez du contenu à partir d’un cas core eDiscovery.

<br>

****

|Description de la limite|Limite|
|---|---|
|Quantité maximale de données exportables à partir d’une seule recherche  <p> **Remarque :** Si les résultats de la recherche sont supérieurs à 2 To, envisagez d’utiliser des plages de dates ou d’autres types de filtres pour réduire la taille totale des résultats de la recherche.|2 To|
|Maximum qu’une organisation peut exporter en une seule journée <p> **Remarque :** Cette limite est réinitialisée quotidiennement à 00:00 UTC|2 To|
|Nombre maximal d’exportations simultanées qui peuvent être exécuter en même temps au sein de votre organisation <p> **Remarque :** L’exécution **d’une exportation** de rapport uniquement est comptabilisée par rapport au nombre total d’exportations simultanées pour votre organisation. Si trois utilisateurs effectuent 3 exportations chacune, une seule autre exportation peut être effectuée. Qu’il s’agit d’exporter un rapport ou des résultats de recherche, aucune autre exportation ne peut être effectuée tant qu’une exportation n’est pas terminée.|10|
|Nombre maximal d’exportations qu’un seul utilisateur peut exécuter à tout moment|3|
|Nombre maximal de boîtes aux lettres pour les résultats de recherche qui peuvent être téléchargées à l’aide de l’outil d’exportation eDiscovery|100 000|
|Taille maximale du fichier PST qui peut être exporté <p> **Remarque :** Si les résultats de recherche de la boîte aux lettres d’un utilisateur sont supérieurs à 10 Go, les résultats de la recherche pour la boîte aux lettres sont exportés dans deux (ou plusieurs) fichiers PST distincts. Si vous choisissez d’exporter tous les résultats de recherche dans un seul fichier PST, le fichier PST est s’insère dans des fichiers PST supplémentaires si la taille totale des résultats de la recherche est supérieure à 10 Go. Si vous souhaitez modifier cette taille par défaut, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Voir [Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery](change-the-size-of-pst-files-when-exporting-results.md). Les résultats de la recherche provenant d’une boîte aux lettres spécifique ne sont pas répartis entre plusieurs fichiers PST, sauf si le contenu d’une seule boîte aux lettres est supérieur à 10 Go. Si vous avez choisi d’exporter les résultats de la recherche dans un fichier PST contenant tous les messages d’un même dossier et que les résultats de la recherche sont supérieurs à 10 Go, les éléments sont toujours organisés dans l’ordre chronologique, de sorte qu’ils seront ajoutés dans des fichiers PST supplémentaires en fonction de la date d’envoi.|10 Go|
|Évaluer la fréquence à laquelle les résultats de recherche provenant de boîtes aux lettres et de sites sont téléchargés vers un emplacement fourni stockage Azure Microsoft.|Maximum de 2 Go par heure|

## <a name="indexing-limits-for-email-messages"></a>Limites d’indexation pour les messages électroniques

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le retour d’un message électronique en tant qu’élément non indexé ou partiellement indexé dans les résultats d’une recherche de contenu.

<br>

****

|Limite d’indexation|Valeur maximale|Description|
|---|---|---|
|Taille maximale de pièce jointe|150 Mo|Taille maximale d’une pièce jointe de courrier électronique qui sera l’indexation. Les pièces jointes dont la taille est supérieure à cette limite ne seront pas indexées et le message avec la pièce jointe sera marqué comme partiellement indexé. <p> **Remarque :** L’examen est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères inutiles tels que les signes de ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé tokenization), qui sont ensuite stockés dans l’index.|
|Nombre maximal de pièces jointes|250|Nombre maximal de fichiers joints à un message électronique qui seront à l’indexation. Si un message a plus de 250 pièces jointes, les 250 premières pièces jointes sont parées et indexées, et le message est marqué comme partiellement indexé car il avait des pièces jointes supplémentaires qui n’ont pas été l’ont été.|
|Profondeur maximale des pièces jointes|30|Nombre maximal de pièces jointes imbrmbrées qui sont parsées. Par exemple, si un message électronique est joint à un autre message et que le message joint contient un document Word joint, le document Word et le message joint sont indexés. Ce comportement se poursuit pour jusqu’à 30 pièces jointes imbrmbrées.|
|Nombre maximal d’images jointes|0|Une image jointe à un message électronique est ignorée par l’asseur et n’est pas indexée.|
|Temps maximal passé à l’d’un élément|30 secondes|Un maximum de 30 secondes est consacré à l’indexation d’un élément. Si le temps d’indexation dépasse 30 secondes, l’élément est marqué comme partiellement indexé.|
|Sortie maximale de l’parseur|2 millions de caractères|Quantité maximale de texte provenant de l’indexeur indexé. Par exemple, si l’utilisateur a extrait 8 millions de caractères d’un document, seuls les 2 premiers millions de caractères sont indexés.|
|Nombre maximal de jetons d’annotation|2 millions|Lorsqu’un message électronique est indexé, chaque mot est annoté avec différentes instructions de traitement qui spécifient comment ce mot doit être indexé. Chaque ensemble d’instructions de traitement est appelé jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions de jetons d’annotation pour un message électronique.|
|Taille maximale du corps dans l’index|67 millions de caractères|Nombre total de caractères dans le corps d’un message électronique et toutes ses pièces jointes. Lorsqu’un message électronique est indexé, tout le texte du corps du message et de toutes les pièces jointes est concaté en une seule chaîne. La taille maximale de cette chaîne indexée est de 67 millions de caractères.|
|Nombre maximal de jetons uniques dans le corps|1 million|Comme indiqué précédemment, les jetons sont le résultat de l’extraction de texte à partir du contenu, de la suppression des signes de ponctuation et des espaces, puis de sa division en mots (appelés jetons) stockés dans l’index. Par exemple, l’expression `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seuls 4 d’entre eux sont des jetons uniques. Il existe une limite de 1 million de jetons uniques par message électronique, ce qui permet d’éviter que l’index ne soit trop grand avec des jetons aléatoires.|
|||

## <a name="more-information"></a>Plus d’informations

Il existe des limites supplémentaires liées à différents aspects de la recherche de contenu, tels que l’indexation de contenu. Pour plus d’informations sur ces limites, consultez les rubriques suivantes :

- [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md)

- [Recherche d’éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)

- [Limites de recherche pour SharePoint Online](/sharepoint/search-limits)

Pour plus d’informations sur les recherches de contenu, voir :

- [Recherche de contenu dans Microsoft 365](content-search.md)

- [Rechercher du contenu dans un cas core eDiscovery](search-for-content-in-core-ediscovery.md)

- [Requêtes par mot clé et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)

Pour les limites de cas liées à core eDiscovery et Advanced eDiscovery, voir :

- [Limites dans Core eDiscovery](limits-core-ediscovery.md)

- [Limites définies dans Advanced eDiscovery](limits-ediscovery20.md)
