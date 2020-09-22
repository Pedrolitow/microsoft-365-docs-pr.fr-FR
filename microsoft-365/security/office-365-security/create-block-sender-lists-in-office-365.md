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
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150s
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour bloquer les messages entrants dans Exchange Online Protection (EOP).
ms.openlocfilehash: 7894a6cfe665539fa8c00f5911c4a588b9cf7ebc
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203190"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Créer des listes d’expéditeurs bloqués dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, EOP offre plusieurs méthodes de blocage des messages provenant d’expéditeurs indésirables. Ces options incluent les expéditeurs bloqués Outlook, les listes d’expéditeurs bloqués ou les listes de domaines bloqués dans les stratégies de blocage du courrier indésirable, les règles de flux de messagerie Exchange (également appelées règles de transport) et la liste d’adresses IP bloquées (filtrage des connexions). Collectivement, ces options peuvent être considérées comme des _listes d’expéditeurs bloqués_.

La meilleure méthode pour bloquer les expéditeurs varie en fonction de l’étendue de l’impact. Pour un seul utilisateur, la bonne solution peut être des expéditeurs bloqués Outlook. Pour de nombreux utilisateurs, l’une des autres options est plus appropriée. Les options suivantes sont classées par portée et étendue d’impact. La liste passe de étroite à large, mais *lit les détails* pour obtenir des recommandations complètes.

1. Expéditeurs bloqués Outlook (la liste des expéditeurs bloqués qui est stockée dans chaque boîte aux lettres)

2. Listes des expéditeurs bloqués ou des listes de domaines bloqués (stratégies anti-courrier indésirable)

3. Règles de flux de messagerie

4. Liste d’adresses IP bloquées (filtrage des connexions)

> [!NOTE]
> Bien que vous puissiez utiliser les paramètres de blocage à l’échelle de l’Organisation pour résoudre les faux négatifs (courrier indésirable manqué), vous devez également envoyer ces messages à Microsoft pour analyse. La gestion des faux négatifs à l’aide de listes rouges augmente considérablement votre charge administrative. Si vous utilisez des listes rouges pour déviation du courrier indésirable manqué, vous devez conserver la rubrique [signaler les messages et les fichiers à Microsoft](report-junk-email-messages-to-microsoft.md) à l’adresse.

En revanche, vous disposez également de plusieurs options pour toujours autoriser les messages provenant de sources spécifiques en utilisant des _listes d’expéditeurs approuvés_. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Notions de base sur les messages électroniques

Un message électronique SMTP standard est constitué d’une *enveloppe de message* et d’un contenu de message. L’enveloppe de message contient les informations requises pour la transmission et la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’*en-tête de message*) et le corps du message. L’enveloppe de message est décrite dans la norme RFC 5321 et l’en-tête de message est décrit dans la spécification RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission des messages, et elle ne fait pas partie du message.

- L' `5321.MailFrom` adresse (également appelée adresse **de messagerie de** l’expéditeur, expéditeur P1 ou expéditeur de l’enveloppe) est l’adresse de messagerie utilisée dans la transmission SMTP du message. Cette adresse de messagerie est généralement enregistrée dans le champ d’en-tête de **retour** de l’en-tête du message (bien que l’expéditeur ait la possibilité de désigner une autre adresse de messagerie de **chemin d’accès** ). Si le message ne peut pas être remis, il s’agit du destinataire de la notification d’échec de remise (également appelée notification de non-remise).

- Le `5322.From` (également appelé l’adresse **de** l’expéditeur ou l’expéditeur P2) est l’adresse de messagerie dans le champ de l’en-tête **de** , et est l’adresse de messagerie de l’expéditeur affichée dans les clients de messagerie.

Fréquemment, les `5321.MailFrom` `5322.From` adresses et sont identiques (communication de personne à personne). Toutefois, lorsque le courrier électronique est envoyé de la part d’une autre personne, les adresses peuvent être différentes.

