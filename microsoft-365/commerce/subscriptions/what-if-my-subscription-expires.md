---
title: Qu’arrive-t-il à mes données et à mon accès à la fin de mon abonnement ?
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sgautam, jmueller
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: high
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Découvrez ce qu’il advient de vos données lorsque votre abonnement Microsoft 365 Business atteint sa date d’expiration, est désactivé, ou que vous procédez à sa résiliation.
ms.date: 09/16/2021
ms.openlocfilehash: 4410d9e7a6df3e6db7b7851c7df9582a2b9cc4f0
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68726131"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement Microsoft 365 Business ?

If your subscription ends—either because it expires, or because you decide to cancel—your access to Microsoft 365 services, applications, and customer data go through multiple states before the subscription is fully turned off, or *deleted*. If you are aware of this progression, you'll be better equipped to return your subscription to an active state before it's too late, or—if you're leaving Microsoft 365—back up your data before it is ultimately deleted.

Veuillez consulter ces informations essentielles avant de contacter le [service clientèle de Microsoft 365](../../admin/get-help-support.md).

> [!NOTE]
> Certains abonnements ne peuvent être annulés que pendant une période limitée après les avoir achetés ou renouvelés. Si la fenêtre d’annulation est écoulée, désactiver la facturation périodique pour annuler l’abonnement à la fin de sa période.
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Qu’arrive-t-il à mes données à l’expiration de mon abonnement ?

- À son expiration, votre abonnement passe par les trois états suivants : expiré, désactivé, supprimé. L’état « Expiré » commence immédiatement lorsque la date de fin de validité de l’abonnement est atteinte.
- Si la facturation périodique est désactivée pour votre abonnement à l’année, les mêmes états s’appliquent. La première phase commence un an après le début de l’abonnement à l’année, et non à la date de désactivation du paramètre de sa facturation périodique.
- Si vous annulez votre abonnement au mois, sa désactivation est effective le jour de l’annulation. Cela signifie que les utilisateurs n’ont immédiatement plus accès aux composants de Microsoft 365, seuls les administrateurs conservent l’accès aux données pour les 90 prochains jours.

Le tableau suivant explique ce à quoi vous pouvez vous attendre à l'expiration d'un abonnement payant à Microsoft 365 Business.

| Actif | Expiré <br/>(30 jours\*) | Désactivé <br/>(90 jours\*) | Supprimé |
|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| *Les données sont accessibles à tous*                                               | *Les données sont accessibles à tous*                                                     | *Les données sont accessibles aux administrateurs uniquement*                                             | **Les données sont supprimées<br/>Azure Active Directory est supprimé s’il n’est pas utilisé par d’autres services** |
| Les utilisateurs disposent d’un accès normal à Microsoft 365, aux fichiers et applications   | Les utilisateurs disposent d’un accès normal à Microsoft 365, aux fichiers et applications              | Les utilisateurs n’ont pas accès à Microsoft 365, aux fichiers ou aux applications                        | Les utilisateurs n’ont pas accès à Microsoft 365, aux fichiers ou aux applications                                     |
| Les utilisateurs disposent d’un accès normal à Microsoft 365, aux données et aux applications Office | Les administrateurs ont accès au centre d'administration                                           | Les administrateurs ont accès au centre d'administration mais ne peuvent pas attribuer de licences aux utilisateurs       | Les administrateurs ont accès au centre d'administration pour l’achat et la gestion d’autres abonnements             |
|                                                                        | Les administrateurs généraux et de facturation peuvent réactiver l’abonnement dans le centre d'administration | Les administrateurs généraux et de facturation peuvent réactiver l’abonnement dans le centre d'administration |                                                                                           |

* Valable sur la plupart des offres, des pays et régions.
  
