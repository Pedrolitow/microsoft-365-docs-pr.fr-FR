---
title: Comprendre les profils de facturation
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: amberb, vikdesai
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Découvrez comment les profils de facturation prennent en charge les factures.
ms.date: 04/02/2021
ms.openlocfilehash: cff74260395f31738753c2217fe15fe51e05d35d
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720325"
---
# <a name="understand-billing-profiles"></a>Comprendre les profils de facturation

Un profil de facturation contient un mode de paiement, des informations de facturation et d’autres paramètres de facture, tels que le numéro de bon de commande et la préférence de facture par e-mail. Vous utilisez un profil de facturation pour payer les produits que vous achetez auprès de Microsoft. Les profils de facturation sont automatiquement créés et chacun d’eux est facturé séparément. 

> [!NOTE]
>
> Tous les comptes n’ont pas de profil de facturation. Si vous ne savez pas si vous en avez un, vous pouvez [afficher la liste de vos profils de facturation](manage-billing-profiles.md#view-my-billing-profiles).

## <a name="what-are-billing-profile-roles"></a>Que sont les rôles de profil de facturation ?

Les rôles sur les profils de facturation disposent des autorisations nécessaires pour contrôler les achats et afficher et gérer les factures. Attribuez ces rôles aux utilisateurs qui effectuent le suivi, l’organisation et le paiement des factures. Par exemple, les membres de l’équipe d’approvisionnement de votre organisation.

| Rôle                         | Description                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Propriétaire du profil de facturation        | Gérer tout pour un profil de facturation                                          |
| Contributeur de profil de facturation  | Gérer tout, sauf les autorisations dans un profil de facturation                        |
| Lecteur de profil de facturation       | Affichage en lecture seule de tous les éléments d’un profil de facturation                                |
| Gestionnaire de factures              | Afficher et payer les factures, et dispose d’une vue en lecture seule de tout ce qui se trouve dans un profil de facturation  |

## <a name="view-my-billing-profiles"></a>Afficher mes profils de facturation

> [!NOTE]
>
> Si vous suivez ces étapes et que la liste des profils de facturation est vide, cela signifie que vous n’avez pas de profil de facturation et que vous ne pouvez pas utiliser cette fonctionnalité.

1. Dans le Centre d’administration, accédez à la page **Factures** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Factures & paiements</a>.
2. Sélectionnez l’onglet **Profil de** facturation, puis sélectionnez un profil de facturation dans la liste.

Chaque profil de facturation inclut les informations suivantes :

- **Nom et état** &ndash; du profil de facturation Nom unique du profil de facturation et indique si le profil de facturation est actif ou désactivé pour l’achat.
- **Paramètres de facture** &ndash; Devise basée sur le pays du compte de facturation, informations sur la fréquence et la date de la facture, l’option de réception des factures sous forme de pièces jointes et un champ de numéro de bon de commande facultatif
- **Modes** &ndash; de paiement Affiche le mode de paiement principal et de secours, le cas échéant, pour le profil
- **Compte** &ndash; de facturation Nom du compte de facturation auquel le profil est lié. Pour plus d’informations sur les comptes de facturation, consultez [Comprendre les comptes de facturation](../manage-billing-accounts.md).
- **Informations de** &ndash; contact Adresse de facturation et nom du contact et adresse e-mail
- Rôles &ndash; **de profil de facturation** Liste des personnes auxquelles l’un des rôles de profil de facturation est attribué pour effectuer des opérations pour ce profil. Par exemple, payer des factures, ajouter un numéro de bon de commande ou remplacer le mode de paiement utilisé pour effectuer des achats.

> [!NOTE]
>
> Vous pouvez uniquement attribuer des rôles de profil de facturation aux utilisateurs de votre organisation.

## <a name="need-help-contact-support"></a>Besoin d’aide ? Contacter le support technique

Si vous avez des questions ou si vous avez besoin d’aide concernant vos frais Azure, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">créez une demande de support avec support Azure</a>.

Si vous avez des questions ou si vous avez besoin d’aide sur votre profil de facturation dans Centre d'administration Microsoft 365, [contactez le support](../../admin/get-help-support.md) technique.

## <a name="related-content"></a>Contenu associé

[Comment payer votre abonnement avec un profil de facturation](pay-for-subscription-billing-profile.md) (article)\
[Comprendre les comptes de facturation](../manage-billing-accounts.md) (article)\
[Gérer les modes de paiement](manage-payment-methods.md) (article)