Listes des expéditeurs bloqués et listes de domaines bloqués dans les stratégies de blocage du courrier indésirable dans EOP, inspectez les `5321.MailFrom` `5322.From` adresses et. Les expéditeurs bloqués d’Outlook utilisent uniquement l' `5322.From` adresse.

## <a name="use-outlook-blocked-senders"></a>Utiliser les expéditeurs bloqués d’Outlook

Lorsque seul un petit nombre d’utilisateurs a reçu du courrier indésirable, les utilisateurs ou les administrateurs peuvent ajouter les adresses de messagerie de l’expéditeur à la liste des expéditeurs bloqués dans la boîte aux lettres. Pour obtenir des instructions, consultez la rubrique [configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).

Lorsque les messages sont bloqués en raison de la liste des expéditeurs bloqués d’un utilisateur, le champ d’en-tête **X-Forefront-antispam-Report** contient la valeur `SFV:BLK` .

> [!NOTE]
> Si les messages indésirables sont des bulletins d’informations provenant d’une source digne de réputation et reconnaissables, l’annulation de l’abonnement au courrier électronique est une autre option permettant d’empêcher l’utilisateur de recevoir les messages.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Utiliser les listes d’expéditeurs bloqués ou les listes de domaines bloqués

Lorsque plusieurs utilisateurs sont affectés, l’étendue est plus large, de sorte que la meilleure meilleure option est les listes d’expéditeurs bloqués ou les listes de domaines bloqués dans les stratégies anti-courrier indésirable. Les messages provenant d’expéditeurs figurant dans les listes sont marqués comme **courrier indésirable**et l’action que vous avez configurée pour le verdict du filtre de **courrier indésirable** est appliquée au message. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

La limite maximale de ces listes est d’environ 1000 entrées.

## <a name="use-mail-flow-rules"></a>Utiliser des règles de flux de messagerie

Si vous avez besoin de bloquer les messages qui sont envoyés à des utilisateurs spécifiques ou à l’ensemble de l’organisation, vous pouvez utiliser des règles de flux de messagerie. Les règles de flux de messagerie sont plus flexibles que les listes de blocs d’expéditeurs ou de domaines d’expéditeurs bloqués, car elles peuvent également rechercher des mots clés ou d’autres propriétés dans les messages indésirables.

Quelles que soient les conditions ou les exceptions que vous utilisez pour identifier les messages, vous configurez l’action permettant de définir le seuil de probabilité de courrier indésirable (SCL) du message sur 9, ce qui marque le message comme un **courrier indésirable de confiance élevée**. Pour plus d’informations, consultez [la rubrique utiliser des règles de flux de messagerie pour définir la valeur SCL dans messages](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md).

> [!IMPORTANT]
> Il est facile de créer des règles qui sont *excessivement* agressives, c’est pourquoi il est important que vous identifiiez uniquement les messages que vous souhaitez bloquer en utilisant des critères très spécifiques. Assurez-vous également d’activer l’audit sur la règle et de tester les résultats de la règle afin de s’assurer que tout fonctionne comme prévu.

## <a name="use-the-ip-block-list"></a>Utiliser la liste d’adresses IP bloquées

Lorsqu’il n’est pas possible d’utiliser l’une des autres options pour bloquer un expéditeur, vous devez *uniquement* utiliser la liste d’adresses IP bloquées dans la stratégie de filtrage des connexions. Pour plus d'informations, consultez la rubrique relative à la [configuration de la stratégie de filtre de connexion](configure-the-connection-filter-policy.md). Il est important de maintenir le nombre d’adresses IP bloquées à un minimum, donc le blocage des plages d’adresses IP entières n’est *pas* recommandé.

En *particulier* , vous devez éviter d’ajouter des plages d’adresses IP appartenant à des services grand public (par exemple, Outlook.com) ou des infrastructures partagées, et veiller à consulter la liste des adresses IP bloquées dans le cadre de la maintenance normale.
