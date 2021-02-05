---
title: Gestion des modes de paiement
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
ms.custom:
- TopSMBIssues
- okr_SMB
- AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez comment gérer vos modes de paiement dans le Centre d’administration Microsoft 365.
ms.date: ''
ms.openlocfilehash: 6cba5e33ba99212cb6e67a90d1535120ccac3c38
ms.sourcegitcommit: 0d709e9ab0d8d56c5fc11a921298f82e40e122c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "50114848"
---
# <a name="manage-payment-methods"></a>Gestion des modes de paiement

::: moniker range="o365-21vianet"
> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet&preserve-view=true).
::: moniker-end

Lorsque vous achetez des produits ou services professionnels auprès de Microsoft, vous pouvez utiliser un mode de paiement existant ou en ajouter un nouveau. Vous pouvez utiliser une carte de crédit ou de débit, ou un compte bancaire pour payer les achats.

Si votre compte d’entreprise possède un profil de facturation et que vous êtes propriétaire du profil de facturation ou collaborateur de profil de facturation, vous pouvez utiliser le profil de facturation qui est dosé par une carte bancaire ou un paiement par facture pour effectuer des achats ou payer des factures. Si vous êtes gestionnaire de factures, vous pouvez uniquement utiliser un profil de facturation pour payer les factures. Pour en savoir plus sur les profils de facturation et les rôles, voir [Gérer les profils de facturation.](manage-billing-profiles.md)

Si votre compte d’entreprise n’a pas de profil de facturation, tout administrateur global ou de facturation peut gérer et utiliser n’importe quel compte bancaire ajouté au compte d’entreprise. Toutefois, vous pouvez uniquement gérer ou utiliser des cartes de crédit que vous ajoutez.

> [!NOTE]
> L’option de paiement avec un compte bancaire n’est pas disponible dans certains pays ou régions.
>
> Vous devez utiliser un mode de paiement émis à partir du même pays que votre client.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur global ou un administrateur de facturation pour effectuer les tâches de cet article. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="add-a-payment-method"></a>Ajouter un mode de paiement

