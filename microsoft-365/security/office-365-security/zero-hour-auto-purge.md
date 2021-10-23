---
title: Purge automatique d’heure zéro dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 06/22/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 96deb75f-64e8-4c10-b570-84c99c674e15
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: La purge automatique (ZAP) de zéro heure déplace de manière identité les messages remis dans une boîte aux lettres Exchange Online vers le dossier Courrier indésirable ou la mise en quarantaine qui sont détectés comme du courrier indésirable, du hameçonnage ou qui contiennent des programmes malveillants après leur remise.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c2b6e8ce6d15ad652b87e6529f9fd3cb2b3878f7
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556339"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Purge automatique de zéro heure (ZAP) dans Exchange Online

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Principes de base de la purge automatique d’heure zéro (ZAP)

Dans Microsoft 365 organisations avec des boîtes aux lettres en Exchange Online, la purge automatique d’heure zéro (ZAP) est une fonctionnalité de protection du courrier électronique qui détecte et s’attaque de manière ident nouvelle aux messages malveillants de hameçonnage, de courrier indésirable ou de programmes malveillants qui ont déjà été remis à des boîtes aux lettres Exchange Online.

ZAP ne fonctionne pas dans les environnements Exchange Online Protection autonomes (EOP) qui protègent les boîtes aux lettres Exchange en local.

## <a name="how-zap-works"></a>Fonctionnement de ZAP

Les signatures de courrier indésirable et de programmes malveillants sont mises à jour quotidiennement dans le service en temps réel. Toutefois, les utilisateurs peuvent toujours recevoir des messages malveillants pour diverses raisons, notamment si le contenu est en cours de saisie après avoir été remis aux utilisateurs. ZaP résout ce problème en surveillant en permanence les mises à jour des signatures de courrier indésirable et de programmes malveillants dans le service. ZAP peut rechercher et supprimer des messages qui se trouvent déjà dans la boîte aux lettres d’un utilisateur.

L’action ZAP est transparente pour l’utilisateur . Ils ne sont pas avertis si un message est détecté et déplacé.

[Coffre](create-safe-sender-lists-in-office-365.md)des listes d’expéditeurs, des règles de flux de messagerie (également appelées règles de transport), des règles de boîte de réception ou des filtres supplémentaires prévalent sur ZAP. Comme dans le flux de messagerie, cela signifie que même si le service détermine que le message remis a besoin de zap, le message n’est pas agit en raison de la configuration des expéditeurs sûrs. C’est une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Purge automatique en heure zéro (ZAP) pour les programmes malveillants

Pour **les messages lus ou non** lus qui contiennent des programmes malveillants après remise, ZAP met en quarantaine le message qui contient la pièce jointe des programmes malveillants. Par défaut, seuls les administrateurs peuvent afficher et gérer les messages de programmes malveillants mis en quarantaine. Toutefois, les administrateurs  peuvent créer et utiliser des stratégies de mise en quarantaine pour définir ce que les utilisateurs sont autorisés à faire aux messages mis en quarantaine en tant que programmes malveillants. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

ZaP pour les programmes malveillants est activé par défaut dans les stratégies anti-programme malveillant. Pour plus d’informations, voir [Configurer des stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Purge automatique sans heure (ZAP) pour hameçonnage

Pour les **messages** lus ou non lus identifiés comme étant du hameçonnage après  la remise, le résultat ZAP dépend de l’action configurée pour un verdict de filtrage du courrier de hameçonnage dans la stratégie anti-courrier indésirable applicable. Les actions de verdict de filtrage disponibles pour le hameçonnage et leurs résultats ZAP possibles sont décrits dans la liste suivante :

- **Ajouter un en-tête X,** ajouter **une** ligne d’objet avec du texte, rediriger **le message** vers l’adresse e-mail, supprimer **le message**: ZAP ne prend aucune mesure sur le message.

- **Déplacer le message vers le courrier** indésirable : ZAP déplace le message vers le dossier Courrier indésirable. Pour plus d’informations, voir [Configurer les paramètres](configure-junk-email-settings-on-exo-mailboxes.md)de courrier indésirable Exchange Online boîtes aux lettres dans Microsoft 365 .

- **Message de mise en** quarantaine : ZAP met le message en quarantaine.

Par défaut, ZAP pour le hameçonnage est activé dans les  stratégies anti-courrier indésirable et l’action par défaut pour le verdict de filtrage du courrier d’hameçonnage est le **message** de mise en quarantaine, ce qui signifie que ZAP pour le hameçonnage met le message en quarantaine par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, voir Configurer des stratégies [anti-courrier](configure-your-spam-filter-policies.md)indésirable dans Microsoft 365 .

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Purge automatique en heure zéro (ZAP) pour le hameçonnage à haut niveau de confiance

Pour **les messages lus ou non lus** identifiés comme hameçonnage à haut niveau de confiance après la remise, ZAP met le message en quarantaine. Par défaut, seuls les administrateurs peuvent afficher et gérer les messages de hameçonnage à haut niveau de confiance mis en quarantaine. Toutefois, les administrateurs  peuvent créer et utiliser des stratégies de mise en quarantaine pour définir ce que les utilisateurs sont autorisés à faire aux messages mis en quarantaine en tant que hameçonnage à haut niveau de confiance. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md)

ZaP pour le hameçonnage à haut niveau de confiance est activé par défaut. Pour plus d’informations, [consultez La](secure-by-default.md)sécurité par défaut dans Office 365 .

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Purge automatique en heure zéro (ZAP) pour le courrier indésirable

