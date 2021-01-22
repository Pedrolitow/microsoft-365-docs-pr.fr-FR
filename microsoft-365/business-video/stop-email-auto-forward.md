---
title: Arrêter le transfert automatique d’e-mails
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
- okr_smb
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment arrêter le forwarding automatique des e-mails.
ms.openlocfilehash: ebbe37ab5c4a60c6ac4b6ebf8877247199460fa1
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49925885"
---
# <a name="stop-email-auto-forward"></a>Arrêter le courrier électronique à l’avance automatique

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

Si un pirate informatique accède à la boîte aux lettres d’un utilisateur, il peut automatiquement le faire accéder à une adresse extérieure et voler des informations confidentielles. Vous pouvez arrêter cela en créant une règle de flux de messagerie.

## <a name="try-it"></a>Essayez !

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Exchange,** flux de messagerie **et,** sous l’onglet Règles, sélectionnez le signe plus et choisissez créer **une règle.** 
1. Sélectionnez **plus d’options.** Nommez votre nouvelle règle.
1. Ensuite, ouvrez la drop-down pour **appliquer cette règle si**, sélectionnez **l’expéditeur,** puis **est interne externe**.
1. Sélectionnez **À l’intérieur de** l’organisation, puis **OK**.
1. Choose **add condition**, open the drop-down, select The message **properties**, then include the **message type**.
1. Ouvrez la drop-down sélectionner le type de **message,** sélectionnez **Auto-forward**, puis **OK**.
1. Ouvrez **la liste suivante,** sélectionnez Bloquer le **message,** puis **rejetez le message et incluez une explication.**
1. Entrez le texte du message pour votre explication, puis sélectionnez **OK.**
1. Faites défiler jusqu’au bas et sélectionnez **Enregistrer.**

    Votre règle a été créée et les pirates informatiques ne pourront plus envoyer automatiquement des messages.