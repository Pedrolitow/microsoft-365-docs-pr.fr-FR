---
title: Fermer, rouvrir et supprimer des cas eDiscovery principaux
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article explique comment gérer les cas eDiscovery principaux. Cela inclut la fermeture d’un cas, la réouverture d’un cas fermé et la suppression d’un cas.
ms.openlocfilehash: 407956540e8881f34244e920fe9e49e6fe48ca7f417d084dcbd1845a2c53c4f6
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53906138"
---
# <a name="close-reopen-and-delete-a-core-ediscovery-case"></a>Fermer, rouvrir et supprimer un cas core eDiscovery

Cet article explique comment fermer, rouvrir et supprimer des cas eDiscovery principaux Microsoft 365.

## <a name="close-a-case"></a>Fermer un cas

Lorsque le dossier juridique ou l’examen pris en charge par un cas eDiscovery principal est terminé, vous pouvez fermer le cas. Voici ce qui se produit lorsque vous fermez un cas :
  
- Si le cas contient des cas de découverte électronique, ils sont désactivés. Une fois la attente désactivée, une période de grâce de 30 jours (appelée attente différée) est appliquée aux emplacements de contenu qui étaient en attente. Cela permet d’empêcher la suppression immédiate du contenu et offre aux administrateurs la possibilité de rechercher et de restaurer du contenu avant qu’il ne soit définitivement supprimé après l’expiration de la période d’attente. Pour plus d’informations, voir [Suppression d’emplacements de contenu d’une attente eDiscovery.](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold)

- La fermeture d’un cas désactive uniquement les conservations associées à ce cas. Si d’autres conservations sont placées sur un emplacement de contenu (par exemple, une conservation pour litige, une stratégie de rétention ou une conservation à partir d’un autre cas core eDiscovery), ces conservations sont conservées.

- Le cas est toujours répertorié sur la page Core eDiscovery dans la Centre de conformité Microsoft 365. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches et exporter des résultats de recherche. La principale différence entre les cas actifs et fermés est que les cas de découverte électronique sont désactivés lorsqu’un cas est fermé.

Pour fermer un cas :
  
1. Dans la Centre de conformité Microsoft 365, cliquez sur **eDiscovery** Core pour afficher la liste des cas  >   eDiscovery principaux dans votre organisation.

2. Cliquez sur le nom du cas que vous souhaitez fermer.

   ![Fermer le cas sur la page d’accueil du cas](../media/eDiscoveryCaseHomePage.png)

3. Dans la page d’accueil, sous **État,** cliquez **sur Fermer le cas.**

    Un avertissement s’affiche et vous avertit que les mises en cause associées au cas seront désactivées.

4. Cliquez **sur Oui** pour fermer le cas.

    L’état de la page d’accueil du cas passe de **Actif** à **Fermeture.**

5. Dans la page **Core eDiscovery,** cliquez sur **Actualiser** pour mettre à jour l’état du cas fermé. L’exécution du processus de clôture peut prendre jusqu’à 60 minutes.

    Une fois le processus terminé, l’état du cas passe à **Fermé** sur la page **Core eDiscovery.**

## <a name="reopen-a-closed-case"></a>Rouvrir un cas fermé

Lorsque vous rouvrez un cas, les cas de découverte électronique mis en place lors de la fermeture ne sont pas automatiquement rétablis. Une fois le cas rouvert, vous devez vous rendre sur la page **Dentes** et activer les précédentes. Pour activer une conservation, sélectionnez-la pour afficher la page de menu volant, puis réglez la bascule **État** sur **Activer**.
  
1. Dans la Centre de conformité Microsoft 365, cliquez sur **eDiscovery** Core pour afficher la liste des cas  >   eDiscovery principaux dans votre organisation.

2. Cliquez sur le nom du cas que vous souhaitez rouvrir.

   ![Rouvrir un cas fermé](../media/eDiscoveryCaseHomePageReopen.png)

3. Dans la page d’accueil, sous **État,** cliquez **sur Rouvrir le cas.**

    Un avertissement s’affiche pour vous dire que les mises en place associées au cas lors de sa fermeture ne seront pas automatiquement allumées.

4. Cliquez **sur Oui** pour rouvrir le cas.

    L’état de la page volante de la page d’accueil du cas passe de **Fermé** à **Actif.**

5. Dans la page **Core eDiscovery,** cliquez sur **Actualiser** pour mettre à jour l’état du cas rouvert. Le processus de réouverture peut prendre jusqu’à 60 minutes. 

    Une fois le processus terminé, l’état du cas passe à **Actif** sur la page **Core eDiscovery.**

6. (Facultatif) Pour activer les attentes associées au  cas rouvert, sélectionnez l’onglet Attentes, sélectionnez une attente, puis cochez la case sous État sur la page de la boîte aux lettres de la boîte aux lettres. 
  
## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez également supprimer des cas eDiscovery principaux et fermés. Lorsque vous supprimez un cas, toutes les recherches et exportations dans le cas sont supprimées et le cas est supprimé de la liste des cas sur la page **eDiscovery** principale dans la Centre de conformité Microsoft 365. Vous ne pouvez pas rouvrir un cas supprimé.

Avant de supprimer un cas (qu’il soit actif  ou fermé), vous devez d’abord supprimer toutes les actualités eDiscovery associées au cas. Cela inclut la suppression des maintiens avec l’état **« Off**». 

Pour supprimer une attente eDiscovery :

1. Go to the **Holds** tab in the case that you want to delete.

2. Sélectionnez la attente à supprimer.

3. Dans la page volante, cliquez sur **Supprimer.**

      ![Supprimer une attente eDiscovery](../media/DeleteeDiscoveryHold.png)

Pour supprimer un cas :

1. Dans la Centre de conformité Microsoft 365, cliquez sur **eDiscovery** Core pour afficher la liste des cas  >   eDiscovery principaux dans votre organisation.

2. Cliquez sur le nom du cas à supprimer.

3. Dans la page d’accueil du cas, sous **État,** cliquez **sur Supprimer le cas.**

      ![Supprimer un cas](../media/eDiscoveryCaseHomePageDelete.png)

Si le cas que vous essayez de supprimer contient toujours des conserves eDiscovery, vous recevrez un message d’erreur. Vous devez supprimer toutes les réserves associées au cas, puis essayer à nouveau de supprimer le cas.
