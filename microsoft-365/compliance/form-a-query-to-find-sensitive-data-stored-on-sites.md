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
localization_priority: Normal
search.appverid:
- MOE150
- MET150
description: Utilisez la protection contre la perte de données (DLP) dans SharePoint Online pour découvrir les documents qui contiennent des données sensibles dans l’ensemble de votre client.
ms.openlocfilehash: 9582974a26e0e112a6b3851494d057cad2010796
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50906778"
---
# <a name="form-a-query-to-find-sensitive-data-stored-on-sites"></a>Créer une requête pour trouver des données sensibles stockées sur des sites

Les utilisateurs stockent souvent des données sensibles, comme les numéros de cartes de crédit, les numéros de sécurité sociale ou des données personnelles, sur leurs sites, ce qui peut exposer au fil du temps une organisation à un risque significatif de perte de données. Les documents stockés sur des sites, y compris OneDrive Entreprise sites, peuvent être partagés avec des personnes extérieures à l’organisation qui ne devraient pas avoir accès aux informations. Avec la protection contre la perte de données (DLP) dans SharePoint Online, vous pouvez découvrir des documents qui contiennent des données sensibles dans l’ensemble de votre client. Après avoir découvert les documents, vous pouvez travailler avec leurs propriétaires pour protéger les données. Cette rubrique peut vous aider à créer une requête pour rechercher des données sensibles.
  
