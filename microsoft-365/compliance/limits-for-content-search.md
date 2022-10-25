---
title: Limites pour la recherche de contenu et eDiscovery (Standard) dans le portail de conformité Microsoft Purview
description: Découvrez les limites en vigueur pour les fonctionnalités recherche de contenu et eDiscovery (Standard) dans le portail de conformité Microsoft Purview.
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
ms.openlocfilehash: 5933a232f9e91f2a0300f6a9fceb6543262cce33
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688129"
---
# <a name="limits-for-content-search-and-ediscovery-standard"></a>Limites pour la recherche de contenu et l’eDiscovery (Standard)

Différentes limites sont appliquées aux outils de recherche eDiscovery dans le portail de conformité Microsoft Purview. Cela inclut les recherches exécutées sur la page **de recherche de contenu** et les recherches associées à un cas eDiscovery sur la page **eDiscovery (Standard).** Ces limites aident à maintenir l’intégrité et la qualité des services fournis aux organisations. Il existe également des limites liées à l’indexation des messages électroniques dans Exchange Online pour la recherche. Vous ne pouvez pas modifier les limites pour les recherches eDiscovery ou l’indexation des e-mails, mais vous devez les connaître afin de pouvoir prendre ces limites en considération lors de la planification, de l’exécution et de la résolution des problèmes des recherches eDiscovery.

Pour connaître les limites liées à l’outil Microsoft Purview eDiscovery (Premium), consultez [Limites dans eDiscovery (Premium)](limits-ediscovery20.md)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="search-limits"></a>Limites de la recherche

Le tableau suivant répertorie les limites de recherche lors de l’utilisation de l’outil de recherche de contenu dans le portail de conformité et pour les recherches associées à un cas Microsoft Purview eDiscovery (Standard).

<br>

****

|Description de la limite|Limite|
|---|---|
|Nombre maximal de boîtes aux lettres ou de sites pouvant faire l’objet d’une recherche en une seule recherche|Aucune limite <sup>1</sup>|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres utilisateur qui peuvent éventuellement être affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche. Les éléments les plus récents sont affichés.|1 000 <sup>2</sup>|
|Nombre maximal de boîtes aux lettres d’utilisateur dont vous pouvez afficher un aperçu des résultats de recherche. Si plus de 1 000 boîtes aux lettres contiennent du contenu qui correspond à la requête de recherche, seules les 1 000 boîtes aux lettres avec le plus de résultats de recherche sont disponibles en préversion.|1 000|
|Nombre maximal d’éléments trouvés dans SharePoint et OneDrive Entreprise sites qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de recherche. Les éléments les plus récents sont affichés.|200 |
|Nombre maximal de sites (dans SharePoint et OneDrive Entreprise) qui peuvent être aperçus pour les résultats de recherche. Si plus de 200 sites au total contiennent du contenu correspondant à la requête de recherche, seuls les 200 premiers sites avec le plus de résultats de recherche seront disponibles en préversion.|200 |
|Nombre maximal d’éléments par boîte aux lettres de dossiers publics affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche de contenu.|100|
|Nombre maximal d’éléments trouvés dans toutes les boîtes aux lettres de dossiers publics qui sont affichés sur la page d’aperçu lors de l’aperçu des résultats de la recherche de contenu.|200 |
|Nombre maximal de boîtes aux lettres de dossiers publics qui peuvent être prévisualisés pour les résultats de la recherche. S’il existe plus de 500 boîtes aux lettres de dossiers publics qui contiennent du contenu correspondant à la requête de recherche, seules les 500 boîtes aux lettres de dossiers publics les plus avancées seront disponibles en préversion.|500|
|Taille maximale d’un élément qui peut être affiché sur la page d’aperçu.|10 000 000 octets (environ 9,5 Mo)|
|Nombre maximal de caractères pour la requête de recherche (y compris les opérateurs et les conditions) pour une recherche. <p> **Note:** Cette limite prend effet une fois que la requête a été développée et inclut les caractères de la requête de mot clé, les filtres d’autorisations de recherche appliqués à l’utilisateur et les URL de tous les emplacements de site. Cela signifie que la requête est développée par rapport à chacun des mots clés. Par exemple, si une requête de recherche a 15 mots clés et des paramètres et conditions supplémentaires, la requête est développée 15 fois, chacune avec les autres paramètres et conditions de la requête. Ainsi, même si le nombre de caractères dans la requête de recherche peut être inférieur à la limite, c’est la requête développée qui peut contribuer à dépasser cette limite.|**Boîtes aux lettres :** 10 000. <p> **Sites :** 4 000 lors de la recherche de tous les sites ou 2 000 lors de la recherche de jusqu’à 20 sites. <sup>3</sup>|
|Nombre maximal de variantes retournées lors de l’utilisation d’un caractère générique de préfixe pour rechercher une expression exacte dans une requête de recherche ou lors de l’utilisation d’un caractère générique de préfixe et de l’opérateur booléen **NEAR** .|10 000 <sup>4</sup>|
|Nombre minimal de caractères alpha pour les caractères génériques de préfixe ; par exemple, `time*`, `one*`ou `set*`.|3|
|Nombre maximal de boîtes aux lettres dans une recherche dans lesquelles vous pouvez supprimer des éléments en effectuant une action « rechercher et vider » (à l’aide de la commande **New-ComplianceSearchAction -Purge** ). Si la recherche pour laquelle vous effectuez une action de vidage a plus de boîtes aux lettres sources que cette limite, l’action de vidage échoue. Pour plus d’informations sur la recherche et le vidage, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).|50 000|
|Nombre maximal d’emplacements dans une recherche à partir lesquels vous pouvez exporter des éléments. Si la recherche que vous exportez a plus d’emplacements que cette limite, l’exportation échoue. Pour plus d’informations, consultez [Exporter les résultats de la recherche de contenu](export-search-results.md).|100 000|

