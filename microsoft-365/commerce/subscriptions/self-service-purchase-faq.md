---
title: FAQ sur les achats en libre-service
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- commerce
search.appverid:
- MET150
description: Trouvez des réponses aux questions fréquemment posées sur les achats en libre-service.
ms.custom: aka.ms/self-service-purchase-faq
ms.openlocfilehash: 1a8cea3b11ecdc6e3ac6d382dc8ffe92c84e187a
ms.sourcegitcommit: e47694dedf7e213167d3d979a44c07c668bba543
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "41932274"
---
# <a name="self-service-purchase-faq"></a>FAQ sur les achats en libre-service

> [!NOTE]
> Les informations contenues dans cet article s’appliquent uniquement aux abonnements Microsoft Power Platform (Power BI, Power Apps et Power automate).

Les achats en libre-service sont désormais disponibles pour Power Platform aux États-Unis, en Australie, au Canada et au Japon.

## <a name="general"></a>Général

### <a name="what-changes-did-microsoft-announce-around-self-service-purchases-for-the-power-platform-products"></a>Quelles sont les modifications apportées par Microsoft pour les achats en libre-service pour les produits Power Platform ?

Le 19 novembre, nous avons fourni aux administrateurs informatiques un moyen de désactiver les achats en libre-service sur une base par produit via PowerShell. Pour savoir comment l’utiliser, voir [use AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

Pour fournir plus de temps à la préparation de cette modification, nous mettons à jour le lancement des fonctionnalités d’achat en libre-service pour les produits Power Platform afin de commencer avec Power BI le 14 janvier pour tous les clients du nuage commercial.  

À partir du 14 janvier 2020, les fonctionnalités d’achat en libre-service, d’abonnement et de gestion des licences pour les produits Power Platform (Power BI, Power Apps et Power automate) seront disponibles pour les clients du nuage commercial aux États-Unis. L’achat en libre-service permet aux utilisateurs de tester de nouvelles technologies et de développer des solutions qui profiteront aux grandes organisations. Cette fonctionnalité ne sera pas disponible pour les clients des États-Unis qui sont des pouvoirs publics, des organisations à but non lucratif ou l’éducation, pour le moment. Les équipes informatiques et les équipes informatiques centrales auront une visibilité pour tous les utilisateurs achetant et déployant des solutions d’achat en libre-service via le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>, et pourront désactiver les achats en libre-service sur une base par produit via PowerShell.

### <a name="why-is-microsoft-adding-a-self-service-purchase-option-for-the-power-platform-products"></a>Pourquoi Microsoft ajoute-t-il une option d’achat en libre-service pour les produits Power Platform ?

Dans le monde actuel, les utilisateurs finaux et les services cherchent de plus en plus à acheter des solutions technologiques. Nous avons reçu de nombreuses demandes de ces clients pour permettre l’achat en libre-service des produits Power Platform. Nous répondons à ce besoin du client tout en équilibrant les besoins des administrateurs informatiques, qui ont souvent des pertes de visibilité et de contrôle lorsque les utilisateurs de leur organisation adoptent des solutions tierces sans leur connaissance. Avec la fonctionnalité libre-service à venir pour les produits Power Platform, les administrateurs informatiques disposeront d’une visibilité complète sur tous les achats en libre-service effectués au sein de leur organisation et les stratégies de gouvernance des données définies au niveau de l’Organisation seront allouées à abonnements achetés via self-service. Les administrateurs peuvent également affecter des licences existantes, ou acheter des abonnements supplémentaires, des produits de plateforme énergétique via des accords existants et une tarification pour les utilisateurs affectés à des achats en libre-service. Après avoir affecté ces licences achetées de manière centralisée, les administrateurs peuvent demander à ce que les acheteurs annulent leurs abonnements existants. Microsoft explore les moyens de simplifier et de rationaliser ce processus pour les administrateurs à l’avenir.

### <a name="which-power-platform-products-are-available-for-self-service-purchase"></a>Quels sont les produits Power Platform disponibles pour l’achat en libre-service ?

Microsoft a lancé un achat en libre-service pour Power Platform (Power BI, Power Apps, and Power Self) aux clients des États-Unis, les autres marchés devenant disponibles au cours des prochains mois. Cette fonctionnalité ne sera pas disponible pour les clients des États-Unis qui sont des pouvoirs publics, des organisations à but non lucratif ou l’éducation, pour le moment.

### <a name="will-self-service-purchase-be-enabled-for-services-beyond-the-power-platform-products"></a>Est-ce que l’achat en libre-service sera activé pour les services au-delà des produits Power Platform ?

Pour le moment, seuls les produits de la famille Power Platform sont offerts par le biais de l’achat en libre-service.

## <a name="making-a-self-service-purchase"></a>Réalisation d’un achat en libre-service

### <a name="how-does-a-customer-make-a-self-service-purchase"></a>Comment un client effectue-t-il un achat en libre-service ?

Les clients pourront effectuer un achat en libre-service en ligne à partir des sites Web de Microsoft Power BI, Power Apps et Power Automated Automated. Les clients seront d’abord invités à entrer une adresse de messagerie pour s’assurer qu’ils sont un utilisateur d’un client Azure Active Directory (AD) existant. Ensuite, ils seront dirigés vers une connexion à l’aide de leurs informations d’identification Azure AD. Une fois connecté, le client est invité à sélectionner le nombre d’abonnements qu’il souhaite acheter et à fournir un paiement par carte de crédit. Une fois l’achat terminé, les utilisateurs peuvent commencer à utiliser leur abonnement. L’acheteur pourra également accéder à une vue limitée du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> où il peut autoriser d’autres personnes de son organisation à utiliser le produit.

### <a name="what-are-the-payment-options-for-self-service-purchases"></a>Quelles sont les options de paiement pour les achats en libre-service ?

Actuellement, la carte de crédit est la seule méthode de paiement disponible. Le paiement par facturation n’est pas pris en charge.

### <a name="who-can-buy-through-self-service-purchase"></a>Qui peut acheter via un achat en libre-service ?

Tout utilisateur disposant d’un compte d’utilisateur non invité dans un client Azure AD géré peut acheter. Cette fonctionnalité ne sera actuellement pas disponible pour les clients qui sont des pouvoirs publics, des organisations à but non lucratif ou des établissements scolaires. Si cela s’applique à votre organisation, aucune action supplémentaire n’est requise pour contrôler l’achat en libre-service pour le moment.

Les utilisateurs des organisations ou des marchés qui ne sont pas éligibles à l’achat en libre-service verront un message leur demandant de contacter leur administrateur informatique comme ils le font aujourd’hui.

### <a name="can-guest-users-buy-through-self-service-purchase"></a>Les utilisateurs invités peuvent-ils acheter par le biais de l’achat en libre-service ?

Non, les utilisateurs invités ne peuvent pas effectuer un achat en libre-service dans un client dans lequel ils sont invités.

### <a name="can-users-synced-from-an-on-premises-active-directory-buy-through-self-service-purchase"></a>Les utilisateurs peuvent-ils être synchronisés à partir d’un achat Active Directory local acheté via l’achat en libre-service ?

Si un utilisateur dispose d’un compte d’utilisateur actif dans un locataire Azure AD éligible, il peut effectuer un achat en libre-service.

### <a name="who-can-self-service-purchasers-assign-licenses-to"></a>Qui peut attribuer des licences aux acheteurs en libre-service ?

Les acheteurs en libre-service pourront uniquement attribuer des licences aux utilisateurs dans le même client Azure AD. L’acheteur pourra accéder à une vue limitée du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> pour attribuer des licences. Ils n’auront qu’une visibilité et peuvent attribuer des licences aux produits qu’ils ont achetés par le biais de l’achat en libre-service, et ils ne pourront attribuer ces licences qu’aux utilisateurs du même client Azure AD.

### <a name="where-does-the-self-service-purchaser-see-and-manage-their-purchases"></a>Où est-ce que l’acheteur en libre-service voit et gère ses achats ?

Les acheteurs en libre-service peuvent gérer leurs achats dans l’affichage limité du <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Les acheteurs peuvent toujours accéder au centre d’administration à partir de la vignette **administrateur** dans le lanceur d’applications Office 365 intégré à toutes les applications Office 365 et Dynamics online. Ils peuvent voir les achats qu’ils ont effectués, acheter des abonnements supplémentaires au même service et attribuer des licences pour ces abonnements à d’autres utilisateurs au sein de leur organisation. En outre, les acheteurs peuvent afficher et payer leur facture, mettre à jour leur mode de paiement et annuler leur abonnement.

**Vue du centre d’administration 365 limité pour les acheteurs en libre-service :**

![Capture d’écran du centre d’administration Microsoft 365.](../media/MACBillingProductsServicesSelfServicePurchaseIW.png)

## <a name="pricing"></a>Tarification

### <a name="what-is-the-pricing-for-self-service-purchases"></a>Quels sont les tarifs pour les achats en libre-service ?

Les tarifs de chacun des produits Power Platform pour les achats en libre-service sont disponibles sur le site Web de Microsoft et s’affichent également dans le cadre de l’expérience de validation lors de la réalisation d’un achat en libre-service. Ces prix peuvent différer des prix qu’une organisation paie lorsqu’elle effectue des achats ou des prix centraux offerts par un partenaire.

### <a name="who-is-responsible-for-payment"></a>Qui est responsable du paiement ?

La personne qui achète l’abonnement par le biais d’un achat en libre-service est facturée et est responsable du paiement en fonction des conditions et de la tarification de l’achat.

## <a name="admin-capabilities"></a>Fonctionnalités d’administration

### <a name="what-capabilities-does-an-admin-have-for-self-service-purchases"></a>Quelles sont les fonctionnalités dont dispose un administrateur pour les achats en libre-service ?

Les administrateurs peuvent afficher tous les achats en libre-service effectués dans leur organisation dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a>. Ils peuvent voir le produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Dans le centre d’administration Power Platform, les administrateurs peuvent également afficher la capacité des achats en libre-service. Si cela est nécessaire pour leur organisation, les administrateurs pourront désactiver les achats en libre-service sur une base par produit via PowerShell. Les administrateurs ont les mêmes stratégies de gestion des données et d’accès que les produits achetés via l’achat en libre-service ou de manière centralisée.

Les administrateurs peuvent également contrôler si les utilisateurs de leur organisation peuvent faire des achats en libre-service. Pour plus d’informations, voir [use AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

### <a name="how-is-microsoft-respecting-data-governance-and-compliance-by-enabling-self-service-purchase"></a>Comment Microsoft respecte-t-il la gouvernance et la conformité des données en activant l’achat en libre-service ?

Les administrateurs maintiennent le contrôle sur les services et les produits activés au sein de leur client en fonction de leurs exigences en matière de gouvernance et de conformité des données. De plus, toutes les stratégies de gestion de données et d’accès, que votre organisation a activées, s’appliquent aux services activés en libre-service.

### <a name="who-owns-the-product-data-created-from-self-service-purchases"></a>Qui est propriétaire des données de produits créées à partir des achats en libre-service ?

Les données créées à partir de produits achetés via un achat en libre-service sont détenues et contrôlées par l’organisation.

### <a name="how-do-i-centralize-the-purchases-made-through-self-service-purchase"></a>Comment centraliser les achats effectués via un achat en libre-service ?

Les administrateurs peuvent attribuer des licences existantes ou acheter des abonnements supplémentaires aux produits Power Platform (Power BI, Power Apps et Power automate) par le biais des accords et tarifs existants pour les utilisateurs affectés à des achats en libre-service. Après avoir affecté ces licences achetées de manière centralisée, les administrateurs peuvent demander à ce que les acheteurs annulent leurs abonnements existants. Microsoft explore les moyens de simplifier et de rationaliser ce processus pour les administrateurs à l’avenir.

### <a name="where-does-the-admin-see-self-service-purchases"></a>Où l’administrateur voit-il les achats en libre service ?

Les administrateurs globaux et de facturation peuvent voir les abonnements achetés par le biais de l’achat en libre-service dans les produits de **facturation** > **& services** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration 365 de Microsoft</a> , ainsi que tous les autres abonnements achetés via le service d’approvisionnement central Ils peuvent filtrer la liste sur les abonnements achetés par le biais de l’approvisionnement central ou inclure les abonnements achetés via un achat en libre-service.

Les administrateurs peuvent voir le produit, le nom de l’acheteur, l’abonnement acheté, la date d’expiration, l’historique des commandes, le prix d’achat et les utilisateurs affectés.

## <a name="support-and-training"></a>Support et formation

### <a name="are-customers-it-departments-or-partners-expected-to-support-products-bought-through-self-service-purchase"></a>Les services ou partenaires informatiques des clients sont-ils censés prendre en charge les produits achetés par le biais de l’achat en libre-service ?

Il n’est pas prévu que les services et partenaires informatiques prennent en charge les produits achetés par le biais de l’achat en libre-service. Microsoft fournira une prise en charge standard pour les acheteurs en libre-service.

### <a name="if-a-self-service-purchaser-calls-support-will-they-use-the-customers-premier-support-incidents"></a>Si un acheteur en libre-service appelle la prise en charge, sera-t-il utilisé par les incidents de support premier du client ?

Les acheteurs en libre-service n’utiliseront pas les incidents de support premier du client pour recevoir un support pour les achats en libre-service.

### <a name="how-are-users-expected-to-receive-training-on-the-products-they-buy-through-self-service-purchase"></a>Comment les utilisateurs sont-ils censés recevoir une formation sur les produits qu’ils achètent via l’achat en libre-service ?

Une formation complète pour les utilisateurs est fournie sur les sites Web Microsoft Power BI, Power Apps et Power Automated Automated. Les produits ont assisté à des formations, des documents, des exemples et des communautés fortes pour obtenir des réponses et des conseils directement auprès d’autres utilisateurs.

### <a name="what-happens-to-a-self-service-purchase-if-a-user-leaves-the-organization"></a>Qu’arrive-t-il à un achat en libre-service si un utilisateur quitte l’Organisation ?

Les utilisateurs valides continueront à utiliser pleinement l’achat en libre-service pendant la durée de l’abonnement. L’abonnement reste actif jusqu’à ce que l’acheteur l’annule directement ou qu’un administrateur demande l’annulation de l’abonnement par le biais du support technique. Les administrateurs peuvent également choisir d’attribuer une licence achetée de manière centralisée aux utilisateurs de l’abonnement annulé.

## <a name="partners"></a>Partenaires

### <a name="whats-the-role-of-microsofts-partners-in-self-service-purchases"></a>Quel est le rôle des partenaires de Microsoft dans les achats en libre-service ?

Les partenaires qui disposent de privilèges d’administration délégués peuvent voir les achats en libre-service dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration 365 de Microsoft</a>, tout comme un administrateur. Les partenaires peuvent aider une organisation qui souhaite centraliser les produits achetés via des achats en libre-service. En outre, les partenaires peuvent proposer des solutions pour étendre les capacités d’un achat en libre-service.