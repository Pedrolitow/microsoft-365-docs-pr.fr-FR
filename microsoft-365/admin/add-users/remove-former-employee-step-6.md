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
localization_priority: Normal
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
search.appverid:
- BCS160
- MET150
- MOE150
description: Suivez ces étapes pour supprimer la licence Microsoft 365 d’un ancien employé.
ms.openlocfilehash: ed86eb28cc6d4996f7def8cb567f0e4085e67624
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52244179"
---
# <a name="step-6---remove-the-microsoft-365-license-from-a-former-employee"></a>Étape 6 : Supprimer la licence Microsoft 365 d’un ancien employé

Si vous ne souhaitez pas payer pour une licence après qu’une personne a quitté votre organisation, vous devez supprimer sa licence Microsoft 365, puis la supprimer de votre abonnement. Vous pouvez attribuer une licence à un autre utilisateur si vous ne la supprimez pas.
  
Lorsque vous effectuez cette opération, toutes les données de cet utilisateur sont conservées pendant 30 jours. Vous pouvez [accéder](get-access-to-and-back-up-a-former-user-s-data.md) aux données, ou [restaurer](restore-user.md) le compte si l'utilisateur revient. Après 30 jours, toutes les données de l’utilisateur (à l’exception des documents stockés sur SharePoint Online) sont définitivement supprimées de Microsoft 365 et ne peuvent pas être récupérées.

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sélectionnez l’onglet **Licences et** applications.
3. Clear the check boxes for the license(s) you want to remove, and then select **Save changes**.

**Pour réduire le nombre de licences que vous** payez jusqu’à ce que vous recrutiez une autre personne, vous devez suivre les étapes suivantes :

1. Dans le Centre d’administration, allez sur **la** page Facturation de vos \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">produits,</a> puis sélectionnez **l’onglet Produits.**
2. Sélectionnez l’abonnement dont vous souhaitez supprimer des licences.
3. Dans la page de détails, **sélectionnez Supprimer des licences.**
4. Dans le **volet Supprimer des licences,** sous Nouvelle quantité, dans la zone Nombre total de **licences,** entrez le nombre total de licences que vous souhaitez pour cet abonnement. Par exemple, si vous avez 25 licences et que vous souhaitez en supprimer une, entrez 24.
5. Cliquez sur **Enregistrer**.

Lorsque vous [ajoutez une autre](add-users.md) personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape !

Pour plus d’informations sur la gestion des licences utilisateur pour Microsoft 365 pour les entreprises, voir Attribuer des [licences](../manage/assign-licenses-to-users.md)aux utilisateurs dans Microsoft 365 entreprise et Désattribuer des licences à des utilisateurs dans [Microsoft 365 entreprise.](../manage/remove-licenses-from-users.md)
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Comment le compte supprimé d'un employé affecte Skype Entreprise

Lorsque vous supprimez une licence d'utilisateur d'Office 365, le numéro d'appel PSTN associé à l'utilisateur est libéré. Vous pouvez l'assigner à un autre utilisateur.
  
Si l'utilisateur appartient à un groupe de files d'attente, il ne sera plus une cible viable des agents de la file d'attente d'appels. Nous recommandons donc de supprimer également l'utilisateur des groupes associés à la file d'attente d'appels.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Configurer le forwarding d’appel vers des personnes de votre organisation

Si vous devez configurer le transfert d’appel pour le numéro de téléphone de l’employé licencié, le paramètre de transfert d’appel sous stratégies d’appel peut configurer le transfert dans lequel les appels entrants peuvent être transmis à d’autres utilisateurs ou faire sonner une autre personne en même temps. Pour plus d’informations, voir [Stratégies d’appel dans Microsoft Teams](/microsoftteams/teams-calling-policy).
