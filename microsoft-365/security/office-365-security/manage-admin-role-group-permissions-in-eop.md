---
title: Gérer des groupes de rôles dans EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
ms.assetid: 125834f4-1024-4325-ad5a-d2573cfb005e
description: Les administrateurs peuvent apprendre à attribuer ou supprimer des autorisations dans le Centre d’administration Exchange (EAC) dans Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b53023521f477b5e864424ec648ccf7e5b749d0c
ms.sourcegitcommit: a1846b1ee2e4fa397e39c1271c997fc4cf6d5619
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2021
ms.locfileid: "50166986"
---
# <a name="manage-role-groups-in-standalone-eop"></a>Gérer les groupes de rôles dans une application EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
-  [Exchange Online Protection autonome](https://go.microsoft.com/fwlink/?linkid=2148611)

Dans les organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, vous pouvez utiliser le Centre d’administration Exchange (CAE) pour ajouter des utilisateurs à des groupes de rôles. L’ajout d’utilisateurs à un groupe de rôles donne à l’utilisateur l’autorisation d’effectuer des tâches d’administration spécifiques. Vous pouvez également supprimer des utilisateurs de groupes de rôles.

Pour plus d’informations sur les rôles et les groupes de [rôles, voir Autorisations dans EOP autonome.](feature-permissions-in-eop.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre d’administration Exchange (CAE), consultez le Centre [d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour ouvrir EOP PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell.](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell)

- Des autorisations doivent vous être attribuées dans Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle  **gestion** des rôles, qui est attribué au groupe de rôles Gestion de l’organisation par défaut. Pour plus d’informations, voir Autorisations dans [EOP](feature-permissions-in-eop.md) autonome et utiliser le CAE pour modifier la liste des membres des [groupes de rôles.](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour plus d’informations sur les raccourcis clavier qui peuvent s’appliquer aux procédures de cet article, voir raccourcis clavier pour le Centre d’administration [Exchange dans Exchange Online.](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center)

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="use-the-eac-to-manage-role-groups"></a>Utiliser le EAC pour gérer des groupes de rôles

### <a name="use-the-eac-to-view-role-groups"></a>Utiliser le EAC pour afficher les groupes de rôles

1. Dans le EAC, allez aux **rôles d’administrateur des** \> **autorisations.** Tous les groupes de rôles de votre organisation sont répertoriés ici.

2. Sélectionnez un groupe de rôles. Le volet Détails affiche le **nom,** **la description,** les rôles **attribués** et géré **par** le groupe de rôles. Vous pouvez également voir ces informations en cliquant sur **Modifier** ![ l’icône ](../../media/ITPro-EAC-EditIcon.png) Modifier.

### <a name="use-the-eac-to-create-role-groups"></a>Utiliser le EAC pour créer des groupes de rôles

Lorsque vous créez un groupe de rôles, vous pouvez configurer tous les paramètres vous-même (lors de la création du groupe ou après). Vous pouvez également copier un groupe de rôles existant et le modifier.

1. Dans le EAC, allez à Rôles d’administrateur **des autorisations,** puis faites l’une des \> étapes suivantes :

   - **Créer manuellement un nouveau groupe de rôles**: cliquez **sur Ajouter** ![ une icône ](../../media/ITPro-EAC-AddIcon.png) .

   - **Copiez un groupe de rôles existant**: sélectionnez  le groupe de rôles à copier, puis cliquez sur Icône Copier ![ la ](../../media/ITPro-EAC-CopyIcon.png) copie.

2. Dans la **fenêtre Nouveau groupe de rôles** qui s’affiche, configurez les paramètres suivants :

    - **Nom**: entrez un nom unique pour le groupe de rôles.

    - **Description**: entrez une description facultative pour le groupe de rôles.

    - **Rôles**: cliquez **sur Icône** Ajouter ou Supprimer pour sélectionner ou modifier les rôles attribués au groupe ![ de ](../../media/ITPro-EAC-AddIcon.png)  ![ ](../../media/ITPro-EAC-RemoveIcon.gif) rôles.

    - **Membres :** cliquez sur **Icône** ![ Ajouter ou Supprimer pour modifier l’appartenance au groupe ](../../media/ITPro-EAC-AddIcon.png) de  ![ ](../../media/ITPro-EAC-RemoveIcon.gif) rôles.

3. Lorsque vous avez terminé, cliquez sur **Enregistrer** pour créer le groupe de rôles.

### <a name="use-the-eac-to-modify-role-groups"></a>Utiliser le EAC pour modifier des groupes de rôles

Dans le EAC, sélectionnez les rôles d’administrateur des **autorisations,** sélectionnez le groupe de rôles à modifier, puis cliquez sur Modifier \>   ![ l’icône ](../../media/ITPro-EAC-EditIcon.png) Modifier.

Les mêmes options sont disponibles lorsque vous modifiez des groupes de rôles que lorsque vous créez des groupes de rôles. Vous pouvez :

- Modifiez le nom et la description.

- Ajouter et supprimer des rôles de gestion (créer ou supprimer des attributions de rôles).

- Ajoutez et supprimez des membres.

**Remarque**: certains groupes de rôles (par exemple, Gestion de l’organisation) limitent les rôles que vous pouvez supprimer d’un groupe.

#### <a name="use-the-eac-modify-the-list-of-members-in-role-groups"></a>Utiliser le EAC pour modifier la liste des membres dans les groupes de rôles

1. Dans le EAC, sélectionnez les rôles d’administrateur des **autorisations,** sélectionnez le groupe de rôles à modifier, puis cliquez sur Modifier \>   ![ l’icône ](../../media/ITPro-EAC-EditIcon.png) Modifier.

2. Dans la page des propriétés du groupe de rôles qui s’ouvre, dans la section **Membres,** faites l’une des étapes suivantes :

   - Cliquez **sur Ajouter** une icône ![ ](../../media/ITPro-EAC-AddIcon.png) . Dans la page qui s’affiche, recherchez l’utilisateur que wou souhaite ajouter, puis cliquez sur **ajouter ->**. Sélectionnez des utilisateurs **et cliquez sur Ajouter ->** plusieurs fois si nécessaire. Lorsque vous avez terminé, cliquez sur **OK**.

   - Sélectionnez les utilisateurs à supprimer, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-RemoveIcon.gif) Supprimer.

3. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   > [!NOTE]
   > Après avoir ajouté ou supprimé des membres dans le groupe de rôles, il est possible que les utilisateurs doivent se déconnecter puis se reconnecter pour que les modifications au niveau de leurs droits d'administration soit appliquées.

### <a name="use-the-eac-to-remove-role-groups"></a>Utiliser le EAC pour supprimer des groupes de rôles

Vous ne pouvez pas supprimer des groupes de rôles intégrés, mais vous pouvez supprimer des groupes de rôles personnalisés que vous avez créés.

1. Dans le EAC, allez aux **rôles d’administrateur des** \> **autorisations.**

2. Sélectionnez le groupe de rôles à supprimer, puis cliquez sur **Supprimer** ![ l’icône ](../../media/ITPro-EAC-DeleteIcon.png) Supprimer.

3. Cliquez **sur Oui** dans la fenêtre de confirmation qui s’affiche.

## <a name="use-powershell-to-manage-role-groups"></a>Utiliser PowerShell pour gérer des groupes de rôles

### <a name="use-standalone-eop-powershell-to-view-role-groups"></a>Utiliser EOP PowerShell autonome pour afficher les groupes de rôles

Pour afficher un groupe de rôles, utilisez la syntaxe suivante :

```PowerShell
Get-RoleGroup [-Identity "<Role Group Name>"] [-Filter <Filter>]
```

Cet exemple renvoie une liste récapitulatif de tous les groupes de rôles.

```PowerShell
Get-RoleGroup
```

Cet exemple renvoie des informations détaillées sur le groupe de rôles nommé Administrateurs des destinataires.

```PowerShell
Get-RoleGroup -Identity "Recipient Administrators" | Format-List
```

Cet exemple renvoie tous les groupes de rôles dont l’utilisateur Julia est membre. Vous devez utiliser la valeur DistinguishedName (DN) pour Julia, que vous pouvez trouver en exécutant la commande : `Get-User -Identity Julia | Format-List DistinguishedName` .

```PowerShell
Get-RoleGroup -Filter "Members -eq 'CN=Julia,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange Hosted Organizations,DC=NAMPR001,DC=PROD,DC=OUTLOOK,DC=COM'"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/Get-RoleGroup).

### <a name="use-standalone-eop-powershell-to-create-role-groups"></a>Utiliser EOP PowerShell autonome pour créer des groupes de rôles

Lorsque vous créez un groupe de rôles, vous pouvez configurer tous les paramètres manuellement (lors de la création du groupe ou après). Vous pouvez également copier un groupe de rôles existant et le modifier.

- Pour créer manuellement un groupe de rôles, utilisez la syntaxe suivante :

  ```PowerShell
  New-RoleGroup -Name "Unique Name" -Description "Descriptive text" -Roles <"Role1","Role2"...>
  ```

  - Le _paramètre Roles_ spécifie les rôles de gestion à attribuer au groupe de rôles à l’aide de la syntaxe `"Role1","Role1",..."RoleN"` suivante. Vous pouvez voir les rôles disponibles à l’aide de l’applet de commande **Get-ManagementRole**.

  - Le _paramètre Members_ spécifie les membres du groupe de rôles à l’aide de la syntaxe suivante : `"Member1","Member2",..."MemberN"` . Vous pouvez spécifier des utilisateurs, des groupes de sécurité universels à extension messagerie ou d’autres groupes de rôles (entités de sécurité).

  Cet exemple crée un groupe de rôles nommé « Limited Recipient Management » avec les paramètres suivants :

  - Le rôle Destinataires de message est attribué au groupe de rôles.

  - Les utilisateurs Kim et Martin sont ajoutés en tant que membres.

  ```PowerShell
  New-RoleGroup -Name "Limited Recipient Management" -Roles "Mail Recipients" -Members "Kim","Martin"
  ```

- Pour copier un groupe de rôles existant, faites les étapes suivantes :

  1. Stockez le groupe de rôles que vous souhaitez copier dans une variable à l’aide de la commande suivante :

     ```PowerShell
     $RoleGroup = Get-RoleGroup "<Existing Role Group Name>"
     ```

  2. Créez le nouveau groupe de rôles à l’aide de la syntaxe suivante :

     ```PowerShell
     New-RoleGroup -Name "<Unique Name>" -Roles $RoleGroup.Roles [-Members <Members>]
     ```

     Le _paramètre Members_ spécifie les membres du groupe de rôles à l’aide de la syntaxe suivante : `"Member1","Member2",..."MemberN"` . Vous pouvez spécifier des utilisateurs, des groupes de sécurité universels à extension messagerie ou d’autres groupes de rôles (entités de sécurité).

     Cet exemple copie le groupe de rôles Gestion de l’organisation dans le nouveau groupe de rôles nommé « Limited Organization Management ». Les membres du groupe de rôles sont Isabelle, Carter et Lukas.

     ```PowerShell
     $RoleGroup = Get-RoleGroup "Organization Management"
     New-RoleGroup "Limited Organization Management" -Roles $RoleGroup.Roles -Members "Isabelle","Carter","Lukas"
     ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [New-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/New-RoleGroup).

### <a name="use-standalone-eop-powershell-modify-the-list-of-members-in-role-groups"></a>Utiliser EOP PowerShell autonome pour modifier la liste des membres dans les groupes de rôles

- Les cmdlets **Add-RoleGroupMember** et **Remove-RoleGroupMember** ajoutent ou suppriment des membres individuels un par un. La cmdlet **Update-RoleGroupMember** peut remplacer ou modifier la liste de membres existante.

- Les membres d’un groupe de rôles peuvent être des utilisateurs, des groupes de sécurité universels à messagerie ou d’autres groupes de rôles (principaux de sécurité).

Pour modifier les membres d’un groupe de rôles, utilisez la syntaxe suivante :

```PowerShell
Update-RoleGroupMember -Identity "<Role Group Name>" -Members <Members>
```

- Pour _remplacer_ la liste existante des membres par les valeurs que vous spécifiez, utilisez la syntaxe suivante `"Member1","Member2",..."MemberN"` :

- Pour _modifier de manière sélective_ la liste existante des membres, utilisez la syntaxe suivante : `@{Add="Member1","Member2"...; Remove="Member3","Member4"...}` .

Cet exemple remplace tous les membres actuels du groupe de rôles Help Desk par les utilisateurs spécifiés.

```PowerShell
Update-RoleGroupMember -Identity "Help Desk" -Members "Gabriela Laureano","Hyun-Ae Rim","Jacob Berger"
```

Cet exemple ajoute Legoro Akai et supprime Valeria Barrio de la liste des membres du groupe de rôles Help Desk.

```PowerShell
Update-RoleGroupMember -Identity "Help Desk" -Members @{Add="Daigoro Akai"; Remove="Valeria Barrios"}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Update-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/Update-RoleGroupMember).

### <a name="use-standalone-eop-powershell-to-remove-role-groups"></a>Utiliser EOP PowerShell autonome pour supprimer des groupes de rôles

Vous ne pouvez pas supprimer des groupes de rôles intégrés, mais vous pouvez supprimer des groupes de rôles personnalisés que vous avez créés.

Pour supprimer un groupe de rôles personnalisé, utilisez la syntaxe suivante :

```PowerShell
Remove-RoleGroup -Identity "<Role Group Name>" [-BypassSecurityGroupManagerCheck]
```

Cet exemple supprime le groupe de rôles Administrateurs de formation.

```PowerShell
Remove-RoleGroup -Identity "Training Administrators"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-RoleGroup](https://docs.microsoft.com/powershell/module/exchange/Remove-RoleGroup).

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement copié un groupe de rôles, faites l’une des étapes suivantes :

- Dans le EAC, allez à Rôles d’administrateur des **autorisations** et vérifiez que le groupe de rôles est répertorié \> (ou non répertorié). Sélectionnez le groupe de rôles et vérifiez les  paramètres dans le volet Détails ou cliquez sur Modifier l’icône ![ modifier pour vérifier les ](../../media/ITPro-EAC-EditIcon.png) paramètres.

- Dans Exchange Online PowerShell, remplacez par le nom du groupe de rôles et exécutez la commande suivante pour vérifier que le groupe de rôles existe (ou n’existe pas) et vérifier les \<Role Group Name\> paramètres :

    ```PowerShell
    Get-RoleGroup -Identity "<Role Group Name>" | Format-List
    ```
