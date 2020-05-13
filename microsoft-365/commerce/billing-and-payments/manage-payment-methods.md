---
title: Créer des méthodes de paiement
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: Découvrez comment gérer vos modes de paiement dans le centre d’administration 365 de Microsoft.
ms.openlocfilehash: c1679b8f525712681aaaad20334840da5e625ad6
ms.sourcegitcommit: 8e655c6cbb91bfb97efda9a99c39fac33eaa974a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "44213067"
---
# <a name="manage-payment-methods"></a>Créer des méthodes de paiement

Lorsque vous achetez des produits ou services d’entreprise auprès de Microsoft, vous pouvez utiliser un mode de paiement existant ou en ajouter un nouveau. Vous pouvez utiliser une carte bancaire ou un compte bancaire pour payer les éléments que vous achetez.

Si votre compte professionnel dispose d’un profil de facturation et que vous êtes un propriétaire de profil de facturation ou un collaborateur de profil de facturation, vous pouvez utiliser le profil de facturation qui est sauvegardé par carte bancaire ou paiement de facture pour effectuer des achats ou payer des factures. Si vous êtes gestionnaire de factures de facturation, vous pouvez uniquement utiliser un profil de facturation pour payer des factures. Pour en savoir plus sur les profils de facturation et les rôles, consultez la rubrique [Manage Billing Profiles](manage-billing-profiles.md).

Si votre compte professionnel ne dispose pas d’un profil de facturation, tout administrateur général ou de facturation peut gérer et utiliser n’importe quel compte bancaire ajouté au compte professionnel. Toutefois, vous ne pouvez gérer ou utiliser que les cartes de crédit que vous ajoutez.

> [!NOTE]
> L’option de paiement avec un compte bancaire n’est pas disponible dans certains pays ou certaines régions.
>
> Vous devez utiliser un mode de paiement émis par le même pays que votre client.

## <a name="add-a-payment-method"></a>Ajouter un mode de paiement

