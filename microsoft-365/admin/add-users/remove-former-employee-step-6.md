---
title: 'Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé'
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
ms.openlocfilehash: 95f95403a316e176f91c7f120ce5a26487a7a59f
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436226"
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

Pour plus d’informations sur la gestion des licences utilisateur pour Microsoft 365 pour les entreprises, consultez [Affecter des licences aux utilisateurs dans Microsoft 365 pour les entreprises](../manage/assign-licenses-to-users.md) et [annuler l’attribution de licences aux utilisateurs dans Microsoft 365 pour les entreprises](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Comment le compte supprimé d'un employé affecte Skype Entreprise

Lorsque vous supprimez une licence d'utilisateur d'Office 365, le numéro d'appel PSTN associé à l'utilisateur est libéré. Vous pouvez l'assigner à un autre utilisateur.
  
Si l'utilisateur appartient à un groupe de files d'attente, il ne sera plus une cible viable des agents de la file d'attente d'appels. Nous recommandons donc de supprimer également l'utilisateur des groupes associés à la file d'attente d'appels.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Configurer le transfert d’appel aux personnes de votre organisation

Si vous devez configurer le transfert d’appel pour le numéro de téléphone de l’employé arrêté, le paramètre de transfert d’appel sous stratégies d’appel peut configurer le transfert où les appels entrants peuvent être transférés à d’autres utilisateurs ou faire sonner une autre personne en même temps. Pour plus d’informations, consultez [Stratégies d’appel dans Microsoft Teams](/microsoftteams/teams-calling-policy).
