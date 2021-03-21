---
title: Gérer les achats en libre-service (administrateurs)
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
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
description: Les administrateurs peuvent apprendre à gérer les achats en libre-service effectués par les utilisateurs de leur organisation.
ms.openlocfilehash: 2ce12b7dba4e765745a94fa10f4ba15e7013e3c8
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50920179"
---
# <a name="manage-self-service-purchases-admin"></a>Gérer les achats libre-service (administrateur)

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](../../admin/microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).

::: moniker-end

En tant qu’administrateur, vous pouvez voir les achats en libre-service effectués par des personnes de votre organisation. Vous pouvez voir le nom du produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Si votre organisation l’exige, vous pouvez désactiver l’achat en libre-service par produit via PowerShell. Vous avez les mêmes stratégies de gestion des données et d’accès que les produits achetés via un achat en libre-service ou de manière centralisée.

Vous pouvez également contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service. Pour plus d’informations, voir [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce.](allowselfservicepurchase-powershell.md)

## <a name="view-self-service-subscriptions"></a>Afficher les abonnements en libre-service

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, sélectionnez l’icône de filtre, puis sélectionnez **Libre-service.**
3. Pour afficher plus de détails sur un abonnement, choisissez-en un dans la liste.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Afficher qui dispose de licences pour un abonnement d’achat en libre-service

1. Dans le Centre d’administration, allez sur la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation.</a>
2. Sélectionnez l’icône de filtre, puis choisissez **Libre-service.**
3. Sélectionnez un produit pour voir les licences attribuées aux personnes.
    > [!NOTE]
    > S’il existe plusieurs achats pour un produit, ce  produit n’est répertorié qu’une seule fois et la colonne Quantité disponible indique le total de tous les abonnements achetés pour ce produit.
4. La **liste Utilisateurs** est regroupée par les noms des personnes qui ont effectué des achats en libre-service.
5. Pour exporter une liste d’utilisateurs avec des licences pour ces abonnements, choisissez les abonnements que vous souhaitez exporter, puis **sélectionnez Exporter les utilisateurs.**

## <a name="disable-or-enable-self-service-purchases"></a>Désactiver ou activer les achats en libre-service

Vous pouvez désactiver ou activer les achats en libre-service pour les utilisateurs de votre organisation. Le module **PowerShell MSCommerce** inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service et pour quels produits.

Vous pouvez utiliser le module **PowerShell MSCommerce** pour :

- Afficher l’état par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’elle soit activée ou désactivée par le produit
- Afficher la liste des produits applicables et si l’achat en libre-service est activé ou désactivé
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

Pour plus d’informations, voir [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce.](allowselfservicepurchase-powershell.md)

## <a name="centralize-licenses-under-a-single-subscription"></a>Centraliser les licences sous un abonnement unique

Vous pouvez attribuer des licences existantes ou acheter des abonnements supplémentaires via des contrats existants pour les utilisateurs affectés à des achats en libre-service. Après avoir attribué ces licences achetées de manière centralisée, vous pouvez demander aux acheteur d’annuler leurs abonnements existants.

1. Dans le centre d’administration, allez à la page **Services** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">d’achat de facturation.</a>
2. Recherchez et choisissez le produit que vous souhaitez acheter, puis choisissez **Acheter.**
3. Effectuer les étapes restantes pour effectuer votre achat.
4. Suivez les étapes de l’affichage qui dispose de licences pour un abonnement acheté en [libre-service](#view-who-has-licenses-for-a-self-service-purchase-subscription) pour exporter une liste d’utilisateurs à référencer à l’étape suivante.
5. Attribuez des licences à toutes les personnes qui disposent d’une licence dans l’autre abonnement. Pour obtenir la procédure complète, voir [Attribuer des licences aux utilisateurs.](../../admin/manage/assign-licenses-to-users.md)
6. Contactez la personne qui a acheté l’abonnement à l’achat en libre-service et demandez-lui de [l’annuler.](manage-self-service-purchases-users.md#cancel-a-subscription)

## <a name="take-over-a-self-service-purchase-subscription"></a>Prendre en compte un abonnement d’achat en libre-service

Vous pouvez prendre le relais d’un abonnement d’achat en libre-service effectué par un utilisateur de votre organisation. Lorsque vous prenez le relais d’un abonnement d’achat en libre-service, deux options s’offrent à vous :

1. Déplacez les utilisateurs vers un autre abonnement et annulez l’abonnement d’origine.
2. Annulez l’abonnement d’achat en libre-service et supprimez les licences des utilisateurs affectés.

### <a name="move-users-to-a-different-subscription"></a>Transférer des utilisateurs vers un autre abonnement

Lorsque vous déplacez des utilisateurs vers un autre abonnement, l’ancien abonnement est automatiquement annulé. L’utilisateur qui a acheté à l’origine l’abonnement à l’achat en libre-service reçoit un courrier électronique qui indique que l’abonnement a été annulé.

> [!NOTE]
> Vous devez avoir une licence disponible pour chaque utilisateur de l’abonnement vers qui vous souhaitez déplacer des utilisateurs.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, sélectionnez l’icône de filtre, puis sélectionnez **Libre-service.**
3. Sélectionnez l’abonnement à prendre en compte.
4. Dans la page détails de l’abonnement, dans la section Abonnements et **paramètres,** sélectionnez **Prendre le contrôle de cet abonnement.**
5. Dans le volet droit, sélectionnez **Déplacer les utilisateurs.**
6. Sélectionnez le produit vers qui vous souhaitez déplacer les utilisateurs, puis **sélectionnez Déplacer les utilisateurs.**
7. Dans la **zone Déplacer les utilisateurs vers,** **sélectionnez Déplacer les utilisateurs.** Le processus de déplacement peut prendre plusieurs minutes. Ne fermez pas votre navigateur pendant l’opération.
8. Lorsque le processus de déplacement est terminé, fermez le **volet Déplacer terminé.**
9. Dans la page des  détails de l’abonnement, l’état de l’abonnement acheté en libre-service s’affiche **comme supprimé.**

### <a name="cancel-a-self-service-purchase-subscription"></a>Annuler un abonnement d’achat en libre-service

Lorsque vous choisissez d’annuler un abonnement d’achat en libre-service, les utilisateurs avec licences perdent l’accès au produit. L’utilisateur qui a acheté à l’origine l’abonnement à l’achat en libre-service reçoit un courrier électronique qui indique que l’abonnement a été annulé.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet** Produits, sélectionnez l’icône de filtre, puis sélectionnez **Libre-service.**
3. Sélectionnez l’abonnement à annuler.
4. Dans la page détails de l’abonnement, dans la section Abonnements et **paramètres,** sélectionnez **Prendre le contrôle de cet abonnement.**
5. Dans le volet droit, sélectionnez **Annuler l’abonnement.**
6. Sélectionnez une raison pour votre annulation dans la liste de listes listes, puis **sélectionnez Annuler l’abonnement.**
7. Dans la **zone Voulez-vous vraiment** annuler ? sélectionnez **Annuler l’abonnement.**
8. Fermez le volet droit.
9. Sur la page des détails de l’abonnement, **l’état de l’abonnement** s’affiche **comme supprimé.**

## <a name="need-help-contact-us"></a>Vous avez besoin d’aide ? Contactez-nous.

Pour les questions courantes sur les achats en libre-service, consultez la FAQ sur les [achats en libre-service.](self-service-purchase-faq.md)

Si vous avez des questions ou si vous avez besoin d’aide sur les achats en libre-service, [contactez le support technique.](../../admin/contact-support-for-business-products.md)