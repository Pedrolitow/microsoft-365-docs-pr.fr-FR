---
title: Purge automatique (ZAP) zéro heure-fonctionnalité de protection de messagerie
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: article
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
description: En savoir plus sur la purge automatique des heures zéro (ZAP), une fonctionnalité de protection de la messagerie électronique dans Microsoft 365 qui détecte les courriers indésirables, les programmes malveillants ou les messages de hameçonnage qui ont déjà été remis à Exchange Online.
ms.openlocfilehash: a6f21147e7beaadb3aa6430b299dea8b248561c1
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44034925"
---
# <a name="zero-hour-auto-purge-zap---protection-against-spam-and-malware-in-microsoft-365"></a>Purge automatique à zéro heure (ZAP)-protection contre le courrier indésirable et les programmes malveillants dans Microsoft 365

## <a name="overview"></a>Vue d'ensemble

La suppression automatique de zéro heure (ZAP) est une fonctionnalité de protection de la messagerie électronique dans Microsoft 365 qui détecte rétroactivement et neutralise les messages malveillants, de courrier indésirable, de courrier indésirable ou de programmes malveillants qui ont déjà été remis à des boîtes aux lettres Exchange Online.

ZAP est disponible avec le service Exchange Online Protection (EOP) par défaut fourni avec tout abonnement Microsoft 365 qui contient des boîtes aux lettres Exchange Online. ZAP ne fonctionne pas dans les environnements EOP autonomes qui protègent les boîtes aux lettres Exchange locales.

## <a name="how-zap-works"></a>Fonctionnement de l’ZAP

Microsoft 365 met à jour quotidiennement les signatures de courrier indésirable et de programmes malveillants en temps réel. Toutefois, les utilisateurs peuvent toujours recevoir des messages malveillants pour diverses raisons, notamment si le contenu est arme après remise aux utilisateurs. ZAP résout ce problème en surveillant en permanence les mises à jour des signatures de courrier indésirable et de programmes malveillants Microsoft 365. ZAP peut rechercher et supprimer des messages qui se trouvent déjà dans la boîte aux lettres d’un utilisateur.

L’action ZAP est transparente pour l’utilisateur ; ils ne sont pas avertis si un message est détecté et déplacé.

Les [listes des expéditeurs approuvés](create-safe-sender-lists-in-office-365.md), les règles de flux de messagerie (également appelées règles de transport), les règles de boîte de réception ou les filtres supplémentaires prévalent sur zap.

### <a name="malware-zap"></a>Programme malveillant ZAP

Pour les **messages lus ou non lus** qui contiennent des programmes malveillants après la remise, ZAP met en quarantaine le message qui contient la pièce jointe de programmes malveillants. Seuls les administrateurs peuvent afficher et gérer les messages malveillants en quarantaine.

Le programme de protection contre les programmes malveillants est activé par défaut dans les stratégies anti-programme malveillant. Pour plus d’informations, consultez la rubrique [configure anti-malware Policies in Microsoft 365](configure-anti-malware-policies.md).

### <a name="phish-zap"></a>Hameçon ZAP

Pour les **messages lus ou non lus** identifiés comme hameçons après la remise, le résultat de la fonction zap dépend de l’action configurée pour le filtrage du **courrier d’hameçonnage** dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage de filtrage disponibles pour les hameçons et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X**, ajouter une **ligne d’objet avec du texte**: zap n’effectue aucune action sur le message.

- **Déplacer le message vers le courrier indésirable**: zap déplace le message vers le dossier courrier indésirable, dans la mesure où la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Rediriger le message vers l’adresse de messagerie**, **supprimer le message**, **mettre en quarantaine**le message : zap met en quarantaine le message. Seuls les administrateurs peuvent afficher et gérer les messages hameçons mis en quarantaine.

Par défaut, le logiciel de hameçonnage ZAP est activé dans les stratégies de blocage du courrier indésirable et l’action par défaut pour le verdict du filtrage du **courrier d’hameçonnage** est **mise en quarantaine**, ce qui signifie que le hameçonnage zap met en quarantaine le message par défaut.

Pour plus d’informations sur la configuration des règles de filtrage du courrier indésirable, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="spam-zap"></a>Blocage du courrier indésirable

Pour les **messages non lus** identifiés comme du courrier indésirable après la remise, le résultat de la fonction zap dépend de l’action configurée pour le verdict du filtrage du **courrier** indésirable dans la stratégie anti-courrier indésirable applicable. Les actions de filtrage de courrier électronique disponibles pour le courrier indésirable et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X**, ajouter une **ligne d’objet avec du texte**: zap n’effectue aucune action sur le message.

