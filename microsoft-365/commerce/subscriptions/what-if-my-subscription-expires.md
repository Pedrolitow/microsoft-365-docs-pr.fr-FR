---
title: Qu’arrive-t-il à mes données et à mon accès à la fin de mon abonnement ?
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- commerce_subscriptions
- AdminTemplateSet
search.appverid: MET150
description: Découvrez ce qu’il advient de vos données lorsque votre abonnement Microsoft 365 Business atteint sa date d’expiration, est désactivé, ou que vous procédez à sa résiliation.
ms.date: 04/08/2021
ms.openlocfilehash: 55a34352da6deef2fd48542dd06859e0024e6966
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180123"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement Microsoft 365 Business ?

Lorsque votre abonnement se termine (parce qu’il est arrivé à sa date d’expiration ou que vous avez décidé de l’annuler), votre accès aux services, applications et données client Microsoft 365 passent par plusieurs états avant la désactivation complète de l’abonnement ou sa *suppression*. En connaissance de cette progression, vous aurez toutes les cartes en main pour réactiver votre abonnement avant qu’il ne soit trop tard, ou si vous ne souhaitez plus utiliser Microsoft 365, pour sauvegarder vos données avant leur suppression finale.

Veuillez consulter ces informations essentielles avant de contacter le [service clientèle de Microsoft 365](../../business-video/get-help-support.md).
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Qu’arrive-t-il à mes données à l’expiration de mon abonnement ?

- À son expiration, votre abonnement passe par les trois états suivants : expiré, désactivé, supprimé. L’état « Expiré » commence immédiatement lorsque la date de fin de validité de l’abonnement est atteinte.
- Si la facturation périodique est désactivée pour votre abonnement à l’année, les mêmes états s’appliquent. Le premier état commence un an après le début de l’abonnement à l’année, et non à la date de désactivation du paramètre de sa facturation périodique.
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
> **Qu'est-ce que les « données client » ?** Les données client, telles que définies dans les [Conditions d'utilisation du service en ligne Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613649), représentent toutes les données, y compris les fichiers texte, audio et image, qui sont fournis à Microsoft par le client, ou pour le compte du client, au cours de l'utilisation des services Microsoft 365 par le client. Pour en savoir plus sur la protection des données client, consultez la rubrique [Prise en main du portail d’approbation de services de Microsoft](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Que se passe-t-il si j’annule un abonnement ?

Si vous annulez votre abonnement avant sa date d’expiration, l’abonnement passe directement à l’état Désactivé (90 jours pour la plupart des abonnements dans la plupart des pays et régions). Nous vous recommandons de [sauvegarder vos données](back-up-data-before-switching-plans.md) avant d’annuler votre abonnement. En tant qu’administrateur, vous pouvez toujours accéder aux données de votre organisation et sauvegarder celles-ci lorsque votre abonnement est au stade de désactivation. Toutes les données client que vous laissez derrière vous peuvent être supprimées après 90 jours, et le seront assurément au plus tard 180 jours après l'annulation.
  
Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Accès des administrateurs** Les administrateurs peuvent toujours se connecter et accéder au centre d'administration, et acheter d'autres abonnements si nécessaire. En tant qu'administrateur général ou de facturation, vous disposez de 90 jours pour [réactiver l’abonnement](reactivate-your-subscription.md) et retrouver toutes les données intactes.

