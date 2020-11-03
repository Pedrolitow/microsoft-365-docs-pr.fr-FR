---
title: Gérer les incidents dans Microsoft 365 Defender
description: Découvrez comment attribuer, mettre à jour l’état,
keywords: incident, incidents, alertes, alertes corrélées, attribuer, mettre à jour, état, gérer, classification, microsoft, 365, m365
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
ms.openlocfilehash: 29f55d99dd3acd26ae305c03b533e2ca9bb61f2a
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48846651"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Gérer les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



La gestion des incidents est essentielle pour s’assurer que les menaces sont contenues et traitées. Dans Microsoft 365 Defender, vous avez accès à la gestion des incidents sur les appareils, les utilisateurs et les boîtes aux lettres. 


Vous pouvez gérer les incidents en sélectionnant un incident dans la **file d’attente d’incidents**. 

Vous pouvez modifier le nom d’un incident, le résoudre, déterminer sa classification et sa détermination. Vous pouvez également attribuer l’incident à vous-même, ajouter des balises d’incident et des commentaires.

Si, lors d’une investigation, vous devez déplacer des alertes d’un incident à un autre, vous pouvez également le faire à partir de l’onglet Alertes, ce qui permet de créer un incident plus important ou plus petit qui inclut toutes les alertes appropriées.

## <a name="edit-incident-name"></a>Modifier le nom de l’incident
Les incidents reçoivent automatiquement un nom basé sur les attributs d’alerte, tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.

Par exemple : plusieurs *étapes incident sur plusieurs points de terminaison signalés par plusieurs sources.*

Vous pouvez modifier le nom de l’incident afin de mieux l’aligner avec votre convention d’affectation de noms préférée.

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la fonctionnalité de dénomination automatique des incidents conserveront leur nom.



## <a name="assign-incidents"></a>Attribuer des incidents
Si aucun incident n’a encore été affecté, vous pouvez sélectionner **À moi-même** pour vous l’attribuer. Cette action suppose l’appropriation non seulement de l’incident, mais aussi de toutes les alertes associées.

## <a name="set-status-and-classification"></a>Définir l’état et la classification
### <a name="incident-status"></a>État de l’incident
Vous pouvez classer les incidents (comme **actifs** ou **résolus** ) en modifiant leur état au fur et à mesure de l’avancement de votre enquête. Cela vous permet d’organiser et de gérer la manière dont votre équipe peut réagir aux incidents.

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
