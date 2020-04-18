---
title: Restaurer un groupe Office 365 supprimé
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b7c66b59-657a-4e1a-8aa0-8163b1f4eb54
description: Découvrez comment restaurer un groupe Office 365 supprimé.
ms.openlocfilehash: 2efd8c35286d224c6a3ed185043c82ab4b8e954e
ms.sourcegitcommit: 0da80ba7b504841c502ab06fea659a985c06fe8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43547531"
---
# <a name="restore-a-deleted-office-365-group"></a>Restaurer un groupe Office 365 supprimé

Si vous avez supprimé un groupe, il est conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression récupérable » car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et le contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.

En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Les groupes d’objets, propriétés et membres d’Azure Active Directory (AD) Office 365.
    
- Adresses de messagerie du groupe.
    
- Calendrier et boîte de réception partagés Exchange Online.
    
- Site et fichiers d’équipe SharePoint Online.
    
- bloc-notes OneNote ;
    
- Planificateur.
    
- Équipes

- Groupe Yammer et contenu de groupe (si le groupe Office 365 a été créé à partir de Yammer)

## <a name="restore-a-group-that-you-own-by-using-outlook"></a>Restaurer un groupe dont vous êtes propriétaire à l’aide d’Outlook

Si vous êtes le propriétaire d’un groupe Office 365, vous pouvez restaurer le groupe vous-même dans Outlook en procédant comme suit :

1. Sur la [page groupes supprimés](https://outlook.office.com/people/group/deleted), sélectionnez l’option **gérer les groupes** sous le nœud **groupes** , puis choisissez **supprimé**.
2. Cliquez sur l’onglet **restaurer** en regard du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.

## <a name="restore-a-group-in-the-microsoft-365-admin-center"></a>Restaurer un groupe dans le centre d’administration Microsoft 365

Si vous êtes un administrateur général ou un administrateur de groupes, vous pouvez restaurer un groupe supprimé dans le centre d’administration 365 de Microsoft :

1. Accédez au [Centre d’administration](https://admin.microsoft.com).
2. Développez **groupes**, puis cliquez sur **groupes supprimés**.
3. Sélectionnez le groupe que vous souhaitez restaurer, puis cliquez sur **restaurer le groupe**.
  
## <a name="permanently-delete-an-office-365-group"></a>Supprimer un groupe Office 365 de manière définitive

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

Pour vérifier que le groupe a été supprimé définitivement, réexécutez l'applet de commande  *Get-AzureADMSDeletedGroup*  pour confirmer que le groupe n'apparaît plus dans la liste des groupes supprimés (suppression réversible). Dans certains cas, la suppression définitive du groupe et de toutes ses données peut prendre jusqu'à 24 heures. 
  
## <a name="got-questions-about-office-365-groups"></a>Vous avez des questions sur les groupes Office 365 ?

Visitez la [communauté Microsoft Tech](https://techcommunity.microsoft.com/t5/Office-365-Groups/ct-p/Office365Groups) pour publier des questions et participer à des conversations sur les groupes Office 365. 
  
## <a name="related-articles"></a>Articles connexes

[Utiliser PowerShell pour gérer les groupes Office 365](https://support.office.com/article/aeb669aa-1770-4537-9de2-a82ac11b0540)
  
[Supprimer des groupes à l'aide de l'applet de commande Remove-UnifiedGroup](https://technet.microsoft.com/library/mt238270%28v=exchg.160%29.aspx)
  
[Gérer les paramètres de votre site d'équipe connecté à un groupe](https://support.office.com/article/8376034d-d0c7-446e-9178-6ab51c58df42.aspx)
  
[Supprimer un groupe dans Outlook](https://support.office.com/article/ca7f5a9e-ae4f-4cbe-a4bc-89c469d1726f.aspx)
