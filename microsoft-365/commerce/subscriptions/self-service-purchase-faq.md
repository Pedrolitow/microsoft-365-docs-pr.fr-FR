---
title: FAQ sur l’achat en libre-service
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
# <a name="self-service-purchase-faq"></a>FAQ sur l’achat en libre-service

L’achat en libre-service permet aux utilisateurs d’essayer de nouvelles technologies et de développer des solutions qui, en fin de compte, profitent à leurs grandes organisations. L’approvisionnement centralisé et les équipes informatiques ont une visibilité pour tous les utilisateurs qui achètent et déploient des solutions d’achat en libre-service via le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365.</a> Les administrateurs peuvent désactiver les achats en libre-service par produit via PowerShell. Pour plus d’informations, voir [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce.](allowselfservicepurchase-powershell.md)

L’achat en libre-service est disponible pour Power Platform (Power BI, Power Apps et Power Automate), Project et Visio.

> [!NOTE]
> L’achat en libre-service n’est pas disponible en Inde, ni pour les clients du secteur public ou de l’éducation. Project et Visio ne sont pas disponibles pour l’achat en libre-service au Brésil et en République yougoslave du Congo.

## <a name="making-a-self-service-purchase"></a>Achat en libre-service

### <a name="how-does-a-customer-make-a-self-service-purchase"></a>Comment un client achète-t-il des services libre-service ?

Les clients peuvent effectuer un achat en libre-service en ligne à partir des sites web du produit ou à partir d’invites d’achat dans l’application. Les clients sont d’abord invités à entrer une adresse de messagerie pour s’assurer qu’ils sont un utilisateur dans un client Azure Active Directory (AD) existant. Ensuite, ils sont dirigés vers la connexion à l’aide de leurs informations d’identification Azure AD. Après la signature, le client est invité à sélectionner le nombre d’abonnements qu’il souhaite acheter et à fournir le paiement par carte de crédit. Une fois l’achat terminé, ils peuvent commencer à utiliser leur abonnement. L’acheteur a accès à une vue limitée du Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365</a> où il peut attribuer des licences au produit à d’autres personnes de son organisation.

### <a name="what-are-the-payment-options-for-self-service-purchases"></a>Quelles sont les options de paiement pour les achats en libre-service ?

Actuellement, la carte de crédit est le seul moyen de paiement disponible. Le paiement par facturation n’est pas pris en charge.

### <a name="who-can-buy-through-self-service-purchase"></a>Qui peut acheter via un achat en libre-service ?

Tout utilisateur avec un compte d’utilisateur non invité dans un client Azure AD géré peut effectuer un achat en libre-service. L’achat en libre-service n’est pas disponible pour les locataires qui sont des organisations gouvernementales ou d’éducation. Si cela s’applique à votre organisation, aucune action supplémentaire n’est requise pour contrôler l’achat en libre-service.

Les utilisateurs d’organisations ou de marchés qui ne sont pas éligibles à un achat en libre-service voient un message leur demandant de contacter leur administrateur informatique.

### <a name="can-guest-users-buy-through-self-service-purchase"></a>Les utilisateurs invités peuvent-ils acheter via un achat en libre-service ?

Non, les utilisateurs invités ne peuvent pas effectuer un achat en libre-service dans un client dans lequel ils sont invités.

### <a name="can-users-synced-from-an-on-premises-active-directory-buy-through-self-service-purchase"></a>Les utilisateurs synchronisés à partir d’un annuaire Active Directory local peuvent-ils acheter via un achat en libre-service ?

Si un utilisateur dispose d’un compte d’utilisateur actif dans un client Azure AD éligible, il peut effectuer un achat en libre-service.

### <a name="who-can-self-service-purchasers-assign-licenses-to"></a>À qui les acheteur en libre-service peuvent-ils attribuer des licences ?

Les acheteur en libre-service peuvent uniquement attribuer des licences aux utilisateurs du même client Azure AD. L’acheteur a accès à une vue limitée du Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365</a> pour attribuer des licences. Les acheteur peuvent attribuer des licences aux produits qu’ils ont achetés par le biais d’un achat en libre-service, et peuvent uniquement attribuer ces licences aux utilisateurs du même client Azure AD.

### <a name="where-does-the-self-service-purchaser-see-and-manage-their-purchases"></a>Où l’acheteur en libre-service voit-il et gère-t-il ses achats ?

Les acheteur en libre-service peuvent gérer leurs achats dans l’affichage limité du Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365.</a> Les acheteur peuvent toujours se rendre  au Centre d’administration à partir de la vignette Administrateur dans le lanceur d’applications intégré à toutes les applications Microsoft 365 et Dynamics Online. Les acheteur peuvent afficher les achats qu’ils ont effectués, acheter des abonnements supplémentaires au même service et attribuer des licences pour ces abonnements à d’autres utilisateurs de leur organisation. En outre, les acheteur peuvent afficher et payer leur facture, mettre à jour leur mode de paiement et annuler leur abonnement.

## <a name="pricing"></a>Tarification

### <a name="what-is-the-pricing-for-self-service-purchases"></a>Quel est le prix des achats en libre-service ?

Le prix de chacun des produits achetés en libre-service est disponible sur le site web de Microsoft. Les prix s’affichent également dans le cadre de l’expérience d’achat lorsque les utilisateurs font un achat en libre-service. Ces prix peuvent différer des prix payés par une organisation lors de l’achat centralisé ou des prix proposés par un partenaire.

### <a name="who-is-responsible-for-payment"></a>Qui est responsable du paiement ?

