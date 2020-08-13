---
title: Gestion des groupes dans Exchange Online Protection (EOP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 212e68ac-6330-47e9-a169-6cf5e2f21e13
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs dans les organisations Exchange Online Protection (EOP) autonomes peuvent apprendre à créer, modifier et supprimer des groupes de distribution et des groupes de sécurité à extension messagerie dans le centre d’administration Exchange et dans Exchange Online Protection (EOP) autonome.
ms.openlocfilehash: 813735d4024c3b8424a6bbac51ebef7b4c53e590
ms.sourcegitcommit: 6a1a8aa024fd685d04da97bfcbc8eadacc488534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46653652"
---
# <a name="manage-groups-in-eop"></a>Gestion des groupes dans Exchange Online Protection (EOP)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez créer, modifier et supprimer les types de groupes suivants :

- **Groupes de distribution**: collection d’utilisateurs de messagerie ou d’autres groupes de distribution. Par exemple, les équipes ou autres groupes ad hoc qui doivent recevoir ou envoyer des courriers électroniques dans un domaine d’intérêt commun. Les groupes de distribution sont exclusivement destinés à la distribution de messages électroniques et ne sont pas des principaux de sécurité (ils ne peuvent pas avoir d’autorisations associées).

- **Groupes de sécurité à extension messagerie**: collection d’utilisateurs de messagerie et d’autres groupes de sécurité qui ont besoin d’autorisations d’accès pour les rôles d’administrateur. Par exemple, vous pouvez accorder à un groupe spécifique d’utilisateurs des autorisations d’administrateur afin qu’ils puissent configurer les paramètres de blocage du courrier indésirable et des programmes malveillants.

    > [!NOTE]
    >
    > - Par défaut, les nouveaux groupes de sécurité à extension messagerie refusent les messages provenant d’expéditeurs externes (non authentifiés).
    >
    > - N’ajoutez pas de groupes de distribution aux groupes de sécurité à extension messagerie.

Vous pouvez gérer les groupes dans le centre d’administration Exchange (Centre d’administration Exchange) et dans la version PowerShell d’EOP autonome.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Lorsque vous gérez des groupes dans une version autonome d’EOP PowerShell, il se peut que vous rencontriez une limitation. Les procédures PowerShell de cette rubrique utilisent une méthode de traitement par lots qui entraîne un délai de propagation de quelques minutes avant que les résultats des commandes soient visibles.

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Plus précisément, vous avez besoin du rôle groupes de distribution, qui est affecté aux groupes de rôles OrganizationManagement (administrateurs globaux) et RecipientManagement par défaut. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures de cette rubrique, voir [raccourcis clavier pour le centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-exchange-admin-center-to-manage-distribution-groups"></a>Utiliser le centre d’administration Exchange pour gérer les groupes de distribution

### <a name="use-the-eac-to-create-groups"></a>Utiliser le centre d’administration Exchange pour créer des groupes

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Cliquez sur **nouvelle** ![ icône ](../../media/ITPro-EAC-AddIcon.png) , puis sélectionnez l’une des options suivantes :

   - **Groupe de distribution**

   - **Groupe de sécurité à extension messagerie**

3. Dans la page nouveau groupe qui s’ouvre, configurez les paramètres suivants. Les paramètres marqués par un <sup>\*</sup> sont obligatoires.

   - <sup>\*</sup>**Nom d’affichage**: ce nom s’affiche dans le carnet d’adresses de votre organisation, sur la ligne à : quand un message électronique est envoyé à ce groupe, et dans la liste **groupes** du centre d’administration Exchange. Le nom complet est obligatoire, doit être unique et doit être convivial afin que les utilisateurs puissent reconnaître ce qu’il est.

   - <sup>\*</sup>**Alias**: ce champ permet de taper le nom de l’alias du groupe. L’alias ne peut pas dépasser 64 caractères et doit être unique. Lorsqu’un utilisateur tape l’alias dans la ligne à d’un message électronique, il est résolu en nom complet du groupe.

   - <sup>\*</sup>**Adresse de messagerie**: l’adresse de messagerie se compose de l’alias sur le côté gauche du symbole arobase (@) et d’un domaine sur le côté droit. Par défaut, la valeur d' **alias** est utilisée pour la valeur d’alias, mais vous pouvez la modifier. Pour la valeur Domain (domaine), cliquez sur le menu déroulant et sélectionnez le domaine accepté dans votre organisation.

   - **Description**: cette description apparaît dans le carnet d’adresses et dans le volet d’informations du centre d’administration Exchange.

   - <sup>\*</sup>**Propriétaires**: un propriétaire de groupe peut gérer l’appartenance à un groupe. Par défaut, la personne qui crée un groupe en est le propriétaire. Tous les groupes doivent avoir au moins un propriétaire.

     Pour ajouter des propriétaires, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

     Pour supprimer un propriétaire, sélectionnez-le, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

   - **Membres**: ajouter et supprimer des membres du groupe.

     Pour ajouter des membres, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

     Pour supprimer un membre, sélectionnez-le, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

4. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer le groupe de distribution.

### <a name="use-the-eac-to-modify-distribution-groups"></a>Utiliser le centre d’administration Exchange pour modifier des groupes de distribution

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Dans la liste des groupes, sélectionnez le groupe de distribution ou le groupe de sécurité à extension messagerie à modifier, puis cliquez sur **modifier** l' ![ icône modifier ](../../media/ITPro-EAC-AddIcon.png) .

3. Dans la page des propriétés du groupe de distribution qui s’ouvre, cliquez sur l’un des onglets suivants pour afficher ou modifier les propriétés.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="general"></a>Général

Utilisez cet onglet pour afficher ou modifier les informations de base relatives au groupe.

- **Nom d’affichage**: ce nom s’affiche dans le carnet d’adresses, sur la ligne à lorsque le courrier électronique est envoyé à ce groupe, et dans la **Liste groupes**. Le nom d'affichage est obligatoire et doit être convivial afin que les personnes identifient facilement de quoi il s'agit. Il doit également être unique dans votre domaine.

  Si vous avez implémenté une stratégie de noms de groupes, le nom d'affichage doit se conformer au format de nom défini par la stratégie.

- **Alias**: il s’agit de la partie de l’adresse de messagerie qui apparaît à gauche du symbole arobase (@). Si vous modifiez l'alias, l'adresse SMTP principale du groupe est également modifiée et contient le nouvel alias. De plus, l'adresse de messagerie électronique qui comprend l'alias précédent est gardée en tant qu'adresse de proxy du groupe.

- **Adresse de messagerie**: l’adresse de messagerie se compose de l’alias sur le côté gauche du symbole arobase (@) et d’un domaine sur le côté droit. Par défaut, la valeur d' **alias** est utilisée pour la valeur d’alias, mais vous pouvez la modifier. Pour la valeur Domain (domaine), cliquez sur le menu déroulant et sélectionnez le domaine accepté dans votre organisation.

- **Description**: cette description apparaît dans le carnet d’adresses et dans le volet d’informations du centre d’administration Exchange.

#### <a name="ownership"></a>Propriété

Utilisez cet onglet pour affecter des propriétaires de groupe. Un propriétaire de groupe peut gérer l’appartenance à un groupe. Par défaut, la personne qui crée un groupe en est le propriétaire. Tous les groupes doivent avoir au moins un propriétaire.

Pour ajouter des propriétaires, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire, puis cliquez sur **Ajouter->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

Pour supprimer un propriétaire, sélectionnez-le, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

#### <a name="membership"></a>Appartenance

Utilisez cet onglet pour ajouter ou supprimer des membres du groupe. Les propriétaires de groupe n’ont pas besoin d’être membres du groupe.

Pour ajouter des membres, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Dans la boîte de dialogue qui s’affiche, recherchez et sélectionnez un destinataire ou un groupe, puis cliquez sur **Ajouter->**. Répétez cette étape autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

Pour supprimer un membre, sélectionnez-le, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

### <a name="use-the-eac-to-remove-groups"></a>Utiliser le centre d’administration Exchange pour supprimer des groupes

1. Dans le CAE, accédez à **Destinataires** \> **Groupes**.

2. Dans la liste des groupes, sélectionnez le groupe de distribution que vous souhaitez supprimer, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

## <a name="use-powershell-to-manage-groups"></a>Utiliser PowerShell pour gérer les groupes

### <a name="use-standalone-eop-powershell-to-view-groups"></a>Utilisation d’EOP PowerShell autonome pour afficher des groupes

Pour renvoyer une liste récapitulative de tous les groupes de distribution et des groupes de sécurité à extension messagerie dans la version autonome d’EOP PowerShell, exécutez la commande suivante :

```powershell
Get-Recipient -RecipientType MailUniversalDistributionGroup,MailUniversalSecurityGroup -ResultSize unlimited
```

Pour renvoyer la liste des membres du groupe, remplacez \<GroupIdentity\> par le nom, l’alias ou l’adresse de messagerie du groupe, puis exécutez la commande suivante :

```powershell
Get-DistributionGroupMember -Identity <GroupIdentity>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-Recipient](https://docs.microsoft.com/powershell/module/exchange/get-recipient) et [Get-DistributionGroupMember](https://docs.microsoft.com/powershell/module/exchange/get-distributiongroupmember).

### <a name="use-standalone-eop-powershell-to-create-groups"></a>Utilisation d’EOP PowerShell autonome pour créer des groupes

Pour créer des groupes de distribution ou des groupes de sécurité à extension messagerie dans une version autonome d’EOP PowerShell, utilisez la syntaxe suivante :

```PowerShell
New-EOPDistributionGroup -Name "<Unique Name>" -ManagedBy @("UserOrGroup1","UserOrGroup2",..."UserOrGroupN">) [-Alias <text>] [-DisplayName "<Descriptive Name>"] [-Members @("UserOrGroup1","UserOrGroup2",..."UserOrGroupN">)] [-Notes "<Optional Text>"] [-PrimarySmtpAddress <SmtpAddress>] [-Type <Distribution | Security>]
```

**Remarques** :

- Le paramètre _Name_ est obligatoire, sa longueur maximale est de 64 caractères et doit être unique. Si vous n’utilisez pas le paramètre _DisplayName_, la valeur du paramètre _Name_ est utilisée pour le nom complet.

- Si vous n’utilisez pas le paramètre _alias_ , le paramètre _Name_ est utilisé pour la valeur alias. Les espaces sont supprimés et les caractères non pris en charge sont convertis en points d’interrogation ( ?).

- Si vous n’utilisez pas le paramètre _PrimarySmtpAddress_ , la valeur d’alias est utilisée dans le paramètre _PrimarySmtpAddress_ .

- Si vous n’utilisez pas le paramètre _type_ , la valeur par défaut est distribution.

Cet exemple crée un groupe de distribution nommé administrateurs informatiques avec les propriétés spécifiées.

```PowerShell
New-EOPDistributionGroup -Name "IT Administrators" -Alias itadmin -Members @("michelle@contoso.com","laura@contoso.com","julia@contoso.com") -ManagedBy "chris@contoso.com"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-EOPDistributionGroup](https://docs.microsoft.com/powershell/module/exchange/New-EOPDistributionGroup).

### <a name="use-standalone-eop-powershell-to-modify-groups"></a>Utilisation d’EOP PowerShell autonome pour modifier des groupes

Pour modifier des groupes dans une version autonome d’EOP PowerShell, utilisez la syntaxe suivante :

```powershell
Set-EOPDistributionGroup -Identity <GroupIdentity> [-Alias <Text>] [-DisplayName <Text>] [-ManagedBy @("User1","User2",..."UserN")] [-PrimarySmtpAddress <SmtpAddress>]

```powershell
Update-EOPDistributionGroupMember -Identity <GroupIdentity> -Members @("User1","User2",..."UserN")
```

Cet exemple utilise la modification de l’adresse SMTP principale (également appelée adresse de réponse) pour le groupe Seattle Employees vers sea.employees@contoso.com.

```PowerShell
Set-EOPDistributionGroup "Seattle Employees" -PrimarysmptAddress "sea.employees@contoso.com"
```

Cet exemple remplace les membres actuels du groupe d’équipe de sécurité par Kitty Petersen et Tyson Fawcett.

```powershell
Update-EOPDistributionGroupMember -Identity "Security Team" -Members @("Kitty Petersen","Tyson Fawcett")
```

Cet exemple ajoute un nouvel utilisateur appelé Tyson Fawcett au groupe nommé « équipe de sécurité » tout en conservant les membres actuels du groupe.

```powershell
$CurrentMemberObjects = Get-DistributionGroupMember "Security Team"
$CurrentMemberNames = $CurrentMemberObjects | % {$_.name}
$CurrentMemberNames += "Tyson Fawcett"
Update-EOPDistributionGroupMember -Identity "Security Team" -Members $CurrentMemberNames
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-EOPDistributionGroup](https://docs.microsoft.com/powershell/module/exchange/set-eopdistributiongroup) et [Update-EOPDistributionGroupMember](https://docs.microsoft.com/powershell/module/exchange/update-eopdistributiongroupmember).

### <a name="remove-a-group-using-remote-windows-powershell"></a>Supprimer un groupe à l’aide de Windows PowerShell à distance

Cet exemple utilise le groupe de distribution nommé administrateurs informatiques.

```PowerShell
Remove-EOPDistributionGroup -Identity "IT Administrators"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-EOPDistributionGroup](https://docs.microsoft.com/powershell/module/exchange/remove-eopdistributiongroup).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien créé, modifié ou supprimé un groupe de distribution ou un groupe de sécurité à extension messagerie, effectuez l’une des opérations suivantes :

- Dans le CAE, accédez à **Destinataires** \> **Groupes**. Vérifiez que le groupe est affiché (ou non), puis vérifiez la valeur du **type de groupe** . Sélectionnez le groupe et affichez les informations dans le volet d’informations, ou cliquez sur **modifier** ![ l’icône modifier ](../../media/ITPro-EAC-AddIcon.png) pour afficher les paramètres.

- Dans la version autonome d’EOP PowerShell, exécutez la commande suivante pour vérifier que le groupe est affiché (ou non) :

  ```PowerShell
  Get-Recipient -RecipientType MailUniversalDistributionGroup,MailUniversalSecurityGroup -ResultSize unlimited
  ```

- Remplacez \<GroupIdentity\> par le nom, l’alias ou l’adresse de messagerie du groupe, puis exécutez la commande suivante pour vérifier les paramètres :

  ```PowerShell
  Get-Recipient -Identity <GroupIdentity> | Format-List
  ```

- Pour afficher les membres du groupe, remplacez \<GroupIdentity\> par le nom, l’alias ou l’adresse de messagerie du groupe, puis exécutez la commande suivante :

  ```PowerShell
  Get-DistributionGroupMember -Identity "<GroupIdentity>"
  ```
