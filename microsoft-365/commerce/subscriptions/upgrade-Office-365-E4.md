---
title: Mise à niveau à partir d Office 365 abonnement E4
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- customer-email
- commerce_subscriptions
- PPM_jmueller
search.appverid: MET150
description: Découvrez comment mettre à niveau un abonnement Office 365 E4.
ms.date: 08/14/2020
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 0e30ece58cfc10ea258a684f9ac6ca4dba1b8692
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52297283"
---
# <a name="upgrade-from-an-office-365-e4-subscription"></a>Mise à niveau à partir d Office 365 abonnement E4

Cet article vous explique le processus de mise à niveau d’un Office 365 E4 vers un nouvel abonnement. Pour plus d’informations sur les options disponibles lors de la mise à niveau Office 365 E4, voir Informations importantes pour Office 365 [clients E4.](important-information-e4.md)

> [!IMPORTANT]
> Cet article s’applique Office 365 abonnements E4 achetés directement auprès de Microsoft via carte bancaire ou facture uniquement. Si votre abonnement a été acheté d’une autre façon, par exemple par le biais d’un partenaire ou du Centre de gestion des licences en volume, contactez votre représentant de compte Microsoft ou votre partenaire pour vous aider à mettre à niveau des plans.

## <a name="what-are-my-options-for-how-to-upgrade"></a>Quelles sont mes options de mise à niveau ?

Le moyen le plus simple de  mettre à niveau votre plan consiste à utiliser l’onglet Mise à niveau dans Microsoft 365 centre d’administration. Toutefois, l’utilisation **de l’onglet** Mise à niveau n’est pas prise en charge dans toutes les situations. Si votre scénario n’est pas pris en charge, vous pourrez peut-être mettre à niveau les plans manuellement.

## <a name="what-is-the-upgrade-tab"></a>Qu’est-ce que l’onglet Mise à niveau ?

**L’onglet** Mise à niveau vous permet d’effectuer les tâches suivantes :

- Aide tout au long du processus d'achat d'une nouvelle offre.
- Réattribution de toutes les licences utilisateur de votre ancienne offre vers votre nouvelle offre.
- Annulation de votre ancienne offre.

## <a name="what-does-it-mean-to-upgrade-plans-manually"></a>Que signifie la mise à niveau manuelle des plans ?

La mise à niveau manuelle des plans implique d’effectuer les procédures distinctes suivantes au lieu d’utiliser l’onglet Mise **à** niveau.

- Achetez un nouvel abonnement avec le nombre de licences le plus élevé.
- Vérification du fait que le nouvel abonnement est prêt à être utilisé.
- Réaffecter des licences aux utilisateurs.
- Annulez l’Office 365 abonnement E4 d’origine.

## <a name="find-out-if-you-can-use-the-upgrade-tab-to-upgrade-to-a-new-plan"></a>Savoir si vous pouvez utiliser l’onglet Mise à niveau pour mettre à niveau vers un nouveau plan

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sélectionnez votre abonnement Office 365 E4.
3. Sélectionnez **l’onglet** Mise à niveau. Si d’autres plans sont répertoriés, cela signifie que vous pouvez mettre à niveau les plans automatiquement.
4. Si vous ne pouvez pas mettre à niveau automatiquement, vous voyez un message qui décrit la raison pour laquelle vous ne pouvez pas mettre à niveau.

Il existe plusieurs raisons pour lesquelles vous ne pouvez pas mettre à niveau les plans automatiquement. La plupart des problèmes sont des dysfonctionnements temporaires, par exemple, des problèmes liés à l'intégrité des services, que vous pouvez résoudre. Pour plus d’informations, [voir Pourquoi ne puis-je pas mettre à niveau les plans ?](upgrade-to-different-plan.md#why-cant-i-upgrade-plans) Si vous avez besoin d’aide pour votre mise à niveau, [contactez le support technique.](../../business-video/get-help-support.md)

## <a name="will-a-credit-check-be-required"></a>Une vérification de solvabilité sera-t-elle nécessaire ?

Si vous avez choisi de régler votre nouvelle offre par facture ou si votre achat dépasse un certain montant, une vérification de solvabilité peut être nécessaire. Si une vérification de solvabilité est nécessaire, la mise à niveau peut prendre jusqu’à deux jours ou moins. Les administrateurs n’ont pas accès au Centre d’administration Microsoft 365'administration centrale tant que la vérification de solvabilité n’est pas terminée. Toutefois, les utilisateurs ont toujours un accès complet au plan E4 jusqu’à la fin de la mise à niveau.

## <a name="upgrade-your-plan-by-using-the-upgrade-tab"></a>Mettre à niveau votre plan à l’aide de l’onglet Mise à niveau

### <a name="before-you-begin"></a>Avant de commencer

Voici quelques points importants à retenir avant de commencer.

- **Planifiez les temps d’arrêt administratifs.** Les administrateurs ne peuvent pas utiliser le centre Microsoft 365'administration lorsque le plan est mis à niveau. Selon le nombre d’utilisateurs que vous avez, la mise à niveau peut prendre de quelques minutes à quelques heures. Nous vous recommandons de planifier la mise à niveau lorsque vous n’avez pas besoin d’effectuer de mises à jour à l’aide Microsoft 365 centre d’administration.

    Les utilisateurs ne font l’expérience d’aucune interruption de service pendant la mise à niveau du plan ; ils continuent à avoir un accès complet à l’abonnement E4 pendant le processus de mise à niveau. Une fois la mise à niveau terminée, les utilisateurs ont accès au nouveau plan.
