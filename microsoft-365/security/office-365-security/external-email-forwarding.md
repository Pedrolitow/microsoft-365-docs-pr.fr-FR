---
title: Configuration et contrôle du forwarding de courrier externe, transmission automatique, 5.7.520 Accès refusé, désactivation du forwarding externe, Votre administrateur a désactivé le forwarding externe, stratégie anti-courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: .
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f42da077ca84341824fad01fcb23eae976336a1
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204205"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Contrôler le forwarding automatique du courrier externe dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

En tant qu’administrateur, vous pouvez avoir des exigences d’entreprise pour restreindre ou contrôler les messages automatiquement transmis à des destinataires externes (destinataires extérieurs à votre organisation). Le forwarding de courrier électronique peut être utile, mais peut également poser un risque de sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou vos partenaires.


Les types de transmission automatique suivants sont disponibles dans Microsoft 365 :

- Les utilisateurs peuvent configurer [des règles](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) de boîte de réception pour transmettre automatiquement des messages à des expéditeurs externes (délibérément ou à la suite d’un compte compromis).

- Les administrateurs peuvent configurer le [forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) de boîte aux lettres (également appelé « _smTP forwarding_) pour qu’il puisse automatiquement envoyer des messages à des destinataires externes. L’administrateur peut choisir de simplement envoyer des messages ou de conserver des copies de messages transmis dans la boîte aux lettres.

Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le forwarding automatique vers des destinataires externes. Trois paramètres sont disponibles :

- **Automatique**: le forwarding externe automatique est bloqué. Le forwarding automatique interne des messages continuera de fonctionner. Il s’agit du paramètre par défaut.
- **On**: le forwarding externe automatique est autorisé et non restreint.
- **Désactivé**: le forwarding externe automatique est désactivé et entraîne une non-remise (également appelée une NDR ou une non-remise) à l’expéditeur.

Pour obtenir des instructions sur la configuration de ces paramètres, voir Configurer le filtrage du courrier indésirable sortant [dans EOP.](configure-the-outbound-spam-policy.md)

> [!NOTE]
>
> - La désactivation du redirection automatique désactive les règles de boîte de réception (utilisateurs) ou de boîtes aux lettres (administrateurs) qui redirigent les messages vers des adresses externes.
>
> - Le filtrage automatique des messages entre utilisateurs internes n’est pas affecté par les paramètres des stratégies de filtrage du courrier indésirable sortant.
>
> - Vous pouvez voir les informations sur les utilisateurs qui sont automatiquement en cours de forwardage des messages à des destinataires externes dans le rapport de [messages transmis automatiquement.](mfi-auto-forwarded-messages-report.md)

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Fonctionnement des paramètres de stratégie de filtrage du courrier indésirable sortant avec d’autres contrôles de transmission automatique du courrier électronique

En tant qu’administrateur, vous avez peut-être déjà configuré d’autres contrôles pour autoriser ou bloquer le forwarding automatique du courrier électronique. Par exemple :

- [Domaines distants permettant](/exchange/mail-flow-best-practices/remote-domains/remote-domains) d’autoriser ou de bloquer le forwarding automatique du courrier électronique vers tout ou partie des domaines externes.

- Conditions et actions dans les règles de flux de messagerie [Exchange](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) pour détecter et bloquer les messages automatiquement transmis à des destinataires externes.

Les paramètres de domaine distant et les règles de flux de messagerie sont indépendants des paramètres des stratégies de filtrage du courrier indésirable sortant. Par exemple :

- Vous autorisez le forwarding automatique pour un domaine distant, mais vous bloquez le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant. Dans cet exemple, les messages automatiquement transmis sont bloqués.

- Vous autorisez le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant, mais vous utilisez des règles de flux de messagerie ou des paramètres de domaine distant pour bloquer le courrier électronique automatiquement transmis. Dans cet exemple, les règles de flux de messagerie ou les paramètres de domaine distant bloquent les messages automatiquement transmis.

Cette indépendance de fonctionnalité vous permet (par exemple) d’autoriser le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant, mais d’utiliser des domaines distants pour contrôler les domaines externes vers qui les utilisateurs peuvent envoyer des messages.

## <a name="blocked-email-forwarding-messages"></a>Messages de courrier bloqués

Lorsqu’un message est détecté comme étant [](configure-the-outbound-spam-policy.md) automatiquement transmis et  que la stratégie de filtrage du courrier indésirable sortant bloque cette activité, le message est renvoyé à l’expéditeur dans une NDR contenant les informations suivantes :

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`