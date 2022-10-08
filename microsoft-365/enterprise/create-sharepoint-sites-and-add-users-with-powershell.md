---
title: Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: landing-page
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: 'Résumé : Utilisez PowerShell pour créer des sites SharePoint Online, puis ajoutez des utilisateurs et des groupes à ces sites.'
ms.openlocfilehash: f640b7abcba9f05460e77fb11b8578c15b0a76fc
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68167536"
---
# <a name="create-sharepoint-online-sites-and-add-users-with-powershell"></a>Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Lorsque vous utilisez PowerShell pour Microsoft 365 pour créer des sites SharePoint Online et ajouter des utilisateurs, vous pouvez effectuer rapidement et à plusieurs reprises des tâches beaucoup plus rapidement que dans le Centre d'administration Microsoft 365. Vous pouvez également effectuer des tâches qui ne sont pas possibles dans le Centre d'administration Microsoft 365.

## <a name="connect-to-sharepoint-online"></a>Se connecter à SharePoint Online

Les procédures décrites dans cette rubrique vous obligent à vous connecter à SharePoint Online. Pour obtenir des instructions, consultez [Se connecter à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="step-1-create-new-site-collections-using-powershell"></a>Étape 1 : Créer des collections de sites à l’aide de PowerShell

Créez plusieurs sites à l’aide de PowerShell et d’un fichier .csv que vous créez à l’aide de l’exemple de code fourni et du Bloc-notes. Pendant cette procédure, vous allez remplacer les informations de l’espace réservé indiquées entre parenthèses par vos informations propres au site et au client. Ce processus vous permet de créer un seul fichier et d’exécuter une seule commande PowerShell qui utilise ce fichier. Cela rend les actions entreprises à la fois reproductibles et portables et élimine beaucoup, sinon la totalité, des erreurs qui peuvent provenir de la saisie de longues commandes dans SharePoint Online Management Shell. Cette procédure est en deux parties. Tout d’abord, vous allez créer un fichier .csv, puis vous référencerez ce fichier .csv à l’aide de PowerShell, qui utilisera son contenu pour créer les sites.

L’applet de commande PowerShell importe le fichier .csv et le dirige vers une boucle à l’intérieur des crochets qui lit la première ligne du fichier en tant qu’en-têtes de colonne. L’applet de commande PowerShell itère ensuite les enregistrements restants, crée une collection de sites pour chaque enregistrement et affecte les propriétés de la collection de sites en fonction des en-têtes de colonne.

### <a name="create-a-csv-file"></a>Créer un fichier CSV

> [!NOTE]
> Le paramètre de quota de ressources fonctionne uniquement sur les sites classiques. Si vous utilisez ce paramètre sur un site moderne, vous pouvez recevoir un message d’avertissement indiquant qu’il a été déprécié.

1. Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :

   ```powershell
   Owner,StorageQuota,Url,ResourceQuota,Template,TimeZoneID,Name
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/TeamSite01,25,EHS#1,10,Contoso Team Site
   owner@tenant.onmicrosoft.com,100,https://tenant.sharepoint.com/sites/Blog01,25,BLOG#0,10,Contoso Blog
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Project01,25,PROJECTSITE#0,10,Project Alpha
   owner@tenant.onmicrosoft.com,150,https://tenant.sharepoint.com/sites/Community01,25,COMMUNITY#0,10,Community Site
   ```

   Où *le locataire* est le nom de votre locataire et le *propriétaire* est le nom d’utilisateur de l’utilisateur sur votre locataire auquel vous souhaitez accorder le rôle d’administrateur de collection de sites principal.

   (Vous pouvez appuyer sur Ctrl+H lorsque vous utilisez le Bloc-notes pour remplacer en bloc plus rapidement.)

2. Enregistrez le fichier sur votre bureau en tant que **SiteCollections.csv**.

> [!TIP]
> Avant d’utiliser cet .csv ou tout autre fichier de script Windows PowerShell, il est recommandé de s’assurer qu’il n’y a pas de caractères superflus ou non imprimables. Ouvrez le fichier dans Word et, dans le ruban, cliquez sur l’icône paragraphe pour afficher les caractères non imprimables. Il ne doit pas y avoir de caractères non imprimables superflus. Par exemple, il ne doit y avoir aucune marque de paragraphe après la dernière marque à la fin du fichier.

### <a name="run-the-windows-powershell-command"></a>Exécuter la commande Windows PowerShell

1. À l’invite Windows PowerShell, tapez ou copiez et collez la commande suivante, puis appuyez sur Entrée :

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\SiteCollections.csv | ForEach-Object {New-SPOSite -Owner $_.Owner -StorageQuota $_.StorageQuota -Url $_.Url -NoWait -ResourceQuota $_.ResourceQuota -Template $_.Template -TimeZoneID $_.TimeZoneID -Title $_.Name}
   ```

   Où *MyAlias* est égal à votre alias d’utilisateur.

2. Attendez que l’invite de Windows PowerShell réapparaisse. Cela peut prendre une minute ou deux.

3. À l’invite de Windows PowerShell, saisissez ou copiez-collez la cmdlet suivante, puis appuyez sur Entrée :

   ```powershell
   Get-SPOSite -Detailed | Format-Table -AutoSize
   ```

4. Notez les nouvelles collections de sites dans la liste. À l’aide de notre exemple de fichier CSV, vous verrez les collections de sites suivantes : **TeamSite01**, **Blog01**, **Project01** et **Community01**

C’est fait. Vous avez créé plusieurs collections de sites à l’aide du fichier .csv que vous avez créé et d’une seule commande Windows PowerShell. Vous êtes maintenant prêt à créer et à affecter des utilisateurs à ces sites.

## <a name="step-2-add-users-and-groups"></a>Étape 2 : Ajout d’utilisateurs et de groupes

Now you’re going to create users and add them to a site collection group. You will then use a .csv file to bulk upload new groups and users.

Les procédures suivantes continuent à utiliser les exemples de sites TeamSite01, Blog01, Project01 et Community01.

### <a name="create-csv-and-ps1-files"></a>Créer des fichiers .csv et .ps1

1. Ouvrez le Bloc-notes et collez-y le bloc de texte suivant :

   ```powershell
   Site,Group,PermissionLevels
   https://tenant.sharepoint.com/sites/Community01,Contoso Project Leads,Full Control
   https://tenant.sharepoint.com/sites/Community01,Contoso Auditors,View Only
   https://tenant.sharepoint.com/sites/Community01,Contoso Designers,Design
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
   https://tenant.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
   https://tenant.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
   https://tenant.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
   ```

   Où *le locataire* est égal au nom de votre locataire.

2. Enregistrez le fichier sur votre bureau en tant que **GroupsAndPermissions.csv**.

3. Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :

   ```powershell
   Group,LoginName,Site
   Contoso Project Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Auditors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   Contoso Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Community01
   XT1000 Team Leads,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   XT1000 Advisors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/TeamSite01
   Contoso Blog Designers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Contoso Blog Editors,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Blog01
   Project Alpha Approvers,username@tenant.onmicrosoft.com,https://tenant.sharepoint.com/sites/Project01
   ```

   Où *le locataire* est égal au nom de votre locataire et le *nom d’utilisateur* correspond au nom d’utilisateur d’un utilisateur existant.

4. Enregistrez le fichier sur votre bureau en tant que **Users.csv**.

5. Ouvrez une nouvelle instance du Bloc-notes et collez-y le bloc de texte suivant :

   ```powershell
   Import-Csv C:\users\MyAlias\desktop\GroupsAndPermissions.csv | ForEach-Object {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
   Import-Csv C:\users\MyAlias\desktop\Users.csv | where {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
   ```

   Où MyAlias est égal au nom d’utilisateur de l’utilisateur actuellement connecté.

6. Enregistrez le fichier sur votre bureau en tant que **UsersAndGroups.ps1**. Il s’agit d’un script Windows PowerShell simple.

Vous êtes maintenant prêt à exécuter le script UsersAndGroup.ps1 pour ajouter des utilisateurs et des groupes à plusieurs collections de sites.

### <a name="run-usersandgroupsps1-script"></a>Exécuter le script UsersAndGroups.ps1

1. Revenez à SharePoint Online Management Shell.

2. À l’invite de Windows PowerShell, saisissez ou copiez-collez la ligne suivante, puis appuyez sur Entrée :

   ```powershell
   Set-ExecutionPolicy Bypass
   ```

3. À l’invite de confirmation, appuyez sur **Y**.

4. À l’invite de Windows PowerShell, saisissez ou copiez-collez ce qui suit, puis appuyez sur Entrée :

   ```powershell
   c:\users\MyAlias\desktop\UsersAndGroups.ps1
   ```

   Où *MyAlias* est égal à votre nom d’utilisateur.

5. Wait for the prompt to return before moving on. You will first see the groups appear as they are created. Then you will see the group list repeated as users are added.

## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Gestion des groupes de sites SharePoint Online avec PowerShell](manage-sharepoint-site-groups-with-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
