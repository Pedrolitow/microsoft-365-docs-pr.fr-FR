---
title: Ajouter des questions personnalisées et requises à la page de réservation
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
localization_priority: Normal
ms.assetid: fd6b7587-5055-4bcd-83a4-13bd4929bfff
description: Si vous avez besoin de poser des questions à vos clients lors de la création d’un rendez-vous avec vous en ligne, vous pouvez ajouter des questions et des questions personnalisées à la page de réservation.
ms.openlocfilehash: ebbb07857fd8bb196f769dfb7e71ad25a85dfd54
ms.sourcegitcommit: 41fd71ec7175ea3b94f5d3ea1ae2c8fb8dc84227
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "47419621"
---
# <a name="add-custom-and-required-questions-to-the-booking-page"></a>Ajouter des questions personnalisées et requises à la page de réservation

Bookings vous permet de créer des questions pour demander à vos clients de réserver des rendez-vous. Elle vous permet également de choisir les questions requises.

Vous associez les questions à un service, afin que chaque service puisse avoir un ensemble de questions différent. Par exemple, un Stylist capillaire peut demander aux clients qui représentent un rendez-vous de coloration capillaire s’ils ont des allergies connues pour des blanchis ou des teintes. Cela vous permet, ainsi qu’à vos clients, de gagner du temps lorsqu’ils arrivent pour leur rendez-vous.

Les clients verront les questions personnalisées lorsqu’ils créeront leur rendez-vous sur la page de réservation. Le personnel verra les questions personnalisées lors de la création d’une réservation à partir du calendrier bookings ou lors de l’affichage d’un rendez-vous existant. Bookings enregistre toutes vos questions dans une liste principale afin de ne pas avoir à recréer les mêmes questions pour chaque service. Vous pouvez également choisir si les questions sont obligatoires ou facultatives.

> [!NOTE]
> Les réponses du client aux questions sont visibles lorsque vous examinez leur rendez-vous dans le calendrier de réservation.

Pour plus d’informations sur la personnalisation et la personnalisation de votre page de réservation, voir [personnaliser votre page de réservation](customize-booking-page.md).

## <a name="add-custom-questions-to-your-services"></a>Ajouter des questions personnalisées à vos services

1. Connectez-vous à Microsoft 365 et accédez à **livres**.

1. Accédez à **services** et modifiez un service existant ou **Ajoutez un service**.

1. Faites défiler vers le bas jusqu’à la section **champs personnalisés** , puis sélectionnez **modifier**.

   Nous avons déjà ajouté des questions relatives aux informations client de base : e-mail du client, numéro de téléphone, adresse du client et notes client. La première fois que vous effectuez cette opération, les questions relatives aux informations client sont mises en évidence en gris. Cela signifie que l’utilisateur verra cette question. Si vous sélectionnez la question, la zone de surbrillance qui la entoure disparaît et votre client n’est pas invité à répondre à cette question.

   Dans cet exemple, le numéro de téléphone et les notes client ont été désactivés et nous avons créé deux nouvelles questions personnalisées à poser.

   ![Image d’un écran de questions personnalisées](../media/bookings-questions-custom-fields.png)

1. Pour faire la question requise, activez la case à cocher **obligatoire** . Votre client ne pourra pas terminer la réservation tant qu’il n’aura pas répondu aux questions requises.

1. Pour créer une question personnalisée, sélectionnez **Ajouter une question** dans la partie supérieure du panneau. Rédigez votre question, puis sélectionnez **Enregistrer**.

1. Cliquez sur la question pour l’activer. Un cadre en surbrillance apparaît entouré et la question est activée.

1. Cliquez sur **OK** en haut de la page, puis **Enregistrez le service**.

Bookings enregistre toutes vos questions personnalisées dans une liste principale afin que vous puissiez facilement ajouter des questions à chaque service sans avoir à taper les mêmes questions. Par exemple, si vous ouvrez un autre service, la question que vous avez créée pour le premier service s’affichera dans la section champs personnalisés, mais elle sera désactivée. Cliquez sur la question afin qu’un rectangle mis en surbrillance s’affiche et que la question soit activée.

Dans cet exemple, vous pouvez voir que les questions qui ont été ajoutées pour le premier service sont disponibles pour ce service. Toutes les questions que vous créez pour ce service seront disponibles pour tous les services.

   ![Image de questions qui apparaissent pour plusieurs services](../media/bookings-questions-services.png)

Si votre page de réservation est déjà publiée, vous n’avez rien à faire d’autre. Les clients verront les questions lors de leur prochaine ouverture de livres. Si votre page de réservation n’est pas encore publiée, accédez à la **page réservation** à partir d’Outlook sur le Web, puis sélectionnez **enregistrer et publier**.

> [!WARNING]
> Vous pouvez également supprimer des questions de la liste principale. Toutefois, si vous supprimez une question, elle sera supprimée de chaque service. Nous vous recommandons de désactiver la question en la sélectionnant afin de vous assurer que vous n’avez aucun impact sur les autres services. Vous pouvez constater qu’une question est désactivée si elle n’est pas entourée d’un rectangle mis en surbrillance.

## <a name="customer-experience"></a>Expérience client

Lorsque vos clients livrent un rendez-vous avec vous, les questions relatives aux informations client de base s’affichent dans la section **ajouter vos informations** . Toutes les questions personnalisées que vous ajoutez seront dans la section **fournir des informations supplémentaires** .

![Image de ce que les clients voient lorsque des questions sont activées](../media/bookings-questions-customer.png)

## <a name="staff-experience"></a>Expérience du personnel

Lorsque vos clients livrent un rendez-vous avec vous, votre équipe verra les questions et les réponses du client sur le calendrier de réservation. Pour le voir, accédez à **livres** \> **civils** , puis ouvrez un rendez-vous.

![Image du personnel qui détermine quand des questions sont activées](../media/bookings-questions-staff.png)
