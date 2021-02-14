---
title: Vérifier la présence d’erreurs dans vos requêtes de recherche de contenu
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 11/30/2016
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
description: Découvrez comment détecter les erreurs et les fautes de frappe dans votre requête par mot clé pour la recherche de contenu, avant d’effectuer la recherche.
ms.openlocfilehash: 250db272014d5801bfb3927d14072eea94bd635f
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818093"
---
# <a name="check-your-content-search-query-for-errors"></a>Vérifier la présence d’erreurs dans vos requêtes de recherche de contenu

Lorsque vous créez ou modifiez une recherche de contenu, Microsoft 365 peut vérifier la recherche de caractères non pris en compte et d’opérateurs booléens minuscules dans votre requête. Comment ? Il vous **suffit de cliquer sur Rechercher les fautes de frappe** dans la page de requête d’une recherche de contenu. 
  
![Cliquez sur « Vérifier la requête pour typos » pour rechercher des caractères non pris en compte dans votre requête de recherche.](../media/e5314306-cfb2-481d-9b5c-13ce658156e7.png)
  
Voici une liste des caractères non pris en place que nous vérifions. Les caractères non pris enupportés sont souvent masqués et ils provoquent généralement une erreur de recherche ou retournent des résultats inattendus.
  
- **Guillemets intelligents** : les guillemets simples et doubles (également appelés guillemets) ne sont pas pris en charge. Seuls les guillemets droits peuvent être utilisés dans une requête de recherche. 
    
- **Caractères non imprimables** et de contrôle : les caractères non imprimables et les caractères de contrôle ne représentent pas un symbole écrit, tel qu’un caractère alpha-numérique. Il peut s'agir de caractères servant à mettre en forme le texte ou à séparer des lignes. 
    
-  Marques de gauche à droite et de droite à gauche : ces marques sont des caractères de contrôle utilisés pour indiquer l’orientation du texte pour les langues de gauche à droite (telles que l’anglais et l’espagnol) et de droite à gauche (comme l’arabe et l’hébreu).
    
- **Opérateurs booléens** en minuscules : si vous utilisez un opérateur booléen, tel que **AND**, **OR** et **NOT** dans une requête de recherche, il doit être en minuscules. Lorsque nous vérifions une requête pour des fautes de frappe, la syntaxe de requête indique souvent qu’un opérateur booléen est utilisé même si des opérateurs en minuscules peuvent être utilisés ; par exemple,  `(WordA or WordB) and (WordC or WordD)` .
    
## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Que se passe-t-il si une requête a un caractère non pris en compte ?

Si des caractères non pris en compte sont trouvés dans votre requête, un message d’avertissement indique que des caractères non pris en compte ont été trouvés et suggère une alternative. Vous avez ensuite la possibilité de conserver la requête d’origine ou de la remplacer par la requête révisée suggérée. Voici un exemple du message d’avertissement qui s’affiche après que vous avez cliqué sur Rechercher les fautes de frappe pour la requête de recherche dans la capture d’écran précédente.  Notez que la requête d’origine contient des guillemets intelligents et des opérateurs booléens minuscules. 
  
![Un message d’avertissement s’affiche avec une révision suggérée pour votre requête](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Comment empêcher les caractères non pris en compte dans vos requêtes de recherche

Les caractères non pris en compte sont généralement ajoutés à une requête lorsque vous copiez la requête ou certaines parties de la requête à partir d’autres applications (telles que Microsoft Word ou Microsoft Excel) et que vous les collez dans la zone de mot clé de la page de requête d’une recherche de contenu. Le meilleur moyen d'éviter les caractères non pris en charge est de saisir la requête dans la zone de mot clé. Vous pouvez également copier une requête à partir de Word ou d’Excel, puis la coller dans un éditeur de texte simple, tel que le Bloc-notes Microsoft. Enregistrez le fichier texte et sélectionnez **ANSI** dans **la** liste de listes listes de codage. Cette action supprime tout le formatage et tous les caractères non pris en charge. Vous pouvez ensuite copier la requête du fichier texte vers la zone de mot clé de la requête. 
