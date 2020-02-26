---
title: Gérer les personnes autorisées à créer des groupes Office 365
f1.keywords:
- NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MSP160
- MST160
- MET150
- MOE150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
description: Découvrez comment contrôler quels utilisateurs peuvent créer des groupes Office 365.
ms.openlocfilehash: a211cb3b69348a4d4a401a3c318fe019d8fd257f
ms.sourcegitcommit: 109b44aa71bb8453d0a602663df0fcf7ed7dfdbe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "42277191"
---
# <a name="manage-who-can-create-office-365-groups"></a>Gérer les personnes autorisées à créer des groupes Office 365

  
Étant donné que les utilisateurs peuvent créer facilement des groupes Office 365, vous n'êtes pas submergé par des demandes de création de la part d'autres personnes. Toutefois, en fonction de votre activité, vous souhaiterez peut-être contrôler les personnes autorisées à créer des groupes.
  
Cet article vous explique comment désactiver la possibilité de créer des groupes **dans tous les services Office 365 qui utilisent les groupes**: 
  
- Outlook
    
- SharePoint
    
- Yammer
    
- Microsoft Teams

- Microsoft Stream
    
- StaffHub
    
- Planificateur
    
- PowerBI

- Feuille de route
    
Vous pouvez restreindre la création de groupe Office 365 aux membres d’un groupe de sécurité particulier. Pour configurer ce, utilisez Windows PowerShell. Cet article vous guide tout au long des étapes nécessaires.
  
Les étapes décrites dans cet article n’empêchent pas les membres de certains rôles de créer des groupes. Les administrateurs globaux Office 365 peuvent créer des groupes via n’importe quel moyen, comme le centre d’administration Microsoft 365, le planificateur, teams, Exchange et SharePoint Online. D’autres rôles peuvent créer des groupes via des moyens limités, présentés ci-dessous.
        
  - Administrateur Exchange : Centre d’administration Exchange, Azure AD
    
  - Prise en charge du niveau 1 du partenaire : Centre d’administration Microsoft 365, Centre d’administration Exchange, Azure AD
    
  - Prise en charge du niveau 2 du partenaire : Centre d’administration Microsoft 365, Centre d’administration Exchange, Azure AD
    
  - Writers d’annuaire : Azure AD

  - Administrateur SharePoint : Centre d’administration SharePoint, Azure AD
  
  - Administrateur de service teams : Centre d’administration Teams, Azure AD
  
  - Administrateur de gestion des utilisateurs : Centre d’administration Microsoft 365, Yammer, Azure AD
     
Si vous êtes membre de l'un de ces rôles, vous pouvez créer des Groupes Office 365 pour un utilisateur avec accès restreint, puis attribuer le statut de propriétaire du groupe à l'utilisateur. Les utilisateurs qui ont ce rôle peuvent créer des groupes connectés dans Yammer, indépendamment des paramètres PowerShell susceptibles d’empêcher la création.

## <a name="licensing-requirements"></a>Critères de licence

Pour gérer la personne qui crée des groupes, les personnes suivantes ont besoin de licences Azure AD Premium ou d’Azure AD base EDU qui leur sont attribuées :

- Administrateur qui configure ces paramètres de création de groupe
- Les membres du groupe de sécurité autorisés à créer des groupes

Les personnes suivantes n’ont pas besoin de posséder des licences Azure ad Premium ou EDU AD basique EDU :

- Personnes membres des groupes Office 365 et qui ne peuvent pas créer d’autres groupes.

## <a name="step-1-create-a-security-group-for-users-who-need-to-create-office-365-groups"></a>Étape 1 : créer un groupe de sécurité pour des utilisateurs qui ont besoin de créer des Groupes Office 365

Un seul groupe de sécurité dans votre organisation peut être utilisé pour contrôler qui est en mesure de créer des groupes. Toutefois, vous pouvez imbriquer d'autres groupes de sécurité en tant que membres de ce groupe. Par exemple, le groupe intitulé « Autoriser la création de groupes » est le groupe de sécurité désigné, et les groupes intitulés Utilisateurs du Planificateur Microsoft et Utilisateurs d'Exchange Online sont membres de ce groupe.

Les administrateurs appartenant aux rôles mentionnés ci-dessus n’ont pas besoin d’être membres de ce groupe : ils conservent leur capacité à créer des groupes.

> [!IMPORTANT]
> Veillez à utiliser un **groupe de sécurité** pour limiter les personnes autorisées à créer des groupes. Si vous essayez d'utiliser un groupe Office 365, les membres ne pourront pas créer de groupe à partir de SharePoint, car ce service vérifie l'existence d'un groupe de sécurité. 
    
1. Dans le centre d’administration, accédez \> à **la page groupes de** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">groupes.</a>

2. Cliquez sur **Ajouter un groupe**.

3. Choisissez **Security** comme type de groupe. Notez bien le nom du groupe ! Vous en aurez besoin plus tard.
  
