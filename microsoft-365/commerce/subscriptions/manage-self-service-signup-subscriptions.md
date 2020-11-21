---
title: Gérer les abonnements d’abonnement en libre-service
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
- M365-subscription-management
- Adm_O365
- commerce
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez comment gérer des abonnements gratuits en libre-service pour votre organisation.
ms.openlocfilehash: 589466908dcda1461011f046b99be21788c1a018
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376304"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Gérer les abonnements d’abonnement en libre-service

## <a name="what-are-self-service-sign-up-subscriptions"></a>Qu’est-ce que les abonnements d’abonnement en libre-service ?

Il existe un nombre limité d’abonnements gratuits d’abonnement libre-service disponibles pour les utilisateurs de votre organisation qui s’inscrivent à. Un utilisateur peut uniquement s’inscrire et utiliser un abonnement d’abonnement libre-service pour lui-même. Vous pouvez gérer les abonnements d’abonnement en libre-service en bloquant les utilisateurs de s’inscrire et en supprimant les abonnements gratuits pour lesquels les utilisateurs se sont inscrits. Pour plus d’informations sur l’inscription en libre-service et les abonnements disponibles, consultez la rubrique [utilisation de l’authentification en libre-service dans votre organisation](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Afficher la liste des abonnements d’abonnement en libre-service

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sur l’onglet **produits** , sélectionnez l’icône de filtre, puis sélectionnez **libre**. La liste de tous les abonnements d’abonnement libre-service s’affiche.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>En quoi ces abonnements sont-ils différents des abonnements aux achats en libre-service ?

Les abonnements d’inscription en libre-service sont gratuits et sont disponibles pour une liste plus importante de produits que les abonnements aux achats en libre-service. Lorsqu’un utilisateur s’inscrit à un abonnement d’achat en libre-service, il est responsable du paiement. Les abonnements aux achats en libre-service sont disponibles uniquement pour les produits Power Platform (Power BI, Power Apps et Power automate), Project et Visio. Pour plus d’informations, consultez la rubrique [Forum aux questions sur les achats en libre-service](self-service-purchase-faq.md).

## <a name="block-users-from-signing-up"></a>Empêcher les utilisateurs de s’inscrire

Vous utilisez la cmdlet [**Set-MsolCompanySettings**](https://docs.microsoft.com/powershell/module/msonline/set-msolcompanysettings?view=azureadps-1.0&preserve-view=true) avec le paramètre **AllowAdHocSubscriptions** pour contrôler si les utilisateurs peuvent s’inscrire pour des abonnements d’abonnement en libre-service. Pour plus d’informations, voir [Comment puis-je contrôler les paramètres en libre-service ?](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Supprimer un abonnement d’abonnement libre-service

> [!IMPORTANT]
> Lorsque vous supprimez un abonnement d’abonnement libre-service, vous empêchez tous les utilisateurs d’accéder à leurs données et à leurs messages électroniques et de supprimer toutes les données et tous les messages électroniques.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sur l’onglet **produits** , sélectionnez l’icône de filtre, puis sélectionnez **libre**.
3. Sélectionnez l’abonnement d’inscription libre-service que vous souhaitez supprimer. 
4. Sur la page Détails de l’abonnement, dans la section **paramètres d’abonnements et de paiement** , sélectionnez **Supprimer l’abonnement**.
5. Dans le volet **supprimer un abonnement** , activez la case à cocher, puis sélectionnez Supprimer l' **abonnement**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>J’ai un abonnement d’inscription libre-service qui bloque la suppression d’annuaire

Les produits d’abonnement en libre-service que des utilisateurs individuels peuvent également créer un utilisateur invité pour l’authentification dans votre répertoire Azure AD. Pour éviter toute perte de données, ces produits en libre-service bloquent les suppressions d’annuaires jusqu’à ce qu’ils soient entièrement supprimés de l’annuaire. Ils ne peuvent être supprimés que par l’administrateur Azure AD. Pour plus d’informations, consultez [la rubrique supprimer un répertoire dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-delete-howto).