L’ajout d’un mode de paiement n’associe aucun abonnement à ce mode. Pour affecter un abonnement unique au mode de paiement, voir Modifier un mode de [paiement pour un abonnement unique.](#change-a-payment-method-for-a-single-subscription) Pour remplacer tous les abonnements qui utilisent un autre mode de paiement par le nouveau, voir [Remplacer un mode de paiement.](#replace-a-payment-method)

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez **Ajouter ou sélectionner un mode de paiement**.
3. Sur la page **Modes de paiement**, sélectionnez un mode de paiement dans le menu déroulant.
4. Entrez les informations de la nouvelle carte ou du nouveau compte bancaire, puis sélectionnez **Ajouter.**

## <a name="update-payment-method-details"></a>Mettre à jour les informations sur le mode de paiement

Vous pouvez modifier le nom sur la carte de crédit ou de débit, l’adresse de facturation ou la date d’expiration d’un mode de paiement existant. Toutefois, vous ne pouvez pas modifier la carte ou le numéro de compte. Si le numéro de compte a changé, remplacez-le par un [autre](#replace-a-payment-method)mode de paiement, puis [supprimez l’ancien.](#delete-a-payment-method)

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à mettre à jour. Dans le volet droit, sélectionnez **Modifier**.
3. Mettez à jour les informations relatives au mode de paiement, notamment le nom figurant sur la carte de crédit ou de débit, l’adresse de facturation ou la date d’expiration, puis sélectionnez **Enregistrer**.

## <a name="replace-a-payment-method"></a>Remplacer un mode de paiement

Lorsque vous remplacez un mode de paiement, vous le remplacez pour tous les abonnements et profils de facturation qui utilisent le même mode de paiement. Le remplacement d’un mode de paiement ne supprime pas le mode de paiement existant. Vous pouvez toujours le sélectionner et l’utiliser pour d’autres abonnements et profils de facturation.

Pour modifier le mode de paiement d’un abonnement unique, voir Modifier un mode de [paiement pour un abonnement unique.](#change-a-payment-method-for-a-single-subscription)

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à changer. Le volet droit répertorie tous les profils de facturation et les abonnements individuels qui utilisent le moyen de paiement sélectionné.
3. Dans le volet droit, sélectionnez **Changer le mode de paiement pour tous les éléments**.
4. Pour utiliser un mode de paiement existant, choisissez-le dans la liste déroulante, puis sélectionnez **Remplacer**.
    > [!NOTE]
    > Si vous avez des abonnements associés à un profil de facturation, vous pouvez uniquement utiliser une carte de débit ou de crédit pour les régler. Si vous avez des comptes bancaires répertoriés sur la page **Modes de paiement**, vous ne pouvez pas les sélectionner dans la liste déroulante.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Dans le volet **Ajouter un mode de paiement**, entrez les informations de compte, puis sélectionnez **Enregistrer**. Vous devez utiliser un mode de paiement provenant du même pays que celui de votre client.
7. Le nouveau mode de paiement est déjà sélectionné dans la liste déroulante. Sélectionnez **Remplacer**.

## <a name="change-a-payment-method-for-a-single-subscription"></a>Modifier un mode de paiement pour un abonnement unique

Vous pouvez modifier le mode de paiement utilisé pour payer un abonnement unique.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, recherchez l’abonnement que vous souhaitez payer avec l’autre mode de paiement.
3. Sélectionnez **Plus d’actions** (trois points), puis **sélectionnez Remplacer le mode de paiement.**
4. Dans le volet Remplacer **le mode** de paiement, dans la liste de listes, choisissez un autre mode de paiement ou ajoutez un mode de paiement.
5. Si vous ajoutez un mode de paiement, entrez les détails de la carte ou du compte, puis sélectionnez **Enregistrer**.
6. Vérifiez que le mode de paiement sélectionné est correct, puis sélectionnez **Remplacer.**

## <a name="delete-a-payment-method"></a>Supprimer un mode de paiement

Vous pouvez uniquement supprimer un mode de paiement qui n’est pas attaché à un profil d’abonnement ou de facturation. Cela s’applique à tous les abonnements, quel que soit leur état.

### <a name="delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement sans abonnement ni profil de facturation associé

Si un mode de paiement n’est associé à aucun abonnement ou profil de facturation, vous pouvez immédiatement le supprimer.

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Recherchez le mode de paiement à supprimer, sélectionnez les trois points, puis sélectionnez **Supprimer.**
3. En bas du volet droit, sélectionnez **Supprimer.**

### <a name="delete-a-payment-method-with-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement avec des abonnements ou des profils de facturation associés

Si un mode de paiement est associé à des abonnements ou à des profils de facturation, remplacez-le d’abord par un mode de paiement existant, ou ajoutez-en un nouveau, puis supprimez l’ancien mode de paiement.

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à supprimer. Le volet droit répertorie les abonnements existants qui utilisent ce mode de paiement.
3. Dans le volet droit, sélectionnez **Supprimer.**
4. Pour utiliser un mode de paiement existant, choisissez-en un dans la liste de listes, sélectionnez **Suivant,** puis **Supprimez.**
    > [!NOTE]
    > Si vous avez des abonnements associés à un profil de facturation, vous pouvez uniquement utiliser une carte de crédit pour les payer. Si vous avez des comptes bancaires répertoriés dans la **page** Modes de paiement, ils ne sont pas disponibles dans la liste de listes.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Choisissez le type de mode de paiement que vous souhaitez ajouter, entrez les informations de compte, puis sélectionnez **Enregistrer**.
7. Le nouveau mode de paiement est déjà sélectionné dans la liste déroulante. Sélectionnez **Suivant**.
8. Sélectionnez **Supprimer**.

## <a name="troubleshoot-payment-methods"></a>Résolution des problèmes des modes de paiement

| Problème | Étapes de dépannage |
|:----------|:-----|
|**Je reçois un message d’erreur qui indique que le navigateur est actuellement prêt à bloquer les cookies.** |Configurez votre navigateur pour autoriser les cookies tiers, puis réessayez. |
|**Ma carte de crédit ou de débit a été refusée.** |Si vous payez par carte de crédit ou de débit et que votre carte est refusée, vous recevez un courrier électronique qui indique que Microsoft n’a pas pu traiter le paiement. Vérifiez que le numéro de carte, la date d’expiration, le nom de la carte et l’adresse, y compris la ville, l’état et le code POSTAL, apparaissent exactement comme sur la carte et votre &mdash; &mdash; instruction. Vous pouvez mettre à jour vos informations de carte et envoyer immédiatement le paiement en utilisant le lien Régler le **solde** dans la **section** Facturation de la page détails de l’abonnement. Pour plus d’informations, [voir Que se passe-t-il si j’ai un solde en suspens ?](pay-for-your-subscription.md#what-if-i-have-an-outstanding-balance)  <br/><br/>  Si vous obtenez toujours le message de refus de la carte bancaire, contactez votre banque. Il est possible que votre carte ne soit pas active. Si vous avez récemment reçu la carte par courrier électronique avec une date d’expiration mise à jour, assurez-vous qu’elle est activée. Votre banque peut également vous indiquer si votre carte n’est pas approuvée pour les transactions en ligne, internationales ou récurrentes. |
|**Je souhaite mettre à jour un numéro de carte ou de compte bancaire.** |Vous ne pouvez pas modifier la carte ou le numéro de compte sur un mode de paiement existant. Si votre carte ou votre numéro de compte [a](#replace-a-payment-method)changé, remplacez-le par un autre mode de paiement, qui déplace tous les abonnements actifs du mode de paiement vers le nouveau, puis supprimez l’ancien mode de [paiement.](#delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached) |
|**Je n’ai qu’une carte ou un compte bancaire sur mon compte et je souhaite la supprimer.** |Si vous n’avez qu’un seul mode de paiement, vous devez le remplacer par [un nouveau](#replace-a-payment-method) mode de paiement avant de pouvoir le supprimer. |
|**Je ne peux pas ajouter ma carte ou mon compte bancaire.**  |Vous devez utiliser un mode de paiement émis à partir du même pays que votre client. Si vous avez des difficultés à entrer vos informations de carte ou de compte bancaire, vous pouvez contacter [le support technique.](../../admin/contact-support-for-business-products.md) |

## <a name="related-content"></a>Contenu connexe

[Payer votre abonnement commercial](pay-for-your-subscription.md) (article)\
[Gérer les profils de](manage-billing-profiles.md) facturation (article)\
[Modifier votre fréquence de facturation](change-payment-frequency.md) (article)