L’ajout d’un mode de paiement n’associe pas d’abonnements à celui-ci. Pour affecter un seul abonnement au mode de paiement, reportez-vous à la rubrique [modifier un mode de paiement pour un seul abonnement](#change-a-payment-method-for-a-single-subscription). Pour remplacer tous les abonnements utilisant un autre mode de paiement par le nouveau, reportez-vous à la rubrique [remplacement d’un mode de paiement](#replace-a-payment-method).

1. Dans le centre d’administration, accédez à **la**  >  page**factures &**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">paiement</a> des paiements.
2. Sélectionnez **Ajouter ou sélectionner un mode de paiement**.
3. Sur la page **Modes de paiement**, sélectionnez un mode de paiement dans le menu déroulant.
4. Entrez les informations pour la nouvelle carte ou le nouveau compte bancaire, puis sélectionnez **Ajouter**.

## <a name="update-payment-method-details"></a>Mettre à jour les détails du mode de paiement

Vous pouvez modifier le nom de la carte bancaire, de l’adresse de facturation ou de la date d’expiration d’un mode de paiement existant. Toutefois, vous ne pouvez pas modifier la carte ou le numéro de compte. Si le numéro de compte a changé, [Remplacez-le par un autre mode de paiement](#replace-a-payment-method), puis [supprimez l’ancien](#delete-a-payment-method).

1. Dans le centre d’administration, accédez à **la**  >  page**factures &**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">paiement</a> des paiements.
2. Sélectionnez la ligne du mode de paiement à mettre à jour. Dans le volet droit, sélectionnez **modifier**.
3. Mettez à jour les informations de votre mode de paiement, notamment le nom de la carte bancaire, de l’adresse de facturation ou de la date d’expiration, puis sélectionnez **Enregistrer**.

## <a name="replace-a-payment-method"></a>Remplacer un mode de paiement

Lorsque vous remplacez un mode de paiement, vous le remplacez pour tous les abonnements et les profils de facturation qui utilisent le même mode de paiement. Le remplacement d’un mode de paiement n’entraîne pas la suppression du mode de paiement existant. Vous pouvez toujours sélectionner et utiliser d’autres abonnements et profils de facturation.

Pour modifier le mode de paiement d’un abonnement unique, consultez la rubrique [modifier un mode de paiement pour un seul abonnement](#change-a-payment-method-for-a-single-subscription).

1. Dans le centre d’administration, accédez à **la**  >  page**factures &**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">paiement</a> des paiements.
2. Sélectionnez la ligne du mode de paiement à remplacer. Le volet droit répertorie tous les profils de facturation et les abonnements individuels qui utilisent le mode de paiement sélectionné.
3. Dans le volet droit, sélectionnez **remplacer le mode de paiement pour tous les éléments**.
4. Pour utiliser un mode de paiement existant, sélectionnez-en un dans la liste déroulante, puis sélectionnez **remplacer**.
    > [!NOTE]
    > Si vous avez des abonnements associés à un profil de facturation, vous pouvez uniquement utiliser une carte bancaire pour les payer. Si vous avez des comptes bancaires répertoriés sur la page **modes de paiement** , ils ne sont pas disponibles dans la liste déroulante.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Dans le volet **Ajouter un mode de paiement** , entrez les informations de compte, puis sélectionnez **Enregistrer**. Vous devez utiliser un mode de paiement du même pays que votre client.
7. Le nouveau mode de paiement est déjà sélectionné dans la liste déroulante. Sélectionnez **Remplacer**.

## <a name="change-a-payment-method-for-a-single-subscription"></a>Modifier un mode de paiement pour un abonnement unique

Vous pouvez modifier le mode de paiement utilisé pour payer un seul abonnement.

1. Dans le centre d’administration, accédez à la page **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> .
2. Sous l’onglet **abonnements** , sélectionnez l’abonnement que vous souhaitez payer avec l’autre mode de paiement. 
3. Sous **facturation**, en regard de mode de paiement, sélectionnez **modifier**.
4. En regard de votre mode de paiement existant, sélectionnez **modifier**.
5. Dans la liste déroulante, choisissez un autre mode de paiement ou choisissez d’ajouter un mode de paiement.
6. Si vous ajoutez un mode de paiement, entrez les informations sur la carte ou le compte, puis sélectionnez **Enregistrer**.
7. Vérifiez que le mode de paiement sélectionné est correct, puis sélectionnez **Enregistrer**.

## <a name="delete-a-payment-method"></a>Supprimer un mode de paiement

Vous pouvez supprimer uniquement un mode de paiement qui n’est pas associé à un abonnement ou un profil de facturation. Cela s’applique à tous les abonnements, quel que soit leur état.

### <a name="delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement sans abonnement ni profil de facturation associé

Si aucun mode de paiement n’est associé à des abonnements ou des profils de facturation, vous pouvez immédiatement le supprimer.

1. Dans le centre d’administration, accédez à **la**  >  page**factures &**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">paiement</a> des paiements.
2. Recherchez le mode de paiement à supprimer, sélectionnez les trois points, puis sélectionnez **supprimer**.
3. En bas du volet droit, sélectionnez **supprimer**.

### <a name="delete-a-payment-method-with-subscriptions-or-billing-profiles-attached"></a>Supprimer un mode de paiement avec des abonnements ou des profils de facturation liés

Si un mode de paiement est associé à des abonnements ou des profils de facturation, commencez par le remplacer par un mode de paiement existant, ou ajoutez-en un nouveau, puis supprimez l’ancien mode de paiement.

1. Dans le centre d’administration, accédez à **la**  >  page**factures &**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2018806" target="_blank">paiement</a> des paiements.
2. Sélectionnez la ligne du mode de paiement à supprimer. Le volet droit répertorie les abonnements existants qui utilisent ce mode de paiement.
3. Dans le volet droit, sélectionnez **supprimer**.
4. Pour utiliser un mode de paiement existant, sélectionnez-en un dans la liste déroulante, cliquez sur **suivant**, puis sélectionnez **supprimer**.
    > [!NOTE]
    > Si vous avez des abonnements associés à un profil de facturation, vous pouvez uniquement utiliser une carte de crédit pour les payer. Si vous avez des comptes bancaires répertoriés sur la page **modes de paiement** , ils ne sont pas disponibles dans la liste déroulante.
5. Pour ajouter un nouveau mode de paiement, sélectionnez **Ajouter un mode de paiement**.
6. Choisissez le type de mode de paiement que vous souhaitez ajouter, entrez les informations de compte, puis sélectionnez **Enregistrer**.
7. Le nouveau mode de paiement est déjà sélectionné dans la liste déroulante. Sélectionnez **Suivant**.
8. Sélectionnez **Supprimer**.

## <a name="troubleshoot-payment-methods"></a>Résolution des problèmes des modes de paiement

|**Problème**|**Étapes de dépannage**|
|:----------|:-----|
|**J’obtiens un message d’erreur indiquant « le navigateur est actuellement configuré pour bloquer les cookies ».** |Configurez votre navigateur pour autoriser les cookies tiers, puis réessayez. |
|**Ma carte bancaire a été refusée.** |Si vous payez par carte bancaire, et que votre carte est refusée, vous recevez un message indiquant que Microsoft n’a pas pu traiter le paiement. Vérifiez que le &mdash; numéro de carte de détails de carte, la date d’expiration, le nom sur la carte et l’adresse, y compris la ville, l’État et le code postal &mdash; apparaissent exactement comme sur la carte et votre relevé. Vous pouvez mettre à jour les informations de votre carte et en envoyer immédiatement le paiement à l’aide du lien **solde de règlement** dans la section **facturation** de la page Détails de l’abonnement. Pour plus d’informations, consultez la rubrique [que se passe-t-il si ma carte de crédit a été refusée et mon paiement est échu ?](pay-for-your-subscription.md#what-if-my-credit-card-was-declined-and-my-payment-is-past-due)  <br/><br/>  Si vous obtenez toujours le message de refus de la carte bancaire, contactez votre banque. Votre carte n’est peut-être pas active. Si vous avez récemment reçu la carte dans le message avec une date d’expiration mise à jour, assurez-vous qu’elle est activée. Votre banque peut également vous indiquer si votre carte n’est pas approuvée pour les transactions en ligne, internationales ou périodiques. |
|**Je veux mettre à jour une carte ou un numéro de compte bancaire.** |Vous ne pouvez pas modifier la carte ou le numéro de compte d’un mode de paiement existant. Si le numéro de votre carte ou de votre compte a changé, [Remplacez-le par un autre mode de paiement](#replace-a-payment-method), ce qui déplace tous les abonnements actifs du mode de paiement vers le nouveau, puis [supprimez l’ancien mode de paiement](#delete-a-payment-method-with-no-subscriptions-or-billing-profiles-attached). |
|**Je ne dispose que d’une carte ou d’un compte bancaire sur mon compte et je souhaite le supprimer.** |Si vous n’avez qu’un seul mode de paiement, vous devez le [remplacer par un nouveau mode de paiement](#replace-a-payment-method) avant de pouvoir le supprimer. |
|**Je ne parviens pas à ajouter ma carte ou mon compte bancaire.**  |Vous devez utiliser un mode de paiement émis par le même pays que votre client. Si vous ne parvenez pas à entrer les informations de votre carte ou de votre compte bancaire, vous pouvez [contacter le support technique](../../admin/contact-support-for-business-products.md). |

## <a name="related-articles"></a>Articles connexes

[Payez votre abonnement professionnel](pay-for-your-subscription.md)

[Gérer les profils de facturation](manage-billing-profiles.md)

[Modifier la fréquence de paiement](change-payment-frequency.md)