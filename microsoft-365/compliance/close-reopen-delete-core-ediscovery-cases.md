---
title: Fermer, rouvrir et supprimer des cas de découverte électronique principaux
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
description: Cet article explique comment gérer les cas de découverte électronique principaux. Cela inclut la fermeture d’un cas, la réouverture d’un incident fermé et la suppression d’un cas.
ms.openlocfilehash: 17b243a7207fd6927188b42e585101ff1d258b76
ms.sourcegitcommit: 5c96d06496d40d2523edbea336f7355c3c77cc80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44412793"
---
# <a name="close-reopen-and-delete-a-core-ediscovery-case"></a>Fermer, rouvrir et supprimer un cas de découverte électronique principale

Cet article explique comment fermer, rouvrir et supprimer des cas de découverte électronique principaux dans Microsoft 365.

## <a name="close-a-case"></a>Fermer un incident

Lorsque le cas juridique ou l’enquête pris en charge par un cas de découverte électronique de base est terminé, vous pouvez fermer le cas. Voici ce qui se passe lorsque vous fermez un cas :
  
- Si le cas contient des emplacements de contenu sur le blocage de la découverte électronique, ces conservations seront désactivées. Une fois la conservation désactivée, une période de grâce de 30 jours (appelée *conservation différée*) est appliquée aux emplacements de contenu en attente. Cela permet d’empêcher la suppression immédiate du contenu et permet aux administrateurs de rechercher et de restaurer du contenu avant qu’il ne soit supprimé définitivement après l’expiration de la période de blocage. Pour plus d’informations, consultez la rubrique [suppression des emplacements de contenu d’une conservation eDiscovery](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- La fermeture d’un incident ne désactive que les blocages associés à ce cas. Si d’autres suspensions sont placées sur un emplacement de contenu (comme une suspension pour litige, une stratégie de rétention ou une conservation d’un autre cas de découverte électronique de base), ces conservations seront conservées.

- Le cas est toujours mentionné sur la page de découverte électronique principale dans le centre de conformité Microsoft 365. Les détails, les conservations, les recherches et les membres d’un cas fermé sont conservés.

- Vous pouvez modifier un cas après sa fermeture. Par exemple, vous pouvez ajouter ou supprimer des membres, créer des recherches et exporter des résultats de recherche. La principale différence entre les cas actifs et fermés est que les conservations eDiscovery sont désactivées lors de la fermeture d’un cas.

Pour fermer un incident :
  
1. Dans le centre de conformité Microsoft 365, cliquez sur base de **découverte électronique**  >  **Core** pour afficher la liste des cas de découverte électronique de base dans votre organisation.

2. Cliquez sur le nom de l’incident que vous souhaitez fermer.

    La page flyout **gérer ce cas** s’affiche.

3. Sous **Manage case Status**, cliquez sur **Close case**.

    Un avertissement s’affiche indiquant que les conservations associées à la casse seront désactivées.

4. Cliquez sur **Oui** pour fermer le cas.

    L’état de la page flyout **gérer ce cas** passe de **actif** à **Fermer**.

5. Fermez la page **gérer ce cas** .

6. Sur la page de **découverte électronique principale** , cliquez sur **Actualiser** pour mettre à jour l’état du cas fermé. Le processus de clôture peut prendre jusqu’à 60 minutes.

    Une fois le processus terminé, l’état du cas est modifié sur **fermé** dans la page de **découverte électronique principale** . Cliquez de nouveau sur le nom de l’incident pour afficher la page de démarrage **gérer cet incident** , qui contient des informations sur la date et l’auteur de la fermeture du dossier.

## <a name="reopen-a-closed-case"></a>Rouvrir un litige clos

Lorsque vous rouvrez un cas, les conservations de découverte électronique qui étaient en place lors de la fermeture de l’incident ne sont pas automatiquement rétablis. Une fois le cas rouvert, vous devez accéder à la page **suspensions** et activer les suspensions précédentes. Pour activer une suspension, sélectionnez-la pour afficher la page de menu volant, puis définissez la bascule d' **État** sur **activé**.
  
1. Dans le centre de conformité Microsoft 365, cliquez sur base de **découverte électronique**  >  **Core** pour afficher la liste des cas de découverte électronique de base dans votre organisation.

2. Cliquez sur le nom de l’incident à rouvrir.

    La page flyout **gérer ce cas** s’affiche. 

3. Sous **gérer le statut du cas**, cliquez sur **rouvrir le cas**.

    Un avertissement s’affiche indiquant que les conservations associées à la casse lorsqu’elle a été fermée ne sont pas activées automatiquement.

4. Cliquez sur **Oui** pour rouvrir le cas.

    L’état de la page flyout **gérer ce cas** passe de **fermé** à **actif**.

5. Fermez la page **gérer ce cas** . 

6. Sur la page de **découverte électronique principale** , cliquez sur **Actualiser** pour mettre à jour l’état du cas rouvert. Le processus de réouverture peut prendre jusqu’à 60 minutes. 

    Une fois le processus terminé, l’état du cas est modifié sur **actif** sur la page de **découverte électronique principale** . 
  
## <a name="delete-a-case"></a>Supprimer un cas

Vous pouvez également supprimer des cas eDiscovery principaux en cours et fermés. Lorsque vous supprimez une demande de devis, toutes les recherches et exportations sont supprimées et le cas est supprimé de la liste des cas de la page de **découverte électronique principale** dans le centre de conformité Microsoft 365. Vous ne pouvez pas rouvrir un cas supprimé.

Avant de pouvoir supprimer un incident (qu’il soit actif ou fermé), vous devez d’abord supprimer *toutes les* conservations eDiscovery associées à la casse. Cela inclut la suppression des blocages dont l’État est **off**. 

Pour supprimer une conservation eDiscovery :

1. Accédez à l’onglet **suspensions** dans le cas que vous souhaitez supprimer.

2. Cliquez sur la conservation que vous souhaitez supprimer.

3. Sur la page de la fenêtre volante, cliquez sur **Supprimer la conservation**.

Pour supprimer un cas :

1. Dans le centre de conformité Microsoft 365, cliquez sur base de **découverte électronique**  >  **Core** pour afficher la liste des cas de découverte électronique de base dans votre organisation.

2. Cliquez sur le nom de la demande de devis que vous souhaitez supprimer.

3. Sous **Manage case Status** sur la page de menu volant, cliquez sur **Delete case**.

Si le cas que vous essayez de supprimer contient toujours des conservations eDiscovery, vous recevrez un message d’erreur. Vous devrez supprimer toutes les conservations associées au cas, puis réessayer de supprimer le cas.
