---
title: Fermer, rouvrir et supprimer des cas eDiscovery (Standard)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article explique comment gérer les cas eDiscovery (Standard). Cela inclut la fermeture d’un cas, la réouverture d’un dossier fermé et la suppression d’un cas.
ms.openlocfilehash: f527d206e7112534db557928daf6ab8942c60d1c
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318313"
---
# <a name="close-reopen-and-delete-a-ediscovery-standard-case"></a>Fermer, rouvrir et supprimer un cas eDiscovery (Standard)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cet article explique comment fermer, rouvrir et supprimer Microsoft Purview cas eDiscovery (Standard) dans Microsoft 365.

## <a name="close-a-case"></a>Fermer un cas

Lorsque l’affaire juridique ou l’enquête prise en charge par une affaire eDiscovery (Standard) est terminée, vous pouvez fermer l’affaire. Voici ce qui se passe lorsque vous fermez un cas :
  
- Si le cas contient des conservations eDiscovery, elles sont désactivées. Une fois la conservation désactivée, une période de grâce de 30 jours (appelée *délai d’attente*) est appliquée aux emplacements de contenu qui étaient en attente. Cela permet d’empêcher la suppression immédiate du contenu et donne aux administrateurs la possibilité de rechercher et de restaurer du contenu avant qu’il ne soit définitivement supprimé après l’expiration de la période de délai d’attente. Pour plus d’informations, consultez [Suppression des emplacements de contenu d’une conservation eDiscovery](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- La fermeture d’un cas désactive uniquement les conservations associées à ce cas. Si d’autres conservations sont placées sur un emplacement de contenu (par exemple, une conservation pour litige, une stratégie de rétention ou une conservation d’un autre cas eDiscovery (Standard), ces conservations sont conservées.

- Le cas est toujours répertorié dans la page eDiscovery (Standard) du portail de conformité Microsoft Purview. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches et exporter des résultats de recherche. La principale différence entre les cas actifs et fermés est que les conservations eDiscovery sont désactivées lorsqu’un cas est fermé.

Pour fermer un cas :
  
1. Dans le portail de conformité, cliquez sur **eDiscoveryeDiscovery** >  **(Standard)** pour afficher la liste des cas eDiscovery (Standard) dans votre organisation.

2. Cliquez sur le nom du cas que vous souhaitez fermer.

   ![Fermer la casse sur la page d’accueil de la casse.](../media/eDiscoveryCaseHomePage.png)

3. Dans la page d’accueil, sous **État**, cliquez sur **Fermer la casse**.

    Un avertissement s’affiche indiquant que les conservations associées à la casse seront désactivées.

4. Cliquez sur **Oui** pour fermer l’affaire.

    L’état de la page d’accueil du cas est passé **d’Actif** à **Fermeture**.

5. Dans la page **eDiscovery (Standard),** cliquez sur **Actualiser** pour mettre à jour l’état de la casse fermée. L’exécution du processus de clôture peut prendre jusqu’à 60 minutes.

    Une fois le processus terminé, l’état du cas est remplacé par **Fermé** sur la page **eDiscovery (Standard).**

## <a name="reopen-a-closed-case"></a>Rouvrir un cas fermé

Lorsque vous rouvrez une affaire, les conservations eDiscovery qui étaient en place lorsque l’affaire a été classée ne seront pas automatiquement rétablies. Une fois le cas rouvert, vous devez accéder à la page **Conservations** et activer les conservations précédentes. Pour activer une conservation, sélectionnez-la pour afficher la page de menu volant, puis réglez la bascule **État** sur **Activer**.
  
1. Dans le portail de conformité, cliquez sur **eDiscoveryCore** >  pour afficher la liste des cas eDiscovery (Standard) dans votre organisation.

2. Cliquez sur le nom du cas que vous souhaitez rouvrir.

   ![Rouvrez un dossier fermé.](../media/eDiscoveryCaseHomePageReopen.png)

3. Dans la page d’accueil, sous **État**, cliquez sur **Rouvrir la casse**.

    Un avertissement s’affiche indiquant que les conservations qui ont été associées au cas lorsqu’elle a été fermée ne seront pas activées automatiquement.

4. Cliquez sur **Oui** pour rouvrir le cas.

    L’état de la page volante de la page d’accueil du cas est passé de **Fermé** à **Actif**.

5. Dans la page **eDiscovery (Standard),** cliquez sur **Actualiser** pour mettre à jour l’état du cas rouvert. L’exécution du processus de réouverture peut prendre jusqu’à 60 minutes. 

    Une fois le processus terminé, l’état du cas est remplacé par **Actif** sur la page **eDiscovery (Standard** ).

6. (Facultatif) Pour activer toutes les conservations associées à la casse rouverte, **accédez** à l’onglet Conservations, sélectionnez une conservation, puis cochez la case sous **État** dans la page de menu volant De suspension.
  
## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez également supprimer les cas eDiscovery (Standard) actifs et fermés. Lorsque vous supprimez un cas, toutes les recherches et exportations dans le cas sont supprimées, et le cas est supprimé de la liste des cas sur la page **eDiscovery (Standard)** dans le portail de conformité. Vous ne pouvez pas rouvrir un cas supprimé.

Avant de pouvoir supprimer un cas (qu’il soit actif ou fermé), vous devez d’abord supprimer *toutes les* conservations eDiscovery associées au cas. Cela inclut la suppression des conservations avec l’état **Désactivé**. 

Pour supprimer une conservation eDiscovery :

1. Accédez à l’onglet **Conservations** dans le cas où vous souhaitez supprimer.

2. Sélectionnez la conservation à supprimer.

3. Dans la page de menu volant, cliquez sur **Supprimer**.

      ![Supprimez une conservation eDiscovery.](../media/DeleteeDiscoveryHold.png)

Pour supprimer un cas :

1. Dans le portail de conformité, cliquez sur **eDiscoveryeDiscovery** >  **(Standard)** pour afficher la liste des cas eDiscovery (Standard) dans votre organisation.

2. Cliquez sur le nom du cas à supprimer.

3. Dans la page d’accueil du cas, sous **État**, cliquez sur **Supprimer le cas**.

      ![Supprimez un cas.](../media/eDiscoveryCaseHomePageDelete.png)

Si le cas que vous essayez de supprimer contient toujours des conservations eDiscovery, vous recevrez un message d’erreur. Vous devrez supprimer toutes les conservations associées au cas, puis réessayer de supprimer le cas.
