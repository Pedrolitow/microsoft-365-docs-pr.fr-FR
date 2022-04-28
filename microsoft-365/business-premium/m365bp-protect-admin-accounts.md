---
title: Protéger vos comptes d’administrateur dans Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
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
description: Découvrez comment configurer et protéger vos comptes d’administrateur dans Microsoft 365 Business Premium.
ms.openlocfilehash: b054267264b8440929559ad1a2e335449f3c0309
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091520"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Protéger vos comptes d’administrateur dans Microsoft 365 Business Premium

Étant donné que les comptes d’administrateur disposent de privilèges élevés, ils sont des cibles précieuses pour les pirates informatiques et les cybercriminels. Cet article décrit les aspects suivants :

- Comment configurer un compte d’administrateur supplémentaire pour les urgences.
- Guide pratique pour protéger ces comptes.

Lorsque vous vous inscrivez à Microsoft 365 et entrez vos informations, vous devenez automatiquement l’administrateur général (également appelé administrateur général). Un administrateur général a le contrôle final des comptes d’utilisateur et de tous les autres paramètres du Centre d’administration Microsoft ([https://admin.microsoft.com](https://admin.microsoft.com)), mais il existe de nombreux types de comptes d’administrateur avec différents degrés d’accès. Consultez les [rôles d’administrateur](/office365/admin/add-users/about-admin-roles) pour plus d’informations sur les différents niveaux d’accès pour chaque type de rôle d’administrateur.

## <a name="create-additional-admin-accounts"></a>Créer des comptes d’administrateur supplémentaires

Utilisez des comptes d’administrateur uniquement pour l’administration. Les administrateurs doivent disposer d’un compte d’utilisateur distinct pour une utilisation régulière des applications Office et utiliser leur compte d’administration uniquement lorsque cela est nécessaire pour gérer les comptes et les appareils, et tout en travaillant sur d’autres fonctions d’administration. Il est également judicieux de supprimer la licence Microsoft 365 des comptes d’administrateur afin que vous n’ayez pas à les payer.

Vous pouvez configurer au moins un compte d’administrateur général supplémentaire pour accorder à l’administrateur l’accès à un autre employé approuvé. Vous pouvez également créer des comptes d’administrateur distincts pour la gestion des utilisateurs (ce rôle est appelé **administrateur de gestion des utilisateurs**). Pour plus d’informations, consultez les [rôles d’administrateur](/office365/admin/add-users/about-admin-roles).

Pour créer des comptes d’administrateur supplémentaires :

 1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centre d’administration Microsoft 365</a>, puis choisissez **Utilisateurs**\>**Utilisateurs actifs** dans le volet de navigation gauche.

    ![Choisissez Utilisateurs, puis Utilisateurs actifs dans le volet de navigation gauche.](../media/Activeusers.png)

 2. Dans la page **Utilisateurs actifs**, sélectionnez **Ajouter un utilisateur** en haut de la page, puis, dans le panneau **Nouvel utilisateur**, entrez le nom et d’autres informations.

 3. Développez la section **Rôles**, puis choisissez **Administrateur général** pour accorder à cet utilisateur un accès administrateur général. Vous pouvez également choisir **Administrateur personnalisé** et choisir l’un des rôles affichés.

    Entrez un autre e-mail dans la zone de texte **Adresse alternative** . Vous pouvez utiliser cette adresse pour récupérer vos informations de mot de passe si vous êtes verrouillé. Pour les administrateurs généraux, un relevé de facturation sera également envoyé à cette adresse.

    ![Choisissez le rôle d’administrateur.](../media/adminroles.png)

 4. Dans la section **Licences de produit**, déplacez le sélecteur pour **Microsoft 365 Business** vers **Désactivé** et **Créer un utilisateur sans licence de produit** sur **Activé**.

    ![Choisissez la licence de produit.](../media/productlicense.png)

## <a name="create-an-emergency-admin-account"></a>Créer un compte d’administrateur d’urgence

Vous devez également créer un compte de sauvegarde qui n’est pas configuré avec l’authentification multifacteur (MFA) afin de ne pas vous verrouiller accidentellement (par exemple, si vous perdez votre téléphone que vous utilisez comme deuxième forme de vérification). Assurez-vous que le mot de passe de ce compte est une expression ou au moins 16 caractères. Il s’agit souvent d’un « compte de secours ».

## <a name="create-a-user-account-for-yourself"></a>Créer un compte d’utilisateur pour vous-même

Utilisez votre compte d’utilisateur pour participer à la collaboration avec votre organisation, y compris la vérification de courrier. Cela signifie que vos informations d’identification d’administrateur peuvent être similaires à *Alice Chavez.<span></span>@Contoso.org* et votre compte d’utilisateur standard peut être similaire à *Alice <span></span>@Contoso.com*.

Pour créer un compte d’utilisateur :

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Centre d’administration Microsoft 365</a>, puis choisissez **Utilisateurs**\>**Utilisateurs actifs** dans le volet de navigation gauche.

2. Dans la page **Utilisateurs actifs**, sélectionnez **Ajouter un utilisateur** en haut de la page, puis, dans le panneau **Nouvel utilisateur**, entrez le nom et d’autres informations.

3. Développez la section **Rôles**, puis choisissez **Utilisateur (aucun accès administratif)**.

4. Dans la section **Licences de produit**, déplacez le sélecteur pour **Microsoft 365 Business** vers **Activé**.

## <a name="additional-recommendations"></a>Recommandations supplémentaires

- Avant d’utiliser des comptes d’administrateur, fermez toutes les sessions et applications de navigateur non liées, y compris les comptes de messagerie personnels. Vous pouvez également l’utiliser dans des fenêtres de navigateur privées ou incognito.

- Après avoir effectué les tâches d’administration, veillez à vous déconnecter de la session du navigateur.

## <a name="next-objective"></a>Objectif suivant

Suivez les étapes pour [activer les paramètres de sécurité par défaut](m365bp-conditional-access.md).

