---
title: Configuration et contrôle du transfert de messages externes, du transfert automatique, de l’accès 5.7.520 refusé, de la désactivation du transfert externe, votre administrateur a désactivé le transfert externe, stratégie anti-courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2020
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: .
ms.openlocfilehash: 88c3dae4f5a6786fe4eddea0d5e1c61dda837a87
ms.sourcegitcommit: 5b769f74bcc76ac8d38aad815d1728824783cd9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "45080112"
---
# <a name="configuring-external-email-forwarding-in-office-365"></a>Configuration du transfert de messages électroniques externes dans Office 365

Le transfert externe est contrôlé par la *stratégie anti-courrier indésirable sortant* et l’étendue aux utilisateurs en fonction du paramètre configuré. Actuellement, 3 les paramètres sont pris en charge :

- **Automatique** : dans ce mode, le système est chargé de décider si un message transféré est autorisé ou non.  Il s’agit du mode par défaut et, dans ce mode, le système bloque le transfert externe automatique.

- **Activé – le** transfert externe automatique est autorisé et non restreint.

- **Off** : le transfert externe automatique est désactivé et entraîne une notification d’échec de remise à l’utilisateur final.

Pour plus d’informations sur la configuration de ces paramètres, voir [configurer le filtrage du courrier indésirable sortant dans EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/configure-the-outbound-spam-policy?view=o365-worldwide) .

## <a name="controlling-external-email-forwarding"></a>Contrôle du transfert du courrier électronique externe

En tant qu’administrateur d’une organisation, vous pouvez avoir des exigences en matière d’entreprise pour limiter ou contrôler qui est en mesure de transférer automatiquement des courriers électroniques à l’aide de règles de boîte de réception ou de l’envoi SMTP, en dehors de l’organisation. Le transfert du courrier peut être une fonctionnalité utile, mais peut également présenter un risque grâce à une divulgation potentielle d’informations, même en fournissant des informations aux attaquants qui peuvent être exploités pour attaquer l’organisation ou ses partenaires.

Office 365 n’autorise pas le transfert externe automatique par les règles de boîte de réception ou la configuration des boîtes aux lettres, qui fournit une stratégie par défaut sécurisée. Toutefois, l’administrateur peut modifier ces paramètres pour tous les utilisateurs de l’organisation. Le transfert de messages entre les utilisateurs internes n’est pas affecté par une telle modification.

> [!NOTE]
> La désactivation du transfert automatique vers des adresses externes dans Office 365 est effectuée en phases avec des détails communiqués via des publications du [Centre de messages](https://admin.microsoft.com/Adminportal/Home?source=applauncher&ref=/MessageCenter) . Pour aider les administrateurs à se préparer à ces modifications, demandez-leur de modifier les stratégies à l’avance afin de s’assurer que les utilisateurs ne sont pas perturbés.

Vous trouverez plus d’informations sur les utilisateurs qui utilisent le transfert automatique (règles de boîte de réception ou le transfert SMTP) dans votre organisation dans le [rapport de messages transférés automatiquement](https://docs.microsoft.com/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report?view=o365-worldwide).

## <a name="the-blocked-email-forwarding-message"></a>Message de transfert de courrier électronique bloqué

Lorsqu’un message est détecté comme étant automatiquement transféré et que la stratégie d’organisation *bloque* cette activité, une notification d’échec de **remise (NDR)** est renvoyée à l’utilisateur final. Le rapport indiquera que le message n’a pas été remis. Le rapport de non-remise aura le format suivant : 

`5.7.520 Access Denied – Your administrator has disabled external forwarding – AS(XXXX)`
