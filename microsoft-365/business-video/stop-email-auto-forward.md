---
title: Arrêter le transfert automatique d’e-mails
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Découvrez comment arrêter le forwarding automatique des e-mails.
ms.openlocfilehash: b6715cfdf8622521d977e0746cb9a340a8f70a5c
ms.sourcegitcommit: 53acc851abf68e2272e75df0856c0e16b0c7e48d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51578602"
---
# <a name="stop-email-auto-forward"></a>Arrêter le courrier électronique à l’avance automatique

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

Si un pirate informatique accède à la boîte aux lettres d’un utilisateur, il peut automatiquement envoyer son courrier électronique à une adresse externe et voler des informations confidentielles. Vous pouvez arrêter cela en créant une règle de flux de messagerie.

## <a name="try-it"></a>Essayez !

1. Dans le Centre d’administration Microsoft 365, sélectionnez **Exchange** **,** flux de messagerie et sous l’onglet Règles, sélectionnez le signe plus, puis créez **une règle.** 
1. Sélectionnez **plus d’options.** Nommez votre nouvelle règle.
1. Ensuite, ouvrez la drop-down pour **appliquer cette règle si**, sélectionnez **l’expéditeur,** puis **est interne externe**.
1. Sélectionnez **À l’intérieur de** l’organisation, puis **OK**.
1. Choose **add condition**, open the drop-down, select The message **properties**, then include the **message type**.
1. Ouvrez la drop-down sélectionner le type de **message,** **sélectionnez Auto-forward**, puis **OK**.
1. Ouvrez **la liste suivante,** sélectionnez Bloquer le **message,** puis **rejetez le message et incluez une explication.**
1. Entrez le texte du message pour votre explication, puis sélectionnez **OK.**
1. Faites défiler jusqu’au bas et sélectionnez **Enregistrer.**

    Votre règle a été créée et les pirates informatiques ne pourront plus envoyer automatiquement des messages.