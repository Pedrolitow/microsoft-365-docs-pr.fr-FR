---
title: Gérer les demandes de licence
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: micurn, nicholak
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- MACBillingLicensesRequests
- AdminSurgePortfolio
- commerce_licensing
search.appverid: MET150
description: Découvrez comment examiner et approuver ou refuser les demandes de licence des utilisateurs pour votre abonnement Microsoft 365 entreprise.
ms.date: 06/07/2021
ms.openlocfilehash: 3a1290c071fa96be654e645d6f7ca82197ecc4b929f6c6c97d1b2c61625b5ef7
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53815050"
---
# <a name="manage-license-requests"></a>Gérer les demandes de licence

> [!NOTE]
> Les informations de cet article s’appliquent uniquement aux produits achetés en libre-service. Pour en savoir plus, consultez [la faq sur l’achat en libre-service.](../subscriptions/self-service-purchase-faq.yml)

Si vous désactivez les achats en libre-service dans votre organisation, vous pouvez utiliser les demandes de licences pour gérer le processus de demande de licence pour vos utilisateurs. Lorsqu’un utilisateur tente d’effectuer un achat en libre-service pour un produit que vous avez bloqué, il peut soumettre une demande de licence à vous, l’administrateur. Lorsqu’ils font une demande, ils peuvent ajouter les noms d’autres utilisateurs qui ont également besoin de licences pour le produit.

> [!NOTE]
> Si vous bloquez les utilisateurs d’effectuer des achats en libre-service, Microsoft ne leur envoie pas de courriers électroniques marketing. En outre, s’ils utilisent une version d’essai d’un produit, ils ne voient pas d’invite pour l’acheter. Pour plus d’informations, voir [Gérer les achats en libre-service (administrateur).](../subscriptions/manage-self-service-purchases-admins.md)

Pour voir et gérer les demandes de licence, l’administrateur utilise **l’onglet Demandes** dans la page **Licences.** La liste affiche le nom du produit demandé, le nom de la personne qui demande une licence, la date demandée et l’état de la demande. Les administrateurs peuvent filtrer la liste pour afficher les demandes en attente ou terminées. Les demandes sont maintenues pendant 30 jours.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un administrateur global pour effectuer les tâches de cet article. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Utiliser votre propre processus de demande

Si votre organisation possède son propre processus de demande, vous pouvez l’utiliser à la place. Vous créez un message qui s’affiche pour les utilisateurs lorsqu’ils demandent une licence.

> [!IMPORTANT]
> Si vous utilisez votre propre processus de demande, aucune demande n’est affichée sous **l’onglet Demandes.** Les demandes existantes avant l’ajout de votre message continuent d’apparaître jusqu’à ce que vous les approuviez ou les refusez.

1. Dans le Centre d’administration, allez à la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation,</a> puis sélectionnez **l’onglet Demandes.**
2. Sélectionnez **Utiliser votre processus de demande existant à la place.**
3. Dans le volet droit, dans la zone **Message,** tapez le message que les utilisateurs doivent voir lorsqu’ils demandent une licence. Si vous souhaitez également inclure un lien vers la stratégie de votre organisation ou une autre documentation, entrez l’URL dans la zone de texte Lien vers la **documentation (facultatif).**
4. Sélectionnez **Enregistrer**.

Lorsque vous revenir à la liste **demandes,** vous voyez le message Que vous utilisez **votre propre processus** de demande de licence . Pour apporter des modifications au message envoyé aux utilisateurs, sélectionnez Utiliser votre processus **de demande existant à la place.**

## <a name="stop-using-your-own-request-process"></a>Arrêter d’utiliser votre propre processus de demande

1. Dans le Centre d’administration, allez à la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation,</a> puis sélectionnez **l’onglet Demandes.**
2. Sélectionnez **Utiliser votre processus de demande existant à la place.**
3. Dans le volet droit, cochez la case Utiliser le processus de demande de **mon** organisation.
4. Sélectionnez **Enregistrer**.

## <a name="approve-or-deny-a-license-request"></a>Approuver ou refuser une demande de licence

1. Dans le Centre d’administration, allez à la page   >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Licences de facturation,</a> puis sélectionnez **l’onglet Demandes.**
2. Sélectionnez la ligne qui contient la demande à réviser. Le volet droit affiche des détails sur les utilisateurs qui souhaitent obtenir des licences pour le produit.
3. Pour refuser l’intégralité de la demande, sélectionnez **N’approuvez pas** et, dans la boîte de dialogue, sélectionnez Ne **pas approuver.**
4. Pour refuser la demande à certains utilisateurs, mais en approuver d’autres, sélectionnez le X par le nom des utilisateurs que vous souhaitez supprimer. Leurs noms sont déplacés sous **Ne pas affecter à ces utilisateurs.**
5. Si vous avez plusieurs produits, sous Sélectionner un **produit,** sélectionnez celui pour qui vous souhaitez attribuer des licences.
6. Pour refuser l’accès des utilisateurs à certains services et applications, développez Activer ou désactiver les applications et **services,** puis cochez les cases de ceux que vous souhaitez exclure.
7. En bas du volet, tapez un message facultatif dans la zone de texte.
8. Lorsque vous avez terminé, sélectionnez **Approuver.** Le volet droit affiche les détails de la demande.
9. Fermez le volet droit.
    Les utilisateurs reçoivent un courrier électronique qui indique que leur demande a été approuvée ou refusée.

## <a name="related-content"></a>Contenu connexe

[Attribuer des licences aux utilisateurs](../../admin/manage/assign-licenses-to-users.md) (article)\
[Déplacer les utilisateurs vers un autre abonnement](../subscriptions/move-users-different-subscription.md) (article)\
[Acheter ou supprimer des licences d’abonnement](buy-licenses.md) (article)
