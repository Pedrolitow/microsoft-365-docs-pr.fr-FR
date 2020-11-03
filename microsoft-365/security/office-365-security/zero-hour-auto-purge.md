---
title: Purge automatique avec zéro heure (ZAP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
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
description: Les administrateurs peuvent découvrir comment la suppression automatique des heures zéro peut déplacer rétroactivement les messages remis dans une boîte aux lettres Exchange Online vers le dossier de courrier indésirable ou la mise en quarantaine qui se trouve rétroactivement comme courrier indésirable ou hameçonnage.
ms.openlocfilehash: e59d93285dd75a749739b8247c156c19533ce2b1
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48845443"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Purge automatique avec zéro heure (ZAP) dans Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-features-of-zap"></a>Fonctionnalités de base de ZAP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, la fonction de purge automatique (ZAP) zéro heure est une fonctionnalité de protection de la messagerie qui détecte rétroactivement et neutralise les messages malveillants, de courrier indésirable ou de programmes malveillants qui ont déjà été remis aux boîtes aux lettres Exchange Online.

ZAP ne fonctionne pas dans les environnements autonomes Exchange Online Protection (EOP) qui protègent les boîtes aux lettres Exchange locales.

## <a name="how-zap-works"></a>Fonctionnement de l’ZAP

Les signatures de courrier indésirable et de programmes malveillants sont mises à jour quotidiennement en temps réel. Toutefois, les utilisateurs peuvent toujours recevoir des messages malveillants pour diverses raisons, notamment si le contenu est arme après remise aux utilisateurs. ZAP résout ce problème en surveillant en continu les mises à jour des signatures de courrier indésirable et de programmes malveillants dans le service. ZAP peut rechercher et supprimer des messages qui se trouvent déjà dans la boîte aux lettres d’un utilisateur.

L’action ZAP est transparente pour l’utilisateur ; ils ne sont pas avertis si un message est détecté et déplacé.

Les [listes des expéditeurs approuvés](create-safe-sender-lists-in-office-365.md), les règles de flux de messagerie (également appelées règles de transport), les règles de boîte de réception ou les filtres supplémentaires prévalent sur zap. À l’instar de ce qui se passe dans le flux de messagerie, cela signifie que même si le service détermine que le message remis a besoin de l’élément ZAP, le message n’est pas traité en raison de la configuration des expéditeurs approuvés. Il s’agit d’une autre raison de contourner le filtrage des messages.

### <a name="malware-zap"></a>Programme malveillant ZAP

Pour les **messages lus ou non lus** qui contiennent des programmes malveillants après la remise, ZAP met en quarantaine le message qui contient la pièce jointe de programmes malveillants. Seuls les administrateurs peuvent afficher et gérer les messages malveillants en quarantaine.

Le programme de protection contre les programmes malveillants est activé par défaut dans les stratégies anti-programme malveillant. Pour plus d’informations, consultez la rubrique [configure anti-malware Policies in EOP](configure-anti-malware-policies.md).

### <a name="phish-zap"></a>Hameçon ZAP

Pour les **messages lus ou non lus** identifiés comme hameçons après la remise, le résultat de la fonction zap dépend de l’action configurée pour le filtrage du **courrier d’hameçonnage** dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage de filtrage disponibles pour les hameçons et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X** , ajouter une **ligne d’objet avec du texte** : zap n’effectue aucune action sur le message.

- **Déplacer le message vers le courrier indésirable** : zap déplace le message vers le dossier courrier indésirable, dans la mesure où la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Rediriger le message vers l’adresse de messagerie** , **supprimer le message** , **mettre en quarantaine** le message : zap met en quarantaine le message.

Par défaut, le logiciel de hameçonnage ZAP est activé dans les stratégies de blocage du courrier indésirable et l’action par défaut pour le verdict du filtrage du **courrier d’hameçonnage** est **mise en quarantaine** , ce qui signifie que le hameçonnage zap met en quarantaine le message par défaut.

Pour plus d’informations sur la configuration des règles de filtrage du courrier indésirable, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="spam-zap"></a>Blocage du courrier indésirable

Pour les **messages non lus** identifiés comme du courrier indésirable après la remise, le résultat de la fonction zap dépend de l’action configurée pour le verdict du filtrage du **courrier** indésirable dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage de courrier électronique disponibles pour le courrier indésirable et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X** , ajouter une **ligne d’objet avec du texte** : zap n’effectue aucune action sur le message.

- **Déplacer le message vers le courrier indésirable** : zap déplace le message vers le dossier courrier indésirable, dans la mesure où la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Rediriger le message vers l’adresse de messagerie** , **supprimer le message** , **mettre en quarantaine** le message : zap met en quarantaine le message. Les utilisateurs finaux peuvent afficher et gérer leurs propres messages de courrier indésirable mis en quarantaine.

Par défaut, le logiciel de détection de courrier indésirable est activé dans les stratégies de blocage du courrier indésirable et l’action par défaut pour le filtrage du **courrier** indésirable est **déplacer le message vers le dossier courrier indésirable** , ce qui signifie que le courrier indésirable déplace les messages **non lus** dans le dossier courrier indésirable

Pour plus d’informations sur la configuration des règles de filtrage du courrier indésirable, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zap-considerations-for-microsoft-defender-for-office-365"></a>Considérations relatives à l’ZAP pour Microsoft Defender pour Office 365

ZAP ne met pas en quarantaine les messages qui se trouvent dans le processus de [remise dynamique](atp-safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) dans l’analyse des pièces jointes approuvées ou dans lesquels le filtrage des programmes malveillants EOP a déjà remplacé la pièce jointe par le fichier d' **alerte de programme malveillant Text.txt** . Si un signal de courrier indésirable ou de courrier indésirable est reçu pour ces types de messages et que le verdict de filtrage dans la stratégie anti-courrier indésirable est défini de façon à effectuer une action sur le message (passer à courrier indésirable, rediriger, supprimer ou mettre en quarantaine), l’action ZAP sera par défaut «déplacer vers le courrier indésirable

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment savoir si la méthode ZAP a déplacé votre message

Pour déterminer si l’élément ZAP a déplacé votre message, vous pouvez utiliser le [rapport d’état de protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) ou l' [Explorateur de menaces (et les détections en temps réel)](threat-explorer.md). Notez qu’en tant qu’action système, ZAP n’est pas consigné dans les journaux d’audit de boîte aux lettres Exchange.

## <a name="zap-faq"></a>FAQ ZAP

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Que se passe-t-il si un message légitime est déplacé vers le dossier courrier indésirable ?

Vous devez suivre le processus de création de rapports normal pour les [faux positifs](report-junk-email-messages-to-microsoft.md). La seule raison pour laquelle le message est déplacé de la boîte de réception vers le dossier courrier indésirable est que le service a déterminé que le message était du courrier indésirable ou malveillant.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Que se passe-t-il si j’utilise le dossier de quarantaine au lieu du dossier courrier indésirable ?

ZAP effectue une action sur un message en fonction de la configuration de vos stratégies anti-courrier indésirable, comme décrit plus haut dans cette rubrique.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Que se passe-t-il si j’utilise des expéditeurs approuvés, des règles de flux de messagerie ou des listes d’expéditeurs autorisés/bloqués ?

Les expéditeurs approuvés, les règles de flux de messagerie ou le blocage et l’autorisation des paramètres organisationnels sont prioritaires. Ces messages sont exclus de l’opération ZAP puisque le service effectue les opérations que vous avez configurées. Il s’agit d’une autre raison de contourner le filtrage des messages.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, des règles de boîte de réception) ?

L’application ZAP fonctionne toujours tant que le message n’a pas été supprimé ou que l’action même ou renforcée n’a pas encore été appliquée. Par exemple, si la stratégie de hameçonnage est définie sur quarantaine et que l’utilisateur ou l’administrateur a déjà un courrier indésirable du courrier, la mise en quarantaine exécute l’action de mise en quarantaine du fichier.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Comment ZAP affecte-t-il les boîtes aux lettres en conservation ?

ZAP ne met pas en quarantaine les messages des boîtes aux lettres en conservation. ZAP peut déplacer des messages vers le dossier courrier indésirable en fonction de l’action configurée pour le verdict de courrier indésirable ou de hameçonnage dans les stratégies de blocage du courrier indésirable.

Pour plus d’informations sur les suspensions dans Exchange Online, consultez la rubrique mise [en attente inaltérable et conservation pour litige dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/in-place-and-litigation-holds).
