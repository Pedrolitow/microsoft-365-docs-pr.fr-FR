---
title: FAQ sur les achats en libre-service
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
- commerce
ms.custom:
- AdminSurgePortfolio
- aka.ms/self-service-purchase-faq
search.appverid:
- MET150
description: Trouvez des réponses aux questions fréquemment posées sur les achats en libre-service.
ms.date: 09/15/2020
ms.openlocfilehash: 81143dfe3794bc4f42bea879905bf08750f498b4
ms.sourcegitcommit: 9f5b136b96b3af4db4cc6f5b1f35130ae60d6b12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "47816924"
---
# <a name="self-service-purchase-faq"></a>FAQ sur les achats en libre-service

L’achat en libre-service permet aux utilisateurs de tester de nouvelles technologies et de développer des solutions qui tirent parti de leurs grandes organisations. Les équipes informatiques et de l’approvisionnement centralisé bénéficient d’une visibilité pour tous les utilisateurs qui achètent et déploient des solutions d’achat en libre-service via le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Les administrateurs peuvent désactiver l’achat en libre-service sur une base par produit via PowerShell. Pour en savoir plus, consultez [la rubrique utiliser AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

L’achat en libre-service est disponible pour Power Platform (Power BI, Power Apps et Power automate), Project et Visio.

> [!NOTE]
> L’achat en libre-service n’est pas disponible en Inde ou pour les clients du secteur public ou de l’éducation. Project et Visio ne sont pas disponibles pour les achats en libre-service au Brésil et en République démocratique du Congo.

## <a name="making-a-self-service-purchase"></a>Réalisation d’un achat en libre-service

### <a name="how-does-a-customer-make-a-self-service-purchase"></a>Comment un client effectue-t-il un achat en libre-service ?

Les clients peuvent faire un achat en libre-service en ligne à partir des sites Web des produits ou des invites d’achat dans l’application. Les clients sont d’abord invités à entrer une adresse de messagerie pour s’assurer qu’ils sont un utilisateur d’un client Azure Active Directory (AD) existant. Ensuite, ils sont dirigés vers la connexion à l’aide de leurs informations d’identification Azure AD. Une fois la connexion terminée, le client est invité à sélectionner le nombre d’abonnements qu’il souhaite acheter et à fournir un paiement par carte de crédit. Une fois l’achat terminé, les utilisateurs peuvent commencer à utiliser leur abonnement. L’acheteur a accès à une vue limitée du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> où il peut attribuer des licences au produit à d’autres membres de son organisation.

### <a name="what-are-the-payment-options-for-self-service-purchases"></a>Quelles sont les options de paiement pour les achats en libre-service ?

Actuellement, la carte de crédit est la seule méthode de paiement disponible. Le paiement par facturation n’est pas pris en charge.

### <a name="who-can-buy-through-self-service-purchase"></a>Qui peut acheter via un achat en libre-service ?

Tout utilisateur disposant d’un compte d’utilisateur non invité dans un client Azure AD géré peut réaliser un achat en libre-service. L’achat en libre-service n’est pas disponible pour les clients qui sont des organisations gouvernementales ou d’éducation. Si cela s’applique à votre organisation, aucune action supplémentaire n’est requise pour contrôler l’achat en libre-service.

Les utilisateurs des organisations ou des marchés qui ne sont pas éligibles à l’achat en libre-service voient un message leur demandant de contacter leur administrateur informatique.

### <a name="can-guest-users-buy-through-self-service-purchase"></a>Les utilisateurs invités peuvent-ils acheter par le biais de l’achat en libre-service ?

Non, les utilisateurs invités ne peuvent pas effectuer un achat en libre-service dans un client dans lequel ils sont invités.

### <a name="can-users-synced-from-an-on-premises-active-directory-buy-through-self-service-purchase"></a>Les utilisateurs peuvent-ils être synchronisés à partir d’un achat Active Directory local acheté via l’achat en libre-service ?

Si un utilisateur dispose d’un compte d’utilisateur actif dans un locataire Azure AD éligible, il peut effectuer un achat en libre-service.

### <a name="who-can-self-service-purchasers-assign-licenses-to"></a>Qui peut attribuer des licences aux acheteurs en libre-service ?

Les acheteurs en libre-service peuvent uniquement attribuer des licences aux utilisateurs dans le même client Azure AD. L’acheteur a accès à une vue limitée du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> pour attribuer des licences. Les acheteurs peuvent attribuer des licences aux produits qu’ils ont achetés par le biais d’un achat en libre-service et ne peuvent les affecter qu’à des utilisateurs appartenant au même client Azure AD.

### <a name="where-does-the-self-service-purchaser-see-and-manage-their-purchases"></a>Où est-ce que l’acheteur en libre-service voit et gère ses achats ?

Les acheteurs en libre-service peuvent gérer leurs achats dans l’affichage limité du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Les acheteurs peuvent toujours accéder au centre d’administration à partir de la vignette **administrateur** dans le lanceur d’applications intégré à toutes les applications Microsoft 365 et Dynamics online. Les acheteurs peuvent consulter les achats qu’ils ont effectués, acheter des abonnements supplémentaires au même service et attribuer des licences pour ces abonnements à d’autres utilisateurs au sein de leur organisation. En outre, les acheteurs peuvent afficher et payer leur facture, mettre à jour leur mode de paiement et annuler leur abonnement.

## <a name="pricing"></a>Tarification

### <a name="what-is-the-pricing-for-self-service-purchases"></a>Quels sont les tarifs pour les achats en libre-service ?

Les tarifs de chaque produit pour l’achat en libre-service sont disponibles sur le site Web de Microsoft. Les prix sont également affichés dans le cadre de l’expérience de validation lorsque les utilisateurs effectuent un achat en libre-service. Ces prix peuvent différer des prix qu’une organisation paie lorsqu’elle effectue des achats ou des prix centraux offerts par un partenaire.

### <a name="who-is-responsible-for-payment"></a>Qui est responsable du paiement ?

La personne qui achète l’abonnement par le biais de l’achat en libre-service est la personne facturée et responsable du paiement en fonction des conditions et de la tarification de l’achat.

## <a name="admin-capabilities"></a>Fonctionnalités d’administration

### <a name="what-capabilities-does-an-admin-have-for-self-service-purchases"></a>Quelles sont les fonctionnalités dont dispose un administrateur pour les achats en libre-service ?

Les administrateurs peuvent afficher tous les achats en libre-service effectués dans leur organisation dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Ils peuvent voir le produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Dans le centre d’administration Power Platform, les administrateurs peuvent également afficher la capacité des achats en libre-service. Si cela est nécessaire pour leur organisation, les administrateurs peuvent désactiver l’achat en libre-service sur une base par produit via PowerShell. Les administrateurs ont les mêmes stratégies de gestion des données et d’accès que les produits achetés via l’achat en libre-service ou de manière centralisée.

Les administrateurs peuvent également contrôler si les utilisateurs de leur organisation peuvent faire des achats en libre-service. Pour plus d’informations, voir [use AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

### <a name="how-is-microsoft-respecting-data-governance-and-compliance-by-enabling-self-service-purchase"></a>Comment Microsoft respecte-t-il la gouvernance et la conformité des données en activant l’achat en libre-service ?

Les administrateurs maintiennent le contrôle sur les services et les produits disponibles au sein de leur client en fonction de leurs exigences en matière de gouvernance et de conformité des données. Toutes les stratégies de gestion de données et d’accès que votre organisation a activée s’appliquent aux services achetés en libre-service disponibles.

### <a name="who-owns-the-product-data-created-from-self-service-purchases"></a>Qui est propriétaire des données de produits créées à partir des achats en libre-service ?

Les données créées à partir de produits achetés via un achat en libre-service sont détenues et contrôlées par l’organisation.

### <a name="how-do-i-centralize-the-purchases-made-through-self-service-purchase"></a>Comment centraliser les achats effectués via un achat en libre-service ?

Les administrateurs peuvent attribuer des licences existantes ou acheter des abonnements supplémentaires de produits achetés en libre-service via des accords existants et une tarification pour les utilisateurs affectés à des achats en libre-service. Après avoir affecté ces licences achetées de manière centralisée, les administrateurs peuvent demander à ce que les acheteurs annulent leurs abonnements existants.

### <a name="where-does-the-admin-see-self-service-purchases"></a>Où l’administrateur voit-il les achats en libre service ?

Les administrateurs globaux et de facturation peuvent voir les abonnements achetés par le biais de l’achat en libre-service dans **facturation**de  >  **vos produits** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration 365 de Microsoft</a>. Ils peuvent filtrer la liste produits pour afficher uniquement les abonnements achetés par le biais de l’approvisionnement central ou pour inclure les abonnements achetés par le biais de l’achat en libre-service.

Les administrateurs peuvent voir le produit, le nom de l’acheteur, l’abonnement acheté, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés.

## <a name="support-and-training"></a>Support et formation

### <a name="are-customers-it-departments-or-partners-expected-to-support-products-bought-through-self-service-purchase"></a>Les services ou partenaires informatiques des clients sont-ils censés prendre en charge les produits achetés par le biais de l’achat en libre-service ?

Il n’est pas prévu que les services et partenaires informatiques prennent en charge les produits achetés par le biais de l’achat en libre-service. Microsoft offre une prise en charge standard pour les acheteurs en libre-service.

### <a name="if-a-self-service-purchaser-calls-support-does-that-use-the-customers-premier-support-incidents"></a>Si un acheteur en libre-service appelle la prise en charge, utilise-t-il les incidents de support premier du client ?

Les acheteurs en libre-service n’utiliseront pas les incidents de support premier du client pour recevoir un support pour les achats en libre-service.

### <a name="how-are-users-expected-to-receive-training-on-the-products-they-buy-through-self-service-purchase"></a>Comment les utilisateurs sont-ils censés recevoir une formation sur les produits qu’ils achètent via l’achat en libre-service ?

Les sites Web des produits fournissent une formation complète pour les utilisateurs. Les produits ont assisté à des formations, des documents, des exemples et des communautés fortes pour obtenir des réponses et des conseils directement auprès d’autres utilisateurs.

### <a name="what-happens-to-a-self-service-purchase-if-a-user-leaves-the-organization"></a>Qu’arrive-t-il à un achat en libre-service si un utilisateur quitte l’Organisation ?

Si la personne qui a acheté le produit acheté en libre-service quitte l’organisation, les utilisateurs valides continuent d’utiliser pleinement le produit pendant la durée de l’abonnement. L’abonnement reste actif jusqu’à ce que l’acheteur l’annule directement ou qu’un administrateur demande l’annulation de l’abonnement via le support technique. Les administrateurs peuvent également choisir d’attribuer une licence achetée de manière centralisée aux utilisateurs de l’abonnement annulé.

## <a name="partners"></a>Partenaires

### <a name="whats-the-role-of-microsofts-partners-in-self-service-purchases"></a>Quel est le rôle des partenaires de Microsoft dans les achats en libre-service ?

Les partenaires qui disposent de privilèges d’administration délégués peuvent voir les achats en libre-service dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration 365 de Microsoft</a>, tout comme un administrateur. Les partenaires peuvent aider une organisation qui souhaite centraliser les produits achetés via des achats en libre-service. En outre, les partenaires peuvent proposer des solutions pour étendre les capacités d’un achat en libre-service.