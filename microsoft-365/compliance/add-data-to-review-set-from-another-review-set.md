---
title: Ajouter des données d’un ensemble de révisions à un autre
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/05/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment sélectionner des documents dans un ensemble de révisions et les utiliser individuellement dans un autre ensemble dans un cas de découverte électronique Microsoft Purview (Premium).
ms.custom:
- seo-marvel-mar2020
- seo-marvel-apr2020
ms.openlocfilehash: deb0389a4f4bd9bafedd3b2a8dd6c367c6e78fbb
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941168"
---
# <a name="add-data-to-a-review-set-from-another-review-set"></a>Ajouter des données à partir d’un groupe de révision à un autre groupe de révision.

Dans certains cas, il peut être nécessaire de sélectionner des documents dans un ensemble de révisions et de les utiliser individuellement dans un autre ensemble de révisions. Cette fonctionnalité est particulièrement utile si vous avez éliminé du contenu dans un ensemble de révision et que vous voulez exécuter des analyses sur le sous-ensemble de données.

Suivez le flux de travail de cet article pour ajouter du contenu d’un ensemble de révisions à un autre.

## <a name="create-a-review-set"></a>Créer un ensemble de révisions

Avant de commencer, vous devez créer un ensemble de révisions à laquelle ajouter les données.  Un nouvel ensemble de révision peut être ajouté sous l’onglet **Ensembles** de révision du cas. Pour plus d’informations, consultez [Créer un ensemble de révisions](managing-review-sets.md#create-a-review-set).

## <a name="step-1-identify-content-to-add-to-another-review-set"></a>Étape 1 : Identifier le contenu à ajouter à un autre ensemble de révisions

Vous pouvez ajouter du contenu d’un ensemble de révision à un autre en sélectionnant des documents spécifiques dans l’ensemble de révision source ou en sélectionnant tous les éléments renvoyés par la requête de révision. Si vous ajoutez des éléments sélectionnés, sélectionnez les éléments, sélectionnez **Action**, puis **sélectionnez Ajouter à un autre jeu de révision**.

![Ajoutez à un autre ensemble de révisions dans le menu Action.](../media/64f2a4d4-eba3-4ab3-a3ba-d519feea3142.png)

## <a name="step-2-specify-options-for-adding-to-another-review-set"></a>Étape 2 : Spécifier les options d’ajout à un autre jeu de révision

Dans la page de menu volant **Ajouter à un autre ensemble de révisions** , choisissez l’ensemble de révision auquel vous souhaitez ajouter les éléments. Indiquez s’il faut ajouter **tous les résultats de la recherche** ou **les éléments sélectionnés**.  **Des informations supplémentaires** fournissent des options permettant d’inclure toutes les métadonnées des éléments et d’inclure les balises (en cochant la case **Étiquettes** ) dans le jeu de révision source lorsque les documents sont ajoutés au nouveau jeu de révision.  

![Options permettant d’ajouter des données à un autre jeu de révision.](../media/6440ee44-68fd-44d7-b43a-3a477345525c.png)

Une fois que vous avez cliqué sur **OK**, un nouveau travail (nommé **Ajout de données à un autre jeu de révision**) est créé pour ajouter le contenu à un autre jeu de révision. Vous pouvez accéder à l’onglet **Travaux** et surveiller la progression de ce travail. Pour plus d’informations, consultez [Gérer les travaux](managing-jobs-ediscovery20.md).
