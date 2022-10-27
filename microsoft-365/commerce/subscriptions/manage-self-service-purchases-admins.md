---
title: Gérer les achats en libre-service (administrateurs)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: prlachhw, pablom
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
description: Les administrateurs peuvent apprendre à gérer les achats en libre-service effectués par les utilisateurs de leur organisation.
ms.date: 05/24/2022
ms.openlocfilehash: 4ca3add92877e9219d88366e8104f5fb038ecccc
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735866"
---
# <a name="manage-self-service-purchases-admin"></a>Gérer les achats libre-service (administrateur)

En tant qu’administrateur, vous pouvez voir les achats en libre-service effectués par des membres de votre organisation. Vous voyez le nom du produit, le nom de l’acheteur, les abonnements achetés, la date d’expiration, le prix d’achat et les utilisateurs affectés pour chaque achat en libre-service. Si votre organisation l’exige, vous pouvez désactiver l’achat en libre-service par produit via PowerShell. Vous disposez des mêmes stratégies de gestion des données et d’accès sur les produits achetés via l’achat en libre-service ou de manière centralisée.

Vous pouvez également contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service. Pour plus d’informations, consultez [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Afficher les abonnements en libre-service

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Produits</a>.
::: moniker-end

2. Sous l’onglet **Produits** , sélectionnez l’icône de filtre, puis **libre-service**.
3. Pour afficher plus de détails sur un abonnement, choisissez-en un dans la liste.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Afficher les utilisateurs disposant de licences pour un abonnement d’achat en libre-service

> [!NOTE]
> En tant qu’administrateur, vous ne pouvez pas attribuer ou annuler des attributions de licences pour un abonnement d’achat en libre-service acheté par un utilisateur de votre organisation. Vous pouvez [prendre le contrôle d’un abonnement d’achat en libre-service](#take-over-a-self-service-purchase-subscription), puis attribuer ou annuler des attributions de licences.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, choisissez la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Licences</a>.

::: moniker-end

2. Sélectionnez l’icône de filtre, puis choisissez **Libre-service**.
3. Sélectionnez un produit pour afficher les licences attribuées aux personnes.
    > [!NOTE]
    > S’il existe plusieurs achats pour un produit, ce produit n’est répertorié qu’une seule fois, et la colonne **Quantité disponible** affiche le total de tous les abonnements achetés pour ce produit.
4. La liste **Utilisateurs** est regroupée par nom des personnes qui ont effectué des achats en libre-service.
5. Pour exporter une liste d’utilisateurs disposant de licences pour ces abonnements, choisissez les abonnements que vous souhaitez exporter, puis choisissez **Exporter les utilisateurs**.

## <a name="disable-or-enable-self-service-purchases"></a>Désactiver ou activer les achats en libre-service

Vous pouvez désactiver ou activer les achats en libre-service pour les utilisateurs de votre organisation. Le module **MsCommerce** PowerShell inclut une valeur de paramètre **PolicyID** pour **AllowSelfServicePurchase** qui vous permet de contrôler si les utilisateurs de votre organisation peuvent effectuer des achats en libre-service et pour quels produits.

Vous pouvez utiliser le module **PowerShell MSCommerce** pour :

- Afficher l’état par défaut de la valeur du paramètre **AllowSelfServicePurchase** , qu’il soit activé ou désactivé par produit
- Afficher la liste des produits applicables et indiquer si l’achat en libre-service est activé ou désactivé
- Afficher ou modifier le paramètre actuel d’un produit spécifique pour l’activer ou le désactiver

> [!IMPORTANT]
> Lorsque vous utilisez la stratégie **AllowSelfServicePurchase** , elle active ou désactive les achats en libre-service et les essais en libre-service. Pour obtenir la liste des produits disponibles pour l’achat en libre-service, consultez [Afficher la liste des produits achetés en libre-service et leur état](allowselfservicepurchase-powershell.md#view-a-list-of-self-service-purchase-products-and-their-status). Seuls Project et Visio sont disponibles pour les abonnements d’évaluation.

Pour plus d’informations, consultez [Utiliser AllowSelfServicePurchase pour le module PowerShell MSCommerce](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Centraliser les licences sous un seul abonnement

Vous pouvez attribuer des licences existantes ou acheter des abonnements supplémentaires via des contrats existants pour les utilisateurs affectés à des achats en libre-service. Après avoir attribué ces licences achetées de manière centralisée, vous pouvez demander aux acheteurs d’annuler leurs abonnements existants.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Services d’achat</a> **de facturation**>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Services d’achat** **de facturation**>.

::: moniker-end

2. Recherchez et choisissez le produit que vous souhaitez acheter, puis choisissez **Acheter**.
3. Effectuez les étapes restantes pour terminer votre achat.
4. Suivez les étapes [décrites dans Afficher qui a des licences pour un abonnement acheté en libre-service](#view-who-has-licenses-for-a-self-service-purchase-subscription) pour exporter une liste d’utilisateurs à référencer à l’étape suivante.
5. Attribuez des licences à toutes les personnes disposant d’une licence dans l’autre abonnement. Pour connaître les étapes [complètes, consultez Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md).
6. Contactez la personne qui a acheté l’abonnement en libre-service et demandez-lui de [l’annuler](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Prendre en charge un abonnement d’achat en libre-service

Vous pouvez reprendre un abonnement d’achat en libre-service effectué par un utilisateur de votre organisation. Lorsque vous prenez en charge un abonnement d’achat en libre-service, vous avez deux options :

1. Déplacez les utilisateurs vers un autre abonnement et annulez l’abonnement d’origine.
2. Annulez l’abonnement d’achat en libre-service et supprimez les licences des utilisateurs affectés.

### <a name="move-users-to-a-different-subscription"></a>Transférer des utilisateurs vers un autre abonnement

Lorsque vous déplacez des utilisateurs vers un autre abonnement, l’ancien abonnement est automatiquement annulé. L’utilisateur qui a initialement acheté l’abonnement d’achat en libre-service reçoit un e-mail indiquant que l’abonnement a été annulé.

> [!NOTE]
> Vous devez disposer d’une licence disponible pour chaque utilisateur que vous déplacez dans l’abonnement vers lequel vous déplacez des utilisateurs.

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **de vos produits** .

::: moniker-end

2. Sous l’onglet **Produits** , sélectionnez l’icône de filtre, puis **libre-service**.
3. Sélectionnez l’abonnement que vous souhaitez prendre en charge.
4. Dans la page détails de l’abonnement, dans la section **Abonnements et paramètres** , sélectionnez **Prendre le contrôle de cet abonnement**.
5. Dans le volet droit, sélectionnez **Déplacer les utilisateurs**.
6. Sélectionnez le produit vers lequel vous souhaitez déplacer les utilisateurs, puis sélectionnez **Déplacer les utilisateurs**.
7. Dans la zone **Déplacer des utilisateurs vers** , sélectionnez **Déplacer des utilisateurs**. Le processus de déplacement peut prendre plusieurs minutes. Ne fermez pas votre navigateur pendant l’exécution du processus.
8. Une fois le processus de déplacement terminé, fermez le **volet Déplacer terminé**.
9. Dans la page des détails de l’abonnement, **l’état de l’abonnement** acheté en libre-service s’affiche comme **Supprimé**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Annuler un abonnement d’achat en libre-service

Lorsque vous choisissez d’annuler un abonnement d’achat en libre-service, les utilisateurs disposant de licences perdent l’accès au produit. L’utilisateur qui a initialement acheté l’abonnement d’achat en libre-service reçoit un e-mail indiquant que l’abonnement a été annulé.

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Centre d’administration</a>, accédez à la page **Facturation** > **de vos produits** .

::: moniker-end

2. Sous l’onglet **Produits** , sélectionnez l’icône de filtre, puis **libre-service**.
3. Sélectionnez l'abonnement que vous voulez annuler.
4. Dans la page détails de l’abonnement, dans la section **Abonnements et paramètres** , sélectionnez **Prendre le contrôle de cet abonnement**.
5. Dans le volet droit, sélectionnez **Annuler l’abonnement**.
6. Sélectionnez la raison de votre annulation dans la liste déroulante, puis sélectionnez **Annuler l’abonnement**.
7. Dans la zone **Voulez-vous vraiment annuler ?** , sélectionnez **Annuler l’abonnement**.
8. Fermez le volet droit.
9. Dans la page des détails de l’abonnement, **l’état de l’abonnement** s’affiche comme **Supprimé**.

## <a name="need-help-contact-us"></a>Besoin d’aide ? Contactez-nous.

Pour les questions courantes sur les achats en libre-service, consultez [FAQ sur les achats en libre-service](self-service-purchase-faq.yml).

Si vous avez des questions ou si vous avez besoin d’aide pour les achats en libre-service, [contactez le support](../../admin/get-help-support.md) technique.
