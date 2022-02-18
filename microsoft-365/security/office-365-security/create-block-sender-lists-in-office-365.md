---
title: Créer des listes d’expéditeurs bloqués
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150s
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour bloquer les messages entrants dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 71f6312f160a445c184a52f96493360af8b9a360
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2022
ms.locfileid: "62896086"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Créer des listes d’expéditeurs bloqués dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP offre plusieurs façons de bloquer les messages électroniques provenant d’expéditeurs indésirables. Ces options incluent les Outlook expéditeurs bloqués, les listes d’expéditeurs bloqués ou les listes de domaines bloqués dans les stratégies anti-courrier indésirable, les règles de flux de messagerie Exchange (également appelées règles de transport) et la liste d’adresses IP bloquées (filtrage des connexions). Collectivement, vous pouvez voir ces options comme des _listes d’expéditeurs bloqués_.

La meilleure méthode pour bloquer les expéditeurs varie selon l’étendue de l’impact. Pour un utilisateur unique, la solution appropriée peut être Outlook expéditeurs bloqués. Pour de nombreux utilisateurs, l’une des autres options serait plus appropriée. Les options suivantes sont classées par étendue et largeur d’impact. La liste passe de étroite à large, mais _lit les spécificités_ pour obtenir des recommandations complètes.

1. Outlook expéditeurs bloqués (liste des expéditeurs bloqués stockée dans chaque boîte aux lettres)

2. Listes d’expéditeurs bloqués ou listes de domaines bloqués (stratégies anti-courrier indésirable)

3. Règles de flux de messagerie

4. Liste d’adresses IP bloqués (filtrage des connexions)

> [!NOTE]
> Bien que vous pouvez utiliser les paramètres de blocage à l’échelle de l’organisation pour traiter les faux négatifs (courrier indésirable manqué), vous devez également envoyer ces messages à Microsoft pour analyse. La gestion des faux négatifs à l’aide de listes de blocage augmente considérablement votre charge administrative. Si vous utilisez des listes d’adresses de blocage pour éviter les courriers indésirables manqués, vous devez maintenir la rubrique [Signaler les messages](report-junk-email-messages-to-microsoft.md) et les fichiers à Microsoft.

En revanche, vous avez également plusieurs options pour toujours autoriser le courrier électronique provenant de sources spécifiques à l’aide de _listes d’expéditeurs fiables_. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Informations de base sur les messages électroniques

Un message électronique SMTP standard est constitué d’une _enveloppe de message_ et d’un contenu de message. L’enveloppe de message contient les informations requises pour transmettre et remettre le message entre des serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’_en-tête de message_) et le corps du message. L’enveloppe du message est décrite dans la RFC 5321 et l’en-tête du message est décrit dans la RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission du message et ne fait pas réellement partie du message.

- L’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) est l’adresse de messagerie utilisée dans la transmission SMTP du message. Cette adresse de messagerie est généralement enregistrée dans le champ **d’en-tête Return-Path dans l’en-tête** du message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse de messagerie **Return-Path** ). Si le message ne peut pas être remis, il s’agit du destinataire de la non-remise (également appelée NDR ou message de non-remise).

- L’adresse e-mail  (également appelée adresse de provenance ou expéditeur P2) est l’adresse de messagerie dans le champ d’en-tête **De** et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de messagerie.`5322.From`

Souvent, les adresses `5321.MailFrom` `5322.From` et les adresses sont identiques (communication de personne à personne). Toutefois, lorsque le courrier électronique est envoyé pour le compte d’une autre personne, les adresses peuvent être différentes.

Les listes d’expéditeurs bloqués et les listes de domaines bloqués dans les stratégies anti-courrier indésirable dans EOP inspectent les adresses `5321.MailFrom` et les `5322.From` adresses. Outlook expéditeurs bloqués utilise uniquement l’adresse`5322.From`.

## <a name="use-outlook-blocked-senders"></a>Utiliser Outlook expéditeurs bloqués

Lorsque seul un petit nombre d’utilisateurs a reçu des messages indésirables, les utilisateurs ou les administrateurs peuvent ajouter les adresses de messagerie de l’expéditeur à la liste des expéditeurs bloqués dans la boîte aux lettres. Pour obtenir des instructions, voir [Configurer les paramètres de courrier indésirable Exchange Online boîtes aux lettres.](configure-junk-email-settings-on-exo-mailboxes.md)

Lorsque les messages sont correctement bloqués en raison de la liste des expéditeurs bloqués d’un utilisateur, le champ **d’en-tête X-Forefront-Antispam-Report** contient la valeur `SFV:BLK`.

> [!NOTE]
> Si les messages indésirables sont des bulletins d’informations provenant d’une source fiable et reconnaissable, l’abonnement à partir du courrier électronique est une autre option pour empêcher l’utilisateur de recevoir les messages.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Utiliser des listes d’expéditeurs bloqués ou des listes de domaines bloqués

Lorsque plusieurs utilisateurs sont affectés, l’étendue est plus large, de sorte que la meilleure option suivante consiste à bloquer les listes d’expéditeurs ou les listes de domaines bloqués dans les stratégies anti-courrier indésirable. Les messages provenant d’expéditeurs sur les listes sont marqués comme courrier **indésirable (et** non comme courrier indésirable à niveau de confiance  **élevé) et** l’action que vous avez configurée pour le verdict de filtrage du courrier indésirable est prise sur le message. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

La limite maximale pour ces listes est d’environ 1 000 entrées.

## <a name="use-mail-flow-rules"></a>Utiliser des règles de flux de messagerie

Si vous devez bloquer les messages envoyés à des utilisateurs spécifiques ou à l’ensemble de l’organisation, vous pouvez utiliser des règles de flux de messagerie. Les règles de flux de messagerie sont plus flexibles que le blocage des listes d’expéditeurs ou des listes de domaines d’expéditeurs bloqués, car elles peuvent également rechercher des mots clés ou d’autres propriétés dans les messages indésirables.

Quelles que soient les conditions ou les exceptions que vous utilisez pour identifier les messages, vous configurez l’action pour définir le niveau de confiance du courrier indésirable (SCL) du message sur 9, ce qui marque le message comme courrier indésirable à niveau de confiance **élevé.** Pour plus d’informations, voir [Utiliser des règles de flux de messagerie pour définir le SCL dans les messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Il est facile de créer des règles trop agressives. Il est donc important d’identifier uniquement les messages que vous souhaitez bloquer à l’aide de critères très spécifiques. Veillez également à activer l’audit sur la règle et à tester les résultats de la règle pour vous assurer que tout fonctionne comme prévu.

## <a name="use-the-ip-block-list"></a>Utiliser la liste d’adresses IP bloqués

Lorsqu’il n’est pas possible d’utiliser l’une des autres options pour bloquer un _expéditeur, vous_ devez utiliser la liste d’adresses IP bloqués dans la stratégie de filtrage des connexions. Pour plus d'informations, consultez la rubrique relative à la [configuration de la stratégie de filtre de connexion](configure-the-connection-filter-policy.md). Il est important de conserver un nombre minimal d’adresses IP bloquées, de sorte que le blocage de plages d’adresses IP entières _n’est pas_ recommandé.

Vous devez  particulièrement éviter d’ajouter des plages d’adresses IP appartenant à des services grand public (par exemple, outlook.com) ou des infrastructures partagées, et veillez également à consulter la liste des adresses IP bloquées dans le cadre d’une maintenance régulière.
