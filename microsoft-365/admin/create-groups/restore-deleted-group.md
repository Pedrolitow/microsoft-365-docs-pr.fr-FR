---
title: Restaurer un groupe Microsoft 365 supprimé
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
description: Découvrez comment restaurer un groupe Microsoft 365 supprimé.
ms.openlocfilehash: f3b6435d82d5beddf44f5920011b076b39c7dcd5
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50910545"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Restaurer un groupe Microsoft 365 supprimé

Si vous avez supprimé un groupe, il sera conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression possible », car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et son contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.

En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Objet, propriétés et membres groupes Microsoft 365 Azure Active Directory (AD).
    
- Adresses de messagerie du groupe.
    
- Boîte de réception et calendrier partagés Exchange Online.
    
- Site et fichiers d’équipe SharePoint Online.
    
- bloc-notes OneNote ;
    
- Planificateur.
    
- Teams

- Yammer de groupe et de groupe (si le groupe Microsoft 365 a été créé à partir Yammer)

> [!NOTE]
> Cet article décrit la restauration uniquement des groupes Microsoft 365. Tous les autres groupes ne peuvent pas être restaurés une fois supprimés.

## <a name="restore-a-group"></a>Restaurer un groupe

# <a name="outlook"></a>[Outlook](#tab/outlook)

Si vous êtes propriétaire d’un groupe Microsoft 365, vous pouvez restaurer le groupe vous-même dans Outlook sur le web en suivant les étapes suivantes :

1. Dans la [page Groupes supprimés,](https://outlook.office.com/people/group/deleted)sélectionnez l’option  Gérer les groupes sous le nœud **Groupes,** puis choisissez **Supprimé.**

2. Cliquez sur **l’onglet Restaurer** en côté du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

# <a name="admin-center"></a>[Centre d’administration](#tab/admin-center)

Si vous êtes administrateur général ou administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le Centre d’administration Microsoft 365 :

1. Allez au [centre administratif](https://admin.microsoft.com).      
2. Développez **Groupes,** puis cliquez **sur Groupes supprimés.**
3. Sélectionnez le groupe à restaurer, puis cliquez sur **Restaurer le groupe.**

> [!NOTE]
> Dans certains cas, la restauration du groupe et de toutes ses données peut prendre jusqu’à 24 heures. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Vous avez des questions sur les groupes Microsoft 365 ?

Visitez la [communauté technique Microsoft pour](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) publier des questions et participer à des conversations sur les groupes Microsoft 365. 
  
## <a name="related-articles"></a>Articles connexes

[Gérer les groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
  
[Supprimer des groupes à l'aide de l'applet de commande Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup)
  
[Gérer les paramètres de votre site d'équipe connecté à un groupe](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42)
  
[Supprimer un groupe dans Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f)