La personne qui achète l’abonnement par le biais d’un achat en libre-service est la personne facturée et responsable du paiement en fonction des termes et du prix de l’achat.

## <a name="admin-capabilities"></a>Fonctionnalités d’administration

### <a name="what-capabilities-does-an-admin-have-for-self-service-purchases"></a>Quelles fonctionnalités un administrateur a-t-il pour les achats en libre-service ?

Les administrateurs peuvent afficher tous les achats en libre-service effectués dans leur organisation dans le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365.</a> Ils peuvent voir le produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Dans le Centre d’administration Power Platform, les administrateurs peuvent également afficher la capacité des achats en libre-service. Si nécessaire pour leur organisation, les administrateurs peuvent désactiver les achats en libre-service par produit via PowerShell. Les administrateurs ont les mêmes stratégies d’accès et de gestion des données que les produits achetés via un achat en libre-service ou de manière centralisée.

Les administrateurs peuvent également contrôler si les utilisateurs de leur organisation peuvent effectuer des achats en libre-service. Pour plus d’informations, voir [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce.](allowselfservicepurchase-powershell.md)

### <a name="how-is-microsoft-respecting-data-governance-and-compliance-by-enabling-self-service-purchase"></a>Comment Microsoft respecte-t-il la gouvernance et la conformité des données en activant l’achat en libre-service ?

Les administrateurs conservent le contrôle sur les services et produits disponibles au sein de leur client en fonction de leurs exigences en matière de gouvernance et de conformité des données. Toutes les stratégies de gestion des données et d’accès que votre organisation a désactivées s’appliquent aux services achetés en libre-service disponibles.

### <a name="who-owns-the-product-data-created-from-self-service-purchases"></a>À qui appartient les données de produit créées à partir d’achats en libre-service ?

Les données créées à partir de produits achetés via un achat en libre-service sont la propriété et le contrôle de l’organisation.

### <a name="how-do-i-centralize-the-purchases-made-through-self-service-purchase"></a>Comment centraliser les achats effectués via un achat en libre-service ?

Les administrateurs peuvent attribuer des licences existantes ou acheter des abonnements supplémentaires de produits d’achat en libre-service via des contrats et des tarifs existants pour les utilisateurs affectés à des achats en libre-service. Après avoir attribué ces licences achetées de manière centralisée, les administrateurs peuvent demander aux acheteur d’annuler leurs abonnements existants.

### <a name="where-does-the-admin-see-self-service-purchases"></a>Où l’administrateur voit-il les achats en libre-service ?

Les administrateurs globaux et de facturation peuvent voir les abonnements achetés via un achat en libre-service dans **Facturation** Vos produits dans le Centre d’administration  >   <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365.</a> Ils peuvent filtrer la liste des produits pour afficher uniquement les abonnements achetés via l’approvisionnement central, ou pour inclure les abonnements achetés via un achat en libre-service.

Les administrateurs peuvent voir le produit, le nom de l’acheteur, l’abonnement acheté, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés.

## <a name="support-and-training"></a>Support et formation

### <a name="are-customers-it-departments-or-partners-expected-to-support-products-bought-through-self-service-purchase"></a>Les services informatiques ou les partenaires des clients sont-ils censés prendre en charge les produits achetés via un achat en libre-service ?

Les services informatiques et les partenaires ne sont pas censés prendre en charge les produits achetés par le biais d’un achat en libre-service. Microsoft fournit une prise en charge standard pour les acheteur en libre-service.

### <a name="if-a-self-service-purchaser-calls-support-does-that-use-the-customers-premier-support-incidents"></a>Si un acheteur en libre-service appelle le support, utilise-t-il les incidents du support Premier du client ?

Les acheteur en libre-service n’utiliseront pas les incidents du support Premier d’un client pour recevoir du support pour ses achats en libre-service.

### <a name="how-are-users-expected-to-receive-training-on-the-products-they-buy-through-self-service-purchase"></a>Comment les utilisateurs sont-ils censés recevoir une formation sur les produits qu’ils achètent par le biais d’un achat en libre-service ?

Une formation complète pour les utilisateurs est fournie sur les sites web du produit. Les produits ont guidé l’apprentissage, la documentation, les exemples et les communautés fortes pour obtenir des réponses et des conseils directement auprès d’autres utilisateurs.

### <a name="what-happens-to-a-self-service-purchase-if-a-user-leaves-the-organization"></a>Qu’advient-il d’un achat en libre-service si un utilisateur quitte l’organisation ?

Si la personne qui a acheté à l’origine le produit d’achat en libre-service quitte l’organisation, les utilisateurs valides continuent à utiliser entièrement le produit pendant toute la durée de l’abonnement. L’abonnement reste actif jusqu’à ce que l’acheteur l’annule directement ou qu’un administrateur demande l’annulation de l’abonnement par le biais du support client. Les administrateurs peuvent également choisir d’attribuer une licence achetée de manière centralisée aux utilisateurs de l’abonnement annulé.

## <a name="partners"></a>Partenaires

### <a name="whats-the-role-of-microsofts-partners-in-self-service-purchases"></a>Quel est le rôle des partenaires de Microsoft dans les achats en libre-service ?

Les partenaires qui ont des privilèges d’administration délégués peuvent voir les achats en libre-service dans le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365,</a>comme un administrateur. Les partenaires peuvent aider à prendre en charge une organisation qui souhaite centraliser les produits achetés via des achats en libre-service. En outre, les partenaires peuvent proposer des solutions pour étendre les fonctionnalités d’un achat en libre-service.