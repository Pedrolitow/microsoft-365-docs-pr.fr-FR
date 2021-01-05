---
title: Statistiques de recherche dans la découverte électronique avancée
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Valider les résultats de la recherche en affichant les statistiques générées après l’exécution d’une recherche de collection dans Advanced eDiscovery.
ms.openlocfilehash: 5b6cfdaffc7851a00035a4edcc9d490b229c455d
ms.sourcegitcommit: 98b889e674ad1d5fa37d4b6c5fc3eda60a1d67f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "49750775"
---
# <a name="search-statistics-in-advanced-ediscovery"></a>Statistiques de recherche dans Advanced eDiscovery

Vous pouvez valider vos résultats de recherche en examinant les statistiques de vos résultats afin de vous assurer qu’ils correspondent à vos attentes. Une fois la recherche terminée, les statistiques de haut niveau apparaissent dans la fenêtre d’affichage des détails de la recherche :

- Nombre et volume d’éléments récupérés par la recherche

- Nombre et volume d’éléments partiellement indexés ou non indexés qui ont été trouvés dans les emplacements de recherche

- Nombre de boîtes aux lettres et d’emplacements recherchés.
Pour afficher des statistiques plus détaillées, cliquez sur « statistiques » dans la fenêtre mobile des détails de recherche.

## <a name="summary-view"></a>Affichage de synthèse

Dans l’affichage de synthèse, vous pouvez voir les résultats de la recherche décomposés par type d’emplacement (par exemple, Exchange). Pour chaque type d’emplacement, vous pouvez voir :

- Nombre d’emplacements qui ont des éléments correspondant aux conditions de recherche

- Nombre d’éléments à partir de ces emplacements qui correspondent aux conditions de recherche

- Volume total des éléments qui correspondent aux conditions de recherche.

## <a name="top-locations-view"></a>Affichage des emplacements les plus fréquents

Dans la vue des emplacements supérieurs, vous voyez les différents emplacements avec le plus de correspondances. Pour chaque emplacement, vous verrez :

- Nom de l’emplacement (par exemple, URL SharePoint)

- Type d'emplacement

- Nombre d’éléments correspondant aux conditions de recherche

- Volume total des éléments qui correspondent aux conditions de recherche.

## <a name="queries-view"></a>Affichage de requêtes

Si vous avez utilisé (c :s) des lignes de mots clés ou de mots clés dans votre requête, vous pouvez voir la répartition de votre requête en mode requêtes par type d’emplacement. Pour chaque type d’emplacement, vous verrez :

- Part : cette colonne aura le mot « Primary » ou « Keyword ». « Primary » signifie que la ligne présente des statistiques sur l’ensemble de la requête, tandis que « Keyword » désigne l’un des composants de la requête.

- Requête : le composant de requête réel auquel la ligne fait référence. Si la partie est « principale », il s’agit de la requête entière ; Si la partie était « mot clé », vous verrez l’un des composants de requête ici.
  
  - Lorsque vous effectuez une recherche dans toutes les boîtes aux lettres de contenu (en ne spécifiant aucun mot-clé), la requête réelle est (taille >= 0) de sorte que tous les éléments soient renvoyés.
  
  - Lorsque vous effectuez des recherches dans des sites SharePoint Online et OneDrive entreprise, les deux composants suivants sont ajoutés :
    
    - NON IsExternalContent : 1-exclut le contenu d’une organisation SharePoint locale
    
    - NON isOneNotePage : 1-exclut tous les fichiers OneNote, car il s’agit de doublons de tous les documents qui correspondent à la requête de recherche.

- Nombre d’emplacements qui ont des éléments correspondant aux conditions de recherche.

- Nombre d’éléments à partir de ces emplacements qui correspondent aux conditions de recherche.

- Volume total des éléments qui correspondent aux conditions de recherche.
