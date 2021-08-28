---
title: Tirez parti de la taxonomie du magasin de termes lors de la création d’un extracteur dans Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
localization_priority: Priority
description: Utilisez la taxonomie du magasin de termes lors de la création d’un extracteur dans votre modèle de compréhension de document via Microsoft SharePoint Syntex.
ms.openlocfilehash: 97ceace09ed4c8b1a8ea8daf6d562d8013533cea
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573726"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Tirez parti de la taxonomie du magasin de termes lors de la création d’un extracteur dans Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

Lorsque vous créez un extracteur dans votre modèle de compréhension de document via SharePoint Syntex, vous pouvez tirer parti des ensembles de termes globaux [Services de métadonnées gérées](/sharepoint/managed-metadata) pour afficher les termes recommandés concernant les données extraites.  

Par exemple, votre modèle identifie et classe tous les documents **Contrat** chargés dans la bibliothèque de documents.  De plus, le modèle extrait également une valeur de **service de contrat** de chaque contrat et l’affiche dans une colonne de la vue de la bibliothèque. Les diverses valeurs de services des contrats incluent plusieurs éléments plus anciens, à présent inutilisés par votre société et renommés. Par exemple, toutes les références aux termes *Conception*, *Graphiques* ou *Topographie* (services de contrat) doivent à présent recevoir l’appellation *Créatif*. Chaque fois que votre modèle extrait l’un des termes obsolètes d’un document contractuel, il doit afficher le terme à jour, à savoir Créatif, dans la vue de la bibliothèque. Dans l’exemple ci-après, lors de la formation du modèle, nous constatons qu’un exemple de document contient le terme obsolète *Conception*.

   ![Magasin de termes.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Utiliser une colonne de métadonnées gérées dans l’extracteur

Les ensembles de termes sont configurés dans le magasin de termes Services de métadonnées gérées (MMS) dans le Centre d’administration SharePoint. Dans l’exemple ci-dessous, *l’ensemble de termes* [Services de contrat](/sharepoint/managed-metadata#term-set) est configuré pour inclure un nombre de termes, y compris *Créatif*.  Les détails indiquent que le terme a trois synonymes (*Conception*, *Graphiques* et *Topographie*). Il convient de les renommer *Créatif*. 

   ![Ensemble de termes.](../media/content-understanding/term-store.png)</br>

Plusieurs raisons peuvent expliquer le désir d’utiliser un synonyme de votre ensemble de termes. Par exemple, cet ensemble peut inclure des termes obsolètes, des termes renommés ou des termes différents en fonction des services de votre organisation.

Pour pouvoir sélectionner le champ de métadonnées gérées lorsque vous créez l’extracteur dans votre modèle, vous devez [l’ajouter en tant que colonne de site de métadonnées gérées](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Après avoir ajouté la colonne de site, vous pouvez la sélectionner lorsque vous créez l’extracteur pour votre modèle.

   ![Service de contrat.](../media/content-understanding/contract-services.png)</br>

Une fois votre modèle appliqué à la bibliothèque de documents, lors du chargement des documents dans la bibliothèque, la colonne *Services de création* affiche le terme recommandé (*Créatif*) quand l’extracteur trouve l’une des valeurs synonymes (*Conception*, *Graphiques* et *Topographie*).

   ![Colonne Service de contrat.](../media/content-understanding/creative.png)</br>


## <a name="see-also"></a>Voir aussi
[Présentation des métadonnées gérées](/sharepoint/managed-metadata#terms)

[Créer un extracteur](create-an-extractor.md)

[Créer une colonne de métadonnées gérées](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)