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
ms.collection: m365-security
ms.localizationpriority: medium
search.appverid:
- MET150s
description: Les administrateurs peuvent en savoir plus sur les options disponibles et préférées pour bloquer les messages entrants dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 0f7538efa9eeaa5cbca2287aab3379bfb614cc3a
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68642368"
---
# <a name="create-blocked-sender-lists-in-eop"></a>Créer des listes d’expéditeurs bloqués dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, EOP offre plusieurs façons de bloquer les e-mails des expéditeurs indésirables. Collectivement, vous pouvez considérer ces options comme des _listes d’expéditeurs bloquées_.

Les listes d’expéditeurs bloqués disponibles sont décrites dans la liste suivante, de la plus recommandée à la moins recommandée :

1. Bloquer les entrées pour les domaines et les adresses e-mail (y compris les expéditeurs usurpés) dans la liste d’autorisations/de blocs du locataire.
2. Expéditeurs bloqués Outlook (liste des expéditeurs bloqués stockée dans chaque boîte aux lettres).
3. Listes d’expéditeurs bloquées ou listes de domaines bloqués (stratégies anti-courrier indésirable).
4. Règles de flux de messagerie (également appelées règles de transport).
5. Liste de blocage IP (filtrage de connexion).

Le reste de cet article contient des détails sur chaque méthode.

> [!NOTE]
> Envoyez toujours des messages dans vos listes d’expéditeurs bloqués à Microsoft à des fins d’analyse. Pour obtenir des instructions, consultez [Signaler un e-mail douteux à Microsoft](admin-submission.md#report-questionable-email-to-microsoft). Si les messages ou les sources de messages sont considérés comme dangereux, Microsoft peut bloquer automatiquement les messages, et vous n’aurez pas besoin de gérer manuellement l’entrée dans les listes d’expéditeurs bloqués.
>
> Au lieu de bloquer l’e-mail, vous disposez également de plusieurs options pour autoriser le courrier électronique provenant de sources spécifiques à l’aide de _listes d’expéditeurs fiables_. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md).

## <a name="email-message-basics"></a>Email principes de base des messages

Un message électronique SMTP standard est constitué d’une _enveloppe de message_ et d’un contenu de message. L’enveloppe du message contient les informations nécessaires à la transmission et à la remise du message entre les serveurs SMTP. Le contenu du message comporte les champs d’en-tête de message (collectivement appelés l’_en-tête de message_) et le corps du message. L’enveloppe du message est décrite dans RFC 5321 et l’en-tête de message est décrit dans RFC 5322. Les destinataires ne voient jamais l’enveloppe de message réelle, car elle est générée par le processus de transmission de message et ne fait pas réellement partie du message.

- L’adresse `5321.MailFrom` (également appelée adresse **MAIL FROM** , expéditeur P1 ou expéditeur d’enveloppe) est l’adresse e-mail utilisée dans la transmission SMTP du message. Cette adresse e-mail est généralement enregistrée dans le champ **d’en-tête Chemin d’accès** de retour dans l’en-tête de message (bien qu’il soit possible pour l’expéditeur de désigner une autre adresse **e-mail return-path** ). Si le message ne peut pas être remis, il s’agit du destinataire du rapport de non-remise (également appelé NDR ou message de rebond).

- L’adresse `5322.From` de messagerie (également appelée adresse **De** ou expéditeur P2) est l’adresse e-mail dans le champ d’en-tête **From** et l’adresse e-mail de l’expéditeur qui s’affiche dans les clients de messagerie.

Souvent, les adresses et `5322.From` les `5321.MailFrom` adresses sont les mêmes (communication de personne à personne). Toutefois, lorsque l’e-mail est envoyé pour le compte d’une autre personne, les adresses peuvent être différentes.

Les listes d’expéditeurs bloquées et les listes de domaines bloquées dans les stratégies anti-courrier indésirable dans EOP inspectent uniquement les `5322.From` adresses. Ce comportement est similaire aux expéditeurs bloqués Outlook qui utilisent l’adresse `5322.From` .

## <a name="use-block-entries-in-the-tenant-allowblock-list"></a>Utiliser des entrées de bloc dans la liste d’autorisations/de blocs du locataire

L’option numéro un recommandée pour bloquer le courrier à partir d’expéditeurs ou de domaines spécifiques est la liste d’autorisation/de blocage du locataire. Pour obtenir des instructions, consultez [Autoriser ou bloquer les e-mails à l’aide de la liste d’autorisation/de blocage du locataire](allow-block-email-spoof.md).

