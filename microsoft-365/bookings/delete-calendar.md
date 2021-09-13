---
title: Supprimer un calendrier
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Utilisez la Centre d'administration Microsoft 365 ou Windows PowerShell pour supprimer des calendriers Bookings.
ms.openlocfilehash: fc5975e25fa3b1f2d2aab991cc7aac8038181f3f
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59178307"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Supprimer un calendrier de réservation dans Bookings

Cet article explique comment supprimer un calendrier de réservation indésirable. Vous pouvez supprimer le calendrier de réservation dans le Centre d'administration Microsoft 365 ou vous pouvez utiliser PowerShell. Le calendrier Bookings est une boîte aux lettres dans Exchange Online vous supprimez le compte d’utilisateur correspondant pour supprimer le calendrier de réservation.

> [!IMPORTANT]
> Tous les calendriers de réservation que vous avez créés en 2017 ou avant doivent être supprimés à l’aide des instructions PowerShell de cette rubrique. Tous les calendriers de réservation créés en 2018 ou après peuvent être supprimés dans le Centre d'administration Microsoft 365.

Le calendrier de réservation est l’endroit où sont stockées toutes les informations pertinentes sur ce calendrier de réservation et les données, notamment :

- Informations professionnelles, logo et heures de travail ajoutés lors de la création du calendrier de réservation
- Personnel et services pertinents ajoutés lors de la création du calendrier de réservation
- Toutes les réservations et les congés ajoutés au calendrier de réservation une fois créés.

> [!WARNING]
> Une fois qu’un calendrier de réservation est supprimé, ces informations supplémentaires sont également définitivement supprimées et ne peuvent pas être récupérées.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Supprimer un calendrier de réservation dans le Centre d'administration Microsoft 365

1. Aller au Centre d’administration Microsoft 365.

1. Dans le centre d'administration, sélectionnez **Utilisateurs**.

   ![Image de l’interface utilisateur utilisateur dans Centre d'administration Microsoft 365.](../media/bookings-admin-center-users.png)

1. Sur la page **Utilisateurs actifs**, sélectionnez les noms des utilisateurs à supprimer, puis **Supprimer l'utilisateur**.

   ![Image de la suppression de l’interface utilisateur dans Centre d'administration Microsoft 365.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Supprimer un calendrier de réservation à l’Exchange Online PowerShell

Consultez [Connecter à Exchange Online PowerShell pour les](/powershell/exchange/exchange-online-powershell-v2) conditions préalables et des instructions pour la connexion Exchange Online PowerShell.

Pour effectuer ces étapes, vous devez utiliser une fenêtre de commande Microsoft PowerShell active que vous avez exécutée en choisissant l’option « Exécuter en tant qu’administrateur ».

1. Dans une fenêtre PowerShell, chargez le module EXO V2 en exécutant la commande suivante :

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > Si vous avez déjà [installé le module EXO v2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module), la commande précédente fonctionnera comme écrite.
   
2. La commande à exécuter utilise la syntaxe suivante:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ est votre compte au format du nom d’utilisateur principal (par exemple, `john@contoso.com`).

3. Lorsque vous y êtes invité, connectez-vous avec les informations d’identification de l’administrateur client au client Microsoft 365 qui héberge le calendrier de réservation que vous souhaitez supprimer définitivement.

4. Une fois cette commande traitée, entrez la commande suivante pour obtenir la liste des boîtes aux lettres de réservation dans votre client :

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. Tapez la commande suivante :

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Faites attention à taper le nom exact de l’alias de boîte aux lettres de réservation que vous souhaitez supprimer définitivement.

6. Pour vérifier que le calendrier a été supprimé, entrez la commande suivante :

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Le calendrier supprimé n’apparaîtra pas dans la sortie.
