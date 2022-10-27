---
title: Gérer la facturation entre plusieurs locataires dans le Centre d'administration Microsoft 365
f1.keywords: NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
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
- commerce_billing
search.appverid: MET150
description: Découvrez comment utiliser des relations de facturation multilocataires pour partager des comptes de facturation entre locataires dans le Centre d'administration Microsoft 365.
ms.date: 08/15/2022
ms.openlocfilehash: 03e0f16f8f457ef95b6161a15078ba5374027476
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720303"
---
# <a name="manage-billing-across-multiple-tenants-in-the-microsoft-365-admin-center"></a>Gérer la facturation entre plusieurs locataires dans le Centre d'administration Microsoft 365

Vous pouvez simplifier la gestion de la facturation pour votre organisation en créant des relations de facturation multilocataires avec d’autres locataires. Une relation de facturation multilocataire vous permet de partager en toute sécurité le compte de facturation de votre organisation avec d’autres locataires, tout en conservant le contrôle de vos données de facturation. Vous pouvez créer des abonnements dans différents locataires et fournir aux utilisateurs de ces locataires l’accès au compte de facturation de votre organisation. Cette relation permet aux utilisateurs de ces locataires d’effectuer des activités de facturation telles que l’affichage et le téléchargement des factures ou la gestion des licences.

> [!IMPORTANT]
> Cet article s’applique uniquement aux clients de comptes d’organisation disposant d’un Contrat client Microsoft.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être propriétaire du compte de facturation pour effectuer les tâches décrites dans cet article. Pour plus d’informations, consultez [Comprendre vos comptes de facturation Microsoft](../manage-billing-accounts.md).

## <a name="decide-which-billing-tenant-solution-is-right-for-your-organization"></a>Déterminer la solution de locataire de facturation qui convient à votre organisation

Choisir de configurer plusieurs locataires de facturation peut être la bonne approche, en fonction des besoins de votre organisation. Le tableau suivant compare l’utilisation d’une approche monolocataire ou multilocataire pour vous aider à déterminer quelle approche convient à votre organisation.

| **Pour cette zone de facturation**   | **Envisagez d’utiliser des comptes de facturation monolocataire si :**  | **Envisagez d’utiliser plusieurs locataires qui partagent un seul compte de facturation si :**  |
|-----------------------------|--------------------------------------------------------|------------------------------------------------------------------------------|
| **Facturation**               | Vous souhaitez que les achats effectués par différents comptes de facturation soient toujours dans des factures différentes.    | Vous souhaitez que les achats effectués par des utilisateurs de différents locataires soient sur la même facture ou sur des factures différentes, selon votre choix.  |
| **Gestion de vos achats** | Vous souhaitez que les abonnements soient créés uniquement dans le locataire dans lequel ils sont achetés.   | Vous souhaitez que les abonnements achetés dans un locataire soient créés dans un autre locataire qui partage le même compte de facturation.  |
| **Contrats**              | Vous souhaitez que chaque compte de facturation de son propre locataire signe son propre contrat avec Microsoft. Les conditions d’achat des affiliés clients (CAPT) peuvent définir des contrats d’affiliation entre différents comptes de facturation sur des locataires uniques.  | Vous souhaitez que les contrats soient signés par un seul compte de facturation et que les mêmes contrats s’appliquent à tous les locataires qui partagent le compte de facturation. |
| **Tarification et remises**   | Vous ne souhaitez pas que les remises soient partagées entre plusieurs comptes de facturation, sauf si ces comptes partagent des conditions CAPT.  | Vous souhaitez appliquer des remises sur un compte de facturation, quel que soit le locataire sur lequel un utilisateur effectue un achat ou où les abonnements sont créés en raison du partage d’un contrat. |
| **Visibility**              | Vous souhaitez uniquement que les utilisateurs d’un compte de facturation aient une visibilité sur ce qui se trouve dans ce compte de facturation, et non sur ce qui se trouve sur un autre locataire. Par exemple, vous souhaitez uniquement que les utilisateurs affichent les coûts et les factures, achètent des produits et effectuent le suivi des paiements pour leur propre locataire. | Vous souhaitez que les utilisateurs disposant de comptes de facturation partagés aient la même vue du compte de facturation, quel que soit le locataire dans lequel ils se trouvent. |
| **Sécurité**                | Vous souhaitez que tous les utilisateurs ayant accès à votre compte de facturation suivent les stratégies de sécurité de votre locataire.  | Vous souhaitez que les utilisateurs que vous avez invités à partager votre compte de facturation suivent les stratégies de sécurité de leur propre locataire. |

