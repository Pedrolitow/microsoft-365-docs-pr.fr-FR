---
title: Créer une recherche
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez comment créer, définir et choisir des dépositaires et des emplacements de conservation pour une recherche dans Advanced eDiscovery cas.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 1d9051824ff3f28484d0750b982edd70334a9b88
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44035766"
---
# <a name="create-a-search"></a>Créer une recherche

Sous **l’onglet Recherches** dans votre cas, vous pouvez créer une recherche en cliquant sur **Nouvelle** recherche et en suivant l’Assistant.

![Assistant recherche dans un cas Advanced eDiscovery recherche](../media/AeDSearch1.png)

## <a name="name-the-search-and-give-it-a-description"></a>Nommez la recherche et donnez-lui une description

Chaque recherche avec un cas doit avoir un nom unique. Vous pouvez éventuellement fournir une description de votre recherche. 

## <a name="choose-the-custodians-and-custodial-locations-to-search"></a>Choisir les dépositaires et les emplacements de conservation à rechercher

Choisissez les emplacements de contenu des dépositaires à rechercher en spécifiant les dépositaires que vous avez ajoutés au cas. En sélectionnant un dépositaire, vous exécutez la recherche sur toutes les sources de données mappées au dépositaire. Vous avez également la possibilité de restreindre la recherche aux sources de données sélectionnées pour chaque dépositaire. Pour plus d’informations sur l’ajout de dépositaires et la gestion de leurs sources de données, voir [Travailler avec les dépositaires.](managing-custodians.md)

## <a name="choose-non-custodial-locations"></a>Choisir des emplacements non privatives

Dans certains cas, vous pouvez rechercher des sources de données qui ne sont pas associées à un dépositaire. Dans ce cas, vous pouvez spécifier les emplacements que vous souhaitez rechercher ou choisir de rechercher tous les emplacements de contenu pour un service Microsoft spécifique (par exemple, la recherche dans toutes les boîtes aux lettres Exchange ou tous les sites SharePoint et les comptes OneDrive).

## <a name="define-the-search-query-and-conditions"></a>Définir la requête de recherche et les conditions

Vous pouvez définir la requête de mots clés et toutes les conditions de la recherche à l’aide des cartes de condition pré-conçues ou à l’aide du langage KQL (Keyword Query Language). Pour plus d’informations, voir [Créer des requêtes de recherche.](building-search-queries.md)
