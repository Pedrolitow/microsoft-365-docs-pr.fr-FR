---
title: Fermer votre compte
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- commerce
ms.custom: ''
search.appverid:
- MET150
description: Découvrez comment fermer votre compte auprès de Microsoft.
ms.openlocfilehash: b71cfe8246b5e3e9471c76cf8043bad52840f194
ms.sourcegitcommit: 60c1932dcca249355ef7134df0ceb0e57757dc81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "43942852"
---
# <a name="close-your-account"></a>Fermer votre compte

Lorsque vous fermez votre compte auprès de Microsoft, toutes les informations relatives à votre compte sont supprimées. Ces informations incluent les abonnements, les licences, les modes de paiement, les utilisateurs et les données utilisateur. Avant de commencer cette procédure, assurez-vous de sauvegarder toutes les données que vous souhaitez conserver.

## <a name="step-1-delete-users"></a>Étape 1 : supprimer des utilisateurs

Supprimez tous les utilisateurs à l’exception d’un administrateur général qui termine les étapes de fermeture du compte. Avant de pouvoir supprimer le répertoire à la fin de ce processus, vous devez supprimer tous les autres utilisateurs.

Si les utilisateurs sont synchronisés en local, désactivez la synchronisation, puis supprimez les utilisateurs dans le répertoire Cloud à l’aide du portail Azure ou des applets de commande Azure PowerShell.

Pour supprimer des utilisateurs, consultez la rubrique <a href="https://docs.microsoft.com/office365/admin/add-users/delete-a-user?view=o365-worldwide#user-management-admin-delete-one-or-more-users-from-office-365">administrateur de gestion des utilisateurs : supprimer un ou plusieurs utilisateurs</a>.

Vous pouvez également utiliser l’applet de commande PowerShell <a href="https://go.microsoft.com/fwlink/?linkid=842230">Remove-MsolUser</a> pour supprimer des utilisateurs en bloc.

Si votre organisation utilise Active Directory qui se synchronise avec Azure AD, supprimez le compte d’utilisateur d’Active Directory. Pour obtenir des instructions, consultez la rubrique <a href="https://docs.microsoft.com/azure/active-directory/users-groups-roles/users-bulk-delete">suppression en bloc d’utilisateurs dans Azure Active Directory</a>.

## <a name="step-2-cancel-all-active-subscriptions"></a>Étape 2 : annuler tous les abonnements actifs

1. Dans le centre d’administration, accédez à la page produits de **facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">& services</a> .

2. Si la liste abonnements est affichée en mode **table** , cliquez sur la droite sur **cartes**.

3. Recherchez un abonnement actif et, dans la section **paramètres & Actions** , sélectionnez **Annuler l’abonnement**.

4. Suivez les invites pour terminer le processus.

5. Répétez les étapes 1 à 4 pour annuler tous les abonnements actifs.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Étape 3 : supprimer tous les abonnements désactivés

1. Dans le centre d’administration, accédez à la page produits de **facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">& services</a> .

2. Si la liste abonnements est affichée en mode **table** , cliquez sur la droite sur **cartes**.

3. En regard de l’option État de l' **abonnement**, sélectionnez **désactivé**.

4. Recherchez un abonnement désactivé et, dans la section **paramètres & Actions** , sélectionnez **supprimer**.

5. Dans la boîte de dialogue **supprimer un abonnement** , activez la case à cocher **j’ai assimilé le choc** , puis sélectionnez **supprimer un abonnement**.

6. Pour chaque abonnement désactivé, répétez les étapes 4 et 5 jusqu’à ce que tous les abonnements aient été supprimés.

## <a name="step-4-disable-multi-factor-authentication"></a>Étape 4 : désactivation de l’authentification multifacteur

1. Dans le centre d’administration, accédez à **la** > page utilisateurs<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">actifs</a> .

2. Choisissez **l’authentification multifacteur**.

3. Sur la page authentification multifacteur, désactivez tous les comptes à l’exception du compte d’administrateur global que vous utilisez actuellement.

Vous pouvez également <a href="https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell">Utiliser PowerShell pour désactiver l’authentification multifacteur pour plusieurs utilisateurs</a>.

## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Étape 5 : supprimer le répertoire dans Azure Active Directory

1. Connectez-vous au <a href="https://aad.portal.azure.com/" target="_blank">Centre d’administration Azure ad</a> à l’aide d’un compte d’administrateur général.

2. Sélectionner **Azure Active Directory**.

3. Basculez vers le répertoire que vous souhaitez supprimer.

4. Sélectionnez **supprimer un répertoire**.

5. Si votre annuaire ne parvient pas à effectuer une ou plusieurs vérifications, un lien vers plus d’informations sur la façon de réussir les vérifications s’affiche. Après avoir passé tous les contrôles, sélectionnez **supprimer** pour terminer le processus.

Une fois cette étape terminée, votre compte auprès de Microsoft est fermé et supprimé.
