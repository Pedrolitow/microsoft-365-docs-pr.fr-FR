---
title: Annuler l'assignation des licences aux utilisateurs
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_smb
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: La méthode que vous utilisez pour désattribuer des licences de produit dépend de la désaffectation des licences d’utilisateurs spécifiques ou d’un produit spécifique.
ms.date: 07/12/2022
ms.openlocfilehash: 667cc1167bbb3f479b7aab6ab6066f8b7448d948
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68199898"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>Annuler l’affectation de licences Microsoft 365 aux utilisateurs

Vous pouvez désattribuer des licences d’utilisateurs sur la page **Utilisateurs actifs** ou sur la page **Licences** . La méthode que vous utilisez varie selon que vous souhaitez annuler l’affectation de licences de produits à des utilisateurs spécifiques ou désattribuer des licences utilisateur à partir d’un produit spécifique.

> [!NOTE]
>
> - En tant qu’administrateur, vous ne pouvez pas attribuer ou annuler des attributions de licences pour un abonnement d’achat en libre-service acheté par un utilisateur de votre organisation. Vous pouvez [prendre le contrôle d’un abonnement d’achat en libre-service](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription), puis attribuer ou annuler des attributions de licences.
>
> - Pour certains abonnements, vous ne pouvez annuler l’abonnement que pendant une période limitée après l’achat ou le renouvellement de votre abonnement. Si la fenêtre d’annulation est écoulée, désactiver la facturation périodique pour annuler l’abonnement à la fin de sa période.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être administrateur général, de licence et d’utilisateur pour annuler l’affectation des licences. Si vous souhaitez en savoir plus, consultez l’article [À propos des rôles d’administrateur Microsoft 365](../add-users/about-admin-roles.md).
- Vous pouvez [supprimer des licences de comptes d'utilisateurs à l'aide d'Office 365 PowerShell](../../enterprise/remove-licenses-from-user-accounts-with-microsoft-365-powershell.md).
- Vous pouvez également [supprimer les comptes d’utilisateur](../add-users/delete-a-user.md) auxquels une licence a été attribuée pour mettre leur licence à la disposition d’autres utilisateurs. Lorsque vous supprimez un compte d’utilisateur, sa licence est immédiatement disponible pour être attribuée à une autre personne.

## <a name="use-the-licenses-page-to-unassign-licenses"></a>Utiliser la page Licences pour annuler l’affectation des licences

La page **Licences** vous permet d’attribuer ou de désattribuer des licences pour jusqu’à 20 utilisateurs à la fois. La page affiche les produits que vous possédez, le nombre de licences disponibles pour chaque produit et le nombre de licences attribuées sur le nombre total de licences disponibles.

La page **Licences** affiche un total agrégé de licences pour tous les abonnements pour le même nom de produit. Par exemple, vous pouvez avoir un abonnement pour Microsoft 365 Business Premium qui a 5 licences et un autre abonnement qui a 8 licences pour le même produit. La page **Licences** indique que vous disposez d’un total de 13 licences pour Microsoft 365 Business Premium sur tous vos abonnements. Cela est différent de ce que vous voyez sur la page **Vos produits** , qui affiche une ligne pour chaque abonnement que vous possédez, même s’ils concernent le même produit.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Sélectionnez un produit.

3. Activez les cases à cocher des utilisateurs pour lesquels vous souhaitez annuler l’attribution de licences.

4. Sélectionnez **Annuler l’affectation des licences**.

5. Dans la zone **Annuler l’affectation des licences** , sélectionnez **Annuler l’affectation**.

## <a name="use-the-active-users-page-to-unassign-licenses"></a>Utiliser la page Utilisateurs actifs pour annuler l’affectation de licences

Lorsque vous utilisez la page **Utilisateurs actifs** pour annuler l’affectation de licences, vous désattribuez les licences de produit des utilisateurs.

### <a name="unassign-licenses-from-one-user"></a>Annuler l’affectation de licences d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez la ligne de l’utilisateur pour lequel vous souhaitez annuler l’attribution d’une licence.

3. Dans le volet de droite, sélectionnez **Licences et applications**.

4. Développez la section **Licences** , décochez les cases pour les licences que vous souhaitez désattribuer, puis **sélectionnez Enregistrer les modifications**.

### <a name="unassign-licenses-from-multiple-users"></a>Annuler l’affectation de licences à plusieurs utilisateurs

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez les cercles en regard des noms des utilisateurs pour lesquels vous souhaitez annuler l’attribution de licences.

3. Dans la partie supérieure, sélectionnez **Gérer des licences de produits**.

4. Dans le volet **Gérer les licences de produit** , sélectionnez **Annuler l’affectation de toutes les** > **modifications d’enregistrement**.

5. En bas du volet, sélectionnez **Terminé**.  

## <a name="what-happens-to-a-users-data-when-you-remove-their-license"></a>Qu’advient-il des données d’un utilisateur lorsque vous supprimez sa licence ?

- Lorsqu’une licence est supprimée d’un utilisateur, Exchange Online données associées à ce compte sont conservées pendant 30 jours. Après la période de grâce de 30 jours, les données sont supprimées et ne peuvent pas être récupérées. Toutefois, il est lié à la stratégie de rétention et le contenu qui correspond aux étiquettes de rétention est conservé pour la découverte.
- Les fichiers enregistrés dans OneDrive Entreprise ne sont pas supprimés, sauf si l’utilisateur est supprimé du Centre d'administration Microsoft 365 ou est supprimé via la synchronisation Active Directory. Pour plus d’informations, consultez [la rétention et la suppression de OneDrive](/onedrive/retention-and-deletion).
- Lorsque la licence est supprimée, la boîte aux lettres de l’utilisateur ne peut plus faire l’objet d’une recherche à l’aide d’un outil eDiscovery tel que recherche de contenu ou eDiscovery (Premium). Pour plus d’informations, consultez « Recherche de boîtes aux lettres déconnectées ou déconnectées » dans [Recherche de contenu dans Microsoft 365](../../compliance/content-search.md).
- Si vous disposez d’un abonnement Entreprise, comme Office 365 Entreprise E3, Exchange Online vous permet de conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé à l’aide de [boîtes aux lettres inactives](../../compliance/inactive-mailboxes-in-office-365.md). Pour plus d’informations, consultez [Créer et gérer des boîtes aux lettres inactives dans Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Pour savoir comment bloquer l’accès d’un utilisateur aux données Microsoft 365 après la suppression de sa licence et comment accéder aux données par la suite, consultez [Supprimer un ancien employé](../add-users/remove-former-employee.md).
- Si vous supprimez la licence d’un utilisateur et que les applications Office sont toujours installées, il voit [des erreurs de produit et d’activation sans licence dans Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) lorsqu’il utilise des applications Office.

## <a name="next-steps"></a>Prochaines étapes

Si vous ne [réattribuez pas les licences inutilisées à d’autres utilisateurs](assign-licenses-to-users.md), envisagez [de supprimer les licences de votre abonnement](../../commerce/licenses/buy-licenses.md) afin de ne pas payer plus de licences que nécessaire.

## <a name="related-content"></a>Contenu associé

[Supprimer des licences de votre abonnement](../../commerce/licenses/buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](assign-licenses-to-users.md) (article)\
[Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises](../../commerce/licenses/subscriptions-and-licenses.md) (article)
