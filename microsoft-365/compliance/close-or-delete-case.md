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
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Découvrez ce qui se passe lorsqu’une enquête ou un cas juridique pris en charge par un cas de découverte électronique (Premium) Microsoft Purview est fermé ou supprimé.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: c3ea769fe6c1e01a14e6a552170da8421a03cf07
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940420"
---
# <a name="close-or-delete-an-ediscovery-premium-case"></a>Fermer ou supprimer un cas eDiscovery (Premium)

Lorsque l’affaire juridique ou l’enquête prise en charge par un cas de découverte électronique Microsoft Purview (Premium) est terminée, vous pouvez fermer ou supprimer un cas. Vous pouvez également rouvrir un dossier clos.

## <a name="close-a-case"></a>Fermer un cas

Voici ce qui se passe lorsque vous fermez un cas eDiscovery (Premium) :

- Si le cas contient des emplacements de contenu en attente, ces conservations sont désactivées. Une fois la conservation désactivée, une période de grâce de 30 jours (appelée *délai d’attente*) est appliquée aux emplacements de contenu qui étaient en attente. Cela permet d’empêcher la suppression immédiate du contenu et donne aux administrateurs la possibilité de rechercher ou de récupérer du contenu qui sera supprimé définitivement après l’expiration de la période de conservation différée. Pour plus d’informations, consultez [Suppression des emplacements de contenu d’une conservation eDiscovery](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- La fermeture d’un cas désactive uniquement les conservations associées à ce cas. Si d’autres conservations sont conservées sur un emplacement de contenu (par exemple, une conservation de litige, une conservation de Microsoft Purview eDiscovery (Standard) ou une conservation d’un autre cas eDiscovery (Premium), ces conservations restent conservées.

- Le cas est toujours répertorié sur la page eDiscovery dans le portail de conformité Microsoft Purview. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches, exporter des résultats de recherche et préparer des résultats de recherche pour l’analyse dans eDiscovery (Premium). La principale différence entre les cas actifs et fermés est que les conservations sont désactivées lorsqu’un cas est fermé.

Pour fermer un cas :

1. Dans la page **eDiscovery (Premium),** sélectionnez le cas à fermer.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

   ![Accédez à la page de menu volant des informations sur le cas dans un cas eDiscovery (Premium).](..\media\AeDSelectCaseInformation.png) 

3. En bas de la page de menu volant Informations sur la **casse** , cliquez sur **Actions**, puis sur **Fermer la casse**.

   L’exécution du processus de clôture peut prendre jusqu’à 60 minutes.

## <a name="reopen-a-closed-case"></a>Rouvrir un cas fermé

Lorsque vous rouvrez un cas eDiscovery (Premium), les conservations en place lors de la fermeture de l’affaire ne sont pas automatiquement rétablies. Une fois le cas rouvert, vous devez accéder à l’onglet **Conservations** et activer les conservations précédentes. Pour activer une conservation, sélectionnez-la pour afficher la page de menu volant, puis réglez la bascule **État** sur **Activer**.

Pour rouvrir un dossier fermé :

1. Dans la page **eDiscovery (Premium),** sélectionnez le cas à rouvrir.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

3. En bas de la page de menu volant Informations sur la **casse** , cliquez sur **Actions**, puis sur **Rouvrir le cas**.

   L’exécution du processus de réouverture peut prendre jusqu’à 60 minutes.

## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez supprimer les cas eDiscovery (Premium) actifs et fermés. Lorsque vous supprimez un cas, tous les composants associés au cas, tels que la liste des consignataires, communications, recherches, ensembles de révision et tâche d’exportation sont supprimés. Le cas est supprimé de la liste des cas dans la page **eDiscovery (Premium)** du portail de conformité Microsoft Purview. Vous ne pouvez pas récupérer ou rouvrir un cas supprimé.

> [!NOTE]
> Dans les scénarios de débordement de données, la seule façon de supprimer les éléments d’un jeu de révision consiste à supprimer le cas eDiscovery (Premium). Les autres méthodes de « recherche et vidage » ne suppriment pas les éléments d’un ensemble de révisions.

Avant de pouvoir supprimer un cas (qu’il soit actif ou fermé), vous devez d’abord supprimer *toutes les* conservations associées au cas. Cela inclut la suppression des conservations avec l’état **Désactivé**.

Pour supprimer les conservations associées à un cas :

1. Accédez à l’onglet **Conservations** dans le cas eDiscovery (Premium) que vous souhaitez supprimer.

2. Cliquez sur la conservation à supprimer.

3. Dans la page de menu volant, cliquez sur **Supprimer la conservation**.

Pour supprimer un cas :

1. Dans la page **eDiscovery (Premium),** sélectionnez le cas à supprimer.

2. Sous l’onglet **Paramètres**, sous **Informations de cas**, cliquez sur **Sélectionner**.

3. En bas de la page de menu volant Informations sur la **casse** , cliquez sur **Actions**, puis sur **Supprimer le cas**.

