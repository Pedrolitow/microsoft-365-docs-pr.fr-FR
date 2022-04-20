---
title: Configuration et contrôle du transfert de courrier externe dans Microsoft 365.
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
description: Cet article couvre des sujets tels que le transfert de courrier externe, le transfert automatique, les messages 5.7.520 Accès refusé, la désactivation du transfert externe, les messages « Votre administrateur a désactivé le transfert externe », ainsi que la stratégie anti-courrier indésirable sortant.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 672e6af3d2aef76a0c944a05c438061861e20060
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971900"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Contrôler le transfert automatique d’e-mails externes dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

En tant qu’administrateur, vous pouvez avoir des exigences de l’entreprise pour restreindre ou contrôler les messages automatiquement transférés aux destinataires externes (destinataires en dehors de votre organisation). Le transfert de courrier électronique peut être utile, mais peut également présenter un risque de sécurité en raison de la divulgation potentielle d’informations. Les attaquants peuvent utiliser ces informations pour attaquer votre organisation ou vos partenaires.

Les types de transfert automatique suivants sont disponibles dans Microsoft 365 :

- Les utilisateurs peuvent configurer [des règles de boîte de réception](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) pour transférer automatiquement les messages aux expéditeurs externes (délibérément ou à la suite d’un compte compromis).
- Les administrateurs peuvent configurer le [transfert de boîte aux lettres](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (également appelé _transfert SMTP_) pour transférer automatiquement les messages aux destinataires externes. L’administrateur peut choisir s’il faut simplement transférer des messages ou conserver des copies des messages transférés dans la boîte aux lettres.

> [!NOTE]
> Les utilisateurs disposant d’un transfert automatique à partir de systèmes de messagerie locaux via Microsoft 365 seront soumis aux mêmes contrôles de stratégie que les boîtes aux lettres cloud dans une prochaine mise à jour. Cette mise à jour sera communiquée via le billet du Centre de messages.

Vous pouvez utiliser des stratégies de filtre de courrier indésirable sortant pour contrôler le transfert automatique vers des destinataires externes. Trois paramètres sont disponibles :

- **Automatique - Contrôlé par le système** : il s’agit du paramètre par défaut. Ce paramètre est désormais identique à **Off**. Lorsque ce paramètre a été introduit à l’origine, il était équivalent à **On**. Au fil du temps, grâce aux principes de [sécurité par défaut](secure-by-default.md), ce paramètre a été progressivement remplacé par **Désactivé** pour tous les clients. Pour plus d’informations, consultez [ce billet de blog](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888).
- **Activé** : le transfert externe automatique est autorisé et non restreint.
- **Désactivé** : le transfert externe automatique est désactivé et génère un rapport de non-remise (également appelé NDR ou message de rebond) à l’expéditeur.

Pour obtenir des instructions sur la configuration de ces paramètres, consultez [Configurer le filtrage de courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - La désactivation du transfert automatique désactive les règles de boîte de réception (utilisateurs) ou le transfert de boîte aux lettres (administrateurs) qui redirigent les messages vers des adresses externes.
> - Le transfert automatique des messages entre les utilisateurs internes n’est pas affecté par les paramètres des stratégies de filtrage du courrier indésirable sortant.

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Fonctionnement des paramètres de stratégie de filtrage du courrier indésirable sortant avec d’autres contrôles de transfert automatique de courrier électronique

En tant qu’administrateur, vous avez peut-être déjà configuré d’autres contrôles pour autoriser ou bloquer le transfert automatique de courrier électronique. Par exemple :

- [Domaines distants](/exchange/mail-flow-best-practices/remote-domains/remote-domains) pour autoriser ou bloquer le transfert automatique d’e-mails vers certains ou tous les domaines externes.
- Conditions et actions dans Exchange [règles de flux de courrier](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) pour détecter et bloquer automatiquement les messages transférés aux destinataires externes.

Lorsqu’un paramètre autorise le transfert externe, mais qu’un autre paramètre bloque le transfert externe, le bloc l’emporte généralement. Les exemples sont décrits dans le tableau suivant :

|Scénario|Résultat|
|---|---|
|<ul><li>Vous configurez les paramètres de domaine distant pour autoriser le transfert automatique.</li><li>Le transfert automatique dans la stratégie de filtrage du courrier indésirable sortant est défini sur **Désactivé**.</li></ul>|Les messages automatiquement transférés aux destinataires dans les domaines affectés sont bloqués.|
|<ul><li>Vous configurez les paramètres de domaine distant pour autoriser le transfert automatique.</li><li>Le transfert automatique dans la stratégie de filtrage du courrier indésirable sortant est défini sur **Automatique - Contrôlé par le système**.</li></ul>|Les messages automatiquement transférés aux destinataires dans les domaines affectés sont bloqués. <p> Comme décrit précédemment, **Automatique - Contrôlé par le système** utilisé pour signifier **Activé**, mais le paramètre a changé au fil du temps pour signifier **Désactivé** dans toutes les organisations. <p> Pour une clarté absolue, vous devez configurer votre stratégie de filtrage du courrier indésirable sortant sur **Activé** ou **Désactivé**.|
|<ul><li>Le transfert automatique dans la stratégie de filtrage du courrier indésirable sortant est défini **sur Activé**</li><li>Vous utilisez des règles de flux de messagerie ou des domaines distants pour bloquer les e-mails transférés automatiquement.</li></ul>|Les messages transférés automatiquement aux destinataires affectés sont bloqués par des règles de flux de messagerie ou des domaines distants.|

Vous pouvez utiliser ce comportement (par exemple) pour autoriser le transfert automatique dans les stratégies de filtre de courrier indésirable sortant, mais utiliser des domaines distants pour contrôler les domaines externes auxquels les utilisateurs peuvent transférer des messages.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Comment rechercher des utilisateurs qui sont automatiquement transférés

Vous pouvez voir des informations sur les utilisateurs qui transfèrent automatiquement des messages à des destinataires externes dans le [rapport des messages transférés automatiquement](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) pour les comptes cloud. Pour les utilisateurs locaux qui transfèrent automatiquement leur système de messagerie local via Microsoft 365, vous devez créer une règle de flux de courrier pour suivre ces utilisateurs. Pour obtenir des instructions sur la création d’une règle de flux de messagerie, consultez [Utiliser le CAE pour créer une règle de flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Les informations suivantes sont requises pour créer la règle de flux de messagerie dans le centre d’administration Exchange (EAC) :

- **Appliquez cette règle si** (condition) : **un en-tête** \> de message **correspond à ces modèles de texte**. Notez que vous devrez peut-être cliquer sur **Autres options** pour voir cette option.
  - **Nom de l’en-tête** : `X-MS-Exchange-Inbox-Rules-Loop`
  - **Valeur d’en-tête** : `.`

  La condition ressemble à ceci : **l’en-tête « X-MS-Exchange-Inbox-Rules-Loop »** correspond à **« . »**

  Cette condition correspond à n’importe quelle valeur de l’en-tête.

- (Facultatif) **Procédez comme suit** (action) : vous pouvez configurer une action facultative. Par exemple, vous pouvez utiliser l’action **Modifier les propriétés** \> du message **pour définir un en-tête de message**, avec le nom **d’en-tête X-Forwarded** et la valeur **True**. Toutefois, la configuration d’une action n’est pas nécessaire.
- Définissez **Auditer cette rue avec le niveau de gravité** sur la valeur **Faible**, **Moyenne** ou **Élevée**. Ce paramètre vous permet d’utiliser le [rapport de règle de transport Exchange](view-email-security-reports.md#exchange-transport-rule-report) pour obtenir des détails sur les utilisateurs qui sont transférés.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="Propriétés de la règle de flux de messagerie dans le CAE pour une règle permettant d’identifier les messages transférés" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::

## <a name="blocked-email-forwarding-messages"></a>Messages de transfert de courrier bloqués

Lorsqu’un message est détecté comme transféré automatiquement et que la stratégie de [filtrage du courrier indésirable sortant](configure-the-outbound-spam-policy.md) *bloque* cette activité, le message est renvoyé à l’expéditeur dans une DNR qui contient les informations suivantes :

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
