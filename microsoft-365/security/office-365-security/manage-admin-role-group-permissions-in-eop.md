---
title: Gérer les groupes de rôles dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: 125834f4-1024-4325-ad5a-d2573cfb005e
description: Les administrateurs peuvent apprendre à attribuer ou supprimer des autorisations dans le centre d’administration Exchange dans Exchange Online Protection.
ms.openlocfilehash: 4a1353963e5e3eadc1a07f8b4aa3a765b06c86ec
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49659296"
---
# <a name="manage-role-groups-in-standalone-eop"></a>Gérer les groupes de rôles dans une application EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez utiliser le centre d’administration Exchange pour ajouter des utilisateurs à des groupes de rôles. L’ajout d’un utilisateur à un groupe de rôles donne à l’utilisateur des autorisations pour effectuer des tâches d’administration spécifiques. Vous pouvez également supprimer des utilisateurs des groupes de rôles.

Pour plus d’informations sur les rôles et les groupes de rôles, voir [Permissions in standalone EOP](feature-permissions-in-eop.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in standalone EOP](exchange-admin-center-in-exchange-online-protection-eop.md).

- Pour ouvrir la version PowerShell d’EOP autonome, consultez la rubrique [Connect to Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour pouvoir effectuer les procédures décrites dans cet article, vous devez disposer d’autorisations dans Exchange Online Protection. Plus précisément, vous avez besoin du rôle de **gestion des rôles** , qui est affecté par défaut au groupe de rôles gestion de l' **organisation** . Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures décrites dans cet article, reportez-vous à [la rubrique raccourcis clavier du centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-eac-to-manage-role-groups"></a>Utiliser le centre d’administration Exchange pour gérer les groupes de rôles

### <a name="use-the-eac-to-view-role-groups"></a>Utiliser le centre d’administration Exchange pour afficher les groupes de rôles

1. Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> . Tous les groupes de rôles de votre organisation sont répertoriés ici.

2. Sélectionnez un groupe de rôles. Le volet d’informations affiche le **nom**, la **Description**, les **rôles attribués** et **gérés par** le groupe de rôles. Vous pouvez également afficher ces informations en cliquant sur **modifier** l' ![ icône modifier ](../../media/ITPro-EAC-EditIcon.png) .

### <a name="use-the-eac-to-create-role-groups"></a>Utiliser le centre d’administration Exchange pour créer des groupes de rôles

Lorsque vous créez un nouveau groupe de rôles, vous pouvez configurer tous les paramètres vous-même (lors de la création du groupe ou après). Sinon, vous pouvez copier un groupe de rôles existant et le modifier.

1. Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> , puis effectuez l’une des opérations suivantes :

   - **Créez manuellement un nouveau groupe de rôles**: cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) .

   - **Copier un groupe de rôles existant**: sélectionnez le groupe de rôles que vous souhaitez copier, puis cliquez sur icône **copier** ![ ](../../media/ITPro-EAC-CopyIcon.png) .

2. Dans la fenêtre **nouveau groupe de rôles** qui s’affiche, configurez les paramètres suivants :

    - **Nom**: entrez un nom unique pour le groupe de rôles.

    - **Description**: entrez une description facultative pour le groupe de rôles.

    - **Rôles**: cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) ou **supprimer** une ![ icône ](../../media/ITPro-EAC-RemoveIcon.gif) pour sélectionner ou modifier les rôles affectés au groupe de rôles.

    - **Membres**: cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) ou **supprimer** ![ l’icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) pour modifier l’appartenance au groupe de rôles.

3. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer le groupe de rôles.

### <a name="use-the-eac-to-modify-role-groups"></a>Utiliser le centre d’administration Exchange pour modifier des groupes de rôles

Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> , sélectionnez le groupe de rôles que vous souhaitez modifier, puis cliquez sur **modifier** l' ![ icône d’édition ](../../media/ITPro-EAC-EditIcon.png) .

Les mêmes options sont disponibles lorsque vous modifiez des groupes de rôles, comme lorsque vous créez des groupes de rôles. Vous pouvez :

- Modifiez le nom et la description.

- Ajouter et supprimer des rôles de gestion (créer ou supprimer des attributions de rôles).

- Ajouter et supprimer des membres.

**Remarque**: certains groupes de rôles (par exemple, gestion de l’organisation) restreignent les rôles que vous pouvez supprimer du groupe.

#### <a name="use-the-eac-modify-the-list-of-members-in-role-groups"></a>Utiliser le centre d’administration Exchange modifier la liste des membres dans les groupes de rôles

1. Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> , sélectionnez le groupe de rôles que vous souhaitez modifier, puis cliquez sur **modifier** l' ![ icône d’édition ](../../media/ITPro-EAC-EditIcon.png) .

2. Dans la page des propriétés du groupe de rôles qui s’ouvre, dans la section **membres** , effectuez l’une des opérations suivantes :

   - Cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Dans la page qui s’affiche, recherchez l’utilisateur que Wou souhaite ajouter, puis cliquez sur **Ajouter->**. Sélectionnez utilisateurs, puis cliquez sur **ajouter >** plusieurs fois autant de fois que nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

   - Sélectionnez les utilisateurs à supprimer, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-RemoveIcon.gif) .

3. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   > [!NOTE]
   > Après avoir ajouté ou supprimé des membres dans le groupe de rôles, il est possible que les utilisateurs doivent se déconnecter puis se reconnecter pour que les modifications au niveau de leurs droits d'administration soit appliquées.

### <a name="use-the-eac-to-remove-role-groups"></a>Utiliser le centre d’administration Exchange pour supprimer des groupes de rôles

Vous ne pouvez pas supprimer les groupes de rôles intégrés, mais vous pouvez supprimer les groupes de rôles personnalisés que vous avez créés.

1. Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> .

2. Sélectionnez le groupe de rôles que vous souhaitez supprimer, puis cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/ITPro-EAC-DeleteIcon.png) .

3. Cliquez sur **Oui** dans la fenêtre de confirmation qui s’affiche.

## <a name="use-powershell-to-manage-role-groups"></a>Utiliser PowerShell pour gérer les groupes de rôles

### <a name="use-standalone-eop-powershell-to-view-role-groups"></a>Utilisation d’EOP PowerShell autonome pour afficher des groupes de rôles

Pour afficher un groupe de rôles, utilisez la syntaxe suivante :

```PowerShell
Get-RoleGroup [-Identity "<Role Group Name>"] [-Filter <Filter>]
```

Cet exemple renvoie la liste récapitulative de tous les groupes de rôles.

```PowerShell
Get-RoleGroup
```

Cet exemple renvoie des informations détaillées sur le groupe de rôles administrateurs des destinataires.

```PowerShell
Get-RoleGroup -Identity "Recipient Administrators" | Format-List
```

Cet exemple renvoie tous les groupes de rôles pour lesquels l’utilisateur Julia est membre. Vous devez utiliser la valeur DistinguishedName (DN) pour Julia, que vous pouvez trouver en exécutant la commande : `Get-User -Identity Julia | Format-List DistinguishedName` .

```PowerShell
Get-RoleGroup -Filter "Members -eq 'CN=Julia,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange Hosted Organizations,DC=NAMPR001,DC=PROD,DC=OUTLOOK,DC=COM'"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/Get-RoleGroup).

### <a name="use-standalone-eop-powershell-to-create-role-groups"></a>Utilisation d’EOP PowerShell autonome pour créer des groupes de rôles

Lorsque vous créez un nouveau groupe de rôles, vous pouvez configurer tous les paramètres manuellement (lors de la création du groupe ou après). Sinon, vous pouvez copier un groupe de rôles existant et le modifier.

- Pour créer manuellement un nouveau groupe de rôles, utilisez la syntaxe suivante :

  ```PowerShell
  New-RoleGroup -Name "Unique Name" -Description "Descriptive text" -Roles <"Role1","Role2"...>
  ```

  - Le paramètre _roles_ spécifie les rôles de gestion à affecter au groupe de rôles à l’aide de la syntaxe suivante `"Role1","Role1",..."RoleN"` . Vous pouvez voir les rôles disponibles à l’aide de l’applet de commande **Get-ManagementRole**.

  - Le paramètre _members_ spécifie les membres du groupe de rôles à l’aide de la syntaxe suivante : `"Member1","Member2",..."MemberN"` . Vous pouvez spécifier des utilisateurs, des groupes de sécurité universels à extension messagerie ou d’autres groupes de rôles (entités de sécurité).

  Cet exemple crée un groupe de rôles nommé « gestion limitée des destinataires » avec les paramètres suivants :

  - Le rôle Destinataires de message est attribué au groupe de rôles.

  - Les utilisateurs Kim et Martin sont ajoutés en tant que membres.

  ```PowerShell
  New-RoleGroup -Name "Limited Recipient Management" -Roles "Mail Recipients" -Members "Kim","Martin"
  ```

- Pour copier un groupe de rôles existant, procédez comme suit :

  1. Stockez le groupe de rôles que vous souhaitez copier dans une variable à l’aide de la commande suivante :

     ```PowerShell
     $RoleGroup = Get-RoleGroup "<Existing Role Group Name>"
     ```

  2. Créez le nouveau groupe de rôles à l’aide de la syntaxe suivante :

     ```PowerShell
     New-RoleGroup -Name "<Unique Name>" -Roles $RoleGroup.Roles [-Members <Members>]
     ```

     Le paramètre _members_ spécifie les membres du groupe de rôles à l’aide de la syntaxe suivante : `"Member1","Member2",..."MemberN"` . Vous pouvez spécifier des utilisateurs, des groupes de sécurité universels à extension messagerie ou d’autres groupes de rôles (entités de sécurité).

     Cet exemple copie le groupe de rôles gestion de l’organisation dans le nouveau groupe de rôles appelé « gestion limitée de l’organisation ». Les membres du groupe de rôles sont Isabelle, Carter et Lukas.

     ```PowerShell
     $RoleGroup = Get-RoleGroup "Organization Management"
     New-RoleGroup "Limited Organization Management" -Roles $RoleGroup.Roles -Members "Isabelle","Carter","Lukas"
     ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [New-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/New-RoleGroup).

