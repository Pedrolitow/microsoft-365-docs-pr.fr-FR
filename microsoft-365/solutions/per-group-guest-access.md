---
title: Bloquer les utilisateurs invités d’un groupe spécifique
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-collaboration
ms.custom:
- M365solutions
f1.keywords: NOCSH
description: Bloquer les utilisateurs invités d’un groupe spécifique
ms.openlocfilehash: 923a9e5cd09d232f377f55fd6a9f499f8f536a84
ms.sourcegitcommit: 66f1f430b3dcae5f46cb362a32d6fb7da4cff5c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "46662607"
---
# <a name="block-guest-users-from-a-specific-group"></a>Bloquer les utilisateurs invités d’un groupe spécifique

Si vous souhaitez autoriser l’accès invité à la plupart des groupes, mais que vous souhaitez empêcher l’accès invité à la plupart des groupes, vous pouvez bloquer l’accès invité pour des groupes individuels.

Si vous utilisez des étiquettes de confidentialité dans votre organisation, nous vous recommandons de les utiliser pour contrôler l’accès invité par groupe. Pour plus d’informations sur la procédure à suivre, [Utilisez les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes microsoft 365 et les sites SharePoint](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites). Il s’agit de l’approche recommandée.

Vous pouvez également bloquer l’accès invité à des groupes individuels à l’aide de Microsoft PowerShell.

Vous devez utiliser la version d’évaluation d' [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (nom de module **AzureADPreview**) pour modifier le paramètre accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview#installing-the-azure-ad-module) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Install-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

> [!NOTE]
> Vous devez disposer des droits d’administrateur globaux pour exécuter ces commandes. 

Exécutez le script suivant, */<GroupName/>* en remplaçant par le nom du groupe dans lequel vous souhaitez bloquer l’accès invité.

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

La vérification se présente comme suit :
    
![Capture d’écran de la fenêtre PowerShell indiquant que l’accès au groupe invité a été défini sur false.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)
  
## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Autoriser ou bloquer l’accès invité en fonction de leur domaine

Vous pouvez autoriser ou bloquer les utilisateurs invités qui utilisent un domaine spécifique. Par exemple, si votre entreprise (contoso) a un partenariat avec une autre entreprise (Fabrikam), vous pouvez ajouter Fabrikam à votre liste verte afin que vos utilisateurs puissent ajouter ces invités à leurs groupes.

Pour plus d’informations, reportez-vous à la rubrique [autoriser ou bloquer des invitations à des utilisateurs B2B d’organisations spécifiques](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Ajouter des invités à la liste d’adresses globale

Par défaut, les invités ne sont pas visibles dans la liste d’adresses globale d’Exchange. Utilisez les étapes répertoriées ci-dessous pour faire en sorte qu’un invité soit visible dans la liste d’adresses globale.

Recherchez l’ObjectID de l’utilisateur invité en exécutant :

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

Exécutez ensuite la commande suivante à l’aide des valeurs appropriées pour ObjectID, GivenName, Surname, DisplayName et TelephoneNumber.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-articles"></a>Articles connexes

[Gérer l’appartenance au groupe dans le centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/create-groups/add-or-remove-members-from-groups)
  
[Avis d’accès à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser)