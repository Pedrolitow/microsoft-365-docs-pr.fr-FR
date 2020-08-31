---
title: Mise à niveau à partir d’un abonnement Office 365 E4
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
- Adm_O365
- Adm_NonTOC
- commerce
ms.custom: customer-email
search.appverid:
- MET150
description: Découvrez comment effectuer une mise à niveau à partir d’un abonnement Office 365 E4.
ms.date: 08/14/2020
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 2587732a6c4092dcb7b53daf9493e7cee2f1987c
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47308004"
---
# <a name="upgrade-from-an-office-365-e4-subscription"></a>Mise à niveau à partir d’un abonnement Office 365 E4

Cet article décrit le processus de mise à niveau à partir d’un Office 365 E4 vers un nouvel abonnement. Pour plus d’informations sur les options disponibles lors de la mise à niveau à partir d’Office 365 E4, consultez la rubrique [informations importantes pour les clients d’office 365 E4](important-information-e4.md).

> [!IMPORTANT]
> Cet article s’applique aux abonnements Office 365 E4 qui ont été achetés directement auprès de Microsoft par le biais d’une carte de crédit ou d’une facture uniquement. Si votre abonnement a été acheté d’une autre manière, par exemple via un partenaire ou via le centre de gestion des licences en volume, contactez votre représentant Microsoft ou votre partenaire pour vous aider à mettre à niveau les plans.

## <a name="what-are-my-options-for-how-to-upgrade"></a>Quelles sont les options de mise à niveau ?

Le moyen le plus simple de mettre à niveau votre plan consiste à utiliser l’onglet **mise à niveau** dans le centre d’administration 365 de Microsoft. Toutefois, l’utilisation de l’onglet **mise à niveau** n’est pas prise en charge dans toutes les situations. Si votre scénario n’est pas pris en charge, vous pourrez peut-être effectuer une mise à niveau manuelle des plans.

## <a name="what-is-the-upgrade-tab"></a>Qu’est-ce que l’onglet mise à niveau ?

L’onglet **mise à niveau** effectue les tâches suivantes :

- Aide tout au long du processus d'achat d'une nouvelle offre.
- Réattribution de toutes les licences utilisateur de votre ancienne offre vers votre nouvelle offre.
- Annulation de votre ancienne offre.

## <a name="what-does-it-mean-to-upgrade-plans-manually"></a>Qu’est-ce que la mise à niveau manuelle des plans ?

La mise à niveau manuelle des plans implique l’exécution des procédures distinctes suivantes au lieu d’utiliser l’onglet **mise à niveau** .

- Acheter un nouvel abonnement avec le nombre de licences approprié.
- Vérification du fait que le nouvel abonnement est prêt à être utilisé.
- Réattribuez des licences aux utilisateurs.
- Annulez l’abonnement Office 365 E4 d’origine.

## <a name="find-out-if-you-can-use-the-upgrade-tab-to-upgrade-to-a-new-plan"></a>Déterminer si vous pouvez utiliser l’onglet mise à niveau pour effectuer une mise à niveau vers un nouveau plan

1. Dans le centre d’administration, accédez à la page **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> .
2. Sélectionnez votre abonnement Office 365 E4.
3. Sélectionnez l’onglet **mise à niveau** . Si d’autres plans sont affichés, cela signifie que vous pouvez effectuer une mise à niveau automatique des plans.
4. Si la mise à niveau n’est pas automatique, un message indiquant la raison de l’impossibilité de la mise à niveau s’affiche.

Il existe plusieurs raisons pour lesquelles vous ne pouvez pas effectuer une mise à niveau automatique des plans. La plupart des problèmes sont des dysfonctionnements temporaires, par exemple, des problèmes liés à l'intégrité des services, que vous pouvez résoudre. Pour plus d’informations, consultez la rubrique [pourquoi ne puis-je pas mettre à niveau des plans ?](upgrade-to-different-plan.md#why-cant-i-upgrade-plans) Si vous avez besoin d’aide pour votre mise à niveau, [Contactez le support technique](../../admin/contact-support-for-business-products.md).

