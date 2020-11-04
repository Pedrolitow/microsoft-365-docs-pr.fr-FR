---
title: Hiérarchisation des incidents dans Microsoft 365 Defender
description: Découvrez comment définir la priorité des incidents à partir de la file d’attente des incidents dans Microsoft 365 Defender
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
ms.openlocfilehash: 4369d51ed740af652be632ba0b8752c708d6c719
ms.sourcegitcommit: b64f36d3873fa0041b24bec029deb73ccfdfdbac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877218"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Hiérarchisation des incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Microsoft 365 Defender applique une analyse de corrélation et agrège toutes les alertes et les analyses associées de différents produits en un seul incident. Microsoft 365 Defender déclenche également des alertes uniques sur des activités qui peuvent uniquement être identifiées comme malveillantes en fonction de la visibilité de bout en bout que Microsoft 365 Defender a sur l’ensemble du parc et de la suite de produits. En procédant ainsi, Microsoft 365 Defender présente le plus grand récit d’attaque, ce qui permet à un analyste des opérations de sécurité de comprendre et de traiter les menaces complexes au sein de l’organisation.


La **file d’attente des incidents** affiche un ensemble d’incidents qui ont été signalés par plusieurs appareils, utilisateurs et boîtes aux lettres. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité.


![Image de la file d’attente des incidents](../../media/incidents-queue.png) 

Par défaut, la file d’attente dans le centre de sécurité Microsoft 365 affiche les incidents détectés au cours des 30 derniers jours. Le dernier incident se trouve en haut de la liste, ce qui vous permet de le voir en premier.

La file d’attente des incidents expose des colonnes personnalisables qui vous donnent une visibilité sur différentes caractéristiques de l’incident ou des entités qu’il contient. Cela vous permet de prendre une décision informée concernant la définition des priorités des incidents à gérer.

Pour une visibilité supplémentaire en un coup d’œil, le nom automatique des incidents génère des noms d’incidents en fonction des attributs d’alerte, tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : plusieurs *étapes incident sur plusieurs points de terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents ne verront pas leur nom modifié.

La file d’attente d’incidents expose également plusieurs options de filtrage, qui, lorsqu’elles sont appliquées, vous permettent d’effectuer un balayage général de tous les incidents existants dans votre environnement, ou de vous concentrer sur un scénario ou une menace spécifique. L’application de filtres dans la file d’attente des incidents permet de déterminer le type d’incident nécessitant une attention immédiate. 

## <a name="available-filters"></a>Filtres disponibles

### <a name="assigned-to"></a>Affectée à
Vous pouvez choisir d’afficher les alertes qui vous sont affectées ou gérées par Automation.

### <a name="categories"></a>Catégories
Choisissez des catégories pour vous concentrer sur des tactiques, des techniques ou des composants d’attaque spécifiques vus. 

### <a name="classification"></a>Classification
Filtrer les incidents en fonction des classifications des alertes associées. Les valeurs incluent les alertes vraies, les fausses alertes ou non définies.

### <a name="data-sensitivity"></a>Confidentialité des données
Certaines attaques se concentrent sur le ciblage de données sensibles ou précieuses. En appliquant un filtre pour déterminer si des données confidentielles sont impliquées dans l’incident, vous pouvez rapidement déterminer si des informations sensibles ont été compromises et hiérarchiser les problèmes.

>[!NOTE]
>Applicable uniquement si la protection des informations Microsoft est activée.

### <a name="device-group"></a>Groupe d’appareils
Filtrer par groupes d’appareils définis.

### <a name="investigation-state"></a>État de l’enquête
Filtrer les incidents selon l’état de l’analyse automatisée. 

### <a name="multiple-categories"></a>Plusieurs catégories 
Vous pouvez choisir d’afficher uniquement les incidents qui ont été mappés à plusieurs catégories et peuvent donc causer des dégâts plus importants. 

### <a name="multiple-service-sources"></a>Plusieurs sources de service 
Filtre pour afficher uniquement les incidents qui contiennent des alertes de sources différentes (Microsoft Defender pour les points de terminaison, sécurité des applications Cloud Microsoft, Microsoft Defender pour l’identité, Microsoft Defender pour Office 365).

### <a name="os-platform"></a>Plateforme de système d’exploitation
Limitez l’affichage de la file d’attente des incidents par système d’exploitation.

### <a name="service-sources"></a>Sources de service
En sélectionnant une source spécifique, vous pouvez vous concentrer sur les incidents qui contiennent au moins une alerte de la source choisie. 

### <a name="severity"></a>Severity
La gravité d’un incident est l’impact qu’il peut avoir sur vos biens. Plus la gravité est élevée, plus l’impact est important et nécessite une attention immédiate. 

### <a name="status"></a>Statut
Vous pouvez choisir de limiter la liste des incidents affichés en fonction de leur état pour identifier ceux qui sont actifs ou résolus.

>[!IMPORTANT]
>La classification, le groupe d’appareils, l’état de l’enquête et les filtres de plateforme du système d’exploitation sont actuellement disponibles uniquement en préversion publique.


## <a name="next-steps"></a>Étapes suivantes
Après avoir déterminé quel incident a besoin de la priorité la plus élevée, vous pouvez effectuer d’autres tâches d’examen sur un incident.
- [Enquêter sur des incidents](investigate-incidents.md)


## <a name="see-also"></a>Voir aussi
- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
