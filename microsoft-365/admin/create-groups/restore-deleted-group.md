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
ms.openlocfilehash: 091697be54b1127a5cb336179733d51519947e14
ms.sourcegitcommit: 3cdb670f10519f7af4015731e7910954ba9f70dc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "48753242"
---
# <a name="restore-a-deleted-microsoft-365-group"></a>Restaurer un groupe Microsoft 365 supprimé

Si vous avez supprimé un groupe, il est conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression récupérable » car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et le contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.

En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Azure Active Directory (AD) Microsoft 365 groupes objet, propriétés et membres.
    
- Adresses de messagerie du groupe.
    
- Calendrier et boîte de réception partagés Exchange Online.
    
- Site et fichiers d’équipe SharePoint Online.
    
- bloc-notes OneNote ;
    
- Planificateur.
    
- Teams

- Groupe Yammer et contenu de groupe (si le groupe Microsoft 365 a été créé à partir de Yammer)

> [!NOTE]
> Cet article décrit la restauration des groupes Microsoft 365 uniquement. Tous les autres groupes ne peuvent pas être restaurés une fois supprimés.

## <a name="restore-a-group"></a>Restaurer un groupe

# <a name="outlook"></a>[Outlook](#tab/outlook)

Si vous êtes le propriétaire d’un groupe Microsoft 365, vous pouvez restaurer le groupe vous-même dans Outlook sur le Web en procédant comme suit :

1. Sur la [page groupes supprimés](https://outlook.office.com/people/group/deleted), sélectionnez l’option **gérer les groupes** sous le nœud **groupes** , puis choisissez **supprimé**.

2. Cliquez sur l’onglet **restaurer** en regard du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

# <a name="admin-center"></a>[Centre d’administration](#tab/admin-center)

Si vous êtes un administrateur général ou un administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le centre d’administration 365 de Microsoft :

1. Allez au [centre administratif](https://admin.microsoft.com).      
2. Développez **groupes**, puis cliquez sur **groupes supprimés**.
3. Sélectionnez le groupe que vous souhaitez restaurer, puis cliquez sur **restaurer le groupe**.

> [!NOTE]
> Dans certains cas, la restauration du groupe et de toutes ses données peut prendre jusqu’à 24 heures. 

---

## <a name="got-questions-about-microsoft-365-groups"></a>Vous avez des questions sur les groupes Microsoft 365 ?

Visitez la [communauté Microsoft Tech](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) pour publier des questions et participer à des conversations sur les groupes Microsoft 365. 
  
## <a name="related-articles"></a>Articles connexes

[Gérer les groupes Microsoft 365 avec PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershell)
  
[Supprimer des groupes à l'aide de l'applet de commande Remove-UnifiedGroup](https://technet.microsoft.com/library/mt238270%28v=exchg.160%29.aspx)
  
[Gérer les paramètres de votre site d'équipe connecté à un groupe](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42)
  
[Supprimer un groupe dans Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f)