## <a name="what-are-the-types-of-tenants-in-a-multi-tenant-billing-relationship"></a>Quels sont les types de locataires dans une relation de facturation multilocataire ?

Il existe deux types de locataires dans un scénario de facturation multilocataire :

1. **Locataire de facturation principal** : le locataire de facturation principal est le locataire utilisé lors de la configuration du compte de facturation. Par défaut, tous les abonnements sont achetés dans ce locataire et seuls les utilisateurs de ce locataire peuvent accéder au compte de facturation.
2. **Locataire de facturation associé** : un locataire de facturation associé est un locataire lié au compte de facturation de votre locataire de facturation principal. Ces locataires peuvent acheter des abonnements à l’aide de votre compte de facturation ou accepter des abonnements de votre part. Vous pouvez également attribuer des rôles de compte de facturation aux utilisateurs d’un locataire de facturation associé.

## <a name="what-access-settings-are-available-for-associated-billing-tenants"></a>Quels sont les paramètres d’accès disponibles pour les locataires de facturation associés ?

Lorsque vous ajoutez un locataire de facturation associé à votre compte de facturation, vous pouvez activer un ou les deux paramètres d’accès suivants.

- **L’approvisionnement** permet de créer des abonnements dans les locataires de facturation associés.
- **La gestion de la facturation** permet aux propriétaires de comptes de facturation d’attribuer des rôles aux utilisateurs d’un locataire de facturation associé, en leur donnant l’autorisation d’accéder aux informations de facturation et de prendre des décisions d’achat.

## <a name="add-an-associated-billing-tenant"></a>Ajouter un locataire de facturation associé

