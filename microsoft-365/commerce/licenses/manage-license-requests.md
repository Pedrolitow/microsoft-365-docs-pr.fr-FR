---
title: Gérer les demandes de licence
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- commerce
ms.custom: MACBillingLicensesRequests
search.appverid:
- MET150
description: Découvrez comment passer en revue et approuver ou refuser les demandes de licence des utilisateurs pour votre abonnement Microsoft 365 pour les entreprises.
ms.date: 08/07/2020
ms.openlocfilehash: cbcdc5550d404278832cc702560ac55f6ace8a44
ms.sourcegitcommit: 9550298946f8accb90cd59be7b46b71d4bf4f8cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "46597653"
---
# <a name="manage-license-requests"></a>Gérer les demandes de licence

> [!NOTE]
> Les informations contenues dans cet article s’appliquent uniquement aux produits achetés en libre-service. Pour en savoir plus, consultez la rubrique [Forum aux questions sur les achats en libre-service](../subscriptions/self-service-purchase-faq.md).

Si vous désactivez les achats en libre-service dans votre organisation, vous pouvez utiliser des demandes de licences pour gérer le processus de demande de licence pour vos utilisateurs. Lorsqu’un utilisateur tente d’effectuer un achat en libre-service pour un produit que vous avez bloqué, il peut soumettre une demande de licence pour vous, l’administrateur. Lorsqu’ils effectuent une demande, ils peuvent ajouter les noms d’autres utilisateurs qui ont également besoin de licences pour le produit.

> [!NOTE]
> Si vous empêchez les utilisateurs de procéder à des achats en libre-service, Microsoft ne les envoie pas. En outre, s’ils utilisent une version d’évaluation d’un produit, ils ne sont pas invités à les acheter. Pour plus d’informations, consultez la rubrique [Manage self-service purchases (admin)](../subscriptions/manage-self-service-purchases-admins.md).

Pour afficher et gérer les demandes de licence, l’administrateur utilise l’onglet **requêtes** de la page de gestion des **licences** . La liste indique le nom du produit demandé, le nom de la personne qui demande une licence, la date de la demande et l’état de la demande. Les administrateurs peuvent filtrer la liste pour afficher les demandes en attente ou terminées. Les demandes sont conservées pendant 30 jours.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur général pour effectuer les tâches décrites dans cet article. Si vous souhaitez en savoir plus, veuillez consulter la page [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Utiliser votre propre processus de requête

Si votre organisation a son propre processus de demande, vous pouvez l’utiliser à la place. Vous créez un message qui s’affiche lorsque les utilisateurs demandent une licence.

> [!IMPORTANT]
> Si vous utilisez votre propre processus de requête, aucune demande n’est affichée sous l’onglet **requêtes** . les demandes existantes avant l’ajout de votre message continuent de s’afficher jusqu’à ce que vous les approuviez ou les refusiez.

1. Dans le centre d’administration, accédez à la page licences de **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licenses</a> , puis sélectionnez l’onglet **requêtes** .
2. Sélectionnez **utiliser votre processus de demande existant à la place**.
3. Dans le volet droit, dans la zone de **message** , tapez le message que vous souhaitez que les utilisateurs voient lorsqu’ils demandent une licence. Si vous souhaitez également inclure un lien vers la stratégie de votre organisation ou une autre documentation, entrez l’URL dans la zone de texte **lien vers la documentation (facultatif)** .
4. Cliquez sur **Enregistrer**.

Lorsque vous revenez à la liste **demandes** , vous voyez le message **que vous utilisez votre propre processus de demande de licence**. Pour modifier le message qui est envoyé aux utilisateurs, sélectionnez utiliser à la **place votre processus de requête existant**.

## <a name="stop-using-your-own-request-process"></a>Arrêter d’utiliser votre propre processus de requête

1. Dans le centre d’administration, accédez à la page licences de **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licenses</a> , puis sélectionnez l’onglet **requêtes** .
2. Sélectionnez **utiliser votre processus de demande existant à la place**.
3. Dans le volet droit, désactivez la case à cocher **utiliser le processus de demande de mon organisation** .
4. Cliquez sur **Enregistrer**.

## <a name="approve-or-deny-a-license-request"></a>Approuver ou refuser une demande de licence

1. Dans le centre d’administration, accédez à la page licences de **facturation**  >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licenses</a> , puis sélectionnez l’onglet **requêtes** .
2. Sélectionnez la ligne contenant la demande que vous souhaitez examiner. Le volet droit affiche des détails sur les utilisateurs qui souhaitent des licences sur le produit.
3. Pour refuser la demande entière, sélectionnez **ne pas approuver**, puis dans la boîte de dialogue, sélectionnez **ne pas approuver**.
4. Pour refuser certains utilisateurs à la demande, mais en approuver d’autres, sélectionnez le X en regard du nom des utilisateurs que vous souhaitez supprimer. Leurs noms sont déplacés sous **ne pas affecter à ces utilisateurs**.
5. Si vous avez plusieurs produits, sous **Sélectionner un produit**, sélectionnez celui que vous voulez utiliser pour attribuer des licences.
6. Pour refuser aux utilisateurs l’accès à certaines applications et certains services, développez **activer ou désactiver les applications et les services**, puis désactivez les cases à cocher pour ceux que vous souhaitez exclure.
7. En bas du volet, tapez un message facultatif dans la zone de texte.
8. Lorsque vous avez terminé, sélectionnez **approuver**. Le volet droit affiche les détails de la demande.
9. Fermez le volet droit.
    Les utilisateurs reçoivent un message électronique indiquant que leur demande a été approuvée ou refusée.

## <a name="related-content"></a>Contenu connexe

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article) \
[Déplacer des utilisateurs vers un autre abonnement](../subscriptions/move-users-different-subscription.md) (article) \
[Acheter ou supprimer des licences d’abonnement](buy-licenses.md) (article)