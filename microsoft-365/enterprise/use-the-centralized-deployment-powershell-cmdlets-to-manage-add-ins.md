---
title: Utiliser les cmdlets PowerShell de déploiement centralisé pour gérer les add-ins
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 1/24/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
ms.custom:
- seo-marvel-apr2020
description: Utilisez les cmdlets PowerShell de déploiement centralisé pour vous aider à déployer et gérer des Office pour votre Microsoft 365 organisation.
ms.openlocfilehash: 37a60ffe7d17f09ecbdb70c80c880b2c7bd51645
ms.sourcegitcommit: 6a73f0f0c0360fc015d9c0d0af26fb6926d9477d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2021
ms.locfileid: "58745840"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Utiliser les cmdlets PowerShell de déploiement centralisé pour gérer les add-ins

En tant qu’administrateur général Microsoft 365, vous pouvez déployer des Office pour les utilisateurs via la fonctionnalité Déploiement centralisé (voir [Déployer](../admin/manage/manage-deployment-of-add-ins.md)des Office dans le Centre d’administration). En plus de déployer Office compléments via le Centre d’administration Microsoft 365, vous pouvez également utiliser Microsoft PowerShell. Installez le [module de déploiement centralisé O365 Add-In pour Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Après avoir téléchargé le module, ouvrez une fenêtre Windows PowerShell et exécutez l’cmdlet suivante :

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Connecter à l’aide de vos informations d’identification d’administrateur

Avant de pouvoir utiliser les cmdlets de déploiement centralisé, vous devez vous inscrire.
  
1. Démarrez PowerShell.
    
2. Connecter powerShell à l’aide des informations d’identification d’administrateur de votre entreprise. Exécutez l’cmdlet suivante.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. Dans la page **Entrer les informations d’identification,** entrez Microsoft 365 administrateur **utilisateur** ou **administrateur** global. Vous pouvez également entrer vos informations d’identification directement dans la cmdlet. 
    
    Exécutez l’cmdlet suivante en spécifiant les informations d’identification d’administrateur de votre entreprise en tant qu’objet PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Pour plus d’informations sur l’utilisation de PowerShell, [voir Connecter à Microsoft 365 avec PowerShell.](./connect-to-microsoft-365-powershell.md) 
  
## <a name="upload-an-add-in-manifest"></a>Télécharger manifeste d’un add-in

Exécutez la cmdlet **New-OrganizationAdd-In** pour télécharger un manifeste de add-in à partir d’un chemin d’accès, qui peut être un emplacement de fichier ou une URL. L’exemple suivant montre un emplacement de fichier pour la valeur du _paramètre ManifestPath._ 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

Vous pouvez également exécuter la cmdlet **New-OrganizationAdd-In** pour télécharger un module et l’affecter directement à des utilisateurs ou des groupes à l’aide du paramètre  _Members,_ comme illustré dans l’exemple suivant. Séparez les adresses e-mail des membres par une virgule. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Télécharger un add-in à partir du Office Store

Exécutez la cmdlet **New-OrganizationAddIn** pour télécharger un manifeste à partir du Office Store.
  
Dans l’exemple suivant, la **cmdlet New-OrganizationAddIn** spécifie l’AssetId d’un add-in pour un marché de contenu et un emplacement aux États-Unis.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Pour déterminer la valeur du paramètre _AssetId,_ vous pouvez la copier à partir de l’URL de la page web Office Store pour le add-in. AssetIds always begin with « WA » followed by a number. Par exemple, dans l’exemple précédent, la source de la valeur AssetId de WA104099688 est l’URL de la page web du Office Store pour le add-in : [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688) .
  
Les valeurs des  _paramètres Locale_ et  _ContentMarket_ sont identiques et indiquent le pays/la région à partir de quel pays vous essayez d’installer le module. Le format est en-US, fr-FR. et ainsi de suite. 
  
> [!NOTE]
> Les add-ins téléchargés à partir du Office Store seront automatiquement mis à jour dans les quelques jours suivant la mise à jour la plus récente disponible sur le Office Store. 
  
## <a name="get-details-of-an-add-in"></a>Obtenir les détails d’un add-in

Exécutez la cmdlet **Get-OrganizationAddIn** comme indiqué ci-dessous pour obtenir les détails de tous les modules de développement téléchargés sur le client, y compris l’ID produit d’un module.
  
```powershell
Get-OrganizationAddIn
```

Exécutez **la cmdlet Get-OrganizationAddIn** avec une valeur pour le paramètre  _ProductId_ afin de spécifier le module pour lequel vous souhaitez récupérer des détails. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Pour obtenir les détails complets de tous les modules, ainsi que les utilisateurs et groupes affectés, canalez la sortie de la cmdlet **Get-OrganizationAddIn** vers la cmdlet Format-List, comme illustré dans l’exemple suivant.
  
```powershell
foreach($G in (Get-organizationAddIn)){Get-OrganizationAddIn -ProductId $G.ProductId | Format-List}
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activer ou désactiver un add-in

Pour désactiver un module de sorte que les utilisateurs et les groupes qui lui sont affectés n’y ont plus accès, exécutez la **cmdlet Set-OrganizationAddIn** avec le paramètre  _ProductId_ et le paramètre  _Enabled_ sur , comme illustré dans l’exemple  `$false` suivant.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Pour activer de nouveau un add-in, exécutez la même cmdlet avec le  _paramètre Enabled_ sur  `$true` .
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Ajouter ou supprimer des utilisateurs d’un add-in

Pour ajouter des utilisateurs et des groupes à un module spécifique, exécutez la cmdlet **Set-OrganizationAddInAssignments** avec les paramètres _ProductId,_ _Add_ et _Members._ Séparez les adresses e-mail des membres par une virgule. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour supprimer des utilisateurs et des groupes, exécutez la même cmdlet à l’aide du _paramètre Remove._ 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Pour affecter un add-in à tous les utilisateurs sur le client, exécutez la même cmdlet à l’aide du paramètre  _AssignToEveryone_ avec la valeur définie sur  `$true` .
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Pour ne pas affecter de module à tout le monde et revenir aux utilisateurs et groupes précédemment affectés, vous pouvez exécuter la même cmdlet et désactiver le paramètre  _AssignToEveryone_ en lui attribuant la valeur  `$false` .
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Mettre à jour un add-in

Pour mettre à jour un add-in à partir d’un manifeste, exécutez la **cmdlet Set-OrganizationAddIn** avec les paramètres  _ProductId,_  _ManifestPath_ et  _Locale,_ comme illustré dans l’exemple suivant. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Les add-ins téléchargés à partir du Office Store seront automatiquement mis à jour dans les quelques jours suivant la mise à jour la plus récente disponible sur le Office Store. 
  
## <a name="delete-an-add-in"></a>Suppression d’un complément

Pour supprimer un add-in, exécutez la **cmdlet Remove-OrganizationAddIn** avec le paramètre  _ProductId,_ comme illustré dans l’exemple suivant. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<!--
## Customize Microsoft Store add-ins for your organization

You must customize the add-in before you deploy it to your organization. Add-ins older than version 1.1 are not supported by this feature. 

We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.

Note also the following restrictions:
- All URLs must be absolute (include http or https) and valid.
- *DisplayName* must not exceed 125 characters 
- *DisplayName*, *Resources* and *AppDomains* must not include the following characters: 
 
    - \<
    -  \>
    -  ;
    -  =   

If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.

To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value. To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article. For example:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "https://site.com/img.jpg" 
```
To customize multiple tags for an add-in, add those tags to the commandline:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "https://site.com/img.jpg" 
```

> [!IMPORTANT]
> You must apply multiple customized tags to one add-in as one command. If you customize tags one by one, only the last customization will be applied. Additionally, if you customize a tag by mistake, you must remove all customizations and start over.

### Tags you can customize

| Tag                  | Description          |
| :------------------- | :------------------- |
| \<IconURL>   </br>| The URL of the image used as the add-in’s icon (in admin center). </br> |
| \<DisplayName>| The title of the add-in  (in admin center).|
| \<Hosts>| List of apps that will support the add-in.|
| \<SourceLocation> | The source URL that the add-in will connect to.| 
| \<AppDomains> | A list of domains that the add-in can connect with. | 
| \<SupportURL>| The URL users can use to access help and support. | 
| \<Resources>  | This tag contains a number of elements including titles, tooltips, and icons of different sizes.| 
|
### Customize Resources tag

Any element in the <Resources> tag of the manifest can be customized dynamically. You first need to check the manifest to find the element id to which you want to assign a new value. The <Resources> tag looks like this:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”https://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”

Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

You can customize as many elements with the command as you need to.

### Remove customization from an add-in

The only option currently available for deleting customizations is to delete all of them at once:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### View add-in customizations

To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet. If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.  

```powershell
Get-OrganizationAddInOverrides 
```
If ProductId is specified, then a list of overrides applied to that add-in is returned. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### Remove an add-in from local cache

If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized. To remive an add-in from cache:

1. Navigate to the “Users” folder in C:\ 
1. Go to your user folder
1. Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office
1. In the *Wef* folder delete the *Manifests* folder.

-->

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtenir une aide détaillée pour chaque cmdlet

Vous pouvez examiner l’aide détaillée de chaque cmdlet à l’aide de la cmdlet Get-help. Par exemple, l’cmdlet suivante fournit des informations détaillées sur l'Remove-OrganizationAddIn cmdlet.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```
