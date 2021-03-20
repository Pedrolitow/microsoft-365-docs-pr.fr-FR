---
title: Gérer les modes de paiement
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- okr_SMB
- AdminSurgePortfolio
- commerce
search.appverid:
- MET150
description: Découvrez comment gérer les modes de paiement dans le centre d'administration Microsoft 365.
ms.date: ''
ms.openlocfilehash: 2a53ae0bfb4806a85e03f293f58e1b575e8bcf90
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50911841"
---
# <a name="manage-payment-methods"></a>Gérer les modes de paiement

::: moniker range="o365-21vianet"
> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](../../admin/microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).
::: moniker-end

Lors de votre achat de produits ou de services commerciaux Microsoft, vous pouvez choisir un mode de paiement existant ou bien en ajouter un autre. Les cartes de débit, de crédit et les informations bancaires sont acceptées pour effectuer ces achats.

Si votre compte professionnel comporte un profil de facturation dont vous êtes le propriétaire ou le contributeur, vous pouvez effectuer vos achats par sa carte de crédit associée ou par paiement de facture. Si vous êtes le directeur financier, vous ne pouvez utiliser qu’un profil de facturation pour régler les factures. Pour en savoir plus sur les profils de facturation et les rôles, consultez [Gérer les profils de facturation](manage-billing-profiles.md).

Si votre compte professionnel ne comporte pas de profil de facturation, tout administrateur global ou financier peut gérer et utiliser les comptes bancaires ajoutés au compte professionnel. Cependant, vous ne pouvez gérer ou utiliser que les cartes de crédit que vous ajoutez.

> [!NOTE]
> L’option de règlement par compte bancaire n’est pas disponible dans certains pays ou régions.
>
> Vous devez utiliser un mode de paiement provenant du même pays que celui de votre client.

## <a name="before-you-begin"></a>Avant de commencer

Pour suivre les étapes décrites dans cet article, vous devez être administrateur général ou de facturation. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="add-a-payment-method"></a>Ajouter un mode de paiement