> [!NOTE]
>
> **What is "customer data"?** Customer data, as defined in the [Microsoft Online Service Terms](https://www.microsoft.com/en-us/licensing/product-licensing/products), refers to all data, including all text, sound, or image files that are provided to Microsoft by, or on behalf of, the customer through the customer's use of Microsoft 365 services. To learn more about the protection of customer data, see the [Get started with the Microsoft Service Trust Portal](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Que se passe-t-il si j’annule un abonnement ?

If you cancel your subscription before its term end date, the subscription skips the Expired stage and moves directly into the Disabled stage, which is 90 days for most subscriptions, in most countries and regions. We recommend that you [back up your data](move-users-different-subscription.md) before canceling, but as an admin, you can still access and back up data for your organization while it is in the Disabled stage. Any customer data that you leave behind may be deleted after 90 days, and will be deleted no later than 180 days after cancellation.
  
Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Admin access** Admins can still sign in and access the admin center, and buy other subscriptions as needed. As a global or billing admin, you have 90 days to [reactivate the subscription](reactivate-your-subscription.md) with all data intact.

- **User access** Your users won't be able to use services like OneDrive for Business, or access customer data—for example, email or documents on team sites. Office applications, like Word and Excel, will eventually move into a read-only, reduced functionality mode and display [Unlicensed Product notifications](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

Pour plus d'informations sur l'annulation de votre abonnement, consultez la rubrique [Annuler un abonnement](cancel-your-subscription.md).
  
> [!IMPORTANT]
> Si vous voulez que les données de votre abonnement soient supprimées avant la fin établie de l’étape de désactivation, vous pouvez [clôturer votre compte](../close-your-account.md).
  
> [!NOTE]
>
> Si vous supprimez explicitement un abonnement, cela ignore les étapes Expiré et Désactivé, et les données et le contenu SharePoint Online, dont OneDrive, sont supprimés immédiatement.

## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Quelles options s’offrent à moi si mon abonnement expire bientôt ?

While a subscription is active, you and your end users have normal access to your data, services like email and OneDrive for Business, and Office applications. As the admin, you'll receive a series of notifications via email and in the admin center as your subscription nears its expiration date.
  
Avant que l’abonnement n’atteigne sa date d’expiration, plusieurs options s’offrent à vous :
  
- **Activer la facturation périodique pour cet abonnement.**
  - If **Recurring billing** is already turned on, you don't have to take any action. Your subscription is automatically billed, and you are charged for an additional year or month, depending on your current payment frequency. If for any reason you've turned **Recurring billing** off, you can always [turn Recurring billing back on](renew-your-subscription.md).
  - Si vous avez acheté Microsoft 365 Apps for business à l’aide d’une carte prépayée, vous pouvez activer la [facturation périodique](renew-your-subscription.md) pour votre abonnement.
  - If you're an Open Volume Licensing customer with a prepaid, one-year subscription, contact your partner to purchase a new product key. You'll receive instructions via email to activate your key in the [Volume Licensing Service Center](https://go.microsoft.com/fwlink/p/?LinkID=282016). To learn how to find a new partner, or the partner you've worked with in the past, see [Find your partner or reseller](../../admin/manage/find-your-partner-or-reseller.md).
  - Si vous avez Microsoft 365 Apps for business, consultez la rubrique [Gérer la facturation périodique pour votre abonnement](renew-your-subscription.md).
- **Laisser l’abonnement expirer.**
  - If you're paying by credit card or invoice and you don't want to continue your subscription, [turn Recurring billing off](renew-your-subscription.md). Your subscription ends on its expiration date, and you can ignore all related email notifications.
  - Si vous êtes un client du programme de licences en volume Open et que vous faites appel à un partenaire, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
  - Si vous êtes un client Office 365 Business Premium, et que vous avez une offre prépayée pour votre abonnement activée à l'aide d'une clé de produit, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
- **Cancel before the subscription expires.** For details, see [Cancel your subscription](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Que se passe-t-il une fois mon abonnement expiré ?

If you let your subscription expire, it goes through multiple states before it is ultimately deleted. This gives you, as the admin, time to reactivate if you want to continue the service, or to back up your data if you decide you no longer want the subscription.
  
Voici ce à quoi vous pouvez vous attendre lorsque votre abonnement atteint ces différents états.
  
### <a name="state-expired"></a>État : Expiré

**What to expect:** The Expired stage lasts for 30 days for most subscriptions, including subscriptions purchased through [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), in most countries and regions. For Volume Licensing products, except for Microsoft Open, the Expired stage lasts 90 days.

Dans cet état, les utilisateurs disposent d’un accès normal au portail Microsoft 365, aux applications d’Office et aux services tels que le courrier et SharePoint Online.
  
As an admin, you still have access to the admin center. Don't worry—global or billing admins can [reactivate the subscription](reactivate-your-subscription.md) and continue using Microsoft 365. If you don't reactivate, [back up your data](move-users-different-subscription.md).
  
### <a name="state-disabled"></a>État : Désactivé

**What to expect:** If you don't reactivate your subscription while it is in the Expired stage, it moves into a Disabled stage, which lasts for 90 days for most subscriptions, in most countries and regions. For Volume Licensing products, the Disabled stage lasts 30 days.

In this state, your access decreases significantly. Your users can't sign in, or access services like email or SharePoint Online. Office applications eventually move into a read-only, reduced functionality mode and display [Unlicensed Product notifications](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). You can still sign in and get to the admin center, but can't assign licenses to users. Your customer data, including all user data, email, and files on team sites, is available only to you and other admins.

As a global or billing admin, you can [reactivate the subscription](reactivate-your-subscription.md) and continue using Microsoft 365 with all of your customer data intact. If you choose not to reactivate, [back up your data](move-users-different-subscription.md).

### <a name="state-deleted"></a>État : Supprimé
  
**Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant qu’il est expiré ou désactivé, il est supprimé.
  
Admins and users no longer have access to the services or Office applications that came with the subscription. All customer data—from user data to documents and email—is permanently deleted and is unrecoverable.
  
At this point, you can't reactivate the subscription. However, as a global or billing admin, you can still access the admin center to manage other subscriptions, or to buy new subscriptions to meet your business needs.
  
> [!NOTE]
>
> - L'ajout d'un nouvel abonnement du même type que celui précédemment supprimé ne restaure pas les données associées à l'abonnement supprimé.
> - Dans le cas d’une suspension de licence provenant d’un fournisseur de solutions Microsoft Cloud, il n’y a pas d’étape expirée de 30 jours et les services sont désactivés immédiatement. Les données sont supprimées après 90 jours si le client n’est pas réactivé par l’ajout d’une nouvelle licence.

### <a name="what-happens-when-my-trial-ends"></a>Que se passe-t-il à l’expiration de ma version d’évaluation ?

À l’expiration de votre version d’évaluation, les services de Microsoft 365 ne peuvent plus être utilisés gratuitement. Plusieurs options s’offrent à vous :

- **Acheter Microsoft 365.** Quand votre version d'évaluation arrive à expiration, elle passe au stade Expiré. Celle-ci vous offre un délai supplémentaire de 30 jours (pour la plupart des versions d'évaluation et dans la plupart des pays et régions) pour acheter Microsoft 365. Pour plus d’informations sur la conversion de votre version d’évaluation en abonnement payant, consultez [Acheter un abonnement à partir de votre version d’évaluation gratuite](../try-or-buy-microsoft-365.md#buy-a-subscription-from-your-free-trial).
- **Prolonger votre version d'évaluation.** Vous avez besoin de davantage de temps pour évaluer Microsoft 365 ? Dans certains cas, vous pouvez [prolonger votre version d’évaluation](../extend-your-trial.md).
- **Annuler la version d’évaluation ou la laisser expirer.** Si vous décidez de ne pas acheter Microsoft 365, vous pouvez laisser expirer ou [annuler](cancel-your-subscription.md) votre version d'évaluation. Veillez à sauvegarder les données que vous souhaitez conserver. Peu de temps après la phase expirée de 30 jours, les informations et les données de votre compte d'évaluation sont définitivement supprimées.

> [!NOTE]
>
> The information on this page is subject to the [Microsoft Policy Disclaimer and Change Notice](https://go.microsoft.com/fwlink/p/?LinkId=613651). Return to this site periodically to review any changes.

## <a name="related-content"></a>Contenu connexe

[Annuler un abonnement](./cancel-your-subscription.md)
[Renouveler Microsoft 365 for business](./renew-your-subscription.md) (article)\
[Réactiver un abonnement](./reactivate-your-subscription.md) (article)
