---
title: Différer le chargement des images et des éléments JavaScript dans SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
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
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: Découvrez comment réduire le temps de chargement des pages SharePoint Online à l’aide de JavaScript pour retarder le chargement des images et des éléments JavaScript non essentiels.
ms.openlocfilehash: 0b0129f691018caf414ebd249e905a97d5560145dc648a073d8000402d11217d
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53813285"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Différer le chargement des images et des éléments JavaScript dans SharePoint Online

Cet article explique comment réduire le temps de chargement des pages SharePoint Online à l’aide de JavaScript pour retarder le chargement des images et en attendant de charger du JavaScript non essentiel jusqu’au chargement de la page.
  
Les images peuvent avoir une incidence négative sur les vitesses de chargement des pages sur SharePoint Online. Par défaut, la plupart des navigateurs Internet modernes pré-récupèrent les images lors du chargement d’une page HTML. Cela peut ralentir inutilement le chargement de la page si les images ne sont pas visibles à l’écran jusqu’à ce que l’utilisateur défile vers le bas. Les images peuvent empêcher le navigateur de charger la partie visible de la page. Pour contourner ce problème, vous pouvez utiliser JavaScript pour ignorer d’abord le chargement des images. En outre, le chargement de JavaScript non essentiels peut ralentir les temps de téléchargement sur SharePoint pages. Cette rubrique décrit certaines méthodes que vous pouvez utiliser pour améliorer les temps de chargement de page avec JavaScript dans SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Améliorer les temps de chargement de page en retardant le chargement d’image dans SharePoint pages en ligne à l’aide de JavaScript

Vous pouvez utiliser JavaScript pour empêcher un navigateur web de pré-récupérer des images. Cela accélère le rendu global des documents. Pour ce faire, vous supprimez la valeur de l’attribut src de la balise et remplacez-la par le chemin d’accès à un fichier dans un attribut de données tel que \<img\> : data-src. Par exemple :
  
```html
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

À l’aide de cette méthode, le navigateur ne télécharge pas les images immédiatement. Si l’image se trouve déjà dans la fenêtre d’affichage, JavaScript indique au navigateur de récupérer l’URL de l’attribut de données et de l’insérer en tant que valeur pour l’attribut src. L’image se charge uniquement à mesure que l’utilisateur défile et qu’elle s’affiche.
  
Pour que tout cela se produise, vous devez utiliser JavaScript.
  
Dans un fichier texte, définissez la fonction **isElementInViewport()** pour vérifier si un élément se trouve dans la partie du navigateur visible par l’utilisateur.
  
```javascript
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth)
  );
}
```

Ensuite, utilisez **isElementInViewport()** dans la **fonction loadItemsInView().** La **fonction loadItemsInView()** charge toutes les images qui ont une valeur pour l’attribut data-src s’ils se trouve dans la partie du navigateur visible par l’utilisateur. Ajoutez la fonction suivante au fichier texte :
  
```javascript
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

Enfin, **appelez loadItemsInView()** à partir de **window.onscroll()** comme illustré dans l’exemple suivant. Cela garantit que toutes les images qui se trouveraient dans laport d’affichage sont chargées en tant que l’utilisateur en a besoin, mais pas avant. Ajoutez ce qui suit au fichier texte :
  
```javascript
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Pour SharePoint Online, vous devez attacher la fonction suivante à l’événement de défilement sur la balise #s4-workspace. \<div\> Cela est dû au fait que les événements de fenêtre sont surchargés afin de s’assurer que le ruban reste attaché au haut de la page.
  
```javascript
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Enregistrez le fichier texte en tant que fichier JavaScript avec l’extension .js, par exemple delayLoadImages.js.
  
Une fois que vous avez terminé delayLoadImages.js, vous pouvez ajouter le contenu du fichier à une page maître dans SharePoint Online. Pour ce faire, ajoutez un lien de script à l’en-tête de la page maître. Une fois qu’il est dans une page maître, le JavaScript est appliqué à toutes les pages de votre site SharePoint Online qui utilisent cette mise en page maître. Sinon, si vous avez l’intention de l’utiliser uniquement sur une page de votre site, utilisez le script éditeur de web part pour incorporer le JavaScript dans la page. Consultez ces rubriques pour plus d’informations :
  
- [Comment appliquer une page maître à un site dans SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)

- [Procédure : Créer une mise en page dans SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)

### <a name="example-referencing-the-javascript-delayloadimagesjs-file-from-a-master-page-in-sharepoint-online"></a>Exemple : référencement du fichier delayLoadImages.js JavaScript à partir d’une page maître dans SharePoint Online
  
Pour que cela fonctionne, vous devez également référencer jQuery dans la page maître. Dans l’exemple suivant, vous pouvez voir dans le chargement initial de la page qu’une seule image est chargée, mais qu’il en existe plusieurs autres sur la page.
  
![Capture d’écran montrant une seule image chargée sur une page](../media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
La capture d’écran suivante montre le reste des images qui sont téléchargées après leur défilement vers l’affichage.
  
![Capture d’écran montrant plusieurs images chargées sur une page](../media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Retarder le chargement de l’image à l’aide de JavaScript peut être une technique efficace pour augmenter les performances . toutefois, si la technique est appliquée sur un site web public, les moteurs de recherche ne sont pas en mesure d’analyser les images de la même façon qu’ils analysent une image formée régulièrement. Cela peut affecter les classements sur les moteurs de recherche, car les métadonnées sur l’image elle-même ne sont pas réellement présentes tant que la page n’est pas en cours de chargement. Les robot d’un moteur de recherche lisent uniquement le code HTML et ne voient donc pas les images en tant que contenu sur la page. Les images sont l’un des facteurs utilisés pour classer les pages dans les résultats de la recherche. L’une des façons de contourner ce besoin consiste à utiliser du texte d’introduction pour vos images.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>GitHub code : injection de JavaScript pour améliorer les performances

Ne manquez pas l’article et l’exemple de code sur [l’injection JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) fournie sur GitHub.
  
## <a name="see-also"></a>Voir aussi

[Navigateurs pris en charge dans Office 2013 et Applications Microsoft 365 pour les grandes entreprises](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Comment appliquer une page maître à un site dans SharePoint 2013](/sharepoint/dev/general-development/how-to-apply-a-master-page-to-a-site-in-sharepoint)
  
[Procédure : Créer une mise en page dans SharePoint 2013](/sharepoint/dev/general-development/how-to-create-a-page-layout-in-sharepoint)