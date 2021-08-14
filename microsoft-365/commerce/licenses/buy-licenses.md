---
title: Acheter ou supprimer des licences d’abonnement
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: argani, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_o365
ms.custom:
- okr_SMB
- AdminSurgePortfolio
- manage_licenses
- commerce_licensing
- AdminTemplateSet
search.appverid: MET150
description: Utilisez ces étapes pour acheter davantage de licences ou réduire le nombre de licences pour votre abonnement Microsoft 365 entreprise.
ms.date: 04/07/2021
ms.openlocfilehash: b5d526ef999da8bb173be2ee26f16d131fe532b64eed88c5c16cbfe8b6a4807e
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53820934"
---
# <a name="buy-or-remove-licenses"></a>Acheter ou supprimer des licences d’abonnement

Vous pouvez acheter davantage de licences ou réduire le nombre de licences pour vos abonnements en suivant les étapes ci-après.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être administrateur global ou administrateur de facturation pour effectuer les tâches décrites dans cet article. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
- Vous pouvez [ajouter des utilisateurs et attribuer des licences en même temps.](../../admin/add-users/add-users.md)
- Si vous avez acheté votre offre Microsoft 365 entreprise ou Office 365 Entreprise par le biais d’un partenaire tiers, vous devez acheter des licences supplémentaires par le biais de ce partenaire.

## <a name="watch-buy-new-licenses"></a>Regarder : Acheter de nouvelles licences

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4KWvE]

Si les personnes pour qui vous achetez des licences ne sont pas encore des utilisateurs actifs de votre organisation, la prochaine chose à faire est d’ajouter des utilisateurs et d’attribuer des [licences en même temps.](../../admin/add-users/add-users.md)

## <a name="watch-remove-existing-licenses"></a>Regarder : Supprimer des licences existantes

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4L53r]

Si vous avez supprimé des licences d’un abonnement, la prochaine chose à faire est de supprimer des utilisateurs [de votre organisation.](../../admin/add-users/delete-a-user.md)

## <a name="buy-or-remove-licenses-for-your-business-subscription"></a>Acheter ou supprimer des licences pour votre abonnement commercial

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Vos produits</a>.
::: moniker-end

::: moniker range="o365-germany"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Vos produits</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Vos produits</a>.
::: moniker-end

2. Sous **l’onglet** Produits, recherchez l’abonnement pour lequel vous souhaitez acheter ou supprimer des licences. Sélectionnez les trois points (plus d’actions), puis **sélectionnez Acheter des licences.** [Que se passe-t-il si je ne vois pas les boutons Acheter des licences ou Supprimer des licences ?](#what-if-i-dont-see-the-buy-licenses-or-remove-licenses-buttons)
3. Si vous souhaitez réduire le nombre de licences, en haut du volet Acheter des **licences,** sélectionnez **Supprimer des licences.**
4. Pour acheter ou supprimer  des licences, sous Nouvelle quantité dans la zone Nombre total de **licences,** entrez le nombre total de licences que vous souhaitez pour cet abonnement. Par exemple, si vous avez 100 licences et que vous souhaitez en ajouter cinq, entrez 105. Si vous souhaitez en supprimer cinq, entrez 95.
5. Sélectionnez **Enregistrer**.

> [!NOTE]
> Vous ne pouvez pas réduire le nombre de licences pour votre abonnement si toutes les licences sont actuellement attribuées à des utilisateurs. Pour réduire le nombre de licences, supprimez d’abord une ou plusieurs licences des [utilisateurs,](../../admin/manage/remove-licenses-from-users.md)puis supprimez les licences de l’abonnement.

## <a name="what-if-i-dont-see-the-buy-licenses-or-remove-licenses-buttons"></a>Que se passe-t-il si je ne vois pas les boutons Acheter des licences ou Supprimer des licences ?

Ce tableau décrit les raisons pour lesquelles les boutons Acheter des **licences** ou Supprimer des **licences** ne sont pas disponibles et les solutions possibles.

|Reason  |Description  |Solution  |
|---------|---------|---------|
|Une vérification de solvabilité est en attente. |Si une vérification de solvabilité est en attente, vous ne pouvez pas acheter ou supprimer de licences tant que la vérification de solvabilité n’est pas terminée.  | Vérifiez ultérieurement si la vérification de solvabilité est terminée. Les vérifications de la solvabilité nécessitent en général deux jours ouvrés.<br/>Une fois la vérification de solvabilité terminée, vous devez voir les boutons Acheter **des licences** et **Supprimer des licences.** |
|Vous avez activé l’abonnement à l’aide d’une clé de produit.| Si l’abonnement a été acheté et activé à l’aide d’une clé  de produit de 25 caractères, vous voyez le mot « Prépayé » dans la colonne Canal d’achat de la page Vos **produits.**  |Voir [Ajouter des licences à un abonnement payé pour l’utilisation d’une clé de produit.](add-licenses-using-product-key.md) |
|Vous avez acheté votre abonnement par le biais d’un revendeur.| Vous voyez le mot « Revendeur  » dans la colonne Canal d’achat de la page **Vos produits.** | Si l’abonnement a été acheté via un partenaire fournisseur de solutions Cloud (CSP), contactez votre partenaire CSP pour acheter d’autres licences.        |
|Vous avez un abonnement d’essai. | Pour afficher vos abonnements d’essai, sélectionnez le bouton filtre, puis choisissez **Version d’essai.** | Tout d’abord, achetez votre abonnement d’essai, puis vous pouvez acheter d’autres licences.|

## <a name="when-will-the-new-licenses-be-available-to-assign"></a>Quand les nouvelles licences pourront-elles être assignées ?

Le mode de paiement associé à votre abonnement ou profil de facturation est facturé dès que vous achetez plus de licences pour un abonnement. Les licences sont immédiatement disponibles pour que vous les affectiez aux utilisateurs.

Si vous avez prépayé votre abonnement avec une clé de produit, vous pouvez ajouter d’autres licences à l’aide d’une autre clé de produit, ou en ajoutant une carte de crédit ou de débit, ou un compte bancaire pour couvrir le coût supplémentaire des nouvelles licences. Si votre abonnement est prépayé, vous ne pouvez pas supprimer de licences.

## <a name="how-does-buying-or-removing-licenses-affect-my-billing-statements"></a>Comment l’achat ou la suppression de licences affecte-t-il mes relevés de facturation ?

- Les licences ajoutées au milieu de votre période de facturation apparaissent sur votre prochaine facture. Si vous payez annuellement, vous êtes facturé dans un mois pour ces modifications.
- Sur votre relevé de facturation suivant, les frais précédents pour le nombre de licences d’origine sont déduits. Nous ajoutons un frais au prorat pour la période avec le nombre de licences d’origine et un frais pour le nouveau nombre de licences. Il existe également un frais pour le nombre de licences actuel pour le restant de votre période de facturation.

## <a name="next-steps"></a>Prochaines étapes

Si vous avez acheté plus de licences pour votre abonnement, vous devez ensuite attribuer ces licences aux [utilisateurs de votre organisation.](../../admin/manage/assign-licenses-to-users.md)

Si vous avez réduit le nombre de licences pour votre abonnement parce qu’une personne a quitté votre organisation, vous pouvez supprimer le compte de cet utilisateur. Pour en savoir plus, [consultez Supprimer un ancien employé.](../../admin/add-users/remove-former-employee.md)

## <a name="related-content"></a>Contenu connexe

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Comprendre les abonnements et les licences](subscriptions-and-licenses.md) (article)\
[Essayer ou acheter un abonnement Microsoft 365 abonnement](../try-or-buy-microsoft-365.md) (article)
