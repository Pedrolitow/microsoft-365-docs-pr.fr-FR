---
title: Qu’arrive-t-il à mes données et à mon accès à la fin de mon abonnement ?
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
- Adm_TOC
- commerce
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 4436582f-211a-45ec-b72e-33647f97d8a3
description: Découvrez ce qu’il advient de vos données lorsque votre abonnement Microsoft 365 pour les entreprises expire, est désactivé ou si vous annulez.
ms.openlocfilehash: c191b2fa795614a272b28cedae8d23693933dc95
ms.sourcegitcommit: 0badd6a7af803a52c7c46a4374211cb89307eacf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "49135978"
---
# <a name="what-happens-to-my-data-and-access-when-my-microsoft-365-for-business-subscription-ends"></a>Qu’advient-il de mes données et de mon accès à la fin de mon abonnement Microsoft 365 pour les entreprises ?

Si votre abonnement prend fin, soit parce qu’il expire, soit parce que vous décidez d’annuler votre accès aux services, applications et données client Microsoft 365, il passe par plusieurs états avant que l’abonnement soit complètement désactivé ou *supprimé.* Si vous êtes conscient de cette progression, vous serez mieux équipé pour revenir à l’état actif de votre abonnement avant qu’il ne soit trop tard, ou, si vous quittez Microsoft 365, de back up vos données avant qu’elles ne soient finalement supprimées.

