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
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
ms.date: 04/22/2022
ms.openlocfilehash: 23fc9ea04f45cdeb50acb0ec2d62d584974d6499
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043239"
---
# <a name="unassign-microsoft-365-licenses-from-users"></a>Annuler l’affectation de licences Microsoft 365 des utilisateurs

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

Lorsque vous utilisez la page **Licences** pour annuler l’attribution de licences, vous désattribuez des licences pour un produit spécifique pour jusqu’à 20 utilisateurs.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Sélectionnez le produit pour lequel vous souhaitez annuler l’affectation des licences.

3. Sélectionnez les utilisateurs pour lesquels vous souhaitez annuler l’attribution de licences.

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
- Les fichiers enregistrés dans OneDrive Entreprise ne sont pas supprimés, sauf si l’utilisateur est supprimé du Centre d'administration Microsoft 365 ou est supprimé via la synchronisation Active Directory. Pour plus d’informations, consultez [OneDrive rétention et suppression](/onedrive/retention-and-deletion).
- Lorsque la licence est supprimée, la boîte aux lettres de l’utilisateur ne peut plus faire l’objet d’une recherche à l’aide d’un outil eDiscovery tel que recherche de contenu ou eDiscovery (Premium). Pour plus d’informations, consultez « Recherche de boîtes aux lettres déconnectées ou déconnectées » dans [Recherche de contenu dans Microsoft 365](../../compliance/content-search.md).
- Si vous avez un abonnement Enterprise, comme Office 365 Entreprise E3, Exchange Online vous permet de conserver les données de boîte aux lettres d’un compte d’utilisateur supprimé à l’aide de [boîtes aux lettres inactives](../../compliance/inactive-mailboxes-in-office-365.md). Pour plus d’informations, consultez [Créer et gérer des boîtes aux lettres inactives dans Exchange Online](../../compliance/create-and-manage-inactive-mailboxes.md).
- Pour savoir comment bloquer l’accès d’un utilisateur à Microsoft 365 données après la suppression de sa licence et comment accéder aux données par la suite, consultez [Supprimer un ancien employé](../add-users/remove-former-employee.md).
- Si vous supprimez la licence d’un utilisateur et qu’il a toujours Office applications installées, il voit [des erreurs de produit et d’activation sans licence dans Office](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380) lorsqu’il utilise Office applications.

## <a name="next-steps"></a>Étapes suivantes

Si vous ne [réattribuez pas les licences inutilisées à d’autres utilisateurs](../../managed-desktop/get-started/assign-licenses.md), envisagez [de supprimer les licences de votre abonnement](../../commerce/licenses/buy-licenses.md) afin de ne pas payer plus de licences que nécessaire.

## <a name="related-content"></a>Contenu connexe

[Supprimer des licences de votre abonnement](../../commerce/licenses/buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](assign-licenses-to-users.md) (article)\
[Comprendre les abonnements et les licences dans Microsoft 365 pour les entreprises](../../commerce/licenses/subscriptions-and-licenses.md) (article)
