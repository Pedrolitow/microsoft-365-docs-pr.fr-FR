---
title: Fermer votre compte
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- commerce
ms.custom:
- AdminSurgePortfolio
- fwlink 2133922 to Delete subscription heading
search.appverid:
- MET150
description: Découvrez comment fermer votre compte auprès de Microsoft.
ms.openlocfilehash: 19e9a92a90f7c88cc150844ab451bc71d63e4c4a
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50911661"
---
# <a name="close-your-account"></a>Fermer votre compte

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](../admin/microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).

::: moniker-end

Lorsque vous fermez votre compte auprès de Microsoft, toutes les informations relatives à votre compte sont supprimées. Ces informations incluent les abonnements, les licences, les modes de paiement, les utilisateurs et les données utilisateur.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer ce processus, veillez à sauvegarder les données que vous voulez conserver.

Pour suivre les étapes décrites dans cet article, vous devez être administrateur général ou de facturation. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Étape 1 : Supprimer des utilisateurs

Supprimez tous les utilisateurs à l’exception d’un administrateur général. L’administrateur général termine la procédure de fermeture du compte. Avant de pouvoir supprimer l’annuaire à la fin de ce processus, vous devez supprimer tous les autres utilisateurs.

Si les utilisateurs sont synchronisés en local, désynchronisé, supprimez les utilisateurs dans l’annuaire cloud à l’aide du portail Azure ou des cmdlets Azure PowerShell.

Pour supprimer des utilisateurs, voir Administrateur de gestion des <a href="/office365/admin/add-users/delete-a-user?view=o365-worldwide#user-management-admin-delete-one-or-more-users-from-office-365">utilisateurs : Supprimer un ou plusieurs utilisateurs.</a>

Vous pouvez également utiliser <a href="https://go.microsoft.com/fwlink/?linkid=842230">l’cmdlet Remove-MsolUser</a> PowerShell pour supprimer des utilisateurs en bloc.

Si votre organisation utilise Active Directory qui se synchronise avec Microsoft Azure Active Directory (Azure AD), supprimez le compte d’utilisateur d’Active Directory. Pour obtenir des instructions, <a href="/azure/active-directory/users-groups-roles/users-bulk-delete">voir Suppression en bloc d’utilisateurs dans Azure Active Directory.</a>

## <a name="step-2-cancel-all-active-subscriptions"></a>Étape 2 : Annuler tous les abonnements actifs

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, recherchez un abonnement actif. Sélectionnez **Autres actions** (points de suspension), puis sélectionnez **Annuler l’abonnement**.
3. Dans le volet **Annuler l’abonnement** , choisissez la raison pour laquelle vous annulez l’abonnement. Vous pouvez également fournir des commentaires.
4. Sélectionnez **Enregistrer**.
5. Répétez les étapes 1 à 4 pour annuler tous les abonnements actifs.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Étape 3 : Supprimer tous les abonnements désactivés

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, sélectionnez un abonnement désactivé.
3. Dans la page détails de l’abonnement, dans la section Paramètres d’abonnement et de **paiement,** **sélectionnez Supprimer l’abonnement.**
4. Dans le **volet Supprimer l’abonnement,** **sélectionnez Supprimer l’abonnement.**
5. Dans la **boîte de dialogue Supprimer un** abonnement, sélectionnez **Oui.**
6. Pour chaque abonnement désactivé, répétez les étapes 3 à 5 jusqu’à ce que tous les abonnements soient supprimés.

> [!NOTE]
> Si vous ne parvenez pas à supprimer immédiatement un abonnement désactivé, <a href="/microsoft-365/Admin/contact-support-for-business-products" target="_blank">contactez le support technique</a>

## <a name="step-4-disable-multi-factor-authentication"></a>Étape 4 : Désactiver l’authentification multifacteur

1. Connectez-vous au Centre d’administration avec un compte d’administrateur général. Pour vérifier les rôles que vous avez, [consultez Vérifier les rôles d’administrateur dans votre organisation.](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization)
2. Go to the **Users**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Active users</a> page.
3. Choisissez **Authentification multifacteur.**
4. Dans la page Authentification multifacteur, désactivez tous les comptes à l’exception du compte d’administrateur général que vous utilisez actuellement.

Vous pouvez également <a href="/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell">utiliser PowerShell pour désactiver l’authentification multifacteur pour plusieurs utilisateurs.</a>

## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Étape 5 : Supprimer le répertoire dans Azure Active Directory

1. Connectez-vous au <a href="https://aad.portal.azure.com/" target="_blank">Centre d’administration Azure AD</a> avec un compte d’administrateur général.
2. Sélectionner **Azure Active Directory**.
3. Basculez vers l’organisation que vous souhaitez supprimer.
4. Sélectionnez **Supprimer le client.**
5. Si votre organisation échoue à une ou plusieurs vérifications, un lien vous permet d’obtenir plus d’informations sur la façon de les réussir. Après avoir réussi toutes les vérifications, **sélectionnez Supprimer** pour terminer le processus.

Une fois cette dernière étape terminée, votre compte microsoft est fermé et supprimé.