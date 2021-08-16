---
title: Optimisation des images pour SharePoint sites de publication classiques en ligne
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Découvrez comment utiliser les rendus et les sprites pour améliorer les performances des images sur vos sites de publication classiques SharePoint Online.
ms.openlocfilehash: d3bc078bd462e6695afd74d36712757d291215a7b9bbdb6158c1862c034f8158
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53864706"
---
# <a name="image-optimization-for-sharepoint-online-classic-publishing-sites"></a>Optimisation des images pour SharePoint sites de publication classiques en ligne

La vitesse de chargement d’une page web dépend de la taille combinée de tous les composants requis pour restituer la page, y compris les images, HTML, JavaScript et CSS. Les images sont un excellent moyen de rendre votre site plus attrayant, mais leur taille peut affecter les performances. En optimisant vos images avec compression et re re resserr, et en utilisant des sprites, vous pouvez décaner les effets des images très grandes. À l SharePoint rendus d’image, vous pouvez charger une seule grande image et afficher des sections de l’image, ce qui permet de la réutiliser plutôt que de la recharger.

>[!NOTE]
>Cette rubrique s’applique SharePoint sites de publication classiques en ligne, et non aux sites portail modernes. Pour plus d’informations sur l’optimisation des images SharePoint sites portail modernes en ligne, voir Optimiser les images dans les pages SharePoint [portail moderne en ligne.](modern-image-optimization.md)
  
## <a name="using-sprites-to-speed-up-image-loading"></a>Utilisation de sprites pour accélérer le chargement de l’image

![Capture d’écran de spcommon](../media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)

Un sprite d’image contient de nombreuses images plus petites. À l’aide de CSS, vous sélectionnez une partie de l’image composite à afficher sur une partie particulière de la page avec un positionnement absolu. En fait, vous déplacez une seule image autour de la page au lieu de charger plusieurs images et rendez visible une petite partie de cette image par le biais d’une petite fenêtre où la partie requise de l’image de sprite est affichée à l’utilisateur final. SharePoint Online utilise des sprites pour afficher ses différentes icônes dans le fichier spcommon.png sprite.

Ce qui est abordé ici :
- Compression d’image
- Optimisation des images
- SharePoint rendus d’image
   
