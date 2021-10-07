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
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: .
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e68526f4a7e83295d8d0748651b07e35cfdaf5c6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60176546"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Contrôler le forwarding automatique du courrier externe dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

En tant qu’administrateur, vous pouvez avoir des exigences d’entreprise pour restreindre ou contrôler les messages automatiquement transmis à des destinataires externes (destinataires extérieurs à votre organisation). Le forwarding de courrier électronique peut être utile, mais peut également poser un risque de sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou vos partenaires.

Les types de transmission automatique suivants sont disponibles dans Microsoft 365 :

- Les utilisateurs peuvent configurer [des règles](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) de boîte de réception pour transmettre automatiquement des messages à des expéditeurs externes (délibérément ou à la suite d’un compte compromis).
- Les administrateurs peuvent configurer le [forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) de boîte aux lettres (également appelé « _smTP forwarding_) pour qu’il puisse automatiquement envoyer des messages à des destinataires externes. L’administrateur peut choisir de simplement envoyer des messages ou de conserver des copies de messages transmis dans la boîte aux lettres.

> [!NOTE]
> Les utilisateurs nationaux dont le transport est automatique à partir de systèmes de messagerie locaux via Microsoft 365 seront soumis aux mêmes contrôles de stratégie que les boîtes aux lettres cloud dans une prochaine mise à jour. Cette mise à jour sera communiquée via le billet du Centre de messages.

Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le forwarding automatique vers des destinataires externes. Trois paramètres sont disponibles :

- **Automatique - Contrôlé par le système**: le transport externe automatique est bloqué. Le forwarding automatique interne des messages continuera de fonctionner. Il s’agit du paramètre par défaut.
- **On**: le forwarding externe automatique est autorisé et non restreint.
- **Désactivé**: le forwarding externe automatique est désactivé et entraîne une non-remise (également appelée une NDR ou une non-remise) à l’expéditeur.

Pour obtenir des instructions sur la configuration de ces paramètres, voir Configurer le filtrage du courrier indésirable sortant [dans EOP.](configure-the-outbound-spam-policy.md)

> [!NOTE]
>
> - La désactivation du redirection automatique désactive les règles de boîte de réception (utilisateurs) ou de boîtes aux lettres (administrateurs) qui redirigent les messages vers des adresses externes.
>
> - Le filtrage automatique des messages entre utilisateurs internes n’est pas affecté par les paramètres des stratégies de filtrage du courrier indésirable sortant.


## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Fonctionnement des paramètres de stratégie de filtrage du courrier indésirable sortant avec d’autres contrôles de transmission automatique du courrier électronique

En tant qu’administrateur, vous avez peut-être déjà configuré d’autres contrôles pour autoriser ou bloquer le forwarding automatique du courrier électronique. Par exemple :

- [Domaines distants permettant](/exchange/mail-flow-best-practices/remote-domains/remote-domains) d’autoriser ou de bloquer le forwarding automatique du courrier électronique vers tout ou partie des domaines externes.
- Conditions et actions dans Exchange règles de [flux](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) de messagerie (également appelées règles de transport) pour détecter et bloquer les messages automatiquement transmis à des destinataires externes.

Les paramètres de domaine distant et les règles de flux de messagerie sont indépendants des paramètres des stratégies de filtrage du courrier indésirable sortant. Par exemple :

- Vous autorisez le forwarding automatique pour un domaine distant, mais vous bloquez le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant. Dans cet exemple, les messages automatiquement transmis sont bloqués.
- Vous autorisez le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant, mais vous utilisez des règles de flux de messagerie ou des paramètres de domaine distant pour bloquer le courrier électronique automatiquement transmis. Dans cet exemple, les règles de flux de messagerie ou les paramètres de domaine distant bloquent les messages automatiquement transmis.

Cette indépendance de fonctionnalité vous permet (par exemple) d’autoriser le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant, mais d’utiliser des domaines distants pour contrôler les domaines externes vers qui les utilisateurs peuvent envoyer des messages.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Comment trouver des utilisateurs qui sont automatiquement transmis

Vous pouvez voir les informations sur les utilisateurs qui sont automatiquement en cours de forwardage de messages à des destinataires externes dans le rapport des [messages](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) transmis automatiquement pour les comptes basés sur le cloud. Pour les utilisateurs locaux qui sont automatiquement transmis à partir de leur système de messagerie local via Microsoft 365, vous devez créer une règle de flux de messagerie pour suivre ces utilisateurs. Pour obtenir des instructions sur la création d’une règle de flux de messagerie, voir Utiliser le [EAC pour créer une règle de flux de messagerie.](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule)

Les informations suivantes sont requises pour créer la règle de flux de messagerie dans le Centre d’administration Exchange (EAC) :

- **Appliquez cette règle si** (condition) : **un en-tête de message** correspond à ces \> **modèles de texte.** Notez que vous devrez peut-être cliquer **sur Plus d’options** pour voir cette option.
  - **Nom de l’en-tête**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Valeur d’en-tête**: `.`

  La condition ressemble à ceci : **l’en-tête « X-MS-Exchange-Inbox-Rules-Loop »** correspond à **« . »**

  Cette condition correspond à n’importe quelle valeur pour l’en-tête.

- (Facultatif) **Pour ce faire** (action), vous pouvez configurer une action facultative. Par exemple, vous pouvez utiliser l’action Modifier les propriétés du message définir un en-tête de **message,** avec le nom d’en-tête \>  **X-Forwarded** et la valeur **True**. Toutefois, la configuration d’une action n’est pas obligatoire.
- Définissez **cet rue avec le niveau de gravité** sur la valeur **Low,** **Medium** ou **High**. Ce paramètre vous permet d’utiliser le rapport [Exchange de transport pour](view-email-security-reports.md#exchange-transport-rule-report) obtenir les détails des utilisateurs qui sont en cours de transport.

![Propriétés de règle de flux de messagerie dans le EAC pour une règle permettant d’identifier les messages transmis.](../../media/mail-flow-rule-for-forwarded-messages.png)

## <a name="blocked-email-forwarding-messages"></a>Messages de courrier électronique bloqués

Lorsqu’un message est détecté comme étant [](configure-the-outbound-spam-policy.md) automatiquement transmis et  que la stratégie de filtrage du courrier indésirable sortant bloque cette activité, le message est renvoyé à l’expéditeur dans une NDR contenant les informations suivantes :

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
