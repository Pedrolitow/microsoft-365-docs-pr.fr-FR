---
title: Gestion des groupes dans Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 212e68ac-6330-47e9-a169-6cf5e2f21e13
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs d’organisations Exchange Online Protection (EOP) autonomes peuvent apprendre à créer, modifier et supprimer des groupes de distribution et des groupes de sécurité à messagerie dans le Centre d’administration Exchange (CAE) et dans Exchange Online Protection (EOP) autonome PowerShell.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3b97e3fac0840753edada964252875a6e3a4fa04
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51203992"
---
# <a name="manage-groups-in-eop"></a>Gestion des groupes dans Exchange Online Protection (EOP)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](exchange-online-protection-overview.md)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez créer, modifier et supprimer les types de groupes suivants :

- **Groupes de distribution**: collection d’utilisateurs de messagerie ou d’autres groupes de distribution. Par exemple, les équipes ou d’autres groupes ad hoc qui doivent recevoir ou envoyer des messages électroniques dans un domaine commun d’intérêt. Les groupes de distribution sont exclusivement dédiés à la distribution des messages électroniques et ne sont pas des principaux de sécurité (ils ne peuvent pas se voir attribuer d’autorisations).

- **Groupes de sécurité à messagerie**: collection d’utilisateurs de messagerie et d’autres groupes de sécurité qui ont besoin d’autorisations d’accès pour les rôles d’administrateur. Par exemple, vous souhaiterez peut-être accorder à un groupe spécifique d’utilisateurs des autorisations d’administration afin qu’ils configurent les paramètres anti-courrier indésirable et anti-programme malveillant.

    > [!NOTE]
    >
    > - Par défaut, les nouveaux groupes de sécurité à messagerie rejettent les messages provenant d’expéditeurs externes (non authentifiés).
    >
    > - N’ajoutez pas de groupes de distribution aux groupes de sécurité à messagerie.

