---
title: Limites pour la recherche de contenu et eDiscovery (Standard) dans le centre de conformité
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Découvrez les limites en vigueur pour les fonctionnalités de recherche de contenu et eDiscovery (Standard) dans le portail de conformité Microsoft Purview.
ms.openlocfilehash: 53af013e5e247d617e88bc0600bd3c0324c7627f
ms.sourcegitcommit: 06b81b66f13774102bb34556479c1ff890011afb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67357519"
---
# <a name="limits-for-ediscovery-search"></a>Limites pour la recherche eDiscovery

Différentes limites sont appliquées aux outils de recherche eDiscovery dans le portail de conformité Microsoft Purview. Cela inclut les recherches exécutées sur la page **de recherche de contenu** et les recherches associées à un cas eDiscovery sur la page **eDiscovery (Standard).** Ces limites contribuent à maintenir la santé et la qualité des services fournis aux organisations. Il existe également des limites liées à l’indexation des messages électroniques dans Exchange Online pour la recherche. Vous ne pouvez pas modifier les limites des recherches eDiscovery ou de l’indexation des e-mails, mais vous devez les connaître afin de pouvoir prendre en compte ces limites lors de la planification, de l’exécution et de la résolution des problèmes liés aux recherches eDiscovery.

Pour connaître les limites liées à l’outil Microsoft Purview eDiscovery (Premium), consultez [Limites dans eDiscovery (Premium)](limits-ediscovery20.md)

## <a name="search-limits"></a>Limites de la recherche

Le tableau suivant répertorie les limites de recherche lors de l’utilisation de l’outil de recherche de contenu dans le portail de conformité et pour les recherches associées à un cas Microsoft Purview eDiscovery (Standard).

<br>

****

|Description de la limite|Limite|
|---|---|
|Nombre maximal de boîtes aux lettres ou de sites pouvant faire l’objet d’une recherche unique|Aucune limite <sup>1</sup>|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres utilisateur qui peuvent éventuellement être affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche. Les éléments les plus récents sont affichés.|1 000 <sup>2</sup>|
|Nombre maximal de boîtes aux lettres d’utilisateur dont vous pouvez afficher un aperçu des résultats de recherche. S’il existe plus de 1 000 boîtes aux lettres contenant du contenu qui correspond à la requête de recherche, au maximum, seules les 1 000 boîtes aux lettres ayant le plus de résultats de recherche sont disponibles en préversion.|1 000|
|Nombre maximal d’éléments trouvés dans SharePoint et OneDrive Entreprise sites affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche. Les éléments les plus récents sont affichés.|200 |
|Nombre maximal de sites (dans SharePoint et OneDrive Entreprise) qui peuvent être aperçus pour les résultats de la recherche. S’il existe plus de 200 sites au total qui contiennent du contenu qui correspond à la requête de recherche, seuls les 200 premiers sites avec le plus de résultats de recherche seront disponibles en préversion.|200 |
|Nombre maximal d’éléments par boîte aux lettres de dossier public qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche de contenu.|100|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres de dossiers publics affichées sur la page d’aperçu lors de l’aperçu des résultats de la recherche de contenu.|200 |
|Nombre maximal de boîtes aux lettres de dossiers publics qui peuvent être affichées en préversion pour les résultats de la recherche. S’il existe plus de 500 boîtes aux lettres de dossiers publics qui contiennent du contenu qui correspond à la requête de recherche, seules les 500 boîtes aux lettres de dossier public ayant le plus de résultats de recherche seront disponibles en préversion.|500|
|Taille maximale d’un élément qui peut être affiché sur la page d’aperçu.|10 000 000 octets (environ 9,5 Mo)|
|Nombre maximal de caractères pour la requête de recherche (y compris les opérateurs et les conditions) pour une recherche. <p> **Note:** Cette limite prend effet une fois la requête développée et inclut les caractères de la requête de mot clé, les filtres d’autorisations de recherche appliqués à l’utilisateur et les URL de tous les emplacements de site. Cela signifie que la requête sera développée par rapport à chacun des mots clés. Par exemple, si une requête de recherche comporte 15 mots clés et des paramètres et conditions supplémentaires, la requête est développée 15 fois, chacune avec les autres paramètres et conditions de la requête. Ainsi, même si le nombre de caractères dans la requête de recherche peut être inférieur à la limite, c’est la requête développée qui peut contribuer à dépasser cette limite.|**Boîtes aux lettres :** 10 000. <p> **Sites :** 4 000 lors de la recherche de tous les sites ou 2 000 lors de la recherche d’un maximum de 20 sites. <sup>3</sup>|
|Nombre maximal de variantes retournées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte dans une requête de recherche ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur **BOOLEAN NEAR** .|10 000 <sup>4</sup>|
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple, `time*`, `one*`ou `set*`.|3|
|Nombre maximal de boîtes aux lettres dans une recherche dans lesquelles vous pouvez supprimer des éléments en effectuant une action de « recherche et purge » (à l’aide de la commande **New-ComplianceSearchAction -Purge** ). Si la recherche pour laquelle vous effectuez une action de vidage contient plus de boîtes aux lettres sources que cette limite, l’action de vidage échoue. Pour plus d’informations sur la recherche et le vidage, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).|50 000|
|Nombre maximal d’emplacements dans une recherche à partir de laquelle vous pouvez exporter des éléments. Si la recherche que vous exportez a plus d’emplacements que cette limite, l’exportation échoue. Pour plus d’informations, consultez [Exporter les résultats de la recherche de contenu](export-search-results.md).|100 000|

