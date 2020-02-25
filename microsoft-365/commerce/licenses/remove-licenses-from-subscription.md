---
title: Supprimer des licences de votre abonnement Office 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- commerce
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 9c64d127-e2dd-4ecc-81f5-2f87e5a74803
description: Découvrez comment supprimer une licence de votre abonnement Office 365 pour les entreprises lorsque celle-ci est déjà affectée à une personne.
ms.openlocfilehash: d1af1b5696d359daf6578e090180b79587952106
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42242328"
---
# <a name="remove-licenses-from-your-office-365-for-business-subscription"></a>Supprimer des licences de votre abonnement Office 365 pour les entreprises

[] Vous ne pouvez pas supprimer une licence d'un abonnement si elle est affectée à un utilisateur. Si vous souhaitez supprimer une licence qui est actuellement attribuée à une personne, vous devez [supprimer-licences-de-utilisateurs](../../admin/manage/remove-licenses-from-users.md)avant de pouvoir supprimer la licence de l’abonnement.

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.

## <a name="remove-licenses"></a>Remove licenses

1. Dans le Centre d’administration, choisissez la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Produits et services</a>.

2. Dans la page **produits & services** , recherchez l’abonnement dont vous souhaitez supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone nombre **total de licences** , entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer la modification**. Par exemple, si vous avez 110 licences et que vous voulez en supprimer 5, entrez 105.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">abonnements</a> de **facturation** \> .

2. Sur la page **abonnements** , sélectionnez l’abonnement dont vous souhaitez supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone **Nombre total de licences**, entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer**. Par exemple, si vous avez 110 licences et que vous voulez en supprimer 5, entrez 105.


::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">abonnements</a> de **facturation** \> .

2. Sur la page **abonnements** , sélectionnez l’abonnement dont vous souhaitez supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone **Nombre total de licences**, entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer**. Par exemple, si vous avez 110 licences et que vous voulez en supprimer 5, entrez 105.

::: moniker-end

## <a name="what-if-i-dont-see-the-addremove-licenses-link"></a>Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?

Cette section décrit les raisons pour lesquelles le lien **Ajouter/Supprimer des licences** n'est pas disponible et la marche à suivre en pareil cas.
  
### <a name="a-credit-check-is-pending"></a>Une vérification de la solvabilité est en attente

Si une vérification de solvabilité est en cours, un message mentionnant cette opération s'affiche et vous ne pouvez pas supprimer de licences avant la fin de la vérification de solvabilité. Si c'est le cas, revenez sur cette page plus tard pour voir si la vérification de solvabilité est terminée. Les vérifications de la solvabilité nécessitent en général deux jours ouvrés.
  
Une fois la vérification terminée, le lien **Ajouter/Supprimer des licences** devrait être disponible dans la section **Utilisateurs**. Si c’est le cas, passez à [la suppression des licences de votre abonnement Office 365 pour les entreprises](#remove-licenses-from-your-office-365-for-business-subscription).
  
### <a name="you-activated-the-subscription-using-a-product-key"></a>Vous avez activé l'abonnement à l'aide d'une clé de produit

Si l'abonnement a été acheté et activé à l'aide d'une clé de produit à 25 caractères, le texte « Prépayé » s'affiche. Si votre abonnement a été prépayé à l'aide d'une clé de produit, vous ne pouvez pas supprimer de licences, car vous avez déjà acheté celles-ci. Vous pouvez toutefois supprimer les licences supplémentaires lors du renouvellement de l'abonnement.
  
### <a name="you-bought-your-subscription-through-a-partner"></a>Vous avez acheté votre abonnement auprès d'un partenaire

Si votre abonnement a été acheté auprès d’un fournisseur de services cryptographiques ou d’un partenaire, vous ne pouvez pas supprimer les licences. Contactez votre fournisseur de services de chiffrement ou utilisez le lien Centre de gestion des licences en volume (VLSC) pour contacter votre partenaire.
  
## <a name="what-you-need-to-know-about-removing-licenses-from-users-in-office-365-for-business"></a>Ce que vous devez savoir sur la suppression de licences d'utilisateur dans Office 365 pour les entreprises

- Vous devez être un administrateur général ou un administrateur de gestion des utilisateurs. Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

- Pour ajouter une licence à un compte d'utilisateur existant, procédez comme suit. [Découvrez comment ajouter un compte d'utilisateur et attribuer une licence en même temps](../../admin/add-users/add-users.md).

## <a name="articles-about-managing-licenses-for-your-subscription"></a>Articles sur la gestion des licences pour votre abonnement

- [Comprendre les abonnements et les licences](subscriptions-and-licenses.md)

- [Retirer des licences aux utilisateurs](../../admin/manage/remove-licenses-from-users.md)

- [Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md)

- [Acheter des licences pour votre abonnement](buy-licenses.md)

- [Acheter un autre abonnement](../buy-another-subscription.md)

- [Acheter ou modifier un composant additionnel](../buy-or-edit-an-add-on.md)

- [Gérer les licences utilisateur Yammer](https://docs.microsoft.com/yammer/manage-yammer-users/manage-yammer-licenses-in-office-365)

## <a name="related-links"></a>Liens connexes

[Annuler votre abonnement](../subscriptions/cancel-your-subscription.md)
