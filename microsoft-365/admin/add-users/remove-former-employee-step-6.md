---
title: 'Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Vous pouvez supprimer la licence Microsoft 365 d’un ancien employé, puis la supprimer de votre abonnement ou attribuer la licence à un autre utilisateur.
ms.openlocfilehash: 8d1c903a9f829605b15887b2b67e7ea61962cbfe
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68186104"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé

Si vous ne souhaitez pas payer une licence après le départ d’une personne de votre organisation, vous devez supprimer sa licence Microsoft 365, puis la supprimer de votre abonnement. Vous pouvez attribuer une licence à un autre utilisateur si vous ne la supprimez pas.

Si la boîte aux lettres doit être accessible par des personnes autorisées qui ont reçu des autorisations eDiscovery pour des raisons légales ou de conformité, une licence plan 2 Exchange Online (ou une licence plan 1 Exchange Online avec une Archivage Exchange Online  licence de module complémentaire) afin qu’une conservation puisse être appliquée à la boîte aux lettres avant sa suppression. Une fois le compte d’utilisateur supprimé, toute licence Exchange Online associée au compte d’utilisateur sera disponible pour être attribuée à un nouvel utilisateur.
  
Lorsque vous effectuez cette opération, toutes les données de cet utilisateur sont conservées pendant 30 jours. Vous pouvez [accéder](get-access-to-and-back-up-a-former-user-s-data.md) aux données, ou [restaurer](restore-user.md) le compte si l'utilisateur revient. Après 30 jours, toutes les données de l’utilisateur (à l’exception des documents stockés sur SharePoint Online) sont définitivement supprimées de Microsoft 365 et ne peuvent pas être récupérées.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé à bloquer, puis sélectionnez l’onglet **Licences et applications** .
3. Désactivez les cases à cocher des licences à supprimer, puis **sélectionnez Enregistrer les modifications**.

**Pour réduire le nombre de licences que vous payez jusqu’à** ce que vous engagez une autre personne, procédez comme suit :

1. Dans le Centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">de vos produits</a> , puis sélectionnez l’onglet **Produits** .
2. Sélectionnez l’abonnement à partir duquel vous souhaitez supprimer des licences.
3. Dans la page de détails, **sélectionnez Supprimer les licences**.
4. Dans le volet **Supprimer les licences** , sous Nouvelle quantité, dans la zone **Total des licences** , entrez le nombre total de licences souhaitées pour cet abonnement. Par exemple, si vous avez 25 licences et que vous souhaitez en supprimer une, entrez 24.
5. Sélectionnez **Enregistrer**.

Lorsque vous [ajoutez une autre personne](add-users.md) à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape !

Pour plus d’informations sur la gestion des licences utilisateur pour Microsoft 365 pour les entreprises, consultez [Affecter des licences aux utilisateurs de Microsoft 365 pour les entreprises](../manage/assign-licenses-to-users.md) et [annuler l’attribution de licences à des utilisateurs dans Microsoft 365 pour les entreprises](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Comment le compte supprimé d'un employé affecte Skype Entreprise

When you remove a user's license from Office 365, the PSTN calling number associated with the user will be released. You can assign it to another user.
  
If the user belongs to a queue group, they will no longer be a viable target of the call queue agents. So, we recommend also removing the user from the groups associated with the call queue.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Configurer le transfert d’appel aux personnes de votre organisation

Si vous devez configurer le transfert d’appel pour le numéro de téléphone de l’employé arrêté, le paramètre de transfert d’appel sous stratégies d’appel peut configurer le transfert où les appels entrants peuvent être transférés à d’autres utilisateurs ou faire sonner une autre personne en même temps. Pour plus d’informations, consultez [Stratégies d’appel dans Microsoft Teams](/microsoftteams/teams-calling-policy).
