---
title: Comprendre votre facture
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
f1_keywords:
- MACBillingBillsPaymentsInvoices
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_billing
search.appverid: MET150
description: Découvrez comment lire et comprendre votre facture pour les produits de productivité Microsoft.
keywords: comptes de facturation, informations sur l’organisation, factures
ms.date: 05/04/2021
ms.openlocfilehash: dc83db458d1d91942352795c9b67578e9f1a2fc2
ms.sourcegitcommit: 967f64dfa1a05f31179c8316b96bfb7758a5d990
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2021
ms.locfileid: "52331934"
---
# <a name="understand-your-bill-or-invoice"></a>Comprendre votre facture

La facture fournit un résumé de vos frais et des instructions de paiement. Vous pouvez [afficher votre facture en ligne](#view-your-online-invoice) dans le centre d’administration Microsoft 365. Vous pouvez également le télécharger au format Portable Document Format (pdf) pour l’envoyer par e-mail.

Pour afficher et imprimer votre facture :

1. Sur la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Factures & paiements</a>, sélectionnez une plage de dates de factures.
2. Pour imprimer ou enregistrer une copie PDF de la facture, sélectionnez **Télécharger le fichier PDF de la facture**, puis imprimez le fichier PDF.

Pour plus d’informations, consultez[Afficher votre facture](view-your-bill-or-invoice.md).

Si vous avez un abonnement Microsoft 365 uniquement, consultez [Comprendre votre facture pour la productivité Microsoft 365](understand-your-invoice2.md).

## <a name="understand-the-invoice-header"></a>Comprendre l’en-tête de la facture

La partie supérieure de la première page indique qui est responsable du paiement, où la facture est envoyée et un résumé des frais.

| Term | Description |
| --- | --- |
| Vendu à |Compte de facturation qui identifie le nom et l’adresse de l’entité juridique responsable du paiement. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">Comptes de facturation</a>, où vous pouvez trouver le contrat de compte et gérer les rôles et les autorisations. |
| Destinataire de la facture |Identifie le destinataire de la facture. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Profils de facturation</a>. Le profil de facturation est également affiché sur la page de facture en ligne, dans la section **Résumé de la facture**. Pour en savoir plus sur les profils de facturation et leur utilisation pour créer des options de facturation plus souples pour votre organisation, consultez [Gérer les profils de facturation](manage-billing-profiles.md). |
| Profil de facturation |Le nom du profil de facturation utilisé pour définir les propriétés de la facture, telles que **Destinataire de la facture**, **Numéro de bon de commande** et les conditions de paiement. Ces informations peuvent être gérées sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=2103629" target="_blank">Profils de facturation</a>. Pour en savoir plus sur les profils de facturation et leur utilisation pour créer des options de facturation plus souples pour votre organisation, consultez [Gérer les profils de facturation](manage-billing-profiles.md). |
| Numéro de facture |Numéro de facture unique généré par Microsoft utilisé à des fins de suivi. |
| Date de facturation |Date de création de la facture, en général de cinq à 12 jours après la fin du cycle de facturation. Vous pouvez consulter votre date de facturation sur la page des détails du profil de facturation. Les frais générés entre la fin de la période de facturation et la date de facturation sont inclus dans la facture du mois suivant, car ils se trouvent dans la période de facturation suivante. Les dates de début et de fin de facturation de chaque facture sont répertoriées dans le fichier PDF de la facture au-dessus de **Résumé de facturation**.|
| Conditions de paiement |Paiement de la facture Microsoft. *30 jours net* signifie que vous payez dans les instructions suivantes sur votre facture, dans les 30 jours suivant la date de facturation. |

## <a name="understand-the-billing-summary"></a>Le résumé de facturation

Le **Résumé de facturation** affiche le résumé des frais depuis la période de facturation précédente, les crédits qui ont été imputés, les taxes et le montant total dû.

| Term | Description |
| --- | --- |
| Frais|Nombre total de produits achetés pour cette période de facturation, ainsi que les frais et taxes correspondants. Les achats sont agrégés pour offrir un affichage concis de votre facture. |
| Crédits |Crédits reçus de retours |
| Crédits Azure appliqués |Vos crédits Azure qui sont automatiquement appliqués à Azure génèrent des frais pour chaque période de facturation. Si vous n’avez pas de crédit Azure, ce champ est masqué. Pour plus d’informations sur les crédits Azure, consultez [Suivre le solde du crédit Azure du contrat client Microsoft](/azure/billing/billing-mca-check-azure-credits-balance). |
| Sous-total |Montant avant impôt dû |
| Taxe |Le type et le montant des taxes payées, selon le pays de votre profil de facturation. Si vous n’avez pas besoin de payer les taxes, aucune taxe n’est affichée sur votre facture. |

### <a name="understand-your-charges"></a>Les frais

Les pages de frais indiquent le coût divisé par produit. Pour les clients Azure, les frais peuvent être organisés par section de facture. Pour plus d’informations sur l’utilisation des sections de facture avec les produits Azure, consultez [Sections de facture](/azure/billing/billing-mca-overview#invoice-sections) dans [Prise en main de votre compte de facturation du contrat client Microsoft](/azure/billing/billing-mca-overview). Au sein de chaque commande de produit, le coût est divisé par la famille de service.

| Term |Description |
| --- | --- |
| Prix unitaire | Le prix unitaire réel du service (dans la devise de tarification) utilisé pour calculer les frais. Ce prix est unique pour un produit, une famille de services, un compteur et une offre. |
| Qté | Quantité achetée ou consommée pendant la période de facturation |
| Frais/crédits | Montant net des frais après les crédits/remboursements |
| Crédit Azure | Montant des crédits Azure appliqués aux frais/crédits |
| Taux d’imposition | Taux d’imposition, selon le pays |
| Montant de l’impôt  | Montant de l’impôt appliqué à l’achat sur la base du taux d’imposition |
| Total | Montant total dû pour l’achat |

Les détails des éléments de ligne varient en fonction du type de produit facturé. Par exemple, pour les produits Azure, la quantité de crédits Azure appliqués est affichée. Les produits basés sur un poste affichent un prix unitaire et une quantité. Les détails de la facture affichent les produits achetés, les remises ou les crédits qui ont été appliqués, le taux et le montant de l’impôt, ainsi que les totaux des éléments de la ligne.

> Total = frais - crédit Azure + impôt

Le montant total dû pour chaque famille de service est calculé en soustrayant les crédits Azure des crédits/frais et en ajoutant les taxes :

> Total = frais/crédits - crédit Azure + impôt

Si vous souhaitez obtenir des informations supplémentaires sur des frais Azure de votre facture , consultez [Réviser la facture du contrat client Microsoft](/azure/cost-management-billing/understand/review-customer-agreement-bill).

## <a name="understand-the-last-invoice-page"></a>La dernière page de la facture

### <a name="payment-instructions"></a>Instructions de paiement

En bas de la facture figurent des instructions sur le mode de paiement de votre facture. Vous pouvez payer par virement, par chèque ou en ligne.

### <a name="publisher-information"></a>Informations sur l’éditeur

Si vous avez des services tiers dans votre facture, le nom et l’adresse de chaque éditeur est noté au bas de votre facture.

## <a name="view-your-online-invoice"></a>Consulter votre facture en ligne

Les factures sont disponibles en ligne. Un lien vers votre facture en ligne est disponible à partir de votre facture PDF et d’une notification par e-mail. La facture en ligne est extensible de sorte que vous puissiez afficher les frais sur votre facture et consulter plus de détails pour chaque article. La facture en ligne inclut :

- **Détails de la tarification**&mdash;Informations supplémentaires, notamment des détails sur les remises et les prix des produits.
- **Paiement en ligne**&mdash;Vous pouvez choisir de faire un paiement en ligne à partir de la facture.
- **Azure Cost Management**&mdash;Pour les clients Azure, les factures en ligne incluent un lien vers Azure Cost Management.

### <a name="to-view-your-online-invoice"></a>Affichage de la facture en ligne

1. Dans le Centre d’administration, accédez à la page **Factures** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Factures & paiements</a>.
2. Pour télécharger la version. pdf de votre facture, sélectionnez **Télécharger la facture PDF** dans la ligne de la facture que vous voulez consulter.
3. Pour afficher votre facture en ligne, choisissez une facture de la liste. Vous pouvez également télécharger le fichier .pdf à partir de la page des détails de la facture.

## <a name="invoice-faq"></a>FAQ des factures

### <a name="when-is-my-invoice-available"></a>Quand ma facture est-elle disponible ?

Certaines factures sont générées dans les 24 heures qui suivent l’achat. D’autres factures sont générées à la fin de la période de facturation et comprennent tous les éléments de cette période.

### <a name="how-do-i-pay-the-amount-due-on-my-invoice"></a>Comment puis-je régler le montant dû sur ma facture ?

Les instructions de paiement dépendent de votre mode de paiement et sont disponibles en bas du fichier PDF de la facture. Si votre mode de paiement est une carte de crédit, elle est automatiquement débitée dans les 10 jours suivant la date de facturation. Si votre mode de paiement est par chèque ou par virement bancaire, consultez les informations sous **Instructions de paiement** dans le fichier PDF.

### <a name="whats-the-difference-between-sold-to-and-bill-to-addresses"></a>Quelle est la différence entre les adresses « Vendu à » et « Destinataire de la facture » ?

- **Vendu à :** L’entité juridique responsable du paiement et identifiée sur la facture. L’adresse fournie ici permet de déterminer votre taux d’imposition, sauf si vous choisissez de fournir une adresse d’expédition alternative pendant votre achat. Si vous souhaitez en savoir plus, consultez l’article [Information sur les taxes](tax-information.md).
- **Destinataire de la facture :** L’adresse à laquelle la facture physique est envoyée, le cas échéant. Il peut y avoir plusieurs adresses de **Destinataire de la facture** par entité juridique, mais une seule adresse de **Destinataire de la facture** par profil de facturation.

### <a name="what-are-billed-amount-and-amount-due"></a>Que signifient « montant facturé » et « montant dû ? »

- **Montant facturé :** Le montant total de l’achat que vous avez effectué.
- **Montant dû :** Le solde restant pour ce que vous devez.

### <a name="what-is-the-difference-between-service-period-and-billing-period"></a>Quelle est la différence entre « période de service » et « période de facturation ? »

- **La période de service :** La période pendant laquelle l'utilisation du service vous est facturée.
- **La période de facturation :** La période écoulée depuis la date de la dernière facture.

### <a name="why-dont-i-see-azure-prepayment-as-a-payment-method"></a>Pourquoi ne puis-je pas voir l’acompte Azure comme mode de paiement ?

L’acompte Azure est disponible comme mode de paiement uniquement pour les produits et services Azure éligibles.

## <a name="need-help-contact-support"></a>Besoin d'aide ? Contacter l’assistance

Si vous avez des questions ou si vous avez besoin d’aide relativement à vos crédits Azure, <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">créer une demande de support avec support Azure</a>.

Si vous avez des questions ou si vous avez besoin d’aide relativement à votre facture dans le centre d’administration Microsoft 365, [contacter le support technique pour les produits professionnels](../../business-video/get-help-support.md).