Cela peut améliorer les performances, car vous ne téléchargez qu’une seule image au lieu de plusieurs, puis cachez et réutilisez cette image. Même si l’image ne reste pas mise en cache, en ayant une seule image au lieu de plusieurs images, cette méthode réduit le nombre total de demandes HTTP au serveur, ce qui réduit les temps de chargement des pages. Il s’agit en fait d’une forme de regroupement d’images. Il s’agit d’une technique très utile si les images ne changent pas très souvent, par exemple, les icônes, comme illustré dans l’exemple SharePoint fourni ci-dessus. Vous pouvez utiliser [Web Essentials,](https://vswebessentials.com/)un projet communautaire open source tiers pour y parvenir facilement dans Microsoft Visual Studio. Pour plus d’informations, [voir Minification et regroupement dans SharePoint Online.](./minification-and-bundling-in-sharepoint-online.md)
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading"></a>Utilisation de la compression et de l’optimisation d’image pour accélérer le chargement de la page

La compression et l’optimisation des images consiste à réduire la taille de fichier des images que vous utilisez sur votre site. Souvent, la meilleure technique pour réduire la taille d’une image consiste à resizer l’image aux dimensions maximales qu’elle sera vue sur le site. Il n’est pas logique d’avoir une image plus grande qu’elle ne le sera jamais. Vous assurer que les images sont des dimensions correctes à l’aide d’un éditeur d’images est un moyen rapide et facile de réduire la taille de votre page.
  
Une fois que les images sont de la bonne taille, l’étape suivante consiste à optimiser la compression de ces images. Différents outils sont disponibles pour la compression et l’optimisation, notamment la galerie de photos et les outils tiers. La clé de la compression consiste à réduire autant que possible la taille de fichier sans perte de qualité visible pour les utilisateurs finaux. Veillez à tester vos fichiers compressés sur un affichage haute définition pour vous assurer qu’ils s’afficheront toujours comme il se doit.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Accélérer les téléchargements de pages à l’aide SharePoint rendus d’image

Les rendus d’image sont une fonctionnalité de SharePoint Online qui vous permet de servir différentes versions d’images en fonction de dimensions d’image prédéfinées. Ceci est particulièrement important lorsqu’il existe du contenu d’image généré par l’utilisateur ou que les dimensions d’image telles que la largeur et la hauteur sont corrigées par le CSS sur le site. Même si une image est corrigée par CSS, l’image de résolution complète est toujours chargée. Dans ce cas, la taille du fichier peut être réduite à l’aide des rendus d’image.
  
> [!NOTE]
> Les rendus ne sont disponibles que pour SharePoint lorsque la publication est activée. Vous pouvez activer la publication sous Paramètres Site Paramètres Gérer les fonctionnalités de \> \> site SharePoint Server \> Publishing. L’option n’apparaîtra pas autrement.
  
Le re dimensionnement du rendu d’image fonctionne en prenant la plus petite dimension que vous définissez, largeur ou hauteur, puis en re dimensionnant l’image de sorte que l’autre dimension soit automatiquement re dimensionné en fonction des proportions verrouillées. Par défaut, elle rognait l’image du centre par les dimensions restantes. Par exemple, si vous définissez un rendu de 100 px de large et de 50 px de haut et que votre image d’origine a une largeur de 1 000 px et une hauteur de 800 px, elle sera re dimensionné de sorte que la dimension 800px soit maintenant de 50 px et que la dimension 1 000 px (désormais 62,5 px) soit rogné du centre de l’image.
  
Les étapes sont relativement simples, mais pour que les images utilisent les rendus, les rendus doivent être sur le site SharePoint avant d’ajouter les images. En outre, les fonctionnalités infrastructure de publication de serveur SharePoint (niveau collection de sites) et SharePoint Server Publishing (niveau site) doivent également être allumées.
  
### <a name="add-an-image-rendition-to-speed-up-page-loading"></a>Ajouter un rendu d’image pour accélérer le chargement de la page
  
1. Vérifiez que le compte d’utilisateur qui exécute cette procédure dispose au minimum d’autorisations de conception sur le site de niveau supérieur de la collection de sites et que le site est publié sur une page web.

2. Dans un navigateur web, allez sur le site de niveau supérieur de la collection de sites de publication.

3. Choisissez l'icône **Paramètres**.

4. Dans la page **Paramètres** site, dans la **section** Apparence, vous verrez les rendus d’image intégrés.

    Vous pouvez utiliser les rendus « out of the box » ou choisir **rendus d’image** pour en créer un nouveau.

    ![Capture d’écran du rendu d’image](../media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. Sur la page **Rendus d’image**, sélectionnez **Ajouter un nouvel élément**.

    ![Capture d’écran de l’option Ajouter un nouvel élément](../media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. Sur la page **Nouveau rendu d'Image**, dans la zone **Nom**, saisissez un nom pour le rendu.

7. Dans les zones de texte **Largeur** et **Hauteur**, saisissez la largeur et la hauteur, en pixels, du rendu voulu, puis choisissez **Enregistrer**.

    ![Capture d’écran du nom de rendu d’image](../media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions"></a>Rognage personnalisé avec rendus d’image

Par défaut, un rendu d'image est généré à partir du centre de l'image. Vous pouvez régler le rendu d'image de chaque image en détourant la partie de l'image que vous souhaitez utiliser. Vous pouvez rogner les images individuellement, par rendu. Rogner les images accélère le chargement de la page à l’aide du cache blob de SharePoint pour créer une version de l’image pour chaque rendu. De cette façon, la charge du serveur est réduite, car l’image n’est re resa capacité qu’une seule fois et est ensuite prête à servir aux utilisateurs finaux plusieurs fois. Pour plus d’informations sur la rogner un rendu d’image, voir [Rogner un rendu d’image.](/sharepoint/dev/general-development/sharepoint-design-manager-device-channels)
