---
title: Gérer les licences d’abonnement
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
ms.custom:
- SaRA
- okr_SMB
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 36081d8d-b3fa-4948-8c34-e217bba825e1
description: Découvrez comment ajouter et supprimer des licences pour votre abonnement Microsoft 365 pour les entreprises.
ms.openlocfilehash: 57768a7e93b19c14c5428508268c2c1e37d700f6
ms.sourcegitcommit: eb3c7f473e8fe62624f52c9bb38dcd6a96fa58a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44045223"
---
# <a name="manage-subscription-licenses"></a>Gérer les licences d’abonnement

Vous pouvez ajouter ou supprimer des licences de vos abonnements à l’aide de la procédure suivante.

[] Vous ne pouvez pas supprimer une licence d'un abonnement si elle est affectée à un utilisateur. Si vous souhaitez supprimer une licence actuellement attribuée à un utilisateur, vous devez [Supprimer les licences des utilisateurs](../../admin/manage/remove-licenses-from-users.md) avant de pouvoir supprimer la licence de l’abonnement.

## <a name="add-or-remove-licenses-for-your-business-subscription"></a>Ajouter ou supprimer des licences pour votre abonnement professionnel

::: moniker range="o365-worldwide"

1. Dans le centre d’administration, accédez à la page **facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> .

2. Sur la page **vos produits** , recherchez l’abonnement auquel vous voulez ajouter ou supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone nombre **total de licences** , entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer la modification**. Par exemple, si vous avez 100 licences et que vous devez en ajouter 5, entrez 105. Si vous souhaitez en supprimer 5, entrez 95.

Une fois que vous avez acheté de nouvelles licences, veillez à [attribuer les licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md).

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.

2. Sur la page **abonnements** , sélectionnez l’abonnement auquel vous voulez ajouter ou supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone nombre **total de licences** , entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer** \> **.** Par exemple, si vous avez 100 licences et que vous devez en ajouter 5, entrez 105. Si vous souhaitez en supprimer 5, entrez 95.

Une fois que vous avez acheté de nouvelles licences, veillez à [attribuer les licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md).

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.