Lisez ces informations importantes avant de contacter le [support Microsoft 365.](https://docs.microsoft.com/microsoft-365/admin/contact-support-for-business-products)
  
## <a name="what-happens-to-data-when-a-subscription-expires"></a>Qu’advient-il des données à l’expiration d’un abonnement ?

- Si votre abonnement expire, il passe par les étapes suivantes : Expiré / Désactivé/ Supprimé. L’étape Expirée commence immédiatement après que l’abonnement a atteint sa date de fin.
- Si vous désactiver la facturation périodique sur votre abonnement annuel, elle passe par les mêmes étapes qu’un abonnement expiré. La première étape commence par l’anniversaire de l’abonnement annuel, et non à la date à laquelle vous avez désactivé le paramètre de facturation périodique de l’abonnement.
- Si vous annulez votre abonnement mensuel, il est désactivé immédiatement (à la date d’annulation). Cela signifie que vos utilisateurs perdent immédiatement l’accès aux biens Microsoft 365 et que seuls les administrateurs ont accès aux données pour les 90 prochains jours.

Le tableau suivant explique ce à quoi vous pouvez vous attendre à l’expiration d’un abonnement Microsoft 365 pour les entreprises payant.

| Actif | Expiré <br/>(30 \* jours) | Désactivé <br/>(90 \* jours) | Deleted |
|------------------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| *Données accessibles à tous*                                               | *Données accessibles à tous*                                                     | *Données accessibles uniquement aux administrateurs*                                             | **Les données supprimées d’Azure Active Directory sont supprimées, si elles ne sont <br/> pas en cours d’utilisation par d’autres services** |
| Les utilisateurs ont un accès normal à Microsoft 365, aux fichiers et aux applications   | Les utilisateurs ont un accès normal à Microsoft 365, aux fichiers et aux applications              | Les utilisateurs ne peuvent pas accéder à Microsoft 365, fichiers ou applications                        | Les utilisateurs ne peuvent pas accéder à Microsoft 365, fichiers ou applications                                     |
| Les administrateurs ont un accès normal à Microsoft 365, aux données et aux applications Office | Les administrateurs peuvent accéder au Centre d’administration                                           | Les administrateurs peuvent accéder au Centre d’administration, mais ne peuvent pas attribuer de licences aux utilisateurs       | Les administrateurs peuvent accéder au Centre d’administration pour acheter et gérer d’autres abonnements             |
|                                                                        | Les administrateurs globaux ou de facturation peuvent réactiver l’abonnement dans le Centre d’administration | Les administrateurs globaux ou de facturation peuvent réactiver l’abonnement dans le Centre d’administration |                                                                                           |

*Pour la plupart des offres, dans la plupart des pays et régions.
  
> [!NOTE]
> **Qu'est-ce que les « données client » ?** Les données client, telles que définies dans les conditions d’utilisation du service En ligne [de Microsoft,](https://go.microsoft.com/fwlink/p/?LinkId=613649)font référence à toutes les données, y compris tous les fichiers texte, son ou image fournis à Microsoft par le client ou pour son compte via l’utilisation des services Microsoft 365 par le client. Pour en savoir plus sur la protection des données client, consultez La mise en place du portail d’confiance [des services Microsoft.](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-service-trust-portal)

## <a name="what-happens-if-i-cancel-a-subscription"></a>Que se passe-t-il si j'annule un abonnement ?

Si vous annulez votre abonnement avant sa date de fin de période, l’abonnement ignore l’état expiré et passe directement à l’état désactivé, qui est de 90 jours pour la plupart des abonnements, dans la plupart des pays et régions. Nous vous [](back-up-data-before-switching-plans.md) recommandons de les mettre à jour avant l’annulation, mais en tant qu’administrateur, vous pouvez toujours accéder aux données de votre organisation et les les mettre à l’état désactivé. Toutes les données client que vous laissez derrière vous peuvent être supprimées après 90 jours, et le seront assurément au plus tard 180 jours après l'annulation.
  
Voici ce à quoi vous et vos utilisateurs devez vous attendre si vous annulez un abonnement.
  
- **Accès administrateur** Les administrateurs peuvent toujours se connecter et accéder au Centre d’administration, et acheter d’autres abonnements si nécessaire. En tant qu’administrateur global ou de facturation, vous avez 90 jours pour [réactiver](reactivate-your-subscription.md) l’abonnement avec toutes les données intactes.

- **Accès des utilisateurs** Vos utilisateurs ne seront pas en mesure d’utiliser des services tels que OneDrive Entreprise ou d’accéder aux données client, par exemple, les e-mails ou les documents sur les sites d’équipe. Les applications Office, telles que Word et Excel, finissent par passer en mode d'utilisation en lecture seule avec fonctionnalités réduites, et affichent des [notifications Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx).

Pour savoir comment annuler votre abonnement, voir [Annuler votre abonnement.](cancel-your-subscription.md)
  
> [!IMPORTANT]
> Si vous souhaitez que vos données d’abonnement soient supprimées avant la fin de la période désactivée classique, vous pouvez [fermer votre compte.](../close-your-account.md)
  
## <a name="what-are-my-options-if-my-subscription-is-about-to-expire"></a>Quelles options s'offrent à moi si mon abonnement expire bientôt ?

Pendant qu’un abonnement est actif, vous et vos utilisateurs finaux avez un accès normal à vos données, services tels que la messagerie, OneDrive Entreprise et les applications Office. En tant qu’administrateur, vous recevrez une série de notifications par courrier électronique et dans le centre d’administration lorsque votre abonnement approche de sa date d’expiration.
  
Avant que l’abonnement n’atteigne sa date d’expiration, plusieurs options s’offrent à vous :

::: moniker range="o365-worldwide"
  
- **Activer la facturation périodique pour l’abonnement.**

  - Si **la facturation périodique** est déjà allumée, vous n’avez aucune action à prendre. Votre abonnement est facturé automatiquement et vous êtes facturé pour une année ou un mois supplémentaire, en fonction de votre fréquence de paiement actuelle. Si, pour une raison  quelconque, vous avez désactivé la facturation périodique, vous pouvez toujours la [ré-activer.](renew-your-subscription.md)

  - Si vous avez acheté Microsoft 365 Apps for business avec une carte prépayée, vous pouvez activer la facturation périodique [de](renew-your-subscription.md) votre abonnement.

  - Si vous êtes un client de licence en volume Open avec un abonnement prépayé d’un an, contactez votre partenaire pour acheter une nouvelle clé de produit. Vous recevrez des instructions par courrier électronique pour activer votre clé dans le [Centre de gestion des licences en volume Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=282016). Pour découvrir comment trouver un nouveau partenaire ou le partenaire avec qui vous avez travaillé dans le passé, consultez Rechercher votre partenaire ou [revendeur.](../../admin/manage/find-your-partner-or-reseller.md)

  - Si vous avez Microsoft 365 Apps for business, voir [Gérer la facturation périodique de votre abonnement.](renew-your-subscription.md)

- **Laisser votre abonnement expirer.**

  - Si vous payez par carte bancaire ou par facture et que vous ne souhaitez pas poursuivre votre abonnement, désactiver [la facturation périodique.](renew-your-subscription.md) Votre abonnement se termine à sa date d’expiration et vous pouvez ignorer toutes les notifications par courrier électronique associées.

  - Si vous êtes un client de licence en volume Open travaillant avec un partenaire, vous pouvez laisser votre abonnement expirer en n’prenant aucune mesure.

  - Si vous êtes un client Office 365 Petite Entreprise Premium et que vous avez prépayé Office 365 et l’avez activé avec une clé de produit, vous pouvez laisser votre abonnement expirer en n’prenant aucune mesure.

- **Annulez votre abonnement avant son expiration.** Pour plus d’informations, voir [Annuler votre abonnement.](cancel-your-subscription.md)
  
::: moniker-end

::: moniker range="o365-germany"
  
- **Gérer la facturation périodique de l’abonnement.**

  - Si **la facturation périodique** est déjà allumée, vous n’avez aucune action à prendre. Votre abonnement est facturé automatiquement et vous devrez payer une année ou un mois supplémentaire, selon la fréquence de paiement actuelle. Si, pour une raison  quelconque, vous avez désactivé la facturation périodique, vous pouvez toujours la [ré-activer.](renew-your-subscription.md)

  - Si vous avez acheté Microsoft 365 Apps for business avec une carte prépayée, vous pouvez activer la facturation périodique [de](renew-your-subscription.md) votre abonnement.

  - Si vous êtes un client de licence en volume Open avec un abonnement prépayé d’un an, contactez votre partenaire pour acheter une nouvelle clé de produit. Vous recevrez des instructions par courrier électronique pour activer votre clé dans le [Centre de gestion des licences en volume Microsoft](https://go.microsoft.com/fwlink/p/?LinkID=282016). Pour découvrir comment trouver un nouveau partenaire ou le partenaire avec qui vous avez travaillé dans le passé, consultez Rechercher votre partenaire ou [revendeur.](../../admin/manage/find-your-partner-or-reseller.md)

  - Si vous avez Microsoft 365 Apps for business, voir [Renouveler votre abonnement.](renew-your-subscription.md)

- **Laisser votre abonnement expirer.**

  - Si vous payez par carte bancaire ou par facture et que vous ne souhaitez pas poursuivre votre abonnement, désactiver [la facturation périodique.](renew-your-subscription.md) Votre abonnement expirera à sa date d’expiration et vous pouvez ignorer toutes les notifications par courrier électronique associées.

  - Si vous êtes un client de licence en volume Open travaillant avec un partenaire, vous pouvez laisser votre abonnement expirer en n’prenant aucune mesure.

  - Si vous êtes un client Office 365 Petite Entreprise Premium et que vous avez prépayé Office 365 et l’avez activé avec une clé de produit, vous pouvez laisser votre abonnement expirer en n’prenant aucune mesure.

- **Annulez votre abonnement avant son expiration.** Pour plus d’informations, voir [Annuler votre abonnement.](cancel-your-subscription.md)
  
::: moniker-end

::: moniker range="o365-21vianet"
  
- **Renouveler l'abonnement.** Si **la facturation périodique** est déjà allumée, vous n’avez aucune action à prendre. Votre abonnement est facturé automatiquement et vous devrez payer une année ou un mois supplémentaire, selon la fréquence de paiement actuelle. Si, pour une raison  quelconque, vous avez désactivé la facturation périodique, vous pouvez toujours la [ré-activer.](renew-your-subscription.md)

- **Laisser votre abonnement expirer.** Si vous payez par carte bancaire ou par facture et que vous ne souhaitez pas poursuivre votre abonnement, désactiver [la facturation périodique.](renew-your-subscription.md) Votre abonnement expirera à sa date d’expiration et vous pouvez ignorer toutes les notifications par courrier électronique associées.

- **Annulez votre abonnement avant son expiration.** Pour plus d’informations, voir [Annuler votre abonnement.](cancel-your-subscription.md)

::: moniker-end

## <a name="what-happens-after-my-subscription-expires"></a>Que se passe-t-il une fois mon abonnement expiré ?
Si vous laissez votre abonnement expirer, il passe par plusieurs états avant sa suppression finale. Cela vous donne le temps, en tant qu’administrateur, de vous réactiver si vous souhaitez continuer le service ou de back up vos données si vous décidez de ne plus vouloir l’abonnement.
  
Voici ce que vous pouvez attendre lorsque votre abonnement atteint les différents états.
  
### <a name="state-expired"></a>État : expiré
  
::: moniker range="o365-worldwide"

 **Ce à quoi vous devez vous attendre :** L'état Expiré dure 30 jours pour la plupart des abonnements, y compris les abonnements achetés via un contrat [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), et dans la plupart des pays et régions. Pour les produits avec licence en volume, à l'exception du contrat Microsoft Open, l'état Expiré dure 90 jours.

::: moniker-end

::: moniker range="o365-germany"

 **Ce à quoi vous devez vous attendre :** L'état Expiré dure 30 jours pour la plupart des abonnements, y compris les abonnements achetés via un contrat [Microsoft Open](https://go.microsoft.com/fwlink/p/?LinkID=613298), et dans la plupart des pays et régions. Pour les produits avec licence en volume, à l'exception du contrat Microsoft Open, l'état Expiré dure 90 jours.

::: moniker-end

::: moniker range="o365-21vianet"

 **Ce à quoi vous devez vous attendre :** l'état Expiré dure 30 jours pour la plupart des abonnements et dans la plupart des pays et régions.

::: moniker-end

Dans cet état, les utilisateurs ont un accès normal au portail Microsoft 365, aux applications Office et aux services tels que la messagerie et SharePoint Online.
  
En tant qu’administrateur, vous avez toujours accès au Centre d’administration. Ne vous inquiétez pas : les administrateurs globaux ou de facturation peuvent [réactiver](reactivate-your-subscription.md) l’abonnement et continuer à utiliser Microsoft 365. Si vous ne réactivez pas, [vous devez les récupérer.](back-up-data-before-switching-plans.md)
  
### <a name="state-disabled"></a>État : désactivé
  
::: moniker range="o365-worldwide"

 **Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant que son état est Expiré, il passe à l'état Désactivé (90 jours pour la plupart des abonnements et dans la plupart des pays et régions). Pour les produits avec licence en volume, l'état Désactivé dure 30 jours.

::: moniker-end

::: moniker range="o365-germany"

 **Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant que son état est Expiré, il passe à l'état Désactivé (90 jours pour la plupart des abonnements et dans la plupart des pays et régions). Pour les produits avec licence en volume, l'état Désactivé dure 30 jours.

::: moniker-end

::: moniker range="o365-21vianet"

 **Ce à quoi vous devez vous attendre :** si vous ne réactivez pas votre abonnement tant que son état est Expiré, il passe à l'état Désactivé (90 jours pour la plupart des abonnements et dans la plupart des pays et régions).

::: moniker-end

::: moniker range="o365-worldwide"

Dans cet état, votre niveau d'accès est considérablement restreint. Vos utilisateurs ne peuvent pas se connecter ou accéder à des services tels que la messagerie ou SharePoint Online. Les applications Office passent en mode d'utilisation avec fonctionnalités réduites et affichent des notifications [Produit sans licence](https://support.microsoft.com/office/0d23d3c0-c19c-4b2f-9845-5344fedc4380.aspx). Vous pouvez toujours vous inscrire et vous rendre au Centre d’administration, mais vous ne pouvez pas attribuer de licences aux utilisateurs. Vos données client, c'est-à-dire l'ensemble des données, messages électroniques et fichiers d'utilisateurs stockés sur des sites d'équipe, sont accessibles uniquement à vous et aux autres administrateurs.

::: moniker-end

En tant qu’administrateur global ou de facturation, vous pouvez [réactiver](reactivate-your-subscription.md) l’abonnement et continuer à utiliser Microsoft 365 avec toutes vos données client intactes. Si vous choisissez de ne pas la réactiver, [vous devez la réactiver.](back-up-data-before-switching-plans.md)

### <a name="state-deleted"></a>État : supprimé
  
 **À quoi s’attendre :** Si vous ne réactivez pas votre abonnement pendant qu’il est en période de grâce ou désactivé, l’abonnement est supprimé.
  
Les administrateurs et les utilisateurs n'ont plus accès aux services ou applications Office inclus dans l'abonnement. Toutes les données client( des données utilisateur aux documents et courriers électroniques) sont définitivement supprimées et irrécables.
  
À ce stade, vous ne pouvez pas réactiver l'abonnement. Toutefois, en tant qu’administrateur global ou de facturation, vous pouvez toujours accéder au Centre d’administration pour gérer d’autres abonnements ou acheter de nouveaux abonnements pour répondre aux besoins de votre entreprise.
  
> [!NOTE]
> L’ajout d’un nouvel abonnement du même type que celui qui a été supprimé ne restaure pas les données associées à l’abonnement supprimé.


> [!NOTE]
> Si une licence CSP est suspendue, il n’y a pas de période de grâce de 30 jours et les services sont désactivés immédiatement. Les données sont supprimées au bout de 90 jours si le client n’est pas réactivé en ajoutant une nouvelle licence.

### <a name="what-happens-when-my-trial-ends"></a>Que se passe-t-il à l'expiration de ma version d'évaluation ?

Lorsque votre version d’essai se termine, vous ne pouvez pas continuer à utiliser Microsoft 365 gratuitement. Plusieurs options s'offrent à vous :

::: moniker range="o365-worldwide"

- **Achetez Microsoft 365.** Lorsque votre version d’essai arrive à expiration, elle passe à une période de grâce, ce qui vous donne 30 jours supplémentaires (pour la plupart des essais, dans la plupart des pays et régions) pour acheter Microsoft 365. Pour savoir comment convertir votre version d’essai en abonnement payant, voir Acheter votre version d’essai de [Microsoft 365 pour les entreprises.](../buy-a-subscription-from-your-free-trial.md)

::: moniker-end

::: moniker range="o365-germany"

- **Achetez Microsoft 365.** Lorsque votre version d’essai arrive à expiration, elle passe à une période de grâce, ce qui vous donne 30 jours supplémentaires (pour la plupart des essais, dans la plupart des pays et régions) pour acheter Microsoft 365. Pour savoir comment convertir votre version d’essai en abonnement payant, voir Acheter votre version d’essai de [Microsoft 365 pour les entreprises.](../buy-a-subscription-from-your-free-trial.md)

::: moniker-end

::: moniker range="o365-21vianet"

- **Achetez Office 365.** Lorsque votre version d’essai arrive à expiration, elle passe à une période de grâce, ce qui vous donne 30 jours supplémentaires (pour la plupart des essais, dans la plupart des pays et régions) pour acheter Office 365. Pour plus d'informations sur la conversion de votre version d'évaluation en abonnement payant, voir [Buy or try subscriptions for Office 365 operated by 21Vianet](../../admin/services-in-china/buy-or-try-subscriptions.md).

::: moniker-end

- **Prolonger votre version d'évaluation.** Vous avez besoin de davantage de temps pour évaluer Microsoft 365 ? Dans certains cas, vous pouvez [prolonger votre version d’essai.](../extend-your-trial.md)

- **Annuler la version d'évaluation ou la laisser expirer.** Si vous décidez de ne pas acheter Microsoft 365, vous pouvez laisser votre version d’essai expirer ou [l’annuler.](cancel-your-subscription.md) Back up any data you want to keep. Peu de temps après la fin de la période de grâce de 30 jours, les informations et les données de votre compte d'évaluation sont définitivement supprimées.

> [!NOTE]
> Les informations présentes dans cette page sont soumises à la [clause d'exclusion de responsabilité et à l'avis préalable en cas de modification mentionnés dans la politique Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=613651). Revenir régulièrement à ce site pour passer en revue les modifications.

## <a name="related-content"></a>Contenu connexe 

[Annuler votre abonnement](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/cancel-your-subscription) (article)\
[Renouveler Microsoft 365 pour les entreprises](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/renew-your-subscription) (article)\
[Réactiver votre abonnement](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/reactivate-your-subscription) (article)

