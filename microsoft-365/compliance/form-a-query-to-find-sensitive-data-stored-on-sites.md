---
title: Créer une requête pour trouver des données sensibles stockées sur des sites
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Utilisez la protection contre la perte de données (DLP) dans SharePoint Online pour découvrir les documents qui contiennent des données sensibles dans l’ensemble de votre locataire.
ms.openlocfilehash: 1bb3ed0286f719f9ea9210b4952044081213914f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638320"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Créer une requête pour trouver des données sensibles stockées sur des sites

Les utilisateurs stockent souvent des données sensibles, comme les numéros de cartes de crédit, les numéros de sécurité sociale ou des données personnelles, sur leurs sites, ce qui peut exposer au fil du temps une organisation à un risque significatif de perte de données. Les documents stockés sur des sites, y compris OneDrive Entreprise sites, peuvent être partagés avec des personnes extérieures à l’organisation qui ne devraient pas avoir accès aux informations. Avec Protection contre la perte de données Microsoft Purview (DLP) dans SharePoint Online, vous pouvez découvrir des documents qui contiennent des données sensibles dans l’ensemble de votre locataire. Après avoir découvert les documents, vous pouvez travailler avec leurs propriétaires pour protéger les données. Cette rubrique peut vous aider à créer une requête pour rechercher des données sensibles.

> [!NOTE]
> La découverte électronique, ou eDiscovery, et DLP sont des fonctionnalités premium qui nécessitent [SharePoint Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080).

## <a name="forming-a-basic-dlp-query"></a>Création d'une requête DLP de base

Trois parties composent une requête DLP de base : SensitiveType,  plage de nombre et plage de confiance. Comme illustré dans le graphique suivant, **SensitiveType:"\<type\> »** est obligatoire et les deux **|\<count range\>** sont **|\<confidence range\>** facultatifs.

![Exemple de requête divisé en obligatoire et facultatif.](../media/DLP-query-example-text.png)

### <a name="sensitive-type---required"></a>Type d'informations sensibles - Obligatoire

De quoi est composée chaque partie ? Les requêtes DLP SharePoint commencent généralement par la propriété  `SensitiveType:"` et un nom de type d’informations à partir de [l’inventaire des types d’informations sensibles](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help), et se terminent par un  `"`. Vous pouvez également utiliser le nom d’un [type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md) que vous avez créé pour votre organisation. Par exemple, il se peut que vous recherchiez des documents qui contiennent des numéros de carte de crédit. Dans ce cas, vous utiliseriez le format suivant :  `SensitiveType:"Credit Card Number"`. Étant donné que vous n’avez pas inclus la plage de nombres ou la plage de confiance, la requête retourne chaque document dans lequel un numéro de carte de crédit est détecté. Il s'agit de la requête la plus simple que vous pouvez exécuter et qui renvoie le plus de résultats. Gardez à l'esprit que l'orthographe et l'espacement du type d'informations sensibles sont importants.

### <a name="ranges---optional"></a>Plages - facultatives

Les deux parties suivantes étant des plages, examinons rapidement à quoi ressemble une plage. Dans les requêtes DLP SharePoint, une plage de base est représentée par deux nombres séparés par deux périodes, ce qui ressemble à ceci :  `[number]..[number]`. Par exemple, si  `10..20` elle est utilisée, cette plage capturerait des nombres compris entre 10 et 20. Il existe beaucoup de combinaisons de plage différentes, dont plusieurs sont couvertes par cette rubrique.

Ajoutons une plage de nombres à la requête. Vous pouvez utiliser la plage de nombres pour définir le nombre d’occurrences d’informations sensibles qu’un document doit contenir avant d’être inclus dans les résultats de la requête. Par exemple, si vous souhaitez que votre requête retourne uniquement des documents contenant exactement cinq numéros de carte de crédit, utilisez ce qui suit : `SensitiveType:"Credit Card Number|5"` La plage de nombre peut également vous aider à identifier les documents qui présentent un degré élevé de risque. Par exemple, votre organisation peut examiner les documents comportant cinq numéros de carte de crédit ou plus avec un risque élevé. Pour rechercher des documents correspondant à ce critère, vous devez utiliser cette requête :  `SensitiveType:"Credit Card Number|5.."`. Vous pouvez également trouver des documents avec cinq numéros de carte de crédit ou moins à l’aide de cette requête :  `SensitiveType:"Credit Card Number|..5"`.

#### <a name="confidence-range"></a>Plage de confiance

Enfin, la plage de confiance est le niveau de confiance auquel le type d'informations sensibles détecté correspond réellement. Les valeurs de la plage de confiance fonctionnent de la même manière que celles de la plage de nombre. Vous pouvez créer une requête sans y inclure de plage de nombre. Par exemple, pour rechercher des documents avec un nombre quelconque de numéros de carte de crédit, tant que la plage de confiance est de 85 % ou plus, vous devez utiliser cette requête :  `SensitiveType:"Credit Card Number|*|85.."`.

