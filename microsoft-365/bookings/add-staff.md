---
title: Ajouter du personnel aux réservations
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
description: Cette page permet de créer votre liste de membres du personnel et de gérer les détails des membres du personnel tels que le nom, le numéro de téléphone et l’adresse e-mail.
ms.openlocfilehash: 3b61c2f3e5597208ace2a87a7d203e8d724e4f5f
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573342"
---
# <a name="add-staff-to-bookings"></a>Ajouter du personnel aux réservations

La page Personnel dans Bookings vous permet de créer votre liste de personnel et de gérer les détails des membres du personnel tels que le nom, le numéro de téléphone et l’adresse e-mail. Vous pouvez également définir des heures de travail pour chaque membre du personnel à partir d’ici.

## <a name="before-you-begin"></a>Avant de commencer

Bien que Bookings soit une fonctionnalité de Microsoft 365, tous les membres de votre personnel ne sont pas tenus d’avoir Microsoft 365 compte. Tous les membres du personnel doivent avoir une adresse de messagerie valide pour recevoir des réservations et planifier des modifications.

## <a name="watch-add-your-staff-to-bookings"></a>Regarder : Ajouter votre personnel à Bookings

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Étapes

1. Go to the [Manage staff page](https://outlook.office.com/bookings/staff) and select Add **staff**

2. Sélectionnez le **bouton Ajouter du personnel.**

3. Lorsque vous ajoutez du personnel au  sein de votre organisation, tapez son nom dans le champ Ajouter des personnes et sélectionnez-les lorsqu’ils apparaissent dans le menu déroulant. Les autres champs sont automatiquement remplis.

    Une fois qu’un membre du personnel est ajouté, vous pouvez modifier le nom qui apparaît  sur toutes les communications Bookings en sélectionnant **le x** en-de côté de leur nom et en éditant le champ Ajouter des personnes. Cela peut être utile si vous souhaitez que les membres du personnel affichent un titre ou un nom spécifique pour les clients, par exemple, en répertoriant Adele Vance en tant que « Dr Vance, MD ».

4. Pour ajouter du personnel externe à votre organisation, remplissez manuellement son courrier électronique et d’autres informations.

    > [!NOTE]
    > Les employés extérieurs à votre client ne pourront pas partager d’informations de libre/occupé avec Bookings.

5. Pour chaque membre du personnel, sélectionnez un rôle : administrateur, visionneuse ou invité.
    - **Les administrateurs** peuvent modifier tous les paramètres, ajouter et supprimer du personnel, et créer, modifier ou supprimer des réservations.
    - **Les** visiteurs peuvent voir toutes les réservations dans le calendrier, mais ils ne peuvent pas les modifier ou les supprimer. Ils ont un accès en lecture seule aux paramètres.
    - **Les** invités peuvent être affectés à des réservations, mais ils ne peuvent pas ouvrir la boîte aux lettres de réservation.

6. Sélectionnez **Avertir tous les membres du personnel par courrier** électronique lorsqu’une réservation qui leur est affectée est créée ou modifiée pour activer les e-mails du personnel. Voici un exemple de message électronique :

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Un e-mail de notification de Bookings.":::

7. La sélection d’événements **Office 365 le calendrier** affecte la disponibilité si vous souhaitez que les informations de disponibilité des calendriers des membres du personnel affectent la disponibilité des services bookings via Bookings.

    Par exemple, si un membre du personnel a une réunion d’équipe ou un rendez-vous personnel prévu pour 15h00 le mercredi, Bookings indique que ce membre du personnel n’est pas disponible pour être réservé dans ce créneau horaire. Cette heure apparaîtra comme occupée ou provisoire dans l’affichage Calendrier Bookings, comme illustré dans l’exemple ci-dessous.

    :::image type="content" source="media/bookings-busy-tentative-view.jpg" alt-text="Affichage d’un calendrier Bookings.":::

> [!IMPORTANT]
> Nous vous recommandons vivement de laisser ce paramètre sur (il est allumé par défaut) pour éviter les doubles réservations et optimiser la disponibilité des membres de votre personnel.

8. Sélectionnez Utiliser **les** heures d’ouverture pour définir toutes les heures de réservation pour que les membres de votre personnel soient uniquement pendant les heures d’ouverture que vous avez définies dans la **section** Heures d’ouverture de la page Informations professionnelles.

    La désélection de cette case permet au personnel de se voir donner des heures personnalisées qui limitent les heures de réservation. Cela est utile dans les scénarios où un membre du personnel peut se trouve uniquement les mardis et mercredis sur le site, ou il dédie ses matins à un type de rendez-vous et ses activités pour d’autres types.

    > [!NOTE]
    > Seuls les 31 premiers membres du personnel que vous ajoutez à la page de votre personnel s’affichent lorsque vous affectez des membres du personnel à un service.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Faire d’un utilisateur Bookings un super utilisateur sans l’ajouter en tant que personnel dans Bookings

Vous souhaitez peut-être ajouter une personne à votre liste de membres du personnel dans Bookings sans les mettre à la disposition des clients ou des clients. Une fois que vous en aurez fait un super utilisateur, ils deviendront administrateur de la boîte aux lettres de réservation. Être administrateur d’une boîte aux lettres de réservation est défini comme ayant un accès total et des autorisations d’envoi en tant que pour la boîte aux lettres de réservation.

> [!NOTE]
> Ces étapes fonctionnent uniquement si l’utilisateur  ajouté n’est pas déjà affecté à un rôle de visionneuse dans Bookings.

1. [Connecter à Microsoft 365 avec PowerShell.](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

2. À l’aide de PowerShell, attribuez un accès total avec les commandes suivantes :

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Exécutez ensuite cette commande pour attribuer des autorisations d’envoi en tant que.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Voici un exemple de commande PowerShell pour ajouter Allie Bellew à la boîte aux lettres de réservation de rendez-vous de contoso.

1. Exécutez d’abord la commande ci-après :

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Exécutez ensuite la commande ci-après :

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew dispose désormais d’un** accès administrateur, mais n’apparaît pas en tant que personnel bookable dans Bookings.