L’ajout d’un mode de paiement n’entraîne aucune association d’abonnement. Pour attribuer un seul abonnement au mode de paiement, consultez [Changer un mode de paiement pour un seul abonnement](#change-a-payment-method-for-a-single-subscription). Pour remplacer le mode de paiement associé à tous les abonnements, consultez [Remplacer un mode de paiement](#replace-a-payment-method).

1. Dans le centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez **Ajouter ou sélectionner un mode de paiement**.
3. Sur la page **Modes de paiement**, sélectionnez un mode de paiement dans le menu déroulant.
4. Entrez les informations de la nouvelle carte bancaire ou du nouveau compte bancaire, puis sélectionnez **Ajouter**.

## <a name="update-payment-method-details"></a>Mettre à jour les informations sur le mode de paiement

Vous pouvez changer le nom du détenteur de la carte de crédit ou de débit, l’adresse de facturation ou la date d’expiration d’un mode de paiement existant. Cependant, vous ne pouvez pas changer le numéro de la carte ou du compte. Si le numéro de compte a changé, [procédez au remplacement du mode de paiement](#replace-a-payment-method), puis [supprimez le mode obsolète](#delete-a-payment-method).

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à mettre à jour. Dans le volet droit, sélectionnez **Modifier**.
3. Mettez à jour les informations relatives au mode de paiement, notamment le nom figurant sur la carte de crédit ou de débit, l’adresse de facturation ou la date d’expiration, puis sélectionnez **Enregistrer**.

## <a name="replace-a-payment-method"></a>Remplacer un mode de paiement

Remplacer un mode de paiement revient à le remplacer pour tous les abonnements et profils de facturation qui l’utilisent. Ceci ne supprime pas l’ancien mode de paiement. Vous pouvez toujours le sélectionner et l’utiliser pour d’autres abonnements et profils de facturation.

Pour changer le mode de paiement d’un seul abonnement, consultez [Changer le mode de paiement d’un seul abonnement](#change-a-payment-method-for-a-single-subscription).

1. Dans le Centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à changer. Le volet droit répertorie tous les profils de facturation et les abonnements individuels qui utilisent le moyen de paiement sélectionné.
3. Dans le volet droit, sélectionnez **Changer le mode de paiement pour tous les éléments**.
4. Pour utiliser un mode de paiement existant, choisissez-le dans la liste déroulante, puis sélectionnez **Remplacer**.
    > [!NOTE]
    > Si vous avez des abonnements associés à un profil de facturation, vous pouvez uniquement utiliser une carte de débit ou de crédit pour les régler. Si vous avez des comptes bancaires répertoriés sur la page **Modes de paiement**, vous ne pouvez pas les sélectionner dans la liste déroulante.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Dans le volet **Ajouter un mode de paiement**, entrez les informations de compte, puis sélectionnez **Enregistrer**. Vous devez utiliser un mode de paiement provenant du même pays que celui de votre client.
7. Le nouveau mode de paiement est déjà sélectionné dans la liste déroulante. Sélectionnez **Remplacer**.

## <a name="change-a-payment-method-for-a-single-subscription"></a>Changer le mode de paiement d’un seul abonnement

Vous pouvez changer le mode de paiement d’un seul abonnement.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Dans l’onglet **Produits**, trouvez l’abonnement pour lequel vous souhaitez utiliser un mode de paiement secondaire.
3. Sélectionnez **Autres actions** (points de suspension), puis sélectionnez **Remplacer le mode de paiement**.
4. Dans le volet **Remplacer le mode de paiement**, dans la liste déroulante, choisissez un mode de paiement secondaire ou ajoutez un mode de paiement.
5. Pour ajouter un mode de paiement, entrez les informations de la carte ou du compte bancaire, puis sélectionnez **Enregistrer**.
6. Vérifiez l’exactitude du mode de paiement sélectionné, puis sélectionnez **Remplacer**.

## <a name="delete-a-payment-method"></a>Supprimer un mode de paiement

Vous ne pouvez supprimer un mode de paiement que s’il n’est pas associé à un abonnement ou à un profil de facturation. Ceci vaut pour tous les abonnements, quel que soit leur statut.

### <a name="delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement non associé à un abonnement ou à un profil de facturation

Si le mode de paiement n’est pas associé à un abonnement ou à un profil de facturation, vous pouvez le supprimer immédiatement.

1. Dans le centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Trouvez le mode de paiement à supprimer, sélectionnez les points de suspension, puis sélectionnez **Supprimer**.
3. Dans la partie inférieure droite du volet, sélectionnez **Supprimer**.

### <a name="delete-a-payment-method-with-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement associé à un abonnement ou à un profil de facturation

Si un mode de paiement est associé à un abonnement ou à un profil de facturation, remplacez-le d’abord par un mode de paiement existant ou ajoutez-en un nouveau, puis supprimez le mode obsolète.

1. Dans le centre d’administration, accédez à la page **Facturation** > **Factures et paiements** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">Modes de paiement</a>.
2. Sélectionnez la ligne du mode de paiement à supprimer. Le volet droit affiche la liste des abonnements qui utilisent actuellement ce mode de paiement.
3. Dans le volet droit, sélectionnez **Supprimer**.
4. Pour utiliser un mode de paiement existant, choisissez-le dans la liste déroulante, sélectionnez **Suivant**, puis sélectionnez **Supprimer**.
    > [!NOTE]
    > Si des abonnements sont associés à un profil de facturation, vous pouvez uniquement utiliser une carte de débit ou de crédit pour les régler. Si des comptes bancaires sont répertoriés sur la page **Modes de paiement**, vous ne pouvez pas les sélectionner dans la liste déroulante.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Choisissez le type de mode de paiement à ajouter, entrez les informations sur le compte, puis sélectionnez **Enregistrer**.
7. Le nouveau mode de paiement est pré-sélectionné dans la liste déroulante. Sélectionnez **Suivant**.
8. Sélectionnez **Supprimer**.

## <a name="troubleshoot-payment-methods"></a>Résolution des problèmes des modes de paiement

| Problème | Étapes de résolution des problèmes |
|:----------|:-----|
|**Un message d'erreur indiquant que le navigateur est actuellement configuré pour bloquer les cookies apparaît.** |Configurez votre navigateur pour autoriser les cookies tiers, puis réessayez. |
|**Ma carte bancaire a été refusée.** |Si vous payez par carte bancaire et que cette dernière est refusée, vous recevez un courrier électronique vous informant que Microsoft n’a pas pu procéder au paiement. Vérifiez que les détails de la carte (numéro, date d’expiration, nom du détenteur et adresse, dont la ville et le code postal) correspondent exactement à ceux inscrits sur la carte et sur votre relevé. Vous pouvez mettre à jour les informations de la carte et autoriser immédiatement le paiement en suivant le lien **Régler le montant** dans la section **Facturation** de la page de détails de l’abonnement. Pour plus d’informations, consultez [Que se passe-t-il si j’ai un montant impayé ?](pay-for-your-subscription.md#what-if-i-have-an-outstanding-balance)  <br/><br/>  Si vous obtenez toujours le message de refus de la carte, contactez votre banque. Votre carte n’est peut-être pas active. Si la carte vous a récemment été remise par courrier postal pour cause d’extension de validité, assurez-vous qu’elle a été activée. Votre établissement bancaire peut également vous indiquer si votre carte bancaire ne vous permet pas d'effectuer de transactions en ligne, internationales ou récurrentes. |
|**Je souhaite mettre à jour un numéro de carte ou de compte bancaire.** |Vous ne pouvez pas modifier le numéro de carte ou de compte bancaire d’un mode de paiement existant. Si le numéro de carte ou de compte bancaire a changé, [procédez au remplacement du mode de paiement](#replace-a-payment-method) : tous les abonnements associés à ce mode de paiement seront reportés sur le nouveau mode ; puis [supprimez le mode obsolète](#delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached). |
|**Je n'ai qu'une carte ou qu’un compte bancaire sur mon compte et je souhaite le ou la supprimer.** |Si vous n’avez qu’un seul mode de paiement, vous devez en [effectuez le remplacement par un nouveau mode de paiement](#replace-a-payment-method) avant de pouvoir le supprimer. |
|**Je ne parviens pas à ajouter ma carte ou mon compte bancaire.**  |Vous devez utiliser un mode de paiement provenant du même pays que celui de votre client. Si vous ne parvenez pas à entrer les informations de votre carte ou votre compte bancaire, vous pouvez [contacter le support technique](../../admin/contact-support-for-business-products.md). |

## <a name="related-content"></a>Contenu connexe

[Régler votre abonnement d’entreprise](pay-for-your-subscription.md)
[Gérer les profils de facturation](manage-billing-profiles.md) (article)\
[Modifier la périodicité de votre facturation](change-payment-frequency.md) (article)