---
title: Messages électroniques mis en quarantaine
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la quarantaine dans Exchange Online Protection (EOP) qui contient des messages potentiellement dangereux ou indésirables.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 000b6d37dea1280371bef2a2e32e9c2b5e61383c
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68091738"
---
# <a name="quarantined-email-messages-in-eop-and-defender-for-office-365"></a>Messages électroniques mis en quarantaine dans EOP et Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, la mise en quarantaine est disponible pour contenir des messages potentiellement dangereux ou indésirables.

Les stratégies anti-programme malveillant mettent automatiquement en quarantaine un message si _une_ pièce jointe contient des programmes malveillants. Pour plus d’informations, consultez [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

Par défaut, les stratégies anti-courrier indésirable met en quarantaine les messages de hameçonnage et de hameçonnage à haut niveau de confiance, et fournissent le courrier indésirable, le courrier indésirable à haut niveau de confiance et les messages électroniques en bloc dans le dossier Courrier indésirable Email de l’utilisateur. Toutefois, vous pouvez également créer et personnaliser des stratégies anti-courrier indésirable pour mettre en quarantaine le courrier indésirable, le courrier indésirable à haut niveau de confiance et les messages électroniques en bloc. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Les utilisateurs et les administrateurs peuvent travailler avec des messages mis en quarantaine :

- _Les stratégies de quarantaine_ définissent ce que les utilisateurs sont autorisés à faire ou non aux messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prises en charge). Les stratégies de quarantaine par défaut appliquent les fonctionnalités historiques, comme décrit ci-dessous. Les administrateurs peuvent créer et appliquer des stratégies de quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs, et activent également les notifications de quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Par défaut, seuls les administrateurs peuvent utiliser des messages qui ont été mis en quarantaine sous forme de programmes malveillants, de hameçonnage à haut niveau de confiance ou à la suite de règles de flux de courrier (également appelées règles de transport). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

- Par défaut, les utilisateurs peuvent utiliser des messages mis en quarantaine lorsqu’ils sont destinataires et que le message a été mis en quarantaine en tant que courrier indésirable, courrier électronique en bloc ou hameçonnage (hameçonnage non fiable). Pour plus d’informations, consultez [Rechercher et libérer des messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md).

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage mis en quarantaine, les administrateurs peuvent attribuer une stratégie de quarantaine qui refuse l’accès aux messages mis en quarantaine à partir du verdict de filtrage des **e-mails de hameçonnage** dans les stratégies anti-courrier indésirable. Pour plus d’informations, consultez [Affecter des stratégies de quarantaine dans les stratégies anti-courrier indésirable](quarantine-policies.md#anti-spam-policies)[Stratégies de quarantaine](quarantine-policies.md).

- Les administrateurs et les utilisateurs peuvent signaler des faux positifs à Microsoft en quarantaine.

- La durée pendant laquelle les messages mis en quarantaine sont maintenus en quarantaine avant leur expiration varie en fonction de la raison pour laquelle le message a été mis en quarantaine. Les fonctionnalités qui mettent en quarantaine les messages et leurs périodes de rétention correspondantes sont décrites dans le tableau suivant :

  |Raison de la mise en quarantaine :|Période de rétention par défaut|Personnalisable?|Comments|
  |---|---|:---:|---|
  |Messages mis en quarantaine par des stratégies anti-courrier indésirable : courrier indésirable, courrier indésirable à haut niveau de confiance, hameçonnage, hameçonnage à haut niveau de confiance ou en bloc.|15 jours : <ul><li>Dans la stratégie anti-courrier indésirable par défaut.</li><li>Dans les stratégies anti-courrier indésirable que vous créez dans PowerShell.</li></ul> <p> 30 jours dans les stratégies anti-courrier indésirable que vous créez dans le portail Microsoft 365 Defender.|Oui|Vous pouvez configurer (inférieur) cette valeur dans les stratégies anti-courrier indésirable. Pour plus d’informations, consultez le paramètre **Conserver le courrier indésirable en quarantaine pour ce nombre de jours** (_QuarantineRetentionPeriod_) dans [Configurer les stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).|
  |Messages mis en quarantaine par des stratégies anti-hameçonnage : renseignement sur l’usurpation d’identité dans EOP ; l’emprunt d’identité de l’utilisateur, l’emprunt d’identité de domaine ou l’intelligence de boîte aux lettres dans Defender pour Office 365.|30 jours|Oui|Cette période de rétention est également contrôlée par le paramètre **Conserver le courrier indésirable en quarantaine pour ce nombre de jours** (_QuarantineRetentionPeriod_) dans les stratégies **anti-courrier indésirable** . La période de rétention utilisée est la valeur de la première stratégie **anti-courrier indésirable** correspondante dans laquelle le destinataire est défini.|
  |Messages mis en quarantaine par des stratégies anti-programme malveillant (messages malveillants).|30 jours|Non||
  |Messages mis en quarantaine par des stratégies de pièces jointes sécurisées dans Defender pour Office 365 (messages de programmes malveillants).|30 jours|Non||
  |Messages mis en quarantaine par des règles de flux de courrier : l’action consiste **à remettre le message à la mise en quarantaine hébergée** (_quarantaine_).|30 jours|Non||
  |Fichiers mis en quarantaine par des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams (fichiers de programmes malveillants).|30 jours|Non|Les fichiers mis en quarantaine dans SharePoint ou OneDrive sont supprimés après 30 jours, mais les fichiers bloqués restent dans SharePoint ou OneDrive dans l’état bloqué.|

  Quand un message expire de la quarantaine, vous ne pouvez pas le récupérer.

Pour plus d’informations sur la quarantaine, consultez [faq sur la quarantaine](quarantine-faq.yml).
