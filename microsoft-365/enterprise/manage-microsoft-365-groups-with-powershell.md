---
title: Gérer Groupes Microsoft 365 avec PowerShell
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
ms.openlocfilehash: 407e242728bf37ebf8c11b8094bfa4931229e4ef
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372200"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Gérer Groupes Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Cet article décrit les étapes à suivre pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il répertorie également les applets de commande PowerShell pour les groupes. Pour plus d’informations sur la gestion des sites SharePoint, consultez [Gérer les sites SharePoint Online à l’aide de PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Lien vers vos instructions d’utilisation de Groupes Microsoft 365

Lorsque les utilisateurs [créent ou modifient un groupe dans Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), vous pouvez leur montrer un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous avez besoin d’ajouter un préfixe ou un suffixe spécifique à un nom de groupe.

Utilisez PowerShell Azure Active Directory (Azure AD) pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour Microsoft 365 groupes. Consultez [Azure Active Directory applets de commande pour configurer les paramètres de groupe](/azure/active-directory/enterprise-users/groups-settings-cmdlets) et suivez les **étapes décrites dans les paramètres de création au niveau du répertoire** pour définir le lien hypertexte des instructions d’utilisation. Une fois que vous avez exécuté l’applet de commande AAD, les utilisateurs voient le lien vers vos instructions lorsqu’ils créent ou modifient un groupe dans Outlook.

