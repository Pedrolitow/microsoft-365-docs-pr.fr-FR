---
title: Octroi de l’accès au Centre de conformité et sécurité aux utilisateurs
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.PermissionsHelp
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Les utilisateurs doivent disposer d’autorisations dans le centre de conformité Microsoft 365 Security & pour pouvoir gérer les fonctionnalités de sécurité ou de conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b51007221257b9adac46c31295e13b20b12342ab
ms.sourcegitcommit: 22dab0f7604cc057a062698005ff901d40771692
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46868920"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Octroi de l’accès au Centre de conformité et sécurité aux utilisateurs

Les utilisateurs doivent disposer d’autorisations dans le centre de conformité & de sécurité avant de pouvoir gérer les fonctionnalités de sécurité ou de conformité. En tant qu’administrateur général ou membre du groupe de rôles OrganizationManagement dans le centre de sécurité & conformité, vous pouvez accorder ces autorisations aux utilisateurs. Ceux-ci pourront uniquement gérer les fonctionnalités de sécurité ou de conformité auxquelles vous leur donnez accès.

Pour plus d’informations sur les différentes autorisations que vous pouvez accorder aux utilisateurs dans le centre de sécurité & conformité, consultez [la rubrique autorisations dans le centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être un administrateur général ou un membre du groupe de rôles OrganizationManagement dans le centre de sécurité & Compliance Center pour effectuer les étapes décrites dans cet article.

- Les groupes de rôles pour le centre de sécurité & conformité peuvent avoir des noms similaires aux groupes de rôles dans Exchange Online, mais ils ne sont pas identiques.

- Les appartenances aux groupes de rôles ne sont pas partagées entre Exchange Online et le centre de sécurité & conformité.

- Les autorisations des partenaires DAP (Delegated Access permission) avec administrer de la part de (administrateur) ne peuvent pas accéder au centre de conformité &.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Utiliser le centre de sécurité & conformité pour accorder à un autre utilisateur l’accès au centre de sécurité & conformité

1. Ouvrez le centre de sécurité & conformité à l’adresse <https://protection.office.com> , puis accédez à **autorisations**. Pour accéder directement à l’onglet **autorisations** , ouvrez <https://protection.office.com/permissions> .

2. Dans la liste des groupes de rôles, sélectionnez le groupe de rôles, puis cliquez sur **modifier** l' ![ icône modifier ](../../media/O365-MDM-CreatePolicy-EditIcon.gif) .

3. Dans la page des propriétés du groupe de rôles sous **membres**, cliquez sur **Ajouter**une ![ icône ](../../media/ITPro-EAC-AddIcon.gif) et sélectionnez le nom de l’utilisateur (ou des utilisateurs) que vous souhaitez ajouter.

4. Une fois que vous avez sélectionné tous les utilisateurs que vous souhaitez ajouter au groupe de rôles, cliquez sur **ajouter- \> ** puis sur **OK**.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Utiliser la sécurité & Centre de conformité PowerShell pour accorder à un autre utilisateur l’accès au centre de sécurité & conformité

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

2. Utilisez la syntaxe suivante :

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Add-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien autorisé l’accès au centre de sécurité & conformité, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à **autorisations** et sélectionnez le groupe de rôles. Dans la fenêtre mobile des détails qui s’ouvre, vérifiez les membres du groupe de rôles. 

- Dans sécurité & Centre de conformité PowerShell, remplacez \<RoleGroupName\> par le nom du groupe de rôles, puis exécutez la commande suivante :

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/Get-RoleGroupMember).
