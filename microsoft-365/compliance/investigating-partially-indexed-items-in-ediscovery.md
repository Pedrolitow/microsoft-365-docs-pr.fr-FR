---
title: Examen des éléments partiellement indexés dans eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment gérer des éléments partiellement indexés (également appelés éléments non indexés) à partir de Exchange, SharePoint et OneDrive Entreprise au sein de votre organisation.
ms.openlocfilehash: 8dd5235027a4563ad868d8ebe28c8dab50fb6376
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944764"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Examen des éléments partiellement indexés dans eDiscovery

Une recherche eDiscovery que vous exécutez à partir du portail de conformité Microsoft Purview inclut automatiquement des éléments partiellement indexés dans les résultats de recherche estimés lorsque vous exécutez une recherche. Les éléments partiellement indexés sont Exchange des éléments de boîte aux lettres et des documents sur SharePoint et OneDrive Entreprise sites qui, pour une raison quelconque, n’ont pas été entièrement indexés pour la recherche. La plupart des messages électroniques et des documents de site sont correctement indexés, car ils sont dans les [limites d’indexation des messages électroniques](limits-for-content-search.md#indexing-limits-for-email-messages). Toutefois, certains éléments peuvent dépasser ces limites d’indexation et seront partiellement indexés. Voici d’autres raisons pour lesquelles les éléments ne peuvent pas être indexés pour la recherche et sont retournés en tant qu’éléments partiellement indexés lorsque vous exécutez une recherche eDiscovery :
  
- Les messages électroniques ont un fichier joint qui ne peut pas être ouvert, tel que des fichiers image ; il s’agit de la cause la plus courante des éléments de courrier partiellement indexés.

- Le nombre de fichiers joints à un message électronique est trop important.

- Un fichier joint à un message électronique est trop volumineux.

- Le type de fichier est pris en charge pour l'indexation, mais une erreur d'indexation s'est produite pour un fichier spécifique.

Bien qu’elle varie, la plupart des clients d’organisations ont moins de 1 % de contenu par volume et moins de 12 % de contenu par taille partiellement indexée. La raison de la différence entre le volume et la taille est que les fichiers plus volumineux ont une probabilité plus élevée de contenir du contenu qui ne peut pas être entièrement indexé.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Pourquoi le nombre d’éléments partiellement indexés change-t-il pour une recherche ?

Après avoir exécuté une recherche eDiscovery, le nombre total et la taille des éléments partiellement indexés dans les emplacements qui ont été recherchés sont répertoriés dans les statistiques des résultats de recherche qui sont affichées dans les statistiques détaillées de la recherche. Notez que ces éléments sont appelés  *éléments non indexés*  dans les statistiques de recherche. Voici quelques éléments qui affecteront le nombre d’éléments partiellement indexés retournés dans les résultats de la recherche :
  
- Si un élément est partiellement indexé et correspond à la requête de recherche, il est inclus à la fois dans le nombre (et la taille) des éléments de résultats de recherche et des éléments partiellement indexés. Toutefois, lorsque les résultats de cette même recherche sont exportés, l’élément est inclus uniquement avec l’ensemble des résultats de la recherche ; il n’est pas inclus en tant qu’élément partiellement indexé.

- Les éléments partiellement indexés situés dans les sites SharePoint et OneDrive *ne sont pas* inclus dans l’estimation des éléments partiellement indexés affichés dans les statistiques détaillées de la recherche. Toutefois, les éléments partiellement indexés peuvent être exportés lorsque vous exportez les résultats d’une recherche eDiscovery. Par exemple, si vous recherchez uniquement des sites, le nombre estimé d’éléments partiellement indexés est égal à zéro.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Calcul du ratio d’éléments partiellement indexés dans votre organisation

Pour comprendre l’exposition de votre organisation aux éléments partiellement indexés, vous pouvez exécuter une recherche de tout le contenu dans toutes les boîtes aux lettres (à l’aide d’une requête de mot clé vide). Dans l’exemple suivant, il y a 1 629 904 éléments entièrement indexés (146,46 Go) et 10 025 (10,27 Go) d’éléments partiellement indexés.
  
![Exemple de statistiques de recherche montrant des éléments partiellement indexés.](../media/PartiallyIndexedItemsTest.png)
  
Vous pouvez déterminer le pourcentage d’éléments partiellement indexés à l’aide des calculs suivants.
  
 **Pour calculer le ratio des éléments partiellement indexés dans votre organisation :**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

En utilisant les résultats de recherche de l’exemple précédent, 0,62 % de tous les éléments de boîte aux lettres sont partiellement indexés.
  
 **Pour calculer le pourcentage de la taille des éléments partiellement indexés dans votre organisation :**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 GB) x 100 = 7.0%`

Ainsi, dans l’exemple précédent, 7 % de la taille totale des éléments de boîte aux lettres proviennent d’éléments partiellement indexés. Comme indiqué précédemment, la plupart des clients d’organisations ont moins de 1 % de contenu par volume et moins de 12 % de contenu par taille partiellement indexée.

## <a name="working-with-partially-indexed-items"></a>Utilisation d’éléments partiellement indexés

Dans les cas où vous devez examiner des éléments partiellement indexés pour vérifier qu’ils ne contiennent pas d’informations pertinentes, vous pouvez [exporter un rapport de recherche de contenu](export-a-content-search-report.md) qui contient des informations sur les éléments partiellement indexés. Lorsque vous exportez un rapport de recherche de contenu, veillez à choisir l’une des options d’exportation qui inclut des éléments partiellement indexés.
  
![Choisissez la deuxième ou la troisième option pour exporter des éléments partiellement indexés.](../media/PartiallyIndexedItemsExportOptions.png)
  
Lorsque vous exportez des résultats de recherche eDiscovery ou un rapport de recherche à l’aide de l’une de ces options, l’exportation inclut un rapport nommé Items.csv non indexé. Ce rapport contient la plupart des mêmes informations que le fichier ResultsLog.csv ; toutefois, le fichier Items.csv non indexé inclut également deux champs liés aux éléments partiellement indexés : **balises d’erreur** et **propriétés d’erreur**. Ces champs contiennent des informations sur l’erreur d’indexation pour chaque élément partiellement indexé. L’utilisation des informations contenues dans ces deux champs peut vous aider à déterminer si l’erreur d’indexation pour un impact particulier sur votre investigation. 

> [!NOTE]
> Le fichier Items.csv non indexé contient également des champs **nommés Type d’erreur** et **Message d’erreur**. Il s’agit de champs hérités qui contiennent des informations similaires aux informations contenues dans les champs **Étiquettes d’erreur** et **Propriétés d’erreur** , mais avec des informations moins détaillées. Vous pouvez ignorer en toute sécurité ces champs hérités.
  
## <a name="errors-related-to-partially-indexed-items"></a>Erreurs liées aux éléments partiellement indexés

Les balises d’erreur sont constituées de deux éléments d’informations, l’erreur et le type de fichier. Par exemple, dans cette paire erreur/type de fichier :

```text
 parseroutputsize_xls