> [!NOTE]
> <sup>1</sup> Bien que vous puissiez rechercher un nombre illimité de boîtes aux lettres dans une seule recherche, vous pouvez uniquement télécharger les résultats de recherche exportés à partir d’un maximum de 100 000 boîtes aux lettres à l’aide de l’outil d’exportation eDiscovery dans le portail de conformité.
>
> <sup>2</sup> L’objectif de la page d’aperçu est d’afficher un échantillon limité des résultats. Même pour les recherches massives avec des milliers de résultats, le nombre d’éléments affichés sur la page d’aperçu peut, et souvent, être bien inférieur à la valeur maximale possible de 1 000. Pour afficher les résultats de la recherche complète, vous devez exporter les résultats.
>
> <sup>3 Lors de</sup> la recherche dans SharePoint et OneDrive Entreprise emplacements, les caractères dans les URL des sites recherchés sont comptabilisés par rapport à cette limite.
>
> <sup>4</sup> Pour les requêtes sans expression (valeur de mot clé qui n’utilise pas de guillemets doubles), nous utilisons un index de préfixe spécial. Cela nous indique qu’un mot se produit dans un document, mais pas là où il se trouve dans le document. Pour effectuer une requête d’expression (valeur de mot clé avec des guillemets doubles), nous devons comparer la position dans le document pour les mots de l’expression. Cela signifie que nous ne pouvons pas utiliser l’index de préfixe pour les requêtes d’expression. Dans ce cas, nous développons en interne la requête avec tous les mots possibles auxquels le préfixe s’étend ; par exemple, `"time*"` peut développer jusqu’à `"time OR timer OR times OR timex OR timeboxed OR ..."`. Le nombre maximal de variantes que le mot peut développer, et non le nombre de documents correspondant à la requête, est de 10 000. Il n’existe aucune limite supérieure pour les termes sans expression.

## <a name="search-times"></a>Durées de recherche

