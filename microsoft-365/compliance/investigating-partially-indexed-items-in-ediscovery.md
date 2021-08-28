---
title: Recherche d’éléments partiellement indexés dans eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 4e8ff113-6361-41e2-915a-6338a7e2a1ed
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment gérer des éléments partiellement indexés (également appelés éléments non indexés) à partir de Exchange, SharePoint et OneDrive Entreprise au sein de votre organisation.
ms.openlocfilehash: f578b5ba4b89338c5d6ef861b20d42c4aebbb3b2
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574170"
---
# <a name="investigating-partially-indexed-items-in-ediscovery"></a>Recherche d’éléments partiellement indexés dans eDiscovery

Une recherche de découverte électronique que vous exécutez à partir du Centre de conformité Microsoft 365 inclut automatiquement des éléments partiellement indexés dans les résultats de recherche estimés lorsque vous exécutez une recherche. Les éléments partiellement indexés sont des Exchange de boîtes aux lettres et des documents sur des sites SharePoint et OneDrive Entreprise qui, pour une raison quelconque, n’ont pas été complètement indexés pour la recherche. La plupart des messages électroniques et des documents de site sont indexés avec succès, car ils se limitent aux [limites d’indexation des messages électroniques.](limits-for-content-search.md#indexing-limits-for-email-messages) Toutefois, certains éléments peuvent dépasser ces limites d’indexation et seront partiellement indexés. Voici d’autres raisons pour lesquelles les éléments ne peuvent pas être indexés pour la recherche et sont renvoyés en tant qu’éléments partiellement indexés lorsque vous exécutez une recherche de découverte électronique :
  
- Les messages électroniques ont un fichier joint sans un handler valide, tel que des fichiers image ; Il s’agit de la cause la plus courante des éléments de courrier partiellement indexés.

- Le nombre de fichiers joints à un message électronique est trop important.

- Un fichier joint à un message électronique est trop volumineux.

- Le type de fichier est pris en charge pour l'indexation, mais une erreur d'indexation s'est produite pour un fichier spécifique.

Bien que cela varie, la plupart des clients d’organisations ont moins de 1 % de contenu par volume et moins de 12 % de contenu par taille partiellement indexée. La différence entre le volume et la taille est dû au fait que les fichiers plus volumineux ont une probabilité plus élevée de contenir du contenu qui ne peut pas être complètement indexé.
  
## <a name="why-does-the-partially-indexed-item-count-change-for-a-search"></a>Pourquoi le nombre d’éléments partiellement indexés change-t-il pour une recherche ?

Après avoir exécuté une recherche de découverte électronique, le nombre total et la taille des éléments partiellement indexés dans les emplacements qui ont fait l’objet de la recherche sont répertoriés dans les statistiques des résultats de la recherche qui sont affichées dans les statistiques détaillées de la recherche. Notez qu’ils sont appelés éléments  *nonndex dans*  les statistiques de recherche. Voici quelques éléments qui affectent le nombre d’éléments partiellement indexés renvoyés dans les résultats de la recherche :
  
- Si un élément est partiellement indexé et correspond à la requête de recherche, il est inclus dans le nombre (et la taille) d’éléments de résultat de recherche et dans les éléments partiellement indexés. Toutefois, lorsque les résultats de cette même recherche sont exportés, l’élément est inclus uniquement avec l’ensemble des résultats de recherche ; il n’est pas inclus en tant qu’élément partiellement indexé.

- Les éléments partiellement indexés situés dans les *sites* SharePoint et OneDrive ne sont pas inclus dans l’estimation des éléments partiellement indexés affichés dans les statistiques détaillées de la recherche. Toutefois, les éléments partiellement indexés peuvent être exportés lorsque vous exportez les résultats d’une recherche de découverte électronique. Par exemple, si vous recherchez uniquement des sites, le nombre estimé d’éléments partiellement indexés sera zéro.
  
## <a name="calculating-the-ratio-of-partially-indexed-items-in-your-organization"></a>Calcul du taux d’éléments partiellement indexés dans votre organisation

Pour comprendre l’exposition de votre organisation aux éléments partiellement indexés, vous pouvez exécuter une recherche de tout le contenu dans toutes les boîtes aux lettres (à l’aide d’une requête de mot clé vide). Dans l’exemple suivant, il y a 1 629 904 (146,46 Go) d’éléments entièrement indexés et 10 025 (10,27 Go) d’éléments partiellement indexés.
  
![Exemple de statistiques de recherche montrant des éléments partiellement indexés.](../media/PartiallyIndexedItemsTest.png)
  
Vous pouvez déterminer le pourcentage d’éléments partiellement indexés à l’aide des calculs suivants.
  
 **Pour calculer le taux d’éléments partiellement indexés dans votre organisation :**

`(Total number of partially indexed items/Total number of items) x 100`

`(10025/1629904) x 100 = 0.62%`

À l’aide des résultats de recherche de l’exemple précédent, 0,62 % de tous les éléments de boîtes aux lettres sont partiellement indexés.
  
 **Pour calculer le pourcentage de la taille des éléments partiellement indexés dans votre organisation :**

`(Size of all partially indexed items/Size of all items) x 100`

`(10.27 GB/146.46 MB) x 100 = 7.0%`

Ainsi, dans l’exemple précédent, 7 % de la taille totale des éléments de boîte aux lettres sont des éléments partiellement indexés. Comme indiqué précédemment, la plupart des clients d’organisations ont moins de 1 % du contenu par volume et moins de 12 % du contenu par taille partiellement indexée.

## <a name="working-with-partially-indexed-items"></a>Travailler avec des éléments partiellement indexés

Dans les cas où vous devez examiner partiellement les éléments pour vérifier [](export-a-content-search-report.md) qu’ils ne contiennent pas d’informations pertinentes, vous pouvez exporter un rapport de recherche de contenu qui contient des informations sur les éléments partiellement indexés. Lorsque vous exportez un rapport de recherche de contenu, n’oubliez pas de choisir l’une des options d’exportation qui inclut les éléments partiellement indexés.
  
![Choisissez la deuxième ou la troisième option pour exporter des éléments partiellement indexés.](../media/PartiallyIndexedItemsExportOptions.png)
  
Lorsque vous exportez des résultats de recherche eDiscovery ou un rapport de recherche à l’aide de l’une de ces options, l’exportation inclut un rapport nommé Items.csv. Ce rapport inclut la plupart des mêmes informations que le fichier ResultsLog.csv' toutefois, le fichier Items.csv non indexé inclut également deux champs liés aux éléments partiellement indexés **:** les balises d’erreur et les propriétés **d’erreur.** Ces champs contiennent des informations sur l’erreur d’indexation pour chaque élément partiellement indexé. L’utilisation des informations de ces deux champs peut vous aider à déterminer si l’erreur d’indexation d’un événement particulier a un impact sur votre enquête. Si c’est le cas, vous pouvez effectuer une recherche ciblée et récupérer et exporter des messages électroniques et des documents SharePoint ou OneDrive spécifiques afin de pouvoir les examiner afin de déterminer s’ils sont pertinents pour votre enquête. Pour obtenir des instructions détaillées, voir Préparer un fichier [CSV](csv-file-for-an-id-list-content-search.md)pour une recherche ciblée dans Office 365 .

> [!NOTE]
> Le fichier Items.csv non Items.csv contient également des champs **nommés Type d’erreur** et **Message d’erreur.** Il s’agit de champs hérités qui  contiennent  des informations similaires aux informations des champs Balises d’erreur et Propriétés d’erreur, mais avec des informations moins détaillées. Vous pouvez ignorer ces champs hérités en toute sécurité.
  
## <a name="errors-related-to-partially-indexed-items"></a>Erreurs liées à des éléments partiellement indexés

Les balises d’erreur sont composés de deux éléments d’information, l’erreur et le type de fichier. Par exemple, dans cette paire erreur/type de fichier :

```text
 parseroutputsize_xls
```

 `parseroutputsize` est l’erreur `xls` et est le type de fichier du fichier sur qui l’erreur s’est produite. Dans les cas où le type de fichier n’a pas été reconnu ou s’il ne s’est pas appliqué à l’erreur, vous verrez la valeur à la `noformat` place du type de fichier.
  
Voici une liste des erreurs d’indexation et une description de la cause possible de l’erreur.
  
| Balise d’erreur | Description |
|:-----|:-----|
| `attachmentcount` <br/> |Un message électronique avait trop de pièces jointes et certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentdepth` <br/> |L’outil de récupération de contenu et l’outil d’outils d’outils de récupération de documents ont trouvé un trop grand nombre de niveaux de pièces jointes imbrmbrées dans d’autres pièces jointes. Certaines de ces pièces jointes n’ont pas été traitées.  <br/> |
| `attachmentrms` <br/> |Échec du décodage d’une pièce jointe car elle était protégée par RMS.  <br/> |
| `attachmentsize` <br/> |Un fichier joint à un message électronique était trop grand et n’a pas pu être traitée.  <br/> |
| `indexingtruncated` <br/> |Lors de l’écriture du message électronique traitée dans l’index, l’une des propriétés indexables était trop grande et a été tronquée. Les propriétés tronquées sont répertoriées dans le champ Propriétés d’erreur.  <br/> |
| `invalidunicode` <br/> |Un message électronique contenait du texte qui n’a pas pu être traitée en tant qu’Unicode valide. L’indexation de cet élément peut être incomplète.  <br/> |
| `parserencrypted` <br/> |Le contenu de la pièce jointe ou du message électronique est chiffré et Microsoft 365 n’a pas pu décoder le contenu.  <br/> |
| `parsererror` <br/> |Une erreur inconnue s’est produite lors de l’échantillonnage. Cela résulte généralement d’un bogue logiciel ou d’un incident de service.  <br/> |
| `parserinputsize` <br/> |Une pièce jointe était trop volumineuse pour que l’outil d’outil de l’outil de recherche gère cette pièce jointe, et l’utilisation de cette pièce jointe n’a pas eu lieu ou n’a pas été achevée.  <br/> |
| `parsermalformed` <br/> |Une pièce jointe a été malformée et n’a pas pu être gérée par l’outil d’outils d’enquête. Ce résultat peut être dû à des anciens formats de fichiers, à des fichiers créés par des logiciels incompatibles ou à des virus qui prétendent être autre chose que revendiqués.  <br/> |
| `parseroutputsize` <br/> |La sortie de l’utilisation d’une pièce jointe était trop volumineuse et devait être tronquée.  <br/> |
| `parserunknowntype` <br/> |Une pièce jointe avait un type de fichier Microsoft 365 impossible à détecter.  <br/> |
| `parserunsupportedtype` <br/> |Une pièce jointe avait un type de fichier Office 365 détecté, mais l’examen de ce type de fichier n’est pas pris en charge.  <br/> |
| `propertytoobig` <br/> |La valeur d’une propriété de messagerie dans Exchange Store était trop importante pour être récupérée et le message n’a pas pu être traitée. Cela se produit généralement uniquement pour la propriété body d’un message électronique.  <br/> |
| `retrieverrms` <br/> |Le récupérateur de contenu n’a pas pu décoder un message protégé par RMS.  <br/> |
| `wordbreakertruncated` <br/> |Trop de mots ont été identifiés dans le document lors de l’indexation. Le traitement de la propriété s’est arrêté lorsque la limite est atteinte et la propriété est tronquée.  <br/> |

Les champs d’erreur décrivent les champs affectés par l’erreur de traitement répertoriée dans le champ Balises d’erreur. Si vous recherchez une propriété telle que ou , les erreurs dans le corps du message n’auront pas  `subject`  `participants` d’impact sur les résultats de votre recherche. Cela peut être utile lors de la détermination des éléments partiellement indexés que vous devrez peut-être examiner plus en détail.
  
## <a name="using-a-powershell-script-to-determine-your-organizations-exposure-to-partially-indexed-email-items"></a>Utilisation d’un script PowerShell pour déterminer l’exposition de votre organisation aux éléments de courrier partiellement indexés

Les étapes suivantes vous montrent comment exécuter un script PowerShell qui recherche tous les éléments dans toutes les boîtes aux lettres Exchange, puis génère un rapport sur le rapport entre les éléments de messagerie partiellement indexés de votre organisation (par nombre et par taille) et affiche le nombre d’éléments (et leur type de fichier) pour chaque erreur d’indexation qui se produit. Utilisez les descriptions de balise d’erreur de la section précédente pour identifier l’erreur d’indexation.
  
1. Enregistrez le texte suivant dans un fichier Windows PowerShell script à l’aide d’un suffixe de nom de fichier .ps1 ; par exemple, `PartiallyIndexedItems.ps1` .

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

3. Dans le Centre de sécurité & conformité PowerShell, allez dans le dossier où vous avez enregistré le script à l’étape 1, puis exécutez le script . par exemple :

   ```powershell
   .\PartiallyIndexedItems.ps1
   ```

Voici un exemple de sortie renvoyée par le script.
  
![Exemple de sortie à partir d’un script qui génère un rapport sur l’exposition de votre organisation aux éléments de courrier partiellement indexés.](../media/aeab5943-c15d-431a-bdb2-82f135abc2f3.png)

> [!NOTE]
> Veuillez prendre en compte les éléments suivants:
>  
> - Le nombre total et la taille des éléments de courrier, ainsi que le rapport de votre organisation des éléments de courrier partiellement indexés (par nombre et par taille).
> 
> - Balises d’erreur de liste et types de fichiers correspondants pour lesquels l’erreur s’est produite.
  
## <a name="see-also"></a>Voir aussi

[Éléments partiellement indexés dans eDiscovery](partially-indexed-items-in-content-search.md)