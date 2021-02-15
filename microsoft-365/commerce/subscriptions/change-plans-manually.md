---
title: Modifier manuellement les plans Microsoft 365 pour les entreprises
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
description: Modifiez les abonnements manuellement en achetant un nouvel abonnement et en vous assurant que les deux abonnements sont répertoriés et actifs.
ms.openlocfilehash: 1127a48ff23c528e3218bae4ccfd063df5e3c26d
ms.sourcegitcommit: 537e513a4a232a01e44ecbc76d86a8bcaf142482
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "50029385"
---
# <a name="change-plans-manually"></a>Modifier manuellement les plans

## <a name="step-1-decide-how-to-change-plans"></a>Étape 1 : Décider comment modifier les plans

La meilleure façon de changer tous vos utilisateurs d’un plan à un autre consiste à [utiliser l’onglet Mise à niveau.](upgrade-to-different-plan.md) Parfois, cela n’est pas possible. Modifiez les plans manuellement à la place :

- Si **l’onglet** Mise à niveau indique que vous ne pouvez pas mettre à niveau le plan actuel.

- Si, lorsque vous sélectionnez **l’onglet** Mise à niveau, le plan que vous souhaitez n’est pas répertorié.

- Si vous ne souhaitez pas mettre à niveau tous vos utilisateurs de la même manière. Certaines entreprises ont besoin de différents utilisateurs abonnés à différentes plans. Utilisez une modification manuelle pour ce faire.

Pour continuer avec une modification manuelle, lisez [Étape 2 : Acheter un nouvel abonnement](#step-2-buy-a-new-subscription) dans cette rubrique.

> [!IMPORTANT]
> Si vous changez de plan avec moins de services liés aux données que votre plan actuel (dégradation), vous devez récupérer manuellement les données que vous souhaitez conserver. Pour plus d’informations, voir [Back up data before changing plans](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>Étape 2 : Acheter un nouvel abonnement

**Déjà acheté ?** Si vous avez déjà un abonnement vers qui vous souhaitez déplacer des [utilisateurs,](#step-3-check-your-new-subscription-and-licenses) ignorez cette étape et passez à l’étape 3 : Vérifiez votre nouvel abonnement et vos nouvelles licences dans cette rubrique.

Ou

**Achetez un nouvel abonnement et des licences :** Suivez les étapes de la procédure d’achat d’un autre abonnement [Microsoft 365](../buy-another-subscription.md) pour les entreprises pour acheter un nouvel abonnement.

Veillez à acheter un abonnement pour la même organisation que les utilisateurs. Par exemple, vérifiez les adresses de messagerie des utilisateurs que vous souhaitez déplacer. Si leurs adresses de messagerie contoso.com, vous devez acheter un nouvel abonnement pour \@ contoso.com.
Incluez une licence pour chaque utilisateur que vous souhaitez déplacer.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Étape 3 : Vérifier votre nouvel abonnement et vos nouvelles licences

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.

2. **Vérifier que les deux abonnements sont répertoriés et actifs** L’abonnement dont vous souhaitez déplacer des utilisateurs et l’abonnement vers qui vous souhaitez déplacer des utilisateurs doivent être répertoriés ensemble. Si le nouvel abonnement n’est pas là lors de la première vérification, essayez à nouveau ultérieurement. Vérifiez que les deux abonnements sont actifs. [Le nouvel abonnement n’est pas répertorié ou n’est pas actif.](#the-new-subscription-isnt-listed-or-isnt-active)

3. **Vérifier que vous avez suffisamment de licences pour chaque utilisateur** Chaque utilisateur a besoin d’une licence qui correspond à son abonnement. Ainsi, si vous souhaitez déplacer dix utilisateurs vers Microsoft 365 Business Premium, vous devez vous assurer que dix licences sont disponibles.

4. **Vous avez besoin de plus de licences pour le nouvel abonnement ?**
   Go to the **Your products** page and buy [more licenses](../licenses/buy-licenses.md).

> [Qu’en est-il des anciennes licences ?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Le nouvel abonnement n’est pas répertorié ou n’est pas actif

- **Si vous avez acheté deux abonnements** et qu’ils ne sont pas répertoriés ici, ils peuvent avoir été achetés pour différentes organisations (pour différents domaines). Les abonnements ne peuvent pas traverser les limites de l’organisation.

- **Si vous savez que vous avez** un abonnement supplémentaire et qu’il n’est pas répertorié ici ou n’est pas actif, appelez le support [Microsoft.](../../admin/contact-support-for-business-products.md)

### <a name="what-about-the-old-licenses"></a>Qu’en est-il des anciennes licences ?

Les licences de l’abonnement actuel seront supprimées ultérieurement . Vous ne payerez que pour les nouvelles licences utilisateur à partir de là.

## <a name="step-4-reassign-licenses"></a>Étape 4 : Réaffecter des licences

### <a name="reassign-a-license-for-one-user"></a>Réaffecter une licence à un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Dans la page **Utilisateurs** actifs, sélectionnez l’utilisateur auquel vous souhaitez attribuer une licence.

3. Sous **l’onglet Licences** et applications, développez **Licences,** sélectionnez les zones des licences que vous souhaitez attribuer, puis sélectionnez **Enregistrer les modifications.**

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Réaffecter des licences à plusieurs utilisateurs à la fois

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les cercles en de côté des noms des utilisateurs pour lesquels vous souhaitez remplacer les licences existantes.

3. En haut, sélectionnez **Plus d’options** (**...**), puis **sélectionnez Gérer les licences de produits.**

4. Sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.

5. Basculez vers la position **Sur** pour les produits que vous souhaitez affecter à ces utilisateurs.

    > [!TIP]
    > - Pour limiter les services disponibles pour l’utilisateur, basculez vers la **position** d’arrêt pour les services que vous souhaitez supprimer pour cet utilisateur. Par exemple, si vous souhaitez que l’utilisateur puisse accéder à tous les services disponibles à l’exception de Skype Entreprise Online, vous pouvez basculer le bouton bascule du service Skype Entreprise Online vers la **position** De.
    > - Les attributions de licences précédentes sont alors supprimées pour les utilisateurs sélectionnés.

6. En bas du volet **Remplacer les produits existants**, sélectionnez **Remplacer** \> **Fermer**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Étape 5 : Annuler des abonnements ou supprimer des licences dont vous n’avez plus besoin (facultatif)

Si vous avez déplacé tous les utilisateurs d’un abonnement vers un autre et que vous n’avez plus besoin de l’abonnement d’origine, vous pouvez [annuler l’abonnement.](cancel-your-subscription.md)

Si vous avez déplacé uniquement certains utilisateurs vers un autre abonnement, supprimez les [licences](../licenses/remove-licenses-from-subscription.md) dont vous n’avez plus besoin.

## <a name="call-support-to-help-you-change-plans"></a>Appeler le support pour vous aider à modifier les plans
[Appeler le support Microsoft](../../admin/contact-support-for-business-products.md)
