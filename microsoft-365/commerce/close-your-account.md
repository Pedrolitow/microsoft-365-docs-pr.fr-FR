---
title: Fermer votre compte
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- fwlink 2133922 to Delete subscription heading
- AdminTemplateSet
search.appverid: MET150
description: Lorsque vous fermez votre compte avec Microsoft, toutes les informations relatives à votre compte sont supprimées, y compris les licences, les utilisateurs et les données utilisateur.
ms.date: 04/02/2021
ms.openlocfilehash: 622c2e2ac8aa06691c08088a0c1e03890dc18419
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68732930"
---
# <a name="close-your-microsoft-account"></a>Fermer votre compte Microsoft

Lorsque vous fermez votre compte auprès de Microsoft, toutes les informations relatives à votre compte sont supprimées. Ces informations incluent les abonnements, les licences, les modes de paiement, les utilisateurs et les données utilisateur.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer ce processus, veillez à sauvegarder les données que vous voulez conserver.

Pour suivre les étapes décrites dans cet article, vous devez être administrateur général ou de facturation. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md).

## <a name="step-1-delete-users"></a>Étape 1 : Supprimer des utilisateurs

Supprimez tous les utilisateurs à l’exception d’un administrateur général. L’administrateur général effectue les étapes de fermeture du compte. Avant de pouvoir supprimer le répertoire à la fin de ce processus, vous devez supprimer tous les autres utilisateurs.

Si les utilisateurs sont synchronisés localement, désactivez d’abord la synchronisation, puis supprimez les utilisateurs dans l’annuaire cloud à l’aide des applets de commande Portail Azure ou Azure PowerShell.

Pour supprimer des utilisateurs, consultez [Administrateur de gestion des utilisateurs : Supprimer un ou plusieurs utilisateurs](../admin/add-users/delete-a-user.md#user-management-admin-delete-one-or-more-users-from-office-365).

Vous pouvez également utiliser l’applet de commande PowerShell [Remove-MsolUser](/powershell/module/msonline/remove-msoluser) pour supprimer des utilisateurs en bloc.

Si votre organisation utilise Active Directory qui se synchronise avec Microsoft Azure Active Directory (Azure AD), supprimez plutôt le compte d’utilisateur d’Active Directory. Pour obtenir des instructions, consultez [Supprimer des utilisateurs en bloc dans Azure Active Directory](/azure/active-directory/users-groups-roles/users-bulk-delete).

## <a name="step-2-cancel-all-active-subscriptions"></a>Étape 2 : Annuler tous les abonnements actifs

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **Produits** , recherchez un abonnement actif. Sélectionnez les trois points (autres actions), puis sélectionnez **Annuler l'abonnement**.
3. Dans le volet **Annuler l’abonnement** , choisissez la raison pour laquelle vous annulez l’abonnement. Vous pouvez également fournir des commentaires.
4. Sélectionnez **Enregistrer**.
5. Répétez les étapes 1 à 4 pour annuler tous les abonnements actifs.

## <a name="step-3-delete-all-disabled-subscriptions"></a>Étape 3 : Supprimer tous les abonnements désactivés

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **Produits** , sélectionnez un abonnement désactivé.
3. Dans la page détails de l’abonnement, dans la section **Paramètres d’abonnement et de paiement** , sélectionnez **Supprimer l’abonnement**.
4. Dans le volet **Supprimer l’abonnement** , sélectionnez **Supprimer l’abonnement**.
5. Dans la boîte de dialogue **Supprimer l’abonnement** , sélectionnez **Oui**.
6. Pour chaque abonnement désactivé, répétez les étapes 3 à 5 jusqu’à ce que tous les abonnements soient supprimés.

> [!NOTE]
> Si vous ne parvenez pas à supprimer immédiatement un abonnement désactivé, [contactez le support](../admin/get-help-support.md) technique.

## <a name="step-4-disable-multi-factor-authentication"></a>Étape 4 : Désactiver l’authentification multifacteur

1. Connectez-vous au Centre d’administration avec un compte Administrateur général. Pour vérifier les rôles dont vous [disposez, consultez Vérifier les rôles d’administrateur dans votre organisation](../admin/add-users/assign-admin-roles.md#check-admin-roles-in-your-organization).
2. Accédez à la page **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a> .
3. Choisissez **Authentification multifacteur**.
4. Dans la page d’authentification multifacteur, désactivez tous les comptes à l’exception du compte d’administrateur général que vous utilisez actuellement.

Vous pouvez également [utiliser PowerShell pour désactiver l’authentification multifacteur pour plusieurs utilisateurs](/azure/active-directory/authentication/howto-mfa-userstates#change-state-using-powershell).


## <a name="step-5-delete-the-directory-in-azure-active-directory"></a>Étape 5 : Supprimer l’annuaire dans Azure Active Directory

1. Connectez-vous au <a href="https://aad.portal.azure.com/" target="_blank">Centre d’administration Azure AD</a> avec un compte Administrateur général.
2. Sélectionnez **Azure Active Directory**.
3. Basculez vers l’organisation que vous souhaitez supprimer.
4. Sélectionnez **Supprimer le locataire**.
5. Si votre organisation échoue à une ou plusieurs vérifications, vous voyez un lien vers plus d’informations sur la façon de réussir les vérifications. Une fois que vous avez réussi toutes les vérifications, sélectionnez **Supprimer** pour terminer le processus.

Une fois cette dernière étape terminée, votre compte microsoft est fermé et supprimé.

## <a name="related-content"></a>Contenu associé 

[Comprendre votre facture pour Microsoft 365 pour les entreprises](./billing-and-payments/understand-your-invoice2.md) (article)\
[Annuler votre abonnement](./subscriptions/cancel-your-subscription.md) (article)

