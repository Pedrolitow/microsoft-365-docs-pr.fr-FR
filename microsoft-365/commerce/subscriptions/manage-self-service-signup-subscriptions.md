---
title: Gérer les abonnements d’inscription en libre-service
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
search.appverid: MET150
description: Découvrez comment gérer les abonnements gratuits à l’inscription en libre-service pour votre organisation.
ms.date: 03/17/2021
ms.openlocfilehash: b942d21fb3c4a6d6b8ab27fafb2af00a095c2a608909142788e46dbe60cdfa9d
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53852150"
---
# <a name="manage-self-service-sign-up-subscriptions"></a>Gérer les abonnements d’inscription en libre-service

## <a name="what-are-self-service-sign-up-subscriptions"></a>Qu’est-ce que les abonnements en libre-service ?

Un nombre limité d’abonnements d’inscription libre-service est disponible pour les utilisateurs de votre organisation. Un utilisateur peut uniquement s’inscrire et utiliser un abonnement d’inscription en libre-service pour lui-même. Vous gérez les abonnements d’inscription en libre-service en bloquant l’inscription des utilisateurs et en supprimant les abonnements gratuits pour les utilisateurs inscrits. Pour plus d’informations sur l’inscription en libre-service et les abonnements disponibles, voir l’utilisation de l’inscription en [libre-service dans votre organisation.](../../admin/misc/self-service-sign-up.md)

## <a name="view-a-list-of-self-service-sign-up-subscriptions"></a>Afficher la liste des abonnements d’inscription en libre-service

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet Produits,** sélectionnez l’icône de filtre, puis sélectionnez **Gratuit**. Une liste de tous les abonnements d’inscription en libre-service s’affiche.

## <a name="how-are-these-subscriptions-different-from-self-service-purchase-subscriptions"></a>En quoi ces abonnements sont-ils différents des abonnements d’achat en libre-service ?

Les abonnements d’inscription en libre-service sont gratuits et sont disponibles pour une plus grande liste de produits que les abonnements d’achat en libre-service. Lorsqu’un utilisateur s’est abonné à un abonnement d’achat en libre-service, il est responsable de son paiement. Les abonnements à des achats en libre-service sont disponibles uniquement pour les produits Power Platform (Power BI, Power Apps et Power Automate), Project et Visio. Pour plus d’informations, [voir le FAQ sur les achats en libre-service.](self-service-purchase-faq.yml)

## <a name="block-users-from-signing-up"></a>Empêcher les utilisateurs de s’inscrire

Vous utilisez la cmdlet [**Set-MsolCompanySettings**](/powershell/module/msonline/set-msolcompanysettings?preserve-view=true&view=azureadps-1.0) avec le paramètre **AllowAdHocSubscriptions** pour contrôler si les utilisateurs peuvent s’inscrire à des abonnements d’inscription en libre-service. Pour plus d’informations, [voir Comment contrôler les paramètres libre-service ?](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="delete-a-self-service-sign-up-subscription"></a>Supprimer un abonnement d’inscription en libre-service

> [!IMPORTANT]
> Lorsque vous supprimez un abonnement d’inscription en libre-service, vous bloquez l’accès de tous les utilisateurs à leurs données et messages électroniques et supprimez toutes les données et tous les messages électroniques.

1. Dans le centre d’administration, accédez à la page **Facturation** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
2. Sous **l’onglet Produits,** sélectionnez l’icône de filtre, puis sélectionnez **Gratuit**.
3. Sélectionnez l’abonnement d’inscription en libre-service à supprimer. 
4. Dans la page détails de l’abonnement, dans la section Abonnements et **paramètres de** paiement, sélectionnez **Supprimer l’abonnement.**
5. Dans le **volet Supprimer l’abonnement,** cochez la case, puis **supprimez l’abonnement.**

## <a name="i-have-a-self-service-sign-up-subscription-that-blocks-directory-deletion"></a>J’ai un abonnement en libre-service qui bloque la suppression d’annuaires

Les produits d’inscription en libre-service que les utilisateurs individuels peuvent inscrire créent également un utilisateur invité pour l’authentification dans votre annuaire Azure AD. Pour éviter la perte de données, ces produits en libre-service bloquent les suppressions d’annuaires jusqu’à ce qu’elles soient entièrement supprimées de l’annuaire. Ils peuvent uniquement être supprimés par l’administrateur Azure AD. Pour plus d’informations, [voir Supprimer un répertoire dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-delete-howto).
