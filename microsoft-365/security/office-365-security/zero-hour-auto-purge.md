---
title: Purge automatique en heure zéro (ZAP)
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
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
description: Les administrateurs peuvent découvrir comment la purge automatique d’heure zéro (ZAP) peut déplacer de manière intégrable les messages remis dans une boîte aux lettres Exchange Online vers le dossier Courrier indésirable ou la mise en quarantaine qui se trouve de manière indespérable comme courrier indésirable ou hameçonnage.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5fd41cf45ad2a49d74684ae3e20dded5c1b8f034
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50287304"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Purge automatique zéro heure (ZAP) dans Exchange Online

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


## <a name="basic-features-of-zap"></a>Fonctionnalités de base de ZAP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, la purge automatique d’heure zéro (ZAP) est une fonctionnalité de protection du courrier électronique qui détecte et s’attaque de manière insérable aux messages malveillants de hameçonnage, de courrier indésirable ou de programmes malveillants qui ont déjà été remis aux boîtes aux lettres Exchange Online.

ZAP ne fonctionne pas dans les environnements Exchange Online Protection (EOP) autonomes qui protègent les boîtes aux lettres Exchange sur site.

## <a name="how-zap-works"></a>Fonctionnement de ZAP

Les signatures de courrier indésirable et de programmes malveillants sont mises à jour quotidiennement dans le service en temps réel. Toutefois, les utilisateurs peuvent toujours recevoir des messages malveillants pour diverses raisons, notamment si le contenu est en cours de saisie après avoir été remis aux utilisateurs. ZaP résout ce problème en surveillant en permanence les mises à jour des signatures de courrier indésirable et de programmes malveillants dans le service. ZAP peut rechercher et supprimer des messages qui se trouvent déjà dans la boîte aux lettres d’un utilisateur.

L’action ZAP est transparente pour l’utilisateur . Ils ne sont pas avertis si un message est détecté et déplacé.

[Les listes d’expéditeurs](create-safe-sender-lists-in-office-365.md)sûrs, les règles de flux de messagerie (également appelées règles de transport), les règles de boîte de réception ou les filtres supplémentaires prévalent sur ZAP. Comme dans le flux de messagerie, cela signifie que même si le service détermine que le message remis a besoin de zap, le message n’est pas agit en raison de la configuration des expéditeurs sûrs. C’est une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

### <a name="malware-zap"></a>ZAP anti-programme malveillant

Pour **les messages lus ou non** lus qui contiennent des programmes malveillants après remise, ZAP met en quarantaine le message qui contient la pièce jointe des programmes malveillants. Seuls les administrateurs peuvent afficher et gérer les messages de programmes malveillants mis en quarantaine.

La stratégie ZAP anti-programme malveillant est activée par défaut dans les stratégies anti-programme malveillant. Pour plus d’informations, voir [Configurer des stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

### <a name="phish-zap"></a>Phish ZAP

Pour les **messages** lus ou non lus identifiés comme étant du hameçonnage après  la remise, le résultat ZAP dépend de l’action configurée pour un verdict de filtrage du courrier de hameçonnage dans la stratégie anti-courrier indésirable applicable. Les actions de verdict de filtrage disponibles pour le hameçonnage et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X**, ajouter une ligne **d’objet avec** du texte : ZAP n’a aucune action sur le message.

- **Déplacer le message** vers le courrier indésirable : ZAP déplace le message vers le dossier Courrier indésirable, tant que la règle de courrier indésirable est activée sur la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, voir Configurer les paramètres du courrier indésirable sur les boîtes aux lettres [Exchange Online dans Microsoft 365.](configure-junk-email-settings-on-exo-mailboxes.md)

- **Rediriger le message vers l’adresse** **e-mail, supprimer le message,** **mettre en quarantaine le message**: ZAP met le message en quarantaine.

Par défaut, la protection ZAP de hameçonnage est activée  dans les stratégies anti-courrier indésirable et l’action par défaut pour le verdict de filtrage du courrier d’hameçonnage est le **message** de mise en quarantaine, ce qui signifie que le programme ZAP de hameçonnage met le message en quarantaine par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans Microsoft 365.](configure-your-spam-filter-policies.md)

### <a name="spam-zap"></a>ZAP de courrier indésirable

Pour **les messages** non lus identifiés comme courrier indésirable après la remise,  le résultat ZAP dépend de l’action configurée pour le verdict de filtrage du courrier indésirable dans la stratégie anti-courrier indésirable applicable. Les actions de verdict de filtrage disponibles pour le courrier indésirable et leurs résultats ZAP possibles sont décrites dans la liste suivante :

