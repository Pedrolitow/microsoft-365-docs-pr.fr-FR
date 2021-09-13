---
title: Minimisation et regroupement dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: Découvrez comment utiliser les techniques de réduction et de regroupement avec Web Essentials pour réduire les demandes HTTP et le temps nécessaire pour charger des pages dans SharePoint Online.
ms.openlocfilehash: 5ba1e174cbb016bdf88a1d4006a0b8aafd5ec042
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59209239"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minimisation et regroupement dans SharePoint Online

Cet article explique comment utiliser les techniques de réduction et de regroupement avec Web Essentials pour réduire le nombre de demandes HTTP et réduire le temps nécessaire au chargement des pages dans SharePoint Online.
  
Lorsque vous personnalisez votre site web, vous pouvez finir par ajouter un grand nombre de fichiers supplémentaires au serveur pour prendre en charge la personnalisation. L’ajout de JavaScript, de CSS et d’images supplémentaires augmente le nombre de requêtes HTTP sur le serveur, ce qui augmente le temps d’affichage d’une page web. Si vous avez plusieurs fichiers du même type, vous pouvez regrouper ces fichiers pour accélérer le téléchargement de ces fichiers.
  
Pour les fichiers JavaScript et CSS, vous pouvez également utiliser une approche appelée réduction, dans laquelle vous réduisez la taille totale des fichiers en supprimant les espaces et autres caractères qui ne sont pas nécessaires.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minification et regroupement de fichiers JavaScript et CSS avec Web Essentials

Vous pouvez utiliser des logiciels tiers tels que Web Essentials pour regrouper les fichiers CSS et JavaScript.
  
> [!IMPORTANT]
> Web Essentials est un projet communautaire tiers, open source. Le logiciel est une extension de Visual Studio 2012 et Visual Studio 2013 et n’est pas pris en charge par Microsoft. Pour télécharger Web Essentials, visitez le site web à [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629) l’adresse . 
  
Web Essentials offre deux formes de regroupement :
  
- .bundle : pour les fichiers CSS et JavaScript
    
- .sprite : pour les images (disponible uniquement dans Visual Studio 2013)
    
Vous pouvez utiliser Web Essentials si vous disposez d’une fonctionnalité existante avec certains éléments de personnalisation référencés dans une page maître personnalisée, telles que :
  
![Capture d’écran de l’élément de marque dans la page maître personnalisée.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Pour créer un ensemble TE000127218 et CSS dans Web Essentials**
  
1. Dans Visual Studio, dans l’Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le fichier groupé.
    
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** Créer un fichier groupé \> **JavaScript** dans le menu contextif. Par exemple : 
    
    ![Capture d’écran montrant les options de menu Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Affichage des résultats du regroupement de fichiers JavaScript et CSS

Lorsque vous créez un fichier groupé JavaScript et CSS, Web Essentials crée un fichier XML appelé fichier de recette qui identifie les fichiers JavaScript et CSS, ainsi que d’autres informations de configuration : 
  
![Capture d’écran du fichier de recette JavaScript et CSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
En outre, si l’indicateur de réduction est définie sur true dans la recette de regroupement, les fichiers sont réduits en taille et regroupés. Cela signifie que de nouvelles versions minifiées des fichiers JavaScript ont été créées que vous pouvez référencer dans votre page maître.
  
![Capture d’écran de l’indicateur minify sur true.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Lorsque vous chargez une page à partir de votre site web, vous pouvez utiliser les outils de développement de votre navigateur web, tels qu’Internet Explorer 11, pour voir le nombre de demandes envoyées au serveur et la durée de chargement de chaque fichier.
  
La figure suivante est le résultat du chargement des fichiers JavaScript et CSS avant la minification.
  
![Capture d’écran montrant 80 éléments en cours de téléchargement.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Après avoir groupé les fichiers CSS et JavaScript, le nombre de demandes abandonnées à 74 et chaque fichier n’a pris que légèrement plus de temps que les fichiers d’origine à télécharger individuellement :
  
![Capture d’écran montrant 74 éléments en cours de téléchargement.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Après le regroupement, le fichier groupé JavaScript est considérablement réduit de 815 000 à 365 000 000 :
  
![Capture d’écran montrant une taille de téléchargement réduite.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Regroupement d’images en créant un sprite d’image

À l’image de la façon dont vous regroupez des fichiers JavaScript et CSS, vous pouvez combiner de nombreuses petites icônes et d’autres images communes dans une feuille de sprite plus grande, puis utiliser CSS pour révéler les images individuelles. Au lieu de télécharger chaque image individuelle, le navigateur web de l’utilisateur télécharge une seule fois la feuille de sprite, puis la met en cache sur l’ordinateur local. Cela améliore les performances de chargement des pages en réduisant le nombre de téléchargements et d’allers-retours vers le serveur web.
  
 **Pour créer un sprite d’image dans Web Essentials**
  
1. Dans Visual Studio, dans l’Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le fichier groupé.
    
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** Créer un \> **sprite d’image** dans le menu contextiqué. Par exemple : 
    
    ![Capture d’écran montrant comment créer un sprite d’image.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Choisissez un emplacement pour enregistrer le fichier sprite. Le fichier .sprite est un fichier XML qui décrit les paramètres et les fichiers du sprite. Les figures suivantes illustrent un fichier PNG sprite et son fichier XML .sprite correspondant.
    
    ![Capture d’écran d’un fichier sprite.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Capture d’écran du fichier XML sprite.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

