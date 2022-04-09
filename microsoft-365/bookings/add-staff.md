---
title: Ajouter du personnel aux réservations
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
description: Utilisez cette page pour créer votre liste de membres du personnel et gérer les détails des membres du personnel, tels que le nom, le numéro de téléphone et l’adresse e-mail.
ms.openlocfilehash: ca938acf4bfb567d366c7ffd684e8bce8c9eea74
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746794"
---
# <a name="add-staff-to-bookings"></a>Ajouter du personnel aux réservations

> [!NOTE]
> Cet article vous aide à interagir avec la dernière version de Microsoft Bookings. Les versions précédentes seront mises hors service dans les prochains mois.

La page Personnel dans Bookings vous permet de créer votre liste de personnel et de gérer les détails des membres du personnel, tels que le nom, le numéro de téléphone et l’adresse e-mail. Vous pouvez également définir des heures de travail pour chaque membre du personnel à partir d’ici.

## <a name="before-you-begin"></a>Avant de commencer

Bien Bookings est une fonctionnalité de Microsoft 365, tous les membres de votre personnel ne sont pas tenus de Microsoft 365 compte. Tous les membres du personnel doivent avoir une adresse de messagerie valide pour recevoir des réservations et planifier des modifications.

## <a name="watch-add-your-staff-to-bookings"></a>Regardez : ajoutez votre personnel à Bookings

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

## <a name="steps"></a>Étapes

1. Choisissez votre calendrier dans la page d’accueil. 

2. Accédez à l’option Personnel dans le volet gauche et **sélectionnez Ajouter un nouveau personnel**.

3. Lorsque vous ajoutez du personnel au sein de votre organisation, tapez son nom dans le **Ajouter des personnes** champ et sélectionnez-les lorsqu’ils apparaissent dans le menu déroulant. Les autres champs sont automatiquement remplis.

    Une fois qu’un membre du personnel est ajouté, vous pouvez modifier le nom qui apparaît sur toutes les communications Bookings en sélectionnant le **x** en regard de son nom et en modifiant le **Ajouter des personnes** champ. Cela peut être utile si vous souhaitez que les membres du personnel disposent d’un titre ou d’un nom spécifique affichés pour les clients, par exemple en listant Adele Vance comme “Dr. Vance, MD.”

4. Pour ajouter du personnel externe à votre organisation, renseignez manuellement son courrier électronique et d’autres informations.

    > [!NOTE]
    > Le personnel externe à votre client ne pourra pas partager les informations de disponibilité avec Bookings.

5. Pour chaque membre du personnel, sélectionnez un rôle : administrateur, visionneuse ou invité.
    - **Administrateurs** pouvez modifier tous les paramètres, ajouter et supprimer du personnel, et créer, modifier ou supprimer des réservations.
    - **Observateurs** peuvent voir toutes les réservations dans le calendrier, mais ils ne peuvent’ pas les modifier ou les supprimer. Ils ont un accès en lecture seule aux paramètres.
    - **Les invités** peuvent être affectés aux réservations, mais ils ne peuvent’ pas ouvrir la boîte aux lettres de réservation.

6. Sélectionnez **Avertir tout le personnel par e-mail lorsqu’une réservation qui lui est attribuée est créée ou modifiée** pour activer les e-mails du personnel. Voici un exemple de signature électronique :

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Un e-mail de notification Bookings.":::

7. Sélectionnez **Événements sur le calendrier Office 365 affectent la disponibilité** si vous souhaitez que les informations de disponibilité des calendriers des membres’ du personnel aient un impact sur la disponibilité des services de réservation via Bookings.

    Par exemple, si un membre du personnel dispose d’une réunion d’équipe ou d’un rendez-vous personnel planifié pour 15h00 un mercredi, Bookings indique que ce membre du personnel n’est pas disponible pour être réservé dans cet intervalle de temps. Cette heure s’affiche comme occupée ou provisoire dans l’affichage Calendrier bookings, comme indiqué dans l’exemple ci-dessous.

    :::image type="content" source="media/bookings-busy-tentative-view-2.png" alt-text="Une vue d’un calendrier Bookings.":::

> [!IMPORTANT]
> Nous vous recommandons vivement de laisser ce paramètre activé (il est activé par défaut) pour éviter les réservations doubles et optimiser la disponibilité de vos membres du personnel.

8. Sélectionnez **Utilisez les heures de bureau** pour définir toutes les heures réservées pour que les membres de votre personnel soient uniquement dans les heures de bureau que vous avez définies dans la section **Heures de bureau** de la page Informations professionnelles.

    En désélectionnant cette zone, le personnel peut recevoir des heures personnalisées qui limitent davantage le nombre de réservations. Cela est utile pour les scénarios où un membre du personnel peut se trouver uniquement sur le site les mardis et mercredis, ou il dédie ses matins pour un type de rendez-vous et ses après-midis pour d’autres types.

    > [!NOTE]
    > Bookings prend en charge jusqu’à 100 membres du personnel dans un calendrier Bookings.

## <a name="make-a-bookings-user-a-super-user-without-adding-them-as-staff-in-bookings"></a>Faire d’un Bookings un super utilisateur sans l’ajouter en tant que personnel dans Bookings

Vous pouvez ajouter une personne à votre liste de membres du personnel dans Bookings sans les mettre à la disposition des clients ou des clients. Une fois que vous en aurez fait un super utilisateur, il deviendra administrateur de la boîte aux lettres de réservation. Être administrateur d’une boîte aux lettres de réservation est défini comme ayant un accès total et des autorisations d’envoi en tant que pour la boîte aux lettres de réservation.

> [!NOTE]
> Ces étapes fonctionnent uniquement si l’utilisateur ajouté ne dispose pas déjà d’un rôle **visionneuse** dans Bookings.

1. [Connexion à Microsoft 365 à l’aide de PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

2. À l’aide de PowerShell, attribuez un accès total avec les commandes suivantes :

    ```powershell
    Add-MailboxPermission -Identity <bookingmailbox@emailaddress> -User <adminusers@emailaddress> -AccessRights FullAccess -Deny:$false
    ```

3. Exécutez ensuite cette commande pour attribuer des autorisations d’envoi en tant que.

    ```powershell
    Add-RecipientPermission -Identity <bookingmailbox@emailaddress> -Trustee <adminusers@emailaddress> -AccessRights SendAs -Confirm:$false
    ```

Voici un exemple de commande PowerShell pour ajouter Allie Bellew à la boîte aux lettres de réservation contoso.

1. Exécutez d’abord la commande ci-après :

    ```powershell
    Add-MailboxPermission -Identity "daycare@contoso.com" -User "Allie Bellew" -AccessRights FullAccess -InheritanceType All
    ```

2. Exécutez la commande suivante :

    ```powershell
    Add-RecipientPermission -Identity "daycare@contoso.com" -Trustee "Allie Bellew" -AccessRights SendAs -Confirm:$false
    ```

**Allie Bellew** dispose désormais d’un accès administrateur, mais n’apparaît pas en tant que personnel pouvant être réservé dans Bookings.
