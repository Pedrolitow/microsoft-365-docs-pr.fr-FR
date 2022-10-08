---
title: Afficher et organiser la file d’attente des incidents
ms.reviewer: ''
description: Consultez la liste des incidents et découvrez comment appliquer des filtres pour limiter la liste et obtenir une vue plus ciblée.
keywords: afficher, organiser, incidents, agrégat, investigations, file d’attente, ttp
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 6d5bf3935b9b12ffc6e892f1e0d8f1a0f1fa7d92
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68232867"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-incidents-queue"></a>Afficher et organiser la file d’attente d’incidents Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

La **file d’attente Incidents** affiche une collection d’incidents qui ont été signalés à partir d’appareils de votre réseau. Elle vous aide à trier les incidents afin de hiérarchiser et de créer une décision de réponse cyber-sécurité.

Par défaut, la file d’attente affiche les incidents observés au cours des 30 derniers jours, l’incident le plus récent s’affichant en haut de la liste, ce qui vous aide à voir les incidents les plus récents en premier.

Vous pouvez choisir parmi plusieurs options pour personnaliser l’affichage de la file d’attente Incidents. 

En haut de la navigation, vous pouvez :
- Personnaliser des colonnes pour ajouter ou supprimer des colonnes 
- Modifier le nombre d’éléments à afficher par page
- Sélectionner les éléments à afficher par page
- Sélectionner par lot les incidents à affecter 
- Naviguer entre les pages
- Appliquer des filtres
- Personnaliser et appliquer des plages de dates

:::image type="content" source="images/atp-incident-queue.png" alt-text="File d’attente Incidents" lightbox="images/atp-incident-queue.png":::

## <a name="sort-and-filter-the-incidents-queue"></a>Trier et filtrer la file d’attente d’incidents
Vous pouvez appliquer les filtres suivants pour limiter la liste des incidents et obtenir une vue plus ciblée.

### <a name="severity"></a>Severity

Gravité de l’incident | Description
:---|:---
Élevé </br>(Rouge) | Menaces souvent associées à des menaces persistantes avancées (APT). Ces incidents indiquent un risque élevé en raison de la gravité des dommages qu’ils peuvent infliger aux appareils.
Moyen </br>(Orange) | Menaces rarement observées dans l’organisation, telles que les modifications anormales du Registre, l’exécution de fichiers suspects et les comportements observés typiques des phases d’attaque.
Faible </br>(Jaune) | Menaces associées aux programmes malveillants et aux outils de piratage qui n’indiquent pas nécessairement une menace avancée ciblant l’organisation.
Informatif </br>(Gris) | Les incidents d’information peuvent ne pas être considérés comme dangereux pour le réseau, mais peuvent être utiles pour effectuer le suivi.

## <a name="assigned-to"></a>Affectée à
Vous pouvez choisir de filtrer la liste en sélectionnant ceux qui vous sont affectés ou ceux qui vous sont affectés.

### <a name="category"></a>Catégorie
Les incidents sont classés en fonction de la description de l’étape dans laquelle se trouve la chaîne de destruction de la cybersécurité. Cette vue aide l’analyste des menaces à déterminer la priorité, l’urgence et la stratégie de réponse correspondante à déployer en fonction du contexte.

### <a name="status"></a>Statut
Vous pouvez choisir de limiter la liste des incidents affichés en fonction de leur état pour identifier ceux qui sont actifs ou résolus.

### <a name="data-sensitivity"></a>Confidentialité des données
Utilisez ce filtre pour afficher les incidents qui contiennent des étiquettes de confidentialité.

## <a name="incident-naming"></a>Nommage des incidents

Pour comprendre l’étendue de l’incident en un clin d’œil, les noms d’incidents sont générés automatiquement en fonction des attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories.

Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*

> [!NOTE]
> Les incidents qui existaient avant le lancement du nommage automatique des incidents conserveront leur nom.


## <a name="see-also"></a>Voir aussi
- [File d’attente des incidents](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)

