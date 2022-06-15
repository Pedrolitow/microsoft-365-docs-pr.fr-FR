---
title: Gérer les abonnements d’inscription en libre-service
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment gérer les abonnements d’inscription libre-service gratuits pour votre organisation.
ms.date: 03/17/2021
ms.openlocfilehash: 58c58c849b72c170e0ccf10de54389bd1245bced
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102347"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Gérer les abonnements d’inscription en libre-service

## <a name="what-are-self-service-sign-up-subscriptions"></a>Qu’est-ce que les abonnements en libre-service ?

Un nombre limité d’abonnements en libre-service gratuits sont disponibles pour que les utilisateurs de votre organisation s’inscrivent. Un utilisateur peut uniquement s’inscrire et utiliser un abonnement d’inscription en libre-service pour lui-même. Vous gérez les abonnements d’inscription en libre-service en empêchant les utilisateurs de s’inscrire et en supprimant les abonnements gratuits auxquels les utilisateurs se sont inscrits. Pour plus d’informations sur l’inscription en libre-service et les abonnements disponibles, consultez [Utilisation de l’inscription en libre-service dans votre organisation](../../admin/misc/self-service-sign-up.md).

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Afficher la liste des abonnements d’inscription en libre-service

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **Produits** , sélectionnez l’icône de filtre, puis **sélectionnez Gratuit**. Une liste de tous les abonnements en libre-service s’affiche.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>En quoi ces abonnements diffèrent-ils des abonnements d’achat en libre-service ?

Les abonnements d’inscription en libre-service sont gratuits et sont disponibles pour une liste de produits plus grande que les abonnements d’achat en libre-service. Lorsqu’un utilisateur s’inscrit à un abonnement d’achat en libre-service, il est responsable du paiement. Les abonnements à l’achat en libre-service sont disponibles uniquement pour les produits Power Platform (Power BI, Power Apps et Power Automate), les Project et les Visio. Pour plus d’informations, consultez la [FAQ sur l’achat en libre-service](self-service-purchase-faq.yml).

## <a name="block-users-from-signing-up"></a>Empêcher les utilisateurs de s’inscrire

Vous utilisez l’applet de commande [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) avec le paramètre **AllowAdHocSubscriptions** pour contrôler si les utilisateurs peuvent s’inscrire à des abonnements d’inscription en libre-service. Pour plus d’informations, consultez [如何实现 contrôler les paramètres en libre-service ?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Supprimer un abonnement en libre-service

> [!IMPORTANT]
> Lorsque vous supprimez un abonnement d’inscription en libre-service, vous empêchez tous les utilisateurs d’accéder à leurs données et à leurs e-mails, et supprimez toutes les données et tous les e-mails.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous l’onglet **Produits** , sélectionnez l’icône de filtre, puis **sélectionnez Gratuit**.
3. Sélectionnez l’abonnement d’inscription en libre-service que vous souhaitez supprimer. 
4. Dans la page détails de l’abonnement, dans la section **Abonnements et paramètres de paiement** , sélectionnez **Supprimer l’abonnement**.
5. Dans le volet **Supprimer l’abonnement** , cochez la case, puis **sélectionnez Supprimer l’abonnement**.

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>J’ai un abonnement d’inscription en libre-service qui bloque la suppression d’annuaires

Les produits d’inscription en libre-service auxquels les utilisateurs individuels peuvent s’inscrire créent également un utilisateur invité pour l’authentification dans votre annuaire Azure AD. Pour éviter la perte de données, ces produits en libre-service bloquent les suppressions de répertoires jusqu’à ce qu’elles soient entièrement supprimées du répertoire. Ils ne peuvent être supprimés que par l’administrateur Azure AD. Pour plus d’informations, consultez [Supprimer un répertoire dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
