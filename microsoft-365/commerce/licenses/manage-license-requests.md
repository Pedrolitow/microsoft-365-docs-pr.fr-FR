---
title: Gérer les demandes de licence
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- MACBillingLicensesRequests
- AdminSurgePortfolio
search.appverid: MET150
description: Découvrez comment examiner et approuver ou refuser des demandes de licence d’utilisateurs pour votre abonnement Microsoft 365 entreprise.
ms.date: 06/07/2021
ms.openlocfilehash: cc1d03717cbdf0ce8768c630044990363feded8a
ms.sourcegitcommit: e13c8fc28c68422308c9d356109797cfcf6f77be
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64841791"
---
# <a name="manage-license-requests"></a>Gérer les demandes de licence

> [!NOTE]
> Les informations contenues dans cet article s’appliquent uniquement aux produits achetés en libre-service. Pour en savoir plus, consultez la [FAQ sur l’achat en libre-service](../subscriptions/self-service-purchase-faq.yml).

Si vous désactivez les achats en libre-service dans votre organisation, vous pouvez utiliser les demandes de licences pour gérer le processus de demande de licence pour vos utilisateurs. Lorsqu’un utilisateur tente d’effectuer un achat en libre-service pour un produit que vous avez bloqué, il peut envoyer une demande de licence à vous, l’administrateur. Lorsqu’ils effectuent une demande, ils peuvent ajouter les noms d’autres utilisateurs qui ont également besoin de licences pour le produit.

> [!NOTE]
> Si vous empêchez les utilisateurs d’effectuer des achats en libre-service, Microsoft ne leur envoie pas d’e-mails marketing. En outre, s’ils utilisent une version d’évaluation d’un produit, ils ne voient pas d’invites pour l’acheter. Pour plus d’informations, consultez [Gérer les achats en libre-service (Administrateur).](../subscriptions/manage-self-service-purchases-admins.md)

Pour afficher et gérer les demandes de licence, l’administrateur utilise l’onglet **Demandes** de la page **Licences** . La liste affiche le nom du produit demandé, le nom de la personne qui demande une licence, la date demandée et l’état de la demande. Les administrateurs peuvent filtrer la liste pour afficher les demandes en attente ou terminées. Les demandes sont conservées pendant 30 jours.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être administrateur général pour effectuer les tâches décrites dans cet article. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Utiliser votre propre processus de demande

Si votre organisation a son propre processus de demande, vous pouvez l’utiliser à la place. Vous créez un message qui s’affiche aux utilisateurs lorsqu’ils demandent une licence.

> [!IMPORTANT]
> Si vous utilisez votre propre processus de demande, aucune demande n’est affichée sous l’onglet **Demandes** . Les demandes existantes avant d’ajouter votre message continuent d’apparaître jusqu’à ce que vous les approuviez ou les refusiez.

1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , puis sélectionnez l’onglet **Demandes**.
2. Sélectionnez **à la place Utiliser votre processus de demande existant**.
3. Dans le volet droit, dans la zone **Message** , tapez le message que les utilisateurs doivent voir lorsqu’ils demandent une licence. Si vous souhaitez également inclure un lien vers votre stratégie d’organisation ou toute autre documentation, entrez l’URL dans la zone de texte **Lien vers la documentation (facultatif** ).
4. Sélectionnez **Enregistrer**.

Lorsque vous revenez à la liste **des demandes** , vous voyez le message **Que vous utilisez votre propre processus de demande de licence**. Pour apporter des modifications au message envoyé aux utilisateurs, sélectionnez **Utiliser votre processus de demande existant à la place**.

## <a name="stop-using-your-own-request-process"></a>Arrêter d’utiliser votre propre processus de demande

1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , puis sélectionnez l’onglet **Demandes**.
2. Sélectionnez **à la place Utiliser votre processus de demande existant**.
3. Dans le volet droit, désactivez la case à cocher **Utiliser le processus de demande de mon organisation** .
4. Sélectionnez **Enregistrer**.

## <a name="approve-or-deny-a-license-request"></a>Approuver ou refuser une demande de licence

1. Dans le Centre d’administration, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > , puis sélectionnez l’onglet **Demandes**.
2. Sélectionnez la ligne qui contient la demande que vous souhaitez examiner. Le volet droit affiche des détails sur les utilisateurs qui souhaitent obtenir des licences pour le produit.
3. Pour refuser l’intégralité de la demande, sélectionnez **Ne pas approuver**, puis, dans la boîte de dialogue, **sélectionnez Ne pas approuver**.
4. Pour refuser certains utilisateurs pour la demande, mais approuver d’autres utilisateurs, sélectionnez le X par le nom des utilisateurs que vous souhaitez supprimer. Leurs noms sont déplacés sous **Ne pas affecter à ces utilisateurs**.
5. Si vous avez plusieurs produits, sous **Sélectionner un produit**, sélectionnez celui pour lequel vous souhaitez attribuer des licences.
6. Pour refuser aux utilisateurs l’accès à certaines applications et services, **développez Activer ou désactiver les applications et services**, puis désactivez les cases à cocher pour celles que vous souhaitez exclure.
7. En bas du volet, tapez un message facultatif dans la zone de texte.
8. Lorsque vous avez terminé, **sélectionnez Approuver**. Le volet droit affiche les détails de la demande.
9. Fermez le volet droit.
    Les utilisateurs reçoivent un e-mail indiquant que leur demande a été approuvée ou refusée.

## <a name="related-content"></a>Contenu associé

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Déplacer des utilisateurs vers un autre abonnement](../subscriptions/move-users-different-subscription.md) (article)\
[Acheter ou supprimer des licences d’abonnement](buy-licenses.md) (article)
