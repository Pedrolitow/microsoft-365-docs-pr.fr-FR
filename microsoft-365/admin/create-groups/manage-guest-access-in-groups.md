---
title: Gérer l’accès invité dans les groupes Office 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
- MOE150
ms.assetid: 9de497a9-2f5c-43d6-ae18-767f2e6fe6e0
description: Découvrez comment ajouter des invités à un groupe Office 365, afficher les utilisateurs invités et utiliser PowerShell pour contrôler l’accès invité.
ms.openlocfilehash: e76718ccb20843b252c939be48653c61c7c1f0a9
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42894502"
---
# <a name="manage-guest-access-in-office-365-groups"></a>Gérer l’accès invité dans les groupes Office 365

Par défaut, l’accès invité pour les groupes Office 365 est activé pour votre organisation. Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité à des groupes pour l’ensemble de l’organisation ou pour des groupes individuels.

Lorsqu’elle est activée, les membres du groupe peuvent inviter des utilisateurs invités à un groupe Office 365 via Outlook sur le Web. Les invitations sont envoyées au propriétaire du groupe pour approbation.

> [!Note]
> Les réseaux d’entreprise yammer en mode natif ou dans l' [Union européenne](https://go.microsoft.com/fwlink/?linkid=2107357) ne prennent pas en charge les invités réseau.
> Les groupes Yammer connectés à Office 365 ne prennent actuellement pas en charge l’accès invité, mais vous pouvez créer des groupes externes non connectés dans votre réseau Yammer. Consultez la rubrique [créer et gérer des groupes externes dans Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a.aspx) pour obtenir des instructions.

### <a name="edit-guest-information"></a>Modifier les informations invité

Une fois approuvé, l’utilisateur invité est ajouté au répertoire et au groupe.

L’accès invité dans des groupes est souvent utilisé dans le cadre d’un scénario plus large qui inclut SharePoint ou Teams. Ces services ont leurs propres paramètres de partage d’invités. Pour obtenir des instructions complètes sur la configuration du partage d’invités entre les groupes, SharePoint et Teams, voir :

- [Collaborer avec des invités sur un site](../../solutions/collaborate-in-site.md)
- [Collaborer avec des invités au sein d’une équipe](../../solutions/collaborate-as-team.md)

## <a name="manage-groups-guest-access"></a>Gérer les groupes accès invité

Si vous souhaitez activer ou désactiver l’accès invité dans des groupes, vous pouvez le faire dans le centre d’administration 365 de Microsoft.

1. Dans le centre d’administration, accédez aux **Settings** \> **paramètres** paramètres et sélectionnez **groupes Office 365**.
  
2. Sur la page **groupes Office 365** , indiquez si vous souhaitez autoriser les personnes extérieures à votre organisation à accéder aux ressources de groupe ou les propriétaires de groupes à ajouter des personnes en dehors de votre organisation à des groupes.

## <a name="add-guests-to-an-office-365-group-from-the-admin-center"></a>Ajouter des invités à un groupe Office 365 à partir du centre d’administration

Si l’invité existe déjà dans votre répertoire, vous pouvez l’ajouter à vos groupes à partir du centre d’administration 365 de Microsoft.
  
1. Dans le centre d’administration, accédez > à **la page groupes de****groupes.**
  
2. Cliquez sur le groupe auquel vous souhaitez ajouter l’invité, puis sélectionnez **Afficher tout et gérer les membres** sous l’onglet **membres** . 
  
4. Sélectionnez **Ajouter des membres**, puis choisissez le nom de l’invité que vous souhaitez ajouter.
    
5. Cliquez sur **Enregistrer**.

Si vous souhaitez ajouter un invité directement à l’annuaire, vous pouvez [Ajouter des utilisateurs de collaboration B2B Azure Active Directory dans le portail Azure](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator).

Si vous souhaitez modifier les informations d’un invité, vous pouvez [Ajouter ou mettre à jour les informations de profil d’un utilisateur à l’aide d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).
  
## <a name="block-guest-users-from-a-specific-group"></a>Bloquer les utilisateurs invités d’un groupe spécifique

Si vous souhaitez autoriser l’accès invité à la plupart des groupes, mais que vous souhaitez empêcher l’accès invité à la plupart des groupes à l’aide de Microsoft PowerShell.

Vous devez utiliser la version d’évaluation d' [Azure Active Directory PowerShell pour Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) (nom de module **AzureADPreview**) pour modifier le paramètre accès invité au niveau du groupe :

- Si vous n’avez jamais installé une version du module Azure AD PowerShell, consultez [l’installation du module Azure AD](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2?view=azureadps-2.0-preview#installing-the-azure-ad-module) et suivez les instructions d’installation de la préversion publique.

- Si la version générale 2.0 du module Azure AD PowerShell (AzureAD) est installée sur votre ordinateur, vous devez la désinstaller en exécutant `Uninstall-Module AzureAD` dans votre session PowerShell, puis installer la préversion en exécutant `Install-Module AzureADPreview`.

- Si vous avez déjà installé lapréversion, exécutez `Install-Module AzureADPreview` pour vous assurer qu’il s’agit de la dernière version de ce module.

> [!NOTE]
> Vous devez disposer des droits d’administrateur globaux pour exécuter ces commandes. 

Exécutez le script suivant, en * / * remplaçant par le nom du groupe dans lequel vous souhaitez bloquer l’accès invité.

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
    
![Capture d’écran de la fenêtre PowerShell indiquant que l’accès au groupe invité a été défini sur false.](../../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)
  
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

[Gérer l’appartenance au groupe dans le centre d’administration Microsoft 365](add-or-remove-members-from-groups.md)
  
[Avis d’accès à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser)
