---
title: Hiérarchiser les incidents dans Microsoft 365 Defender
description: Découvrez comment filtrer les incidents à partir de la file d’attente des incidents dans Microsoft 365 Defender
keywords: incident, file d’attente, vue d’ensemble, appareils, identités, utilisateurs, boîte aux lettres, e-mail, incidents
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 5aba1ab4bed0eeb5f6127ab865ceea674e8d5902
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51501003"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Hiérarchiser les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Microsoft 365 Defender applique l’analyse de corrélation et regroupe toutes les alertes et enquêtes associées de différents produits en un seul incident. Microsoft 365 Defender déclenche également des alertes uniques sur les activités qui peuvent uniquement être identifiées comme malveillantes en raison de la visibilité de bout en bout de Microsoft 365 Defender sur l’ensemble du patrimoine et de la suite de produits. Cette vue donne à votre analyste des opérations de sécurité un niveau d’attaque plus large, ce qui lui permet de mieux comprendre et de gérer les menaces complexes au sein de l’organisation.


La **file d’attente des incidents** affiche un ensemble d’incidents qui ont été signalés par plusieurs appareils, utilisateurs et boîtes aux lettres. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité.


![Image de la file d’attente des incidents](../../media/incidents-queue.png) 

Par défaut, la file d’attente du Centre de sécurité Microsoft 365 affiche les incidents observés au cours des 30 derniers jours. L’incident le plus récent se trouve en haut de la liste pour que vous le voyez en premier.

La file d’attente des incidents expose des colonnes personnalisables qui vous donnent une visibilité sur les différentes caractéristiques de l’incident ou des entités contenues. Cela vous permet de prendre une décision éclairée concernant la hiér donc des incidents à gérer.

Pour une visibilité supplémentaire en un coup d’œil, l’appellation automatique des incidents génère des noms d’incident basés sur des attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : incident en plusieurs étapes sur plusieurs points de *terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents ne seront pas modifiés.

La file d’attente des incidents expose également plusieurs options de filtrage qui, lorsqu’elles sont appliquées, vous permettent d’effectuer un large éventail de tous les incidents existants dans votre environnement ou de décider de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

## <a name="available-filters"></a>Filtres disponibles

### <a name="assigned-to"></a>Affectée à
Vous pouvez choisir d’afficher les alertes qui vous sont affectées ou celles gérées par l’automatisation.

### <a name="categories"></a>Catégories
Choisissez des catégories pour vous concentrer sur des tactiques, des techniques ou des composants d’attaque spécifiques. 

### <a name="classification"></a>Classification
Filtrez les incidents en fonction des classifications définies des alertes associées. Les valeurs incluent des alertes vraies, des alertes fausses ou non définies.

### <a name="data-sensitivity"></a>Confidentialité des données
Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour déterminer si des données confidentielles sont impliquées dans l’incident, vous pouvez rapidement déterminer si des informations sensibles ont été compromises et hiérarchiser les problèmes.

>[!NOTE]
>Applicable uniquement si la protection des informations Microsoft est activée.

### <a name="device-group"></a>Groupe d’appareils
Filtrer par groupes d’appareils définis.

### <a name="investigation-state"></a>État de l’examen
Filtrer les incidents selon l’état de l’examen automatisé. 

### <a name="multiple-categories"></a>Plusieurs catégories 
Vous pouvez choisir de ne voir que les incidents qui ont été mappés à plusieurs catégories et qui peuvent donc potentiellement causer davantage de dommages. 

### <a name="multiple-service-sources"></a>Plusieurs sources de service 
Filtrez pour voir uniquement les incidents qui contiennent des alertes provenant de différentes sources (Microsoft Defender pour endpoint, Microsoft Cloud App Security, Microsoft Defender pour l’identité, Microsoft Defender pour Office 365).

### <a name="os-platform"></a>Plateforme du système d’exploitation
Limitez l’affichage de la file d’attente des incidents par système d’exploitation.

### <a name="service-sources"></a>Sources de service
En sélectionnant une source spécifique, vous pouvez vous concentrer sur les incidents qui contiennent au moins une alerte de la source choisie. 

### <a name="severity"></a>Severity
La gravité d’un incident indique l’impact qu’il peut avoir sur vos ressources. Plus la gravité est élevée, plus l’impact est important et nécessite généralement l’attention la plus immédiate. 

### <a name="status"></a>Statut
Vous pouvez choisir de limiter la liste des incidents affichés en fonction de leur état pour identifier ceux qui sont actifs ou résolus.




## <a name="next-steps"></a>Étapes suivantes
Après avoir déterminé quel incident a besoin de la priorité la plus élevée, vous pouvez effectuer d’autres tâches d’examen sur un incident.
- [Enquêter sur des incidents](investigate-incidents.md)


## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
