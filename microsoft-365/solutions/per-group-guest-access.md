---
title: Empêcher l’ajout d’invités à un groupe spécifique
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Découvrez comment empêcher l’ajout d’invités à un groupe spécifique
ms.openlocfilehash: 366acaa609dd8ef3c5f500c87c27b2a637d62bec
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67584020"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Empêcher l’ajout d’invités à un groupe Microsoft 365 spécifique ou à une équipe Microsoft Teams spécifique

Si vous souhaitez autoriser l’accès invité à la plupart des groupes et des équipes, mais que vous souhaitez empêcher l’accès invité, vous pouvez bloquer l’accès invité pour des groupes et des équipes individuels. (Le blocage de l’accès invité à une équipe est effectué en bloquant l’accès invité au groupe associé.) Cela empêche l’ajout de nouveaux invités, mais ne supprime pas les invités qui sont déjà dans le groupe ou l’équipe.

Si vous utilisez des étiquettes de confidentialité dans votre organisation, nous vous recommandons de les utiliser pour contrôler l’accès invité par groupe. Pour plus d’informations sur la façon de procéder, [utilisez des étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md). Il s’agit de l’approche recommandée.

## <a name="change-group-settings-using-microsoft-powershell"></a>Modifier les paramètres de groupe à l’aide de Microsoft PowerShell

Vous pouvez également empêcher l’ajout de nouveaux invités à des groupes individuels à l’aide de PowerShell. (N’oubliez pas que le site SharePoint associé de l’équipe dispose de [contrôles de partage d’invités distincts](/sharepoint/change-external-sharing-site).)

Vous devez utiliser la préversion [d’Azure Active Directory PowerShell pour Graph](/powershell/azure/active-directory/install-adv2) (nom du module **AzureADPreview**) pour modifier le paramètre d’accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Install-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

> [!NOTE]
> Vous devez disposer des droits d’administrateur général pour exécuter ces commandes. 

Exécutez le script suivant, en remplaçant *\<GroupName\>* le nom du groupe dans lequel vous souhaitez bloquer l’accès invité.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Pour vérifier vos paramètres, exécutez la commande suivante :

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

La vérification ressemble à ceci :
    
![Capture d’écran de la fenêtre PowerShell montrant que l’accès au groupe invité a été défini sur false.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Si vous souhaitez réactiver le paramètre pour autoriser l’accès invité à un groupe particulier, exécutez le script suivant, en remplaçant ```<GroupName>``` le nom du groupe dans lequel vous souhaitez autoriser l’accès invité.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$True
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
$id = (get-AzureADObjectSetting -TargetType groups -TargetObjectId $groupID).id
Set-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy -id $id
```

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Autoriser ou bloquer l’accès invité en fonction de son domaine

Vous pouvez autoriser ou bloquer les invités qui utilisent un domaine spécifique. Par exemple, si votre entreprise (Contoso) a un partenariat avec une autre entreprise (Fabrikam), vous pouvez ajouter Fabrikam à votre liste verte afin que vos utilisateurs puissent ajouter ces invités à leurs groupes.

Pour plus d’informations, consultez [Autoriser ou bloquer des invitations à des utilisateurs B2B provenant d’organisations spécifiques](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Ajouter des invités à la liste d’adresses globale

Par défaut, les invités ne sont pas visibles dans la liste d’adresses globale Exchange. Utilisez les étapes répertoriées ci-dessous pour rendre un invité visible dans la liste d’adresses globale.

Recherchez l’ObjectID de l’invité en exécutant :

```PowerShell
get-AzureADUser -all $true | ?{$_.CreationType -eq "Invitation"}
```

Exécutez ensuite ce qui suit à l’aide des valeurs appropriées pour ObjectID, GivenName, Surname, DisplayName et TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Gérer l’appartenance à un groupe dans le Centre d'administration Microsoft 365](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[Révisions d’accès Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