> [!NOTE]
> <sup>1</sup> Bien que vous puissiez rechercher un nombre illimité de boîtes aux lettres dans une seule recherche, vous pouvez uniquement télécharger les résultats de recherche exportés à partir d’un maximum de 100 000 boîtes aux lettres à l’aide de l’outil d’exportation eDiscovery dans le portail de conformité.
>
> <sup>2</sup> L’objectif de la page d’aperçu est d’afficher un échantillon limité des résultats. Même pour les recherches massives avec des milliers de résultats, le nombre d’éléments affichés sur la page d’aperçu peut, et souvent, être bien inférieur à la valeur maximale possible de 1 000. Pour afficher les résultats complets de la recherche, vous devez exporter les résultats.
>
> <sup>3</sup> Lors de la recherche dans SharePoint et OneDrive Entreprise emplacements, les caractères dans les URL des sites recherchés sont comptabilisés dans cette limite.
>
> <sup>4</sup> Pour les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela nous indique qu’un mot se produit dans un document, mais pas là où il se produit dans le document. Pour effectuer une requête d’expression (valeur de mot clé avec guillemets doubles), nous devons comparer la position dans le document pour les mots de l’expression. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expression. Dans ce cas, nous étendons en interne la requête avec tous les mots possibles auxquels le préfixe se développe ; par exemple, `"time*"` peut s’étendre à `"time OR timer OR times OR timex OR timeboxed OR ..."`. Le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête, est de 10 000. Il n’existe aucune limite supérieure pour les termes autres que les termes d’expression.

## <a name="search-times"></a>Heures de recherche

Microsoft collecte des informations sur les performances pour les recherches exécutées par toutes les organisations. Bien que la complexité de la requête de recherche puisse avoir un impact sur les heures de recherche, le facteur le plus important qui détermine la durée de la recherche est le nombre de boîtes aux lettres recherchées. Bien que Microsoft ne fournisse pas de contrat de niveau de service pour les temps de recherche, le tableau suivant répertorie les temps de recherche moyens pour les recherches de regroupement en fonction du nombre de boîtes aux lettres incluses dans la recherche.

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

Le tableau suivant répertorie les limites lors de l’exportation des résultats d’une recherche de contenu. Ces limites s’appliquent également lorsque vous exportez du contenu à partir d’un cas eDiscovery (Standard).

<br>

****

|Description de la limite|Limite|
|---|---|
|Quantité maximale de données exportables à partir d’une seule recherche  <p> **Note:** Si les résultats de la recherche sont supérieurs à 2 To, envisagez d’utiliser des plages de dates ou d’autres types de filtres pour réduire la taille totale des résultats de la recherche.|2 To|
|Nombre maximal d’exportations d’une organisation en une seule journée <p> **Note:** Cette limite est réinitialisée tous les jours à 00:00 UTC|2 To|
|Nombre maximal de boîtes aux lettres pour les résultats de recherche qui peuvent être téléchargés à l’aide de l’outil d’exportation eDiscovery|100 000|
|Taille maximale du fichier PST pouvant être exporté <p> **Note:** Si les résultats de recherche de la boîte aux lettres d’un utilisateur sont supérieurs à 10 Go, les résultats de recherche de la boîte aux lettres sont exportés dans deux fichiers PST distincts (ou plus). Si vous choisissez d’exporter tous les résultats de recherche dans un seul fichier PST, le fichier PST sera placé dans des fichiers PST supplémentaires si la taille totale des résultats de recherche est supérieure à 10 Go. Si vous souhaitez modifier cette taille par défaut, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Voir [Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery](change-the-size-of-pst-files-when-exporting-results.md). Les résultats de recherche d’une boîte aux lettres spécifique ne seront pas répartis entre plusieurs fichiers PST, sauf si le contenu d’une seule boîte aux lettres est supérieur à 10 Go. Si vous avez choisi d’exporter les résultats de la recherche dans un fichier PST pour lequel contient tous les messages d’un dossier unique et que les résultats de recherche sont supérieurs à 10 Go, les éléments sont toujours organisés dans l’ordre chronologique, de sorte qu’ils seront placés dans des fichiers PST supplémentaires en fonction de la date d’envoi.|10 Go|
|Taux auquel les résultats de recherche des boîtes aux lettres et des sites sont chargés vers un emplacement de stockage Azure fourni par Microsoft.|Maximum de 2 Go par heure|

## <a name="indexing-limits-for-email-messages"></a>Limites d’indexation pour les messages électroniques

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le retour d’un message électronique en tant qu’élément non indexé ou élément partiellement indexé dans les résultats d’une recherche de contenu.

