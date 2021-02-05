---
title: Annuler l'assignation des licences aux utilisateurs
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_TOC
- commerce
ms.custom:
- AdminSurgePortfolio
- manage_licenses
search.appverid:
- MET150
description: Découvrez comment désattribuer des licences à des comptes d’utilisateurs.
ms.date: 07/01/2020
ms.openlocfilehash: 6fb07883fdfd4f4a837890e3e8c4c04b2411772b
ms.sourcegitcommit: 0d709e9ab0d8d56c5fc11a921298f82e40e122c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50114476"
---
# <a name="unassign-licenses-from-users"></a>Annuler l'assignation des licences aux utilisateurs

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).

::: moniker-end

::: moniker range="o365-worldwide"

Vous pouvez désattribuer des licences à des utilisateurs sur la page **Utilisateurs** actifs ou sur la page **Licences.** La méthode que vous utilisez varie selon que vous souhaitez soit désattribuer des licences de produits à des utilisateurs spécifiques, soit désattribuer des licences d’utilisateurs à partir d’un produit spécifique.

::: moniker-end

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur global, de licence, d’utilisateur pour désattribuer des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [supprimer des licences de comptes d'utilisateurs à l'aide d'Office 365 PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell).
- Vous pouvez également [supprimer les comptes d’utilisateurs](../add-users/delete-a-user.md) qui ont été affectés à une licence pour les rendre disponibles pour d’autres utilisateurs. Lorsque vous supprimez un compte d’utilisateur, sa licence est immédiatement disponible pour être assignée à une autre personne.

::: moniker range="o365-worldwide"

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Utiliser la page Licences pour désattribuer des licences

Lorsque vous utilisez la page **Licences** pour désattribuer des licences, vous désattribuez les licences d’un produit spécifique à 20 utilisateurs au plus.

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.
2. Sélectionnez le produit pour lequel vous souhaitez désattribuer des licences.
3. Sélectionnez les utilisateurs pour lesquels vous souhaitez désattribuer des licences.
4. Sélectionnez **Désattribuer des licences.**
5. In the **Unassign licenses** box, select **Unassign**.

::: moniker-end

::: moniker range="o365-worldwide"

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Utiliser la page Utilisateurs actifs pour désattribuer des licences

Lorsque vous utilisez la page **Utilisateurs actifs** pour désattribuer des licences, vous désattribuez des licences de produits aux utilisateurs.

### <a name="unassign-licenses-from-one-user"></a>Désattribuer des licences à un utilisateur
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la ligne de l’utilisateur pour qui vous souhaitez désattribuer une licence.
3. Dans le volet de droite, sélectionnez **Licences et applications**.
4. Développez la section **Licences,** désélectionnez les zones des licences que vous souhaitez désattribuer, puis sélectionnez **Enregistrer les modifications.**

::: moniker-end

::: moniker range="o365-germany"

## <a name="unassign-licenses-from-one-user"></a>Désattribuer des licences à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez l’utilisateur pour qui vous souhaitez désattribuer la licence.
3. Sur la droite, dans la ligne **Licences de produits,** sélectionnez **Modifier.**
4. Dans le **volet Licences de** produits, basculez vers la **position** d’arrêt de la licence que vous souhaitez désattribuer à l’utilisateur. Par exemple, si vous désaffectez la licence Office 365 Entreprise E3, elle désattribue cette licence et tous les services sous cette licence pour cet utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

## <a name="unassign-licenses-from-one-user"></a>Désattribuer des licences à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez l’utilisateur pour qui vous souhaitez désattribuer la licence.
3. Sur la droite, dans la ligne **Licences de produits,** sélectionnez **Modifier.**
4. Dans le **volet Licences de** produits, basculez vers la **position** d’arrêt de la licence que vous souhaitez désattribuer à l’utilisateur. Par exemple, si vous désaffectez la licence Office 365 Entreprise E3, elle désattribue cette licence et tous les services sous cette licence pour cet utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-worldwide"
###  <a name="unassign-licenses-from-multiple-users"></a>Désattribuer des licences à plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez les cercles en de côté des noms des utilisateurs pour qui vous souhaitez désattribuer des licences.
3. Dans la partie supérieure, sélectionnez **Plus d'options (...)**, puis choisissez **Gérer les licences de produits**.
4. Dans le volet **Gérer des licences de produits**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du  volet Remplacer les produits existants, cochez la case Supprimer toutes les licences de produits des **utilisateurs sélectionnés,** puis **sélectionnez Remplacer** \> **fermer.**

::: moniker-end

::: moniker range="o365-germany"

##  <a name="unassign-licenses-from-multiple-users"></a>Désattribuer des licences à plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez les cases en de côté des noms des utilisateurs pour qui vous souhaitez désattribuer toutes les licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Remplacer les produits existants**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du  volet Remplacer les produits **existants,** cochez la case Supprimer toutes les licences de produits de la case utilisateur sélectionnée, puis **sélectionnez** Remplacer \>  \> **fermer.**

::: moniker-end

::: moniker range="o365-21vianet"

##  <a name="unassign-licenses-from-multiple-users"></a>Désattribuer des licences à plusieurs utilisateurs
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez les cases en de côté des noms des utilisateurs pour qui vous souhaitez désattribuer toutes les licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Remplacer les produits existants**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du  volet Remplacer les produits **existants,** cochez la case Supprimer toutes les licences de produits de la case utilisateur sélectionnée, puis **sélectionnez** Remplacer \>  \> **fermer.**

::: moniker-end

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Qu’advient-il des données d’un utilisateur lorsque vous supprimez sa licence ?

- Lorsqu’une licence est supprimée d’un utilisateur, les données associées à ce compte sont détenues pendant 30 jours. Après la période de grâce de 30 jours, les données sont supprimées et ne peuvent pas être récupérées.
- Les fichiers enregistrés dans OneDrive Entreprise ne sont pas supprimés, sauf si l’utilisateur est supprimé du Centre d’administration Microsoft 365 ou supprimé via la synchronisation Active Directory. Pour plus d’informations, voir Rétention et [suppression de OneDrive.](https://docs.microsoft.com/onedrive/retention-and-deletion)
- Lorsque la licence est supprimée, la boîte aux lettres de l’utilisateur n’est plus utilisable dans une recherche à l’aide d’un outil eDiscovery tel que la recherche de contenu ou Advanced eDiscovery. Pour plus d’informations, voir « Recherche de boîtes aux lettres déconnectées ou déconnectées » dans la recherche de [contenu dans Microsoft 365.](https://docs.microsoft.com/microsoft-365/compliance/content-search#searching-disconnected-or-de-licensed-mailboxes)
- Si vous avez un abonnement Entreprise, comme Office 365 Entreprise E3, Exchange Online vous permet de conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé à l’aide de boîtes aux lettres [inactives.](https://docs.microsoft.com/microsoft-365/compliance/inactive-mailboxes-in-office-365) Pour plus d’informations, voir Créer et gérer des boîtes aux lettres [inactives dans Exchange Online.](https://docs.microsoft.com/microsoft-365/compliance/create-and-manage-inactive-mailboxes)
- Pour savoir comment bloquer l’accès d’un utilisateur aux données Microsoft 365 après la suppression de sa licence et comment accéder aux données par la suite, voir Supprimer un ancien [employé.](../add-users/remove-former-employee.md)
- Si vous supprimez la licence d’un utilisateur et que des applications Office sont toujours [installées,](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) les erreurs d’activation et de produit sans licence s’y sont installées lorsqu’ils utilisent des applications Office.

## <a name="next-steps"></a>Étapes suivantes

Si vous ne comptez pas réattribuer les licences inutilisées à d’autres [utilisateurs,](../../managed-desktop/get-started/assign-licenses.md)envisagez de supprimer les [licences](../../commerce/licenses/buy-licenses.md) de votre abonnement afin de ne pas payer plus de licences que nécessaire.

## <a name="related-content"></a>Contenu connexe

[Supprimer des licences de votre abonnement](../../commerce/licenses/remove-licenses-from-subscription.md) (article)\
[Attribuer des licences aux utilisateurs](assign-licenses-to-users.md) (article)\
[Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises](../../commerce/licenses/subscriptions-and-licenses.md) (article)