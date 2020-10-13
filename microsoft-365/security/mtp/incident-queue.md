---
title: Hiérarchiser les incidents dans la Protection Microsoft contre les menaces
description: Découvrir comment hiérarchiser les incidents à partir de la file d’attente des incidents dans la Protection Microsoft contre les menaces
keywords: incident, file d’attente, vue d’ensemble, appareils, identités, utilisateurs, boîte aux lettres, e-mail, incidents
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 382cfd374c40d0c5a0dd7d7705281bd56263d8b8
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430822"
---
# <a name="prioritize-incidents-in-microsoft-threat-protection"></a>Hiérarchiser les incidents dans la Protection Microsoft contre les menaces

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces



La Protection Microsoft contre les menaces applique l’analyse de la corrélation et regroupe toutes les alertes et analyses associées à différents produits en un seul incident. La Protection Microsoft contre les menaces déclenche également des alertes uniques pour les activités qui peuvent uniquement être détectées comme malveillantes, en raison de la visibilité de bout en bout que la Protection Microsoft de la protection de menace a sur l’ensemble du patrimoine et de la suite de produits. En procédant ainsi, la Protection Microsoft contre les menaces donne une vue d’ensemble des attaques, ce qui permet à un analyste en charge des opérations de sécurité de comprendre et de gérer les menaces complexes au sein de l’organisation.


La **file d’attente des incidents** affiche un ensemble d’incidents qui ont été signalés par plusieurs appareils, utilisateurs et boîtes aux lettres. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité.


![Image de la file d’attente des incidents](../../media/incidents-queue.png) 

Par défaut, la file d’attente dans le Centre de sécurité Microsoft 365 affiche les incidents détectés au cours des 30 derniers jours, l’incident le plus récent apparaissant en tête de liste, qui vous permet d’accéder en avant-première aux incidents les plus récents.

La file d’attente des incidents présente les colonnes personnalisables qui vous permettent de tirer parti des différentes caractéristiques de l’incident ou des entités qu’il contient, ce qui vous permet de prendre une décision éclairée sur la hiérarchisation des incidents à traiter.

Pour une visibilité supplémentaire en un coup d’œil, le nom automatique des incidents génère des noms d’incidents en fonction des attributs d’alerte, tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : plusieurs *étapes incident sur plusieurs points de terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents ne verront pas leur nom modifié.

La file d’attente des incidents présente également plusieurs options de filtrage, qui, lorsqu’elles sont appliquées, vous permettent de choisir d’effectuer un large éventail de tous les incidents existants dans votre environnement, ou de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

## <a name="available-filters"></a>Filtres disponibles

### <a name="status"></a>Statut
Vous pouvez choisir de limiter la liste des incidents affichés en fonction de leur état pour identifier ceux qui sont actifs ou résolus.

### <a name="severity"></a>Gravité
La gravité d'un incident est indicative de l'impact qu'il peut avoir sur vos actifs. Plus la gravité est élevée, plus l’impact est important et nécessite une attention immédiate. 

### <a name="assigned-to-owner"></a>Assignée à (propriétaire)
Vous pouvez choisir de filtrer la liste en sélectionnant ceux qui vous sont affectés ou ceux qui vous sont affectés.

### <a name="multiple-alerts"></a>Plusieurs alertes 
Filtre pour afficher uniquement les incidents contenant plusieurs alertes. Il peut s’agir d’une indication d’une attaque plus complexe ou plus avancée dans la chaîne de terminaison. 


### <a name="multiple-service-sources"></a>Plusieurs sources de service 
Filtre pour afficher uniquement les incidents qui contiennent des alertes provenant de différentes sources (Microsoft Defender - Protection avancée contre les menaces, Microsoft Cloud App Security, Azure - Protection avancée contre les menaces, Office 365 - Protection avancée contre les menaces)
### <a name="service-sources"></a>Sources de service
En sélectionnant une source spécifique, vous pouvez vous concentrer sur les incidents qui contiennent au moins une alerte de la source choisie. 

### <a name="multiple-categories"></a>Plusieurs catégories 
Vous pouvez choisir d’afficher uniquement les incidents qui ont été mappés à plusieurs catégories de la chaîne de terminaison et qui peuvent causer des dommages plus importants. 

### <a name="categories"></a>Catégories
Choisir des catégories spécifiques pour vous concentrer sur une étape spécifique de la chaîne de terminaison

### <a name="data-sensitivity"></a>Confidentialité des données
Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour déterminer si des données confidentielles sont impliquées dans l’incident, vous pouvez rapidement déterminer si des informations sensibles ont été compromises et hiérarchiser les problèmes.

>[!NOTE]
>Applicable uniquement si la protection des informations Microsoft est activée.


## <a name="next-steps"></a>Étapes suivantes
Après avoir déterminé quel incident a besoin de la priorité la plus élevée, vous pouvez effectuer d’autres tâches d’examen sur un incident.
- [Enquêter sur des incidents](investigate-incidents.md)


## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
