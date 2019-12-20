---
title: Gérer les incidents dans la Protection Microsoft contre les menaces
description: Découvrez comment attribuer, mettre à jour l’état,
keywords: incident, incidents, alertes, alertes corrélées, attribuer, mettre à jour, état, gérer, classification, microsoft, 365, m365
search.product: eADQiWindows 10XVcnh
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: d6b7c754db3b43e909871a5a60fa1ab155f2d01d
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40806953"
---
# <a name="manage-incidents-in-microsoft-threat-protection"></a>Gérer les incidents dans la Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

La gestion des incidents est essentielle pour s’assurer que les menaces sont contenues et traitées. La Protection Microsoft contre les menaces vous permet d’accéder à la gestion des incidents sur les appareils, chez les utilisateurs et dans les boîtes aux lettres. 


Vous pouvez gérer les incidents en sélectionnant un incident dans la **file d’attente d’incidents**. 

Vous pouvez modifier le nom d’un incident, le résoudre, déterminer sa classification et sa détermination. Vous pouvez également attribuer l’incident à vous-même, ajouter des balises d’incident et des commentaires.

Si, lors d’une investigation, vous devez déplacer des alertes d’un incident à un autre, vous pouvez également le faire à partir de l’onglet Alertes, ce qui permet de créer un incident plus important ou plus petit qui inclut toutes les alertes appropriées.

## <a name="edit-incident-name"></a>Modifier le nom de l’incident
Par défaut, un numéro est attribué à un incident. Vous pouvez modifier le nom de l’incident afin de mieux l’aligner avec votre convention d’affectation de noms préférée.
 
## <a name="assign-incidents"></a>Attribuer des incidents
Si aucun incident n’a encore été affecté, vous pouvez sélectionner **À moi-même** pour vous l’attribuer. Cette action suppose l’appropriation non seulement de l’incident, mais aussi de toutes les alertes associées.

## <a name="set-status-and-classification"></a>Définir l’état et la classification
### <a name="incident-status"></a>État de l’incident
Vous pouvez classer les incidents (comme **actifs**ou **résolus**) en modifiant leur état au fur et à mesure de l’avancement de votre enquête. Cela vous permet d’organiser et de gérer la manière dont votre équipe peut réagir aux incidents.

Par exemple, votre analyste SOC peut passer en revue les incidents **actifs** urgents pour la journée et décider de se les attribuer pour enquête.

Sinon, il est possible que votre analyste SOC configure l’incident comme **résolu** si l’incident a été corrigé. La résolution d’un incident ferme automatiquement toutes les alertes toujours ouvertes faisant partie de l’incident. 

### <a name="classification-and-determination"></a>Classification et détermination
Vous pouvez choisir de ne pas définir de classification ou décider de spécifier si un incident est vrai ou faux. Cette opération permet à l’équipe de voir les modèles et d’en apprendre davantage. 

## <a name="add-comments"></a>Ajouter des commentaires
Vous pouvez ajouter des commentaires et afficher les événements historiques relatifs à un incident afin de voir les modifications précédentes apportées à ce dernier.

Chaque fois qu’une modification ou un commentaire est apporté à une alerte, cet élément est enregistré dans la section Commentaires et historique.

Les commentaires ajoutés apparaissent instantanément dans le volet.

## <a name="add-incident-tags"></a>Ajouter des balises d’incident
Vous pouvez ajouter des balises personnalisées à un incident, par exemple, pour marquer un groupe d’incidents présentant des caractéristiques communes. Vous pouvez filtrer ultérieurement la file d’attente des incidents pour afficher tous ceux qui contiennent une balise spécifique.