- **Utilisateurs, licences, facturation et domaines personnalisés.** Pour comprendre comment les utilisateurs et les licences sont gérés pendant la mise à niveau, comment les plans de mise à niveau affectent votre facturation et comment gérer les domaines personnalisés, voir que fait la mise à niveau d’un plan vers mon service et la facturation [?](upgrade-to-different-plan.md#what-does-upgrading-a-plan-do-to-my-service-and-billing)
- **Modifier le nombre de licences utilisateur.** Vous ne pouvez pas supprimer de licences dans le cadre des plans de mise à niveau. Toutefois, vous pouvez [réduire le nombre de licences](../licenses/buy-licenses.md) avant ou après les plans de mise à niveau.

### <a name="start-the-upgrade-by-using-the-upgrade-tab"></a>Démarrer la mise à niveau à l’aide de l’onglet Mise à niveau

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sélectionnez votre abonnement Office 365 E4.
3. Dans la page détails de l’abonnement, sélectionnez **l’onglet Mise à** niveau.
4. Recherchez l’abonnement que vous souhaitez acheter, puis sélectionnez **Mettre à niveau.**
5. Dans la page **Panier,** vérifiez que tout est correct. Sélectionnez s’il faut payer mensuellement ou chaque année, et vérifiez le nombre de licences sous **Quantité**.
    > [!NOTE]
    > Tous les abonnements de modules Office 365 votre abonnement E4, tels que Stockage de fichiers supplémentaire Office 365 sont également répertoriés. Toutefois, si vous avez des abonnements à des modules modules qui sont inclus dans l’abonnement vers qui vous êtes en train de mettre à niveau, nous allons les supprimer.
6. Une fois que vous avez passé en revue votre commande, **sélectionnez Go to checkout**.
7. Dans la page **d’checkout,** **consultez La vente** à , **Facturé à** et Éléments dans **cet ordre**. Sélectionnez **Modifier** à côté de l’un de ces éléments pour modifier les informations.
    > [!NOTE]
    > L’option d’utilisation de la facture comme mode de paiement est disponible uniquement pour les commandes dont le coût dépasse un certain montant. La sélection de l’option de paiement par facture peut retarder le processus de mise à niveau de deux jours ou plus si une vérification de solvabilité est requise.
8. Lorsque vous avez terminé, sélectionnez **Ordre des commandes.**

> [!NOTE]
> La mise à niveau des plans prend généralement moins de dix minutes en l’absence d’erreurs ou de problèmes. Vous pouvez vérifier l’état de votre mise à niveau en regardant votre ancien ou votre nouvel abonnement.

## <a name="upgrade-your-plan-manually"></a>Mettre à niveau votre plan manuellement

Pour mettre manuellement à niveau les utilisateurs vers un autre abonnement, complétz les étapes suivantes dans l’ordre indiqué.

- [Étape 1 : Acheter un nouvel abonnement](#step-1-buy-a-new-subscription)
- [Étape 2 : Vérifier que votre abonnement dispose du nombre de licences le plus élevé](#step-2-verify-that-your-subscription-has-the-right-number-of-licenses)
- [Étape 3 : Réattribuer des licences aux utilisateurs](#step-3-reassign-licenses-to-users)
- [Étape 4 : Annuler l’abonnement Office 365 E4](#step-4-cancel-the-office-365-e4-subscription)

### <a name="step-1-buy-a-new-subscription"></a>Étape 1 : Acheter un nouvel abonnement

Si vous n’avez pas encore de nouvel abonnement, vous pouvez acheter un autre [abonnement Microsoft 365 pour les entreprises.](../try-or-buy-microsoft-365.md)

Si vous avez déjà un abonnement, continuez à l’étape suivante.

### <a name="step-2-verify-that-your-subscription-has-the-right-number-of-licenses"></a>Étape 2 : Vérifier que votre abonnement dispose du nombre de licences le plus élevé

Avant de passer à l’étape suivante, il est important de s’assurer que tous les services au sein de votre nouvel abonnement ont été mis en place. Si l’abonnement n’est pas prêt lors de la première vérification, essayez à nouveau ultérieurement.

> [!NOTE]
> Si vous avez choisi de payer le nouvel abonnement par facture, une vérification de solvabilité peut être nécessaire. L’abonnement peut prendre jusqu’à deux jours ou jours ou moins avant d’être disponible.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Dans la **drop-down État** de l’abonnement, sélectionnez **Active**.
3. Assurez-vous que votre nouvel abonnement s’affiche et que le nombre de licences est identique à celui que vous aviez pour Office 365 E4.
4. Si vous avez besoin d’acheter d’autres licences, suivez les étapes de l’étape Acheter ou supprimer [des licences d’abonnement.](../licenses/buy-licenses.md)

### <a name="step-3-reassign-licenses-to-users"></a>Étape 3 : Réattribuer des licences aux utilisateurs

Vous pouvez utiliser le Centre d Microsoft 365 pour réaffecter des licences à 20 utilisateurs à la fois. Pour savoir comment faire, voir [Déplacer des utilisateurs vers un autre abonnement.](move-users-different-subscription.md)

> [!TIP]
> Si vous avez un grand nombre d’utilisateurs, vous pouvez utiliser Office 365 PowerShell pour attribuer des [licences utilisateur en bloc.](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md)

### <a name="step-4-cancel-the-office-365-e4-subscription"></a>Étape 4 : Annuler l’abonnement Office 365 E4

Une fois que tous vos utilisateurs ont été réassignés à votre nouvel abonnement, annulez [Office 365 abonnement E4.](cancel-your-subscription.md)

## <a name="related-content"></a>Contenu connexe

[Mettre à niveau vers un autre plan](upgrade-to-different-plan.md) (article)\
[Acheter ou supprimer des licences d’abonnement](../licenses/buy-licenses.md) (article)\
[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)