<br>

****

|Limite d’indexation|Valeur maximale|Description|
|---|---|---|
|Taille maximale de pièce jointe|150 Mo|Taille maximale d’une pièce jointe d’e-mail qui sera analysée pour l’indexation. Toute pièce jointe supérieure à cette limite ne sera pas analysée pour l’indexation, et le message avec la pièce jointe sera marqué comme partiellement indexé. <p> **Note:** L’analyse est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères inutiles tels que la ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé tokenization), qui sont ensuite stockés dans l’index.|
|Nombre maximal de pièces jointes|250|Nombre maximal de fichiers attachés à un e-mail qui seront analysés pour l’indexation. Si un message comporte plus de 250 pièces jointes, les 250 premières pièces jointes sont analysées et indexées, et le message est marqué comme partiellement indexé, car il contient des pièces jointes supplémentaires qui n’ont pas été analysées.|
|Profondeur maximale de la pièce jointe|30|Nombre maximal de pièces jointes imbriqués analysées. Par exemple, si un message électronique est associé à un autre message et que le message joint comporte un document Word attaché, le document Word et le message joint sont indexés. Ce comportement se poursuivra jusqu’à 30 pièces jointes imbriqués.|
|Nombre maximal d’images jointes|0|Une image attachée à un message électronique est ignorée par l’analyseur et n’est pas indexée.|
|Temps maximal consacré à l’analyse d’un élément|30 secondes|Un maximum de 30 secondes est consacré à l’analyse d’un élément pour l’indexation. Si la durée d’analyse dépasse 30 secondes, l’élément est marqué comme partiellement indexé.|
|Sortie maximale de l’analyseur|2 millions de caractères|Quantité maximale de sortie de texte de l’analyseur indexé. Par exemple, si l’analyseur a extrait 8 millions de caractères d’un document, seuls les 2 premiers millions de caractères sont indexés.|
|Nombre maximal de jetons d’annotation|2 millions|Lorsqu’un e-mail est indexé, chaque mot est annoté avec différentes instructions de traitement qui spécifient comment ce mot doit être indexé. Chaque ensemble d’instructions de traitement est appelé jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions de jetons d’annotation pour un e-mail.|
|Taille maximale du corps dans l’index|67 millions de caractères|Nombre total de caractères dans le corps d’un e-mail et toutes ses pièces jointes. Lorsqu’un e-mail est indexé, tout le texte dans le corps du message et dans toutes les pièces jointes est concaténé en une seule chaîne. La taille maximale de cette chaîne indexée est de 67 millions de caractères.|
|Nombre maximal de jetons uniques dans le corps|1 million|Comme expliqué précédemment, les jetons sont le résultat de l’extraction du texte du contenu, de la suppression de la ponctuation et des espaces, puis de sa division en mots (appelés jetons) stockés dans l’index. Par exemple, l’expression `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seuls 4 d’entre eux sont des jetons uniques. Il existe une limite de 1 million de jetons uniques par e-mail, ce qui permet d’empêcher l’index de devenir trop volumineux avec des jetons aléatoires.|
|||

## <a name="jobs-limits"></a>Limites des travaux

> [!NOTE]
> Les travaux eDiscovery (Premium) sont comptabilisés dans les limites eDiscovery (Standard). Par exemple, si vous avez 50 travaux en cours d’exécution dans eDiscovery (Premium), vous ne pourrez pas démarrer des travaux dans eDiscovery (Standard). Les travaux eDiscovery (Standard) ne sont pas comptabilisés dans les limites eDiscovery (Premium).

|Description|Limite|
|---|---|
|Nombre maximal de travaux simultanés dans votre organisation.|50|
|Nombre maximal de travaux simultanés qu’un seul utilisateur peut démarrer en même temps.|25|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, recherches à l’échelle du locataire) dans votre organisation.|5|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, les recherches à l’échelle du locataire) qu’un seul utilisateur peut démarrer à la fois.|5|
|Nombre maximal de travaux par jour dans votre organisation. <p> **Note:** Cette limite est réinitialisée tous les jours à 00:00 UTC|500|

## <a name="more-information"></a>Plus d’informations

Il existe des limites supplémentaires liées à différents aspects de la recherche de contenu, tels que l’indexation de contenu. Pour plus d’informations sur ces limites, consultez les rubriques suivantes :

- [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md)

- [Examen des éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)

- [Limites de recherche pour SharePoint Online](/sharepoint/search-limits)

Pour plus d’informations sur les recherches de contenu, consultez :

- [Recherche de contenu dans Microsoft 365](content-search.md)

- [Rechercher du contenu dans un cas eDiscovery (Standard)](search-for-content-in-core-ediscovery.md)

- [Requêtes de mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)

Pour connaître les limites de cas liées à eDiscovery (Standard) et eDiscovery (Premium), consultez :

- [Limites dans eDiscovery (Standard)](limits-core-ediscovery.md)

- [Limites dans eDiscovery (Premium)](limits-ediscovery20.md)