2. Sur la page **abonnements** , sélectionnez l’abonnement auquel vous voulez ajouter ou supprimer des licences, puis sélectionnez **Ajouter/supprimer des licences**.

    [Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?](#what-if-i-dont-see-the-addremove-licenses-link)

3. Dans la zone nombre **total de licences** , entrez le nombre total de licences dont vous avez besoin pour cet abonnement, puis sélectionnez **Envoyer** \> **.** Par exemple, si vous avez 100 licences et que vous devez en ajouter 5, entrez 105. Si vous souhaitez en supprimer 5, entrez 95.

Une fois que vous avez acheté de nouvelles licences, veillez à [attribuer les licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md).

::: moniker-end

## <a name="what-if-i-dont-see-the-addremove-licenses-link"></a>Que faire si le lien Ajouter/Supprimer des licences n'est pas disponible ?

Ce tableau décrit les raisons pour lesquelles le lien **Ajouter/supprimer des licences** n’est peut-être pas disponible, et ce que vous pouvez faire. 

|Reason  |Description  |Solution  |
|---------|---------|---------|
|Une vérification de solvabilité est en attente. |Si une vérification de solvabilité est en cours, un message mentionnant cette opération s'affiche et vous ne pouvez pas acheter de licence avant la fin de la vérification de solvabilité.  | Vérifiez plus tard pour voir si la vérification du crédit est terminée. Les vérifications de la solvabilité nécessitent en général deux jours ouvrés.<br>Une fois la vérification terminée, le lien **Ajouter/Supprimer des licences** devrait être disponible dans la section **Utilisateurs**. Si c’est le cas, accédez à [gérer les licences d’abonnement](#manage-subscription-licenses). |
|Vous avez activé l’abonnement à l’aide d’une clé de produit.| Si l'abonnement a été acheté et activé à l'aide d'une clé de produit à 25 caractères, le texte « Prépayé » s'affiche.  |Voir [Ajouter des licences à un abonnement payé pour l’utilisation d’une clé de produit](add-licenses-using-product-key.md). |
|Vous avez acheté votre abonnement auprès d’un partenaire. | Si l'abonnement a été acheté auprès d'un partenaire, le lien Centre de gestion des licences en volume s'affiche. | Voir [Ajouter des licences à un abonnement acheté via le centre de gestion des licences en volume](add-licenses-bought-through-vlsc.md). |
|Vous avez acheté votre abonnement auprès d’un revendeur.|| Si l'abonnement a été acheté auprès d'un Fournisseur de solutions Microsoft Cloud, vous devez le contacter pour acheter davantage de licences.        |
|Vous disposez d’un abonnement d’évaluation. |Une version d’évaluation de Microsoft 365 affiche le texte « version d’évaluation ». | Vous devez d’abord acheter votre abonnement d’évaluation, puis ajouter des licences supplémentaires. Consultez [la rubrique acheter un abonnement à Microsoft 365 pour les entreprises à partir de votre version d’évaluation gratuite](../buy-a-subscription-from-your-free-trial.md).|

## <a name="what-you-need-to-know-about-buying-licenses-for-your-business-subscription"></a>Ce que vous devez savoir sur l’achat de licences pour votre abonnement professionnel

### <a name="buying-licenses"></a>Achat de licences

- Vous devez être un administrateur général ou un administrateur de facturation pour acheter des licences. Pour plus d’informations, consultez la rubrique [à propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
- Pour acheter une licence et ajouter un nouvel utilisateur à votre abonnement en même temps, reportez-vous à la rubrique [Ajouter des utilisateurs individuellement ou en bloc Microsoft 365-aide de l’administrateur](../../admin/add-users/add-users.md).

### <a name="license-availability"></a>Disponibilité des licences

- Si vous réglez le montant de votre abonnement par carte de crédit ou par compte bancaire, les nouvelles licences que vous achetez sont disponibles dès que vous recevez une confirmation de commande. Si vous payez par facture, il est possible que vous deviez attendre la vérification de votre solvabilité avant que les nouvelles licences ne soient disponibles et utilisables.

  > [!NOTE]
  > Le règlement par compte bancaire n’est pas disponible dans certains pays ou régions.

- Si vous avez prépayé votre abonnement avec une clé de produit, vous pouvez ajouter des licences supplémentaires en ajoutant une carte bancaire ou un compte bancaire pour traiter les frais supplémentaires des nouvelles licences. Une fois que vous avez acheté les nouvelles licences, nous ajoutons un deuxième abonnement avec le nombre de nouvelles licences que vous venez d'ajouter. Par exemple, si vous avez un abonnement prépayé avec 5 licences et que vous avez acheté 10 licences supplémentaires, vous verrez deux abonnements répertoriés : un avec cinq licences prépayées et l'autre avec les 10 nouvelles licences.

### <a name="billing-statements"></a>Relevés de facturation

- Si vous payez par carte bancaire ou compte bancaire, les frais d'achat de nouvelles licences apparaîtront sur votre moyen de paiement dans deux jours.
- Si vous payez par facture, le prix d'achat de nouvelles licences apparaîtra sur votre relevé de facturation suivant.
- Si vous achetez de nouvelles licences au milieu de votre période de facturation, votre premier relevé de facturation est susceptible de comprendre une fraction des frais. Le solde sera repris sur votre relevé de facturation suivant.

## <a name="related-articles"></a>Articles connexes

[Comprendre les abonnements et les licences](subscriptions-and-licenses.md)

[Acheter des licences pour votre abonnement](buy-licenses.md)

[Acheter un autre abonnement](../buy-another-subscription.md)

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md)

[Gérer les licences utilisateur Yammer](https://docs.microsoft.com/yammer/manage-yammer-users/manage-yammer-licenses-in-office-365)