Pour **les messages** non lus identifiés comme courrier indésirable après la remise,  le résultat ZAP dépend de l’action configurée pour le verdict de filtrage du courrier indésirable dans la stratégie anti-courrier indésirable applicable. Les actions de verdict de filtrage disponibles pour le courrier indésirable et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X,** ajouter **une** ligne d’objet avec du texte, rediriger **le message** vers l’adresse e-mail, supprimer **le message**: ZAP ne prend aucune mesure sur le message.

- **Déplacer le message vers le courrier** indésirable : ZAP déplace le message vers le dossier Courrier indésirable. Pour plus d’informations, voir [Configurer les paramètres](configure-junk-email-settings-on-exo-mailboxes.md)de courrier indésirable Exchange Online boîtes aux lettres dans Microsoft 365 .

- **Message de mise en** quarantaine : ZAP met le message en quarantaine. Par défaut, les utilisateurs finaux peuvent afficher et gérer les messages de courrier indésirable mis en quarantaine lorsqu’ils sont destinataires. Toutefois, les administrateurs  peuvent créer et utiliser des stratégies de mise en quarantaine pour définir ce que les utilisateurs sont autorisés à faire aux messages mis en quarantaine comme courrier indésirable. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md)

Par défaut, la zap de courrier indésirable est activée dans  les stratégies anti-courrier indésirable et l’action par défaut pour le verdict de filtrage du courrier indésirable est Déplacer le **message** vers le dossier Courrier indésirable, ce qui signifie que le courrier indésirable ZAP déplace les **messages** non lus vers le dossier Courrier indésirable par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, voir Configurer des stratégies [anti-courrier](configure-your-spam-filter-policies.md)indésirable dans Microsoft 365 .

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Considérations sur la purge automatique d’heure zéro (ZAP) pour Microsoft Defender pour Office 365

ZAP ne met pas en quarantaine les [](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) messages en cours de remise dynamique dans l’analyse de la stratégie de  pièces jointes Coffre, ou lorsque le filtrage des programmes malveillants EOP a déjà remplacé la pièce jointe par le fichier Text.txtd’alerte anti-programme malveillant. Si un message d’hameçonnage ou de courrier indésirable est reçu pour ces types de messages et que le verdict de filtrage dans la stratégie anti-courrier indésirable est définie pour prendre une mesure sur le message (Déplacer vers le courrier indésirable, rediriger, supprimer ou mettre en quarantaine), zap est définie par défaut sur une action « Déplacer vers le courrier indésirable ».

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment savoir si ZAP a déplacé votre message

Pour déterminer si ZAP a déplacé votre message, vous pouvez utiliser le rapport d’état de la [protection](view-email-security-reports.md#threat-protection-status-report) contre les menaces ou l’Explorateur [de menaces (et les détections en temps réel).](threat-explorer.md) Notez qu’en tant qu’action système, ZAP n’est pas journalisé dans les journaux d’audit Exchange boîte aux lettres.

## <a name="zero-hour-auto-purge-zap-faq"></a>FAQ sur la purge automatique d’heure zéro (ZAP)

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Que se passe-t-il si un message légitime est déplacé vers le dossier Courrier indésirable ?

Vous devez suivre le processus de création de rapports normal pour [les faux positifs.](report-junk-email-messages-to-microsoft.md) La seule raison pour laquelle le message serait déplacé de la boîte de réception vers le dossier Courrier indésirable serait parce que le service a déterminé que le message était du courrier indésirable ou malveillant.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Que se passe-t-il si j’utilise le dossier De quarantaine au lieu du dossier Courrier indésirable ?

ZAP prendra des mesures sur un message en fonction de la configuration de vos stratégies anti-courrier indésirable, comme décrit plus tôt dans cet article.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Que se passe-t-il si j’utilise des expéditeurs autorisés, des règles de flux de messagerie ou des listes d’expéditeurs autorisés/bloqués ?

Coffre expéditeurs, règles de flux de messagerie ou bloquer et autoriser les paramètres organisationnels à être prioritaire. Ces messages sont exclus de ZAP, car le service fait ce que vous avez configuré pour le faire. C’est une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Quelles sont les conditions de licence requises pour que la purge automatique sans heure (ZAP) fonctionne ?

Les licences ne sont pas limitées. ZAP fonctionne sur toutes les boîtes aux lettres hébergées sur Exchange en ligne. ZAP ne fonctionne pas dans les environnements Exchange Online Protection autonomes (EOP) qui protègent les boîtes aux lettres Exchange en local.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, règles de boîte de réception) ?

La purge automatique d’heure zéro fonctionne toujours tant que le message n’a pas été supprimé, ou tant que la même action, ou plus forte, n’a pas déjà été appliquée. Par exemple, si la stratégie anti-hameçonnage est mise en quarantaine et que le message se trouve déjà dans le courrier indésirable, ZAP prendra des mesures pour mettre le message en quarantaine.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Comment la zap affecte-t-elle les boîtes aux lettres en attente ?

La purge automatique d’heure zéro met en quarantaine les messages des boîtes aux lettres placées en attente. ZAP peut déplacer des messages vers le dossier Courrier indésirable en fonction de l’action configurée pour un verdict de courrier indésirable ou de hameçonnage dans les stratégies anti-courrier indésirable.

Pour plus d’informations sur les Exchange Online, voir [In-Place Hold and Litigation Hold in Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds).
