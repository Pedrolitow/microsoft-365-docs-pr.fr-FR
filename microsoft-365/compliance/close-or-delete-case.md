---
title: Fermer ou supprimer un cas
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez ce qui se produit lorsqu’un examen ou un dossier juridique pris en charge par un cas Advanced eDiscovery est fermé ou supprimé.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ffdd93351325be0c4b5d6d8cdfb78e55b710c0be
ms.sourcegitcommit: 6746fae2f68400fd985711b1945b66766d2a59a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419060"
---
# <a name="close-or-delete-an-advanced-ediscovery-case"></a>Fermer ou supprimer un cas Advanced eDiscovery

Lorsque le dossier juridique ou l’examen pris en charge par un cas Advanced eDiscovery est terminé, vous pouvez fermer ou supprimer un cas. Vous pouvez également rouvrir un cas fermé.

## <a name="close-a-case"></a>Fermer un cas

Voici ce qui se produit lorsque vous fermez un cas Advanced eDiscovery :

- Si le cas contient des emplacements de contenu en attente, ces conservations sont désactivées. Une fois la attente désactivée, une période de grâce de 30 jours (appelée attente différée) est appliquée aux emplacements de contenu qui étaient en attente. Cela permet d’empêcher la suppression immédiate du contenu et donne aux administrateurs la possibilité de rechercher ou de récupérer du contenu qui sera définitivement supprimé après l’expiration de la période de retard. Pour plus d’informations, voir [Suppression d’emplacements de contenu d’une attente eDiscovery.](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold)

- La fermeture d’un cas désactive uniquement les conservations associées à ce cas. Si d’autres sont conservées sur un emplacement de contenu (par exemple, une attente pour litige, une découverte électronique principale ou une attente à partir d’un autre cas Advanced eDiscovery), celles-ci sont conservées.

- Le cas est toujours répertorié sur la page eDiscovery dans le Centre de conformité Microsoft 365. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches, exporter des résultats de recherche et préparer des résultats de recherche pour analyse dans Advanced eDiscovery. La principale différence entre les cas actifs et fermés est que les conservations sont désactivées lorsqu’un cas est fermé.

Pour fermer un cas :

1. Dans la page **Advanced eDiscovery**, sélectionnez le cas que vous voulez fermer.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

3. Cliquez sur **Fermer le cas**.

   L’exécution du processus de clôture peut prendre jusqu’à 60 minutes.

## <a name="reopen-a-closed-case"></a>Rouvrir un cas fermé

Lorsque vous rouvrez un cas Advanced eDiscovery, les conserves qui étaient en place lors de la fermeture du cas ne seront pas automatiquement rétablies. Une fois le cas rouvert, vous devez passer à l’onglet **Holds** et activer les précédentes. Pour activer une conservation, sélectionnez-la pour afficher la page de menu volant, puis réglez la bascule **État** sur **Activer**.

Pour rouvrir un cas fermé :

1. Dans la page **Advanced eDiscovery**, sélectionnez le cas que vous voulez rouvrir.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

3. Cliquez sur **Rouvrir le cas**.

   Le processus de réouverture peut prendre jusqu’à 60 minutes.

## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez supprimer les cas Advanced eDiscovery actifs et fermés. Lorsque vous supprimez un cas, tous les composants associés au cas, tels que la liste des consignataires, communications, recherches, ensembles de révision et tâche d’exportation sont supprimés. Le cas est supprimé de la liste des cas dans la page **Advanced eDiscovery** du Centre de conformité Microsoft 365. Vous ne pouvez pas récupérer ou rouvrir un cas supprimé.

> [!NOTE]
> Dans les scénarios de débordement de données, la seule façon de supprimer des éléments d’un jeu à réviser consiste à supprimer le cas Advanced eDiscovery. Les autres méthodes de « recherche et purge » ne suppriment pas les éléments d’un jeu à réviser.

Avant de pouvoir supprimer un cas (qu’il soit  actif ou fermé), vous devez d’abord supprimer toutes les ententes associées au cas. Cela inclut la suppression des maintiens avec l’état **« Off**».

Pour supprimer les cas associés à un cas :

1. Go the **Holds** tab in the Advanced eDiscovery case that you want to delete.

2. Cliquez sur la attente à supprimer.

3. Dans la page volante, cliquez **sur Supprimer la attente.**

Pour supprimer un cas :

1. Dans la page **Advanced eDiscovery**, sélectionnez le cas que vous voulez supprimer.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

3. Cliquez sur **Supprimer le cas**.
