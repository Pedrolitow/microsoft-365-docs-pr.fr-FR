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
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Les utilisateurs doivent disposer d’autorisations dans le Centre de sécurité & conformité Microsoft 365 avant de pouvoir gérer ses fonctionnalités de sécurité ou de conformité.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 922606623ef8834f7e39d48ebc758d9c6e6c414e
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67596486"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Octroi de l’accès au Centre de conformité et sécurité aux utilisateurs

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les utilisateurs doivent se voir attribuer des autorisations dans le Centre de sécurité & conformité avant de pouvoir gérer l’une de ses fonctionnalités de sécurité ou de conformité. En tant qu’administrateur général ou membre du groupe de rôles OrganizationManagement dans le Centre de sécurité & conformité, vous pouvez accorder ces autorisations aux utilisateurs. Ceux-ci pourront uniquement gérer les fonctionnalités de sécurité ou de conformité auxquelles vous leur donnez accès.

Pour plus d’informations sur les différentes autorisations que vous pouvez accorder aux utilisateurs dans le Centre de sécurité & conformité, consultez [Autorisations dans le Centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être administrateur général ou membre du groupe de rôles OrganizationManagement dans le Centre de sécurité & conformité pour suivre les étapes décrites dans cet article.

- Les groupes de rôles du Centre de sécurité & conformité peuvent avoir des noms similaires aux groupes de rôles dans Exchange Online, mais ils ne sont pas les mêmes.

- Les appartenances aux groupes de rôles ne sont pas partagées entre Exchange Online et le Centre de sécurité & conformité.

- Les partenaires d’autorisation d’accès délégué (DAP) disposant d’autorisations d’administration au nom de (AOBO) ne peuvent pas accéder au Centre de sécurité & conformité.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Utilisez le Centre de sécurité & conformité pour permettre à un autre utilisateur d’accéder au Centre de sécurité & conformité

1. Ouvrez le Centre de sécurité & conformité, <https://protection.office.com> puis accédez à **Autorisations**. Pour accéder directement à l’onglet **Autorisations** , ouvrez <https://protection.office.com/permissions>.

2. Dans la liste des groupes de rôles, choisissez le groupe de rôles, puis cliquez sur **l’icône Modifier**![.](../../media/O365-MDM-CreatePolicy-EditIcon.gif)

3. Dans la page des propriétés du groupe de rôles sous **Membres**, cliquez sur **Ajouter**![une icône.](../../media/ITPro-EAC-AddIcon.gif) et sélectionnez le nom de l’utilisateur (ou des utilisateurs) que vous souhaitez ajouter.

4. Une fois que vous avez sélectionné tous les utilisateurs que vous souhaitez ajouter au groupe de rôles, cliquez sur **ajouter,\>** puis **SUR OK**.

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-security--compliance-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Utiliser Security & Compliance PowerShell pour permettre à un autre utilisateur d’accéder au Centre de sécurité & conformité

1. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Utilisez la syntaxe suivante :

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Pour obtenir des problèmes de syntaxe et de paramètre détaillés, consultez [Add-RoleGroupMember](/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez correctement accordé l’accès au Centre de sécurité & conformité, effectuez l’une des étapes suivantes :

- Dans le Centre de sécurité & conformité, accédez à Autorisations et sélectionnez le groupe de **rôles** . Dans le menu volant des détails qui s’ouvre, vérifiez les membres du groupe de rôles.

- Dans Security & Compliance PowerShell, remplacez \<RoleGroupName\> par le nom du groupe de rôles et exécutez la commande suivante :

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-RoleGroupMember](/powershell/module/exchange/Get-RoleGroupMember).
