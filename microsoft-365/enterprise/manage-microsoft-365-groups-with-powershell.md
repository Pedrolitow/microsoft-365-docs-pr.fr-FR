---
title: Gérer les groupes Microsoft 365 avec PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Dans cet article, découvrez comment effectuer des tâches de gestion courantes pour les groupes Microsoft 365 dans PowerShell.
ms.openlocfilehash: 1cad2aa39a6b106cbb4dbfbafa995899b2442ed1
ms.sourcegitcommit: 9d1351ea6d9942550b52132817f9f9693ddef2fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2020
ms.locfileid: "48830614"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Gérer les groupes Microsoft 365 avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Cet article décrit les étapes à suivre pour effectuer des tâches de gestion courantes pour les groupes dans Microsoft PowerShell. Il répertorie également les cmdlets PowerShell pour les groupes. Pour plus d’informations sur la gestion des sites SharePoint, voir [Gérer les sites SharePoint Online à l’aide de PowerShell.](https://docs.microsoft.com/sharepoint/manage-team-and-communication-sites-in-powershell)

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Lien vers vos recommandations en matière d’utilisation des Groupes Microsoft 365
<a name="BK_LinkToGuideLines"> </a>

Lorsque les [utilisateurs créent ou modifient](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx)un groupe dans Outlook, vous pouvez leur afficher un lien vers les instructions d’utilisation de votre organisation. Par exemple, si vous avez besoin d’ajouter un préfixe ou un suffixe spécifique à un nom de groupe.

Utilisez Azure Active Directory (Azure AD) PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes Microsoft 365. Consultez les [cmdlets Azure Active Directory](https://go.microsoft.com/fwlink/?LinkID=827484) pour configurer les paramètres de groupe et suivez les étapes de la procédure Créer des **paramètres** au niveau de l’annuaire pour définir le lien hypertexte de recommandation d’utilisation. Une fois que vous avez exécuté la cmdlet AAD, les utilisateurs voient le lien vers vos instructions lorsqu’ils créent ou modifient un groupe dans Outlook.

![Créer un groupe avec le lien Recommandations en matière d’utilisation](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Cliquez sur Recommandations en matière d’utilisation des groupes pour consulter les recommandations relatives aux groupes Office 365 de votre organisation](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Autoriser les utilisateurs à envoyer en tant que groupe Microsoft 365
<a name="BK_LinkToGuideLines"> </a>

Si vous souhaitez activer vos groupes Microsoft 365 pour « Envoyer en tant que », utilisez les cmdlets [Add-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/add-recipientpermission) et [Get-RecipientPermission](https://docs.microsoft.com/powershell/module/exchange/get-recipientpermission) pour configurer cette configuration. Une fois ce paramètre activé, les utilisateurs du groupe Microsoft 365 peuvent utiliser Outlook ou Outlook sur le web pour envoyer des messages électroniques et y répondre en tant que groupe Microsoft 365. Les utilisateurs peuvent aller au groupe, créer un e-mail et modifier le champ « Envoyer en tant que » en l’adresse e-mail du groupe.

([Vous pouvez également le faire dans le Centre d’administration Exchange.)](https://docs.microsoft.com/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)

Utilisez le script suivant, en remplaçant par l’alias du groupe que vous souhaitez mettre à jour, et par l’alias de l’utilisateur auquel vous souhaitez accorder *\<GroupAlias\>* *\<UserAlias\>* des autorisations. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) pour exécuter ce script.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Une fois la cmdlet exécutée, les utilisateurs peuvent se rendre dans Outlook ou Outlook sur le web pour envoyer en tant que groupe, en ajoutant l’adresse de messagerie du groupe au champ **De.**

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Créer des classifications pour les groupes Microsoft 365 dans votre organisation

Vous pouvez créer des étiquettes de niveau de sensibilité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Si vous souhaitez classer des groupes, nous vous recommandons d’utiliser des étiquettes de niveau de sensibilité plutôt que la fonctionnalité de classification des groupes précédente. Pour plus d’informations sur l’utilisation des étiquettes de sensibilité, voir Utiliser des étiquettes de niveau de sensibilité pour protéger le contenu dans Microsoft Teams, les groupes [Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)et les sites SharePoint.

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de niveau de sensibilité activées.

Vous pouvez toujours utiliser la fonctionnalité de classification des groupes précédente. Vous pouvez créer des classifications que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Par exemple, vous pouvez autoriser les utilisateurs à définir « Standard », « Secret » et « Top Secret » sur les groupes qu’ils créent. Les classifications de groupe ne sont pas définies par défaut et vous devez la créer pour que vos utilisateurs la définissent. Utilisez Azure Active Directory PowerShell pour pointer vos utilisateurs vers les instructions d’utilisation de votre organisation pour les groupes Microsoft 365.

Consultez les [cmdlets Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets) pour configurer les paramètres de groupe et suivez les étapes de la procédure Créer des **paramètres** au niveau de l’annuaire pour définir la classification des groupes Microsoft 365.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Pour associer une description à chaque classification, vous pouvez utiliser l’attribut paramètres  *ClassificationDescriptions* pour définir.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

où Classification correspond aux chaînes dans ClassificationList.

Exemple :

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Après avoir exécuté la cmdlet Azure Active Directory ci-dessus pour définir votre classification, exécutez la cmdlet [Set-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/Set-UnifiedGroup) si vous souhaitez définir la classification pour un groupe spécifique.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Vous pouvez également créer un groupe avec une classification.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Consultez [l’utilisation de PowerShell avec Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell) et [connectez-vous](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) à Exchange Online PowerShell pour plus d’informations sur l’utilisation d’Exchange Online PowerShell.

Une fois ces paramètres activés, le propriétaire du groupe peut choisir une classification dans le menu déroulant  dans Outlook sur le web et Outlook, puis l’enregistrer à partir de la page Modifier le groupe.

![Choisir la classification de groupe Microsoft 365](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Masquer les groupes Microsoft 365 dans la liste d’adresses globale.
<a name="BKMK_CreateClassification"> </a>

Vous pouvez spécifier si un groupe Microsoft 365 apparaît dans la liste d’adresses globale (LAL) et dans d’autres listes de votre organisation. Par exemple, si vous avez un groupe de services juridiques que vous ne souhaitez pas afficher dans la liste d’adresses, vous pouvez empêcher ce groupe d’apparaître dans la liste d’adresses. Exécutez la cmdlet Set-Unified groupe pour masquer le groupe dans la liste d’adresses comme ceci :

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Autoriser uniquement les utilisateurs internes à envoyer des messages aux groupes Microsoft 365
<a name="BKMK_CreateClassification"> </a>

Si vous ne souhaitez pas que les utilisateurs d’autres organisations envoient des courriers électroniques à un groupe Microsoft 365, vous pouvez modifier les paramètres de ce groupe. Il permet uniquement aux utilisateurs internes d’envoyer un courrier électronique à votre groupe. Si un utilisateur externe tente d’envoyer un message à ce groupe, il est rejeté.

Exécutez lSet-UnifiedGroup cmdlet pour mettre à jour ce paramètre, comme ceci :

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Ajouter des mailTips aux groupes Microsoft 365
<a name="BKMK_CreateClassification"> </a>

Chaque fois qu’un expéditeur tente d’envoyer un courrier électronique à un groupe Microsoft 365, une boîte aux lettres peut lui être affichée.

Exécutez la cmdlet Set-Unified groupe pour ajouter une mailTip au groupe :

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

En plus de l’tip de courrier, vous pouvez également définir MailTipTranslations, qui spécifie des langues supplémentaires pour l’mailTip. Supposons que vous vouliez avoir la traduction espagnole, puis exécutez la commande suivante :

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Modifier le nom complet du groupe Microsoft 365

Le nom complet spécifie le nom du groupe Microsoft 365. Vous pouvez voir ce nom dans votre Centre d’administration Exchange ou dans le Centre d’administration Microsoft 365. Vous pouvez modifier le nom complet du groupe ou attribuer un nom complet à un groupe Microsoft 365 existant en exécutant la commande Set-UnifiedGroup commande :

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Modifier le paramètre par défaut de Groupes Microsoft 365 pour Outlook sur Public ou Privé
<a name="BKMK_CreateClassification"> </a>

Les groupes Microsoft 365 dans Outlook sont créés en tant que groupes privés par défaut. Si votre organisation souhaite que les groupes Microsoft 365 soient créés en tant que Groupes Publics par défaut (ou de nouveau en privé), utilisez la syntaxe de l’cmdlet PowerShell suivante :

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

Pour définir sur Privé :

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

Pour vérifier le paramètre :

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

Pour plus d’informations, [voir Set-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/set-organizationconfig) et [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Cmdlets de groupes Microsoft 365

Les cmdlets suivantes peuvent être utilisées avec les Groupes Microsoft 365.

|**Nom de l'applet de commande**|**Description**|
|:-----|:-----|
|[Get-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616182) <br/> |Utilisez cette cmdlet pour rechercher des groupes Microsoft 365 existants et pour afficher les propriétés de l’objet groupe  <br/> |
|[Set-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616189) <br/> |Mettre à jour les propriétés d’un groupe Microsoft 365 spécifique  <br/> |
|[New-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616183) <br/> |Créez un groupe Microsoft 365. Cette cmdlet fournit un ensemble minimal de paramètres. Pour définir des valeurs pour les propriétés étendues, utilisez Set-UnifiedGroup après la création du nouveau groupe  <br/> |
|[Remove-UnifiedGroup](https://go.microsoft.com/fwlink/p/?LinkId=616186) <br/> |Supprimer un groupe Microsoft 365 existant  <br/> |
|[Get-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616194) <br/> |Récupérer les informations d’appartenance et de propriétaire d’un groupe Microsoft 365  <br/> |
|[Add-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616191) <br/> |Ajouter des membres, des propriétaires et des abonnés à un groupe Microsoft 365 existant <br/> |
|[Remove-UnifiedGroupLinks](https://go.microsoft.com/fwlink/p/?LinkId=616195) <br/> |Supprimer des propriétaires et des membres d’un groupe Microsoft 365 existant  <br/> |
|[Get-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536510) <br/> |Utilisé pour afficher les informations sur la photo de l’utilisateur associée à un compte. Les photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Set-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536511) <br/> |Utilisé pour associer une photo d’utilisateur à un compte. Les photos de l’utilisateur sont stockées dans Active Directory  <br/> |
|[Remove-UserPhoto](https://go.microsoft.com/fwlink/p/?LinkId=536512) <br/> |Supprimer la photo d’un groupe Microsoft 365  <br/> |

## <a name="related-topics"></a>Rubriques connexes

[Mettre à niveau les listes de distribution vers groupes Microsoft 365](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)

[Gérer les personnes qui peuvent créer des groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups)

[Gérer l’accès invité aux groupes Microsoft 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Modifier l’appartenance à un groupe statique en dynamique dans](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type)
