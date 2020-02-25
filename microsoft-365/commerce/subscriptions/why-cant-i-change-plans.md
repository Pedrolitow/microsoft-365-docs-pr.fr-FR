---
title: Pourquoi ne puis-je pas modifier les offres Office 365 pour les entreprises ?
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- commerce
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ROBOTS: NOINDEX
description: Comprenez les raisons pour lesquelles il est parfois nécessaire de modifier les plans manuellement ou en appelant le support technique.
monikerRange: o365-worldwide
ms.openlocfilehash: 4f193db074dccb8146615b72febc62f47a44b7d5
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42243136"
---
# <a name="why-cant-i-upgrade-plans"></a>Pourquoi ne puis-je pas mettre à niveau les plans ?

Si vous ne voyez aucun plan sous l’onglet **mise à niveau** , cela signifie que votre offre ne peut pas être mise à niveau automatiquement. Dans certains cas, vous pouvez résoudre le problème afin de pouvoir afficher les offres disponibles pour la mise à niveau, ou vous pouvez mettre à niveau ou modifier les plans manuellement.

> [!NOTE]
> Cet article s’applique au nouveau centre d’administration. Le nouveau centre d’administration est accessible à tous les administrateurs de Microsoft 365, et vous pouvez vous abonner en sélectionnant **essayer le nouveau centre d’administration** bascule en haut de la page d’accueil. Pour plus d’informations, voir [À propos du nouveau Centre d’administration Microsoft 365](../../admin/microsoft-365-admin-center-preview.md). Pour afficher l’article à propos de l’ancien centre d’administration, consultez la rubrique [pourquoi ne puis-je pas changer d’offre Office 365 pour les entreprises ?](why-can-t-i-switch-plans.md).

## <a name="why-are-there-no-plans-listed-to-upgrade"></a>Pourquoi existe-t-il des plans répertoriés pour la mise à niveau ?

### <a name="you-cant-upgrade-subscriptions-now-because-you-have-more-users-than-licenses"></a>Vous ne pouvez pas mettre à niveau les abonnements maintenant car vous disposez de plus d’utilisateurs que de licences.

Pour effectuer une mise à niveau automatique des plans, tous vos utilisateurs doivent disposer de licences valides. Si vous avez attribué un nombre de licences supérieur à celui acheté, une alerte indiquant un conflit de licence devant être résolu s'affichera sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences</a>. [Découvrez comment résoudre les conflits de licence.](../../admin/manage/resolve-license-conflicts.md) Une fois que vous avez résolu les conflits de licence, vous devez voir les plans affichés sous l’onglet **mise à niveau** . Si ce n’est pas le cas, vous pouvez [modifier les offres manuellement](change-plans-manually.md)ou [appeler le support technique](../../admin/contact-support-for-business-products.md).

### <a name="you-cant-upgrade-subscriptions-right-now-because-this-subscription-isnt-fully-set-up-or-the-service-isnt-available"></a>Vous ne pouvez pas mettre à niveau les abonnements pour le moment car cet abonnement n'\'est pas entièrement configuré ou le service n’est pas disponible.

Par exemple, si l’un des services rencontre un incident, vous ne pourrez pas effectuer la mise à niveau tant que tous les services ne seront pas sains. Pour voir s’il existe des problèmes liés à l’intégrité des services ou de l’approvisionnement, dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">État du service</a> d' **intégrité** \> .

Si vous découvrez qu'un service n'est pas entièrement configuré ou si vous rencontrez un problème d'état du service, attendez quelques heures que votre service redevienne disponible et réessayez. Si le problème persiste, appelez le [support technique](../../admin/contact-support-for-business-products.md).

### <a name="you-cant-upgrade-plans-because-another-plan-is-in-the-process-of-being-upgraded-or-is-pending-a-credit-check"></a>Vous ne pouvez pas mettre à niveau les plans car une autre offre est en cours de mise à niveau ou est en attente d’une vérification de solvabilité.

Attendez la fin de la vérification de solvabilité avant de mettre à niveau les plans. La vérification du crédit peut prendre jusqu'à deux jours ouvrés.

