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
description: Suivez ces étapes pour supprimer la licence Microsoft 365 d’un ancien employé.
ms.openlocfilehash: b724e8d65c990396ad376544de86d4ffd0cb5fdc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315160"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Étape 6 : Supprimer et supprimer la licence Microsoft 365 d’un ancien employé

Si vous ne souhaitez pas payer pour une licence après qu’une personne a quitté votre organisation, vous devez supprimer sa licence Microsoft 365, puis la supprimer de votre abonnement. Vous pouvez attribuer une licence à un autre utilisateur si vous ne la supprimez pas.

Si la boîte aux lettres doit être accessible par des personnes autorisées qui ont obtenu des autorisations eDiscovery pour des raisons de conformité ou de droit, une licence Exchange Online Plan 2 doit lui être attribuée (ou une licence Exchange Online Plan 1 avec une Archivage Exchange Online  licence de modules), de sorte qu’une boîte aux lettres puisse être en attente avant sa suppression. Une fois le compte d’utilisateur supprimé, toute licence Exchange Online associée au compte d’utilisateur peut être assignée à un nouvel utilisateur.
  
Lorsque vous effectuez cette opération, toutes les données de cet utilisateur sont conservées pendant 30 jours. Vous pouvez [accéder](get-access-to-and-back-up-a-former-user-s-data.md) aux données, ou [restaurer](restore-user.md) le compte si l'utilisateur revient. Après 30 jours, toutes les données de l’utilisateur (à l’exception des documents stockés sur SharePoint Online) sont définitivement supprimées de Microsoft 365 et ne peuvent pas être récupérées.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sélectionnez l’onglet **Licences et** applications.
3. Cochez les cases des licences que vous souhaitez supprimer, puis sélectionnez **Enregistrer les modifications**.

**Pour réduire le nombre de licences que vous payez jusqu’à** ce que vous recrutiez une autre personne, vous devez suivre les étapes suivantes :

1. Dans le Centre d’administration, allez **sur la** \> page <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Facturation de vos produits</a> , puis sélectionnez **l’onglet Produits** .
2. Sélectionnez l’abonnement dont vous souhaitez supprimer des licences.
3. Dans la page de détails, **sélectionnez Supprimer des licences**.
4. Dans le **volet Supprimer des licences** , sous Nouvelle quantité, dans la zone Nombre total de **licences** , entrez le nombre total de licences que vous souhaitez pour cet abonnement. Par exemple, si vous avez 25 licences et que vous souhaitez en supprimer une, entrez 24.
5. Sélectionnez **Enregistrer**.

Lorsque vous [ajoutez une autre](add-users.md) personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape !

Pour plus d’informations sur la gestion des licences utilisateur pour Microsoft 365 pour les entreprises, voir Attribuer des [licences à des utilisateurs dans Microsoft 365](../manage/assign-licenses-to-users.md) entreprise et Désattribuer des [licences à des utilisateurs dans Microsoft 365](../manage/remove-licenses-from-users.md) entreprise.
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Comment le compte supprimé d'un employé affecte Skype Entreprise

Lorsque vous supprimez une licence d'utilisateur d'Office 365, le numéro d'appel PSTN associé à l'utilisateur est libéré. Vous pouvez l'assigner à un autre utilisateur.
  
Si l'utilisateur appartient à un groupe de files d'attente, il ne sera plus une cible viable des agents de la file d'attente d'appels. Nous recommandons donc de supprimer également l'utilisateur des groupes associés à la file d'attente d'appels.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Configurer le forwarding d’appel vers des personnes de votre organisation

Si vous devez configurer le transfert d’appel pour le numéro de téléphone de l’employé licencié, le paramètre de transfert d’appel sous stratégies d’appel peut configurer le transfert dans lequel les appels entrants peuvent être transmis à d’autres utilisateurs ou sonner en même temps. Pour plus d’informations, voir [Stratégies d’appel Microsoft Teams](/microsoftteams/teams-calling-policy).
