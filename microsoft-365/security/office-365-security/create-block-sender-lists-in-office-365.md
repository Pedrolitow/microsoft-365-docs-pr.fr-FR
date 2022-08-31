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
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150s
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour bloquer les messages entrants dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a8abd50deb509564acb6646dc0732bf4a61b6cfd
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67481413"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Créer des listes d’expéditeurs bloqués dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, EOP offre plusieurs façons de bloquer les e-mails des expéditeurs indésirables. Ces options incluent les expéditeurs bloqués Outlook, les listes d’expéditeurs bloqués ou les listes de domaines bloquées dans les stratégies anti-courrier indésirable, les règles de flux de messagerie Exchange (également appelées règles de transport) et la liste de blocage IP (filtrage de connexion). Collectivement, vous pouvez considérer ces options comme des _listes d’expéditeurs bloquées_.

La meilleure méthode pour bloquer les expéditeurs varie en fonction de l’étendue de l’impact. Pour un seul utilisateur, la solution appropriée peut être Outlook Blocked Senders. Pour de nombreux utilisateurs, l’une des autres options serait plus appropriée. Les options suivantes sont classées par étendue d’impact et étendue. La liste passe d’étroite à large, mais _lit les spécificités des recommandations complètes_ .

1. Expéditeurs bloqués Outlook (liste des expéditeurs bloqués stockée dans chaque boîte aux lettres)

2. Listes d’expéditeurs bloquées ou listes de domaines bloqués (stratégies anti-courrier indésirable)

3. Règles de flux de messagerie

4. Liste de blocage IP (filtrage de connexion)

> [!NOTE]
> Bien que vous puissiez utiliser les paramètres de bloc à l’échelle de l’organisation pour traiter les faux négatifs (courrier indésirable manqué), vous devez également envoyer ces messages à Microsoft pour analyse. La gestion des faux négatifs à l’aide de listes de blocs augmente considérablement votre charge administrative. Si vous utilisez des listes de blocs pour détourner le courrier indésirable manqué, vous devez conserver la rubrique [Signaler les messages et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md) au moment de la préparation.

En revanche, vous disposez également de plusieurs options pour toujours autoriser le courrier électronique provenant de sources spécifiques à l’aide de _listes d’expéditeurs fiables_. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Email principes de base des messages

Un message électronique SMTP standard est constitué d’une _enveloppe de message_ et d’un contenu de message. L’enveloppe du message contient les informations nécessaires à la transmission et à la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’_en-tête de message_) et le corps du message. L’enveloppe du message est décrite dans RFC 5321 et l’en-tête de message est décrit dans RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission de message et ne fait pas réellement partie du message.

- L’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) est l’adresse e-mail utilisée dans la transmission SMTP du message. Cette adresse e-mail est généralement enregistrée dans le champ **d’en-tête Chemin d’accès** de retour dans l’en-tête de message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse **e-mail return-path** ). Si le message ne peut pas être remis, il s’agit du destinataire du rapport de non-remise (également appelé NDR ou message de rebond).

- L’adresse `5322.From` de messagerie (également appelée adresse **De** ou expéditeur P2) est l’adresse e-mail dans le champ d’en-tête **From** et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de messagerie.

Souvent, les adresses et `5322.From` les `5321.MailFrom` adresses sont les mêmes (communication de personne à personne). Toutefois, lorsque l’e-mail est envoyé pour le compte d’une autre personne, les adresses peuvent être différentes.

Les listes d’expéditeurs bloquées et les listes de domaines bloquées dans les stratégies anti-courrier indésirable dans EOP inspectent à la fois les adresses et `5322.From` les `5321.MailFrom` adresses. Les expéditeurs bloqués Outlook utilisent uniquement l’adresse `5322.From` .

## <a name="use-outlook-blocked-senders"></a>Utiliser des expéditeurs bloqués Outlook

Quand seul un petit nombre d’utilisateurs ont reçu des e-mails indésirables, les utilisateurs ou administrateurs peuvent ajouter les adresses e-mail de l’expéditeur à la liste Des expéditeurs bloqués dans la boîte aux lettres. Pour obtenir des instructions, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres](configure-junk-email-settings-on-exo-mailboxes.md).

Lorsque les messages sont bloqués en raison de la liste des expéditeurs bloqués d’un utilisateur, le champ **d’en-tête X-Forefront-Antispam-Report** contient la valeur `SFV:BLK`.

> [!NOTE]
> Si les messages indésirables sont des bulletins d’informations provenant d’une source reconnue et reconnaissable, l’annulation de l’abonnement à partir de l’e-mail est une autre option permettant d’empêcher l’utilisateur de recevoir les messages.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Utiliser des listes d’expéditeurs bloquées ou des listes de domaines bloquées

Lorsque plusieurs utilisateurs sont affectés, l’étendue est plus large. La meilleure option suivante est donc de bloquer les listes d’expéditeurs ou les listes de domaines bloquées dans les stratégies anti-courrier indésirable. Les messages des expéditeurs figurant sur les listes sont marqués comme **courrier indésirable** (et non **courrier indésirable à haut niveau de confiance**) et l’action que vous avez configurée pour le verdict de filtre **de courrier indésirable** est effectuée sur le message. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

La limite maximale pour ces listes est d’environ 1 000 entrées.

## <a name="use-mail-flow-rules"></a>Utiliser des règles de flux de messagerie

Si vous devez bloquer les messages envoyés à des utilisateurs spécifiques ou à l’ensemble de l’organisation, vous pouvez utiliser des règles de flux de courrier. Les règles de flux de courrier sont plus flexibles que les listes d’expéditeurs de blocs ou les listes de domaines d’expéditeur bloquées, car elles peuvent également rechercher des mots clés ou d’autres propriétés dans les messages indésirables.

Quelles que soient les conditions ou exceptions que vous utilisez pour identifier les messages, vous configurez l’action pour définir le niveau de confiance du courrier indésirable (SCL) du message sur 9, ce qui marque le message comme courrier **indésirable à haut niveau de confiance**. Pour plus d’informations, consultez [Utiliser des règles de flux de messagerie pour définir la liste de contrôle de contrôle d’accès dans les messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Il est facile de créer des règles _trop_ agressives. Il est donc important d’identifier uniquement les messages que vous souhaitez bloquer à l’aide de critères très spécifiques. Veillez également à activer l’audit sur la règle et à tester les résultats de la règle pour vous assurer que tout fonctionne comme prévu.

## <a name="use-the-ip-block-list"></a>Utiliser la liste de blocs IP

Lorsqu’il n’est pas possible d’utiliser l’une des autres options pour bloquer un expéditeur, _vous devez uniquement_ utiliser la liste de blocage IP dans la stratégie de filtre de connexion. Pour plus d'informations, consultez la rubrique relative à la [configuration de la stratégie de filtre de connexion](configure-the-connection-filter-policy.md). Il est important de limiter au minimum le nombre d’adresses IP bloquées. Il n’est donc _pas_ recommandé de bloquer des plages d’adresses IP entières.

Vous devez _en particulier_ éviter d’ajouter des plages d’adresses IP qui appartiennent à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées, et également vérifier que vous passez en revue la liste des adresses IP bloquées dans le cadre d’une maintenance régulière.
