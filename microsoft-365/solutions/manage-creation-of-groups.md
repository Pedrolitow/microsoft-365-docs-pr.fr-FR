---
title: Gérer les personnes autorisées à créer des groupes Microsoft 365
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
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
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
description: Découvrez comment contrôler quels utilisateurs peuvent créer des groupes Microsoft 365.
ms.openlocfilehash: d6e6c6d9caff2ac7c13d03dad97b73906a509f46
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47307858"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Gérer les personnes autorisées à créer des groupes Microsoft 365

Par défaut, tous les utilisateurs peuvent créer des groupes Microsoft 365. Il s’agit de l’approche recommandée, car elle permet aux utilisateurs de commencer à collaborer sans avoir besoin d’assistance.

Si votre entreprise exige que vous restreigniez les personnes autorisées à créer des groupes, vous pouvez le faire en suivant les procédures décrites dans cet article. Lorsque vous limitez les personnes autorisées à créer un groupe, elle affecte tous les services qui dépendent des groupes pour l’accès, notamment :

- Outlook
    
- SharePoint
    
- Yammer
    
- Microsoft Teams

- Microsoft Stream

- Planificateur
    
- PowerBI (classique)
    
- Projet pour le Web/feuille de route
    
Vous pouvez restreindre la création de groupes Microsoft 365 aux membres d’un groupe de sécurité particulier. Pour configurer ce, utilisez Windows PowerShell. Cet article vous guide tout au long des étapes nécessaires.
  
Les étapes décrites dans cet article n’empêchent pas les membres de certains rôles de créer des groupes. Les administrateurs globaux Office 365 peuvent créer des groupes via n’importe quel moyen, comme le centre d’administration Microsoft 365, le planificateur, teams, Exchange et SharePoint Online. D’autres rôles peuvent créer des groupes via des moyens limités, présentés ci-dessous.
        
  - Administrateur Exchange : Centre d’administration Exchange, Azure AD
    
  - Prise en charge du niveau 1 du partenaire : Centre d’administration Microsoft 365, Centre d’administration Exchange, Azure AD
    
  - Prise en charge du niveau 2 du partenaire : Centre d’administration Microsoft 365, Centre d’administration Exchange, Azure AD
    
  - Writers d’annuaire : Azure AD

  - Administrateur SharePoint : Centre d’administration SharePoint, Azure AD
  
  - Administrateur de service teams : Centre d’administration Teams, Azure AD
  
  - Administrateur de gestion des utilisateurs : Centre d’administration Microsoft 365, Yammer, Azure AD
     
Si vous êtes membre de l’un de ces rôles, vous pouvez créer des groupes Microsoft 365 pour des utilisateurs restreints, puis affecter l’utilisateur comme propriétaire du groupe.

## <a name="licensing-requirements"></a>Critères de licence

Pour gérer la personne qui crée des groupes, les personnes suivantes ont besoin de licences Azure AD Premium ou d’Azure AD base EDU qui leur sont attribuées :

- Administrateur qui configure ces paramètres de création de groupe
- Les membres du groupe de sécurité autorisés à créer des groupes
 
> [!NOTE]
> Pour plus d’informations sur l’attribution de licences Azure [, voir attribuer ou supprimer des licences dans le portail Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/license-users-groups) .

Les personnes suivantes n’ont pas besoin de posséder des licences Azure ad Premium ou EDU AD basique EDU :

- Personnes membres des groupes Microsoft 365 et qui ne peuvent pas créer d’autres groupes.

## <a name="step-1-create-a-security-group-for-users-who-need-to-create-microsoft-365-groups"></a>Étape 1 : créer un groupe de sécurité pour les utilisateurs qui ont besoin de créer des groupes Microsoft 365

Un seul groupe de sécurité dans votre organisation peut être utilisé pour contrôler qui est en mesure de créer des groupes. Toutefois, vous pouvez imbriquer d'autres groupes de sécurité en tant que membres de ce groupe.

Les administrateurs appartenant aux rôles mentionnés ci-dessus n’ont pas besoin d’être membres de ce groupe : ils conservent leur capacité à créer des groupes.

> [!IMPORTANT]
> Veillez à utiliser un **groupe de sécurité** pour limiter les personnes autorisées à créer des groupes. L’utilisation d’un groupe Microsoft 365 n’est pas prise en charge. 
    
1. Dans le centre d’administration, accédez à la [page groupes](https://admin.microsoft.com/adminportal/home#/groups).

2. Cliquez sur **Ajouter un groupe**.

3. Choisissez **Security** comme type de groupe. Notez bien le nom du groupe ! Vous en aurez besoin plus tard.
  
4. Terminez la configuration du groupe de sécurité, en ajoutant des personnes ou d’autres groupes de sécurité qui doivent être en mesure de créer des groupes dans votre organisation.
    
Pour obtenir des instructions détaillées, reportez-vous à [créer, modifier ou supprimer un groupe de sécurité dans le centre d’administration 365 de Microsoft](https://docs.microsoft.com/microsoft-365/admin/email/create-edit-or-delete-a-security-group).
 
## <a name="step-2-run-powershell-commands"></a>Étape 2 : exécuter les commandes PowerShell

Vous devez utiliser la version d’évaluation d' [Azure Active Directory PowerShell pour Graph (AzureAD)](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (nom de module **AzureADPreview**) pour modifier le paramètre d’accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview#installing-the-azure-ad-module) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Install-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

Copiez le script ci-dessous dans un éditeur de texte, tel que le bloc-notes, ou [Windows PowerShell ISE](https://docs.microsoft.com/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Remplacez *\<SecurityGroupName\>* par le nom du groupe de sécurité que vous avez créé. Par exemple :

`$GroupName = "Group Creators"`

Enregistrez le fichier en tant que GroupCreators.ps1. 

Dans la fenêtre PowerShell, accédez à l’emplacement où vous avez enregistré le fichier (tapez « CD <FileLocation> »).

Exécutez le script en tapant :

`.\GroupCreators.ps1`

Lorsque vous y êtes invité, [Connectez-vous avec votre compte d’administrateur](https://docs.microsoft.com/microsoft-365/enterprise/connect-to-microsoft-365-powershell#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) .

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
    
## <a name="step-3-verify-that-it-works"></a>Étape 3 : vérifier le bon fonctionnement

Les modifications peuvent durer au moins 30 minutes. Vous pouvez vérifier les nouveaux paramètres en procédant comme suit :

1. Connectez-vous à Microsoft 365 avec un compte d’utilisateur qui ne doit pas avoir la possibilité de créer des groupes. Autrement dit, ils ne sont pas membres du groupe de sécurité que vous avez créé ou d’un administrateur.
    
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