4. Terminez la configuration du groupe de sécurité, en ajoutant des personnes ou d’autres groupes de sécurité qui doivent être en mesure de créer des groupes dans votre organisation.
    
Pour obtenir des instructions détaillées, reportez-vous à [créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration 365 de Microsoft](../email/create-edit-or-delete-a-security-group.md).
  
## <a name="step-2-install-the-preview-version-of-the-azure-active-directory-powershell-for-graph"></a>Étape 2 : installer la version d’évaluation d’Azure Active Directory PowerShell pour Graph

Ces procédures nécessitent la version préliminaire d’Azure Active Directory PowerShell pour Graph. La version GA ne fonctionnera pas.


> [!IMPORTANT]
> Vous ne pouvez pas installer simultanément les versions aperçu et GA sur le même ordinateur. Vous pouvez installer le module sur Windows 10, Windows Server 2016.

  
Pour obtenir les meilleurs résultats, nous vous recommandons de  *toujours*  être à jour : désinstallez l'ancienne version d'AzureADPreview ou AzureAD, et téléchargez la plus récente. 
  
1. Dans la barre de recherche, tapez Windows PowerShell.
    
2. Cliquez avec le bouton droit sur **Windows PowerShell**, puis sélectionnez **Exécuter en tant qu'administrateur**.
    
    ![Ouvrez PowerShell avec « Exécuter en tant qu'administrateur ».](../media/52517af8-c7b0-4c8f-b2f3-0f82f9d5ace1.png)
    
3. Définissez la stratégie sur RemoteSigned à l’aide de [Set-ExecutionPolicy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy).
    
    ```
    Set-ExecutionPolicy RemoteSigned
    ```
  
4. Vérifiez le module installé :
    
    ```
    Get-InstalledModule -Name "AzureAD*"
    ```

5. Pour désinstaller une version précédente de AzureADPreview ou AzureAD, exécutez la commande suivante :
  
    ```
    Uninstall-Module AzureADPreview
    ```

    ou
  
    ```
    Uninstall-Module AzureAD
    ```

6. To install the latest version of AzureADPreview, run this command:
  
    ```
    Install-Module AzureADPreview
    ```

    At the message about an untrusted repository, type **Y**. It will take a minute or so for the new module to install. 

Laissez la fenêtre PowerShell ouverte à l’étape 3, ci-dessous.
  
## <a name="step-3-run-powershell-commands"></a>Étape 3 : exécuter les commandes PowerShell

Copiez le script ci-dessous dans un éditeur de texte, tel que le bloc-notes, ou [Windows PowerShell ISE](https://docs.microsoft.com/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Remplacez * \<SecurityGroupName\> * par le nom du groupe de sécurité que vous avez créé. Par exemple :

`$GroupName = "Group Creators"`

Enregistrez le fichier sous le GroupCreators. ps1. 

Dans la fenêtre PowerShell, accédez à l’emplacement où vous avez enregistré le fichier (tapez « <FileLocation>CD »).

Exécutez le script en tapant :

`.\GroupCreators.ps1`

Lorsque vous y êtes invité, [Connectez-vous avec votre compte d’administrateur](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#step-2-connect-to-azure-ad-for-your-office-365-subscription) .

```PowerShell
$GroupName = "<SecurityGroupName>"
$AllowGroupCreation = "False"

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
      $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
    $settingsCopy = $template.CreateDirectorySetting()
    New-AzureADDirectorySetting -DirectorySetting $settingsCopy
    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
    $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
}
 else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

La dernière ligne du script affiche les paramètres mis à jour :

![This is what your settings will look like when you're done.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Si, à l’avenir, vous souhaitez modifier le groupe de sécurité utilisé, vous pouvez réexécuter le script avec le nom du nouveau groupe de sécurité.

Si vous souhaitez désactiver la restriction de création de groupe et permettre à tous les utilisateurs de créer des groupes, définissez $GroupName sur "" et $AllowGroupCreation sur "true", puis réexécutez le script.
    
## <a name="step-4-verify-that-it-works"></a>Étape 4 : vérifier qu’elle fonctionne

1. Connectez-vous à Office 365 avec le compte d'utilisateur d'une personne qui ne doit PAS être autorisée à créer des groupes. Autrement dit, ils ne sont pas membres du groupe de sécurité que vous avez créé ou d’un administrateur.
    
2. Sélectionnez la vignette **planificateur** . 
    
3. Dans le planificateur, sélectionnez **nouveau plan** dans le volet de navigation de gauche pour créer un plan. 
  
4. Vous devriez recevoir un message indiquant que la création de plan et de groupe est désactivée.

Renouvelez la même procédure avec un membre du groupe de sécurité.

> [!NOTE]
> Si les membres du groupe de sécurité ne peuvent pas créer de groupes, vérifiez qu’ils ne sont pas bloqués via leur [stratégie de boîte aux lettres OWA](https://go.microsoft.com/fwlink/?linkid=852135).
    
## <a name="related-articles"></a>Articles connexes

[Mise en route d’Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=808033)

[Configurer la gestion des groupes en libre-service dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
