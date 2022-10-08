---
title: Vidage automatique de zéro heure dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
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
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Le vidage automatique de zéro heure (ZAP) déplace rétroactivement les messages remis dans une boîte aux lettres Exchange Online vers le dossier de Email indésirable ou la quarantaine qui sont détectés comme courrier indésirable, hameçonnage ou qui contiennent des programmes malveillants après la remise.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 0517a0fff88486315815b1a68458e968c2860f5e
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68072368"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Purge automatique de zéro heure (ZAP) dans Exchange Online

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Principes de base du vidage automatique de zéro heure (ZAP)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, le vidage automatique de zéro heure (ZAP) est une fonctionnalité de protection par e-mail qui détecte et neutralise rétroactivement les messages malveillants de hameçonnage, de courrier indésirable ou de programmes malveillants qui ont déjà été remis à Exchange Online boîtes aux lettres.

ZAP ne fonctionne pas dans des environnements Exchange Online Protection autonomes (EOP) qui protègent les boîtes aux lettres Exchange locales.

## <a name="how-zap-works"></a>Fonctionnement de ZAP

Les signatures de courrier indésirable et de programmes malveillants sont mises à jour quotidiennement dans le service en temps réel. Toutefois, les utilisateurs peuvent toujours recevoir des messages malveillants pour diverses raisons, notamment si le contenu est armé après avoir été remis aux utilisateurs. ZAP résout ce problème en surveillant en permanence les mises à jour des signatures de courrier indésirable et de programmes malveillants dans le service. ZAP peut rechercher et supprimer des messages qui se trouvent déjà dans la boîte aux lettres d’un utilisateur.

L’action ZAP est transparente pour l’utilisateur ; ils ne sont pas avertis si un message est détecté et déplacé.

[Les listes d’expéditeurs fiables](create-safe-sender-lists-in-office-365.md), les règles de flux de messagerie (également appelées règles de transport), les règles de boîte de réception ou les filtres supplémentaires sont prioritaires sur ZAP. À l’instar de ce qui se passe dans le flux de messagerie, cela signifie que même si le service détermine que le message remis a besoin de ZAP, le message n’est pas activé en raison de la configuration des expéditeurs sécurisés. Il s’agit d’une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

Regardez cette courte vidéo pour découvrir comment ZAP dans Microsoft Defender pour Office 365 détecte et neutralise automatiquement les menaces par e-mail. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrLg]

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Vidage automatique de zéro heure (ZAP) pour les programmes malveillants

Pour les **messages lus ou non lus** qui contiennent des programmes malveillants après la remise, ZAP met en quarantaine le message qui contient la pièce jointe du programme malveillant. Par défaut, seuls les administrateurs peuvent afficher et gérer les messages malveillants mis en quarantaine. Toutefois, les administrateurs peuvent créer et utiliser des _stratégies de quarantaine_ pour définir ce que les utilisateurs sont autorisés à faire pour les messages qui ont été mis en quarantaine en tant que programmes malveillants. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

