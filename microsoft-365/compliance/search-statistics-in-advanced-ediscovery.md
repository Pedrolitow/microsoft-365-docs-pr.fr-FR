---
title: Statistiques de recherche dans Advance eDiscovery
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
description: Validez vos résultats de recherche en visualxant les statistiques générées après avoir exécuté une recherche de collection dans Advanced eDiscovery.
ms.openlocfilehash: 5b6cfdaffc7851a00035a4edcc9d490b229c455d
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59175772"
---
# <a name="search-statistics-in-advanced-ediscovery"></a>Statistiques de recherche dans Advanced eDiscovery

Une façon de valider vos résultats de recherche consiste à examiner les statistiques relatives à vos résultats pour vous assurer qu’ils correspondent à vos attentes. Lorsqu’une recherche est terminée, des statistiques de haut niveau sont affichées dans le volant des détails de la recherche :

- Nombre et volume d’éléments récupérés par la recherche

- Nombre et volume d’éléments partiellement indexés ou non indexés trouvés dans les emplacements de recherche

- Nombre de boîtes aux lettres et d’emplacements recherchés.
Pour afficher des statistiques plus détaillées, cliquez sur « Statistiques » dans le volant des détails de la recherche.

## <a name="summary-view"></a>Affichage récapitulatif

Dans l’affichage Résumé, vous pouvez voir les résultats de la recherche décomposés par type d’emplacement (par exemple, Exchange). Pour chaque type d’emplacement, vous pouvez voir :

- Nombre d’emplacements dont les éléments correspondent aux conditions de recherche

- Nombre d’éléments provenant de ces emplacements qui correspondent aux conditions de recherche

- Volume total d’éléments qui correspondent aux conditions de recherche.

## <a name="top-locations-view"></a>Affichage des emplacements supérieurs

Dans l’affichage Emplacements supérieurs, vous voyez les emplacements individuels avec le plus de correspondances. Pour chaque emplacement, vous verrez :

- Nom de l’emplacement (par exemple, SharePoint URL)

- Type d'emplacement

- Nombre d’éléments qui correspondent aux conditions de recherche

- Volume total d’éléments qui correspondent aux conditions de recherche.

## <a name="queries-view"></a>Affichage des requêtes

Si vous avez utilisé (c:s) des lignes de mot clé ou de mot clé dans votre requête, vous pouvez voir la répartition de votre requête dans l’affichage Requêtes par type d’emplacement. Pour chaque type d’emplacement, vous verrez :

- Partie : cette colonne aura le mot « Primary » ou « Keyword ». « Principal » signifie que la ligne présente des statistiques sur l’ensemble de la requête, tandis que « Mot clé » signifie l’un des composants de requête.

- Requête : composant de requête réel à qui la ligne fait référence. Si la partie est « Primaire », il s’agit de la requête entière ; Si la partie était « Mot clé », vous verrez l’un des composants de requête ici.
  
  - Lorsque vous recherchez dans toutes les boîtes aux lettres de contenu (en ne spécifiant aucun mot clé), la requête réelle est (taille >= 0) afin que tous les éléments soient renvoyés.
  
  - Lorsque vous recherchez SharePoint online et OneDrive Entreprise sites web, les deux composants suivants sont ajoutés :
    
    - NOT IsExternalContent:1 : exclut tout contenu d’une organisation SharePoint local
    
    - NOT isOneNotePage: 1 - exclut tous les fichiers OneNote car il s’agit de doublons de tout document qui correspond à la requête de recherche.

- Nombre d’emplacements dont les éléments correspondent aux conditions de recherche.

- Nombre d’éléments provenant de ces emplacements qui correspondent aux conditions de recherche.

- Volume total d’éléments qui correspondent aux conditions de recherche.