- **Accès des utilisateurs** Vos utilisateurs ne peuvent plus utiliser les services OneDrive Entreprise ou accéder aux données client (par exemple les courriers électroniques ou les documents sur les sites d'équipe). Les applications Office, telles que Word et Excel, passent en mode d’utilisation en lecture seule et de fonctionnalités réduites, et affichent des [notifications « Produit sans licence »](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx).

Pour plus d'informations sur l'annulation de votre abonnement, consultez la rubrique [Annuler un abonnement](cancel-your-subscription.md).
  
> [!IMPORTANT]
> Si vous voulez que les données de votre abonnement soient supprimées avant la fin établie de l’étape de désactivation, vous pouvez [clôturer votre compte](../close-your-account.md).
  
> [!NOTE]
>
> Si vous supprimez explicitement un abonnement, cela ignore les étapes Expiré et Désactivé, et les données et le contenu SharePoint Online, dont OneDrive, sont supprimés immédiatement.

## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Quelles options s’offrent à moi si mon abonnement expire bientôt ?

Tant que votre abonnement est actif, vous et vos utilisateurs finaux disposez d'un accès normal à vos données, aux services tels que le courrier électronique et OneDrive Entreprise, et aux applications Office. En tant qu'administrateur, vous recevez plusieurs notifications par courrier électronique et dans le Centre d'administration lorsque la date d'expiration de votre abonnement approche.
  
Avant que l’abonnement n’atteigne sa date d’expiration, plusieurs options s’offrent à vous :
  
- **Activer la facturation périodique pour cet abonnement.**
  - Si la **facturation périodique** est déjà activée, aucune action n’est requise. Votre abonnement est facturé automatiquement et vous devrez payer une année ou un mois supplémentaire, selon la fréquence de paiement actuelle. Si pour quelque raison vous avez désactivé la **facturation périodique**, vous pouvez toujours [la réactiver](renew-your-subscription.md).
  - Si vous avez acheté Microsoft 365 Apps for business à l’aide d’une carte prépayée, vous pouvez activer la [facturation périodique](renew-your-subscription.md) pour votre abonnement.
  - Si vous êtes client du programme de licence en volume Open avec un abonnement prépayé d'un an, contactez votre partenaire pour acheter une nouvelle clé de produit dans le cadre du renouvellement. Vous recevrez des instructions par courrier électronique pour activer votre clé dans le [Centre VLSC (Volume Licensing Service Center)](https://go.microsoft.com/fwlink/p/?LinkID=282016). Pour découvrir comment rechercher un nouveau partenaire ou trouver le partenaire avec lequel vous avez traité précédemment, voir [Trouver votre partenaire ou revendeur](../../admin/manage/find-your-partner-or-reseller.md).
  - Si vous avez Microsoft 365 Apps for business, consultez la rubrique [Gérer la facturation périodique pour votre abonnement](renew-your-subscription.md).
- **Laisser l’abonnement expirer.**
  - Si vous payez par carte bancaire ou par facture et ne souhaitez pas renouveler votre abonnement, [désactivez la facturation périodique](renew-your-subscription.md). Votre abonnement prend fin à sa date d’expiration. Vous pouvez ignorer toutes les notifications par courrier électronique qui y sont relatives.
  - Si vous êtes un client du programme de licences en volume Open et que vous faites appel à un partenaire, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
  - Si vous êtes un client Office 365 Business Premium, et que vous avez une offre prépayée pour votre abonnement activée à l'aide d'une clé de produit, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
- **Annulez votre abonnement avant son expiration.** Pour plus de détails, consultez la rubrique [Annuler l’abonnement](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Que se passe-t-il une fois mon abonnement expiré ?

Si vous laissez votre abonnement expirer, il passe par plusieurs états avant sa suppression finale. En tant qu’administrateur, cela vous laisse le temps de le réactiver si vous voulez continuer à utiliser le service, ou de sauvegarder vos données si vous décidez de ne plus utiliser l’abonnement.
  
Voici ce à quoi vous pouvez vous attendre lorsque votre abonnement atteint ces différents états.
  
### <a name="state-expired"></a>État : Expiré

**Ce à quoi vous devez vous attendre :** L'état Expiré dure 30 jours pour la plupart des abonnements, y compris les abonnements achetés via un contrat [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), et dans la plupart des pays et régions. Pour les produits de licence en volume, à l’exception de Microsoft Open, l’étape Expiré dure 90 jours.

Dans cet état, les utilisateurs disposent d’un accès normal au portail Microsoft 365, aux applications d’Office et aux services tels que le courrier et SharePoint Online.
  
En tant qu'administrateur, vous avez toujours accès au centre d'administration. À tout moment, un administrateur général ou de facturation peut [réactiver l’abonnement](reactivate-your-subscription.md) pour prolonger l’utilisation de Microsoft 365. Si vous ne procédez pas à la réactivation, veillez à [sauvegarder vos données](back-up-data-before-switching-plans.md).
  
### <a name="state-disabled"></a>État : Désactivé

**Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant que son état est Expiré, il passe à l'état Désactivé (90 jours pour la plupart des abonnements et dans la plupart des pays et régions). Pour les produits de licence en volume, l’étape Désactivée dure 30 jours.

Dans cet état, votre niveau d'accès est considérablement restreint. Les utilisateurs ne peuvent pas se connecter ou accéder à des services tels que les courriers électroniques ou SharePoint Online. Les applications Office passent en mode d'utilisation en lecture seule et de fonctionnalités réduites et affichent des notifications [Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx). Vous pouvez toujours vous connecter et accéder au centre d'administration, mais vous ne pouvez plus attribuer de licences aux utilisateurs. Vos données client, c’est-à-dire, l’ensemble des données, des courriers électroniques et des fichiers des clients stockés sur les sites d’équipe, sont accessibles uniquement à vous et aux autres administrateurs.

En tant qu'administrateur général ou de facturation, vous pouvez [réactiver l'abonnement](reactivate-your-subscription.md) et prolonger l’utilisation de Microsoft 365 avec toutes vos données client intactes. Si vous choisissez de ne pas procéder à la réactivation de l’abonnement, veillez à [sauvegarder vos données](back-up-data-before-switching-plans.md).

### <a name="state-deleted"></a>État : Supprimé
  
**Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant qu’il est expiré ou désactivé, il est supprimé.
  
Les administrateurs et les utilisateurs n'ont plus accès aux services ou applications Office inclus dans l'abonnement. Toutes les données client, par exemple les données, les documents et les messages électroniques des utilisateurs, sont supprimées définitivement et irrémédiablement.
  
À ce stade, vous ne pouvez pas réactiver l'abonnement. Toutefois, en tant qu'administrateur général ou administrateur de facturation, vous pouvez toujours accéder à Centre d'administration pour gérer d'autres abonnements ou acheter de nouveaux abonnements pour répondre aux besoins de votre entreprise.
  
> [!NOTE]
>
> - L'ajout d'un nouvel abonnement du même type que celui précédemment supprimé ne restaure pas les données associées à l'abonnement supprimé.
> - Dans le cas d’une suspension de licence provenant d’un fournisseur de solutions Microsoft Cloud, il n’y a pas d’étape expirée de 30 jours et les services sont désactivés immédiatement. Les données sont supprimées après 90 jours si le client n’est pas réactivé par l’ajout d’une nouvelle licence.

### <a name="what-happens-when-my-trial-ends"></a>Que se passe-t-il à l’expiration de ma version d’évaluation ?

À l’expiration de votre version d’évaluation, les services de Microsoft 365 ne peuvent plus être utilisés gratuitement. Plusieurs options s’offrent à vous :

- **Acheter Microsoft 365.** Quand votre version d'évaluation arrive à expiration, elle passe au stade Expiré. Celle-ci vous offre un délai supplémentaire de 30 jours (pour la plupart des versions d'évaluation et dans la plupart des pays et régions) pour acheter Microsoft 365. Pour plus d’informations sur la conversion de votre version d’évaluation en abonnement payant, consultez [Acheter un abonnement à partir de votre version d’évaluation gratuite](../try-or-buy-microsoft-365.md#buy-a-subscription-from-your-free-trial).
- **Prolonger votre version d'évaluation.** Vous avez besoin de davantage de temps pour évaluer Microsoft 365 ? Dans certains cas, vous pouvez [prolonger votre version d’évaluation](../extend-your-trial.md).
- **Annuler la version d’évaluation ou la laisser expirer.** Si vous décidez de ne pas acheter Microsoft 365, vous pouvez laisser expirer ou [annuler](cancel-your-subscription.md) votre version d'évaluation. Veillez à sauvegarder les données que vous souhaitez conserver. Peu de temps après la fin de la phase Expiré de 30 jours, les informations et les données de votre compte d'évaluation sont définitivement supprimées.

> [!NOTE]
>
> Les informations présentes dans cette page sont soumises à la [clause d'exclusion de responsabilité et à l'avis préalable en cas de modification mentionnés dans la politique Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613651). Consultez régulièrement ce site pour passer en revue les modifications susceptibles d'y avoir été apportées.

## <a name="related-content"></a>Contenu connexe

[Annuler un abonnement](./cancel-your-subscription.md)
[Renouveler Microsoft 365 for business](./renew-your-subscription.md) (article)\
[Réactiver un abonnement](./reactivate-your-subscription.md) (article)