## <a name="will-a-credit-check-be-required"></a>Une vérification de solvabilité sera-t-elle nécessaire ?

Si vous avez choisi de régler votre nouvelle offre par facture ou si votre achat dépasse un certain montant, une vérification de solvabilité peut être nécessaire. Si une vérification de solvabilité est nécessaire, la mise à niveau peut prendre jusqu’à deux jours ouvrés. Les administrateurs n’ont pas accès au centre d’administration Microsoft 365 tant que la vérification de solvabilité n’est pas terminée. Toutefois, les utilisateurs ont toujours un accès complet au plan E4 jusqu’à ce que la mise à niveau soit terminée.

## <a name="upgrade-your-plan-by-using-the-upgrade-tab"></a>Mettre à niveau votre plan à l’aide de l’onglet mise à niveau

### <a name="before-you-begin"></a>Avant de commencer

Voici quelques points importants à retenir avant de commencer.

- **Planifier le temps d’arrêt administratif.** Les administrateurs ne peuvent pas utiliser le centre d’administration Microsoft 365 lors de la mise à niveau du plan. Selon le nombre d’utilisateurs dont vous disposez, la mise à niveau peut prendre de minutes à quelques heures. Nous vous recommandons de procéder à la mise à niveau lorsque vous n’avez pas besoin d’effectuer des mises à jour à l’aide du centre d’administration Microsoft 365.

    Les utilisateurs ne subissent aucune interruption de service tandis que le plan est mis à niveau-ils continuent à avoir un accès total à l’abonnement E4 pendant le processus de mise à niveau. Lorsque la mise à niveau est terminée, les utilisateurs ont accès à la nouvelle offre.
