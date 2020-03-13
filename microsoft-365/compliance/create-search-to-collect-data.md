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
description: ''
ms.openlocfilehash: 47d30cb2da91eff1260ffcf07838bd066917b4a1
ms.sourcegitcommit: dcea75af89f5f80ec6670346ee176407e043de54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "42610641"
---
# <a name="create-a-search"></a>Créer une recherche

Sous l’onglet **recherches** de votre cas, vous pouvez créer une nouvelle recherche en cliquant sur **nouvelle recherche** et en suivant l’Assistant.

![Assistant recherche dans un cas avancé eDiscovery](../media/AeDSearch1.png)

## <a name="name-the-search-and-give-it-a-description"></a>Nommez la recherche et donnez-lui une description.

Chaque recherche avec un cas doit avoir un nom unique. Vous pouvez éventuellement fournir une description pour votre recherche. 

## <a name="choose-the-custodians-and-custodial-locations-to-search"></a>Choisir les dépositaires et les lieux de recherche

Choisissez les emplacements de contenu de dépositaire à rechercher en spécifiant les dépositaires que vous avez ajoutés à l’incident. En sélectionnant un dépositaire, vous lancez la recherche par rapport à toutes les sources de données mappées au dépositaire. Vous avez également la possibilité de limiter la recherche aux sources de données sélectionnées pour chaque dépositaire. Pour plus d’informations sur la façon d’ajouter des dépositaires et de gérer leurs sources de données, consultez la rubrique [work with dépositaires](managing-custodians.md).

## <a name="choose-non-custodial-locations"></a>Choisir les emplacements non privatives de cœur

Dans certains cas, vous souhaiterez peut-être Rechercher des sources de données qui ne sont pas associées à un dépositaire. Dans ce cas, vous pouvez spécifier les emplacements de recherche, ou choisir de rechercher tous les emplacements de contenu pour un service Office 365 spécifique (par exemple, rechercher toutes les boîtes aux lettres Exchange ou tous les sites SharePoint et OneDrive).

## <a name="define-the-search-query-and-conditions"></a>Définir la requête de recherche et les conditions

Vous pouvez définir la requête de mots clés et les conditions de la recherche à l’aide des cartes de condition prédéfinies ou du langage de requête de mot clé (KQL). Pour plus d’informations, consultez la rubrique [créer des requêtes de recherche](building-search-queries.md).