- **Déplacer le message vers le courrier indésirable**: zap déplace le message vers le dossier courrier indésirable, dans la mesure où la règle de courrier indésirable est activée dans la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, consultez la rubrique [configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Rediriger le message vers l’adresse de messagerie**, **supprimer le message**, **mettre en quarantaine**le message : zap met en quarantaine le message. Les utilisateurs finaux peuvent afficher et gérer leurs propres messages de courrier indésirable mis en quarantaine.

Par défaut, le logiciel de détection de courrier indésirable est activé dans les stratégies de blocage du courrier indésirable et l’action par défaut pour le filtrage du **courrier** indésirable est **déplacer le message vers le dossier courrier indésirable**, ce qui signifie que le courrier indésirable déplace les messages **non lus** dans le dossier courrier indésirable

Pour plus d’informations sur la configuration des règles de filtrage du courrier indésirable, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zap-considerations-for-office-365-advanced-threat-protection-atp"></a>Considérations sur l’ZAP pour Office 365 protection avancée contre les menaces (ATP)

ZAP ne met pas en quarantaine les messages qui se trouvent dans le processus d’analyse de [remise dynamique](dynamic-delivery-and-previewing.md) , ou où le filtrage des programmes malveillants a déjà remplacé la pièce jointe par le fichier **texte. txt de l’alerte anti-programme malveillant** . Si un signal de courrier indésirable ou de courrier indésirable est reçu pour ces types de messages et que le verdict de filtrage dans la stratégie de blocage du courrier indésirable est défini de façon à effectuer une action sur le message (déplacer vers le courrier indésirable, rediriger, supprimer, mettre en quarantaine), ZAP utilise l’action « déplacer vers courrier indésirable »

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment savoir si la méthode ZAP a déplacé votre message

Pour déterminer si l’élément ZAP a déplacé votre message, vous pouvez utiliser le [rapport d’état de protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) ou l' [Explorateur de menaces (et les détections en temps réel)](threat-explorer.md). Notez qu’en tant qu’action système, ZAP n’est pas consigné dans les journaux d’audit de boîte aux lettres Exchange.

## <a name="zap-faq"></a>FAQ ZAP

### <a name="q-what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Q : que se passe-t-il si un message légitime est déplacé vers le dossier courrier indésirable ?

A : vous devez suivre le processus de création de rapports normal pour les [faux positifs](report-junk-email-messages-to-microsoft.md). La seule raison pour laquelle le message est déplacé de la boîte de réception vers le dossier courrier indésirable est que le service a déterminé que le message était du courrier indésirable ou malveillant.

### <a name="q-what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Q : que se passe-t-il si j’utilise le dossier de quarantaine au lieu du dossier courrier indésirable ?

Un : ZAP effectue une action sur un message en fonction de la configuration de vos stratégies anti-courrier indésirable, comme décrit plus haut dans cette rubrique.

### <a name="q-what-if-im-using-mail-flow-rules-or-allowedblocked-sender-lists"></a>Q : que se passe-t-il si j’utilise des règles de flux de messagerie ou des listes d’expéditeurs autorisés/bloqués ?

A : les règles de flux de messagerie ou bloquer et autoriser les paramètres organisationnels sont prioritaires. Ces messages sont exclus de ZAP.

### <a name="q-what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Q : que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, les règles de boîte de réception) ?

Un : ZAP fonctionne toujours tant que le message n’a pas été supprimé, ou tant que l’action même ou renforcée n’a pas encore été appliquée. Par exemple, si la stratégie de hameçonnage est définie sur quarantaine et que l’utilisateur ou l’administrateur a déjà un courrier indésirable du courrier, la mise en quarantaine exécute l’action de mise en quarantaine du fichier.

### <a name="q-does-zap-change-the-message-header"></a>Q : est-ce que l’en-tête de message est modifié ?

A : une action ZAP n’effectue aucune modification dans l’en-tête du message.

### <a name="q-how-does-zap-affect-mailboxes-on-hold"></a>Q : Comment ZAP affecte-t-il les boîtes aux lettres en conservation ?

Un : ZAP ne met pas en quarantaine les messages des boîtes aux lettres en conservation. ZAP peut déplacer des messages vers le dossier courrier indésirable en fonction de l’action configurée pour le verdict de courrier indésirable ou de hameçonnage dans les stratégies de blocage du courrier indésirable.

Pour plus d’informations sur les suspensions dans Exchange Online, consultez la rubrique mise [en attente inaltérable et conservation pour litige dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/in-place-and-litigation-holds).
