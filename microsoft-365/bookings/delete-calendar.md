---
title: Supprimer un calendrier de réservation
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: Utilisez le centre d’administration Microsoft 365 ou Windows PowerShell pour supprimer des calendriers de livres.
ms.openlocfilehash: 3a1cb1c54f60247ab72056b3e39b56b0981228b7
ms.sourcegitcommit: eb3c30d53a5434d8bad7c8f48a5612f3e2675945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47422441"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Supprimer un calendrier de réservation dans bookings

Cet article explique comment supprimer un calendrier de réservation indésirable. Vous pouvez supprimer le calendrier de réservation dans le centre d’administration 365 de Microsoft ou utiliser PowerShell. Le calendrier bookings est une boîte aux lettres dans Exchange Online, ce qui vous permet de supprimer le compte d’utilisateur correspondant afin de supprimer le calendrier de réservation.

> [!IMPORTANT]
> Tous les calendriers de réservation que vous avez créés dans 2017 ou antérieur doivent être supprimés à l’aide des instructions PowerShell de cette rubrique. Tous les calendriers de réservation créés dans 2018 ou après peuvent être supprimés dans le centre d’administration de Microsoft 365.

Le calendrier de réservation est l’emplacement où sont stockées toutes les informations pertinentes sur le calendrier et les données de réservation, notamment :

- Informations professionnelles, logo et heures de travail ajoutées lors de la création du calendrier de réservation
- Personnel et services appropriés ajoutés lors de la création du calendrier de réservation
- Tous les rendez-vous et les rendez-vous qui ont été ajoutés au calendrier de réservation une fois qu’il a été créé.

> [!WARNING]
> Une fois qu’un calendrier de réservation est supprimé, ces informations supplémentaires sont également supprimées définitivement et ne peuvent pas être récupérées.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Supprimer un calendrier de réservation dans le centre d’administration Microsoft 365

1. Aller au Centre d’administration Microsoft 365.

1. Dans le centre d'administration, sélectionnez **Utilisateurs**.

   ![Image de l’interface utilisateur des utilisateurs dans le centre d’administration Microsoft 365](../media/bookings-admin-center-users.png)

1. Sur la page **Utilisateurs actifs**, sélectionnez les noms des utilisateurs à supprimer, puis **Supprimer l'utilisateur**.

   ![Image de la suppression de l’interface utilisateur dans le centre d’administration Microsoft 365](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Supprimer un calendrier de réservation à l’aide d’Exchange Online PowerShell

Consultez la rubrique [connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) pour connaître les conditions préalables et obtenir des instructions pour la connexion à Exchange Online PowerShell.

Pour effectuer ces étapes, vous devez utiliser une fenêtre de commande Microsoft PowerShell active que vous avez exécutée en sélectionnant l’option « Exécuter en tant qu’administrateur ».

1. Entrez la commande suivante :

   ```PowerShell
    $user = get-credential
   ```

1. Lorsque vous y êtes invité, ouvrez une session avec des informations d’identification d’administrateur client sur le client Microsoft 365 qui héberge le calendrier de réservation que vous souhaitez supprimer définitivement.

1. À l’invite de commandes PowerShell, entrez la commande suivante :

   ```PowerShell
    $s = New-Pssession -ConnectionUri https://outlook.office365.com/powershell-liveid -Credential $user -Authentication basic -AllowRedirection -ConfigurationName Microsoft.Exchange
   ```

1. Entrez la commande suivante :

   ```PowerShell
    Import-PSSession $s
   ```

1. Une fois cette commande terminée, entrez la commande suivante pour obtenir la liste des boîtes aux lettres de réservation de votre client :

   ```PowerShell
    get-mailbox -RecipientTypeDetails Scheduling
   ```

1. Tapez la commande suivante :

   ```PowerShell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Veillez à taper le nom exact de l’alias de la boîte aux lettres de réservation que vous souhaitez supprimer définitivement.

1. Pour vérifier que le calendrier a été supprimé, entrez la commande suivante :

   ```PowerShell
    get-mailbox -RecipientTypeDetails Scheduling
   ```

   Le calendrier supprimé n’apparaît pas dans la sortie.
