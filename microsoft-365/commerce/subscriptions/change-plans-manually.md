---
title: Modifier manuellement les offres Microsoft 365 pour les entreprises
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
- BCS160
- MET150
- MOE150
- BEA160
ROBOTS: NOINDEX
description: Modifiez les abonnements manuellement en achetant un nouvel abonnement et en vous assurant que les abonnements sont répertoriés et actifs.
ms.openlocfilehash: 09557b3556db1e6f17d7a4cd54a88ba34d0f0bd7
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48647818"
---
# <a name="change-plans-manually"></a>Modifier les offres manuellement

## <a name="step-1-decide-how-to-change-plans"></a>Étape 1 : décider de la façon de modifier les offres

La meilleure façon de modifier tous les utilisateurs d’un plan à un autre consiste à [utiliser l’onglet mise à niveau](upgrade-to-different-plan.md). Parfois, cela n’est pas possible. Modifiez les plans manuellement à la place :

- Si l’onglet **mise à niveau** indique que vous ne pouvez pas mettre à niveau le plan actuel.

- Si, lorsque vous sélectionnez l’onglet **mise à niveau** , le plan souhaité n’est pas affiché.

- Si vous ne souhaitez pas mettre à niveau tous les utilisateurs de la même manière. Certaines entreprises ont besoin de différents utilisateurs qui s’abonnent à différents plans. Utilisez une modification manuelle pour ce.

Pour poursuivre une modification manuelle, lisez l' [étape 2 : acheter un nouvel abonnement](#step-2-buy-a-new-subscription) dans cette rubrique.

> [!IMPORTANT]
> Si vous passez à un plan avec moins de services liés aux données par rapport à votre forfait actuel (rétrogradation), vous devez sauvegarder manuellement les données que vous souhaitez conserver. Pour plus d’informations, consultez la rubrique [sauvegarder les données avant de modifier les offres](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Étape 2 : acheter un nouvel abonnement

**Vous avez déjà acheté ?** Si vous disposez déjà d’un abonnement auquel vous souhaitez déplacer des utilisateurs, ignorez cette étape et passez à [l’étape 3 : Vérifiez votre nouvel abonnement et vos licences](#step-3-check-your-new-subscription-and-licenses) dans cette rubrique.

OR

**Acheter un nouvel abonnement et des licences :** Suivez les étapes de la procédure [acheter un autre abonnement Microsoft 365 pour les entreprises](../buy-another-subscription.md) pour acheter un nouvel abonnement.

Assurez-vous que vous achetez un abonnement pour la même organisation que les utilisateurs. Par exemple, vérifiez les adresses de messagerie des utilisateurs que vous souhaitez déplacer. Si leurs adresses de messagerie incluent \@ contoso.com, vous devez acheter un nouvel abonnement pour contoso.com.
Incluez une licence pour chaque utilisateur que vous souhaitez déplacer.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Étape 3 : vérifier votre nouvel abonnement et vos nouvelles licences

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

2. **Vérifier que les deux abonnements sont répertoriés et actifs** L’abonnement à partir duquel vous déplacez les utilisateurs et l’abonnement vers lequel vous déplacez les utilisateurs doivent être regroupés. Si le nouvel abonnement n’est pas présent lors de la vérification initiale, réessayez ultérieurement. Vérifiez que les deux abonnements sont actifs. [Le nouvel abonnement n’est pas indiqué, ou n’est pas actif](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Vérifier que vous disposez de suffisamment de licences pour chaque utilisateur** Chaque utilisateur doit disposer d’une licence correspondant à son abonnement. Par conséquent, si vous souhaitez déplacer dix utilisateurs vers Microsoft 365 Business Premium, vous devez vous assurer que dix licences sont disponibles.

4. **Vous avez besoin de plus de licences pour le nouvel abonnement ?**
   Accédez à la page **vos produits** et [achetez plus de licences](../licenses/buy-licenses.md).

> [Qu’en est-il des anciennes licences ?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Le nouvel abonnement n’est pas indiqué, ou n’est pas actif

- **Si vous avez acheté deux abonnements et qu’ils ne sont pas répertoriés ici**, ils ont peut-être été achetés pour différentes organisations (pour différents domaines). Les abonnements ne peuvent pas franchir les limites de l’organisation.

- **Si vous êtes certain d’avoir un abonnement supplémentaire**et qu’il n’est pas répertorié ici, ou n’est pas actif, [appelez le support Microsoft](../../admin/contact-support-for-business-products.md).

### <a name="what-about-the-old-licenses"></a>Qu’en est-il des anciennes licences ?

Les licences pour l’abonnement actuel seront supprimées ultérieurement ; vous ne payez que les nouvelles licences utilisateur à partir de Then.

## <a name="step-4-reassign-licenses"></a>Étape 4 : réattribuer des licences

### <a name="reassign-a-license-for-one-user"></a>Réattribuer une licence pour un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sur la page **utilisateurs actifs** , sélectionnez l’utilisateur auquel vous souhaitez attribuer une licence.

3. Sous l’onglet **licences et applications** , développez **licences**, activez les cases à cocher correspondant aux licences que vous souhaitez attribuer, puis sélectionnez **enregistrer les modifications**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Réattribuer des licences pour plusieurs utilisateurs à la fois

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les cercles en regard des noms des utilisateurs pour lesquels vous souhaitez remplacer les licences existantes.

3. En haut, sélectionnez **autres options** (**...**), puis **gérer les licences des produits**.

4. Sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.

5. Activez **le bouton** bascule pour les produits que vous souhaitez attribuer à ces utilisateurs.

    > [!TIP]
    > - Pour limiter les services disponibles pour l’utilisateur, basculez en mode de basculement vers l' **arrêt** pour les services que vous souhaitez supprimer pour cet utilisateur. Par exemple, si vous souhaitez que l’utilisateur ait accès à tous les services disponibles à l’exception de Skype entreprise Online, vous pouvez activer **ou désactiver le** bouton bascule pour le service Skype entreprise online.
    > - Les attributions de licences précédentes sont alors supprimées pour les utilisateurs sélectionnés.

6. En bas du volet **Remplacer les produits existants**, sélectionnez **Remplacer** \> **Fermer**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Étape 5 : annulez les abonnements ou supprimez les licences dont vous n’avez plus besoin (facultatif)

Si vous avez déplacé tous les utilisateurs d’un abonnement vers un autre, et que vous n’avez plus besoin de l’abonnement d’origine, vous pouvez [Annuler l’abonnement](cancel-your-subscription.md).

Si vous avez déplacé uniquement certains utilisateurs vers un autre abonnement, [supprimez les licences](../licenses/remove-licenses-from-subscription.md) dont vous n’avez plus besoin.

## <a name="call-support-to-help-you-change-plans"></a>Appeler le support pour vous aider à modifier les offres
[Appeler le support Microsoft](../../admin/contact-support-for-business-products.md)