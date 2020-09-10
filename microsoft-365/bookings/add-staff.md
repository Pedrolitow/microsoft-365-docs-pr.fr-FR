---
title: Ajouter du personnel aux réservations
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: 298c529b-407b-4a2b-b2c5-6e77a9d1f07f
description: Cette page permet de créer votre liste de personnel et de gérer les détails des membres du personnel, tels que le nom, le numéro de téléphone et l’adresse de messagerie.
ms.openlocfilehash: cfd42eedb6e0bea08cdee1503fc373167996c75b
ms.sourcegitcommit: 41fd71ec7175ea3b94f5d3ea1ae2c8fb8dc84227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47419624"
---
# <a name="add-staff-to-bookings"></a>Ajouter du personnel aux réservations

La page personnel dans bookings est l’endroit où vous créez votre liste de personnel et gérez les détails de membre du personnel, tels que le nom, le numéro de téléphone et l’adresse de messagerie. Vous pouvez également définir des heures de travail pour chaque membre du personnel à partir de cet emplacement.

> [!NOTE]
> Bookings est activé par défaut pour les clients qui disposent des abonnements Microsoft 365 Business standard, Microsoft 365 a3 ou Microsoft 365 a5. Bookings est également disponible pour les clients disposant d’Office 365 entreprise E3 et d’Office 365 entreprise E5, mais il est désactivé par défaut. Pour commencer, consultez la rubrique [obtenir l’accès à Microsoft bookings](get-access.md). Pour activer ou désactiver les réservations, reportez-vous à [la rubrique activer ou désactiver des réservations pour votre organisation](turn-bookings-on-or-off.md).

## <a name="add-staff"></a>Ajouter du personnel

Bien que les réservations soient une fonctionnalité de Microsoft 365, tous les membres de votre équipe ne doivent pas nécessairement disposer d’un compte Microsoft 365. Tous les membres du personnel doivent avoir une adresse de messagerie valide afin qu’ils puissent recevoir des réservations et planifier des modifications.

Regardez cette vidéo ou suivez les étapes ci-dessous pour ajouter votre équipe.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWuVka]

1. Accédez à la [page gérer le personnel](https://outlook.office.com/bookings/staff) , puis sélectionnez **Ajouter un personnel** .

2. Sélectionnez le bouton **Ajouter du personnel** .

3. Lorsque vous ajoutez du personnel à partir de votre client, tapez son nom dans le champ **Ajouter des personnes** et sélectionnez-le lorsqu’ils apparaissent dans le menu déroulant. Les autres champs sont renseignés automatiquement.

    Une fois qu’un membre du personnel est ajouté, vous pouvez modifier le nom qui apparaît sur toutes les communications de livres en sélectionnant le **x** en regard de son nom et en modifiant le champ **Ajouter des personnes** . Cela peut être utile si vous souhaitez que les membres du personnel aient un titre ou un nom spécifique affiché pour les clients, tels que l’énumération de l’Adele Vance sous la forme « Dr. Vance, MD ».

4. Pour ajouter du personnel provenant de l’extérieur de votre client, remplissez manuellement le courrier électronique et d’autres informations.

    > [!NOTE]
    > Les membres de l’extérieur de votre client ne seront pas en mesure de partager les informations de disponibilité avec les réservations.

5. Pour chaque membre du personnel, sélectionnez un rôle : administrateur, visionneuse ou invité.
    - Les **administrateurs** peuvent modifier tous les paramètres, ajouter et supprimer des membres du personnel, et créer, modifier ou supprimer des réservations.
    - Les **utilisateurs** peuvent voir toutes les réservations sur le calendrier, mais ils ne peuvent pas les modifier ou les supprimer. Ils ont un accès en lecture seule aux paramètres.
    - Les **invités** peuvent être affectés à des réservations, mais ils ne peuvent pas ouvrir la boîte aux lettres de réservation.

6. Sélectionnez **avertir tous les membres du personnel par e-mail lorsqu’une réservation qui leur est affectée est créée ou modifiée** pour activer les courriels de personnel. Voici un exemple de message électronique :

    :::image type="content" source="media/bookings-notify-all-email.jpg" alt-text="Un courrier électronique de notification à partir de livres":::

7. Sélectionner **des événements sur le calendrier Office 365 affecte la disponibilité** si vous souhaitez que les informations de disponibilité des calendriers des membres du personnel soient en incidence sur la disponibilité des services de livres dans les réservations.

    Par exemple, si un membre du personnel a une réunion d’équipe ou un rendez-vous personnel planifié pour 3pm un mercredi, les réservations indiquent que le membre du personnel n’est pas disponible pour être enregistré dans ce créneau horaire. Cette fois apparaîtra comme étant occupé ou provisoire dans l’affichage Calendrier livres, comme illustré dans l’exemple ci-dessous.

    :::image type="content" source="media/bookings-busy-tentative-view.jpg" alt-text="Affichage d’un calendrier bookings":::

> [!IMPORTANT]
> Nous vous recommandons vivement de laisser ce paramètre activé (il est activé par défaut) afin d’éviter les doubles réservations et d’optimiser la disponibilité de vos membres du personnel.

8. Sélectionnez **utiliser les heures d’ouverture** pour définir toutes les heures d’réservables pour que les membres de votre équipe soient uniquement pendant les heures d’ouverture que vous avez définies dans la section **heures** d’ouverture de la page d’informations professionnelles.

    Si vous désactivez cette case à cocher, le personnel peut recevoir des heures personnalisées supplémentaires lorsqu’il peut être réservé. Ceci est utile pour les scénarios dans lesquels un membre du personnel peut se trouver uniquement sur le site au mardi et au mercredi, ou les matins pour un type de rendez-vous et ses après-midi pour d’autres types.