- **Utilisateurs, licences, facturation et domaines personnalisés.** Pour comprendre comment les utilisateurs et les licences sont traités au cours de la mise à niveau, comment la mise à niveau des plans influe sur votre facturation et comment gérer les domaines personnalisés, voir qu’est- [ce que la mise à niveau d’un plan vers mon service et la facturation ?](upgrade-to-different-plan.md#what-does-upgrading-a-plan-do-to-my-service-and-billing)
- **Modifier le nombre de licences utilisateur.** Vous ne pouvez pas supprimer des licences dans le cadre de la mise à niveau des plans. Toutefois, vous pouvez [réduire le nombre de licences](../licenses/buy-licenses.md) avant ou après la mise à niveau des plans.

### <a name="start-the-upgrade-by-using-the-upgrade-tab"></a>Démarrer la mise à niveau à l’aide de l’onglet mise à niveau

1. Dans le centre d’administration, accédez à la page **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> .
2. Sélectionnez votre abonnement Office 365 E4.
3. Sur la page Détails de l’abonnement, sélectionnez l’onglet **mise à niveau** .
4. Recherchez l’abonnement que vous souhaitez acheter, puis sélectionnez **mettre à niveau**.
5. Sur la page **Cart** , vérifiez que tout est correct. Indiquez si vous souhaitez payer tous les mois ou tous les ans, et vérifiez le nombre de licences sous **quantité**.
    > [!NOTE]
    > Tout abonnement de module complémentaire associé à votre abonnement Office 365 E4, tel que le stockage de fichiers supplémentaire Office 365 est également répertorié. Toutefois, si vous avez des abonnements de module complémentaire qui sont inclus dans l’abonnement vers lequel vous effectuez la mise à niveau, nous les supprimerons.
6. Une fois que vous avez vérifié votre commande, sélectionnez **aller à la conclusion de la transaction**.
7. Sur la page **validation** , vérifiez les éléments **vendus à**, **facturés à**et **dans cet ordre**. Sélectionnez **modifier** en regard de l’un de ces éléments pour modifier les informations.
    > [!NOTE]
    > La possibilité d’utiliser la facture comme mode de paiement n’est disponible que pour les commandes dont le montant est supérieur à un coût donné. La sélection de l’option de paiement de facture peut retarder le processus de mise à niveau de deux jours ouvrés au maximum si une vérification de solvabilité est requise.
8. Lorsque vous avez terminé, sélectionnez **passer une commande**.

> [!NOTE]
> La mise à niveau des plans prend généralement moins de dix minutes s’il n’y a pas d’erreurs ou de problèmes. Vous pouvez vérifier l’état de votre mise à niveau en consultant l’ancien ou le nouvel abonnement.

## <a name="upgrade-your-plan-manually"></a>Mise à niveau manuelle de votre plan

Pour mettre à niveau manuellement des utilisateurs vers un autre abonnement, effectuez les étapes suivantes dans l’ordre indiqué.

- [Étape 1 : acheter un nouvel abonnement](#step-1-buy-a-new-subscription)
- [Étape 2 : vérifier que votre abonnement dispose du nombre de licences correct](#step-2-verify-that-your-subscription-has-the-right-number-of-licenses)
- [Étape 3 : réattribuer des licences aux utilisateurs](#step-3-reassign-licenses-to-users)
- [Étape 4 : annuler l’abonnement à Office 365 E4](#step-4-cancel-the-office-365-e4-subscription)

### <a name="step-1-buy-a-new-subscription"></a>Étape 1 : acheter un nouvel abonnement

Si vous n’avez pas encore de nouvel abonnement, vous pouvez [acheter un autre abonnement Microsoft 365 pour les entreprises](../buy-another-subscription.md).

Si vous disposez déjà d’un abonnement, passez à l’étape suivante.

### <a name="step-2-verify-that-your-subscription-has-the-right-number-of-licenses"></a>Étape 2 : vérifier que votre abonnement dispose du nombre de licences correct

Avant de passer à l’étape suivante, il est important de s’assurer que tous les services à l’intérieur de votre nouvel abonnement ont été configurés. Si l’abonnement n’est pas prêt lors de votre première vérification, réessayez ultérieurement.

> [!NOTE]
> Si vous avez choisi de payer le nouvel abonnement par facture, une vérification de solvabilité peut être nécessaire. Deux jours ouvrables peuvent être nécessaires avant que l’abonnement ne soit disponible.

1. Dans le centre d’administration, accédez à la page **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> .
2. Dans la liste déroulante état de l' **abonnement** , sélectionnez **active**.
3. Assurez-vous que votre nouvel abonnement est affiché, et que le nombre de licences est identique à celui que vous aviez pour Office 365 E4.
4. Si vous avez besoin d’acheter des licences supplémentaires, suivez les étapes de la procédure [acheter ou supprimer des licences d’abonnement](../licenses/buy-licenses.md).

### <a name="step-3-reassign-licenses-to-users"></a>Étape 3 : réattribuer des licences aux utilisateurs

Vous pouvez utiliser le centre d’administration Microsoft 365 pour réattribuer des licences pour un maximum de 20 utilisateurs à la fois. Pour savoir comment procéder, consultez la rubrique [déplacer des utilisateurs vers un autre abonnement](move-users-different-subscription.md).

> [!TIP]
> Si vous avez un grand nombre d’utilisateurs, vous pouvez [utiliser Office 365 PowerShell pour attribuer des licences utilisateur en bloc](https://docs.microsoft.com/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell).

### <a name="step-4-cancel-the-office-365-e4-subscription"></a>Étape 4 : annuler l’abonnement à Office 365 E4

Une fois que tous vos utilisateurs ont été réaffectés à votre nouvel abonnement, [annulez l’abonnement Office 365 E4](cancel-your-subscription.md).

## <a name="related-content"></a>Contenu connexe

[Mise à niveau vers un autre plan](upgrade-to-different-plan.md) (article) \
[Acheter ou supprimer des licences d’abonnement](../licenses/buy-licenses.md) (article) \
[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)
