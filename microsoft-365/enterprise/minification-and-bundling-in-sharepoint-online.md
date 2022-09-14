---
title: Minimisation et regroupement dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: troubleshooting
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
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
description: Découvrez comment utiliser des techniques de minification et de regroupement avec Web Essentials pour réduire les requêtes HTTP et le temps nécessaire au chargement des pages dans SharePoint Online.
ms.openlocfilehash: 38149275f2f3987fe5c989b355fc1f5aa5368f69
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67694500"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minimisation et regroupement dans SharePoint Online

Cet article explique comment utiliser des techniques de minification et de regroupement avec Web Essentials pour réduire le nombre de requêtes HTTP et réduire le temps nécessaire au chargement des pages dans SharePoint Online.
  
Lorsque vous personnalisez votre site web, vous pouvez ajouter un grand nombre de fichiers supplémentaires au serveur pour prendre en charge la personnalisation. L’ajout d’images javaScript, CSS et supplémentaires augmente le nombre de requêtes HTTP adressées au serveur, ce qui augmente le temps nécessaire à l’affichage d’une page web. Si vous avez plusieurs fichiers du même type, vous pouvez regrouper ces fichiers pour accélérer le téléchargement de ces fichiers.
  
Pour les fichiers JavaScript et CSS, vous pouvez également utiliser une approche appelée minification, où vous réduisez la taille totale des fichiers en supprimant les espaces blancs et autres caractères qui ne sont pas nécessaires.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minification et regroupement de fichiers JavaScript et CSS avec Web Essentials

Vous pouvez utiliser des logiciels tiers tels que Web Essentials pour regrouper des fichiers CSS et JavaScript.
  
> [!IMPORTANT]
> Web Essentials est un projet tiers, open source et communautaire. Le logiciel est une extension de Visual Studio 2012 et Visual Studio 2013 et n’est pas pris en charge par Microsoft. Pour télécharger Web Essentials, visitez le site Web [Essentials 2012](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebEssentials2012).
  
Web Essentials offre deux formes de regroupement :
 
- .bundle : pour les fichiers CSS et JavaScript
- .sprite : pour les images (disponibles uniquement dans Visual Studio 2013)

Vous pouvez utiliser Web Essentials si vous disposez d’une fonctionnalité existante avec certains éléments de personnalisation référencés dans une page maître personnalisée, par exemple :
  
![Capture d’écran de l’élément de marque dans la page maître personnalisée.](../media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
### <a name="to-create-a-te000127218-and-css-bundle-in-web-essentials"></a>Pour créer un bundle TE000127218 et CSS dans Web Essentials
  
1. Dans Visual Studio, dans Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le bundle.
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** \> **Créer un fichier groupé JavaScript** dans le menu contextuel. Par exemple :

    ![Capture d’écran montrant les options de menu Web Essentials.](../media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Affichage des résultats du regroupement de fichiers JavaScript et CSS

Lorsque vous créez un bundle JavaScript et CSS, Web Essentials crée un fichier XML appelé fichier recette qui identifie les fichiers JavaScript et CSS, ainsi que d’autres informations de configuration :
  
![Capture d’écran du fichier de recettes JavaScript et CSS.](../media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
En outre, si l’indicateur minify est défini sur true dans la recette de regroupement, les fichiers sont réduits en taille et regroupés. Cela signifie que de nouvelles versions minifiées des fichiers JavaScript ont été créées que vous pouvez référencer dans votre page maître.
  
![Capture d’écran de l’indicateur minify défini sur true.](../media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Lorsque vous chargez une page à partir de votre site web, vous pouvez utiliser les outils de développement de votre navigateur web, tels qu’Internet Explorer 11, pour voir le nombre de demandes envoyées au serveur et la durée de chargement de chaque fichier.
  
La figure suivante est le résultat du chargement des fichiers JavaScript et CSS avant la minification.
  
![Capture d’écran montrant 80 éléments en cours de téléchargement.](../media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Après avoir regroupé les fichiers CSS et JavaScript, le nombre de demandes est passé à 74 et chaque fichier a pris un peu plus de temps que les fichiers d’origine à télécharger individuellement :
  
![Capture d’écran montrant 74 éléments en cours de téléchargement.](../media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Après le regroupement, le fichier bundle JavaScript est considérablement réduit, passant de 815 Ko à 365 Ko :
  
![Capture d’écran montrant une taille de téléchargement réduite.](../media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Regrouper des images en créant un sprite d’image

De la même façon que vous regroupez des fichiers JavaScript et CSS, vous pouvez combiner de nombreuses petites icônes et d’autres images courantes dans une feuille sprite plus grande, puis utiliser CSS pour révéler les images individuelles. Au lieu de télécharger chaque image individuelle, le navigateur web de l’utilisateur télécharge la feuille sprite une seule fois, puis la met en cache sur l’ordinateur local. Cela améliore les performances de chargement de page en réduisant le nombre de téléchargements et d’allers-retours vers le serveur web.
  
### <a name="to-create-an-image-sprite-in-web-essentials"></a>Pour créer un sprite d’image dans Web Essentials**
  
1. Dans Visual Studio, dans Explorateur de solutions, sélectionnez les fichiers que vous souhaitez inclure dans le bundle.
2. Cliquez avec le bouton droit sur les fichiers sélectionnés, puis sélectionnez **Web Essentials** \> **Créer un sprite d’image** dans le menu contextuel. Par exemple :

    ![Capture d’écran montrant comment créer un sprite d’image.](../media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Choisissez un emplacement pour enregistrer le fichier sprite. Le fichier .sprite est un fichier XML qui décrit les paramètres et les fichiers dans le sprite. Les figures suivantes montrent un exemple de fichier PNG sprite et son fichier XML .sprite correspondant.

    ![Capture d’écran d’un fichier sprite.](../media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Capture d’écran du fichier XML sprite.](../media/d1f94776-280d-4d56-abb5-384f145d9989.png)
