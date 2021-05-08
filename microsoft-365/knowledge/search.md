---
title: Utiliser Microsoft Search (recherche Microsoft) pour rechercher des rubriques dans les rubriques microsoft
ms.author: efrene
author: efrene
manager: pamgreen
ms.reviewer: cjtan
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: ''
localization_priority: None
description: Découvrez comment rechercher des rubriques dans Microsoft Microsoft Microsoft.
ms.openlocfilehash: 15b42c9d3689a73c865be53bb29f298fcbf896bd
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281041"
---
# <a name="use-microsoft-search-to-find-topics-in-microsoft-viva-topics"></a>Utiliser Microsoft Search (recherche Microsoft) pour rechercher des rubriques dans les rubriques microsoft

Bien que les utilisateurs de Rubriques Dev peuvent trouver des rubriques par le biais des points forts de rubriques sur leurs sites SharePoint sites, ils peuvent également les trouver par le biais de Microsoft Search (recherche Microsoft). 

## <a name="topic-answer"></a>Réponse à la rubrique

Lorsque vous recherchez une rubrique spécifique dans Recherche Microsoft (par exemple, « Saturne »), si une rubrique existe et est trouvée, elle affiche le résultat au format de suggestion Réponses.

La réponse à la rubrique s’affiche :
- Nom de la rubrique
- Autres noms : autres noms ou acronymes pour la rubrique.
- Définition : description de la rubrique fournie par l’IA ou ajoutée manuellement par une personne.
- Personnes suggérées ou épinglées : personnes suggérées par l’IA ou épinglées à la rubrique par une personne
- Ressources suggérées ou épinglées : fichiers, pages ou sites suggérés par l’IA ou épinglés à la rubrique par une personne. 

   ![Rubrique dans la recherche](../media/knowledge-management/search-topic-answer.png) 

La page de rubrique peut s’afficher dans les résultats de la recherche même si la carte de réponse de la rubrique n’apparaît pas.

Les résultats de la recherche dans Word et PowerPoint afficheront également la réponse à la rubrique lorsqu’une réponse est trouvée.


## <a name="acronyms"></a>Acronymes

Dans Rubriques de Contrôle, vous pouvez modifier manuellement une rubrique afin d’y inclure un acronyme en tant <b>qu’autre nom.</b> Cela permet à un utilisateur qui recherche uniquement l’acronyme de la rubrique de trouver la réponse à la rubrique par le biais de Microsoft Search (recherche Microsoft).

[Acronym Answers](/microsoftsearch/manage-acronyms) est une fonctionnalité fournie par Microsoft Search (recherche Microsoft) et est gérée séparément de Topics.

## <a name="bookmarks-and-topics"></a>Signets et rubriques

[Les signets](/microsoftsearch/manage-bookmarks) sont une fonctionnalité de Recherche Microsoft qui permet aux personnes de trouver rapidement des sites et des outils importants à l’aide d’une simple recherche (par exemple, un outil de réservation de voyage sur un site externe en dehors de leur client Microsoft 365). Ils sont créés par les administrateurs de recherche dans Microsoft 365'administration centrale. 

Pour les utilisateurs qui recherchent des informations sur la réservation d’un voyage pour le travail :

- Si certains utilisateurs connaissent le nom de l’outil de voyage (par exemple, « Concur ») il est plus facile de créer un signet pour aller directement sur le site externe.
- Pour les utilisateurs qui recherchent généralement « voyage », créez une rubrique sur « Voyage » avec les informations qu’ils s’attendent à voir. Envisagez d’ajouter un lien vers le site externe Concur dans la description de la rubrique. Si le lien est plutôt vers un site de réservation de voyage interne hébergé sur le client Microsoft 365, vous pouvez l’ajouter aux « ressources épinglées ».
 
### <a name="search-results-priority"></a>Priorité des résultats de la recherche 
 
Dans l’expérience de recherche des utilisateurs, lorsqu’un utilisateur recherche un terme comme « voyage », les résultats de la recherche s’affichent selon la priorité suivante dans Microsoft Search (recherche Microsoft)
1. Rubriques publiées ou confirmées 
2. Signets
3. Rubriques suggérées
