---
title: Configuration et contrôle du transfert de messages externes, du transfert automatique, de l’accès 5.7.520 refusé, de la désactivation du transfert externe, votre administrateur a désactivé le transfert externe, stratégie anti-courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: .
ms.openlocfilehash: 76cd560c3b97bb67d25d2e4ff2c219669c3d4f0d
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658880"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Contrôler le transfert automatique du courrier électronique externe dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

En tant qu’administrateur, vous pouvez être amené à limiter ou contrôler automatiquement les messages transférés à des destinataires externes (destinataires extérieurs à votre organisation). Le transfert du courrier peut être utile, mais peut également poser un risque de sécurité en raison de la divulgation potentielle des informations. Les agresseurs peuvent utiliser ces informations pour attaquer votre organisation ou vos partenaires.

Les types de transferts automatiques suivants sont disponibles dans Microsoft 365 :

- Les utilisateurs peuvent configurer des [règles de boîte de réception](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) pour transférer automatiquement des messages vers des expéditeurs externes (délibérément ou en raison d’un compte compromis).

- Les administrateurs peuvent configurer le transfert des [boîtes aux lettres](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (également appelé _transfert SMTP_) pour transférer automatiquement les messages vers des destinataires externes. L’administrateur peut choisir de transférer simplement les messages ou de conserver des copies des messages transférés dans la boîte aux lettres.

Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le transfert automatique vers des destinataires externes. Trois paramètres sont disponibles :

- **Automatique**: le transfert externe automatique est bloqué. Le transfert automatique interne des messages continuera à fonctionner. Il s’agit du paramètre par défaut.
- **Activé : le** transfert externe automatique est autorisé et non restreint.
- **Off**: le transfert externe automatique est désactivé et entraîne une notification d’échec de remise (également appelée notification de non-remise) à l’expéditeur.

Pour obtenir des instructions sur la configuration de ces paramètres, consultez la rubrique [configuration du filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - La désactivation du transfert automatique désactive les règles de boîte de réception (utilisateurs) ou le transfert des boîtes aux lettres (administrateurs) qui redirigent les messages vers des adresses externes.
>
> - Le transfert automatique des messages entre les utilisateurs internes n’est pas affecté par les paramètres des stratégies de filtrage du courrier indésirable sortant.
>
> - Vous pouvez afficher des informations sur les utilisateurs qui transfèrent automatiquement des messages à des destinataires externes dans le [rapport de messages transférés](mfi-auto-forwarded-messages-report.md)automatiquement.

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Fonctionnement des paramètres de stratégie de filtrage du courrier indésirable sortant avec d’autres contrôles de transfert automatique du courrier

En tant qu’administrateur, vous avez peut-être déjà configuré d’autres contrôles pour autoriser ou bloquer le transfert automatique du courrier électronique. Par exemple :

- [Domaines distants](https://docs.microsoft.com/exchange/mail-flow-best-practices/remote-domains/remote-domains) pour autoriser ou bloquer le transfert du courrier automatique vers certains ou tous les domaines externes.

- Conditions et actions dans les [règles de flux de messagerie](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Exchange (également appelées règles de transport) pour détecter et bloquer les messages transférés automatiquement vers des destinataires externes.

Les paramètres des domaines distants et les règles de flux de messagerie sont indépendants des paramètres des stratégies de filtrage du courrier indésirable sortant. Par exemple :

- Vous autorisez le transfert automatique pour un domaine distant, mais vous bloquez le transfert automatique dans les stratégies de filtrage du courrier indésirable sortant. Dans cet exemple, les messages transférés automatiquement sont bloqués.

- Vous autorisez le transfert automatique dans les stratégies de filtrage du courrier indésirable sortant, mais vous utilisez des règles de flux de messagerie ou des paramètres de domaine distant pour bloquer le transfert automatique du courrier électronique. Dans cet exemple, les règles de flux de messagerie ou les paramètres de domaine distant bloquent les messages transférés automatiquement.

Cette indépendance de fonctionnalité vous permet (par exemple) d’autoriser le transfert automatique dans les stratégies de filtrage du courrier indésirable sortant, mais d’utiliser des domaines distants pour contrôler les domaines externes vers lesquels les utilisateurs peuvent transférer des messages.

## <a name="the-blocked-email-forwarding-message"></a>Message de transfert de courrier électronique bloqué

Lorsqu’un message est détecté comme étant automatiquement transféré et que la stratégie d’organisation *bloque* cette activité, le message est renvoyé à l’expéditeur dans une notification d’inactivité contenant les informations suivantes :

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
