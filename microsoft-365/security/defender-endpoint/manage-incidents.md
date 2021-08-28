---
title: Gérer Microsoft Defender pour les incidents de point de terminaison
description: Gérez les incidents en l’attribuant, en mettant à jour son état ou en attribuant sa classification.
keywords: incidents, gérer, affecter, état, classification, alerte vraie, alerte false
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 9deece85ec5a310cea652af1dd1da39cea386848
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58571300"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>Gérer Microsoft Defender pour les incidents de point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

La gestion des incidents est une partie importante de chaque opération de cybersécurité. Vous pouvez gérer les incidents en sélectionnant un incident dans la file **d’attente Incidents** ou dans le volet de **gestion Incidents.** 


La sélection d’un incident dans la  file **d’attente Incidents** ouvre le volet Gestion des incidents dans lequel vous pouvez ouvrir la page incident pour plus d’informations.


![Image du volet de gestion des incidents.](images/atp-incidents-mgt-pane-updated.png)

Vous pouvez affecter des incidents à vous-même, modifier l’état et la classification, les renommer ou commenter pour suivre leur progression.

> [!TIP]
> Pour une visibilité supplémentaire en un coup d’œil, les noms des incidents sont générés automatiquement en fonction des attributs d’alerte tels que le nombre de points de terminaison affectés, les utilisateurs affectés, les sources de détection ou les catégories. Cela vous permet de comprendre rapidement l’étendue de l’incident.
>
> Par exemple : *incident en plusieurs étapes sur plusieurs points de terminaison signalés par plusieurs sources.*
>
> Les incidents qui existaient avant le déploiement de la dénomination automatique des incidents conserveront leurs noms.
>


![Image de la page de détails de l’incident.](images/atp-incident-details-updated.png)

## <a name="assign-incidents"></a>Attribuer des incidents
Si aucun incident n’a encore  été affecté, vous pouvez sélectionner Affecter à moi pour vous attribuer l’incident. Cette action suppose l’appropriation non seulement de l’incident, mais aussi de toutes les alertes associées.

## <a name="set-status-and-classification"></a>Définir l’état et la classification
### <a name="incident-status"></a>État de l’incident
Vous pouvez classer les incidents (comme **actifs** ou **résolus**) en modifiant leur état au fur et à mesure de l’avancement de votre enquête. Cela vous permet d’organiser et de gérer la manière dont votre équipe peut réagir aux incidents.

Par exemple, votre analyste SoC peut examiner les incidents **actifs** urgents de la journée et décider de les affecter à lui-même pour examen.

Sinon, votre analyste SoC peut  définir l’incident comme résolu si l’incident a été corrigé. 

### <a name="classification"></a>Classification
Vous pouvez choisir de ne pas définir de classification ou décider de spécifier si un incident est vrai ou faux. Cette opération permet à l’équipe de voir les modèles et d’en apprendre davantage.

### <a name="add-comments"></a>Ajouter des commentaires
Vous pouvez ajouter des commentaires et afficher les événements historiques relatifs à un incident afin de voir les modifications précédentes apportées à ce dernier.

Chaque fois qu’une modification ou un commentaire est apporté à une alerte, cet élément est enregistré dans la section Commentaires et historique.

Les commentaires ajoutés apparaissent instantanément dans le volet.



## <a name="related-topics"></a>Voir aussi
- [File d’attente des incidents](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [Afficher et organiser la file d’attente des incidents](view-incidents-queue.md)
- [Examiner des incidents](investigate-incidents.md)
