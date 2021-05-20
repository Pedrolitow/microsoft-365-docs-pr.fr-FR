---
title: Restaurer un groupe de Microsoft 365 supprimé
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: Un groupe supprimé est conservé pendant 30 jours et vous pouvez toujours le restaurer. Après 30 jours, le groupe et son contenu sont supprimés définitivement.
ms.openlocfilehash: 285796ec45b1e6d77d46d7a0c39706f566bb8cf6
ms.sourcegitcommit: 9541d5e6720a06327dc785e3ad7e8fb11246fd72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2021
ms.locfileid: "52582679"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Restaurer un groupe de Microsoft 365 supprimé

Si vous avez supprimé un groupe, il sera conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression possible », car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et son contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.

En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Azure Active Directory (AD) Microsoft 365, propriétés et membres groups.
    
- Adresses de messagerie du groupe.
    
- Exchange Online boîte de réception et calendrier partagés.
    
- SharePoint Site d’équipe et fichiers en ligne.
    
- bloc-notes OneNote ;
    
- Planificateur.
    
- Équipes

- Yammer de groupe et de groupe (si le groupe Microsoft 365 a été créé à partir de Yammer)

> [!NOTE]
> Cet article décrit la restauration uniquement Microsoft 365 groupes. Tous les autres groupes ne peuvent pas être restaurés une fois supprimés.

## <a name="restore-a-group"></a>Restaurer un groupe

# <a name="outlook"></a>[Outlook](#tab/outlook)

Si vous êtes propriétaire d’un groupe Microsoft 365, vous pouvez restaurer le groupe vous-même dans Outlook sur le web en suivant les étapes suivantes :

1. Dans la [page Groupes supprimés,](https://outlook.office.com/people/group/deleted)sélectionnez l’option  Gérer les groupes sous le nœud **Groupes,** puis choisissez **Supprimé.**

2. Cliquez sur **l’onglet Restaurer** en côté du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

# <a name="admin-center"></a>[Centre d’administration](#tab/admin-center)

Si vous êtes administrateur général ou administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le centre d Microsoft 365'administration :

1. Allez au [centre administratif](https://admin.microsoft.com).      
2. Développez **Groupes,** puis cliquez **sur Groupes supprimés.**
3. Sélectionnez le groupe à restaurer, puis cliquez sur **Restaurer le groupe.**

> [!NOTE]
> Dans certains cas, la restauration du groupe et de toutes ses données peut prendre jusqu’à 24 heures. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Vous avez des questions sur Microsoft 365 groupes ?

Visitez le site [Tech Community Microsoft](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) pour publier des questions et participer à des conversations sur Microsoft 365 groupes. 
  
## <a name="related-content"></a>Contenu associé

[Gérer Microsoft 365 groupes avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (article)
  
[Supprimer des groupes à l’aide Remove-UnifiedGroup cmdlet](/powershell/module/exchange/remove-unifiedgroup) (article)
  
[Gérer les paramètres de votre site d’équipe](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) connecté à un groupe (article)
  
[Supprimer un groupe dans Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (article)