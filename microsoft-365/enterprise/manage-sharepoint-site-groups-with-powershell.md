---
title: Gestion des groupes de sites SharePoint Online avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/17/2019
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
description: Dans cet article, recherchez les procédures d’utilisation de PowerShell pour Microsoft 365 afin de gérer les groupes de sites SharePoint Online.
ms.openlocfilehash: 1fd9e87b49248dfef6a451f681267a2aaf02269e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194662"
---
# <a name="manage-sharepoint-online-site-groups-with-powershell"></a>Gestion des groupes de sites SharePoint Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Bien que vous puissiez utiliser le Centre d'administration Microsoft 365, vous pouvez également utiliser PowerShell pour Microsoft 365 pour gérer vos groupes de sites SharePoint Online.

## <a name="before-you-begin"></a>Avant de commencer

Les procédures décrites dans cet article vous obligent à vous connecter à SharePoint Online. Pour plus d’informations, voir [Connect to SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

## <a name="view-sharepoint-online-with-powershell-for-microsoft-365"></a>Afficher SharePoint Online avec PowerShell pour Microsoft 365

Le Centre d’administration SharePoint Online propose des méthodes faciles à utiliser pour la gestion des groupes de sites. Par exemple, supposons que vous souhaitez examiner les groupes et les membres du groupe pour le `https://litwareinc.sharepoint.com/sites/finance` site. Voici ce que vous devez faire pour :

1. Dans le Centre d’administration SharePoint, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Sites actifs**</a>, puis l’URL du site.
2. Dans la page du site, sélectionnez <a href="https://go.microsoft.com/fwlink/?linkid=2185072" target="_blank">**Paramètres**</a> (situés dans le coin supérieur droit de la page), puis sélectionnez **Autorisations de site**.

Répétez ensuite ce processus pour le prochain site que vous souhaitez consulter.

Pour obtenir la liste des groupes avec PowerShell pour Microsoft 365, vous pouvez utiliser les commandes suivantes :

```powershell
$siteURL = "https://litwareinc.sharepoint.com/sites/finance"
$x = Get-SPOSiteGroup -Site $siteURL
foreach ($y in $x)
    {
        Write-Host $y.Title -ForegroundColor "Yellow"
        Get-SPOSiteGroup -Site $siteURL -Group $y.Title | Select-Object -ExpandProperty Users
        Write-Host
    }
```

Il existe deux façons d’exécuter ce jeu de commandes dans l’invite de commandes SharePoint Online Management Shell :

- Copiez les commandes dans le Bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** , sélectionnez les commandes, puis collez-les dans l’invite de commandes SharePoint Online Management Shell. Dans ce cas, PowerShell s’arrête à une **>>** invite. Appuyez sur Entrée pour exécuter la `foreach` commande.<br/>
- Copiez les commandes dans le Bloc-notes (ou un autre éditeur de texte), modifiez la valeur de la variable **$siteURL** et enregistrez ce fichier texte avec un nom et l’extension .ps1 dans un dossier approprié. Ensuite, exécutez le script à partir de l’invite de commandes SharePoint Online Management Shell en spécifiant son chemin d’accès et son nom de fichier. Voici un exemple de commande :

```powershell
C:\Scripts\SiteGroupsAndUsers.ps1
```

Dans les deux cas, quelque chose de ce type doit apparaître :

![Groupes de sites SharePoint Online.](../media/SPO-site-groups.png)

Il s’agit de tous les groupes qui ont été créés pour le site `https://litwareinc.sharepoint.com/sites/finance`et de tous les utilisateurs affectés à ces groupes. Les noms de groupes apparaissent en jaune pour que vous puissiez distinguer les noms de groupes de leurs membres.

Voici un autre exemple de jeu de commandes qui répertorie les groupes et toutes les appartenances aux groupes pour tous vos sites SharePoint Online.

```powershell
$x = Get-SPOSite
foreach ($y in $x)
    {
        Write-Host $y.Url -ForegroundColor "Yellow"
        $z = Get-SPOSiteGroup -Site $y.Url
        foreach ($a in $z)
            {
                 $b = Get-SPOSiteGroup -Site $y.Url -Group $a.Title
                 Write-Host $b.Title -ForegroundColor "Cyan"
                 $b | Select-Object -ExpandProperty Users
                 Write-Host
            }
    }
```

## <a name="see-also"></a>Voir aussi

[Connexion à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)

[Création de sites SharePoint Online et ajout d’utilisateurs avec PowerShell](create-sharepoint-sites-and-add-users-with-powershell.md)

[Gestion des utilisateurs et des groupes SharePoint Online avec PowerShell](manage-sharepoint-users-and-groups-with-powershell.md)

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)

[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)
