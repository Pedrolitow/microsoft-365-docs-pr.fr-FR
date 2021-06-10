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
description: Découvrez comment arrêter le forwarding automatique des e-mails en créant une règle de flux de messagerie pour éviter le vol d’informations propriétaires.
ms.openlocfilehash: 82e4c80b0edc501889e0fc4dc28f1ec1ad703568
ms.sourcegitcommit: a05f61a291eb4595fa9313757a3815b7f217681d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "52706473"
---
# <a name="stop-email-auto-forward"></a>Arrêter le courrier électronique à l’avance automatique

## <a name="watch-stop-auto-forwarding-emails"></a>Regardez : arrêter le forwarding automatique des e-mails

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2W6kS?autoplay=false]

Si un pirate informatique accède à la boîte aux lettres d’un utilisateur, il peut automatiquement le faire accéder à une adresse extérieure et voler des informations confidentielles. Vous pouvez arrêter cela en créant une règle de flux de messagerie.

## <a name="try-it"></a>Essayez !

1. Dans le Microsoft 365 d’administration, sélectionnez **Exchange** **,** flux  de messagerie et sous l’onglet Règles, sélectionnez le signe plus et choisissez créer **une règle.**
1. Sélectionnez **plus d’options.** Nommez votre nouvelle règle.
1. Ensuite, ouvrez la drop-down pour **appliquer cette règle si**, sélectionnez **l’expéditeur,** puis **est interne externe**.
1. Sélectionnez **À l’intérieur de** l’organisation, puis **OK**.
1. Choose **add condition**, open the drop-down, select The message **properties**, then include the **message type**.
1. Ouvrez la drop-down sélectionner le type de **message,** sélectionnez **Auto-forward**, puis **OK**.
1. Ouvrez **la liste suivante,** sélectionnez Bloquer le **message,** puis **rejetez le message et incluez une explication.**
1. Entrez le texte du message pour votre explication, puis sélectionnez **OK.**
1. Faites défiler jusqu’au bas et sélectionnez **Enregistrer.**

    Votre règle a été créée et les pirates informatiques ne pourront plus envoyer automatiquement des messages.

## <a name="related-content"></a>Contenu associé

[Ajouter un autre alias de courrier pour un utilisateur](../admin/email/add-another-email-alias-for-a-user.md) (article)\
[Configurer le transfert des e-mails dans Microsoft 365](../admin/email/configure-email-forwarding.md) (article)\
[Rechercher et résoudre les problèmes de remise des e-mails en tant qu’administrateur Office 365 entreprise](/exchange/troubleshoot/email-delivery/email-delivery-issues) (article)