Avant de commencer, vérifiez que vous disposez de l’ID de locataire ou du nom de domaine principal du locataire que vous souhaitez inviter. Pour plus d’informations, consultez [Rechercher un ID de locataire ou un nom de domaine](https://aka.ms/findtenantiddomain).

1. Dans le Centre d’administration, accédez à la page **Comptes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">facturation</a> .
2. Sélectionnez le nom du compte de facturation que vous souhaitez utiliser comme locataire de facturation principal.
3. Dans la page détails du compte de facturation, sélectionnez l’onglet **Locataires de facturation associés** , puis **sélectionnez Ajouter un locataire de facturation associé**.
4. Dans le volet **Ajouter un** **locataire de facturation associé** , entrez l’ID de locataire ou le nom de domaine, puis entrez un nom convivial pour le locataire.
5. Dans la section **Paramètres d’accès** , sélectionnez une ou les deux options pour **l’approvisionnement** et **la gestion de la facturation**.
6. Lisez et sélectionnez la case en regard de l’instruction de visibilité de l’utilisateur.
7. Sélectionnez **Ajouter un locataire**.

Si le paramètre **d’accès** à l’approvisionnement est activé, un lien unique est créé pour vous permettre de l’envoyer à l’administrateur général sur le locataire de facturation associé. Ils doivent accepter la demande avant de pouvoir déplacer des abonnements vers leur locataire.

## <a name="assign-roles-to-users-from-the-associated-billing-tenant-optional"></a>Attribuer des rôles aux utilisateurs à partir du locataire de facturation associé (facultatif)

1. Dans le Centre d’administration, accédez à la page **Comptes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">facturation</a> .
2. Sélectionnez le nom du compte de facturation à attribuer des rôles.
3. Dans la page détails du compte de facturation, sélectionnez l’onglet **Rôles de compte de facturation** , puis sélectionnez **Attribuer des rôles.**
4. Dans le volet **Attribuer un rôle** , recherchez le locataire de facturation associé, sélectionnez un rôle, puis entrez l’adresse e-mail des utilisateurs auxquels vous souhaitez attribuer un rôle.
5. Sélectionnez **Attribuer.**

L’utilisateur reçoit un e-mail avec un lien pour passer en revue la demande d’attribution de rôle. Une fois qu’ils ont accepté le rôle, ils ont accès à votre compte de facturation. Pour plus d’informations sur les rôles de compte de facturation, consultez [Comprendre vos comptes de facturation Microsoft](../manage-billing-accounts.md).

> [!IMPORTANT]
> Tout utilisateur disposant d’un rôle dans le compte de facturation peut voir tous les utilisateurs de tous les locataires qui ont accès à ce compte de facturation. Par exemple, si Contoso.com est le locataire de facturation principal et qu’un propriétaire de compte de facturation ajoute Fabrikam.com en tant que locataire de facturation associé, puis ajoute Katarina en tant que propriétaire du compte de facturation, Katarina peut voir tous les utilisateurs qui ont accès au compte de facturation sur Contoso.com et Fabrikam.com.

## <a name="move-subscriptions-to-an-associated-billing-tenant-optional"></a>Déplacer des abonnements vers un locataire de facturation associé (facultatif)

L’administrateur général du locataire de facturation associé doit accepter la demande d’approvisionnement du locataire de facturation principal avant de pouvoir déplacer des abonnements vers son locataire de facturation associé.

> [!IMPORTANT]
> Vous ne pouvez déplacer un abonnement vers un locataire de facturation associé que si toutes les licences de l’abonnement sont disponibles. Si des licences sont attribuées, vous ne pouvez pas déplacer l’abonnement.

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.
2. Sélectionnez le nom du produit que vous souhaitez déplacer vers le locataire de facturation associé.
3. Dans la page détails du produit, dans la section **Licences attribuées à partir de tous les abonnements** , sélectionnez **Déplacer vers un autre locataire**.
4. Dans le volet **Déplacer l’abonnement vers un autre locataire** , recherchez un nom de locataire ou sélectionnez un locataire dans la liste, puis sélectionnez **Déplacer** **l’abonnement**.

## <a name="remove-an-associated-billing-tenant"></a>Supprimer un locataire de facturation associé

La suppression d’un locataire de facturation associé est une action permanente qui ne peut pas être annulée. L’accès est supprimé pour tous les utilisateurs clients auxquels des rôles sont attribués sur votre compte de facturation, et vous ne pouvez plus déplacer d’abonnements vers le locataire. Les abonnements qui ont déjà été déplacés restent avec le locataire et sont toujours facturés à votre compte de facturation.

1. Dans le Centre d’administration, accédez à la page **Comptes de** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">facturation</a> .
2. Sélectionnez le nom du compte de facturation qui est le locataire de facturation principal.
3. Dans la page détails du compte de facturation, sélectionnez l’onglet **Locataires de facturation associés** .
4. Sélectionnez le locataire de facturation associé que vous souhaitez supprimer.
5. Dans le volet client de facturation associé, sélectionnez **Supprimer l’accès.**
6. Dans le volet Supprimer **l’accès** à **la gestion de l’approvisionnement et de la facturation**, sélectionnez **Supprimer l’accès.**
7. Dans la boîte de dialogue de confirmation, sélectionnez **Oui**.

## <a name="accept-or-decline-an-invitation-for-provisioning-access-to-your-associated-billing-tenant"></a>Accepter ou refuser une invitation pour l’approvisionnement de l’accès à votre locataire de facturation associé

En tant qu’administrateur général d’un locataire de facturation associé, vous pouvez accepter ou refuser une demande du propriétaire du compte de facturation pour créer des abonnements dans votre locataire. Lorsqu’un propriétaire de compte de facturation ajoute votre locataire en tant que locataire de facturation associé et active le paramètre **d’accès Provisionnement** , vous recevez un lien du propriétaire du compte de facturation pour accepter ou refuser l’invitation.

1. Sélectionnez le lien partagé par le propriétaire du compte de facturation.
2. Dans la page **Invitation à être un locataire de facturation associé** , sélectionnez **Accepter** ou **Refuser**.

> [!NOTE]
> Si vous décidez ultérieurement de révoquer l’accès **provisionnement** , vous pouvez utiliser le même lien.

## <a name="related-articles"></a>Articles connexes

[Comprendre vos comptes de facturation Microsoft](../manage-billing-accounts.md) (article)\
[Comprendre les profils de facturation](manage-billing-profiles.md) (article)
