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
localization_priority: Normal
ms.collection: Strat_O365_IP
search.appverid:
- MOE150
- MET150
ms.assetid: 2cfce2c8-20c5-47f9-afc4-24b059c1bd76
description: Des autorisations doivent être attribuées aux utilisateurs dans le Centre de conformité et sécurité Microsoft 365 & avant de pouvoir gérer l’une de ses fonctionnalités de sécurité ou de conformité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6ab02773a19e1b5881858104097b0b03e4385b40
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50907227"
---
# <a name="give-users-access-to-the-security--compliance-center"></a>Octroi de l’accès au Centre de conformité et sécurité aux utilisateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Des autorisations doivent être attribuées aux utilisateurs dans le Centre de sécurité & conformité avant de pouvoir gérer l’une de ses fonctionnalités de sécurité ou de conformité. En tant qu’administrateur global ou membre du groupe de rôles OrganizationManagement dans le Centre de sécurité & conformité, vous pouvez accorder ces autorisations aux utilisateurs. Ceux-ci pourront uniquement gérer les fonctionnalités de sécurité ou de conformité auxquelles vous leur donnez accès.

Pour plus d’informations sur les différentes autorisations que vous pouvez accorder aux utilisateurs dans le Centre de sécurité & conformité, consultez [Autorisations](permissions-in-the-security-and-compliance-center.md)dans le Centre de sécurité & conformité.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous devez être un administrateur global ou un membre du groupe de rôles OrganizationManagement dans le Centre de sécurité & conformité, pour effectuer les étapes de cet article.

- Les groupes de rôles pour le Centre de sécurité & conformité peuvent avoir des noms similaires aux groupes de rôles dans Exchange Online, mais ils ne sont pas identiques.

- Les appartenances aux groupes de rôles ne sont pas partagées entre Exchange Online et le Centre de sécurité & conformité.

- Les partenaires avec autorisation d’accès délégué avec des autorisations Administrer de la part de (AOBO) ne peuvent pas accéder au Centre de sécurité & conformité.

## <a name="use-the-security--compliance-center-to-give-another-user-access-to-the-security--compliance-center"></a>Utiliser le Centre de sécurité & conformité pour accorder à un autre utilisateur l’accès au Centre de sécurité & conformité

1. Ouvrez le Centre de sécurité & conformité <https://protection.office.com> à l’accueil, puis allez à **Autorisations.** Pour aller directement à **l’onglet Autorisations,** ouvrez <https://protection.office.com/permissions> .

2. Dans la liste des groupes de rôles,  choisissez le groupe de rôles, puis cliquez sur Modifier ![ l’icône ](../../media/O365-MDM-CreatePolicy-EditIcon.gif) Modifier.

3. Dans la page des propriétés du groupe de rôles sous **Membres,** cliquez sur Ajouter une icône et sélectionnez le nom de l’utilisateur (ou des ![ utilisateurs) que vous ](../../media/ITPro-EAC-AddIcon.gif) souhaitez ajouter.

4. Lorsque vous avez sélectionné tous les utilisateurs que vous souhaitez ajouter au groupe de rôles, cliquez sur **Ajouter, \>** puis **SUR OK.**

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-security--compliance-center-powershell-to-give-another-user-access-to-the-security--compliance-center"></a>Utiliser le Centre de sécurité & conformité PowerShell pour accorder à un autre utilisateur l’accès au Centre de sécurité & conformité

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Utilisez la syntaxe suivante :

   ```powershell
   Add-RoleGroupMember -Identity <RoleGroup> -Member <UserIdentity>

   - _Identity_ is the role group.
   - _Member_ is the user or universal security group (USG). You can specify only one member at a time.

   This example adds MatildaS to the Organization Management role group.

   ```PowerShell
   Add-RoleGroupMember -Identity "Organization Management" -Member MatildaS
   ```

Pour des problèmes de syntaxe et de paramètres détaillés, voir [Add-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/add-rolegroupmember)

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien accordé l’accès au Centre de sécurité & conformité, faites l’une des étapes suivantes :

- Dans le Centre de sécurité & conformité, sélectionnez le groupe de **rôles Autorisations.** Dans le volant d’informations qui s’ouvre, vérifiez les membres du groupe de rôles.

- Dans le Centre & de sécurité PowerShell, remplacez-le par le nom du groupe de rôles \<RoleGroupName\> et exécutez la commande suivante :

  ```powershell
  Get-RoleGroupMember -Identity "<RoleGroupName>"
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-RoleGroupMember.](/powershell/module/exchange/Get-RoleGroupMember)