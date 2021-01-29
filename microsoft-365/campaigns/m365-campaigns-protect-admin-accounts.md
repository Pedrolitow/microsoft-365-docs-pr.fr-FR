---
title: Protéger vos comptes d’administrateur
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Découvrez comment configurer et protéger vos comptes d’administrateur.
ms.openlocfilehash: 73e4b69571b1e1d0a4d1585224fe256ff135c40a
ms.sourcegitcommit: 1b30ac6e05906c8a014b1fed33fc71e1821f6ad2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2021
ms.locfileid: "50044487"
---
# <a name="protect-your-administrator-accounts"></a>Protéger vos comptes d’administrateur

Étant donné que les comptes d’administrateur ont des privilèges élevés, ils sont des cibles précieuses pour les pirates informatiques et les cybercriminels. Cet article décrit les aspects suivants :

- Comment configurer un compte d’administrateur supplémentaire pour les urgences.
- Comment protéger ces comptes.

Lorsque vous vous inscrivez à Microsoft 365 et entrez vos informations, vous devenez automatiquement l’administrateur global. Un administrateur global a le contrôle ultime des comptes d’utilisateur et de tous les autres paramètres dans le Centre d’administration Microsoft, mais il existe de nombreux types de comptes d’administrateur avec différents degrés d’accès. Pour plus [d’informations sur](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles) les différents niveaux d’accès pour chaque type de rôle d’administrateur, voir les rôles d’administrateur.

## <a name="create-additional-admin-accounts"></a>Créer des comptes d’administrateur supplémentaires

Utilisez des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent avoir un compte d’utilisateur distinct pour une utilisation régulière des applications Office et utiliser leur compte administratif uniquement lorsque cela est nécessaire pour gérer les comptes et les appareils, et tout en travaillant sur d’autres fonctions d’administration. Il est également bon de supprimer la licence Microsoft 365 des comptes d’administrateur afin de ne pas avoir à les payer.

Vous pouvez configurer au moins un compte d’administrateur global supplémentaire pour accorder à l’administrateur l’accès à un autre employé approuvé. Vous pouvez également créer des comptes d’administrateur distincts pour la gestion des utilisateurs (ce rôle est appelé **administrateur de gestion des utilisateurs).** Pour plus d’informations, voir [les rôles d’administrateur.](https://docs.microsoft.com/office365/admin/add-users/about-admin-roles)

Pour créer des comptes d’administrateur supplémentaires :

 1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">admin center</a> and then choose **Users** \> **Active users** in the left nav.

    ![Sélectionnez Utilisateurs, puis Utilisateurs actifs dans le navigation gauche](../media/Activeusers.png)

 2. Dans la page **Utilisateurs** actifs, sélectionnez Ajouter un utilisateur  en haut de la page, puis, dans le panneau Nouvel utilisateur, entrez le nom et d’autres informations. 
 3. Développez la section **Rôles,** puis choisissez **Administrateur général** pour accorder à cet utilisateur un accès d’administrateur général. Vous pouvez également choisir **un administrateur personnalisé et** choisir l’un des rôles affichés.

    Entrez un autre message électronique dans la zone de texte **Adresse de messagerie** alternative. Vous pouvez utiliser cette adresse pour récupérer les informations de votre mot de passe si vous êtes verrouillé. Pour les administrateurs globaux, un relevé de facturation est également envoyé à cette adresse.

    ![Choisir le rôle d’administrateur](../media/adminroles.png)

 4. Dans la section **Licences de** produits, déplacez le sélecteur de **Microsoft 365 Business** sur Hors et l’utilisateur Créer sans licence de produit  **sur** **Sur**.

    ![Choisir la licence de produit](../media/productlicense.png)

## <a name="create-an-emergency-admin-account"></a>Créer un compte d’administrateur d’urgence

Vous devez également créer un compte de sauvegarde qui n’est pas installé avec l’authentification multifacteur (MFA) afin de ne pas vous verrouiller accidentellement (par exemple, si vous perdez votre téléphone que vous utilisez comme deuxième forme de vérification). Assurez-vous que le mot de passe de ce compte est une expression d’au moins 16 caractères. Ce compte est souvent appelé « compte à l’état « break-glass ».

## <a name="create-a-user-account-for-yourself"></a>Créer un compte d’utilisateur pour vous-même

Utilisez votre compte d’utilisateur pour participer à la collaboration avec votre organisation, y compris la vérification de la messagerie. Cela signifie que vos informations d’identification d’administrateur peuvent être similaires à  *Alice.Contrôlez <span></span> @Contoso.org* et que votre compte d’utilisateur normal peut être similaire à *Alice <span></span> @Contoso.com*.

Pour créer un compte d’utilisateur :

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">admin center</a> and then choose **Users** \> **Active users** in the left nav.
2. Dans la page **Utilisateurs** actifs, sélectionnez Ajouter un utilisateur  en haut de la page, puis, dans le panneau Nouvel utilisateur, entrez le nom et d’autres informations. 
3. Développez la section **Rôles,** puis choisissez **Utilisateur (pas d’accès administratif).**
4. Dans la section **Licences de produits,** déplacez le sélecteur **de Microsoft 365 Business** sur **On**.

## <a name="register-each-of-these-accounts-for-multi-factor-authentication"></a>Inscrire chacun de ces comptes pour l’authentification multifacteur

Assurez-vous que ces comptes utilisent [l’authentification multifacteur.](m365-campaigns-multifactor-authenication.md)

## <a name="additional-recommendations"></a>Recommandations supplémentaires

- Assurez-vous que les comptes d’administrateur sont également mis en place pour l’authentification multifacteur. Nous allons vous montrer comment faire dans [Configurer les stratégies d’accès conditionnel.](m365-campaigns-conditional-access.md)
- Avant d’utiliser des comptes d’administrateur, fermez toutes les applications et sessions de navigateur non liées, y compris les comptes de messagerie personnels. Vous pouvez également l’utiliser dans des fenêtres de navigateur privées ou privées.
- Après avoir terminé les tâches d’administration, n’oubliez pas de vous ausserer de la session du navigateur.
