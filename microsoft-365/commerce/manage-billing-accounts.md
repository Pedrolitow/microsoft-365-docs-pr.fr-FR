---
title: Gérer les comptes de facturation
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
- commerce
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
description: Découvrez les comptes de facturation et comment les gérer.
ms.openlocfilehash: 87cc861ab48b99106a3cbd50d8ded91205ffb0a2
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44402605"
---
# <a name="manage-billing-accounts"></a>Gérer les comptes de facturation

Un compte de facturation est créé lorsque vous vous inscrivez pour essayer ou acheter des produits Microsoft. Votre compte de facturation vous permet de gérer les paramètres de votre compte, les factures, les modes de paiement et les achats. Vous pouvez accéder à plusieurs comptes de facturation. Par exemple, vous avez souscrit Microsoft 365 directement ou vous avez accès à l’accord entreprise de votre organisation, à l’accord de services de & de produits Microsoft ou à l’accord client Microsoft. Pour chacun de ces scénarios, vous devez disposer d’un compte de facturation distinct.

Le centre d’administration Microsoft 365 prend actuellement en charge le type de compte de facturation suivant :

- Programme Microsoft Online Services : ce compte de facturation est créé lorsque vous vous inscrivez directement à un abonnement Microsoft 365.
- Programme Microsoft Products & Services Agreement (MPSA) : ce compte de facturation est créé lorsque votre organisation signe un contrat de licence en volume MPSA pour acheter des services logiciels et en ligne.
- Accord client Microsoft : ce compte de facturation est créé lorsque votre organisation travaille avec un représentant Microsoft, un partenaire autorisé ou s’il achète indépendamment.

La page <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">comptes de facturation</a> fournit une vue de vos comptes commerciaux auprès de Microsoft. Par défaut, votre organisation a au moins un compte de facturation associé à un contrat qui est accepté au moment de l’achat direct ou via un accord de licence en volume.

## <a name="understand-billing-account-details"></a>Comprendre les détails des comptes de facturation

Le haut de la page de détails des **comptes de facturation** est votre profil de compte et contient des informations légales et fiscales sur votre organisation. Vous pouvez mettre à jour votre profil pour modifier votre adresse légale et votre numéro de téléphone. Ce compte est l’entité juridique qui paie les produits que vous achetez.

Le tableau suivant répertorie les termes importants que vous voyez sur la page de détails des **comptes de facturation** .

| Nom du champ | Description |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Adresse de vente | Entité juridique chargée du paiement et identifiée sur la facture. L’adresse fournie ici est utilisée pour déterminer votre taux de t.v.a. à moins que vous n’ayez choisi de fournir une adresse de livraison alternative pendant votre achat. Pour plus d’informations, consultez la rubrique [Tax information](billing-and-payments/tax-information.md). |
| Segment | Champ en lecture seule qui identifie le segment commercial de votre organisation (commercial, éducation, gouvernement ou non lucratif). |
| État du compte | Champ en lecture seule qui spécifie l’état de votre compte commercial auprès de Microsoft. |
| ID de taxe | Si vous n’êtes pas aux États-Unis, vous devez fournir une T.V.A. ou une équivalence locale. Pour plus d’informations, consultez la rubrique [Tax information](billing-and-payments/tax-information.md). |
| Contrat | Lorsqu’un compte de facturation est créé, par le biais d’un achat direct ou d’un contrat de licence en volume, un signataire de l’Organisation accepte, ou signe, un accord qui décrit les termes & conditions du compte. Le cas échéant, cet affichage répertorie un historique des accords. Si vous devez accepter les termes mis à jour, un lien pour **approuver un accord** s’affiche. |
| Profils de facturation | Un profil de facturation définit les propriétés de votre facture, comme le destinataire de la facture, le mode de remise de la facture, les conditions de paiement et un numéro de bon de commande. Pour répartir la facturation au sein de votre organisation, vous pouvez créer plusieurs profils de facturation et identifier le profil de facturation approprié au moment de l’achat. Pour plus d’informations sur les profils de facturation et sur la façon dont vous pouvez les utiliser pour créer des options de facturation plus flexibles pour votre organisation, [Gérez les profils de facturation](billing-and-payments/manage-billing-profiles.md). |

> [!NOTE]
> Si vous souhaitez modifier le nom ou l’adresse du **vendu** , mais ne voyez pas de lien de **modification** , vous devez  [contacter le support technique](https://docs.microsoft.com/office365/admin/contact-support-for-business-products) pour le modifier. Les demandes d’un changement de nom **vendu** nécessitent une vérification de solvabilité. Lorsque vous contactez le support technique, préparez l’un des documents suivants :
>
> - Document d’annonce externe qui indique toute modification apportée au nom de la société ou à la structure de l’entreprise
> - Document ou lettre d’inscription du gouvernement
> - Imprimer à partir du registre de l’entreprise locale
>
> La prise en charge peut vous aider avec les changements de nom et d’adresse où seul le nom du client change, mais l’entité reste la même. La documentation fournie doit indiquer clairement que seul le nom de l’entité a été modifié. Si la modification est liée à une transaction, comme une vente commerciale, ou une cession ou un « Spinoff » d’un affilié client, veuillez contacter votre vendeur Microsoft.

## <a name="shipping-addresses"></a>Adresses d’expédition

Cette section répertorie les adresses de livraison associées à votre compte de facturation. Lorsque vous effectuez un achat, vous pouvez utiliser cette adresse pour identifier l’endroit où votre achat est livré ou utilisé. L’adresse d’expédition est modifiable. Vous pouvez ajouter une adresse d’expédition ou mettre à jour l’adresse existante. Cette adresse est utilisée pour déterminer le taux de taxe pour votre achat.

## <a name="understand-access-to-billing-accounts"></a>Comprendre l’accès aux comptes de facturation

Vous pouvez fournir aux autres utilisateurs l’accès au compte de facturation dans le centre d’administration 365 de Microsoft via les rôles et les autorisations. Seul le propriétaire d’un compte de facturation peut accorder l’accès à un compte de facturation. Vous pouvez attribuer l’un des rôles suivants aux utilisateurs :

- Propriétaire du compte de **facturation** &mdash; Peut attribuer des autorisations, modifier des comptes, signer des contrats et afficher des comptes.
- Collaborateur de compte de **facturation** &mdash; Peut modifier des comptes, signer des contrats et afficher des comptes.
- Lecteur de compte de **facturation** &mdash; Peut afficher les comptes.

> [!Note]
> Les rôles de compte de facturation s’appliquent uniquement aux comptes de facturation, et ne s’appliquent pas aux autres scénarios du centre d’administration 365 de Microsoft.

## <a name="related-articles"></a>Articles connexes

[Informations fiscales](billing-and-payments/tax-information.md)

[Gérer les profils de facturation](billing-and-payments/manage-billing-profiles.md)