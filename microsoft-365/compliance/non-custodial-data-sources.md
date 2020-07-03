---
title: Ajout de sources de données non privatives de Troie à un cas avancé eDiscovery
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
description: Vous pouvez ajouter des sources de données non privatives de Troie à un cas avancé eDiscovery et mettre en attente la source de données. Les sources de données non privatives de cœur sont réindexées, de sorte que tout contenu considéré comme partiellement indexé est retraité afin de pouvoir faire l’objet d’une recherche complète et rapide.
ms.openlocfilehash: 2009a8cc82dc9407e9871409e85cdcd321ea9bb0
ms.sourcegitcommit: 51a9f34796535309b8ca8b52da92da0a3621327b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "45024744"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Ajout de sources de données non privatives de Troie à un cas avancé eDiscovery

Dans les cas de découverte électronique avancée, il ne répond pas toujours à vos besoins pour associer une source de données Microsoft 365 à un dépositaire dans le cas. Toutefois, vous devrez peut-être toujours associer ces données à un cas afin de les Rechercher, de les ajouter à l’ensemble de la révision et de les consulter. La nouvelle fonctionnalité *, appelée sources de données non privatives de ressources,* vous permet d’ajouter des données à un cas sans avoir à associer les données à un dépositaire. Elle applique également la même fonctionnalité eDiscovery avancée aux données non privatives de Troie qui sont disponibles pour les données associées aux dépositaires. Deux des fonctionnalités les plus utiles que vous pouvez appliquer à des données non privatives de temps sont placées en conservation et traitées à l’aide de l' [indexation avancée](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Ajouter une source de données non-privatives de cœur

Procédez comme suit pour ajouter et gérer des sources de données non privatives de Troie dans un cas avancé de découverte électronique.

1. Sur la page d’accueil de la **découverte électronique avancée** , cliquez sur le cas auquel vous souhaitez ajouter les données.

2. Sur la page **sources** , cliquez sur l’onglet **emplacements de données** , puis cliquez sur Ajouter un emplacement de **données**.

3. Cliquez sur **Ajouter un emplacement de données** , puis choisissez les sources de données que vous souhaitez ajouter à l’incident. Vous pouvez ajouter plusieurs sites et boîtes aux lettres.

4. Dans la page **choisir les emplacements** de l’Assistant, ajoutez des boîtes aux lettres ou des sites (ou les deux) comme sources de données non-privatives de ressources pour le cas.

5. Après avoir ajouté les sources de données, cliquez sur **suivant**.

6. Sur la page **Placer** en attente, choisissez les sources de données que vous souhaitez mettre en attente en activant ou en désactivant la case à cocher associée.

7. Vérifiez les sélections de blocage, puis cliquez sur **Envoyer**.

   Chaque source de données qui n’est pas une source de données non privatives ajoutée est indiquée dans la page **sources de données** .

   De plus, un travail d' *indexation des données non privatives* de responsabilité est créé et affiché sous l’onglet **travaux** de l’incident. Une fois le travail créé, le processus d’indexation avancé dans initié et les sources de données sont réindexés.

## <a name="managing-the-hold-on-non-custodial-data-sources"></a>Gestion de la conservation sur des sources de données non-privatives de cœur

Une fois que vous avez placé une conservation sur une source de données non privatives de place, une stratégie de blocage contenant toutes les sources de données non privatives de l’incident est automatiquement créée. Lorsque vous placez des sources de données non privatives de conservation supplémentaires, elles sont ajoutées à cette stratégie de blocage.

1. Sur la page d' **Accueil** de l’incident, cliquez sur l’onglet **suspensions** .

2. Sur la page **suspensions** , cliquez sur **NCDSHold \<GUID\> -**, où la valeur GUID est unique pour le cas.

3. Sur la page de la fenêtre déroulante, cliquez sur **modifier le blocage** pour afficher toutes les sources de données non-privatives de stock mises en attente.

Vous pouvez effectuer la tâche de gestion suivante sur des sources de données non privatives de Troie :

- Vous pouvez modifier la conservation pour créer une conservation basée sur une requête qui est appliquée à toutes les sources de données non-privatives dans le cas.

- Vous pouvez libérer une source de données non privatives de personnes à partir de la suspension. La libération d’une source de données ne supprime pas la source de données non privatives de la casse. Il supprime uniquement le blocage passé sur la source de données.