![Créez un groupe avec le lien des instructions d’utilisation.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Cliquez sur Instructions relatives à l’utilisation des groupes pour afficher les instructions de vos organisations Office 365 groupes.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Autoriser les utilisateurs à envoyer en tant que groupe Microsoft 365

Si vous souhaitez autoriser vos groupes Microsoft 365 à « Envoyer sous », utilisez les applets de [commande Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) et [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) pour configurer cela. Une fois ce paramètre activé, Microsoft 365 utilisateurs du groupe peuvent utiliser Outlook ou Outlook sur le web pour envoyer et répondre à un e-mail en tant que groupe Microsoft 365. Les utilisateurs peuvent accéder au groupe, créer un e-mail et remplacer le champ « Envoyer sous » par l’adresse e-mail du groupe.

([Vous pouvez également le faire dans le centre d’administration Exchange](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)

Utilisez le script suivant, en *\<GroupAlias\>* remplaçant par l’alias du groupe à mettre à jour et *\<UserAlias\>* par l’alias de l’utilisateur auquel vous souhaitez accorder des autorisations. [Connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour exécuter ce script.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Une fois l’applet de commande exécutée, les utilisateurs peuvent accéder à Outlook ou Outlook sur le web pour envoyer en tant que groupe, en ajoutant l’adresse e-mail du groupe au champ **From**.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Créer des classifications pour Groupes Microsoft 365 dans votre organisation

Vous pouvez créer des étiquettes de confidentialité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Si vous souhaitez classifier des groupes, nous vous recommandons d’utiliser des étiquettes de confidentialité au lieu de la fonctionnalité de classification des groupes précédente. Pour plus d’informations sur l’utilisation d’étiquettes de confidentialité, consultez [Utiliser des étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de confidentialité activées.

Vous pouvez toujours utiliser la fonctionnalité de classification des groupes précédents. Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Par exemple, vous pouvez autoriser les utilisateurs à définir « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Les classifications de groupe ne sont pas définies par défaut et vous devez la créer pour que vos utilisateurs le définissent. Utilisez Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour Groupes Microsoft 365.

Consultez [Azure Active Directory applets de commande pour configurer les paramètres de groupe](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) et suivez les **étapes décrites dans les paramètres de création au niveau du répertoire** pour définir la classification pour Groupes Microsoft 365.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Pour associer une description à chaque classification, vous pouvez utiliser les attributs de paramètre  *ClassificationDescriptions* à définir.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Où classification correspond aux chaînes dans classificationList.

Exemple :

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté l’applet de commande Azure Active Directory ci-dessus pour définir votre classification, exécutez l’applet [de commande Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) si vous souhaitez définir la classification pour un groupe spécifique.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Ou créez un groupe avec une classification.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Pour plus d’informations sur l’utilisation de Exchange Online PowerShell, consultez [l’utilisation de PowerShell avec Exchange Online](/powershell/exchange/exchange-online-powershell) et [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Une fois ces paramètres activés, le propriétaire du groupe peut choisir une classification dans le menu déroulant dans Outlook sur le web et Outlook, puis l’enregistrer à partir de la page **Modifier** le groupe.

![Choisissez Microsoft 365 classification de groupe.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Masquez Groupes Microsoft 365 de la liste d’adresses globale.

Vous pouvez spécifier si un groupe Microsoft 365 apparaît dans la liste d’adresses globale (GAL) et d’autres listes de votre organisation. Par exemple, si vous avez un groupe de services juridiques que vous ne souhaitez pas afficher dans la liste d’adresses, vous pouvez empêcher ce groupe d’apparaître dans la liste d’adresses. Exécutez l’applet de commande Set-Unified Group pour masquer le groupe de la liste d’adresses comme suit :

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Autoriser uniquement les utilisateurs internes à envoyer des messages à Groupes Microsoft 365

Si vous ne souhaitez pas que les utilisateurs d’autres organisations envoient des e-mails à un groupe Microsoft 365, vous pouvez modifier les paramètres de ce groupe. Il autorise uniquement les utilisateurs internes à envoyer un e-mail à votre groupe. Si un utilisateur externe tente d’envoyer un message à ce groupe, il est rejeté.

Exécutez l’applet de commande Set-UnifiedGroup pour mettre à jour ce paramètre, comme suit :

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Ajouter des info-bulles à Groupes Microsoft 365

Chaque fois qu’un expéditeur tente d’envoyer un e-mail à un groupe Microsoft 365, une info-bulle peut lui être affichée.

Exécutez l’applet de commande Set-Unified Group pour ajouter une info-bulle au groupe :

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Avec MailTip, vous pouvez également définir MailTipTranslations, qui spécifient d’autres langues pour l’info-bulle. Supposons que vous souhaitiez avoir la traduction en espagnol, puis exécutez la commande suivante :

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Modifier le nom d’affichage du groupe Microsoft 365

Le nom complet spécifie le nom du groupe Microsoft 365. Vous pouvez voir ce nom dans votre <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration ou</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a> Exchange. Vous pouvez modifier le nom d’affichage du groupe ou attribuer un nom d’affichage à un groupe Microsoft 365 existant en exécutant la commande Set-UnifiedGroup :

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut de Groupes Microsoft 365 pour Outlook en public ou privé

Groupes Microsoft 365 dans Outlook sont créées comme privées par défaut. Si votre organisation souhaite que Groupes Microsoft 365 soit créé en tant que public par défaut (ou revenir à Private), utilisez la syntaxe de l’applet de commande PowerShell :

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Public
 ```

Pour définir sur Privé :

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Private
 ```

Pour vérifier le paramètre :

 ```powershell
 Get-OrganizationConfig | ft DefaultGroupAccessType
 ```

Pour plus d’informations, consultez [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) et [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>applets de commande Groupes Microsoft 365

Les applets de commande suivantes peuvent être utilisées avec Groupes Microsoft 365.

|**Nom de l'applet de commande**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Utilisez cette applet de commande pour rechercher des Groupes Microsoft 365 existants et afficher les propriétés de l’objet de groupe  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Mettre à jour les propriétés d’un groupe Microsoft 365 spécifique  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Créez un groupe Microsoft 365. Cette applet de commande fournit un ensemble minimal de paramètres. Pour définir des valeurs pour les propriétés étendues, utilisez Set-UnifiedGroup après la création du groupe  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Supprimer un groupe de Microsoft 365 existant  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Récupérer les informations d’appartenance et de propriétaire d’un groupe Microsoft 365  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Ajouter des membres, des propriétaires et des abonnés à un groupe Microsoft 365 existant <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Supprimer des propriétaires et des membres d’un groupe de Microsoft 365 existant  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Permet d’afficher des informations sur la photo d’utilisateur associée à un compte. Les photos des utilisateurs sont stockées dans Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Permet d’associer une photo d’utilisateur à un compte. Les photos des utilisateurs sont stockées dans Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Supprimer la photo d’un groupe Microsoft 365  <br/> |

## <a name="related-topics"></a>Voir aussi

[Mettre à niveau les listes de distribution vers Groupes Microsoft 365](/office365/admin/manage/upgrade-distribution-lists)

[Gérer les personnes autorisées à créer des groupes Microsoft 365](/office365/admin/create-groups/manage-creation-of-groups)

[Gérer l’accès invité à Groupes Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Modifier l’appartenance à un groupe statique en mode dynamique](/azure/active-directory/users-groups-roles/groups-change-type)
