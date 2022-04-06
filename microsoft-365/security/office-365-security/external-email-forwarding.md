---
title: Configuration et contrôle du forwarding de courrier externe dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2021
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Cet article couvre des rubriques telles que le forwarding de courrier externe, le forwarding automatique, 5.7.520 Accès refusé, la désactivation du forwarding externe, « Votre administrateur a désactivé le forwarding externe » messages, ainsi que la stratégie anti-courrier indésirable sortant.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df0ff9902fe22fd44a0d15f7f01e13e791c7b12
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473604"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Contrôler le forwarding automatique du courrier externe dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

En tant qu’administrateur, vous pouvez avoir des exigences d’entreprise pour restreindre ou contrôler les messages automatiquement transmis à des destinataires externes (destinataires extérieurs à votre organisation). Le forwarding de courrier électronique peut être utile, mais peut également poser un risque de sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou vos partenaires.

Les types de transmission automatique suivants sont disponibles dans Microsoft 365 :

- Les utilisateurs peuvent configurer [des règles](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) de boîte de réception pour transmettre automatiquement des messages à des expéditeurs externes (délibérément ou à la suite d’un compte compromis).
- Les administrateurs peuvent configurer le [forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) de boîte aux lettres (également appelé « _smTP forwarding_ ) pour qu’il puisse automatiquement envoyer des messages à des destinataires externes. L’administrateur peut choisir de simplement envoyer des messages ou de conserver des copies de messages transmis dans la boîte aux lettres.

> [!NOTE]
> Les utilisateurs nationaux dont le transport est automatique à partir de systèmes de messagerie locaux via Microsoft 365 seront soumis aux mêmes contrôles de stratégie que les boîtes aux lettres cloud dans une prochaine mise à jour. Cette mise à jour sera communiquée via le billet du Centre de messages.

Vous pouvez utiliser des stratégies de filtrage du courrier indésirable sortant pour contrôler le forwarding automatique vers des destinataires externes. Trois paramètres sont disponibles :

- **Automatique - Contrôlé par le système** : il s’agit du paramètre par défaut. Ce paramètre est désormais le même que **l’paramètre Off**. Lorsque ce paramètre a été introduit à l’origine, il était équivalent à **On**. Au fil du temps, grâce aux principes de sécurité par [défaut, ce](secure-by-default.md) paramètre a été progressivement modifié pour être **éteint** pour tous les clients. Pour plus d’informations, [consultez ce billet de blog](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888). 
- **On**: Automatic external forwarding is allowed and not restricted.
- **Désactivé** : le forwarding externe automatique est désactivé et entraîne une non-remise (également appelée NDR ou bounce message) à l’expéditeur.

