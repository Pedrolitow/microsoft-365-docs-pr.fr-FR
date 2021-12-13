---
title: Gérer Microsoft 365 groupes avec PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Dans cet article, découvrez comment effectuer des tâches de gestion courantes pour Microsoft 365 groupes dans PowerShell.
ms.openlocfilehash: aed6af15889d7a0923207be5ea4220b3c3d6937c
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61422110"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Gérer Microsoft 365 groupes avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Cet article décrit les étapes à suivre pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il répertorie également les cmdlets PowerShell pour les groupes. Pour plus d’informations sur la gestion SharePoint sites web, voir [Gérer SharePoint sites en ligne à l’aide de PowerShell.](/sharepoint/manage-team-and-communication-sites-in-powershell)

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Lien vers vos recommandations Microsoft 365'utilisation des groupes de sécurité

Lorsque les [utilisateurs créent ou modifient](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)un groupe dans Outlook, vous pouvez leur afficher un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous avez besoin d’ajouter un préfixe ou un suffixe spécifique à un nom de groupe.

Utilisez la Azure Active Directory PowerShell (Azure AD) pour faire pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour Microsoft 365 groupes. Consultez [Azure Active Directory cmdlets](/azure/active-directory/enterprise-users/groups-settings-cmdlets) pour configurer les paramètres de groupe et suivez les étapes de la procédure Créer des **paramètres** au niveau du répertoire pour définir le lien hypertexte de recommandation d’utilisation. Une fois que vous avez exécuté AAD cmdlet, les utilisateurs voient le lien vers vos instructions lorsqu’ils créent ou modifient un groupe dans Outlook.

