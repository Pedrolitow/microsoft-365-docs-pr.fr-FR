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
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Découvrez ce qu’il advient de vos données lorsque votre abonnement Microsoft 365 Business atteint sa date d’expiration, est désactivé, ou que vous procédez à sa résiliation.
ms.date: 09/16/2021
ms.openlocfilehash: a9837a146ff6494ceaa94adeefeeaf6ed7769986
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66128698"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Qu'arrive-t-il à mes données et à mon accès à la fin de mon abonnement Microsoft 365 Business ?

Si votre abonnement prend fin (parce qu'il est arrivé à expiration ou que vous avez décidé de l'annuler), votre accès aux services, applications et données client Microsoft 365 passent par plusieurs états avant la désactivation complète de l'abonnement ou sa *suppression*. Conscient de cette progression, vous aurez toutes les cartes en main pour réactiver votre abonnement avant qu'il ne soit trop tard. Si vous ne souhaitez plus utiliser Microsoft 365, nous vous conseillons de sauvegarder vos données avant leur suppression finale.

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
> **Qu'est-ce que les « données client » ?** Les données client, comme définies dans les [Conditions d'utilisation du service en ligne Microsoft](https://www.microsoft.com/en-us/licensing/product-licensing/products), font référence à toutes les données, y compris les fichiers texte, audio et image qui sont fournis à Microsoft par le client, ou pour le compte du client, au cours de l'utilisation des services Microsoft 365 par le client. Pour en savoir plus sur la protection des données client, voir le [Prise en main du Portail d’approbation de services Microsoft](../../compliance/get-started-with-service-trust-portal.md).

## <a name="what-happens-if-i-cancel-a-subscription"></a>Que se passe-t-il si j’annule un abonnement ?

Si vous annulez votre abonnement avant sa date d'expiration, l'abonnement passe directement à l'état Désactivé (lequel dure 90 jours pour la plupart des abonnements et dans la plupart des pays et régions).en ignorant l’état Expiré. Nous vous recommandons de [sauvegarder vos données](back-up-data-before-switching-plans.md) avant d'annuler votre abonnement. En tant qu'administrateur, vous pouvez toujours accéder aux données de votre organisation et les sauvegarder lorsque votre abonnement présente un état Désactivé. Les données client que vous laissez peuvent être supprimées après 90 jours, et seront supprimées au maximum 180 jours après l'annulation.
  
Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Accès des administrateurs** Les administrateurs peuvent toujours se connecter et accéder au Centre d'administration et acheter d'autres abonnements si nécessaire. En tant qu'administrateur général ou de facturation, vous disposez de 90 jours pour [réactiver l’abonnement](reactivate-your-subscription.md) avec toutes les données intactes.

- **Accès des utilisateurs** Vos utilisateurs ne peuvent plus utiliser les services tels que OneDrive Entreprise ou accéder aux données client (par exemple, des courriers électroniques ou des documents sur des sites d'équipe). Les applications Office, telles que Word et Excel, finissent par passer en mode d'utilisation en lecture seule avec fonctionnalités réduites, et affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380).

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
  - Si la **Facturation périodique** est déjà activée, vous n'avez aucune mesure à prendre. Votre abonnement sera automatiquement facturé et vous serez facturé pour une année ou un mois supplémentaire, en fonction de votre fréquence de paiement actuelle. Si, pour une raison quelconque, vous avez désactivé la **Facturation périodique**, vous pouvez toujours la [réactiver la Facturation périodique](renew-your-subscription.md).
  - Si vous avez acheté Microsoft 365 Apps for business à l’aide d’une carte prépayée, vous pouvez activer la [facturation périodique](renew-your-subscription.md) pour votre abonnement.
  - Si vous êtes client du programme de licence en volume Open avec un abonnement prépayé d'un an, contactez votre partenaire pour acheter une nouvelle clé de produit dans le cadre du renouvellement. Vous recevrez des instructions par courrier électronique pour activer votre clé dans le [Centre VLSC (Volume Licensing Service Center)](https://go.microsoft.com/fwlink/p/?LinkID=282016). Pour découvrir comment rechercher un nouveau partenaire ou trouver le partenaire avec lequel vous avez traité précédemment, voir [Trouver votre partenaire ou revendeur](../../admin/manage/find-your-partner-or-reseller.md).
  - Si vous avez Microsoft 365 Apps for business, consultez la rubrique [Gérer la facturation périodique pour votre abonnement](renew-your-subscription.md).
- **Laisser l’abonnement expirer.**
  - Si vous payez par carte bancaire ou par facture, et que vous ne voulez pas continuer votre abonnement, [désactivez la Facturation périodique](renew-your-subscription.md). Votre abonnement prend fin à sa date d'expiration. Vous pouvez ignorer toutes les notifications par courrier électronique associées.
  - Si vous êtes un client du programme de licences en volume Open et que vous faites appel à un partenaire, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
  - Si vous êtes un client Office 365 Business Premium, et que vous avez une offre prépayée pour votre abonnement activée à l'aide d'une clé de produit, vous pouvez laisser votre abonnement expirer en n'effectuant aucune action.
- **Annulez votre abonnement avant son expiration.** Pour plus d'informations, voir [Annuler votre abonnement](cancel-your-subscription.md).

## <a name="what-happens-after-my-subscription-expires"></a>Que se passe-t-il une fois mon abonnement expiré ?

Si vous laissez votre abonnement expirer, il passe par plusieurs états avant sa suppression finale. En tant qu’administrateur, cela vous laisse le temps de le réactiver si vous voulez continuer à utiliser le service, ou de sauvegarder vos données si vous décidez de ne plus utiliser l’abonnement.
  
Voici ce à quoi vous pouvez vous attendre lorsque votre abonnement atteint ces différents états.
  
### <a name="state-expired"></a>État : Expiré

**Ce à quoi vous devez vous attendre :** L'état Expiré dure 30 jours pour la plupart des abonnements, y compris les abonnements achetés via un contrat [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), et dans la plupart des pays et régions. Pour les produits avec licence en volume, à l'exception du contrat Microsoft Open, l'état Expiré dure 90 jours.

Dans cet état, les utilisateurs disposent d’un accès normal au portail Microsoft 365, aux applications d’Office et aux services tels que le courrier et SharePoint Online.
  
En tant qu'administrateur, vous avez toujours accès au Centre d'administration. Ne vous inquiétez pas, un administrateur général ou un administrateur de facturation peut [réactiver un abonnement](reactivate-your-subscription.md) et continuer à utiliser Microsoft 365. Si vous ne procédez pas à la réactivation, [sauvegardez vos données](back-up-data-before-switching-plans.md).
  
### <a name="state-disabled"></a>État : Désactivé

**Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant que son état est Expiré, il passe à l'état Désactivé (90 jours pour la plupart des abonnements et dans la plupart des pays et régions). Pour les produits avec licence en volume, l'état Désactivé dure 30 jours.

Dans cet état, votre niveau d'accès est considérablement restreint. Vos utilisateurs ne peuvent pas se connecter ou accéder à des services tels que la messagerie électronique ou SharePoint Online. Les applications Office passent en mode lecture seule avec des fonctionnalités réduites et affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380). Vous pouvez toujours vous connecter et accéder au Centre d'administration, mais vous ne pouvez plus attribuer de licences aux utilisateurs. Vos données client, notamment les données, messages électroniques et fichiers d'utilisateurs stockés sur des sites d'équipe, sont accessibles uniquement par vous et d’autres administrateurs.

En tant qu'administrateur général ou de facturation, vous pouvez [réactiver l'abonnement](reactivate-your-subscription.md) et prolonger l’utilisation de Microsoft 365 avec toutes vos données client intactes. Si vous décidez de ne pas réactiver, [sauvegardez vos données](back-up-data-before-switching-plans.md).

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
- **Annuler la version d’évaluation ou la laisser expirer.** Si vous décidez de ne pas acheter Microsoft 365, vous pouvez laisser expirer ou [annuler](cancel-your-subscription.md) votre version d'évaluation. Veillez à sauvegarder les données que vous souhaitez conserver. Peu de temps après la phase expirée de 30 jours, les informations et les données de votre compte d'évaluation sont définitivement supprimées.

> [!NOTE]
>
> Les informations présentes dans cette page sont soumises à la [Clause d'exclusion de responsabilité et à l'avis préalable en cas de modification mentionnés dans la politique Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613651). Consultez régulièrement ce site pour passer en revue les modifications susceptibles d'y avoir été apportées.

## <a name="related-content"></a>Contenu connexe

[Annuler un abonnement](./cancel-your-subscription.md)
[Renouveler Microsoft 365 for business](./renew-your-subscription.md) (article)\
[Réactiver un abonnement](./reactivate-your-subscription.md) (article)
