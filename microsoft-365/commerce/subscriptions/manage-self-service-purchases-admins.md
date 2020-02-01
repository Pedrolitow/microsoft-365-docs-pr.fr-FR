---
title: Gérer les achats en libre-service (administrateurs)
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
description: Les administrateurs peuvent apprendre à gérer les achats en libre-service effectués par les utilisateurs au sein de leur organisation.
ms.openlocfilehash: 5db942b42f398e8951da43add7013569af52c53f
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41594108"
---
# <a name="manage-self-service-purchases-admin"></a>Gérer les achats en libre-service (administrateur)

En tant qu’administrateur, vous pouvez voir les achats en libre-service effectués par les membres de votre organisation. Vous pouvez voir le produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Si cela est nécessaire pour votre organisation, vous pouvez désactiver l’achat en libre-service sur une base par produit via PowerShell. Vous disposez des mêmes stratégies de gestion des données et d’accès que les produits achetés via l’achat en libre-service ou de manière centralisée.

Vous pouvez également contrôler si les utilisateurs de votre organisation peuvent faire des achats en libre-service. Pour plus d’informations, voir [use AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Afficher les abonnements en libre-service

1. Dans le centre d’administration, accédez à la page produits de **facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">& services</a> .

2. En regard d' **affiner les résultats**, dans la liste déroulante **type de compte** , choisissez **self-service**.

3. Pour afficher plus de détails sur un abonnement, choisissez-en un dans la liste.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Afficher les personnes ayant des licences pour un abonnement achat libre-service

1. Dans le centre d’administration, accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">licences</a> de **facturation** > .

2. Choisissez l’icône de filtre, puis choisissez **self-service**.

3. Sélectionnez un produit pour afficher les licences attribuées à des personnes.

    > [!NOTE]
    > S’il existe plusieurs achats pour un produit, ce produit n’est répertorié qu’une seule fois et la colonne **quantité disponible** indique le total de tous les abonnements achetés pour ce produit.

4. La liste des **utilisateurs** est regroupée selon le nom des personnes qui ont effectué des achats en libre-service.

5. Pour exporter une liste d’utilisateurs avec des licences pour ces abonnements, choisissez les abonnements que vous souhaitez exporter, puis choisissez **Exporter les utilisateurs**.

## <a name="disable-or-enable-self-service-purchases"></a>Désactiver ou activer les achats en libre-service

Vous pouvez désactiver ou activer les achats en libre-service pour les utilisateurs de votre organisation. Le module PowerShell **MSCommerce** inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent faire des achats en libre-service et pour quels produits.

Vous pouvez utiliser le module PowerShell **MSCommerce** pour :

- Afficher l’État par défaut de **** la valeur &mdash; du paramètre AllowSelfServicePurchase, qu’elle soit activée ou désactivée par le produit
- Afficher la liste des produits applicables et indiquer si les achats en libre-service sont activés ou désactivés
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

Pour plus d’informations, voir [use AllowSelfServicePurchase pour le module MSCommerce PowerShell](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Centralisation des licences sous un seul abonnement

Vous pouvez attribuer des licences existantes ou acheter des abonnements supplémentaires via des accords existants pour les utilisateurs affectés à des achats en libre-service. Une fois que vous avez attribué ces licences achetées de manière centralisée, vous pouvez demander à ce que les acheteurs annulent leurs abonnements existants.

1. Connectez-vous au <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration</a> à l’aide de votre administrateur général ou de votre compte d’administrateur de facturation.

2. Accédez à la page<a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">services d’achat</a> de **facturation** > .

3. Recherchez et sélectionnez le produit que vous souhaitez acheter, puis choisissez **acheter**.

4. Suivez les étapes restantes pour terminer votre achat.

5. Suivez les étapes de la procédure [affichage des licences pour un abonnement acheté en libre-service](#view-who-has-licenses-for-a-self-service-purchase-subscription) pour exporter une liste d’utilisateurs à référencer à l’étape 6.

6. Attribuez des licences à toutes les personnes disposant d’une licence dans l’autre abonnement. Pour connaître les étapes complètes, consultez la rubrique [attribuer des licences aux utilisateurs](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users).

7. Contactez la personne qui a acheté l’abonnement d’achat en libre-service et demandez-lui de l’annuler.

## <a name="need-help-contact-us"></a>Besoin d’aide ? Contactez-nous.

Pour les questions courantes sur les achats en libre-service, voir [FAQ sur les achats en libre-service](self-service-purchase-faq.md).

Si vous avez des questions ou si vous avez besoin d’aide pour des achats en libre-service, [Contactez le support technique](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).