![Créez un groupe avec le lien Recommandations en matière d’utilisation.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Cliquez sur Recommandations en matière d’utilisation des groupes pour voir vos Office 365 groupes.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Autoriser les utilisateurs à envoyer en tant que Microsoft 365 groupe

Si vous souhaitez activer vos groupes Microsoft 365 sur « Envoyer en tant que », utilisez les cmdlets [Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) et [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) pour configurer cette configuration. Une fois ce paramètre activé, les Microsoft 365 de groupe peuvent utiliser Outlook ou Outlook sur le web pour envoyer et répondre à des messages électroniques en tant que Microsoft 365 groupe. Les utilisateurs peuvent aller au groupe, créer un e-mail et modifier le champ « Envoyer en tant que » en l’adresse e-mail du groupe.

([Vous pouvez également le faire dans le Exchange Admin Center.)](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)

Utilisez le script suivant, en remplaçant par l’alias du groupe que vous souhaitez mettre à jour, et par l’alias de l’utilisateur auquel vous souhaitez accorder *\<GroupAlias\>* *\<UserAlias\>* des autorisations. [Connecter à Exchange Online PowerShell pour](/powershell/exchange/connect-to-exchange-online-powershell) exécuter ce script.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Une fois la cmdlet exécutée, les utilisateurs peuvent passer à Outlook ou Outlook sur le web pour envoyer en  tant que groupe, en ajoutant l’adresse e-mail du groupe au champ De.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Créer des classifications pour Microsoft 365 groupes de votre organisation

Vous pouvez créer des étiquettes de niveau de sensibilité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un Microsoft 365 de données. Si vous souhaitez classer des groupes, nous vous recommandons d’utiliser des étiquettes de niveau de sensibilité plutôt que la fonctionnalité de classification des groupes précédente. Pour plus d’informations sur l’utilisation d’étiquettes de sensibilité, voir Utiliser des étiquettes de niveau de Microsoft Teams, Microsoft 365 groupes et sites [SharePoint sites.](../compliance/sensitivity-labels-teams-groups-sites.md)

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de niveau de sensibilité activées.

Vous pouvez toujours utiliser la fonctionnalité de classification de groupes précédente. Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent Microsoft 365 groupe. Par exemple, vous pouvez autoriser les utilisateurs à définir « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Les classifications de groupe ne sont pas définies par défaut et vous devez la créer pour que vos utilisateurs la définissent. Utilisez Azure Active Directory PowerShell pour faire pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour Microsoft 365 groupes.

Consultez [Azure Active Directory cmdlets](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) pour configurer les paramètres de groupe et suivez les étapes de la procédure Créer des **paramètres** au niveau du répertoire pour définir la classification des groupes Microsoft 365 de groupe.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Pour associer une description à chaque classification, vous pouvez utiliser l’attribut paramètres  *ClassificationDescriptions* pour définir.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

où Classification correspond aux chaînes dans ClassificationList.

Exemple :

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté l’Azure Active Directory cmdlet ci-dessus pour définir votre classification, exécutez la cmdlet [Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) si vous souhaitez définir la classification pour un groupe spécifique.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Vous pouvez également créer un groupe avec une classification.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Consultez [l’utilisation](/powershell/exchange/exchange-online-powershell) de PowerShell Exchange Online et Connecter pour Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour plus d’informations sur l’utilisation Exchange Online PowerShell.

Une fois ces paramètres activés, le propriétaire du groupe peut choisir une classification dans le menu déroulant dans Outlook  sur le Web et Outlook, puis l’enregistrer à partir de la page Modifier le groupe.

![Choisissez Microsoft 365 classification de groupe.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Masquez Microsoft 365 de la liste d’adresses globale.

Vous pouvez spécifier si un groupe Microsoft 365 apparaît dans la liste d’adresses globale (LAL) et dans d’autres listes de votre organisation. Par exemple, si vous avez un groupe de services juridiques que vous ne souhaitez pas afficher dans la liste d’adresses, vous pouvez empêcher ce groupe d’apparaître dans la liste d’adresses. Exécutez la cmdlet Set-Unified groupe pour masquer le groupe dans la liste d’adresses comme ceci :

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Autoriser uniquement les utilisateurs internes à envoyer des messages à Microsoft 365 groupes

Si vous ne souhaitez pas que les utilisateurs d’autres organisations envoient des courriers électroniques à un groupe Microsoft 365, vous pouvez modifier les paramètres de ce groupe. Il permet uniquement aux utilisateurs internes d’envoyer un courrier électronique à votre groupe. Si un utilisateur externe tente d’envoyer un message à ce groupe, il est rejeté.

Exécutez lSet-UnifiedGroup cmdlet pour mettre à jour ce paramètre, comme ceci :

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Ajouter des mailTips à Microsoft 365 groupes

Chaque fois qu’un expéditeur tente d’envoyer un message électronique à un groupe Microsoft 365, une boîte aux lettres peut s’affiche.

Exécutez la cmdlet Set-Unified groupe pour ajouter une mailTip au groupe :

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

En plus de l’tip de courrier, vous pouvez également définir MailTipTranslations, qui spécifie des langues supplémentaires pour l’mailTip. Supposons que vous vouliez avoir la traduction espagnole, puis exécutez la commande suivante :

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Modifier le nom complet du groupe de Microsoft 365

Le nom complet spécifie le nom du groupe Microsoft 365 groupe. Vous pouvez voir ce nom dans votre centre <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">d’administration Exchange ou</a> dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe Microsoft 365 existant en exécutant la commande Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut de Microsoft 365 groupes pour Outlook public ou privé

Microsoft 365 groupes dans Outlook sont créés comme privés par défaut. Si votre organisation souhaite créer Microsoft 365 groupes publics par défaut (ou de nouveau en privé), utilisez la syntaxe de l’cmdlet PowerShell suivante :

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

Pour définir sur Privé :

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

Pour vérifier le paramètre :

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

Pour plus d’informations, [voir Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) et [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 cmdlets de groupes

Les cmdlets suivantes peuvent être utilisées avec Microsoft 365 groupes.

|**Nom de l'applet de commande**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Utilisez cette cmdlet pour rechercher des groupes Microsoft 365 existants et pour afficher les propriétés de l’objet groupe  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Mettre à jour les propriétés d’un groupe Microsoft 365 spécifique  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Créez un groupe Microsoft 365'équipe. Cette cmdlet fournit un ensemble minimal de paramètres. Pour définir des valeurs pour les propriétés étendues, utilisez Set-UnifiedGroup après la création du nouveau groupe  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Supprimer un groupe de Microsoft 365 existant  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Récupérer les informations d’appartenance et de propriétaire d’Microsoft 365 groupe  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Ajouter des membres, des propriétaires et des abonnés à un groupe Microsoft 365 existant <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Supprimer des propriétaires et des membres d’un groupe Microsoft 365 existant  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Utilisé pour afficher les informations sur la photo de l’utilisateur associée à un compte. Les photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Utilisé pour associer une photo d’utilisateur à un compte. Les photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Supprimer la photo d’un groupe Microsoft 365 de recherche  <br/> |

## <a name="related-topics"></a>Voir aussi

[Mettre à niveau les listes de distribution Microsoft 365 groupes](/office365/admin/manage/upgrade-distribution-lists)

[Gérer les personnes autorisées à créer des groupes Microsoft 365](/office365/admin/create-groups/manage-creation-of-groups)

[Gérer l’accès invité à Microsoft 365 groupes](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Modifier l’appartenance à un groupe statique en dynamique dans](/azure/active-directory/users-groups-roles/groups-change-type)
