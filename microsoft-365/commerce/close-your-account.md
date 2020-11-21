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
ms.openlocfilehash: bdcf4408ddc9c198fab1d68b4c096fad9059b975
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376316"
---
# <a name="close-your-account"></a>Fermer votre compte

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).

::: moniker-end

Lorsque vous fermez votre compte auprès de Microsoft, toutes les informations relatives à votre compte sont supprimées. Ces informations incluent les abonnements, les licences, les modes de paiement, les utilisateurs et les données utilisateur.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer ce processus, veillez à sauvegarder les données que vous voulez conserver.

Vous devez être un administrateur général ou un administrateur de facturation pour effectuer les tâches décrites dans cet article. Si vous souhaitez en savoir plus, veuillez consulter la page [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Étape 1 : supprimer des utilisateurs

Supprimez tous les utilisateurs à l’exception d’un administrateur général. L’administrateur général termine les étapes de fermeture du compte. Avant de pouvoir supprimer le répertoire à la fin de ce processus, vous devez supprimer tous les autres utilisateurs.

Si les utilisateurs sont synchronisés en local, désactivez la synchronisation, puis supprimez les utilisateurs dans le répertoire Cloud à l’aide du portail Azure ou des applets de commande Azure PowerShell.

Pour supprimer des utilisateurs, consultez la rubrique <a href="https://docs.microsoft.com/office365/admin/add-users/delete-a-user?view=o365-worldwide#user-management-admin-delete-one-or-more-users-from-office-365">administrateur de gestion des utilisateurs : supprimer un ou plusieurs utilisateurs</a>.

Vous pouvez également utiliser l’applet de commande PowerShell <a href="https://go.microsoft.com/fwlink/?linkid=842230">Remove-MsolUser</a> pour supprimer des utilisateurs en bloc.

Si votre organisation utilise Active Directory qui se synchronise avec Microsoft Azure Active Directory (Azure AD), supprimez le compte d’utilisateur d’Active Directory. Pour obtenir des instructions, consultez la rubrique <a href="https://docs.microsoft.com/azure/active-directory/users-groups-roles/users-bulk-delete">suppression en bloc d’utilisateurs dans Azure Active Directory</a>.

## <a name="step-2-cancel-all-active-subscriptions"></a>Étape 2 : annuler tous les abonnements actifs

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **produits** , recherchez un abonnement actif. Sélectionnez **Autres actions** (points de suspension), puis sélectionnez **Annuler l’abonnement**.
3. Dans le volet **Annuler l’abonnement** , choisissez la raison pour laquelle vous annulez l’abonnement. Vous pouvez également fournir des commentaires.
4. Sélectionnez **Enregistrer**.
5. Répétez les étapes 1 à 4 pour annuler tous les abonnements actifs.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Étape 3 : supprimer tous les abonnements désactivés

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **produits** , sélectionnez un abonnement désactivé.
3. Sur la page Détails de l’abonnement, dans la section **paramètres d’abonnement et de paiement** , sélectionnez **Supprimer l’abonnement**.
4. Dans le volet **supprimer un abonnement** , sélectionnez Supprimer un **abonnement**.
5. Dans la boîte de dialogue **supprimer un abonnement** , sélectionnez **Oui**.
6. Pour chaque abonnement désactivé, répétez les étapes 3 à 5 jusqu’à ce que tous les abonnements soient supprimés.

> [!NOTE]
> Si vous ne parvenez pas à supprimer immédiatement un abonnement désactivé, <a href="https://go.microsoft.com/fwlink/p/?linkid=518322" target="_blank">Contactez le support technique</a> .

## <a name="step-4-disable-multi-factor-authentication"></a>Étape 4 : désactivation de l’authentification multifacteur

1. Connectez-vous au centre d’administration à l’aide d’un compte d’administrateur général. Pour vérifier les rôles que vous avez, reportez-vous à [la rubrique vérifier les rôles d’administrateur dans votre organisation](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. Accédez **à la**  >  page utilisateurs <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a> .
3. Choisissez **l’authentification multifacteur**.
4. Sur la page authentification multifacteur, désactivez tous les comptes à l’exception du compte d’administrateur global que vous utilisez actuellement.

Vous pouvez également <a href="https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell">Utiliser PowerShell pour désactiver l’authentification multifacteur pour plusieurs utilisateurs</a>.

## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Étape 5 : supprimer le répertoire dans Azure Active Directory

1. Connectez-vous au <a href="https://aad.portal.azure.com/" target="_blank">Centre d’administration Azure ad</a> à l’aide d’un compte d’administrateur général.
2. Sélectionner **Azure Active Directory**.
3. Basculez vers l’organisation que vous souhaitez supprimer.
4. Sélectionnez **supprimer le client**.
5. Si votre organisation ne parvient pas à effectuer une ou plusieurs vérifications, un lien vers plus d’informations sur la façon de réussir les vérifications s’affiche. Après avoir passé tous les contrôles, sélectionnez **supprimer** pour terminer le processus.

Une fois cette étape terminée, votre compte auprès de Microsoft est fermé et supprimé.