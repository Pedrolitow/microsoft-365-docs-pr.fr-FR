---
title: Restaurer un groupe Microsoft 365 supprimé
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: Un groupe supprimé est conservé pendant 30 jours et vous pouvez toujours le restaurer. Après 30 jours, le groupe et son contenu sont supprimés définitivement.
ms.openlocfilehash: ea154fa9a1533fdabf4cc9b1a8a6c50cd62cacff
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726725"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Restaurer un groupe Microsoft 365 supprimé

Si vous avez supprimé un groupe, il est conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression réversible », car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et son contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.

En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Azure Active Directory (AD) Groupes Microsoft 365 objet, propriétés et membres.
    
- Adresses de messagerie du groupe.
    
- Exchange Online boîte de réception et calendrier partagés.
    
- Site et fichiers d’équipe SharePoint Online.
    
- bloc-notes OneNote ;
    
- Planificateur
    
- Teams

- Contenu du groupe et du groupe Yammer (si le groupe Microsoft 365 a été créé à partir de Yammer)

- [Espace de travail](/power-bi/collaborate-share/service-create-workspaces) Power BI Classic

> [!NOTE]
> Cet article décrit la restauration des groupes Microsoft 365 uniquement. Tous les autres groupes ne peuvent pas être restaurés une fois supprimés.

## <a name="restore-a-group"></a>Restaurer un groupe

# <a name="outlook"></a>[Outlook](#tab/outlook)

Si vous êtes propriétaire d’un groupe Microsoft 365, vous pouvez restaurer le groupe vous-même dans Outlook sur le web en procédant comme suit :

1. Dans la [page Groupes supprimés](https://outlook.office.com/people/group/deleted), sélectionnez l’option **Gérer les groupes** sous le nœud **Groupes** , puis choisissez **Supprimé**.

2. Cliquez sur l’onglet **Restaurer** en regard du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

# <a name="admin-center"></a>[centre Administration](#tab/admin-center)

Si vous êtes administrateur général ou administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le Centre d'administration Microsoft 365 :

1. Allez au [centre administratif](https://admin.microsoft.com).      
2. Développez **Groupes**, puis cliquez sur **Groupes supprimés**.
3. Sélectionnez le groupe que vous souhaitez restaurer, puis cliquez sur **Restaurer le groupe**.

> [!NOTE]
> Dans certains cas, la restauration du groupe et de toutes ses données peut prendre jusqu’à 24 heures. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Vous avez des questions sur Groupes Microsoft 365 ?

Visitez le [Microsoft Tech Community](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) pour publier des questions et participer à des conversations sur les groupes Microsoft 365. 
  
## <a name="related-content"></a>Contenu associé

[Gérer Groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (article)\
[Supprimer des groupes à l’aide de l’applet de commande Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) (article)\
[Gérer les paramètres de votre site d’équipe connecté à un groupe](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42) (article)\
[Supprimer un groupe dans Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f) (article)
