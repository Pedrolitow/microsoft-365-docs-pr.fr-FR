---
title: Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: landing-page
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- SPO_Content
- seo-marvel-apr2020
ms.assetid: d0d3877a-831f-4744-96b0-d8167f06cca2
description: Dans cet article, découvrez comment utiliser PowerShell pour Microsoft 365 afin de gérer SharePoint utilisateurs, groupes et sites en ligne.
ms.openlocfilehash: 78c829e476c63e435d9543b3a4175cdbbccb76e8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100674"
---
# <a name="manage-sharepoint-online-users-and-groups-with-powershell"></a>Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous êtes un administrateur SharePoint Online qui travaille avec de grandes listes de comptes d’utilisateurs ou de groupes et souhaite un moyen plus simple de les gérer, vous pouvez utiliser PowerShell pour Microsoft 365.

Avant de commencer, les procédures décrites dans cet article vous obligent à vous connecter à SharePoint Online. Pour obtenir des instructions, consultez [Connecter pour SharePoint PowerShell en ligne](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

## <a name="get-a-list-of-sites-groups-and-users"></a>Obtenir une liste de sites, de groupes et d’utilisateurs

Avant de commencer à gérer les utilisateurs et les groupes, vous devez obtenir les listes de vos sites, groupes et utilisateurs. Vous pouvez ensuite utiliser ces informations pour travailler à partir de l’exemple figurant dans cet article.

Vous pouvez obtenir la liste des sites de votre client avec la commande suivante :

```powershell
Get-SPOSite
```

Vous pouvez obtenir la liste des groupes de votre client avec la commande suivante :

```powershell
Get-SPOSite | ForEach {Get-SPOSiteGroup -Site $_.Url} | Format-Table
```

Vous pouvez obtenir la liste des utilisateurs de votre client avec la commande suivante :

```powershell
Get-SPOSite | ForEach {Get-SPOUser -Site $_.Url}
```

## <a name="add-a-user-to-the-site-collection-administrators-group"></a>Ajouter un utilisateur au groupe Administrateurs de collection de sites

Vous utilisez l’applet `Set-SPOUser` de commande pour ajouter un utilisateur à la liste des administrateurs de collections de sites sur une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
 ```

Pour utiliser ces commandes, remplacez tout ce qui se trouve dans les guillemets, y compris les caractères < et >, par les noms corrects.

Par exemple, cet ensemble de commandes ajoute Opal Forme (nom d’utilisateur opalc) à la liste des administrateurs de collection de sites sur la collection de sites ContosoTest dans la location Contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "opalc"
Set-SPOUser -Site https://$tenant.sharepoint.com/sites/$site -LoginName $user@$tenant.com -IsSiteCollectionAdmin $true
```

Vous pouvez copier et coller ces commandes dans Bloc-notes, modifier les valeurs de variables pour $tenant, $site et $user en valeurs réelles de votre environnement, puis les coller dans votre fenêtre SharePoint Online Management Shell pour les exécuter.

## <a name="add-a-user-to-other-site-collection-groups"></a>Ajouter un utilisateur à d’autres groupes de collections de sites

Dans cette tâche, nous allons utiliser l’applet `Add-SPOUser` de commande pour ajouter un utilisateur à un groupe SharePoint sur une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site

```

Par exemple, nous allons ajouter Glen Rife (glenr de nom d’utilisateur) au groupe Auditeurs sur la collection de sites ContosoTest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "glenr"
$group = "Auditors"
Add-SPOUser -Group $group -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="create-a-site-collection-group"></a>Créer un groupe de collections de sites

Vous utilisez l’applet `New-SPOSiteGroup` de commande pour créer un groupe SharePoint et l’ajouter à une collection de sites.

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$group = "<group name name, such as Auditors>"
$level = "<permission level, such as View Only>"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

Les propriétés de groupe, telles que les niveaux d’autorisation, peuvent être mises à jour ultérieurement à l’aide de l’applet `Set-SPOSiteGroup` de commande.

Par exemple, nous allons ajouter le groupe Auditeurs avec des autorisations d’affichage uniquement à la collection de sites contosotest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$group = "Auditors"
$level = "View Only"
New-SPOSiteGroup -Group $group -PermissionLevels $level -Site https://$tenant.sharepoint.com/sites/$site
```

## <a name="remove-users-from-a-group"></a>Supprimer des utilisateurs d’un groupe

Parfois, vous devez supprimer un utilisateur d’un site ou même de tous les sites. Peut-être que l’employé passe d’une division à une autre ou quitte l’entreprise. Vous pouvez le faire facilement pour un employé dans l’interface utilisateur, mais cela n’est pas facile quand vous devez déplacer une division complète d’un site à un autre.

Toutefois, en utilisant les fichiers SharePoint Online Management Shell et CSV, cela est rapide et facile. Dans cette tâche, vous allez utiliser Windows PowerShell pour supprimer un utilisateur d’un groupe de sécurité de collection de sites. Vous utiliserez ensuite un fichier CSV et supprimerez de nombreux utilisateurs de différents sites.

Nous allons utiliser l’applet de commande « Remove-SPOUser » pour supprimer un seul utilisateur Microsoft 365 d’un groupe de collections de sites afin de voir la syntaxe de commande. Voici à quoi ressemble la syntaxe :

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
$user = "<user account name, such as opalc>"
$group = "<group name name, such as Auditors>"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Par exemple, nous allons supprimer Bobby Overby du groupe Auditeurs de collection de sites dans la collection de sites contosotest dans la location contoso :

```powershell
$tenant = "contoso"
$site = "contosotest"
$user = "bobbyo"
$group = "Auditors"
Remove-SPOUser -LoginName $user@$tenant.com -Site https://$tenant.sharepoint.com/sites/$site -Group $group
```

Supposons que nous voulions supprimer Bobby de tous les groupes dans lesquels il est actuellement. Voici comment procéder :

```powershell
$tenant = "contoso"
$user = "bobbyo"
Get-SPOSite | ForEach {Get-SPOSiteGroup –Site $_.Url} | ForEach {Remove-SPOUser -LoginName $user@$tenant.com -Site &_.Url}
```

> [!WARNING]
> Ce n’est qu’un exemple. Vous ne devez pas exécuter cette commande sauf si vous devez vraiment supprimer un utilisateur de chaque groupe, par exemple si l’utilisateur quitte l’entreprise.

## <a name="automate-management-of-large-lists-of-users-and-groups"></a>Automatiser la gestion des grandes listes d’utilisateurs et de groupes

Pour ajouter un grand nombre de comptes à SharePoint sites et leur accorder des autorisations, vous pouvez utiliser les Centre d'administration Microsoft 365, les commandes PowerShell individuelles ou PowerShell et un fichier CSV. Parmi tous ces choix, le fichier CSV est le moyen le plus rapide d’automatiser cette tâche.

Le processus de base consiste à créer un fichier CSV qui possède des en-têtes (colonnes) correspondant aux paramètres dont le script Windows PowerShell a besoin. Vous pouvez facilement créer une telle liste dans Excel, puis l’exporter en tant que fichier CSV. Ensuite, vous utilisez un script Windows PowerShell pour parcourir les enregistrements (lignes) dans le fichier CSV, en ajoutant les utilisateurs à des groupes et les groupes à des sites.

Par exemple, nous allons créer un fichier CSV pour définir un groupe de collections de sites, de groupes et d’autorisations. Ensuite, nous allons créer un fichier CSV pour remplir les groupes avec des utilisateurs. Enfin, nous allons créer et exécuter un script Windows PowerShell qui crée et remplit les groupes.

Le premier fichier CSV ajoutera des groupes à des collections de sites et aura la structure suivante :

En-tête:

```powershell
Site,Group,PermissionLevels
```

Article:

```powershell
https://tenant.sharepoint.com/sites/site,group,level
```

Voici un exemple de fichier :

```powershell
Site,Group,PermissionLevels
https://contoso.sharepoint.com/sites/contosotest,Contoso Project Leads,Full Control
https://contoso.sharepoint.com/sites/contosotest,Contoso Auditors,View Only
https://contoso.sharepoint.com/sites/contosotest,Contoso Designers,Design
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Team Leads,Full Control
https://contoso.sharepoint.com/sites/TeamSite01,XT1000 Advisors,Edit
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Designers,Design
https://contoso.sharepoint.com/sites/Blog01,Contoso Blog Editors,Edit
https://contoso.sharepoint.com/sites/Project01,Project Alpha Approvers,Full Control
```

Le second fichier CSV ajoutera des utilisateurs à des groupes et aura la structure suivante :

En-tête:

```powershell
Group,LoginName,Site
```

Article:

```powershell
group,login,https://tenant.sharepoint.com/sites/site
```

Voici un exemple de fichier :

```powershell
Group,LoginName,Site
Contoso Project Leads,bobbyo@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Auditors,allieb@contoso.com,https://contoso.sharepoint.com/sites/contosotest
Contoso Designers,bonniek@contoso.com,https://contoso.sharepoint.com/sites/contosotest
XT1000 Team Leads,dorenap@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
XT1000 Advisors,garthf@contoso.com,https://contoso.sharepoint.com/sites/TeamSite01
Contoso Blog Designers,janets@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Contoso Blog Editors,opalc@contoso.com,https://contoso.sharepoint.com/sites/Blog01
Project Alpha Approvers,robinc@contoso.com,https://contoso.sharepoint.com/sites/Project01
```

Pour la prochaine étape, vous devez avoir enregistré les deux fichiers CSV sur votre lecteur. Voici des exemples de commandes qui utilisent à la fois des fichiers CSV et pour ajouter des autorisations et l’appartenance au groupe :

```powershell
Import-Csv C:\O365Admin\GroupsAndPermissions.csv | ForEach {New-SPOSiteGroup -Group $_.Group -PermissionLevels $_.PermissionLevels -Site $_.Site}
Import-Csv C:\O365Admin\Users.csv | ForEach {Add-SPOUser -Group $_.Group –LoginName $_.LoginName -Site $_.Site}
```

Le script importe le contenu du fichier CSV et utilise les valeurs des colonnes pour remplir les paramètres des commandes **New-SPOSiteGroup** et **Add-SPOUser** . Dans notre exemple, nous enregistrons ce fichier dans le dossier O365Admin sur le lecteur C, mais vous pouvez l’enregistrer où vous le souhaitez.

Maintenant, nous allons supprimer un groupe de personnes pour plusieurs groupes dans différents sites à l’aide du même fichier CSV. Voici un exemple de commande :

```powershell
Import-Csv C:\O365Admin\Users.csv | ForEach {Remove-SPOUser -LoginName $_.LoginName -Site $_.Site -Group $_.Group}
```

## <a name="generate-user-reports"></a>Générer des rapports sur les utilisateurs

Vous pouvez obtenir un rapport pour quelques sites et afficher les utilisateurs de ces sites, leur niveau d’autorisation et d’autres propriétés. Voici à quoi ressemble la syntaxe :

```powershell
$tenant = "<tenant name, such as litwareinc for litwareinc.com>"
$site = "<site name>"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | select * | Format-table -Wrap -AutoSize | Out-File c\UsersReport.txt -Force -Width 360 -Append
```

Cela permet de collecter les données de ces trois sites et de les écrire dans un fichier texte sur votre lecteur local. Le paramètre –Append ajoute un nouveau contenu à un fichier existant.

Par exemple, nous allons exécuter un rapport sur les sites ContosoTest, TeamSite01 et Project01 pour la location contoso1 :

```powershell
$tenant = "contoso"
$site = "contosotest"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "TeamSite01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site |Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
$site = "Project01"
Get-SPOUser -Site https://$tenant.sharepoint.com/sites/$site | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Nous avons dû modifier uniquement la variable **$site** . La **variable $tenant** conserve sa valeur au cours des trois exécutions de la commande.

Mais que faire si vous souhaitez effectuer cette action pour chaque site ? Vous pouvez le faire sans avoir à entrer tous ces sites web à l’aide de cette commande :

```powershell
Get-SPOSite | ForEach {Get-SPOUser –Site $_.Url} | Format-Table -Wrap -AutoSize | Out-File c:\UsersReport.txt -Force -Width 360 -Append
```

Ce rapport est assez simple, et vous pouvez ajouter du code pour créer des rapports plus spécifiques ou des rapports qui contiennent des informations plus détaillées. Toutefois, cela devrait vous donner une idée de l’utilisation du SharePoint Online Management Shell pour gérer les utilisateurs dans l’environnement SharePoint Online.

## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Gérer SharePoint Online avec PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