> [!NOTE]
> La découverte électronique, ou eDiscovery, et DLP sont des fonctionnalités premium qui SharePoint [Online Plan 2](https://go.microsoft.com/fwlink/?LinkId=510080). 
  
## <a name="forming-a-basic-dlp-query"></a>Création d'une requête DLP de base

Trois parties composent une requête DLP de base : SensitiveType,  plage de nombre et plage de confiance. Comme illustré dans le graphique suivant, **SensitiveType: \<type\> " est** obligatoire, et les deux et **|\<count range\>** sont **|\<confidence range\>** facultatifs. 
  
![Exemple de requête divisée en obligatoire et facultative](../media/DLP-query-example-text.png)
  
### <a name="sensitive-type---required"></a>Type d'informations sensibles - Obligatoire

De quoi est composée chaque partie ? SharePoint Les requêtes DLP commencent généralement par la propriété et un nom de type d’informations à partir de l’inventaire des types d’informations sensibles `SensitiveType:"` et se terminent par un [](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) `"` . Vous pouvez également utiliser le nom d’un [type d’informations](create-a-custom-sensitive-information-type.md) sensibles personnalisé que vous avez créé pour votre organisation. Par exemple, il se peut que vous recherchiez des documents qui contiennent des numéros de carte de crédit. Dans ce cas, vous devez utiliser le format suivant  `SensitiveType:"Credit Card Number"` : Étant donné que vous n’avez pas inclus de plage de nombre ou de plage de confiance, la requête renvoie chaque document dans lequel un numéro de carte de crédit est détecté. Il s'agit de la requête la plus simple que vous pouvez exécuter et qui renvoie le plus de résultats. Gardez à l'esprit que l'orthographe et l'espacement du type d'informations sensibles sont importants. 
  
### <a name="ranges---optional"></a>Plages - facultatives

Les deux parties suivantes sont des plages. Nous allons donc rapidement examiner à quoi ressemble une plage. Dans SharePoint requêtes DLP, une plage de base est représentée par deux nombres séparés par deux points, ce qui ressemble à `[number]..[number]` ceci : Par exemple, si elle est utilisée, cette plage capture des nombres de  `10..20` 10 à 20. Il existe beaucoup de combinaisons de plage différentes, dont plusieurs sont couvertes par cette rubrique. 
  
Nous allons ajouter une plage de nombres à la requête. Vous pouvez utiliser la plage de nombres pour définir le nombre d’occurrences d’informations sensibles qu’un document doit contenir avant d’être inclus dans les résultats de la requête. Par exemple, si vous souhaitez que votre requête retourne uniquement les documents qui contiennent exactement cinq numéros de carte de crédit, utilisez ceci  `SensitiveType:"Credit Card Number|5"` : La plage de nombre peut également vous aider à identifier les documents qui présentent un degré élevé de risque. Par exemple, votre organisation peut examiner les documents comportant cinq numéros de carte de crédit ou plus avec un risque élevé. Pour rechercher des documents qui s’y trouvent, vous devez utiliser cette requête  `SensitiveType:"Credit Card Number|5.."` : Vous pouvez également trouver des documents avec cinq numéros de carte de crédit ou moins à l’aide de cette requête  `SensitiveType:"Credit Card Number|..5"` : 
  
#### <a name="confidence-range"></a>Plage de confiance

Enfin, la plage de confiance est le niveau de confiance auquel le type d'informations sensibles détecté correspond réellement. Les valeurs de la plage de confiance fonctionnent de la même manière que celles de la plage de nombre. Vous pouvez créer une requête sans y inclure de plage de nombre. Par exemple, pour rechercher des documents avec un nombre quelconque de numéros de carte de crédit, tant que la plage de confiance est supérieure ou supérieure à 85 pour cent, utilisez cette requête  `SensitiveType:"Credit Card Number|*|85.."` : 
  
> [!IMPORTANT]
> L’astérisque ( `*` ) est un caractère générique qui signifie que n’importe quelle valeur fonctionne. Vous pouvez utiliser le caractère générique ( ) dans la plage de nombre ou dans la plage de confiance, mais pas `*` dans un type sensible. 
  
### <a name="additional-query-properties-and-search-operators-available-in-the-ediscovery-center"></a>Propriétés de requête supplémentaires et opérateurs de recherche disponibles dans le centre eDiscovery

DLP dans SharePoint présente également la propriété LastSensitiveContentScan, qui peut vous aider à rechercher des fichiers analysés au cours d’une période spécifique. Pour obtenir des exemples de requête avec la propriété, voir les exemples de requêtes complexes `LastSensitiveContentScan` dans la section suivante. [](#examples-of-complex-queries) 
  
Vous pouvez utiliser non seulement des propriétés spécifiques à DLP pour créer une requête, mais également des propriétés de SharePoint eDiscovery standard telles `Author` que ou `FileExtension` . Vous pouvez utiliser des opérateurs pour créer des requêtes complexes. Pour obtenir la liste des propriétés et des opérateurs disponibles, consultez le billet de blog Utilisation des propriétés et opérateurs de recherche avec [eDiscovery.](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery) 
  
## <a name="examples-of-complex-queries"></a>Exemples

Les exemples suivants utilisent différents types sensibles, propriétés et opérateurs pour illustrer comment affiner vos requêtes afin de trouver exactement ce que vous recherchez.
  
|**Query**|**Explication**|
|:-----|:-----|
| `SensitiveType:"International Banking Account Number (IBAN)"` <br/> |Le nom peut sembler étrange car il est trop long, mais il s’agit du nom correct pour ce type sensible. Veillez à utiliser les noms exacts de [l’inventaire des types d’informations sensibles.](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) Vous pouvez également utiliser le nom d’un [type d’informations](create-a-custom-sensitive-information-type.md) sensibles personnalisé que vous avez créé pour votre organisation.  <br/> |
| `SensitiveType:"Credit Card Number|1..4294967295|1..100"` <br/> |Cela renvoie des documents avec au moins une correspondance avec le type sensible « Numéro de carte de crédit ». Les valeurs de chaque plage sont les valeurs minimales et maximales respectives. Une façon plus simple d’écrire cette requête est, mais où est  `SensitiveType:"Credit Card Number"` le plaisir ?  <br/> |
| `SensitiveType:"Credit Card Number| 5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018"` <br/> |Cela renvoie des documents avec 5 à 25 numéros de carte de crédit qui ont été analysés du 11 août 2018 au 13 août 2018.  <br/> |
| `SensitiveType:"Credit Card Number| 5..25" AND LastSensitiveContentScan:"8/11/2018..8/13/2018" NOT FileExtension:XLSX` <br/> |Cela renvoie des documents avec 5 à 25 numéros de carte de crédit qui ont été analysés du 11 août 2018 au 13 août 2018. Les fichiers avec une extension XLSX ne sont pas inclus dans les résultats de la requête.  `FileExtension` est l’une des nombreuses propriétés que vous pouvez inclure dans une requête. Pour plus d’informations, voir [Utilisation des propriétés et opérateurs de recherche avec eDiscovery.](/archive/blogs/quentin/using-search-properties-and-operators-with-ediscovery)  <br/> |
| `SensitiveType:"Credit Card Number" OR SensitiveType:"U.S. Social Security Number (SSN)"` <br/> |Cela renvoie les documents contenant un numéro de carte de crédit ou un numéro de sécurité sociale.  <br/> |
   
## <a name="examples-of-queries-to-avoid"></a>Exemples

Toutes les requêtes ne sont pas égales. Le tableau suivant donne des exemples de requêtes qui ne fonctionnent pas avec la DLP SharePoint et décrit pourquoi.
  
|**Requête non prise en charge**|**Raison**|
|:-----|:-----|
| `SensitiveType:"Credit Card Number|.."` <br/> |Vous devez ajouter au moins un nombre.  <br/> |
| `SensitiveType:"NotARule"` <br/> |« NotARule » n’est pas un nom de type sensible valide. Seuls les noms dans [l’inventaire des types d’informations sensibles](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help) fonctionnent dans les requêtes DLP.  <br/> |
| `SensitiveType:"Credit Card Number|0"` <br/> |Zéro n’est pas valide en tant que valeur minimale ou valeur maximale d’une plage.  <br/> |
| `SensitiveType:"Credit Card Number"` <br/> |Cela peut être difficile à voir, mais il existe un espace supplémentaire entre « Crédit » et « Carte » qui rend la requête non valide. Utilisez des noms de types sensibles exacts de [l’inventaire des types d’informations sensibles.](/Exchange/what-the-sensitive-information-types-in-exchange-look-for-exchange-2013-help)  <br/> |
| `SensitiveType:"Credit Card Number|1. .3"` <br/> |La partie à deux points ne doit pas être séparée par un espace.  <br/> |
| `SensitiveType:"Credit Card Number| |1..|80.."` <br/> |Il y a trop de délimiteur de canal (|). Suivez plutôt ce format : `SensitiveType: "Credit Card Number|1..|80.."` <br/> |
| `SensitiveType:"Credit Card Number|1..|80..101"` <br/> |Étant donné que les valeurs de confiance représentent un pourcentage, elles ne peuvent pas dépasser 100. Choisissez plutôt un nombre compris entre 1 et 100.  <br/> |
   
## <a name="for-more-information"></a>Pour plus d'informations

- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)
- [Exécuter une Recherche de Contenu](content-search.md)
- [Requêtes par mots clés et conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md)
