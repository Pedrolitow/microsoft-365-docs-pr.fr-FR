---
title: Gérer les incidents dans Microsoft 365 Defender
description: Découvrez comment attribuer, mettre à jour l’état,
keywords: incident, incidents, alertes, alertes corrélées, attribuer, mettre à jour, état, gérer, classification, microsoft, 365, m365
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
ms.openlocfilehash: da5a2190a53dfe7f8dd0cc3cf7b410af92ca4ec5
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861730"
---
# <a name="manage-incidents-in-microsoft-365-defender"></a>Gérer les incidents dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La gestion des incidents est essentielle pour s'assurer que les menaces sont contenues et traitées.

Vous gérez les incidents à partir **d'incidents & alertes** > incidents dans le lancement rapide du Centre de sécurité Microsoft 365 ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Exemple de file d'attente d'incident":::

Voici comment gérer vos incidents :

- Modifier le nom de l'incident
- Ajoutez des balises d'incident.
- Affecter l'incident à un compte d'utilisateur
- Résoudre les problèmes 
- Définir sa classification et sa détermination
- Ajoutez des commentaires.

Vous pouvez gérer les incidents à partir du **volet Gérer les incidents** pour un incident. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Exemple du volet Gérer les incidents d'un incident":::

Vous pouvez afficher ce volet à partir du lien **Gérer l'incident** sur :

- Volet des propriétés d'un incident dans la file d'attente des incidents.
- **Page récapitulatif** d'un incident.

Dans les cas où, lors de l'enquête, vous souhaitez déplacer des alertes d'un incident à un autre, vous pouvez également le faire à partir de l'onglet **Alertes,** créant ainsi un incident plus ou moins volumineux qui inclut toutes les alertes pertinentes.

## <a name="edit-the-incident-name"></a>Modifier le nom de l'incident

Microsoft 365 Defender attribue automatiquement un nom basé sur les attributs d'alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l'étendue de l'incident. Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*

Vous pouvez modifier le nom de l'incident à partir du **champ Nom de l'incident** dans le volet Gérer **l'incident.**

> [!NOTE]
> Les incidents qui existaient avant le déploiement de la fonctionnalité de nommage automatique des incidents conserveront leur nom.

## <a name="add-incident-tags"></a>Ajouter des balises d’incident

Vous pouvez ajouter des balises personnalisées à un incident, par exemple pour baliser un groupe d'incidents avec une caractéristique commune. Vous pouvez ensuite filtrer la file d'attente des incidents pour tous les incidents qui contiennent une balise spécifique.

Lorsque vous commencez à taper, vous avez la possibilité de sélectionner des balises dans une liste de balises sélectionnées.

## <a name="assign-incidents"></a>Attribuer des incidents

Si aucun incident n'a encore été affecté, vous pouvez sélectionner **Affecter** à et spécifier le compte d'utilisateur. Cette action affecte la propriété de l'incident et toutes les alertes qui lui sont associées.

## <a name="resolve-incident"></a>Résoudre l'incident

Si l'incident a été corrigé, sélectionnez **Résoudre l'incident** pour déplacer le basculement vers la droite. Notez que la résolution d'un incident résout également toutes les alertes liées et actives liées à l'incident.

Un incident qui n'est pas résolu s'affiche comme **étant actif.**

## <a name="set-the-classification-and-determination"></a>Définir la classification et la détermination

La classification des incidents est la question de savoir s'il s'agit d'une alerte vraie ou d'une fausse alerte, que vous configurez à partir du champ **Classification.** 

S'il s'agissait d'une alerte réelle, vous devez également spécifier le type de menace qu'il s'agissait avec le **champ Détermination.** La spécification du type de menace permet à votre équipe de sécurité de voir les modèles de menace et d'agir pour défendre votre organisation contre ces modèles. 

## <a name="add-comments"></a>Ajouter des commentaires

Vous pouvez ajouter plusieurs commentaires à un incident avec le **champ Commentaire.** Chaque commentaire est ajouté aux événements historiques de l'incident. Vous pouvez voir les commentaires et l'historique d'un incident à partir du lien Commentaires et historique dans la page **Résumé.** 

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Enquêter sur des incidents](investigate-incidents.md)
