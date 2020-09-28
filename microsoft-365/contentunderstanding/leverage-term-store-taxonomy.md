---
title: Utilisation de la taxonomie de magasin de termes lors de la création d’un extracteur
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/1/2020
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Utiliser la taxonomie de magasin de termes lors de la création d’un extracteur dans votre modèle de présentation de document dans Microsoft SharePoint Syntex.
ms.openlocfilehash: 94f7a0389d2f06e0f8c1a60a341a02e43dfb2071
ms.sourcegitcommit: 15be7822220041c25fc52565f1c64d252e442d89
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "48295861"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor"></a>Utilisation de la taxonomie de magasin de termes lors de la création d’un extracteur


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSoL]

</br>

Lorsque vous créez un extracteur dans votre modèle de présentation de document dans SharePoint Syntex, vous pouvez tirer parti de la taxonomie de magasin de termes [services de métadonnées gérées](https://docs.microsoft.com/sharepoint/managed-metadata#terms) pour afficher les termes préférés des données que vous extrayez.  

Par exemple, votre modèle identifie et classe tous les documents de **contrat** téléchargés vers la bibliothèque de documents.  En outre, le modèle extrait également une valeur de **service de contrat** de chaque contrat et l’affiche dans une colonne de votre vue de bibliothèque. Parmi les différentes valeurs de services contractuels dans les contrats, il existe plusieurs valeurs plus anciennes que votre société n’utilise plus et qui ont été renommées. Par exemple, toutes les références à la *conception*des termes, aux *graphiques*ou aux services contractuels *topographiques* doivent maintenant être nommées *Creative*. Chaque fois que votre modèle extrait l’un des termes obsolètes d’un document de contrat, vous voulez qu’il affiche le terme « Creative » dans votre vue de bibliothèque. Dans l’exemple ci-dessous, lors de la formation du modèle, nous voyons qu’un exemple de document contient le terme de *conception*obsolète.

   ![Banque de termes](../media/content-understanding/design.png)</br>


## <a name="term-set-synonyms"></a>Synonymes de l’ensemble de termes 

Les ensembles de termes sont configurés dans le magasin de termes services de métadonnées gérées dans le centre d’administration SharePoint. Dans l’exemple ci-dessous, l' [ensemble de termes](https://docs.microsoft.com/sharepoint/managed-metadata#term-set) *services contractuel* est configuré pour inclure un certain nombre de termes, y compris *Creative*.  Les détails s’affichent pour indiquer que le terme a trois synonymes (*conception*, *graphiques*et *topographie*) et que les synonymes doivent être traduits en *éléments créatifs*.

   ![Ensemble de termes](../media/content-understanding/term-store.png)</br>

<Mike, je ne sais pas comment le décrire.  Quelle action indique au modèle que lors de la création d’un extracteur pour extraire et afficher une colonne services de contrat, comment cette colonne est-elle « marquée » pour utiliser l’ensemble de termes de métadonnées gérées pour les services Creative ? >

## <a name="configure-your-document-library-site-column-for-a-managed-metadata-field"></a>Configurer votre colonne de site de bibliothèque de documents pour un champ de métadonnées gérées


   ![Créer des métadonnées gérées](../media/content-understanding/creative.png)</br>

## <a name="see-also"></a>Voir aussi
[Présentation des métadonnées gérées](https://docs.microsoft.com/sharepoint/managed-metadata#terms)</br>
[Créer un extracteur](create-an-extractor.md)</br>
[Créer une colonne de métadonnées gérées](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)</br>





