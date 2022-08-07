---
title: Protéger vos comptes d’administrateur dans Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Découvrez comment configurer et protéger vos comptes d’administrateur dans Microsoft 365 Business Premium.
ms.openlocfilehash: 6534cf3285aa08b4b9da4ea65965751a1ac14a6b
ms.sourcegitcommit: cd9df1a681265905eef99c039f7036b2fa6e8b6d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2022
ms.locfileid: "67277024"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Protéger vos comptes d’administrateur dans Microsoft 365 Business Premium

Étant donné que les comptes d’administrateur disposent de privilèges élevés, ils sont des cibles précieuses pour les pirates informatiques et les cybercriminels. Cet article décrit :

- [Comment configurer un autre compte administrateur pour les urgences](#create-other-admin-accounts).
- [Comment créer un compte administrateur d'urgence](#create-an-emergency-admin-account).
- [Comment créer un compte utilisateur pour vous-même](#create-a-user-account-for-yourself).
- [Comment protéger les comptes administrateur](#protect-admin-accounts).
- [Recommandations supplémentaires](#additional-recommendations) et votre [prochain objectif](#next-objective).

Lorsque vous vous inscrivez à Microsoft 365 et entrez vos informations, vous devenez automatiquement l’administrateur général (également appelé administrateur général). Un administrateur général a le contrôle final des comptes d’utilisateur et de tous les autres paramètres du Centre d’administration Microsoft ([https://admin.microsoft.com](https://admin.microsoft.com)), mais il existe de nombreux types de comptes d’administrateur avec différents degrés d’accès. Consultez les [rôles d’administrateur](/office365/admin/add-users/about-admin-roles) pour plus d’informations sur les différents niveaux d’accès pour chaque type de rôle d’administrateur.

## <a name="create-other-admin-accounts"></a>Créer d'autres comptes d'administrateur

Utilisez les comptes d'administrateur uniquement pour l'administration de Microsoft 365. Les administrateurs doivent disposer d'un compte d'utilisateur distinct pour leur utilisation régulière des applications Office et n'utiliser leur compte administratif que lorsque cela est nécessaire pour gérer les comptes et les appareils, et lorsqu'ils travaillent sur d'autres fonctions d'administration. C'est également une bonne idée de supprimer la licence Microsoft 365 de vos comptes d'administrateur afin de ne pas avoir à payer pour des licences supplémentaires.

Vous souhaiterez configurer au moins un autre compte d'administrateur global pour donner un accès administrateur à un autre employé de confiance. Vous pouvez également créer des comptes d’administrateur distincts pour la gestion des utilisateurs (ce rôle est appelé **administrateur de gestion des utilisateurs**). Pour plus d’informations, consultez les [rôles d’administrateur](/office365/admin/add-users/about-admin-roles).

> [!IMPORTANT]
> Bien que nous vous recommandions de configurer un ensemble de comptes d'administrateur, vous souhaiterez limiter le nombre d'administrateurs globaux pour votre organisation. De plus, nous vous recommandons d'adhérer au concept d'accès au moindre privilège, ce qui signifie que vous n'accordez l'accès qu'aux données et opérations nécessaires à l'exécution de leur travail. [En savoir plus sur le principe du moindre privilège](/azure/active-directory/develop/secure-least-privileged-access). 

Pour créer plus de comptes administrateur :

 1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centre d’administration Microsoft 365</a>, puis choisissez **Utilisateurs**\>**Utilisateurs actifs** dans le volet de navigation gauche.

    ![Choisissez Utilisateurs, puis Utilisateurs actifs dans le volet de navigation gauche.](../media/Activeusers.png)

 2. Dans la page **Utilisateurs actifs**, sélectionnez **Ajouter un utilisateur** en haut de la page. 

 3. Dans le volet **Ajouter un utilisateur** , entrez des informations de base telles que les informations de nom et de nom d’utilisateur.

 4. Entrez et configurez les informations sur les **licences de produit** .

 5. Dans **paramètres facultatifs**, définissez le rôle de l’utilisateur, y compris l’ajout d’un accès au Centre d’administration le cas échéant.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Définissez de nouveaux rôles d’utilisateur.":::

 6. Terminez et passez en revue vos paramètres, puis sélectionnez **Terminer l’ajout** pour confirmer les détails.

## <a name="create-an-emergency-admin-account"></a>Créer un compte d’administrateur d’urgence

Vous devez également créer un compte de sauvegarde qui n'est pas configuré avec l'authentification multifacteur (MFA) afin de ne pas vous verrouiller accidentellement (par exemple, si vous perdez votre téléphone que vous utilisez comme deuxième forme de vérification ). Assurez-vous que le mot de passe de ce compte est une expression ou au moins 16 caractères. Ce compte d'administrateur d'urgence est souvent appelé "compte de bris de glace".

## <a name="create-a-user-account-for-yourself"></a>Créer un compte d’utilisateur pour vous-même

Si vous êtes un administrateur, vous aurez besoin d'un compte d'utilisateur pour les tâches de travail régulières, telles que la vérification du courrier. Nommez vos comptes afin que vous sachiez lequel est lequel. Par exemple, vos informations d'identification d'administrateur peuvent être similaires à  *Alice.Chavez <span></span>@Contoso.org*, et votre compte d'utilisateur habituel peut être similaire à *Alice <span></span>@Contoso.com*.

Pour créer un compte d’utilisateur :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centre d’administration Microsoft 365</a>, puis choisissez **Utilisateurs**\>**Utilisateurs actifs** dans le volet de navigation gauche.

2. Dans la page **Utilisateurs actifs**, sélectionnez **Ajouter un utilisateur** en haut de la page, puis, dans le panneau **Ajouter un utilisateur**, entrez le nom et d’autres informations.

3. Dans la section **Licences de produit**, activez la case à cocher **Microsoft 365 Business Premium (sans accès administratif).**

4. Dans la section **Paramètres facultatifs**, laissez la case d’option par défaut sélectionnée pour **Utilisateur (aucun accès au Centre d’administration).**

5. Terminez et passez en revue vos paramètres, puis sélectionnez **Terminer l’ajout** pour confirmer les détails.

## <a name="protect-admin-accounts"></a>Protéger les comptes d’administrateur

Pour protéger tous vos comptes administrateur, assurez-vous de suivre ces recommandations :

- Exigez que tous les comptes d'administrateur utilisent l'authentification sans mot de passe (telle que Windows Hello ou une application d'authentification) ou MFA. Pour en savoir plus sur l'importance de l'authentification sans mot de passe, consultez le livre blanc [Microsoft Security : Passwordless protection](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2KEup).

- Évitez d'utiliser des autorisations personnalisées pour les administrateurs. Au lieu d'accorder des autorisations à des utilisateurs spécifiques, attribuez des autorisations via des rôles dans Azure Active Directory (Azure AD). Et n'accordez l'accès qu'aux données et aux opérations nécessaires pour effectuer la tâche à accomplir. [En savoir plus sur les rôles les moins privilégiés dans Azure AD](/azure/active-directory/roles/delegate-by-task).

- Utilisez des rôles intégrés pour attribuer des autorisations dans la mesure du possible. Le contrôle d'accès basé sur les rôles Azure (RBAC) comporte plusieurs rôles intégrés que vous pouvez utiliser. [En savoir plus sur les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="additional-recommendations"></a>Recommandations supplémentaires

- Avant d’utiliser des comptes d’administrateur, fermez toutes les sessions et applications de navigateur non liées, y compris les comptes de messagerie personnels. Vous pouvez également l’utiliser dans des fenêtres de navigateur privées ou incognito.

- Après avoir effectué les tâches d’administration, veillez à vous déconnecter de la session du navigateur.

## <a name="next-objective"></a>Objectif suivant

[Augmenter la protection contre les menaces pour Microsoft 365 Business Premium](m365bp-increase-protection.md)
