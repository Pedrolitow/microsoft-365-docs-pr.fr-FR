---
title: Modifier un dictionnaire de mots clés
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment modifier un dictionnaire de mots clés dans le centre Microsoft 365 conformité.
ms.openlocfilehash: acdf8b24aced21ed2f576fd57a3c685ef14debea
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2022
ms.locfileid: "62271813"
---
# <a name="modify-a-keyword-dictionary"></a>Modifier un dictionnaire de mots clés

Vous devrez peut-être modifier des mots clés dans l’un de vos dictionnaires de mots clés ou modifier l’un des dictionnaires intégrés. Vous pouvez le faire via PowerShell ou via le Centre de conformité.

## <a name="modify-a-keyword-dictionary-in-compliance-center"></a>Modifier un dictionnaire de mots clés dans le Centre de conformité

Les dictionnaires de mots clés peuvent être utilisés en tant `Primary elements` `Supporting elements` que modèles de type d’informations sensibles (SIT). Vous pouvez modifier un dictionnaire de mots clés lors de la création d’un sit ou d’un sit existant. Par exemple, pour modifier un dictionnaire de mots clés existant :

1. Ouvrez le modèle qui possède le dictionnaire de mots clés que vous souhaitez mettre à jour.
2. Recherchez le dictionnaire de mots clés que vous souhaitez mettre à jour et sélectionnez Modifier.
3. A effectuer vos modifications à l’aide d’un mot clé par ligne.

   ![capture d’écran des mots clés de modification.](../media/edit-keyword-dictionary.png)

4. Choose `Done`.

## <a name="modify-a-keyword-dictionary-using-powershell"></a>Modifier un dictionnaire de mots clés à l’aide de PowerShell

Par exemple, nous allons modifier certains termes dans PowerShell, les enregistrer localement pour qu’ils puissent être modifiés dans un éditeur, puis mettre à jour les termes précédemment intégrés.

Tout d’abord, récupérez l’objet dictionnaire :

```powershell
$dict = Get-DlpKeywordDictionary -Name "Diseases"
```

L’impression `$dict` affiche les différentes propriétés. Les mots clés eux-mêmes sont stockés dans un objet sur le système arrière, `$dict.KeywordDictionary` mais contiennent une représentation sous la chaîne de ces mots clés, que vous utiliserez pour modifier le dictionnaire.

Avant de modifier le dictionnaire, vous devez revenir à la chaîne de termes en tableau à l’aide de la `.split(',')` méthode. Ensuite, vous nettoyerez les espaces `.trim()` indésirables entre les mots clés avec la méthode, en laissant uniquement les mots clés à travailler.

```powershell
$terms = $dict.KeywordDictionary.split(',').trim()
```

Vous allez maintenant supprimer certains termes du dictionnaire. Étant donné que l’exemple de dictionnaire ne contient que quelques mots clés, vous pourriez simplement passer directement à l’exportation et à la modification du dictionnaire dans le Bloc-notes, mais les dictionnaires contiennent généralement une grande quantité de texte. Vous allez donc d’abord découvrir la méthode qui permet de les modifier facilement dans PowerShell.

Dans la dernière étape, vous avez enregistré les mots clés dans un tableau. Il existe plusieurs façons de [supprimer des éléments dans un tableau](/previous-versions/windows/it-pro/windows-powershell-1.0/ee692802(v=technet.10)), mais une approche simple consiste à créer un tableau des termes à supprimer du dictionnaire et à copier uniquement les termes dans celui-ci de dictionnaire qui ne figurent pas dans la liste des termes à supprimer.

Exécutez la commande `$terms` pour afficher la liste actuelle des termes. Le résultat de la commande ressemble à ceci :

```powershell
aarskog's syndrome
abandonment
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablatio
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Exécutez cette commande pour spécifier les termes à supprimer :

```powershell
$termsToRemove = @('abandonment','ablatio')
```

Exécutez cette commande pour supprimer réellement les termes de la liste :

```powershell
$updatedTerms = $terms | Where-Object {$_ -notin $termsToRemove}
```

Exécutez la commande `$updatedTerms` pour afficher la liste des termes mise à jour. La sortie de la commande ressemble à ceci (les termes spécifiés ont été supprimés) :

```powershell
aarskog's syndrome
abasia
abderhalden-kaufmann-lignac
abdominalgia
abduction contracture
abetalipoproteinemia
abiotrophy
ablation
ablepharia
abocclusion
abolition
aborter
abortion
abortus
aboulomania
abrami's disease
```

Enregistrez maintenant le dictionnaire localement et ajoutez quelques termes supplémentaires. Vous pourriez ajouter les termes ici dans PowerShell, mais vous devrez quand même exporter le fichier localement pour vous assurer qu’il a été enregistré avec le codage Unicode et qu’il contient la marque BOM.

Exécutez la commande suivante pour enregistrer le dictionnaire localement :

```powershell
Set-Content $updatedTerms -Path "C:\myPath\terms.txt"
```

À présent, ouvrez simplement le fichier, ajoutez les autres termes et enregistrez-le avec le codage Unicode (UTF-16). Chargez ensuite les termes mis à jour et mettez à jour le dictionnaire sur place.

```powershell
Set-DlpKeywordDictionary -Identity "Diseases" -FileData ([System.IO.File]::ReadAllBytes('C:myPath\terms.txt'))
```

Le dictionnaire a maintenant été mis à jour sur place. Le `Identity` champ prend le nom du dictionnaire. Si vous souhaitez `Set-` également modifier le nom de votre dictionnaire à l’aide de la cmdlet, `-Name` il vous suffit d’ajouter le paramètre à ce qui est indiqué ci-dessus avec votre nouveau nom de dictionnaire.

## <a name="see-also"></a>Voir aussi

- [Créer un dictionnaire de mots clés](create-a-keyword-dictionary.md)
- [Créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md)