> [!IMPORTANT]
> L’astérisque ( `*` ) est un caractère générique qui signifie que toute valeur fonctionne. Vous pouvez utiliser le caractère générique ( `*` ) dans la plage de nombres ou dans la plage de confiance, mais pas dans un type sensible.

### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Propriétés de requête supplémentaires et opérateurs de recherche disponibles dans le centre eDiscovery

DLP dans SharePoint introduit également la propriété LastSensitiveContentScan, qui peut vous aider à rechercher des fichiers analysés dans un délai spécifique. Pour obtenir des exemples de requête avec la  `LastSensitiveContentScan` propriété, consultez les [exemples de requêtes complexes](#examples-of-complex-queries) dans la section suivante.

Vous pouvez utiliser non seulement des propriétés spécifiques à DLP pour créer une requête, mais également des propriétés de recherche SharePoint eDiscovery standard telles que  `Author` ou  `FileExtension`. Vous pouvez utiliser des opérateurs pour créer des requêtes complexes. Pour obtenir la liste des propriétés et opérateurs disponibles, consultez le billet de blog [Using Search Properties and Operators with eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) .

## <a name="examples-of-complex-queries"></a>Exemples

Les exemples suivants utilisent différents types, propriétés et opérateurs sensibles pour illustrer la façon dont vous pouvez affiner vos requêtes pour trouver exactement ce que vous recherchez.

<br>

****

|Requête|Explication|
|---|---|
|`SensitiveType:"International Banking Account Number (IBAN)"`|Le nom peut sembler étrange, car il est si long, mais il s’agit du nom approprié pour ce type sensible. Veillez à utiliser les noms exacts de [l’inventaire des types d’informations sensibles](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help). Vous pouvez également utiliser le nom d’un [type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md) que vous avez créé pour votre organisation.|
|`SensitiveType:"Credit Card Number|1..4294967295|1..100"`|Cela renvoie des documents avec au moins une correspondance avec le type sensible « Numéro de carte de crédit ». Les valeurs de chaque plage sont les valeurs minimales et maximales respectives. Un moyen plus simple d’écrire cette requête est  `SensitiveType:"Credit Card Number"`, mais où est le plaisir dans ce?|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"`|Cela renvoie des documents contenant 5 à 25 numéros de carte de crédit analysés du 11 août 2018 au 13 août 2018.|
|`SensitiveType:"Credit Card Number|5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX`|Cela renvoie des documents contenant 5 à 25 numéros de carte de crédit analysés du 11 août 2018 au 13 août 2018. Les fichiers avec une extension XLSX ne sont pas inclus dans les résultats de la requête.  `FileExtension` est l’une des nombreuses propriétés que vous pouvez inclure dans une requête. Pour plus d’informations, consultez [Utilisation des propriétés et opérateurs de recherche avec eDiscovery](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery).|
|`SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"`|Cela renvoie les documents contenant un numéro de carte de crédit ou un numéro de sécurité sociale.|
|

## <a name="examples-of-queries-to-avoid"></a>Exemples

Toutes les requêtes ne sont pas égales. Le tableau suivant fournit des exemples de requêtes qui ne fonctionnent pas avec DLP dans SharePoint et explique pourquoi.

<br>

****

|Requête non prise en charge|Reason|
|---|---|
|`SensitiveType:"Credit Card Number|.."`|Vous devez ajouter au moins un nombre.|
|`SensitiveType:"NotARule"`|« NotARule » n’est pas un nom de type sensible valide. Seuls les noms de [l’inventaire des types d’informations sensibles](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) fonctionnent dans les requêtes DLP.|
|`SensitiveType:"Credit Card Number|0"`|Zéro n’est pas valide en tant que valeur minimale ou valeur maximale dans une plage.|
|`SensitiveType:"Credit Card Number"`|Cela peut être difficile à voir, mais il existe un espace blanc supplémentaire entre « Credit » et « Card » qui rend la requête non valide. Utilisez les noms de types sensibles exacts de [l’inventaire des types d’informations sensibles](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help).|
|`SensitiveType:"Credit Card Number|1. .3"`|La partie à deux périodes ne doit pas être séparée par un espace.|
|`SensitiveType:"Credit Card Number| |1..|80.."`|Il y a trop de délimiteurs de canal (\|). Suivez ce format à la place : `SensitiveType: "Credit Card Number|1..|80.."`|
|`SensitiveType:"Credit Card Number|1..|80..101"`|Étant donné que les valeurs de confiance représentent un pourcentage, elles ne peuvent pas dépasser 100. Choisissez plutôt un nombre compris entre 1 et 100.|
|

## <a name="for-more-information"></a>Pour plus d'informations

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Exécuter une Recherche de Contenu](content-search.md)
- [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)