ZAP pour les programmes malveillants est activé par défaut dans les stratégies anti-programmes malveillants. Pour plus d’informations, consultez [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Vidage automatique de zéro heure (ZAP) pour hameçonnage

Pour les **messages lus ou non lus** identifiés comme hameçonnage après la remise, le résultat ZAP dépend de l’action configurée pour un verdict de filtrage des **e-mails de hameçonnage** dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage disponibles pour le hameçonnage et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X**, **ajouter une ligne d’objet avec du texte**, **rediriger le message vers l’adresse e-mail**, **Supprimer le message** : ZAP n’effectue aucune action sur le message.

- **Déplacer le message vers junk Email** : ZAP déplace le message vers le dossier Junk Email. Pour plus d’informations, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Message de mise en quarantaine** : ZAP met le message en quarantaine.

Par défaut, ZAP pour le hameçonnage est activé dans les stratégies anti-courrier indésirable, et l’action par défaut pour le verdict de filtrage des **e-mails de hameçonnage** est **le message de quarantaine**, ce qui signifie que ZAP pour le hameçonnage met le message en quarantaine par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, consultez [Configurer les stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Vidage automatique de zéro heure (ZAP) pour le hameçonnage à haut niveau de confiance

Pour les **messages lus ou non lus** identifiés comme hameçonnage à haut niveau de confiance après la remise, ZAP met le message en quarantaine. Par défaut, seuls les administrateurs peuvent afficher et gérer les messages de hameçonnage à haut niveau de confiance mis en quarantaine. Toutefois, les administrateurs peuvent créer et utiliser des _stratégies de quarantaine_ pour définir ce que les utilisateurs sont autorisés à faire pour les messages qui ont été mis en quarantaine comme hameçonnage à haut niveau de confiance. Pour plus d’informations, consultez [Stratégies de quarantaine](quarantine-policies.md)

ZAP pour le hameçonnage à haut niveau de confiance est activé par défaut. Pour plus d’informations, consultez [Sécuriser par défaut dans Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>Vidage automatique de zéro heure (ZAP) pour le courrier indésirable

Pour les **messages non lus** identifiés comme courrier indésirable après la remise, le résultat ZAP dépend de l’action configurée pour le verdict de filtrage du courrier **indésirable** dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage disponibles pour le courrier indésirable et leurs résultats ZAP possibles sont décrits dans la liste suivante :

- **Ajouter un en-tête X**, **ajouter une ligne d’objet avec du texte**, **rediriger le message vers l’adresse e-mail**, **Supprimer le message** : ZAP n’effectue aucune action sur le message.

- **Déplacer le message vers junk Email** : ZAP déplace le message vers le dossier Junk Email. Pour plus d’informations, consultez [Configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux lettres dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Message de mise en quarantaine** : ZAP met le message en quarantaine. Par défaut, les utilisateurs finaux peuvent afficher et gérer les messages indésirables mis en quarantaine où ils sont destinataires. Toutefois, les administrateurs peuvent créer et utiliser des _stratégies de quarantaine_ pour définir ce que les utilisateurs sont autorisés à faire pour les messages qui ont été mis en quarantaine en tant que courrier indésirable. Pour plus d’informations, consultez [Stratégies de quarantaine](quarantine-policies.md)

Par défaut, spam ZAP est activé dans les stratégies anti-courrier indésirable, et l’action par défaut pour le verdict de filtrage du courrier **indésirable** est **Déplacer le message vers le dossier Courrier indésirable Email**, ce qui signifie que spam ZAP déplace les messages **non lus** vers le dossier Courrier indésirable Email par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, consultez [Configurer les stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Considérations relatives au vidage automatique de zéro heure (ZAP) pour Microsoft Defender pour Office 365

ZAP ne met en quarantaine aucun message en cours de [livraison dynamique](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) dans l’analyse de la stratégie pièces jointes sécurisées, ou où le filtrage des programmes malveillants EOP a déjà remplacé la pièce jointe par le fichier **d’alerte de programme malveillant Text.txt** . Si un signal de hameçonnage ou de courrier indésirable est reçu pour ces types de messages, et que le verdict de filtrage dans la stratégie anti-courrier indésirable est défini pour prendre une action sur le message (Déplacer vers le courrier indésirable, rediriger, supprimer ou mettre en quarantaine), ZAP utilise par défaut une action « Déplacer vers le courrier indésirable ».

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment voir si ZAP a déplacé votre message

Pour déterminer si ZAP a déplacé votre message, vous disposez des options suivantes :

- **Nombre de messages** : utilisez la [vue Flux de courrier dans le rapport d’état mailflow](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) pour voir le nombre de messages affectés par ZAP pour la plage de dates spécifiée.
- **Détails du message** : Utilisez [l’Explorateur de menaces (et les détections en temps réel)](threat-explorer.md) pour filtrer **tous les** événements de messagerie par la valeur **ZAP** pour la colonne **d’action Supplémentaire** .

> [!NOTE]
> ZAP n’est pas journalisé dans les journaux d’audit de boîte aux lettres Exchange en tant qu’action système.

## <a name="zero-hour-auto-purge-zap-faq"></a>FAQ sur le vidage automatique de zéro heure (ZAP)

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Que se passe-t-il si un message légitime est déplacé vers le dossier Junk Email ?

Vous devez suivre le processus de création de rapports normal pour [les faux positifs](report-junk-email-messages-to-microsoft.md). La seule raison pour laquelle le message serait déplacé de la boîte de réception vers le dossier Courrier indésirable Email serait parce que le service a déterminé que le message était du courrier indésirable ou malveillant.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Que se passe-t-il si j’utilise le dossier Quarantaine au lieu du dossier Courrier indésirable ?

ZAP prendra des mesures sur un message basé sur la configuration de vos stratégies anti-courrier indésirable, comme décrit précédemment dans cet article.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Que se passe-t-il si j’utilise des expéditeurs approuvés, des règles de flux de courrier ou des listes d’expéditeurs autorisés/bloqués ?

Les expéditeurs approuvés, les règles de flux de messagerie ou bloquent et autorisent les paramètres de l’organisation à être prioritaires. Ces messages sont exclus de ZAP, car le service fait ce que vous l’avez configuré pour faire. Il s’agit d’une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Quelles sont les conditions de licence requises pour que le vidage automatique de zéro heure (ZAP) fonctionne ?

Il n’existe aucune limitation sur les licences. ZAP fonctionne sur toutes les boîtes aux lettres hébergées sur Exchange Online. ZAP ne fonctionne pas dans des environnements Exchange Online Protection autonomes (EOP) qui protègent les boîtes aux lettres Exchange locales.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, des règles de boîte de réception) ?

Le vidage automatique de zéro heure fonctionne toujours tant que le message n’a pas été supprimé, ou tant que la même action, ou plus forte, n’a pas déjà été appliquée. Par exemple, si la stratégie anti-hameçonnage est définie sur mise en quarantaine et que le message figure déjà dans le Email indésirable, ZAP prend des mesures pour mettre le message en quarantaine.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Comment ZAP affecte-t-il les boîtes aux lettres en attente ?

Le vidage automatique de zéro heure met en quarantaine les messages des boîtes aux lettres en attente. ZAP peut déplacer des messages vers le dossier Junk Email en fonction de l’action configurée pour un verdict de courrier indésirable ou de hameçonnage dans les stratégies anti-courrier indésirable.

Pour plus d’informations sur les conservations dans Exchange Online, consultez conservation [sur place et conservation des litiges dans Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds).
