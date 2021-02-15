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
description: Utilisez le Centre d’administration Microsoft 365 ou Windows PowerShell pour supprimer des calendriers Bookings.
ms.openlocfilehash: 2fcb92cee18d709ef0e1fa3faa0246e622a9f9db
ms.sourcegitcommit: 0402d3275632fceda9137b6abc3ce48c8020172a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "49126648"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>Supprimer un calendrier de réservation dans Bookings

Cet article explique comment supprimer un calendrier de réservation indésirable. Vous pouvez supprimer le calendrier de réservation dans le Centre d’administration Microsoft 365 ou vous pouvez utiliser PowerShell. Le calendrier Bookings est une boîte aux lettres dans Exchange Online, vous supprimez le compte d’utilisateur correspondant pour supprimer le calendrier de réservation.

> [!IMPORTANT]
> Tous les calendriers de réservation que vous avez créés en 2017 ou avant doivent être supprimés à l’aide des instructions PowerShell de cette rubrique. Tous les calendriers de réservation créés en 2018 ou après peuvent être supprimés dans le Centre d’administration Microsoft 365.

Le calendrier de réservation est l’endroit où sont stockées toutes les informations pertinentes sur ce calendrier de réservation et les données, notamment :

- Informations professionnelles, logo et heures de travail ajoutés lors de la création du calendrier de réservation
- Personnel et services pertinents ajoutés lors de la création du calendrier de réservation
- Toutes les réservations et les congés ajoutés au calendrier de réservation une fois créés.

> [!WARNING]
> Une fois qu’un calendrier de réservation est supprimé, ces informations supplémentaires sont également définitivement supprimées et ne peuvent pas être récupérées.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>Supprimer un calendrier de réservation dans le Centre d’administration Microsoft 365

1. Aller au Centre d’administration Microsoft 365.

1. Dans le centre d'administration, sélectionnez **Utilisateurs**.

   ![Image de l’interface utilisateur utilisateur dans le Centre d’administration Microsoft 365](../media/bookings-admin-center-users.png)

1. Sur la page **Utilisateurs actifs**, sélectionnez les noms des utilisateurs à supprimer, puis **Supprimer l'utilisateur**.

   ![Image de la suppression de l’interface utilisateur dans le Centre d’administration Microsoft 365](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>Supprimer un calendrier de réservation à l’aide d’Exchange Online PowerShell

Consultez [La connexion à Exchange Online PowerShell pour les](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps) conditions préalables et des instructions pour la connexion à Exchange Online PowerShell.

Pour effectuer ces étapes, vous devez utiliser une fenêtre de commande Microsoft PowerShell active que vous avez exécutée en choisissant l’option « Exécuter en tant qu’administrateur ».

1. Entrez la commande suivante :

   ```PowerShell
    $user = get-credential
   ```

1. Lorsque vous y êtes invité, connectez-vous avec les informations d’identification de l’administrateur client au client Microsoft 365 qui héberge le calendrier de réservation que vous souhaitez supprimer définitivement.

1. À l’invite de commandes PowerShell, entrez la commande ci-après :

   ```PowerShell
    $s = New-Pssession -ConnectionUri https://outlook.office365.com/powershell-liveid -Credential $user -Authentication basic -AllowRedirection -ConfigurationName Microsoft.Exchange
   ```

1. Entrez la commande suivante :

   ```PowerShell
    Import-PSSession $s
   ```

1. Une fois cette commande traitée, entrez la commande suivante pour obtenir la liste des boîtes aux lettres de réservation dans votre client :

   ```PowerShell
    get-mailbox -RecipientTypeDetails Scheduling
   ```

1. Tapez la commande suivante :

   ```PowerShell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > Faites attention à taper le nom exact de l’alias de boîte aux lettres de réservation que vous souhaitez supprimer définitivement.

1. Pour vérifier que le calendrier a été supprimé, entrez la commande suivante :

   ```PowerShell
    get-mailbox -RecipientTypeDetails Scheduling
   ```

   Le calendrier supprimé n’apparaîtra pas dans la sortie.