- **Ajouter un en-tête X,** ajouter une ligne **d’objet** avec du texte : ZAP n’a aucune action sur le message.

- **Déplacer le message** vers le courrier indésirable : ZAP déplace le message vers le dossier Courrier indésirable, tant que la règle de courrier indésirable est activée sur la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, voir Configurer les paramètres du courrier indésirable sur les boîtes aux lettres [Exchange Online dans Microsoft 365.](configure-junk-email-settings-on-exo-mailboxes.md)

- **Rediriger le message vers l’adresse** **e-mail, supprimer le message,** **mettre en quarantaine le message**: ZAP met le message en quarantaine. Les utilisateurs finaux peuvent afficher et gérer leurs propres messages de courrier indésirable mis en quarantaine.

Par défaut, la zap de courrier indésirable est activée dans  les stratégies anti-courrier indésirable et l’action par défaut pour le verdict de filtrage du courrier indésirable est Déplacer le **message** vers le dossier Courrier indésirable, ce qui signifie que le courrier indésirable ZAP déplace les **messages** non lus vers le dossier Courrier indésirable par défaut.

Pour plus d’informations sur la configuration des verdicts de filtrage du courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans Microsoft 365.](configure-your-spam-filter-policies.md)

### <a name="zap-considerations-for-microsoft-defender-for-office-365"></a>Considérations zap pour Microsoft Defender pour Office 365

ZAP ne met pas en quarantaine les [](atp-safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) messages en cours de remise dynamique dans l’analyse des pièces jointes sécurisées, ou lorsque le filtrage des programmes malveillants EOP a déjà remplacé la pièce jointe par le fichier Text.txtd’alerte **anti-programme** malveillant. Si un hameçonnage ou un signal de courrier indésirable est reçu pour ces types de messages et que le verdict de filtrage dans la stratégie anti-courrier indésirable est définie pour prendre une mesure sur le message (déplacer vers le courrier indésirable, la redirection, la suppression ou la mise en quarantaine), zap est définie par défaut sur une action « Déplacer vers le courrier indésirable ».

## <a name="how-to-see-if-zap-moved-your-message"></a>Comment savoir si ZAP a déplacé votre message

Pour déterminer si ZAP a déplacé votre message, vous pouvez utiliser le rapport d’état de la [protection](view-email-security-reports.md#threat-protection-status-report) contre les menaces ou l’Explorateur [de menaces (et les détections en temps réel).](threat-explorer.md) Notez qu’en tant qu’action système, ZAP n’est pas journalisé dans les journaux d’audit de la boîte aux lettres Exchange.

## <a name="zap-faq"></a>ZAP FAQ

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Que se passe-t-il si un message légitime est déplacé vers le dossier Courrier indésirable ?

Vous devez suivre le processus de création de rapports normal pour [les faux positifs.](report-junk-email-messages-to-microsoft.md) La seule raison pour laquelle le message serait déplacé de la boîte de réception vers le dossier Courrier indésirable serait parce que le service a déterminé que le message était du courrier indésirable ou malveillant.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Que se passe-t-il si j’utilise le dossier De quarantaine au lieu du dossier Courrier indésirable ?

ZAP prendra des mesures sur un message en fonction de la configuration de vos stratégies anti-courrier indésirable, comme décrit plus tôt dans cet article.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Que se passe-t-il si j’utilise des expéditeurs autorisés, des règles de flux de messagerie ou des listes d’expéditeurs autorisés/bloqués ?

Expéditeurs sûrs, règles de flux de messagerie ou blocage et autoriser les paramètres organisationnels à être prioritaire. Ces messages sont exclus de ZAP, car le service fait ce que vous avez configuré pour le faire. C’est une autre raison de faire attention à la configuration des messages pour contourner le filtrage.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>Que se passe-t-il si un message est déplacé vers un autre dossier (par exemple, règles de boîte de réception) ?

ZaP fonctionne toujours tant que le message n’a pas été supprimé, ou tant que la même action, ou plus forte, n’a pas encore été appliquée. Par exemple, si la stratégie anti-hameçonnage est mise en quarantaine et que le message se trouve déjà dans le courrier indésirable, ZAP prendra des mesures pour mettre le message en quarantaine.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>Comment la zap affecte-t-elle les boîtes aux lettres en attente ?

ZAP ne met pas en quarantaine les messages des boîtes aux lettres placées en attente. ZAP peut déplacer des messages vers le dossier Courrier indésirable en fonction de l’action configurée pour un verdict de courrier indésirable ou de hameçonnage dans les stratégies anti-courrier indésirable.

Pour plus d’informations sur les attentes dans Exchange Online, voir [In-Place Hold and Litigation Hold in Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/in-place-and-litigation-holds).
