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
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: Découvrez comment contrôler les utilisateurs qui peuvent créer Microsoft 365 groupes.
ms.openlocfilehash: 19a106d255708f4b1df8f798219ea7ea778bbef3
ms.sourcegitcommit: f780de91bc00caeb1598781e0076106c76234bad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52539178"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Gérer les personnes autorisées à créer des groupes Microsoft 365

Par défaut, tous les utilisateurs peuvent créer Microsoft 365 groupes. Il s’agit de l’approche recommandée, car elle permet aux utilisateurs de commencer à collaborer sans nécessiter l’assistance de l’équipe technique.

Si votre entreprise exige que vous restreignez les personnes qui peuvent créer des groupes, vous pouvez limiter la création de groupes Microsoft 365 aux membres d’un groupe Microsoft 365 particulier ou d’un groupe de sécurité.

Si vous êtes préoccupé par le fait que les utilisateurs créent des équipes ou des groupes qui ne sont pas conformes à vos normes professionnelles, envisagez de demander aux utilisateurs de terminer un cours de formation, puis de les ajouter au groupe d’utilisateurs autorisés.

Lorsque vous limitez les personnes autorisées à créer un groupe, cela affecte tous les services qui s’appuient sur les groupes pour l’accès, notamment :

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planificateur
- Power BI (classique)
- Project pour le web / Feuille de route

Les étapes de cet article n’empêchent pas les membres de certains rôles de créer des groupes. Office 365 Les administrateurs globaux peuvent créer des groupes via Microsoft 365 centre d’administration, planificateur, Exchange et SharePoint Online. D’autres rôles peuvent créer des groupes via des moyens limités, répertoriés ci-dessous.

- Exchange Administrateur : Exchange admin center, Azure AD
- Support partenaire de niveau 1 : centre d’administration Microsoft 365, centre d’administration Exchange, Azure AD
- Support partenaire de niveau 2 : centre Microsoft 365'administration, centre Exchange’administration, Azure AD
- Rédacteurs d’annuaire : Azure AD
- SharePoint Administrateur : SharePoint admin center, Azure AD
- Teams Administrateur de service : Teams admin center, Azure AD
- Administrateur utilisateur : centre Microsoft 365'administration, Azure AD

Si vous êtes membre de l’un de ces rôles, vous pouvez créer des groupes Microsoft 365 pour les utilisateurs restreints, puis affecter l’utilisateur en tant que propriétaire du groupe.

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

Pour gérer les personnes qui créent des groupes, les personnes suivantes ont besoin de licences Azure AD Premium ou de licences Azure AD Basic EDU qui leur sont attribuées :

- Administrateur qui configure ces paramètres de création de groupe
- Membres du groupe autorisés à créer des groupes

> [!NOTE]
> Voir [Attribuer ou supprimer des licences dans](/azure/active-directory/fundamentals/license-users-groups) le portail Azure Active Directory pour plus d’informations sur l’attribution de licences Azure.

Les personnes suivantes n’ont pas besoin des licences Azure AD Premium ou Azure AD Basic EDU qui leur sont attribuées :

- Personnes qui sont membres de Microsoft 365 groupes et qui n’ont pas la possibilité de créer d’autres groupes.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>Étape 1 : Créer un groupe pour les utilisateurs qui doivent créer des groupes Microsoft 365 utilisateurs

Un seul groupe de votre organisation peut être utilisé pour contrôler qui est en mesure de créer des groupes. Toutefois, vous pouvez imbribrier d’autres groupes en tant que membres de ce groupe.

Les administrateurs des rôles répertoriés ci-dessus n’ont pas besoin d’être membres de ce groupe : ils conservent leur capacité à créer des groupes.

1. Dans le Centre d’administration, allez à la [page Groupes.](https://admin.microsoft.com/adminportal/home#/groups)

2. Cliquez sur **Ajouter un groupe.**

3. Choisissez le type de groupe de votre choix. Notez bien le nom du groupe ! Vous en aurez besoin plus tard.

4. Terminez la configuration du groupe, en ajoutant des personnes ou d’autres groupes que vous souhaitez pouvoir créer dans votre organisation.

Pour obtenir des instructions détaillées, voir Créer, modifier ou supprimer un groupe de sécurité dans [le centre d Microsoft 365'administration.](../admin/email/create-edit-or-delete-a-security-group.md)

## <a name="step-2-run-powershell-commands"></a>Étape 2 : exécuter les commandes PowerShell

Vous devez utiliser la version d’aperçu de [Azure Active Directory PowerShell pour Graph (AzureAD) (nom](/powershell/azure/active-directory/install-adv2) du module **AzureADPreview)** pour modifier le paramètre d’accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Install-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

Copiez le script ci-dessous dans un éditeur de texte, tel que Bloc-notes, ou le [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise).

Remplacez *\<GroupName\>* par le nom du groupe que vous avez créé. Par exemple :

`$GroupName = "Group Creators"`

Enregistrez le fichier sous GroupCreators.ps1.

Dans la fenêtre PowerShell, accédez à l’emplacement où vous avez enregistré le fichier (tapez « CD <FileLocation> »).

Exécutez le script en tapant :

`.\GroupCreators.ps1`

et [connectez-vous à l’invite avec votre compte](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) d’administrateur.

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
}
 else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

La dernière ligne du script affiche les paramètres mis à jour :

![Capture d’écran de la sortie du script PowerShell.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Si, à l’avenir, vous souhaitez modifier le groupe utilisé, vous pouvez réexécuter le script avec le nom du nouveau groupe.

Si vous souhaitez désactiver la restriction de création de groupe et autoriser à nouveau tous les utilisateurs à créer des groupes, définissez $GroupName sur « » et $AllowGroupCreation sur « True » et réexécutez le script.

## <a name="step-3-verify-that-it-works"></a>Étape 3 : vérifier le bon fonctionnement

L’application des modifications peut prendre 30 minutes ou plus. Vous pouvez vérifier les nouveaux paramètres en suivant les règles suivantes :

1. Connectez-vous Microsoft 365 avec un compte d’utilisateur d’une personne qui ne doit PAS avoir la possibilité de créer des groupes. Autrement dit, ils ne sont pas membres du groupe que vous avez créé ou administrateur.

2. Sélectionnez la **vignette Planificateur.**

3. Dans le Planificateur, **sélectionnez Nouveau plan** dans le navigation de gauche pour créer un plan.

4. Vous devez obtenir un message vous messageant que la création de groupe et de plan est désactivée.

Essayez à nouveau la même procédure avec un membre du groupe.

> [!NOTE]
> Si les membres du groupe ne sont pas en mesure de créer des groupes, vérifiez qu’ils ne sont pas bloqués par le biais de [leur stratégie OWA boîte aux lettres.](/powershell/module/exchange/set-owamailboxpolicy)

## <a name="related-topics"></a>Voir aussi

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Mise en route d’Office 365 PowerShell](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Configurer la gestion des groupes libre-service dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