Email messages de ces expéditeurs sont marqués comme _courrier indésirable à haut niveau de confiance_ (SCL = 9). Ce qui arrive aux messages est déterminé par la [stratégie anti-courrier indésirable](configure-your-spam-filter-policies.md) qui a détecté le message pour le destinataire. Dans la stratégie anti-courrier indésirable par défaut et les nouvelles stratégies personnalisées, les messages marqués comme courrier indésirable à haut niveau de confiance sont remis par défaut au dossier Junk Email. Dans les [stratégies de sécurité prédéfinies](preset-security-policies.md) Standard et Strict, les messages indésirables à haut niveau de confiance sont mis en quarantaine.

En guise d’avantage supplémentaire, les utilisateurs de l’organisation ne peuvent pas envoyer de courrier électronique à ces domaines et adresses bloqués. Ils recevront le rapport de non-remise suivant (également appelé NDR ou message `5.7.1  Your message can't be delivered because one or more recipients are blocked by your organization's tenant allow/block list policy.` de rebond) : l’intégralité du message est bloquée pour tous les destinataires si l’e-mail est envoyé à l’une des entrées de la liste.

Uniquement si vous ne pouvez pas utiliser la liste d’autorisation/de blocage du locataire pour une raison quelconque si vous envisagez d’utiliser une autre méthode pour bloquer les expéditeurs.

## <a name="use-outlook-blocked-senders"></a>Utiliser des expéditeurs bloqués Outlook

Quand seul un petit nombre d’utilisateurs ont reçu des e-mails indésirables, les utilisateurs ou administrateurs peuvent ajouter les adresses e-mail de l’expéditeur à la liste Des expéditeurs bloqués dans la boîte aux lettres. Pour obtenir des instructions, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres](configure-junk-email-settings-on-exo-mailboxes.md).

Lorsque les messages sont bloqués en raison de la liste des expéditeurs bloqués d’un utilisateur, le champ **d’en-tête X-Forefront-Antispam-Report** contient la valeur `SFV:BLK`.

> [!NOTE]
> Si les messages indésirables sont des bulletins d’informations provenant d’une source reconnue et reconnaissable, l’annulation de l’abonnement à partir de l’e-mail est une autre option permettant d’empêcher l’utilisateur de recevoir les messages.

## <a name="use-blocked-sender-lists-or-blocked-domain-lists"></a>Utiliser des listes d’expéditeurs bloquées ou des listes de domaines bloquées

Lorsque plusieurs utilisateurs sont affectés, l’étendue est plus large. La meilleure option suivante est donc de bloquer les listes d’expéditeurs ou les listes de domaines bloquées dans les stratégies anti-courrier indésirable. Les messages des expéditeurs figurant sur les listes sont marqués comme **courrier indésirable à haut niveau de confiance**, et l’action que vous avez configurée pour le verdict du filtre **de courrier indésirable à haut niveau de confiance** est effectuée sur les messages. Pour plus d’informations, consultez [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

La limite maximale pour ces listes est d’environ 1 000 entrées.

## <a name="use-mail-flow-rules"></a>Utiliser des règles de flux de messagerie

Les règles de flux de courrier peuvent également rechercher des mots clés ou d’autres propriétés dans les messages indésirables.

Quelles que soient les conditions ou exceptions que vous utilisez pour identifier les messages, vous configurez l’action pour définir le niveau de confiance du courrier indésirable (SCL) du message sur 9, ce qui marque le message comme courrier **indésirable à haut niveau de confiance**. Pour plus d’informations, consultez [Utiliser des règles de flux de messagerie pour définir la liste de contrôle de contrôle d’accès dans les messages](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

> [!IMPORTANT]
> Il est facile de créer des règles _trop_ agressives. Il est donc important d’identifier uniquement les messages que vous souhaitez bloquer à l’aide de critères très spécifiques. Veillez également à [surveiller l’utilisation de la règle](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#monitor-rule-usage) pour vous assurer que tout fonctionne comme prévu.

## <a name="use-the-ip-block-list"></a>Utiliser la liste de blocs IP

Lorsqu’il n’est pas possible d’utiliser l’une des autres options pour bloquer un expéditeur, _vous devez uniquement_ utiliser la liste de blocage IP dans la stratégie de filtre de connexion. Pour plus d'informations, consultez la rubrique relative à la [configuration de la stratégie de filtre de connexion](configure-the-connection-filter-policy.md). Il est important de limiter au minimum le nombre d’adresses IP bloquées. Il n’est donc _pas_ recommandé de bloquer des plages d’adresses IP entières.

Vous devez _en particulier_ éviter d’ajouter des plages d’adresses IP qui appartiennent à des services grand public (par exemple, outlook.com) ou à des infrastructures partagées, et également vérifier que vous passez en revue la liste des adresses IP bloquées dans le cadre d’une maintenance régulière.
