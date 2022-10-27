---
title: Passer en revue les privilèges d’administration des partenaires
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- empty
search.appverid: MET150
description: Découvrez comment consulter votre liste de fournisseurs de solutions certifiés Microsoft (partenaires) pour déterminer les privilèges d’administrateur dont ils disposent et comment supprimer ces privilèges.
ms.date: 12/03/2021
ms.openlocfilehash: 67cafa9ebac7f641de43f0debab733d89a8b1853
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718301"
---
# <a name="review-microsoft-certified-cloud-solution-provider-partner-administrative-privileges"></a>Passez en revue les privilèges d’administration des partenaires du fournisseur de solutions cloud certifiés Microsoft

Si vous disposez d’un fournisseur de solutions cloud certifié Microsoft (partenaire revendeur), nous vous recommandons d’effectuer un examen trimestriel des privilèges d’administration délégués (DAP) qui lui sont attribués. Assurez-vous que votre organisation souhaite que ce partenaire ait accès aux données de votre organisation et effectue des achats en votre nom.

> [!IMPORTANT]
> L’octroi d’un DAP, qui inclut des autorisations d’administrateur général, à n’importe quel partenaire peut présenter un risque pour la sécurité. Le fait d’avoir un trop grand nombre d’administrateurs généraux constitue également un risque pour la sécurité. [En savoir plus sur l’activité récente ciblant les privilèges délégués](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Une fois que vous avez accepté un contrat DAP d’un partenaire revendeur, celui-ci peut attribuer le rôle d’administrateur général pour votre organisation à ses employés. Le rôle d’administrateur général permet aux employés du partenaire d’accéder aux données personnelles de vos employés et à d’autres informations sensibles. Il leur donne également l’autorisation d’effectuer des actions à l’échelle du locataire, telles que les actions suivantes :

- Modification des mots de passe utilisateur
- Ajout d’utilisateurs avec des comptes de messagerie
- Ajout et gestion de domaines web associés à votre organisation

Lorsque DAP est activé, vous n’avez aucun contrôle sur le nombre d’administrateurs généraux que votre partenaire peut ajouter. Vous pouvez uniquement accorder ou refuser l’accès d’administrateur général (DAP) partenaire à votre compte.

## <a name="review-and-remove-roles-from-partners"></a>Examiner et supprimer des rôles des partenaires

1. Dans la Centre d'administration Microsoft 365, accédez à la page **Paramètres** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Relations avec les partenaires</a>. Les partenaires avec DAP ont **l’administrateur général** répertorié dans la colonne **Rôles** .
2. Pour supprimer le rôle d’administrateur général d’un partenaire, recherchez le nom du partenaire que vous souhaitez supprimer.
3. Sélectionnez la ligne avec **Reseller** comme Type de **relation**.
4. Dans la page des détails du partenaire, sélectionnez **Supprimer les rôles**, puis **Oui**.

> [!NOTE]
>
> - Si vous supprimez DAP (rôle d’administrateur général) d’un partenaire, nous vous recommandons de le contacter pour discuter de la livraison future des services. Par exemple, vous pouvez créer un compte d’utilisateur avec des privilèges inférieurs et partager les informations de ce compte avec votre partenaire. En savoir plus sur [l’ajout d’utilisateurs](../admin/add-users/add-users.md) et [l’attribution de rôles d’administrateur](../admin/add-users/assign-admin-roles.md).
> - Même si le rôle d’administrateur général a été supprimé, le partenaire peut toujours effectuer des achats en votre nom. Nous vous recommandons de contacter le partenaire pour lui demander de supprimer cette fonctionnalité dans l’Espace partenaires.

## <a name="related-content"></a>Contenu associé

[Gérer les relations avec les partenaires](manage-partners.md) (article)\
[À propos des rôles d’administrateur](../admin/add-users/about-admin-roles.md) (article)\
[Privilèges d’administrateur délégués dans Azure AD](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (article)
