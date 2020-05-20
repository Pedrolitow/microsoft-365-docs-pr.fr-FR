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
description: Découvrez ce qui se passe lorsqu’une enquête ou une casse légale prise en charge par un cas avancé eDiscovery est fermée ou supprimée.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e64f5cc0483129396a28cbf657778001e5d372a7
ms.sourcegitcommit: 261d51b90a9ad53a6a42348c414b1b1e1230c37f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "44292410"
---
# <a name="close-or-delete-an-advanced-ediscovery-case"></a>Fermer ou supprimer un cas avancé eDiscovery

Lorsque le cas juridique ou l’enquête pris en charge par un cas avancé eDiscovery est terminé, vous pouvez fermer ou supprimer un incident. Vous pouvez également rouvrir un cas fermé.

## <a name="close-a-case"></a>Fermer un incident

Voici ce qui se passe lorsque vous fermez un cas avancé de découverte électronique :

- Si le cas contient des emplacements de contenu en conservation, ceux-ci sont désactivés. Cela peut entraîner la suppression ou le vidage définitifs du contenu, soit par l’utilisateur, soit par un processus automatisé, tel qu’une stratégie de suppression.

- La fermeture d’un incident ne désactive que les blocages associés à ce cas. Si d’autres suspensions sont placées sur un emplacement de contenu (comme une conservation pour litige, la conservation de découverte électronique principale ou une suspension d’un autre cas de découverte électronique avancée), ces conservations seront toujours conservées.

- Le cas est toujours mentionné sur la page eDiscovery dans le centre de conformité Microsoft 365. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches, exporter des résultats de recherche et préparer des résultats de recherche pour analyse dans Advanced eDiscovery. La principale différence entre les cas actifs et fermés est que les conservations sont désactivées lors de la fermeture d’un cas.

Pour fermer un incident :

1. Sur la page **Advanced eDiscovery** , sélectionnez le cas que vous souhaitez fermer.

2. Dans l’onglet **paramètres** , sous **informations**sur le cas, cliquez sur **Sélectionner**.

3. Cliquez sur **Fermer le cas**.

   Le processus de clôture peut prendre jusqu’à 60 minutes.

## <a name="reopen-a-closed-case"></a>Rouvrir un litige clos

Lorsque vous rouvrez un cas avancé eDiscovery, les conservations qui étaient en place lors de la fermeture de l’incident ne sont pas automatiquement rétablis. Une fois le cas rouvert, vous devez accéder à l’onglet **suspensions** et activer les suspensions précédentes. Pour activer une suspension, sélectionnez-la pour afficher la page de menu volant, puis définissez la bascule d' **État** sur **activé**.

Pour rouvrir un cas fermé :

1. Sur la page **Advanced eDiscovery** , sélectionnez le cas que vous souhaitez supprimer.

2. Dans l’onglet **paramètres** , sous **informations**sur le cas, cliquez sur **Sélectionner**.

3. Cliquez sur **rouvrir la demande de devis**.

   Le processus de réouverture peut prendre jusqu’à 60 minutes.

## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez supprimer à la fois des cas de découverte électronique avancée et active. Lorsque vous supprimez un incident, tous les composants associés à celui-ci, tels que la liste des dépositaires, les communications, les recherches, les ensembles de révision et les tâches d’exportation, sont supprimés. Le cas est supprimé de la liste des incidents de la page **Advanced eDiscovery** dans le centre de conformité Microsoft 365. Vous ne pouvez pas récupérer ou rouvrir un cas supprimé.

> [!NOTE]
> Dans les scénarios de fuite de données, la seule façon de supprimer des éléments dans un jeu de révision est de supprimer le cas avancé de découverte électronique. Les autres méthodes « recherche et purge » ne suppriment pas les éléments d’un jeu de révision.

Avant de pouvoir supprimer un incident (qu’il soit actif ou fermé), vous devez d’abord supprimer *toutes les* conservations associées au cas. Cela inclut la suppression des blocages dont l’État est **off**.

Pour supprimer les conservations associées à un cas :

1. Accédez à l’onglet **suspensions** dans le cas eDiscovery avancé que vous souhaitez supprimer.

2. Cliquez sur la conservation que vous souhaitez supprimer.

3. Sur la page de la fenêtre volante, cliquez sur **Supprimer la conservation**.

Pour supprimer un cas :

1. Sur la page **Advanced eDiscovery** , sélectionnez le cas que vous souhaitez supprimer.

2. Dans l’onglet **paramètres** , sous **informations**sur le cas, cliquez sur **Sélectionner**.

3. Cliquez sur **supprimer le cas**.
