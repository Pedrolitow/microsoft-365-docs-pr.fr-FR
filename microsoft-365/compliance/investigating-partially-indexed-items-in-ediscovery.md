---
title: Examen des éléments partiellement indexés dans eDiscovery
description: Découvrez comment gérer les éléments partiellement indexés (également appelés éléments non indexés) à partir d’Exchange, SharePoint et OneDrive Entreprise au sein de votre organisation.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 06/14/2022
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
ms.openlocfilehash: 813841c6c0196b51ad4a64eeb5ae0e4ab4f8a38b
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68687648"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Examen des éléments partiellement indexés dans eDiscovery

Une recherche eDiscovery que vous exécutez à partir du portail de conformité Microsoft Purview inclut automatiquement des éléments partiellement indexés dans les résultats estimés de la recherche lorsque vous exécutez une recherche. Les éléments partiellement indexés sont des éléments de boîte aux lettres Exchange et des documents sur SharePoint et OneDrive Entreprise sites qui, pour une raison quelconque, n’ont pas été complètement indexés pour la recherche. La plupart des messages électroniques et des documents de site sont correctement indexés, car ils entrent dans les [limites d’indexation des messages électroniques](limits-for-content-search.md#indexing-limits-for-email-messages). Toutefois, certains éléments peuvent dépasser ces limites d’indexation et seront partiellement indexés. Voici d’autres raisons pour lesquelles les éléments ne peuvent pas être indexés pour la recherche et sont retournés en tant qu’éléments partiellement indexés lorsque vous exécutez une recherche eDiscovery :
  
- Email messages ont un fichier joint qui ne peut pas être ouvert ; il s’agit de la cause la plus courante d’éléments de courrier partiellement indexés.
- Le nombre de fichiers joints à un message électronique est trop important.
- Un fichier joint à un message électronique est trop volumineux.
- Le type de fichier est pris en charge pour l'indexation, mais une erreur d'indexation s'est produite pour un fichier spécifique.

Bien que cela varie, la plupart des clients des organisations ont moins de 1 % du contenu par volume et moins de 12 % du contenu par taille qui est partiellement indexé. La raison de la différence entre le volume et la taille est que les fichiers plus volumineux ont une probabilité plus élevée de contenir du contenu qui ne peut pas être complètement indexé.

Pour plus d’informations sur les éléments à indexer partiellement dans la recherche de contenu, consultez [Examen des éléments partiellement indexés dans la recherche de contenu](partially-indexed-items-in-content-search.md).
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Pourquoi le nombre d’éléments partiellement indexés change-t-il pour une recherche ?

Après avoir exécuté une recherche eDiscovery, le nombre total et la taille des éléments partiellement indexés dans les emplacements recherchés sont répertoriés dans les statistiques de résultats de recherche affichées dans les statistiques détaillées de la recherche. Notez que ces éléments sont appelés  *éléments non indexés*  dans les statistiques de recherche. Voici quelques éléments qui affecteront le nombre d’éléments partiellement indexés retournés dans les résultats de recherche :
  
- Si un élément est partiellement indexé et correspond à la requête de recherche, il est inclus dans le nombre (et la taille) des éléments de résultats de recherche et des éléments partiellement indexés. Toutefois, lorsque les résultats de cette même recherche sont exportés, l’élément est inclus uniquement avec un ensemble de résultats de recherche ; il n’est pas inclus en tant qu’élément partiellement indexé.
- Les éléments partiellement indexés situés dans les sites SharePoint et OneDrive *ne sont pas* inclus dans l’estimation des éléments partiellement indexés qui sont affichés dans les statistiques détaillées pour la recherche. Toutefois, les éléments partiellement indexés peuvent être exportés lorsque vous exportez les résultats d’une recherche eDiscovery. Par exemple, si vous recherchez uniquement des sites, le nombre estimé d’éléments partiellement indexés sera égal à zéro.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Calcul du ratio des éléments partiellement indexés dans votre organisation

Pour comprendre l’exposition de votre organisation aux éléments partiellement indexés, vous pouvez exécuter une recherche de tout le contenu dans toutes les boîtes aux lettres (à l’aide d’une requête de mot clé vide). Dans l’exemple suivant, il y a 1 629 904 (146,46 Go) d’éléments entièrement indexés et 10 025 (10,27 Go) partiellement indexés.
  
![Exemple de statistiques de recherche montrant des éléments partiellement indexés.](../media/PartiallyIndexedItemsTest.png)
  
Vous pouvez déterminer le pourcentage d’éléments partiellement indexés à l’aide des calculs suivants.
  
 **Pour calculer le ratio d’éléments partiellement indexés dans votre organisation :**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

En utilisant les résultats de recherche de l’exemple précédent, 0,62 % de tous les éléments de boîte aux lettres sont partiellement indexés.
  
 **Pour calculer le pourcentage de taille des éléments partiellement indexés dans votre organisation :**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

Ainsi, dans l’exemple précédent, 7 % de la taille totale des éléments de boîte aux lettres proviennent d’éléments partiellement indexés. Comme indiqué précédemment, la plupart des clients des organisations ont moins de 1 % du contenu par volume et moins de 12 % du contenu par taille qui est partiellement indexé.

## <a name="working-with-partially-indexed-items"></a>Utilisation d’éléments partiellement indexés

Dans les cas où vous devez examiner des éléments partiellement indexés pour vérifier qu’ils ne contiennent pas d’informations pertinentes, vous pouvez [exporter un rapport de recherche de contenu](export-a-content-search-report.md) qui contient des informations sur les éléments partiellement indexés. Lorsque vous exportez un rapport de recherche de contenu, veillez à choisir l’une des options d’exportation qui inclut des éléments partiellement indexés.
  
![Choisissez la deuxième ou la troisième option pour exporter des éléments partiellement indexés.](../media/PartiallyIndexedItemsExportOptions.png)
  
Lorsque vous exportez des résultats de recherche eDiscovery ou un rapport de recherche à l’aide de l’une de ces options, l’exportation inclut un rapport nommé Unindexed Items.csv. Ce rapport contient la plupart des mêmes informations que le fichier ResultsLog.csv ; Toutefois, le fichier de Items.csv non indexé inclut également deux champs liés aux éléments partiellement indexés : **Balises d’erreur** et **Propriétés d’erreur**. Ces champs contiennent des informations sur l’erreur d’indexation pour chaque élément partiellement indexé. L’utilisation des informations contenues dans ces deux champs peut vous aider à déterminer si l’erreur d’indexation d’un particulier a ou non un impact sur votre investigation. 

> [!NOTE]
> Le fichier de Items.csv non indexé contient également des champs nommés **Type d’erreur** et **Message d’erreur**. Il s’agit de champs hérités qui contiennent des informations similaires à celles des **champs Balises d’erreur** et **Propriétés d’erreur** , mais avec des informations moins détaillées. Vous pouvez ignorer en toute sécurité ces champs hérités.
  
## <a name="errors-related-to-partially-indexed-items"></a>Erreurs liées aux éléments partiellement indexés

Les balises d’erreur sont constituées de deux éléments d’informations: l’erreur et le type de fichier. Par exemple, dans cette paire erreur/type de fichier :

```text
 parseroutputsize_xls
```

 `parseroutputsize` est l’erreur et `xls` est le type de fichier du fichier sur lequel l’erreur s’est produite. Dans les cas où le type de fichier n’a pas été reconnu ou si le type de fichier ne s’applique pas à l’erreur, vous verrez la valeur `noformat` à la place du type de fichier.
  
Voici une liste des erreurs d’indexation et une description de la cause possible de l’erreur.
  
| Balise d’erreur | Description |
|:-----|:-----|
| `attachmentcount` <br/> |Un e-mail contient trop de pièces jointes, et certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentdepth` <br/> |Le récupérateur de contenu et l’analyseur de documents ont trouvé trop de niveaux de pièces jointes imbriqués dans d’autres pièces jointes. Certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentrms` <br/> |Le décodage d’une pièce jointe a échoué, car elle était protégée par RMS.  <br/> |
| `attachmentsize` <br/> |Un fichier joint à un e-mail était trop volumineux et n’a pas pu être traité.  <br/> |
| `indexingtruncated` <br/> |Lors de l’écriture du message électronique traité dans l’index, l’une des propriétés indexables était trop volumineuse et tronquée. Les propriétés tronquées sont répertoriées dans le champ Propriétés d’erreur.  <br/> |
| `invalidunicode` <br/> |Un e-mail contenait du texte qui n’a pas pu être traité comme unicode valide. L’indexation de cet élément peut être incomplète.  <br/> |
| `parserencrypted` <br/> |Le contenu de la pièce jointe ou du message électronique est chiffré, et Microsoft 365 n’a pas pu décoder le contenu.  <br/> |
| `parsererror` <br/> |Une erreur inconnue s’est produite lors de l’analyse. Cela résulte généralement d’un bogue logiciel ou d’un incident de service.  <br/> |
| `parserinputsize` <br/> |Une pièce jointe était trop grande pour que l’analyseur le gère, et l’analyse de cette pièce jointe n’a pas eu lieu ou n’a pas été terminée.  <br/> |
| `parsermalformed` <br/> |Une pièce jointe était incorrecte et ne pouvait pas être gérée par l’analyseur. Ce résultat peut être dû à d’anciens formats de fichiers, à des fichiers créés par des logiciels incompatibles ou à des virus prétendant être autre chose que revendiqué.  <br/> |
| `parseroutputsize` <br/> |La sortie de l’analyse d’une pièce jointe était trop grande et a dû être tronquée.  <br/> |
| `parserunknowntype` <br/> |Une pièce jointe avait un type de fichier que Microsoft 365 n’a pas pu détecter.  <br/> |
| `parserunsupportedtype` <br/> |Une pièce jointe avait un type de fichier que Office 365 pouviez détecter, mais l’analyse de ce type de fichier n’est pas prise en charge.  <br/> |
| `propertytoobig` <br/> |La valeur d’une propriété d’e-mail dans Exchange Store était trop importante pour être récupérée et le message n’a pas pu être traité. Cela se produit généralement uniquement pour la propriété body d’un e-mail.  <br/> |
| `retrieverrms` <br/> |Le récupérateur de contenu n’a pas pu décoder un message protégé par RMS.  <br/> |
| `wordbreakertruncated` <br/> |Trop de mots ont été identifiés dans le document pendant l’indexation. Le traitement de la propriété s’est arrêté lors de l’atteinte de la limite et la propriété est tronquée.  <br/> |

Les champs d’erreur décrivent les champs affectés par l’erreur de traitement répertoriée dans le champ Balises d’erreur. Si vous recherchez une propriété telle que  `subject` ou  `participants`, les erreurs dans le corps du message n’ont pas d’impact sur les résultats de votre recherche. Cela peut être utile pour déterminer exactement les éléments partiellement indexés que vous devrez peut-être examiner plus en détail.