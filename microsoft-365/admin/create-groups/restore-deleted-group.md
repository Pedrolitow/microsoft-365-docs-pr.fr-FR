---
title: Restaurer un groupe supprimé
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
ms.openlocfilehash: d7cf548816af1661298458f27c704d654845075d
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818506"
---
# <a name="restore-a-deleted-group"></a>Restaurer un groupe supprimé

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

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

## <a name="restore-a-group-that-you-own-by-using-outlook-on-the-web"></a>Restaurer un groupe dont vous êtes propriétaire à l’aide d’Outlook sur le Web

Si vous êtes le propriétaire d’un groupe Microsoft 365, vous pouvez restaurer le groupe vous-même dans Outlook sur le Web en procédant comme suit :

1. Sur la [page groupes supprimés](https://outlook.office.com/people/group/deleted), sélectionnez l’option **gérer les groupes** sous le nœud **groupes** , puis choisissez **supprimé**.

2. Cliquez sur l’onglet **restaurer** en regard du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

## <a name="restore-a-group-in-the-microsoft-365-admin-center"></a>Restaurer un groupe dans le centre d’administration Microsoft 365

Si vous êtes un administrateur général ou un administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le centre d’administration 365 de Microsoft :

1. Accédez au [Centre d’administration](https://admin.microsoft.com).
2. Développez **groupes**, puis cliquez sur **groupes supprimés**.
3. Sélectionnez le groupe que vous souhaitez restaurer, puis cliquez sur **restaurer le groupe**.

> [!NOTE]
> Dans certains cas, la restauration du groupe et de toutes ses données peut prendre jusqu’à 24 heures. 
  
## <a name="permanently-delete-a-microsoft-365-group"></a>Supprimer définitivement un groupe Microsoft 365

Il peut arriver que vous souhaitiez purger définitivement un groupe sans attendre que la période de suppression du logiciel de 30 jours expire. Pour ce faire, démarrez PowerShell et exécutez la commande suivante pour obtenir l'ID d'objet du groupe.
  
```
Get-AzureADMSDeletedGroup
```

Prenez note de l’ID d’objet du ou des groupes que vous souhaitez supprimer définitivement.
  
> [!CAUTION]
> La suppression définitive du groupe supprime le groupe et ses données pour toujours. 
  
Pour supprimer définitivement le groupe, exécutez la commande suivante dans PowerShell :
  
```
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

To confirm that the group has been successfully purged, run the  *Get-AzureADMSDeletedGroup*  cmdlet again to confirm that the group no longer appears on the list of soft-deleted groups. In some cases it may take as long as 24 hours for the group and all of its data to be permanently deleted. 
  
## <a name="got-questions-about-microsoft-365-groups"></a>Vous avez des questions sur les groupes Microsoft 365 ?

Visitez la [communauté Microsoft Tech](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) pour publier des questions et participer à des conversations sur les groupes Microsoft 365. 
  
## <a name="related-articles"></a>Articles connexes

[Gérer les groupes Microsoft 365 avec PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)
  
[Supprimer des groupes à l'aide de l'applet de commande Remove-UnifiedGroup](https://technet.microsoft.com/library/mt238270%28v=exchg.160%29.aspx)
  
[Gérer les paramètres de votre site d'équipe connecté à un groupe](https://support.microsoft.com/office/8376034d-d0c7-446e-9178-6ab51c58df42)
  
[Supprimer un groupe dans Outlook](https://support.microsoft.com/office/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f)
