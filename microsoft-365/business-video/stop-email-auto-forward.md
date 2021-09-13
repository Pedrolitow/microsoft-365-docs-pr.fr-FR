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
- AdminTemplateSet
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment arrêter le forwarding automatique des e-mails en créant une règle de flux de messagerie pour éviter le vol d’informations propriétaires.
ms.openlocfilehash: 5c13e43f29b6d49b13daf4eb0aa6e3d6fd8275ae
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59180595"
---
# <a name="stop-email-auto-forward"></a>Arrêter le courrier électronique à l’avance automatique

## <a name="watch-stop-auto-forwarding-emails"></a>Regardez : arrêter le forwarding automatique des e-mails

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

Si un pirate informatique accède à la boîte aux lettres d’un utilisateur, il peut automatiquement envoyer son courrier électronique à une adresse externe et voler des informations confidentielles. Vous pouvez arrêter cela en créant une règle de flux de messagerie.

## <a name="try-it"></a>Essayez !

1. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365,</a>sélectionnez **Exchange** **,** flux de messagerie  et sous l’onglet Règles, sélectionnez le signe plus et choisissez créer **une règle.**
1. Sélectionnez **plus d’options.** Nommez votre nouvelle règle.
1. Ensuite, ouvrez la drop-down pour **appliquer cette règle si**, sélectionnez **l’expéditeur,** puis **est interne externe**.
1. Sélectionnez **À l’intérieur de** l’organisation, puis **OK**.
1. Choose **add condition**, open the drop-down, select The message **properties**, then include the **message type**.
1. Ouvrez la drop-down sélectionner le type de **message,** **sélectionnez Auto-forward**, puis **OK**.
1. Ouvrez **la liste suivante,** sélectionnez Bloquer le **message,** puis **rejetez le message et incluez une explication.**
1. Entrez le texte du message pour votre explication, puis sélectionnez **OK.**
1. Faites défiler jusqu’au bas et sélectionnez **Enregistrer.**

    Votre règle a été créée et les pirates informatiques ne pourront plus envoyer automatiquement des messages.

## <a name="related-content"></a>Contenu associé

[Ajouter un autre alias de courrier pour un utilisateur](../admin/email/add-another-email-alias-for-a-user.md) (article)\
[Configurer le transfert des e-mails dans Microsoft 365](../admin/email/configure-email-forwarding.md) (article)\
[Rechercher et résoudre les problèmes de remise des e-mails en tant qu’administrateur Office 365 entreprise](/exchange/troubleshoot/email-delivery/email-delivery-issues) (article)