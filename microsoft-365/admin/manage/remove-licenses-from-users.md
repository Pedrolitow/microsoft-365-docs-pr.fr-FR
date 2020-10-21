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
description: Découvrez comment désaffecter des licences à partir de comptes d’utilisateurs.
ms.date: 07/01/2020
ms.openlocfilehash: 455348e7dba20913e54e5a4059755f9391644e03
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48645094"
---
# <a name="unassign-licenses-from-users"></a>Annuler l'assignation des licences aux utilisateurs

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

::: moniker range="o365-worldwide"

Vous pouvez annuler l’affectation de licences aux utilisateurs sur la page **utilisateurs actifs** ou sur la page **licences** . La méthode que vous utilisez varie selon que vous souhaitez annuler l’affectation de licences de produit à des utilisateurs spécifiques ou désaffecter des licences d’utilisateurs d’un produit spécifique.

::: moniker-end

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être un administrateur général, une licence et un administrateur d’utilisateur pour annuler l’affectation des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [supprimer des licences de comptes d'utilisateurs à l'aide d'Office 365 PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell).
- Vous pouvez également [supprimer des comptes d’utilisateurs](../add-users/delete-a-user.md) auxquels une licence a été attribuée afin de mettre leur licence à la disposition d’autres utilisateurs. Lorsque vous supprimez un compte d’utilisateur, sa licence est immédiatement disponible pour l’attribuer à une autre personne.

::: moniker range="o365-worldwide"

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Utilisation de la page licences pour annuler l’affectation des licences

Lorsque vous utilisez la page **licences** pour annuler l’affectation des licences, vous désaffectez les licences d’un produit spécifique pour un maximum de 20 utilisateurs.

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.
2. Sélectionnez le produit pour lequel vous souhaitez annuler l’affectation des licences.
3. Sélectionnez les utilisateurs pour lesquels vous souhaitez annuler l’affectation des licences.
4. Sélectionnez **Annuler l’affectation des licences**.
5. Dans la zone **désaffecter les licences** , sélectionnez **Annuler l’affectation**.

::: moniker-end

::: moniker range="o365-worldwide"

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Utiliser la page utilisateurs actifs pour annuler l’affectation des licences

Lorsque vous utilisez la page **utilisateurs actifs** pour annuler l’affectation des licences, vous désaffectez les licences de produits aux utilisateurs.

### <a name="unassign-licenses-from-one-user"></a>Désaffecter des licences d’un utilisateur
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la ligne de l’utilisateur pour lequel vous souhaitez annuler l’affectation d’une licence.
3. Dans le volet de droite, sélectionnez **Licences et applications**.
4. Développez la section **licences** , désactivez les cases à cocher correspondant aux licences que vous souhaitez annuler, puis sélectionnez **enregistrer les modifications**.

::: moniker-end

::: moniker range="o365-germany"

## <a name="unassign-licenses-from-one-user"></a>Désaffecter des licences d’un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez l’utilisateur pour lequel vous souhaitez annuler l’affectation de la licence.
3. À droite, dans la ligne **licences de produit** , sélectionnez **modifier**.
4. Dans le volet **licences de produits** , **désactivez** le bouton bascule correspondant à la licence que vous souhaitez annuler. Par exemple, si vous désactivez la licence Office 365 entreprise E3, il annule l’affectation de cette licence et de tous les services sous cette licence pour cet utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-21vianet"

## <a name="unassign-licenses-from-one-user"></a>Désaffecter des licences d’un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez l’utilisateur pour lequel vous souhaitez annuler l’affectation de la licence.
3. À droite, dans la ligne **licences de produit** , sélectionnez **modifier**.
4. Dans le volet **licences de produits** , **désactivez** le bouton bascule correspondant à la licence que vous souhaitez annuler. Par exemple, si vous désactivez la licence Office 365 entreprise E3, il annule l’affectation de cette licence et de tous les services sous cette licence pour cet utilisateur.
5. En bas du volet **Licences de produits**, sélectionnez **Enregistrer** \> **Fermer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-worldwide"
###  <a name="unassign-licenses-from-multiple-users"></a>Désaffecter les licences de plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez les cercles en regard des noms des utilisateurs pour lesquels vous souhaitez annuler l’affectation de licences.
3. Dans la partie supérieure, sélectionnez **Plus d'options (...)**, puis choisissez **Gérer les licences de produits**.
4. Dans le volet **Gérer des licences de produits**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du volet **remplacer les produits existants** , activez la case à cocher **supprimer toutes les licences de produits des utilisateurs sélectionnés** , puis sélectionnez **remplacer** \> **Fermer**.

::: moniker-end

::: moniker range="o365-germany"

##  <a name="unassign-licenses-from-multiple-users"></a>Désaffecter les licences de plusieurs utilisateurs

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.
2. Activez les cases à cocher en regard des noms des utilisateurs pour lesquels vous souhaitez annuler l’affectation de toutes les licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Remplacer les produits existants**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du volet **remplacer les produits existants** , activez la case à cocher **supprimer toutes les licences de produits des utilisateurs sélectionnés** , puis sélectionnez **remplacer** \> **le fermer** \> **Close**.

::: moniker-end

::: moniker range="o365-21vianet"

##  <a name="unassign-licenses-from-multiple-users"></a>Désaffecter les licences de plusieurs utilisateurs
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.
2. Activez les cases à cocher en regard des noms des utilisateurs pour lesquels vous souhaitez annuler l’affectation de toutes les licences.
3. Dans le volet **Actions en bloc**, sélectionnez **Modifier les licences de produits**.
4. Dans le volet **Remplacer les produits existants**, sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.
5. En bas du volet **remplacer les produits existants** , activez la case à cocher **supprimer toutes les licences de produits des utilisateurs sélectionnés** , puis sélectionnez **remplacer** \> **le fermer** \> **Close**.

::: moniker-end

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Qu’arrive-t-il aux données d’un utilisateur lorsque vous supprimez sa licence ?

- Lorsqu’une licence est supprimée d’un utilisateur, les données associées à ce compte sont conservées pendant 30 jours. Après la période de grâce de 30 jours, les données sont supprimées et ne peuvent pas être récupérées.
- Les fichiers enregistrés dans OneDrive entreprise ne sont pas supprimés, sauf si l’utilisateur est supprimé du centre d’administration 365 de Microsoft ou s’il est supprimé par le biais de la synchronisation Active Directory. Pour plus d’informations, consultez la rubrique [OneDrive Retention and suppression](https://docs.microsoft.com/onedrive/retention-and-deletion).
- Lorsque la licence est supprimée, la boîte aux lettres de l’utilisateur ne peut plus faire l’objet d’une recherche à l’aide d’un outil eDiscovery tel que la recherche de contenu ou Advanced eDiscovery. Pour plus d’informations, consultez la rubrique « recherche de boîtes aux lettres déconnectées ou sous licence » dans [recherche de contenu dans Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/content-search#searching-disconnected-or-de-licensed-mailboxes).
- Si vous disposez d’un abonnement Enterprise, comme Office 365 entreprise E3, Exchange Online vous permet de conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé en utilisant des [boîtes aux lettres inactives](https://docs.microsoft.com/microsoft-365/compliance/inactive-mailboxes-in-office-365). Pour plus d’informations, consultez la rubrique [créer et gérer des boîtes aux lettres inactives dans Exchange Online](https://docs.microsoft.com/microsoft-365/compliance/create-and-manage-inactive-mailboxes).
- Pour en savoir plus sur la façon de bloquer l’accès d’un utilisateur aux données Microsoft 365 après la suppression de leur licence et la façon d’y accéder par la suite, consultez la rubrique [supprimer un ancien employé](../add-users/remove-former-employee.md).
- Si vous supprimez la licence d’un utilisateur et que les applications Office sont toujours installées, les [Erreurs de produit et d’activation sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) s’affichent dans Office lorsqu’elles utilisent les applications Office.

## <a name="next-steps"></a>Étapes suivantes

Si vous ne souhaitez pas [réaffecter les licences inutilisées à d’autres utilisateurs](../../managed-desktop/get-started/assign-licenses.md), envisagez [de supprimer les licences de votre abonnement](../../commerce/licenses/buy-licenses.md) afin de ne pas payer plus de licences que vous n’en avez besoin.

## <a name="related-content"></a>Contenu connexe

[Supprimer des licences de votre abonnement](../../commerce/licenses/remove-licenses-from-subscription.md) (article) \
[Attribuer des licences aux utilisateurs](assign-licenses-to-users.md) (article) \
[Comprendre les abonnements et les licences dans Microsoft 365 for Business](../../commerce/licenses/subscriptions-and-licenses.md) (article)