### <a name="use-standalone-eop-powershell-modify-the-list-of-members-in-role-groups"></a>Utiliser l’PowerShell EOP autonome modifier la liste des membres dans les groupes de rôles

- Les applets **de commande Add-RoleGroupMember** et **Remove-RoleGroupMember** ajoutent ou suppriment des membres individuels un par un. L’applet de commande **Update-RoleGroupMember** peut remplacer ou modifier la liste de membres existante.

- Les membres d’un groupe de rôles peuvent être des utilisateurs, des groupes de sécurité universels à extension messagerie (USG) ou d’autres groupes de rôles (principaux de sécurité).

Pour modifier les membres d’un groupe de rôles, utilisez la syntaxe suivante :

```PowerShell
Update-RoleGroupMember -Identity "<Role Group Name>" -Members <Members>
```

- Pour _remplacer_ la liste de membres existante par les valeurs que vous spécifiez, utilisez la syntaxe suivante : `"Member1","Member2",..."MemberN"` .

- Pour _modifier de manière sélective_ la liste de membres existante, utilisez la syntaxe suivante : `@{Add="Member1","Member2"...; Remove="Member3","Member4"...}` .

Cet exemple remplace tous les membres actuels du groupe de rôles support technique par les utilisateurs spécifiés.

```PowerShell
Update-RoleGroupMember -Identity "Help Desk" -Members "Gabriela Laureano","Hyun-Ae Rim","Jacob Berger"
```

Cet exemple montre comment ajouter Daigoro Akai et supprimer Valeria Barrio de la liste des membres du groupe de rôles support technique.

```PowerShell
Update-RoleGroupMember -Identity "Help Desk" -Members @{Add="Daigoro Akai"; Remove="Valeria Barrios"}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Update-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/Update-RoleGroupMember).

### <a name="use-standalone-eop-powershell-to-remove-role-groups"></a>Utilisation d’EOP PowerShell autonome pour supprimer des groupes de rôles

Vous ne pouvez pas supprimer les groupes de rôles intégrés, mais vous pouvez supprimer les groupes de rôles personnalisés que vous avez créés.

Pour supprimer un groupe de rôles personnalisé, utilisez la syntaxe suivante :

```PowerShell
Remove-RoleGroup -Identity "<Role Group Name>" [-BypassSecurityGroupManagerCheck]
```

Cet exemple supprime le groupe de rôles Administrateurs de formation.

```PowerShell
Remove-RoleGroup -Identity "Training Administrators"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/Remove-RoleGroup).

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien copié un groupe de rôles, effectuez l’une des opérations suivantes :

- Dans le centre d’administration Exchange, accédez à rôles d’administrateur des **autorisations** \> et vérifiez que le groupe de rôles est affiché (ou non). Sélectionnez le groupe de rôles et vérifiez les paramètres dans le volet d’informations ou cliquez sur **modifier** ![ l’icône modifier ](../../media/ITPro-EAC-EditIcon.png) pour vérifier les paramètres.

- Dans Exchange Online PowerShell, remplacez \<Role Group Name\> par le nom du groupe de rôles et exécutez la commande suivante pour vérifier que le groupe de rôles existe (ou n’existe pas) et vérifiez les paramètres :

    ```PowerShell
    Get-RoleGroup -Identity "<Role Group Name>" | Format-List
    ```