Vous pouvez gérer des groupes dans le Centre d’administration Exchange (CAE) et dans EOP PowerShell autonome.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre d’administration Exchange, consultez le [Centre d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Lorsque vous gérez des groupes dans EOP PowerShell autonome, vous pouvez rencontrer une limitation. Les procédures PowerShell de cet article utilisent une méthode de traitement par lots qui entraîne un délai de propagation de quelques minutes avant que les résultats des commandes ne soient visibles.

- Des autorisations doivent vous être attribuées dans Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle  Groupes de  **distribution,** qui est attribué par défaut aux groupes de rôles Gestion de l’organisation et Gestion des destinataires. Pour plus d’informations, voir [Autorisations](feature-permissions-in-eop.md) dans EOP autonome et utiliser le CAE pour modifier la liste des membres des groupes [de rôles.](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cet article, voir raccourcis clavier pour le Centre d’administration [Exchange dans Exchange Online.](/Exchange/accessibility/keyboard-shortcuts-in-admin-center)

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://social.technet.microsoft.com/Forums/forefront/home?forum=FOPE) .

## <a name="use-the-exchange-admin-center-to-manage-distribution-groups"></a>Utiliser le Centre d’administration Exchange pour gérer les groupes de distribution

### <a name="use-the-eac-to-create-groups"></a>Utiliser le EAC pour créer des groupes

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Cliquez **sur Nouvelle** ![ ](../../media/ITPro-EAC-AddIcon.png) icône, puis sélectionnez l’une des options suivantes :

   - **Groupe de distribution**

   - **Groupe de sécurité à extension messagerie**

3. Dans la page de nouveau groupe qui s’ouvre, configurez les paramètres suivants. Les paramètres marqués par un <sup>\*</sup> paramètre sont obligatoires.

   - <sup>\*</sup>**Nom d’affichage**: ce nom apparaît dans le carnet d’adresses de votre organisation, sur la ligne À : lorsque le courrier électronique est envoyé à ce groupe, et dans la liste Groupes dans leAC.  Le nom d’affichage est obligatoire, doit être unique et convivial afin que les utilisateurs reconnaissent ce qu’il est.

   - <sup>\*</sup>**Alias**: utilisez cette zone pour taper le nom de l’alias du groupe. L’alias ne peut pas dépasser 64 caractères et doit être unique. Lorsqu’un utilisateur tape l’alias dans la ligne À d’un message électronique, il est résolu en nom complet du groupe.

   - <sup>\*</sup>**Adresse de messagerie**: l’adresse de messagerie se compose de l’alias sur le côté gauche du symbole (@) et d’un domaine sur le côté droit. Par défaut, la valeur **d’Alias** est utilisée pour la valeur d’alias, mais vous pouvez la modifier. Pour la valeur du domaine, cliquez sur le nom de domaine et sélectionnez le domaine accepté dans votre organisation.

   - **Description**: cette description apparaît dans le carnet d’adresses et dans le volet Détails du EAC.

   - <sup>\*</sup>**Propriétaires**: un propriétaire de groupe peut gérer l’appartenance au groupe. Par défaut, la personne qui crée un groupe en est le propriétaire. Tous les groupes doivent avoir au moins un propriétaire.

     Pour ajouter des propriétaires, cliquez **sur Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter ->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

     Pour supprimer un propriétaire, sélectionnez-le, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

   - **Membres :** ajoutez et supprimez des membres du groupe.

     Pour ajouter des membres, cliquez **sur Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter ->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

     Pour supprimer un membre, sélectionnez-le, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer le groupe de distribution.

### <a name="use-the-eac-to-modify-distribution-groups"></a>Utiliser le CENTRE D’EAC pour modifier des groupes de distribution

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Dans la liste des groupes, sélectionnez le groupe de distribution ou le  groupe de sécurité à messagerie à modifier, puis cliquez sur Modifier ![ l’icône ](../../media/ITPro-EAC-AddIcon.png) Modifier.

3. Dans la page des propriétés du groupe de distribution qui s’ouvre, cliquez sur l’un des onglets suivants pour afficher ou modifier les propriétés.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="general"></a>Général

Utilisez cet onglet pour afficher ou modifier les informations de base relatives au groupe.

- **Nom complet**: ce nom apparaît dans le carnet d’adresses, sur la ligne À lorsque le courrier électronique est envoyé à ce groupe et dans la liste **Groupes.** Le nom d'affichage est obligatoire et doit être convivial afin que les personnes identifient facilement de quoi il s'agit. Il doit également être unique dans votre domaine.

  Si vous avez implémenté une stratégie de noms de groupes, le nom d'affichage doit se conformer au format de nom défini par la stratégie.

- **Alias**: il s’agit de la partie de l’adresse de messagerie qui apparaît à gauche du symbole @. Si vous modifiez l'alias, l'adresse SMTP principale du groupe est également modifiée et contient le nouvel alias. De plus, l'adresse de messagerie électronique qui comprend l'alias précédent est gardée en tant qu'adresse de proxy du groupe.

- **Adresse de messagerie**: l’adresse de messagerie se compose de l’alias sur le côté gauche du symbole @, et d’un domaine sur le côté droit. Par défaut, la valeur **d’Alias** est utilisée pour la valeur d’alias, mais vous pouvez la modifier. Pour la valeur du domaine, cliquez sur le nom de domaine et sélectionnez le domaine accepté dans votre organisation.

- **Description**: cette description apparaît dans le carnet d’adresses et dans le volet Détails du EAC.

#### <a name="ownership"></a>Propriété

Utilisez cet onglet pour attribuer des propriétaires de groupe. Un propriétaire de groupe peut gérer l’appartenance au groupe. Par défaut, la personne qui crée un groupe en est le propriétaire. Tous les groupes doivent avoir au moins un propriétaire.

Pour ajouter des propriétaires, cliquez **sur Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire, puis cliquez sur **Ajouter ->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

Pour supprimer un propriétaire, sélectionnez-le, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

#### <a name="membership"></a>Appartenance

Utilisez cet onglet pour ajouter ou supprimer des membres du groupe. Les propriétaires de groupe n’ont pas besoin d’être membres du groupe.

Pour ajouter des membres, cliquez **sur Ajouter** une ![ icône ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter ->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

Pour supprimer un membre, sélectionnez-le, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

### <a name="use-the-eac-to-remove-groups"></a>Utiliser le EAC pour supprimer des groupes

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Dans la liste des groupes, sélectionnez le groupe de  distribution à supprimer, puis cliquez sur Supprimer ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

## <a name="use-powershell-to-manage-groups"></a>Utiliser PowerShell pour gérer les groupes

### <a name="use-standalone-eop-powershell-to-view-groups"></a>Utiliser EOP PowerShell autonome pour afficher des groupes

Pour renvoyer une liste récapitulatif de tous les groupes de distribution et groupes de sécurité à messagerie dans EOP PowerShell autonome, exécutez la commande suivante :

```powershell
Get-Recipient -RecipientType MailUniversalDistributionGroup,MailUniversalSecurityGroup -ResultSize unlimited
```

Pour renvoyer la liste des membres du groupe, remplacez-la par le nom, l’alias ou l’adresse e-mail du groupe, puis \<GroupIdentity\> exécutez la commande suivante :

```powershell
Get-DistributionGroupMember -Identity <GroupIdentity>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-Recipient](/powershell/module/exchange/get-recipient) et [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember).

### <a name="use-standalone-eop-powershell-to-create-groups"></a>Utiliser EOP PowerShell autonome pour créer des groupes

Pour créer des groupes de distribution ou des groupes de sécurité à messagerie dans EOP PowerShell autonome, utilisez la syntaxe suivante :

```PowerShell
New-EOPDistributionGroup -Name "<Unique Name>" -ManagedBy @("UserOrGroup1","UserOrGroup2",..."UserOrGroupN">) [-Alias <text>] [-DisplayName "<Descriptive Name>"] [-Members @("UserOrGroup1","UserOrGroup2",..."UserOrGroupN">)] [-Notes "<Optional Text>"] [-PrimarySmtpAddress <SmtpAddress>] [-Type <Distribution | Security>]
```

**Remarques** :

- Le _paramètre Name_ est obligatoire, a une longueur maximale de 64 caractères et doit être unique. Si vous n’utilisez pas le paramètre _DisplayName_, la valeur du paramètre _Name_ est utilisée pour le nom complet.

- Si vous n’utilisez pas le paramètre _Alias,_ le paramètre _Name_ est utilisé pour la valeur d’alias. Les espaces sont supprimés et les caractères non pris en place sont convertis en points d’interrogation (?).

- Si vous n’utilisez pas le _paramètre PrimarySmtpAddress,_ la valeur d’alias est utilisée dans le _paramètre PrimarySmtpAddress._

- Si vous n’utilisez pas le _paramètre Type,_ la valeur par défaut est Distribution.

Cet exemple crée un groupe de distribution nommé Administrateurs informatiques avec les propriétés spécifiées.

```PowerShell
New-EOPDistributionGroup -Name "IT Administrators" -Alias itadmin -Members @("michelle@contoso.com","laura@contoso.com","julia@contoso.com") -ManagedBy "chris@contoso.com"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-EOPDistributionGroup](/powershell/module/exchange/New-EOPDistributionGroup).

### <a name="use-standalone-eop-powershell-to-modify-groups"></a>Utiliser EOP PowerShell autonome pour modifier des groupes

Pour modifier des groupes dans EOP PowerShell autonome, utilisez la syntaxe suivante :

```powershell
Set-EOPDistributionGroup -Identity <GroupIdentity> [-Alias <Text>] [-DisplayName <Text>] [-ManagedBy @("User1","User2",..."UserN")] [-PrimarySmtpAddress <SmtpAddress>]

```powershell
Update-EOPDistributionGroupMember -Identity <GroupIdentity> -Members @("User1","User2",..."UserN")
```

Cet exemple utilise la modification de l’adresse SMTP principale (également appelée adresse de réponse) pour le groupe Seattle Employees sea.employees@contoso.com.

```PowerShell
Set-EOPDistributionGroup "Seattle Employees" -PrimarySmtpAddress "sea.employees@contoso.com"
```

Cet exemple remplace les membres actuels du groupe d’équipe de sécurité par Kitty Petersen et ContrôleSyrence.

```powershell
Update-EOPDistributionGroupMember -Identity "Security Team" -Members @("Kitty Petersen","Tyson Fawcett")
```

Cet exemple ajoute un nouvel utilisateur nommé « Named Agitcett » au groupe nommé « Security Team » tout en conservant les membres actuels du groupe.

```powershell
$CurrentMemberObjects = Get-DistributionGroupMember "Security Team"
$CurrentMemberNames = $CurrentMemberObjects | % {$_.name}
$CurrentMemberNames += "Tyson Fawcett"
Update-EOPDistributionGroupMember -Identity "Security Team" -Members $CurrentMemberNames
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-EOPDistributionGroup](https://docs.microsoft.com/powershell/module/exchange/set-eopdistributiongroup) et [Update-EOPDistributionGroupMember](https://docs.microsoft.com/powershell/module/exchange/update-eopdistributiongroupmember).

### <a name="remove-a-group-using-remote-windows-powershell"></a>Supprimer un groupe à l’aide d’Windows PowerShell

Cet exemple utilise la suppression du groupe de distribution nommé Administrateurs informatiques.

```PowerShell
Remove-EOPDistributionGroup -Identity "IT Administrators"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-EOPDistributionGroup](https://docs.microsoft.com/powershell/module/exchange/remove-eopdistributiongroup).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement créé, modifié ou supprimé un groupe de distribution ou un groupe de sécurité à messagerie, faites l’une des étapes suivantes :

- Dans le CAE, accédez à **Destinataires** \> **Groupes**. Vérifiez que le groupe est répertorié (ou non répertorié) et vérifiez la valeur **type de** groupe. Sélectionnez le groupe et affichez les informations  dans le volet d’informations, ou cliquez sur Modifier l’icône ![ Modifier pour afficher les ](../../media/ITPro-EAC-AddIcon.png) paramètres.

- Dans EOP PowerShell autonome, exécutez la commande suivante pour vérifier que le groupe est répertorié (ou n’est pas répertorié) :

  ```PowerShell
  Get-Recipient -RecipientType MailUniversalDistributionGroup,MailUniversalSecurityGroup -ResultSize unlimited
  ```

- Remplacez-le par le nom, l’alias ou l’adresse e-mail du groupe et exécutez la commande suivante \<GroupIdentity\> pour vérifier les paramètres :

  ```PowerShell
  Get-Recipient -Identity <GroupIdentity> | Format-List
  ```

- Pour afficher les membres du groupe, remplacez-les par le nom, l’alias ou l’adresse e-mail du groupe \<GroupIdentity\> et exécutez la commande suivante :

  ```PowerShell
  Get-DistributionGroupMember -Identity "<GroupIdentity>"
  ```