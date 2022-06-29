---
title: Gérer les personnes autorisées à créer des groupes Microsoft 365
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: Découvrez comment contrôler les utilisateurs qui peuvent créer des Groupes Microsoft 365.
ms.openlocfilehash: 2136fbf51912e00b7552e687282d4a80688dcd9e
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493040"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Gérer les personnes autorisées à créer des groupes Microsoft 365

Par défaut, tous les utilisateurs peuvent créer des groupes Microsoft 365. Il s’agit de l’approche recommandée, car elle permet aux utilisateurs de commencer à collaborer sans nécessiter l’aide de l’informatique.

Si votre entreprise exige que vous restreigniez qui peut créer des groupes, vous pouvez limiter Groupes Microsoft 365 création aux membres d’un groupe ou d’un groupe de sécurité Microsoft 365 particulier.

Si vous êtes préoccupé par les utilisateurs qui créent des équipes ou des groupes qui ne sont pas conformes aux normes de votre entreprise, envisagez de demander aux utilisateurs de suivre un cours de formation, puis de les ajouter au groupe d’utilisateurs autorisés.

Lorsque vous limitez qui peut créer un groupe, cela affecte tous les services qui s’appuient sur des groupes pour l’accès, notamment :

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planificateur
- Power BI (classique)
- Projet pour le web / Feuille de route

Les étapes décrites dans cet article n’empêchent pas les membres de certains rôles de créer des groupes. Les administrateurs généraux de Microsoft 365 peuvent créer des groupes via le Centre d'administration Microsoft 365, le Planificateur, Exchange et SharePoint, mais pas d’autres emplacements tels que Teams. D’autres rôles peuvent créer des Groupes Microsoft 365 par des moyens limités, répertoriés ci-dessous.

- Administrateur Exchange : Centre d’administration Exchange, Azure AD
- Support de niveau 1 partenaire : Centre d'administration Microsoft 365, Centre d’administration Exchange, Azure AD
- Support de niveau partenaire 2 : Centre d'administration Microsoft 365, Centre d’administration Exchange, Azure AD
- Enregistreurs d’annuaires : Azure AD
- Administrateur SharePoint : Centre d’administration SharePoint, Azure AD
- Administrateur de service Teams : Centre d’administration Teams, Azure AD
- Administrateur d’utilisateurs : Centre d'administration Microsoft 365, Azure AD

Si vous êtes membre de l’un de ces rôles, vous pouvez créer Groupes Microsoft 365 pour les utilisateurs restreints, puis affecter l’utilisateur en tant que propriétaire du groupe.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Pour gérer les personnes qui créent des groupes, les personnes suivantes ont besoin de licences Azure AD Premium ou de licences Azure AD Basic EDU qui leur sont attribuées :

- L’administrateur qui configure ces paramètres de création de groupe
- Membres du groupe autorisés à créer des groupes

> [!NOTE]
> Pour plus d’informations sur [l’attribution de licences Azure, consultez Attribuer ou supprimer des licences dans le portail Azure Active Directory](/azure/active-directory/fundamentals/license-users-groups) .

Les personnes suivantes n’ont pas besoin des licences Azure AD Premium ou Azure AD Basic EDU qui leur sont attribuées :

- Les personnes qui sont membres de groupes Microsoft 365 et qui n’ont pas la possibilité de créer d’autres groupes.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>Étape 1 : Créer un groupe pour les utilisateurs qui doivent créer des groupes Microsoft 365

Un seul groupe de votre organisation peut être utilisé pour contrôler qui est en mesure de créer Groupes Microsoft 365. Toutefois, vous pouvez imbriquer d’autres groupes en tant que membres de ce groupe.

Les administrateurs des rôles répertoriés ci-dessus n’ont pas besoin d’être membres de ce groupe : ils conservent leur capacité à créer des groupes.

1. Dans le Centre d’administration, accédez à la [page Groupes](https://admin.microsoft.com/adminportal/home#/groups).

2. Cliquez sur **Ajouter un groupe**.

3. Choisissez le type de groupe souhaité. Notez bien le nom du groupe ! Vous en aurez besoin plus tard.

4. Terminez la configuration du groupe, en ajoutant des personnes ou d’autres groupes que vous souhaitez créer en tant que membres (et non en tant que propriétaires).

Pour obtenir des instructions détaillées, consultez [Créer, modifier ou supprimer un groupe de sécurité dans le Centre d'administration Microsoft 365](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>Étape 2 : exécuter les commandes PowerShell

Vous devez utiliser la préversion [d’Azure Active Directory PowerShell pour Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2) nom de module **AzureADPreview**) pour modifier le paramètre d’accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Update-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

Copiez le script ci-dessous dans un éditeur de texte, tel que le Bloc-notes ou le [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Remplacez *\<GroupName\>* par le nom du groupe que vous avez créé. Par exemple :

`$GroupName = "Group Creators"`

Enregistrez le fichier en tant que GroupCreators.ps1.

Dans la fenêtre PowerShell, accédez à l’emplacement où vous avez enregistré le fichier (tapez « CD \<FileLocation\>»).

Exécutez le script en tapant :

`.\GroupCreators.ps1`

et [connectez-vous avec votre compte d’administrateur](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) lorsque vous y êtes invité.

```PowerShell
$GroupName = "<GroupName>"
$AllowGroupCreation = $False

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
} else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

La dernière ligne du script affiche les paramètres mis à jour :

![Capture d’écran de la sortie du script PowerShell.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Si vous souhaitez à l’avenir modifier le groupe utilisé, vous pouvez réexécuter le script avec le nom du nouveau groupe.

Si vous souhaitez désactiver la restriction de création de groupe et autoriser à nouveau tous les utilisateurs à créer des groupes, définissez $GroupName sur « » et $AllowGroupCreation sur « True » et réexécutez le script.

## <a name="step-3-verify-that-it-works"></a>Étape 3 : vérifier le bon fonctionnement

L’application des modifications peut prendre au moins trente minutes. Vous pouvez vérifier les nouveaux paramètres en procédant comme suit :

1. Connectez-vous à Microsoft 365 avec un compte d’utilisateur d’une personne qui ne doit PAS avoir la possibilité de créer des groupes. Autrement dit, ils ne sont pas membres du groupe que vous avez créé ou administrateur.

2. Sélectionnez la vignette **Planificateur** .

3. Dans le Planificateur, sélectionnez **Nouveau plan** dans le volet de navigation de gauche pour créer un plan.

4. Vous devez recevoir un message indiquant que la création d’un plan et d’un groupe est désactivée.

Réessayez la même procédure avec un membre du groupe.

> [!NOTE]
> Si les membres du groupe ne sont pas en mesure de créer des groupes, vérifiez qu’ils ne sont pas bloqués via leur [stratégie de boîte aux lettres OWA](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>Sujets associés

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Mise en route d’Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Configurer la gestion des groupes en libre-service dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
