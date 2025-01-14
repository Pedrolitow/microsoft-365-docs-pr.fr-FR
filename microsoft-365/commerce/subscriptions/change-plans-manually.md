---
title: Modifier manuellement les plans Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: nalinkla, jmueller
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: Modifiez les abonnements manuellement en achetant un nouvel abonnement et en veillant à ce que les deux abonnements soient répertoriés et actifs.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: 4acc53fd99b9e2c624445f8f724f73766666f13d
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68736318"
---
# <a name="manually-change-microsoft-plans"></a>Modifier manuellement les plans Microsoft

## <a name="step-1-decide-how-to-change-plans"></a>Étape 1 : Décider comment modifier les plans

La meilleure façon de changer tous vos utilisateurs d’un plan à un autre consiste à [utiliser l’onglet Mise à niveau](upgrade-to-different-plan.md). Parfois, ce n’est pas possible. Modifiez les plans manuellement à la place :

- Si l’onglet **Mise à niveau** indique que vous ne pouvez pas mettre à niveau le plan actuel.

- Si, lorsque vous sélectionnez l’onglet **Mise à niveau** , le plan souhaité n’est pas répertorié.

- Si vous ne souhaitez pas mettre à niveau tous vos utilisateurs de la même façon. Certaines entreprises ont besoin d’utilisateurs différents abonnés à différents plans. Utilisez une modification manuelle pour cela.

Pour poursuivre une modification manuelle, lisez [Étape 2 : Acheter un nouvel abonnement](#step-2-buy-a-new-subscription) dans cette rubrique.

> [!IMPORTANT]
> Si vous passez à un plan avec moins de services liés aux données que votre plan actuel (rétrogradation), vous devez sauvegarder manuellement toutes les données que vous souhaitez conserver. Pour plus d’informations, consultez [Sauvegarder des données avant de changer de plan](move-users-different-subscription.md).

## <a name="step-2-buy-a-new-subscription"></a>Étape 2 : Acheter un nouvel abonnement

**Vous avez déjà acheté ?** Si vous disposez déjà d’un abonnement vers lequel vous souhaitez déplacer des utilisateurs, ignorez cette étape et [passez à Étape 3 : Vérifier votre nouvel abonnement et vos nouvelles licences](#step-3-check-your-new-subscription-and-licenses) dans cette rubrique.

OR

**Acheter un nouvel abonnement et de nouvelles licences :** Suivez les étapes décrites dans [Acheter un autre abonnement Microsoft 365 pour les entreprises](../try-or-buy-microsoft-365.md) pour acheter un nouvel abonnement.

Veillez à acheter un abonnement pour la même organisation que celle dans laquelle se trouvent les utilisateurs. Par exemple, vérifiez les adresses e-mail des utilisateurs que vous souhaitez déplacer. Si leurs adresses de messagerie incluent \@des contoso.com, vous devez acheter un nouvel abonnement pour contoso.com.
Incluez une licence pour chaque utilisateur que vous souhaitez déplacer.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>Étape 3 : Vérifier votre nouvel abonnement et vos nouvelles licences

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits</a>.

2. **Vérifiez que les deux abonnements sont répertoriés et actifs** L’abonnement à partir duquel vous déplacez des utilisateurs et l’abonnement vers lequel vous déplacez des utilisateurs doivent être répertoriés ensemble. Si le nouvel abonnement n’existe pas lors de la première vérification, réessayez ultérieurement. Vérifiez que les deux abonnements sont actifs. [Le nouvel abonnement n’est pas répertorié ou n’est pas actif](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Vérifier que vous disposez de suffisamment de licences pour chaque utilisateur** Chaque utilisateur a besoin d’une licence qui correspond à son abonnement. Par conséquent, si vous souhaitez déplacer dix utilisateurs vers Microsoft 365 Business Premium, vous devez vous assurer que dix licences sont disponibles.

4. **Vous avez besoin de licences supplémentaires pour le nouvel abonnement ?**
   Accédez à la page **Vos produits** et [achetez d’autres licences](../licenses/buy-licenses.md).

> [Qu’en est-il des anciennes licences ?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Le nouvel abonnement n’est pas répertorié ou n’est pas actif

- **Si vous avez acheté deux abonnements et qu’ils ne sont pas tous les deux répertoriés ici**, ils ont peut-être été achetés pour différentes organisations (pour différents domaines). Les abonnements ne peuvent pas franchir les limites de l’organisation.

- **Si vous savez que vous disposez d’un abonnement supplémentaire**, qu’il n’est pas répertorié ici ou qu’il n’est pas actif, [appelez le support Microsoft](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Qu’en est-il des anciennes licences ?

Les licences de l’abonnement actuel seront supprimées ultérieurement; À partir de là, vous payez uniquement pour les nouvelles licences utilisateur.

## <a name="step-4-reassign-licenses"></a>Étape 4 : Réaffecter des licences

Lorsque vous effectuez une mise à niveau d’un plan Office 365 vers un plan Microsoft 365, vous devez modifier les attributions de licences pour tous les utilisateurs. Les licences ne sont pas automatiquement attribuées lorsque vous modifiez manuellement des plans.

### <a name="reassign-a-license-for-one-user"></a>Réaffecter une licence pour un utilisateur

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Dans la page **Utilisateurs actifs** , sélectionnez l’utilisateur auquel vous souhaitez attribuer une licence.

3. Sous l’onglet **Licences et applications** , développez **Licences**, sélectionnez les zones pour les licences que vous souhaitez attribuer, puis sélectionnez **Enregistrer les modifications**.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Réaffecter des licences pour plusieurs utilisateurs à la fois

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez les cercles en regard des noms des utilisateurs pour lesquels vous souhaitez remplacer les licences existantes.

3. En haut, sélectionnez les trois points (autres actions), puis choisissez **Gérer les licences de produit**.

4. Sélectionnez **Remplacer les attributions de licence de produit existantes** \> **Suivant**.

5. Basculez vers la position **Activé** pour les produits que vous souhaitez affecter à ces utilisateurs.

    > [!TIP]
    > - Pour limiter les services disponibles pour l’utilisateur, basculez vers la position **Désactivé** pour les services que vous souhaitez supprimer pour cet utilisateur. Par exemple, si vous souhaitez que l’utilisateur ait accès à tous les services disponibles, à l’exception de Skype Entreprise Online, vous pouvez basculer le bouton bascule du service Skype Entreprise Online sur la position **Désactivé**.
    > - Les attributions de licences précédentes sont alors supprimées pour les utilisateurs sélectionnés.

6. En bas du volet **Remplacer les produits existants**, sélectionnez **Remplacer** \> **Fermer**.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>Étape 5 : Annuler les abonnements ou supprimer les licences dont vous n’avez plus besoin (facultatif)

Si vous avez déplacé tous les utilisateurs d’un abonnement à un autre et que vous n’avez plus besoin de l’abonnement [d’origine, vous pouvez annuler l’abonnement](cancel-your-subscription.md).

Si vous avez déplacé uniquement certains utilisateurs vers un autre abonnement, [supprimez les licences](../licenses/buy-licenses.md) dont vous n’avez plus besoin.

## <a name="call-support-to-help-you-change-plans"></a>Appeler le support technique pour vous aider à modifier les plans

[Appelez le support Microsoft](../../admin/get-help-support.md).
