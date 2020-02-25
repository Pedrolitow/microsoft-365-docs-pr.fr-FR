---
title: Restaurer un groupe Office 365 supprimé
ms.reviewer: arvaradh
f1.keywords:
- CSH
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
description: 'Découvrez comment restaurer un groupe Office 365 supprimé à l’aide du centre d’administration Exchange. '
ms.openlocfilehash: 98eb00d90f5b607a58cd32728ce43cb4a1de1ff5
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42242595"
---
# <a name="restore-a-deleted-office-365-group"></a>Restaurer un groupe Office 365 supprimé

Si vous êtes le propriétaire d’un groupe Office 365, vous pouvez restaurer le groupe vous-même en suivant ces étapes.

1. Sur la [page groupes supprimés](https://outlook.office.com/people/group/deleted), sélectionnez l’option **gérer les groupes** sous le nœud **groupes** , puis choisissez **supprimé**.
2. Cliquez sur l’onglet **restaurer** en regard du groupe que vous souhaitez restaurer.

Si le groupe supprimé n’apparaît pas ici, contactez un administrateur.
  
Si vous êtes un utilisateur qui souhaite restaurer un groupe Office 365, demandez à un administrateur de suivre ces étapes pour vous ou de contacter votre support technique.  
   
Si vous avez supprimé un groupe, il est conservé pendant 30 jours par défaut. Cette période de 30 jours est considérée comme une « suppression récupérable » car vous pouvez toujours restaurer le groupe. Après 30 jours, le groupe et le contenu associé sont supprimés définitivement et ne peuvent pas être restaurés.
  
Pendant la période de suppression « récupérable », si un utilisateur tente d’accéder au site, il obtiendra un message de 404 _interdit_ . Après cette période, si un utilisateur tente d’accéder au site, il obtiendra un message 404 _introuvable_ .
  
En cas de restauration d'un groupe, le contenu suivant est restauré :
  
- Les groupes d’objets, propriétés et membres d’Azure Active Directory (AD) Office 365.
    
- Adresses de messagerie du groupe.
    
- Calendrier et boîte de réception partagés Exchange Online.
    
- Site et fichiers d’équipe SharePoint Online.
    
- bloc-notes OneNote ;
    
- Planificateur.
    
- Équipes

- Groupe Yammer et contenu de groupe (si le groupe Office 365 a été créé à partir de Yammer)
    
Vous pouvez [Supprimer un groupe Office 365 de manière définitive](#permanently-delete-an-office-365-group) si vous voulez supprimer définitivement le contenu avant la fin de la période de rétention de 30 jours. 

> [!NOTE]
> Le propriétaire du groupe Office 365 supprimé peut également restaurer le groupe. Pour restaurer un groupe Office 365 à l’aide de l’autorisation propriétaire sans autorisation d’administrateur, voir [restaurer un groupe office 365 à l’aide de PowerShell](#restore-an-office-365-group-using-powershell).

## <a name="restore-an-office-365-group-using-the-exchange-admin-center"></a>Restaurer un groupe Office 365 via le Centre d'administration Exchange

Vous devez disposer des autorisations d’administrateur global d’Office 365.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d'administration Exchange</a>.
    
2. Dans le Centre d'administration Exchange, sélectionnez **destinataires**, puis sélectionnez **groupes**. Vous pouvez voir si le groupe est actif ou supprimé de manière récupérable. Si le groupe a été supprimé de manière définitive, il n'est pas répertorié.
  
3. Pour afficher l’heure exacte à laquelle le groupe a été supprimé de manière récupérable, sélectionnez le groupe et affichez les informations dans le volet droit.
      
4. Sélectionnez le groupe que vous souhaitez restaurer, puis sélectionnez l’icône restaurer.
    
    ![Sélectionnez le groupe que vous souhaitez restaurer, puis sélectionnez l’icône restaurer.](../media/restore-group.png)
  
5. Sélectionnez actualiser ![Icône Actualiser](../media/6464df90-2a91-4c1f-92a6-9a38c7696ac3.gif) pour mettre à jour les informations dans la page. Votre groupe aura l'état Actif. Les formulaires et les données de formulaire associés à votre groupe seront également restaurés.
    
## <a name="restore-an-office-365-group-using-powershell"></a>Restaurer un groupe Office 365 via PowerShell

Vous devez disposer des autorisations d’administrateur global d’Office 365 ou être un ancien propriétaire du groupe Office 365 supprimé.

> [!IMPORTANT]
> Si vous utilisez Remove-MsolGroup dans PowerShell pour supprimer un groupe, le groupe est définitivement supprimé. Lorsque vous utilisez PowerShell pour supprimer des groupes, nous vous recommandons d'utiliser l'applet de commande **Remove-AzureADMSGroup** pour supprimer (suppression réversible) le groupe Office 365. Vous pourrez ainsi le restaurer, le cas échéant. 
  
### <a name="install-the-preview-version-of-the-azure-active-directory-powershell-for-graph"></a>Installer la version d'essai de Azure Active Directory PowerShell pour Graph

> [!IMPORTANT]
> Vous ne pouvez pas installer simultanément les versions aperçu et GA sur le même ordinateur.
  
En guise de meilleure pratique, nous vous recommandons de *toujours* rester à jour, c’est-à-dire de désinstaller l’ancienne AzureADPreview ou ancienne version AzureAD et d’obtenir la dernière version. 
  
 
1. Dans la barre de recherche, tapez Windows PowerShell.
    
2. Cliquez avec le bouton droit sur **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu'administrateur**.
  
2. Passez en revue vos modules installés :
    
  ```
  Get-InstalledModule -Name "AzureAD*"
  ```

3. Pour désinstaller une version précédente de AzureADPreview ou AzureAD, exécutez la commande suivante :
  
```
   Uninstall-Module AzureADPreview
```

ou
  
```
   Uninstall-Module AzureAD
```

4. To install the latest version of AzureADPreview, run this command:
  
```
   Install-Module AzureADPreview
```



At the message about an untrusted repository, type **Y**. It will take a minute or so for the new module to install. 
  
### <a name="restore-the-deleted-group"></a>Restaurer le groupe supprimé
  
1. Avez-vous installé le module **AzureADPreview** , comme indiqué dans la section previoius « installer la version d’évaluation du module Azure Active Directory pour Windows PowerShell » ?  Cette procédure ne fonctionne généralement pas si la version d' **évaluation** la plus récente du module est manquante. 
    
2. Si ce n'est pas déjà fait, ouvrez une fenêtre Windows PowerShell sur votre ordinateur (il peut s'agir d'une fenêtre Windows PowerShell standard ou d'une fenêtre que vous avez ouvert en sélectionnant **Exécuter en tant qu'administrateur**).
    
3. Exécutez les commandes suivantes en appuyant sur **entrée** après chacune d’elles : 
    
  ```
  Import-Module AzureADPreview
  ```

  ```
  Connect-AzureAD
  ```



  Dans l’écran Connectez-vous **à votre compte** qui s’ouvre, entrez le nom d’utilisateur et le mot de passe de votre compte administratif pour vous connecter à votre service Azure ad, puis sélectionnez **se connecter**.
  
4. Exécutez cette commande pour afficher tous les groupes Office 365 supprimés de votre organisation qui se trouvent encore dans la période de suppression logicielle de 30 jours :
    
  ```
  Get-AzureADMSDeletedGroup
  ```

5. Prenez note de l'ID d'objet du ou des groupes que vous voulez restaurer. Si vous ne voyez pas le groupe que vous recherchez dans cette liste, il a probablement été définitivement purgé.
    
    > [!CAUTION]
    > Si un groupe a été créé avec le même alias ou la même adresse SMTP que votre groupe supprimé, vous devez supprimer ce nouveau groupe pour pouvoir restaurer le groupe supprimé. 
  
6. Pour restaurer ce groupe, exécutez la commande suivante :
    
  ```
  Restore-AzureADMSDeletedDirectoryObject -Id <objectId>
  ```

7. Ce processus ne prend généralement que quelques minutes, mais dans quelques rares cas, il peut prendre jusqu’à 24 heures pour être entièrement restauré. Pour vérifier que le groupe a été correctement restauré, exécutez la commande suivante dans PowerShell :
    
  ```
  Get-AzureADGroup -ObjectId <objectId>
  ```

Une fois restauré, le groupe doit réapparaître dans le volet de navigation d'Outlook et d'Outlook sur le web. Tout le contenu restauré, y compris celui de SharePoint et du Planificateur, doivent être de nouveau accessibles aux membres du groupe.
  
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
