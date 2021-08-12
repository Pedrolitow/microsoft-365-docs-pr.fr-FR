---
title: Comprendre les profils de facturation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
f1_keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_billing
- AdminTemplateSet
search.appverid: MET150
description: Découvrez comment les profils de facturation supportent les factures.
ms.date: 04/02/2021
ms.openlocfilehash: f5fc1e162e6471feb62e886d65755b4b434bdf4a834be59bcf7b37f76f23f129
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53797145"
---
# <a name="understand-billing-profiles"></a>Comprendre les profils de facturation

Un profil de facturation contient un mode de paiement, des informations de facturation et d’autres paramètres de facture, tels que le numéro de bon de commande et les préférences de facture par courrier électronique. Vous utilisez un profil de facturation pour payer les produits que vous achetez auprès de Microsoft. Un profil de facturation est créé automatiquement lorsqu’un utilisateur effectue un achat en libre-service. Chaque profil de facturation est facturé séparément.

> [!NOTE]
>
> Les profils de facturation ne sont pas disponibles pour les clients qui achètent des produits et des services Microsoft.com ou sur la page Acheter des **services** du Centre d’administration Microsoft 365.

## <a name="what-are-billing-profile-roles"></a>Quels sont les rôles de profil de facturation ?

Les rôles sur les profils de facturation sont autorisés à contrôler les achats et à afficher et gérer les factures. Attribuez ces rôles aux utilisateurs qui s’en chargent du suivi, de l’organisation et du paiement des factures. Par exemple, les membres de l’équipe d’approvisionnement de votre organisation.

| Rôle                         | Description                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Propriétaire du profil de facturation        | Tout gérer pour un profil de facturation                                          |
| Collaborateur de profil de facturation  | Gérer tout sauf les autorisations dans un profil de facturation                        |
| Lecteur de profil de facturation       | Affichage en lecture seule de tous les informations d’un profil de facturation                                |
| Gestionnaire de factures              | Afficher et payer les factures, et dispose d’une vue en lecture seule de tous les informations d’un profil de facturation  |

## <a name="view-my-billing-profiles"></a>Afficher mes profils de facturation

> [!NOTE]
>
> Si vous suivez ces étapes et que la liste des profils de facturation est vide, cela signifie que vous n’avez pas de profil de facturation et que vous ne pouvez pas utiliser cette fonctionnalité.

1. Dans le Centre d’administration, accédez à la page **Factures** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Factures & paiements</a>.
2. Sélectionnez **l’onglet Profil** de facturation, puis sélectionnez un profil de facturation dans la liste.

Chaque profil de facturation inclut les informations suivantes :

- **Nom et état du profil de facturation** &ndash; Nom unique du profil de facturation et si le profil de facturation est actif ou désactivé pour l’achat.
- **Paramètres de facture** &ndash; Devise en fonction du pays du compte de facturation, des informations sur la fréquence et la date de facturation, l’option de réception de factures en pièces jointes et un champ de numéro de bon de visite facultatif
- **Modes de paiement** &ndash; Indique le mode de paiement principal et de sauvegarde, le caser, pour le profil
- **Compte de facturation** &ndash; Nom du compte de facturation lié au profil. Pour plus d’informations sur les comptes de facturation, voir [Comprendre les comptes de facturation.](../manage-billing-accounts.md)
- **Informations de contact** &ndash; Adresse de facturation, nom de contact et adresse e-mail
- **Rôles de profil de facturation** &ndash; Liste des personnes affectées à l’un des rôles de profil de facturation pour ce profil. Par exemple, payez les factures, ajoutez un numéro de bon de paiement ou remplacez le mode de paiement utilisé pour effectuer des achats.

> [!NOTE]
>
> Vous pouvez uniquement attribuer des rôles de profil de facturation aux utilisateurs de votre organisation.

## <a name="need-help-contact-support"></a>Besoin d’aide ? Contacter le support technique

Si vous avez des questions ou avez besoin d’aide sur vos frais Azure, créez une demande de <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">support avec le support Azure.</a>

Si vous avez des questions ou si vous avez besoin d’aide sur votre profil de facturation dans Centre d’administration Microsoft 365, [contactez le support technique.](../../business-video/get-help-support.md)

## <a name="related-content"></a>Contenu connexe

[Comment payer votre abonnement avec un profil de facturation](pay-for-subscription-billing-profile.md) (article)\
[Comprendre les comptes de facturation](../manage-billing-accounts.md) (article)\
[Gérer les modes de paiement](manage-payment-methods.md) (article)