Microsoft collecte des informations sur les performances pour les recherches exécutées par toutes les organisations. Bien que la complexité de la requête de recherche puisse avoir un impact sur les heures de recherche, le facteur le plus important qui détermine la durée de la recherche est le nombre de boîtes aux lettres recherchées. Bien que Microsoft ne fournisse pas de contrat de niveau de service pour les durées de recherche, le tableau suivant répertorie les temps de recherche moyens pour les recherches de collections en fonction du nombre de boîtes aux lettres incluses dans la recherche.

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
|Nombre maximal qu’une organisation peut exporter en une seule journée <p> **Note:** Cette limite est réinitialisée quotidiennement à 00:00 UTC|2 To|
|Nombre maximal de boîtes aux lettres pour les résultats de recherche qui peuvent être téléchargés à l’aide de l’outil d’exportation eDiscovery|100 000|
|Taille maximale du fichier PST pouvant être exporté <p> **Note:** Si les résultats de la recherche de la boîte aux lettres d’un utilisateur sont supérieurs à 10 Go, les résultats de la recherche de la boîte aux lettres sont exportés dans deux fichiers PST distincts (ou plus). Si vous choisissez d’exporter tous les résultats de recherche dans un seul fichier PST, le fichier PST est injecté dans des fichiers PST supplémentaires si la taille totale des résultats de la recherche est supérieure à 10 Go. Si vous souhaitez modifier cette taille par défaut, vous pouvez modifier le Registre Windows sur l’ordinateur que vous utilisez pour exporter les résultats de la recherche. Consultez [Modifier la taille des fichiers PST lors de l’exportation des résultats de recherche eDiscovery](change-the-size-of-pst-files-when-exporting-results.md). Les résultats de la recherche d’une boîte aux lettres spécifique ne sont pas divisés entre plusieurs fichiers PST, sauf si le contenu d’une même boîte aux lettres est supérieur à 10 Go. Si vous avez choisi d’exporter les résultats de la recherche dans un fichier PST pour qui contient tous les messages dans un seul dossier et que les résultats de la recherche sont supérieurs à 10 Go, les éléments sont toujours organisés dans l’ordre chronologique, de sorte qu’ils seront redirigés dans des fichiers PST supplémentaires en fonction de la date d’envoi.|10 Go|
|Fréquence à laquelle les résultats de recherche des boîtes aux lettres et des sites sont chargés vers un emplacement de stockage Azure fourni par Microsoft.|Maximum de 2 Go par heure|

## <a name="indexing-limits-for-email-messages"></a>Limites d’indexation des messages électroniques

Le tableau suivant décrit les limites d’indexation qui peuvent entraîner le renvoi d’un e-mail en tant qu’élément non indexé ou partiellement indexé dans les résultats d’une recherche de contenu.

<br>

****

