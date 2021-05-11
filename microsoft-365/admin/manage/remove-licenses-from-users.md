---
title: Annuler l'assignation des licences aux utilisateurs
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
- M365-subscription-management
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- manage_licenses
- okr_smb
- commerce
search.appverid:
- MET150
description: Découvrez comment désattribuer des licences à des comptes d’utilisateurs.
ms.date: 07/01/2020
ms.openlocfilehash: 87bb8f6fe0e85fc4ac832f2bc4ad746e8d6386eb
ms.sourcegitcommit: efb932db63ad3ab4af4b585428d567d069410e4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52310991"
---
# <a name="unassign-licenses-from-users"></a>Annuler l'assignation des licences aux utilisateurs

Vous pouvez désattribuer des licences à des utilisateurs sur la page **Utilisateurs** actifs ou sur la page **Licences.** La méthode que vous utilisez varie selon que vous souhaitez soit désattribuer des licences de produits à des utilisateurs spécifiques, soit désattribuer des licences d’utilisateurs à partir d’un produit spécifique.

> [!NOTE]
> En tant qu’administrateur, vous ne pouvez pas attribuer ou annuler des attributions de licences pour un abonnement d’achat en libre-service acheté par un utilisateur de votre organisation. Vous pouvez [prendre le contrôle d’un abonnement d’achat en libre-service](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), puis attribuer ou annuler des attributions de licences.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur global, de licence, d’utilisateur pour désattribuer des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [supprimer des licences de comptes d'utilisateurs à l'aide d'Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Vous pouvez également [supprimer les comptes d’utilisateurs](../add-users/delete-a-user.md) qui ont été affectés à une licence afin de les rendre disponibles pour d’autres utilisateurs. Lorsque vous supprimez un compte d’utilisateur, sa licence est immédiatement disponible pour une autre personne.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Utiliser la page Licences pour désattribuer des licences

Lorsque vous utilisez la page **Licences** pour désattribuer des licences, vous désattribuez les licences d’un produit spécifique à 20 utilisateurs au plus.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, choisissez la page **Facturation** > **Licences**.
::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, choisissez la page **Facturation** > **Licences**.

::: moniker-end

2. Sélectionnez le produit pour lequel vous souhaitez désattribuer des licences.
3. Sélectionnez les utilisateurs pour lesquels vous souhaitez désattribuer des licences.
4. Sélectionnez **Désattribuer des licences.**
5. In the **Unassign licenses** box, select **Unassign**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Utiliser la page Utilisateurs actifs pour désattribuer des licences

Lorsque vous utilisez la page **Utilisateurs actifs** pour désattribuer des licences, vous désattribuez des licences de produits aux utilisateurs.

### <a name="unassign-licenses-from-one-user"></a>Désattribuer des licences à un utilisateur
  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **Utilisateurs actifs**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **Utilisateurs actifs**.

::: moniker-end

2. Sélectionnez la ligne de l’utilisateur pour qui vous souhaitez désattribuer une licence.
3. Dans le volet de droite, sélectionnez **Licences et applications**.
4. Développez la section **Licences,** désélectionnez les zones des licences que vous souhaitez désattribuer, puis sélectionnez **Enregistrer les modifications.**

###  <a name="unassign-licenses-from-multiple-users"></a>Désattribuer des licences à plusieurs utilisateurs

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **Utilisateurs actifs**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **Utilisateurs actifs**.

::: moniker-end

2. Sélectionnez les cercles en de côté des noms des utilisateurs pour qui vous souhaitez désattribuer des licences.
3. Dans la partie supérieure, sélectionnez **Plus d'options (...)**, puis choisissez **Gérer les licences de produits**.
4. Dans le volet **Gérer des licences de produits**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du  volet Remplacer les produits existants, cochez la case Supprimer toutes les licences de produits des **utilisateurs sélectionnés,** puis **sélectionnez Remplacer** \> **fermer.**

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Qu’advient-il des données d’un utilisateur lorsque vous supprimez sa licence ?

- Lorsqu’une licence est supprimée d’un utilisateur, les données associées à ce compte sont détenues pendant 30 jours. Après la période de grâce de 30 jours, les données sont supprimées et ne peuvent pas être récupérées.
- Les fichiers enregistrés dans OneDrive Entreprise ne sont pas supprimés, sauf si l’utilisateur est supprimé du Centre d’administration Microsoft 365 ou supprimé via la synchronisation Active Directory. Pour plus d’informations, [voir OneDrive rétention et suppression.](/onedrive/retention-and-deletion)
- Lorsque la licence est supprimée, la boîte aux lettres de l’utilisateur n’est plus utilisable dans une recherche à l’aide d’un outil eDiscovery tel que la recherche de contenu ou Advanced eDiscovery. Pour plus d’informations, voir « Recherche de boîtes aux lettres déconnectées ou déconnectées » dans la référence de [recherche de contenu.](../../compliance/content-search-reference.md#searching-disconnected-or-de-licensed-mailboxes)
- Si vous avez un abonnement Enterprise, comme Office 365 Entreprise E3, Exchange Online vous permet de conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé à l’aide de boîtes aux lettres [inactives.](../../compliance/inactive-mailboxes-in-office-365.md) Pour plus d’informations, voir [Créer et gérer des boîtes aux lettres inactives dans Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Pour savoir comment bloquer l’accès d’un utilisateur aux données Microsoft 365 après la suppression de sa licence et comment accéder aux données par la suite, voir Supprimer un [ancien employé.](../add-users/remove-former-employee.md)
- Si vous supprimez la licence d’un utilisateur et que des applications Office sont toujours installées, les erreurs d’activation et de produit sans licence s’Office s’Office aux [utilisateurs.](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380)

## <a name="next-steps"></a>Étapes suivantes

Si vous ne comptez pas réattribuer les licences inutilisées à d’autres [utilisateurs,](../../managed-desktop/get-started/assign-licenses.md)envisagez de supprimer les [licences](../../commerce/licenses/buy-licenses.md) de votre abonnement afin de ne pas payer plus de licences que nécessaire.

## <a name="related-content"></a>Contenu connexe

[Supprimer des licences de votre abonnement](../../commerce/licenses/buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](assign-licenses-to-users.md) (article)\
[Comprendre les abonnements et les licences dans Microsoft 365 entreprise](../../commerce/licenses/subscriptions-and-licenses.md) (article)