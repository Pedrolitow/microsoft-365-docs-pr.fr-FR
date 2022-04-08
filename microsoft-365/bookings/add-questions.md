---
title: Ajouter des questions personnalisées et requises à la page réservation
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: fd6b7587-5055-4bcd-83a4-13bd4929bfff
description: Si vous avez besoin de poser des questions aux clients lorsqu’ils prennent rendez-vous avec vous en ligne, vous pouvez ajouter des questions personnalisées et des questions requises à la page de réservation.
ms.openlocfilehash: 9830dfaa9ac1964e74eb16321d061e096aad1bab
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714612"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Ajouter des questions personnalisées et requises à la page réservation

> [!NOTE]
> Cet article vous aide à interagir avec la dernière version de Microsoft Bookings. Les versions précédentes seront mises hors service dans les prochains mois.

Bookings vous permet de créer des questions pour poser des questions à vos clients lorsqu’ils réservent des rendez-vous. Il vous permet également de choisir les questions requises.

Vous associez les questions à un service, afin que chaque service puisse avoir un ensemble de questions différent. Par exemple, un coiffeur peut demander aux clients qui réservent un rendez-vous de coloration des cheveux s’ils ont des allergies connues aux blanchissements ou teintes. Cela vous permet, ainsi qu’à vos clients, de gagner du temps lorsqu’ils arrivent pour leur rendez-vous.

Les clients voient les questions personnalisées lorsqu’ils créent leur rendez-vous sur la page de réservation. Le personnel verra les questions personnalisées lorsqu’il créera une réservation à partir du calendrier Bookings ou lors de l’affichage d’un rendez-vous existant. Bookings enregistre toutes vos questions dans une liste maître afin de ne pas avoir à recréer les mêmes questions pour chaque service. Vous pouvez également choisir si des questions sont requises ou facultatives.

> [!NOTE]
> Les réponses du client aux questions sont visibles lorsque vous examinez son rendez-vous dans le calendrier de réservation.

Pour plus d’informations sur la personnalisation et la personnalisation de votre page de réservation, consultez [Personnaliser votre page de réservation](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Ajouter des questions personnalisées à vos services

1. Connectez-vous à Microsoft 365 et accédez à **Bookings**.

1. Choisissez votre calendrier.

1. Accédez à **Services** et modifiez un service existant ou **ajoutez un service**.

1. Choisissez la section **Champs personnalisés** .

   Nous avons déjà ajouté des questions de base sur les informations client : adresse e-mail, numéro de téléphone, adresse client et notes client. La première fois que vous effectuez cette opération, les questions sur les informations client sont mises en surbrillance en gris. Cela signifie que l’utilisateur verra cette question. Si vous sélectionnez la question, la zone de surbrillance qui l’entoure disparaît et votre client ne se pose pas cette question.

   Dans cet exemple, le numéro de téléphone et les notes des clients ont été désactivés et nous avons créé deux nouvelles questions personnalisées à poser.

   ![Image de l’écran des questions personnalisées.](../media/bookings-questions-custom-fields.png)

1. Pour rendre la question obligatoire, cochez la case **Obligatoire** . Votre client ne pourra pas terminer la réservation tant qu’il n’aura pas répondu aux questions requises.

1. Pour créer une question personnalisée, sélectionnez **Ajouter une question** en haut du panneau. Écrivez votre question, puis **sélectionnez Enregistrer**.

1. Cliquez sur la question pour l’activer. Une zone en surbrillance s’affiche autour de celle-ci et la question est activée.

1. Cliquez sur **OK** en haut de la page, puis **enregistrez le service**.

Bookings enregistrez toutes vos questions personnalisées dans une liste maître afin que vous puissiez facilement ajouter des questions à chaque service sans avoir à taper à plusieurs reprises les mêmes questions. Par exemple, si vous ouvrez un autre service, la question que vous avez créée pour le premier service s’affiche dans la section Champs personnalisés, mais elle sera désactivée. Cliquez sur la question pour qu’un rectangle mis en surbrillance s’affiche et que la question soit activée.

Dans cet exemple, vous pouvez voir que les questions qui ont été ajoutées pour le premier service sont disponibles pour ce service. Toutes les questions que vous créez pour ce service seront disponibles pour tous les services.

   ![Image des questions qui s’affichent pour plusieurs services.](../media/bookings-questions-services.png)

Si votre page de réservation est déjà publiée, vous n’avez rien à faire d’autre. Les clients verront les questions la prochaine fois qu’ils réserveront avec vous. Si votre page de réservation n’est pas encore publiée, accédez à la **page de réservation** à partir de Outlook sur le web, puis **sélectionnez Enregistrer et publier**.

> [!WARNING]
> Vous pouvez également supprimer des questions de la liste maître. Toutefois, si vous supprimez une question, elle sera supprimée de chaque service. Nous vous recommandons de désactiver la question en la sélectionnant pour vous assurer que vous n’avez pas d’impact sur les autres services. Vous pouvez voir qu’une question est désactivée si elle n’est pas entourée d’un rectangle mis en surbrillance.

## <a name="customer-experience"></a>Expérience client

Lorsque vos clients réservent un rendez-vous avec vous, les questions de base sur les informations client s’affichent dans la section **Ajouter vos détails** . Toutes les questions personnalisées que vous ajoutez se trouverez dans la section **Fournir des informations supplémentaires** .

![Image de ce que les clients voient quand les questions sont activées.](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Expérience du personnel

Lorsque vos clients réservent un rendez-vous avec vous, votre personnel voit les questions et les réponses du client dans le calendrier de réservation. Pour le voir, accédez à **Bookings** \> **Calendrier**, puis ouvrez un rendez-vous.

![Image de ce que le personnel voit quand les questions sont activées.](../media/bookings-questions-staff.png)
