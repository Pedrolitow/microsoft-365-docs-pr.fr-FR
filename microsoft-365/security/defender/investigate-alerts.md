---
title: Examiner les alertes dans Microsoft 365 Defender
description: Examinez les alertes visibles sur les appareils, les utilisateurs et les boîtes aux lettres.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
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
ms.openlocfilehash: 601a8674327c424592c65014793599dc19b2bcd3
ms.sourcegitcommit: 07dea2aa98daf0c4086f8590375167830027c802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51759431"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Examiner les alertes dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Les alertes sont la base de tous les incidents et indiquent l'occurrence d'événements malveillants ou suspects dans votre environnement. Les alertes font généralement partie d'une attaque plus large et fournissent des indices sur un incident.

Dans Microsoft 365 Defender, les alertes associées sont regroupées pour former des incidents. Les incidents fournissent toujours le contexte plus large d'une attaque, mais l'analyse des alertes peut être utile lorsque des analyses plus approfondies sont nécessaires. 



## <a name="using-alert-pages-in-investigations"></a>Utilisation de pages d'alerte dans les enquêtes

À partir de l'onglet Alertes d'une page d'incident, la sélection d'une alerte vous amène aux pages d'alerte individuelles. Une page d'alerte se compose de trois sections : ressources affectées, article d'alerte et volet d'informations.

![Image d'exemple de page d'alerte](../../media/new-alert-page2.png)

Tout au long d'une page d'alerte, vous pouvez sélectionner l'icône à trois points (**...**) en regard de n'importe quelle entité afin de voir les actions disponibles, telles que l'ouverture de la page de biens spécifiques ou l'application d'étapes de correction spécifiques.

### <a name="analyze-affected-assets"></a>Analyser les ressources affectées
La section Ressources affectées répertorie les boîtes aux lettres, les appareils et les utilisateurs concernés par cette alerte. La sélection de l'une des cartes de biens remplit le volet latéral détails avec des informations, y compris d'autres alertes impliquant les biens, le cas caser.


### <a name="trace-an-alerts-role-in-the-alert-story"></a>Suivre le rôle d'une alerte dans l'article d'alerte
L'article d'alerte affiche toutes les ressources ou entités associées à l'alerte dans une arborescence de processus. L'alerte dans le titre est celle qui est sélectionnée lorsque vous vous pointez pour la première fois sur la page de votre alerte sélectionnée. Les ressources de l'article d'alerte sont ex expandables et peuvent être cliquées. Ils fournissent des informations supplémentaires et accélèrent la réponse en vous permettant d'agir directement dans le contexte de la page d'alerte. 

> [!NOTE]
> La section de l'article sur l'alerte peut contenir plusieurs alertes, avec des alertes supplémentaires liées à la même arborescence d'exécution apparaissant avant ou après l'alerte que vous avez sélectionnée.

### <a name="view-more-alert-information-in-the-details-pane"></a>Afficher plus d'informations sur les alertes dans le volet d'informations

Le volet d'informations affiche d'abord les détails de l'alerte sélectionnée, ainsi que les détails et les actions qui y sont associés. Si vous sélectionnez l'une des ressources ou entités concernées dans l'article d'alerte, le volet d'informations change pour fournir des informations contextuelles et des actions pour l'objet sélectionné.

Une fois que vous avez sélectionné une entité d'intérêt, le volet d'informations change pour afficher les informations sur le type d'entité sélectionné, les informations historiques lorsqu'elle est disponible et les options d'action sur cette entité directement à partir de la page d'alerte.

### <a name="manage-alerts"></a>Gérer des alertes

Une fois que vous avez terminé d'examiner les alertes, vous pouvez revenir à l'alerte que vous avez démarrée, marquer l'état de l'alerte comme résolu et le classer comme alerte False ou Alerte True. La classification des alertes permet d'affiner votre produit pour fournir plus d'alertes vraies et moins de fausses alertes.

> [!NOTE]
> Une façon de gérer les alertes via l'utilisation de balises. La fonctionnalité de marquage de Microsoft Defender pour Office 365 est déployée de manière incrémentielle et est actuellement en prévisualisation. <br>
> Actuellement, les noms de balise modifiés sont appliqués uniquement aux alertes créées *après la* mise à jour. Les alertes qui ont été générées avant la modification ne reflètent pas le nom de balise mis à jour. 


## <a name="manage-the-unified-alert-queue"></a>Gérer la file d'attente d'alerte unifiée

La sélection des alertes sous Incidents & alertes dans le volet de navigation du Centre de sécurité Microsoft 365 vous amène à la file d'attente d'alertes unifiée. Les alertes de différentes solutions de sécurité Microsoft telles que Microsoft Defender pour le point de terminaison, Microsoft Defender pour Office 365 et Microsoft 365 Defender apparaissent dans cette section. 

![Image de l'exemple de page d'alerte](../../media/unified-alert-queue.png)

La file d'attente Alertes affiche la liste des alertes qui ont été signalées dans votre réseau. Par défaut, la file d'attente affiche les alertes visibles au cours des 30 derniers jours. Les alertes les plus récentes sont affichées en haut de la liste pour vous aider à voir les alertes les plus récentes en premier.

> [!NOTE]
> Au moment du lancement, la file d'attente des alertes unifiées ne dispose que de 7 jours d'alertes Microsoft Defender pour Office 365 disponibles. La file d'attente continuera à se développer au fil du temps. Si vous devez trier les alertes avant le lancement de la file d'attente d'alertes unifiée, utilisez la file d'attente des alertes dans le Centre de sécurité [et conformité.](https://protection.office.com/viewalerts)


Sur la barre de navigation supérieure, vous pouvez :

- Appliquer des filtres
- Personnaliser des colonnes pour ajouter ou supprimer des colonnes
- Exporter des données

Vous pouvez également filtrer les alertes en fonction de différents critères :

- Severity
- Statut
- Catégorie
- Source de détection
- Stratégie
- Ressources impactées
- Première activité
- Dernière activité


Pour démarrer une enquête sur un incident, [lisez Examiner les incidents dans Microsoft 365 Defender](investigate-incidents.md)
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
