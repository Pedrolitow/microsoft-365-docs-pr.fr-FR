---
title: Comprendre votre facture
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
f1_keywords:
- MACBillingBillsPaymentsInvoices
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- commerce
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez comment lire et comprendre votre facture pour les produits Microsoft Business.
keywords: comptes de facturation, informations sur l’organisation, factures
ms.openlocfilehash: f0575683cdcaf0ac76de80c93e0d7573e8c63bae
ms.sourcegitcommit: 41eb898143286755cd36df9f7e769de641263d73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "45391517"
---
# <a name="understand-your-bill-or-invoice"></a>Comprendre votre facture

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

La facture fournit un résumé de vos frais et des instructions de paiement. Vous pouvez [afficher votre facture en ligne](#view-your-online-invoice) dans le centre d’administration 365 de Microsoft. Vous pouvez également le télécharger au format. pdf (portable document format) pour l’envoyer par courrier électronique.

Si vous avez un abonnement Microsoft 365 uniquement, consultez [la rubrique comprendre votre facture pour microsoft 365 pour les entreprises](understand-your-invoice2.md).

## <a name="understand-the-invoice-header"></a>Comprendre l’en-tête de facture

Le haut de la première page identifie la personne responsable du paiement, le lieu d’envoi de la facture et un résumé des frais.

| Term | Description |
| --- | --- |
| Vendu à |Le compte de facturation qui identifie le nom et l’adresse de l’entité juridique chargée du paiement. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">comptes de facturation</a> , dans laquelle vous pouvez trouver le contrat de compte et gérer les rôles et les autorisations. |
| Facturer à |Identifie la personne qui reçoit la facture. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">profils de facturation</a> . Le profil de facturation est également affiché sur la page facture en ligne, dans la section Résumé de la **facture** . Pour en savoir plus sur les profils de facturation et sur la façon dont vous pouvez les utiliser pour créer des options de facturation plus flexibles pour votre organisation, consultez la rubrique [Manage Billing Profiles](manage-billing-profiles.md). |
| Profil de facturation |Nom du profil de facturation utilisé pour définir les propriétés de facture telles que facture, **numéro de bon de commande**et conditions **de**paiement. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">profils de facturation</a> . Pour plus d’informations sur les profils de facturation et sur la façon dont vous pouvez les utiliser pour créer des options de facturation plus flexibles pour votre organisation, consultez la rubrique [Manage Billing Profiles](manage-billing-profiles.md). |
| Numéro de facture |Numéro de facture unique généré par Microsoft utilisé à des fins de suivi. |
| Date de facturation |Date à laquelle la facture est générée, généralement entre cinq et 12 jours après la fin du cycle de facturation. Vous pouvez vérifier la date de votre facture sur la page Détails du profil de facturation. Les frais qui se produisent entre la fin de la période de facturation et la date de facturation sont inclus dans la facture du mois suivant, car ils se trouvent dans la période de facturation suivante. Les dates de début et de fin de la période de facturation de chaque facture sont répertoriées dans le fichier PDF de facture au-dessus de la **synthèse de facturation**.|
| Conditions de paiement |Le mode de paiement de votre facture Microsoft. *Net 30 jours* signifie que vous payez en suivant les instructions figurant sur votre facture, dans les 30 jours suivant la date de facturation. |

## <a name="understand-the-billing-summary"></a>Comprendre le résumé de la facturation

Le **récapitulatif de facturation** affiche le résumé des frais depuis la période de facturation précédente, les crédits appliqués, les taxes et le montant total dû.

| Term | Description |
| --- | --- |
| Frais|Nombre total de produits achetés pour cette période de facturation, ainsi que leurs frais et taxes connexes. Les achats sont regroupés pour fournir un aperçu concis de votre facture. |
| Crédits |Crédits reçus à partir de retours |
| Crédits Azure appliqués |Vos crédits Azure appliqués automatiquement à Azure facturent chaque période de facturation. Si vous n’avez aucun crédit Azure, ce champ est masqué. Pour plus d’informations sur les crédits Azure, consultez la rubrique [Track Microsoft Customer Agreement credit Balance](https://docs.microsoft.com/azure/billing/billing-mca-check-azure-credits-balance). |
| Subtotal |Montant des impôts impayés |
| Taxes |Type et montant de la taxe que vous payez, en fonction du pays de votre profil de facturation. Si vous n’avez pas besoin de payer les taxes, aucune taxe n’est indiquée sur votre facture. |

### <a name="understand-your-charges"></a>Comprendre vos frais

Les pages de frais indiquent le coût réparti par produit. Pour les clients Azure, les frais peuvent être organisés par section facture. Pour plus d’informations sur la façon dont les sections de facturation sont utilisées avec les produits Azure, consultez la rubrique relative aux [factures](https://docs.microsoft.com/azure/billing/billing-mca-overview#invoice-sections) dans la rubrique [prise en main de votre compte de facturation Microsoft Customer Agreement](https://docs.microsoft.com/azure/billing/billing-mca-overview). Dans chaque commande de produit, le coût est réparti par famille de services.

| Term |Description |
| --- | --- |
| Prix unitaire | Prix unitaire effectif du service (en devise de tarification) utilisé pour calculer les frais. Ce prix est unique pour un produit, une famille de services, un compteur et une offre. |
| Compt | Quantité achetée ou consommée pendant la période de facturation |
| Frais/crédits | Montant net des frais après l’application des crédits/remboursements |
| Crédit Azure | Montant des crédits Azure appliqués aux frais/crédits |
| Taux de taxation | Taux de taxation, en fonction du pays |
| Montant de la taxe | Montant de la taxe appliquée à l’achat en fonction du taux de taxation |
| Total | Montant total dû pour l’achat |

Les détails des lignes varient en fonction du type de produit facturé. Par exemple, pour les produits Azure, la quantité de crédits Azure appliqués est affichée. Les produits basés sur le siège indiquent un prix unitaire et une quantité. Les détails de la facture indiquent les produits achetés, l’escompte ou les crédits qui ont été appliqués, le taux et le montant de la taxe, ainsi que les totaux des lignes.

> Total = charges-crédit Azure + taxe

Le montant total dû pour chaque famille de services est calculé en soustrayant les crédits Azure des crédits/frais et en ajoutant la taxe :

> Total = charges/crédits-crédit Azure + taxe

S’il existe des frais Azure sur votre facture pour lesquels vous souhaitez plus d’informations, consultez [la rubrique consulter votre facture de contrat de client Microsoft](https://docs.microsoft.com/azure/cost-management-billing/understand/review-customer-agreement-bill).

## <a name="understand-the-last-invoice-page"></a>Présentation de la dernière page de facturation

### <a name="payment-instructions"></a>Instructions de paiement

Au bas de la facture, vous trouverez des instructions sur le paiement de votre facture. Vous pouvez payer par câble, chèque ou en ligne.

### <a name="publisher-information"></a>Informations sur l’éditeur

Si votre facture comporte des services tiers, le nom et l’adresse de chaque éditeur figurent en bas de votre facture.

## <a name="view-your-online-invoice"></a>Afficher votre facture en ligne

Les factures sont disponibles en ligne. Un lien vers votre facture en ligne est disponible à partir de votre facture PDF, ainsi qu’à partir d’une notification par courrier électronique. La facture en ligne est extensible afin que vous puissiez voir les frais sur votre facture et obtenir plus de détails pour chaque élément. La facture en ligne comprend les éléments suivants :

- Détails de la **tarification** &mdash; Informations supplémentaires, notamment des détails sur les remises et la tarification des produits.

- **Paiement** &mdash; en ligne Vous pouvez choisir d’effectuer un paiement en ligne à partir de la facture.

- Gestion des coûts **Azure** &mdash; Pour les clients Azure, les factures en ligne incluent un lien vers la gestion des coûts Azure.

### <a name="to-view-your-online-invoice"></a>Pour afficher votre facture en ligne

1. Dans le Centre d’administration, accédez à la page **Factures** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Factures & paiements</a>.

2. Pour télécharger la version. pdf de votre facture, sélectionnez **Télécharger le fichier PDF** de la facture dans la ligne correspondant à la facture que vous souhaitez voir.

3. Pour afficher votre facture en ligne, choisissez une facture dans la liste. Vous pouvez également télécharger le fichier. pdf à partir de la page Détails de la facture.

## <a name="invoice-faq"></a>FAQ sur les factures

### <a name="when-is-my-invoice-available"></a>Quand ma facture est-elle disponible ?

Certaines factures sont générées dans les 24 heures suivant l’achat. D’autres factures sont générées à la fin de la période de facturation et incluent tous les éléments de cette période.

### <a name="how-do-i-pay-the-amount-due-on-my-invoice"></a>Comment puis-je payer le montant dû sur ma facture ?

Les instructions de paiement dépendent de votre mode de paiement et sont fournies en bas du document PDF de la facture. Si votre mode de paiement est une carte de crédit, elle est automatiquement facturée dans les 10 jours suivant la date de facturation. Si votre mode de paiement est vérifié ou virement bancaire, reportez-vous aux informations figurant sous **instructions de paiement** dans le fichier PDF.

### <a name="whats-the-difference-between-sold-to-and-bill-to-addresses"></a>Quelle est la différence entre les adresses « vendu à » et « facturation » ?

- **Vendu à :** Entité juridique chargée du paiement et identifiée sur la facture. L’adresse fournie ici est utilisée pour déterminer votre taux de t.v.a. à moins que vous n’ayez choisi de fournir une adresse de livraison alternative pendant votre achat. Pour plus d’informations, consultez la rubrique [Tax information](tax-information.md).
- **Facturation :** Adresse à laquelle la facture physique est envoyée, le cas échéant. Il peut y avoir plusieurs adresses **de facturation** par entité juridique, mais une seule adresse de facturation par profil **de** facturation.

### <a name="what-are-billed-amount-and-amount-due"></a>Qu’est-ce que le « montant facturé » et le « montant dû » ?

- **Montant facturé :** Montant total de l’achat que vous avez effectué.
- **Montant dû :** Solde restant de ce que vous devez.

### <a name="what-is-the-difference-between-service-period-and-billing-period"></a>Quelle est la différence entre « période de service » et « période de facturation » ?

- **Période de service :** La période de temps pendant laquelle vous serez facturé à utiliser le service.
- **Période de facturation :** Période depuis la dernière date de facturation.

### <a name="how-do-i-view-and-print-my-bill"></a>Comment afficher et imprimer mon facture ?

1. Dans la **Billing**  >  page<a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">factures & paiements</a> , sélectionnez une plage de dates de facturation.
2. Pour imprimer ou enregistrer une copie PDF de la facture, sélectionnez **Télécharger le fichier PDF**de la facture, puis imprimez le PDF.

Pour en savoir plus, consultez [la rubrique consulter votre](view-your-bill-or-invoice.md)facture.

### <a name="why-dont-i-see-azure-prepayment-as-a-payment-method"></a>Pourquoi ne puis-je pas voir paiement anticipé Azure comme mode de paiement ?

Azure acompte est disponible comme mode de paiement uniquement pour les produits et services Azure éligibles.

## <a name="need-help-contact-support"></a>Besoin d’aide ? Contactez le support technique.

Si vous avez des questions ou si vous avez besoin d’aide pour vos crédits Azure, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">créez une demande de support technique avec Azure</a>.

Si vous avez des questions ou si vous avez besoin d’aide pour votre facture dans le centre d’administration Microsoft 365, [Contactez le support technique pour les produits professionnels](../../admin/contact-support-for-business-products.md).