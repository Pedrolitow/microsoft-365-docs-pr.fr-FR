---
title: Notifications d’attaque de point de terminaison
ms.reviewer: ''
description: Les notifications d’attaque de point de terminaison fournissent une recherche proactive des menaces les plus importantes pour votre réseau.
keywords: Notification d’attaque de point de terminaison, repérage des menaces managées, service de détection et de réponse managée (MDR), MTE, Spécialistes des menaces Microsoft, notification d’attaque de point de terminaison, Experts Ask Defender, experts à la demande
search.product: Windows 10
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: fbe9bc01c5006d45a3f3a55c36525294009eb5ba
ms.sourcegitcommit: 4f8200453d347de677461f27eb5a3802ce5cc888
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2022
ms.locfileid: "68542494"
---
# <a name="endpoint-attack-notifications"></a>Notifications d’attaque de point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Cela couvre la chasse aux menaces sur votre service Microsoft Defender pour point de terminaison. Toutefois, si vous souhaitez explorer le service au-delà de votre licence actuelle et chasser de manière proactive les menaces non seulement sur les points de terminaison, mais aussi sur les Office 365, les applications cloud et l’identité, reportez-vous à [Microsoft Defender Experts pour la chasse](/microsoft-365/security/defender/defender-experts-for-hunting). 

Les notifications d’attaque de point de terminaison (précédemment appelées Spécialistes des menaces Microsoft - Notification d’attaque ciblée) permettent de rechercher de manière proactive les menaces les plus importantes pour votre réseau, notamment les intrusions d’adversaires humains, les attaques au clavier ou les attaques avancées telles que le cyber-espionnage. Ces notifications s’affichent sous la forme d’une nouvelle alerte. Le service de chasse managé comprend :

- Surveillance et analyse des menaces, réduction du temps de séjour et des risques pour l’entreprise
- Intelligence artificielle entraînée par hunter pour découvrir et hiérarchiser les attaques connues et inconnues
- Identifier les risques les plus importants, aider les SOC à optimiser le temps et l’énergie
- Étendue de compromission et autant de contexte que possible rapidement pour permettre une réponse SOC rapide


![Capture d’écran de l’alerte Notifications d’attaque de point de terminaison](../../media/defender-endpoint/endpoint-attack-notification-alert.png)

## <a name="apply-for-endpoint-attack-notifications"></a>Appliquer pour les notifications d’attaque de point de terminaison
Si vous êtes un client Microsoft Defender pour point de terminaison, vous pouvez demander des notifications d’attaque de point de terminaison. Accédez aux **notifications** \> d’attaque de point de terminaison des **fonctionnalités** **avancées** \> **générales** \> des **paramètres** \> à appliquer. Une fois accepté, vous bénéficiez des avantages des notifications d’attaque de point de terminaison.

![Comment activer les notifications d’attaque de point de terminaison dans le portail Defender 365](../../media/defender-endpoint/enable-endpoint-attack-notifications.png)

## <a name="receive-endpoint-attack-notifications"></a>Recevoir des notifications d’attaque de point de terminaison
Les notifications d’attaque de point de terminaison sont des alertes qui ont été générées manuellement par le service de chasse managé de Microsoft en fonction d’activités suspectes dans votre environnement. Elles peuvent être affichées par le biais de plusieurs supports :
- File d’attente d’alertes dans le portail Microsoft 365 Defender
- Utilisation de [l’API](../../security/defender-endpoint/get-alerts.md)
- [Table DeviceAlertEvents](../../security/defender-endpoint/advanced-hunting-devicealertevents-table.md) dans la chasse avancée
- Votre e-mail si vous [configurez une règle de notification par e-mail](../../security/defender-endpoint/configure-email-notifications.md)


Les notifications d’attaque de point de terminaison peuvent être identifiées par :
- Avoir une balise nommée **Notification d’attaque de point de terminaison**
- Avoir une source de service de **Microsoft Defender pour point de terminaison** \> **Microsoft Defender Experts**

> [!NOTE]
> Si vous êtes inscrit aux notifications d’attaque de point de terminaison mais que vous ne voyez pas d’alertes du service, cela indique que vous disposez d’une posture de sécurité forte et que vous êtes moins susceptible d’être attaqué.

## <a name="create-an-email-notification-rule"></a>Créer une règle de notification par e-mail
Vous pouvez créer des règles pour envoyer des notifications par e-mail aux destinataires de notification. Pour plus d’informations, consultez [Configurer les notifications d’alerte](configure-email-notifications.md) pour créer, modifier, supprimer ou résoudre les problèmes de notification par e-mail.


## <a name="next-steps"></a>Prochaines étapes
- Pour demander aux experts Defender directement à partir du portail Microsoft Defender pour point de terminaison des informations sur certaines notifications de point de terminaison, [reportez-vous à Ask Defender Experts](../defender-endpoint/experts-on-demand.md).
- Pour chasser de manière proactive les menaces entre les points de terminaison, les Office 365, les applications cloud et l’identité, reportez-vous à [Microsoft Defender Experts pour la chasse](../defender/defender-experts-for-hunting.md).