Pour obtenir des instructions sur la configuration de ces paramètres, voir Configurer le filtrage du courrier indésirable [sortant dans EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - La désactivation du redirection automatique désactive les règles de boîte de réception (utilisateurs) ou de boîtes aux lettres (administrateurs) qui redirigent les messages vers des adresses externes.
>
> - Le filtrage automatique des messages entre utilisateurs internes n’est pas affecté par les paramètres des stratégies de filtrage du courrier indésirable sortant.


## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Fonctionnement des paramètres de stratégie de filtrage du courrier indésirable sortant avec d’autres contrôles de transmission automatique du courrier électronique

En tant qu’administrateur, vous avez peut-être déjà configuré d’autres contrôles pour autoriser ou bloquer le forwarding automatique du courrier électronique. Par exemple :

- [Domaines distants permettant](/exchange/mail-flow-best-practices/remote-domains/remote-domains) d’autoriser ou de bloquer le forwarding automatique du courrier électronique vers tout ou partie des domaines externes.
- Conditions et actions dans Exchange règles de flux de [messagerie (également](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) appelées règles de transport) pour détecter et bloquer les messages automatiquement transmis à des destinataires externes.

Lorsqu’un paramètre autorise le forwarding externe, mais qu’un autre paramètre bloque le forwarding externe, le bloc l’emporte généralement. Les exemples sont décrits dans le tableau suivant :

|Scénario|Résultat|
|---|---|
|<ul><li>Vous configurez les paramètres de domaine distant pour autoriser le forwarding automatique.</li><li>Le filtrage automatique du courrier indésirable dans la stratégie de filtrage du courrier indésirable sortant est **éteint**.</li></ul>|Les messages automatiquement transmis aux destinataires des domaines concernés sont bloqués.|
|<ul><li>Vous configurez les paramètres de domaine distant pour autoriser le forwarding automatique.</li><li>Le filtrage automatique du courrier indésirable dans la stratégie de filtrage du courrier indésirable sortant est automatiquement **contrôlé par le système**.</li></ul>|Les messages automatiquement transmis aux destinataires des domaines concernés sont bloqués. <p> Comme décrit précédemment, **Automatique :** contrôlé par le système utilisé pour signifier **«** On » mais le paramètre a changé au fil du temps pour signifier « **Off** » dans toutes les organisations. <p> Pour une clarté absolue, vous devez configurer votre stratégie de filtrage du courrier indésirable sortant sur **On** ou **Off**.|
|<ul><li>Le filtrage automatique du courrier indésirable dans la stratégie de filtrage du courrier indésirable sortant est **sur « On »**</li><li>Vous utilisez des règles de flux de messagerie ou des domaines distants pour bloquer le courrier électronique automatiquement transmis.</li></ul>|Les messages automatiquement transmis aux destinataires concernés sont bloqués par les règles de flux de messagerie ou les domaines distants.|

Vous pouvez utiliser ce comportement (par exemple) pour autoriser le forwarding automatique dans les stratégies de filtrage du courrier indésirable sortant, mais utiliser des domaines distants pour contrôler les domaines externes vers qui les utilisateurs peuvent envoyer des messages.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Comment rechercher des utilisateurs qui sont automatiquement transmis

Vous pouvez voir les informations sur les utilisateurs qui sont automatiquement en cours de forwardage de messages à des destinataires externes dans le rapport des [messages](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) transmis automatiquement pour les comptes basés sur le cloud. Pour les utilisateurs locaux qui sont automatiquement transmis à partir de leur système de messagerie local via Microsoft 365, vous devez créer une règle de flux de messagerie pour suivre ces utilisateurs. Pour obtenir des instructions sur la création d’une règle de flux de messagerie, voir Utiliser le [EAC pour créer une règle de flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Les informations suivantes sont requises pour créer la règle de flux de messagerie dans le Centre d’administration Exchange (EAC) :

- **Appliquez cette règle si** (condition) : **un en-tête de** \> message **correspond à ces modèles de texte**. Notez que vous devrez peut-être cliquer **sur Plus d’options** pour voir cette option.
  - **Nom de l’en-tête** : `X-MS-Exchange-Inbox-Rules-Loop`
  - **Valeur d’en-tête** : `.`

  La condition ressemble à ceci : **l’en-tête « X-MS-Exchange-Inbox-Rules-Loop »** correspond à **« . »**

  Cette condition correspond à n’importe quelle valeur pour l’en-tête.

- (Facultatif) **Pour ce faire** (action), vous pouvez configurer une action facultative. Par exemple, vous pouvez utiliser l’action Modifier les propriétés du **message** définir un en-tête de **message**\>, avec le nom d’en-tête **X-Forwarded** et la valeur **True**. Toutefois, la configuration d’une action n’est pas obligatoire.
- **Définissez cet rue avec le niveau de gravité** sur **la valeur Low**, **Medium** ou **High**. Ce paramètre vous permet d’utiliser le rapport [Exchange règle de transport pour](view-email-security-reports.md#exchange-transport-rule-report) obtenir les détails des utilisateurs qui sont en cours de transport.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="Propriétés de règle de flux de messagerie dans le EAC pour une règle permettant d’identifier les messages transmis" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::


## <a name="blocked-email-forwarding-messages"></a>Messages de courrier bloqués

Lorsqu’un message est détecté comme étant automatiquement transmis et que la stratégie [](configure-the-outbound-spam-policy.md) de filtrage du courrier indésirable  sortant bloque cette activité, le message est renvoyé à l’expéditeur dans une NDR contenant les informations suivantes :

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