```

 `parseroutputsize` est l’erreur et `xls` est le type de fichier du fichier sur lequel l’erreur s’est produite. Dans les cas où le type de fichier n’a pas été reconnu ou si le type de fichier ne s’est pas appliqué à l’erreur, vous verrez la valeur `noformat` à la place du type de fichier.
  
Voici une liste d’erreurs d’indexation et une description de la cause possible de l’erreur.
  
| Balise d’erreur | Description |
|:-----|:-----|
| `attachmentcount` <br/> |Un message électronique contient trop de pièces jointes, et certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentdepth` <br/> |Le récupérateur de contenu et l’analyseur de documents ont trouvé trop de niveaux de pièces jointes imbriqués dans d’autres pièces jointes. Certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentrms` <br/> |Échec du décodage d’une pièce jointe, car elle était protégée par RMS.  <br/> |
| `attachmentsize` <br/> |Un fichier attaché à un e-mail était trop volumineux et n’a pas pu être traité.  <br/> |
| `indexingtruncated` <br/> |Lors de l’écriture du message électronique traité dans l’index, l’une des propriétés indexables était trop grande et tronquée. Les propriétés tronquées sont répertoriées dans le champ Propriétés d’erreur.  <br/> |
| `invalidunicode` <br/> |Un message électronique contenait du texte qui n’a pas pu être traité en tant qu’Unicode valide. L’indexation de cet élément peut être incomplète.  <br/> |
| `parserencrypted` <br/> |Le contenu de la pièce jointe ou du message électronique est chiffré et Microsoft 365 n’a pas pu le décoder.  <br/> |
| `parsererror` <br/> |Une erreur inconnue s’est produite lors de l’analyse. Cela résulte généralement d’un bogue logiciel ou d’un incident de service.  <br/> |
| `parserinputsize` <br/> |Une pièce jointe était trop grande pour être gérée par l’analyseur, et l’analyse de cette pièce jointe n’a pas eu lieu ou n’a pas été effectuée.  <br/> |
| `parsermalformed` <br/> |Une pièce jointe a été mal formée et n’a pas pu être gérée par l’analyseur. Ce résultat peut être dû à d’anciens formats de fichiers, à des fichiers créés par des logiciels incompatibles ou à des virus faisant semblant d’être autre chose que revendiqué.  <br/> |
| `parseroutputsize` <br/> |La sortie de l’analyse d’une pièce jointe était trop grande et devait être tronquée.  <br/> |
| `parserunknowntype` <br/> |Une pièce jointe avait un type de fichier que Microsoft 365 n’a pas pu détecter.  <br/> |
| `parserunsupportedtype` <br/> |Une pièce jointe avait un type de fichier que Office 365 pouvait détecter, mais l’analyse de ce type de fichier n’est pas prise en charge.  <br/> |
| `propertytoobig` <br/> |La valeur d’une propriété de messagerie dans Exchange Store était trop grande pour être récupérée et le message n’a pas pu être traité. Cela se produit généralement uniquement pour la propriété de corps d’un e-mail.  <br/> |
| `retrieverrms` <br/> |Le récupérateur de contenu n’a pas pu décoder un message protégé par RMS.  <br/> |
| `wordbreakertruncated` <br/> |Trop de mots ont été identifiés dans le document lors de l’indexation. Le traitement de la propriété s’est arrêté lorsque vous atteignez la limite, et la propriété est tronquée.  <br/> |

Les champs d’erreur décrivent les champs affectés par l’erreur de traitement répertoriée dans le champ Étiquettes d’erreur. Si vous effectuez une recherche dans une propriété telle que  `subject` ou  `participants`, les erreurs dans le corps du message n’ont pas d’impact sur les résultats de votre recherche. Cela peut être utile pour déterminer exactement quels éléments partiellement indexés vous devrez peut-être examiner plus en détail.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>Utilisation d’un script PowerShell pour déterminer l’exposition de votre organisation aux éléments de messagerie partiellement indexés

Les étapes suivantes vous montrent comment exécuter un script PowerShell qui recherche tous les éléments dans toutes les boîtes aux lettres Exchange, puis génère un rapport sur le ratio d’éléments de courrier partiellement indexés de votre organisation (par nombre et par taille) et affiche le nombre d’éléments (et leur type de fichier) pour chaque erreur d’indexation qui se produit. Utilisez les descriptions des balises d’erreur dans la section précédente pour identifier l’erreur d’indexation.
  
1. Enregistrez le texte suivant dans un fichier de script Windows PowerShell à l’aide d’un suffixe de nom de fichier de .ps1 ; par exemple, `PartiallyIndexedItems.ps1`.

   ```powershell
     write-host "**************************************************"
     write-host "     Security & Compliance Center PowerShell      " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "   eDiscovery Partially Indexed Item Statistics   " -foregroundColor yellow -backgroundcolor darkgreen
     write-host "**************************************************"
     " " 
     # Create a search with Error Tags Refinders enabled
     Remove-ComplianceSearch "RefinerTest" -Confirm:$false -ErrorAction 'SilentlyContinue'
     New-ComplianceSearch -Name "RefinerTest" -ContentMatchQuery "size>0" -RefinerNames ErrorTags -ExchangeLocation ALL
     Start-ComplianceSearch "RefinerTest"
     # Loop while search is in progress
     do{
         Write-host "Waiting for search to complete..."
         Start-Sleep -s 5
         $complianceSearch = Get-ComplianceSearch "RefinerTest"
     }while ($complianceSearch.Status -ne 'Completed')
     $refiners = $complianceSearch.Refiners | ConvertFrom-Json
     $errorTagProperties = $refiners.Entries | Get-Member -MemberType NoteProperty
     $partiallyIndexedRatio = $complianceSearch.UnindexedItems / $complianceSearch.Items
     $partiallyIndexedSizeRatio = $complianceSearch.UnindexedSize / $complianceSearch.Size
     " "
     "===== Partially indexed items ====="
     "         Total          Ratio"
     "Count    {0:N0}{1:P2}" -f $complianceSearch.Items.ToString("N0").PadRight(15, " "), $partiallyIndexedRatio
     "Size(GB) {0:N2}{1:P2}" -f ($complianceSearch.Size / 1GB).ToString("N2").PadRight(15, " "), $partiallyIndexedSizeRatio
     " "
     Write-Host ===== Reasons for partially indexed items =====
     foreach($errorTagProperty in $errorTagProperties)
     {
         $name = $refiners.Entries.($errorTagProperty.Name).Name
         $count = $refiners.Entries.($errorTagProperty.Name).TotalCount
         $frag = $name.Split("{_}")
         $errorTag = $frag[0]
         $fileType = $frag[1]
         if ($errorTag -ne $lastErrorTag)
         {
             $errorTag
         }
         "    " + $fileType + " => " + $count
         $lastErrorTag = $errorTag
     }
   ```

2. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/exchange-online-powershell).

3. Dans Security & Compliance Center PowerShell, accédez au dossier dans lequel vous avez enregistré le script à l’étape 1, puis exécutez le script ; par exemple :

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Voici un exemple de sortie retournée par le script.
  
![Exemple de sortie à partir d’un script qui génère un rapport sur l’exposition de votre organisation à des éléments de messagerie partiellement indexés.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Veuillez prendre en compte les éléments suivants:
>  
> - Le nombre total et la taille des éléments de messagerie, ainsi que le rapport entre les éléments de messagerie partiellement indexés de votre organisation (par nombre et par taille).
> 
> - Balises d’erreur de liste et types de fichiers correspondants pour lesquels l’erreur s’est produite.
  
## <a name="see-also"></a>Voir aussi

[Éléments partiellement indexés dans eDiscovery](partially-indexed-items-in-content-search.md)