|Limite d’indexation|Valeur maximale|Description|
|---|---|---|
|Taille maximale de pièce jointe|150 Mo|Taille maximale d’une pièce jointe à analyser pour l’indexation. Toute pièce jointe supérieure à cette limite ne sera pas analysée pour l’indexation, et le message avec la pièce jointe sera marqué comme partiellement indexé. <p> **Note:** L’analyse est le processus dans lequel le service d’indexation extrait le texte de la pièce jointe, supprime les caractères inutiles tels que la ponctuation et les espaces, puis divise le texte en mots (dans un processus appelé tokenisation), qui sont ensuite stockés dans l’index.|
|Nombre maximal de pièces jointes|250|Nombre maximal de fichiers joints à un e-mail qui seront analysés pour l’indexation. Si un message comporte plus de 250 pièces jointes, les 250 premières pièces jointes sont analysées et indexées, et le message est marqué comme partiellement indexé, car il contient des pièces jointes supplémentaires qui n’ont pas été analysées.|
|Profondeur maximale de la pièce jointe|30|Nombre maximal de pièces jointes imbriquées analysées. Par exemple, si un message électronique comporte un autre message joint et que le message joint a un document Word joint, le document Word et le message joint sont indexés. Ce comportement se poursuit pour jusqu’à 30 pièces jointes imbriquées.|
|Nombre maximal d’images attachées|0|Une image jointe à un e-mail est ignorée par l’analyseur et n’est pas indexée.|
|Temps maximal consacré à l’analyse d’un élément|30 secondes|Un maximum de 30 secondes est consacré à l’analyse d’un élément pour l’indexation. Si le temps d’analyse dépasse 30 secondes, l’élément est marqué comme partiellement indexé.|
|Sortie maximale de l’analyseur|2 millions de caractères|Quantité maximale de sortie de texte de l’analyseur indexé. Par exemple, si l’analyseur a extrait 8 millions de caractères d’un document, seuls les 2 premiers millions de caractères sont indexés.|
|Nombre maximal de jetons d’annotation|2 millions|Lorsqu’un message électronique est indexé, chaque mot est annoté avec des instructions de traitement différentes qui spécifient comment ce mot doit être indexé. Chaque ensemble d’instructions de traitement est appelé jeton d’annotation. Pour maintenir la qualité de service dans Office 365, il existe une limite de 2 millions de jetons d’annotation pour un e-mail.|
|Taille maximale du corps dans l’index|67 millions de caractères|Nombre total de caractères dans le corps d’un message électronique et de toutes ses pièces jointes. Lorsqu’un e-mail est indexé, tout le texte dans le corps du message et dans toutes les pièces jointes est concaténé en une seule chaîne. La taille maximale de cette chaîne indexée est de 67 millions de caractères.|
|Nombre maximal de jetons uniques dans le corps|1 million|Comme expliqué précédemment, les jetons sont le résultat de l’extraction de texte du contenu, de la suppression de la ponctuation et des espaces, puis de sa division en mots (appelés jetons) qui sont stockés dans l’index. Par exemple, l’expression `"cat, mouse, bird, dog, dog"` contient 5 jetons. Mais seulement 4 d’entre eux sont des jetons uniques. Il existe une limite de 1 million de jetons uniques par e-mail, ce qui permet d’éviter que l’index ne soit trop volumineux avec des jetons aléatoires.|
|||

## <a name="jobs-limits"></a>Limites des travaux

|Description|Limite|
|:----------|:----|
|Nombre maximal de travaux simultanés dans votre organisation.|50|
|Nombre maximal de travaux simultanés qu’un seul utilisateur peut démarrer en même temps.|25|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, des recherches à l’échelle du locataire) dans votre organisation.|5|
|Nombre maximal de travaux simultanés à l’échelle du locataire (par exemple, des recherches à l’échelle du locataire) qu’un seul utilisateur peut démarrer en une seule fois.|5|
|Nombre maximal de travaux par jour dans votre organisation. <p> **Note:** Cette limite est réinitialisée quotidiennement à 00:00 UTC|500|

## <a name="more-information"></a>Plus d’informations

Il existe des limites supplémentaires liées à différents aspects de la recherche de contenu, comme l’indexation de contenu. Pour plus d’informations sur ces limites, consultez les articles suivants :

- [Éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md)
- [Examen des éléments partiellement indexés dans eDiscovery](investigating-partially-indexed-items-in-ediscovery.md)
- [Limites de recherche pour SharePoint Online](/sharepoint/search-limits)

Pour plus d’informations sur les recherches de contenu, consultez :

- [Recherche de contenu dans Microsoft 365](content-search.md)
- [Rechercher du contenu dans un cas eDiscovery (Standard)](search-for-content-in-core-ediscovery.md)
- [Requêtes par mot clé et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)

Pour connaître les limites de cas liées à eDiscovery (Standard) et eDiscovery (Premium), consultez :

- [Limites dans eDiscovery (Standard)](limits-core-ediscovery.md)
- [Limites dans eDiscovery (Premium)](limits-ediscovery20.md)