### <a name="currently-this-subscription-is-not-eligible-to-upgrade"></a>Actuellement, cet abonnement n’est pas éligible à la mise à niveau.

Vous pouvez [modifier les offres manuellement](change-plans-manually.md) ou [appeler le support technique](../../admin/contact-support-for-business-products.md).

### <a name="i-see-a-different-message-than-whats-listed-here"></a>Le message qui s'affiche n'est pas dans cette liste.

Vous pouvez [modifier les offres manuellement](change-plans-manually.md) ou [appeler le support technique](../../admin/contact-support-for-business-products.md).

## <a name="additional-reasons-you-cant-upgrade"></a>Raisons supplémentaires que vous ne pouvez pas mettre à niveau

### <a name="you-have-two-or-more-plans-for-the-same-product"></a>Vous disposez de deux ou plusieurs offres pour le même produit

L’onglet **mise à niveau** ne peut être utilisé que si tous les utilisateurs s’abonnent à la même offre. Par exemple, si vous avez deux plans Office 365 Business Premium, vous ne pourrez pas mettre à niveau automatiquement l’un d’entre eux vers un autre plan.

### <a name="you-have-a-prepaid-plan"></a>Vous avez une offre prépayée.

Si vous avez payé votre abonnement à l’avance, vous pourrez peut-être [modifier les offres manuellement](change-plans-manually.md). Toutefois, vous ne recevrez pas de crédit pour le temps non utilisé restant sur votre abonnement actuel si vous mettez à niveau les plans avant l’expiration du plan actuel.

Vous pouvez également [appeler le support](../../admin/contact-support-for-business-products.md) pour obtenir de l’aide.

### <a name="you-have-a-government-or-non-profit-plan"></a>Vous avez une offre destinée au secteur public ou aux organismes à but non lucratif

Si vous avez une offre publique ou à but non lucratif, vous pouvez [modifier les offres manuellement](change-plans-manually.md) ou [appeler le support](../../admin/contact-support-for-business-products.md) pour obtenir de l’aide.

### <a name="the-subscription-that-you-want-to-upgrade-from-has-a-temporary-issue"></a>L’abonnement à partir duquel vous souhaitez effectuer la mise à niveau a un problème temporaire.

Vous ne verrez peut-être aucun plan sous l’onglet **mise à niveau** , car le service est en train de mettre à niveau un volume élevé de plans. Essayez à nouveau environ une heure après votre première tentative.

### <a name="the-plan-that-you-want-to-upgrade-to-isnt-a-supported-option"></a>L’offre sur laquelle vous souhaitez effectuer la mise à niveau n’est pas prise en charge.

Lorsque vous mettez à niveau les plans, les plans disponibles pour la mise à niveau sont affichés en fonction des services de votre forfait actuel. Vous pouvez uniquement effectuer une mise à niveau vers un plan qui a les mêmes services liés aux données, comme Exchange Online ou SharePoint Online, ou vers une version ultérieure. Cela garantit que les utilisateurs\'ne perdent pas les données liées à ces services pendant la mise à niveau.

Si votre plan ne peut pas être mis à niveau automatiquement, vous pouvez [modifier les plans manuellement](change-plans-manually.md). Vous pouvez également [appeler le support](../../admin/contact-support-for-business-products.md) pour obtenir de l’aide.

### <a name="your-subscription-has-an-add-on"></a>Votre abonnement dispose d’un module complémentaire

Si vous disposez d’un module complémentaire avec votre abonnement, vous pourrez peut-être [modifier les offres manuellement](change-plans-manually.md).

### <a name="your-subscription-has-an-unpaid-balance"></a>Votre abonnement a un solde impayé

Pour résoudre ce message, recherchez l’abonnement sur la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">produits & services</a> , puis sélectionnez le lien **payer maintenant** dans la section **facturation** . Une fois le paiement effectué, réactivez l’onglet **mise à niveau** .

## <a name="call-support-to-help-you-change-plans"></a>Appeler le support pour vous aider à modifier les offres
[Appeler le support Microsoft](../../admin/contact-support-for-business-products.md)