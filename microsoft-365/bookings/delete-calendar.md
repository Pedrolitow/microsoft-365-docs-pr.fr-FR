---
title: Supprimer un calendrier
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Utilisez la Centre d'administration Microsoft 365 ou Windows PowerShell pour supprimer les calendriers Bookings.
ms.openlocfilehash: b5cb74940bc68116673322c6d38e3fecd4002326
ms.sourcegitcommit: 95ac076310ab9006ed92c69938f7ae771cd10826
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67851189"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Supprimer un calendrier de réservation dans Bookings

Cet article explique comment supprimer un calendrier de réservation indésirable. Vous pouvez supprimer le calendrier de réservation dans le Centre d'administration Microsoft 365 ou utiliser PowerShell. Le calendrier Bookings étant une boîte aux lettres dans Exchange Online vous supprimez le compte d’utilisateur correspondant pour supprimer le calendrier de réservation.

> [!IMPORTANT]
> Tous les calendriers de réservation que vous avez créés en 2017 ou avant doivent être supprimés à l’aide des instructions PowerShell de cette rubrique. Tous les calendriers de réservation créés en 2018 ou après peuvent être supprimés dans le Centre d'administration Microsoft 365.

Le calendrier de réservation est l’endroit où toutes les informations pertinentes sur ce calendrier de réservation et les données sont stockées, notamment :

- Informations professionnelles, logo et heures de travail ajoutées lors de la création du calendrier de réservation
- Personnel et services pertinents ajoutés lors de la création du calendrier de réservation
- Toutes les réservations et les rendez-vous de congé ajoutés au calendrier de réservation une fois qu’il a été créé.

> [!WARNING]
> Une fois qu’un calendrier de réservation est supprimé, ces informations supplémentaires sont également supprimées définitivement et ne peuvent pas être récupérées.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Supprimer un calendrier de réservation dans le Centre d'administration Microsoft 365

1. Aller au Centre d’administration Microsoft 365.

1. Dans le centre d'administration, sélectionnez **Utilisateurs**.

   ![Image de l’interface utilisateur utilisateur utilisateur dans Centre d'administration Microsoft 365.](../media/bookings-admin-center-users.png)

1. Dans la page **Utilisateurs actifs** , choisissez le nom du calendrier de réservation à supprimer, puis **sélectionnez Supprimer l’utilisateur**.

   ![Image de l’interface utilisateur Supprimer l’utilisateur dans Centre d'administration Microsoft 365.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Supprimer un calendrier de réservation à l’aide de Exchange Online PowerShell

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande suivante pour obtenir la liste des boîtes aux lettres de réservation dans votre locataire :

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

3. Remplacez par \<BookingCalendarToDelete\> le nom exact de l’alias de boîte aux lettres de réservation que vous souhaitez supprimer définitivement, puis exécutez la commande suivante :

   ```powershell
   Remove-Mailbox -Identity <BookingCalendarToDelete>
   ```

   > [!IMPORTANT]
   > Veillez à taper le nom exact de l’alias de boîte aux lettres de réservation que vous souhaitez supprimer définitivement.

4. Pour vérifier que le calendrier a été supprimé, exécutez la commande suivante :

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   Le calendrier supprimé n’apparaît pas dans la sortie.
