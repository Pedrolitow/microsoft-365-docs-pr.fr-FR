---
title: Arrêter les messages électroniques de transfert automatique
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment arrêter le transfert automatique des courriers électroniques.
ms.openlocfilehash: 0683e133f6c261dc19cc098b13be298cd8086001
ms.sourcegitcommit: f231eece2927f0d01072fd092db1eab15525bbc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "49702019"
---
# <a name="stop-email-auto-forward"></a>Arrêter l’envoi automatique de messages électroniques

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

Si un pirate accède à la boîte aux lettres d’un utilisateur, il peut transférer automatiquement le courrier électronique de l’utilisateur vers une adresse externe et voler des informations propriétaires. Vous pouvez l’arrêter en créant une règle de flux de messagerie.

## <a name="try-it"></a>Essayez !

1. Dans le centre d’administration 365 de Microsoft, sélectionnez **Exchange**, **flux de messagerie**, puis sous l’onglet **règles** , sélectionnez le signe plus et choisissez **créer une nouvelle règle**.
1. Sélectionnez **plus d’options**. Nommez votre nouvelle règle.
1. Ensuite, ouvrez la liste déroulante pour **appliquer cette règle si**, sélectionnez **l’expéditeur**, puis **externe interne**.
1. Sélectionnez **dans l’organisation**, puis cliquez sur **OK**.
1. Choisissez **Ajouter une condition**, ouvrez la liste déroulante, sélectionnez **les propriétés du message**, puis **le type de message**.
1. Ouvrez la liste déroulante **Sélectionner un type de message** , choisissez **transfert automatique**, puis **OK**.
1. Ouvrez la liste déroulante **effectuer les opérations suivantes** , sélectionnez **bloquer le message**, puis **rejeter le message et inclure une explication**.
1. Entrez le texte du message correspondant à votre explication, puis sélectionnez **OK**.
1. Faites défiler vers le bas, puis sélectionnez **Enregistrer**.

    Votre règle a été créée et les pirates ne seront plus en mesure de transférer automatiquement les messages.