---
title: Vérifier la présence d’erreurs dans vos requêtes de recherche
description: Découvrez comment détecter les erreurs et les fautes de frappe dans votre requête de mot clé pour les recherches eDiscovery avant d’exécuter la recherche.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 88898874-e262-4c5c-b6d2-4e697497fc74
ms.custom: seo-marvel-apr2020
ms.collection:
- tier1
- purview-compliance
- ediscovery
ms.openlocfilehash: 30aebce0734c7e9043516cb058fb1aceaa79c9ef
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688044"
---
# <a name="check-your-search-query-for-errors"></a>Vérifier la présence d’erreurs dans vos requêtes de recherche
  
Voici une liste des caractères non pris en charge que nous vérifions dans les requêtes de recherche pour recherche de contenu et Microsoft Purview eDiscovery (Standard). Les caractères non pris en charge sont souvent masqués et provoquent généralement une erreur de recherche ou retournent des résultats inattendus.
  
- **Guillemets** intelligents : les guillemets simples et doubles intelligents (également appelés guillemets bouclés) ne sont pas pris en charge. Seuls les guillemets droits peuvent être utilisés dans une requête de recherche.
- **Caractères non imprimables et de contrôle** : les caractères non imprimables et de contrôle ne représentent pas un symbole écrit, tel qu’un caractère alphanumérique. Il peut s'agir de caractères servant à mettre en forme le texte ou à séparer des lignes.
- **Marques de gauche à droite et de droite à gauche** : ces marques sont des caractères de contrôle utilisés pour indiquer la direction du texte pour les langues de gauche à droite (telles que l’anglais et l’espagnol) et de droite à gauche (comme l’arabe et l’hébreu).
- **Opérateurs booléens en minuscules** : si vous utilisez un opérateur booléen, tel que **AND**, **OR** et **NOT** dans une requête de recherche, il doit être majuscule. Lorsque nous vérifions les fautes de frappe dans une requête, la syntaxe de la requête indique souvent qu’un opérateur booléen est utilisé même si des opérateurs en minuscules peuvent être utilisés ; par exemple,  `(WordA or WordB) and (WordC or WordD)`.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="what-happens-if-a-query-has-an-unsupported-character"></a>Que se passe-t-il si une requête a un caractère non pris en charge ?

Si des caractères non pris en charge sont trouvés dans votre requête, un message d’avertissement s’affiche indiquant que des caractères non pris en charge ont été trouvés et suggère une alternative. Vous avez ensuite la possibilité de conserver la requête d’origine ou de la remplacer par la requête révisée suggérée.

Voici un exemple de message d’avertissement qui s’affiche après avoir sélectionné **Vérifier la requête pour les fautes de frappe** pour la requête de recherche dans la capture d’écran précédente. Notez que la requête d’origine utilisait des guillemets intelligents et des opérateurs booléens en minuscules.
  
![Un message d’avertissement s’affiche avec une révision suggérée pour votre requête.](../media/23214b30-8e52-412c-bd80-63fb1b3ed52d.png)
  
## <a name="how-to-prevent-unsupported-characters-in-your-search-queries"></a>Comment empêcher les caractères non pris en charge dans vos requêtes de recherche

Les caractères non pris en charge sont généralement ajoutés à une requête lorsque vous copiez la requête ou des parties de la requête à partir d’autres applications (telles que Microsoft Word ou Microsoft Excel) et que vous les collez dans la zone de mot clé de la page de requête d’une recherche de contenu. Le meilleur moyen d'éviter les caractères non pris en charge est de saisir la requête dans la zone de mot clé. Vous pouvez également copier une requête à partir de Word ou Excel, puis la coller dans un éditeur de texte brut, tel que le Bloc-notes Microsoft. Enregistrez le fichier texte et sélectionnez **ANSI** dans la liste déroulante **Encodage** . Cette action supprime tout le formatage et tous les caractères non pris en charge. Vous pouvez ensuite copier la requête du fichier texte vers la zone de mot clé de la requête.
