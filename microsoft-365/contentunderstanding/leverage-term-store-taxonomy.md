---
title: Tirer parti de la taxonomie du magasin de termes lors de la création d’un extracteur dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Utilisez la taxonomie du magasin de termes lors de la création d’un extracteur dans votre modèle dans Microsoft Syntex.
ms.openlocfilehash: 71ac6c7452303362d503132d6a049acf86e59bf1
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659606"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-syntex"></a>Tirer parti de la taxonomie du magasin de termes lors de la création d’un extracteur dans Microsoft Syntex

<sup>**S’applique à :**  &ensp; &#10003; traitement de documents non structurés</sup>

<!---
</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>
--->

Lorsque vous créez un extracteur dans votre modèle de traitement de document non structuré à l’aide de Microsoft Syntex, vous pouvez tirer parti des ensembles de termes globaux dans le [magasin](/sharepoint/managed-metadata) de termes pour afficher les termes préférés pour les données que vous extrayez.  

Par exemple, votre modèle identifie et classe tous les documents **Contrat** chargés dans la bibliothèque de documents.  De plus, le modèle extrait également une valeur de **service de contrat** de chaque contrat et l’affiche dans une colonne de la vue de la bibliothèque. Les diverses valeurs de services des contrats incluent plusieurs éléments plus anciens, à présent inutilisés par votre société et renommés. Par exemple, toutes les références aux termes *Conception*, *Graphiques* ou *Topographie* (services de contrat) doivent à présent recevoir l’appellation *Créatif*. Chaque fois que votre modèle extrait l’une des conditions obsolètes d’un document de contrat, vous souhaitez qu’il affiche le terme actuel( *Creative*) dans votre vue de bibliothèque. Dans l’exemple suivant, lors de l’entraînement du modèle, nous voyons qu’un exemple de document contient le terme obsolète *De conception*.

   ![Magasin de termes.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Utiliser une colonne de métadonnées managées dans votre extracteur

Les ensembles de termes sont configurés dans le magasin de termes MMS (Managed Metadata Services) du <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">Centre d’administration SharePoint</a>. Dans l’exemple ci-dessous, *l’ensemble de termes* [Services de contrat](/sharepoint/managed-metadata#term-set) est configuré pour inclure un nombre de termes, y compris *Créatif*.  Les détails indiquent que le terme a trois synonymes (*Conception*, *Graphiques* et *Topographie*). Il convient de les renommer *Créatif*. 

   ![Ensemble de termes.](../media/content-understanding/term-store.png)</br>

Plusieurs raisons peuvent expliquer le désir d’utiliser un synonyme de votre ensemble de termes. Par exemple, cet ensemble peut inclure des termes obsolètes, des termes renommés ou des termes différents en fonction des services de votre organisation.

Pour pouvoir sélectionner le champ de métadonnées gérées lorsque vous créez l’extracteur dans votre modèle, vous devez [l’ajouter en tant que colonne de site de métadonnées gérées](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Après avoir ajouté la colonne de site, vous pouvez la sélectionner lorsque vous créez l’extracteur pour votre modèle.

   ![Service de contrat.](../media/content-understanding/contract-services.png)</br>

Une fois votre modèle appliqué à la bibliothèque de documents, lors du chargement des documents dans la bibliothèque, la colonne *Services de création* affiche le terme recommandé (*Créatif*) quand l’extracteur trouve l’une des valeurs synonymes (*Conception*, *Graphiques* et *Topographie*).

   ![Colonne Service de contrat.](../media/content-understanding/creative.png)</br>

> [!NOTE]
> Si l’ensemble de termes est ouvert, toutes les valeurs extraites qui ne correspondent pas à une valeur de terme ou de synonyme préférée sont ajoutées en tant que nouveau terme à la racine de l’ensemble de termes. Ces nouveaux termes peuvent être déplacés, fusionnés ou créés en synonymes dans le magasin de termes où réside l’ensemble de termes.

## <a name="see-also"></a>Voir aussi

[Présentation des métadonnées gérées](/sharepoint/managed-metadata#terms)

[Créer un extracteur](create-an-extractor.md)

[Créer une colonne de métadonnées gérées](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)