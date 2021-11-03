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
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la mise en quarantaine Exchange Online Protection (EOP) qui contient des messages potentiellement dangereux ou indésirables.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 58097b5dba60c1ea085ea6e78c878982abe24021
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60668453"
---
# <a name="quarantined-email-messages-in-eop-and-defender-for-office-365"></a>Messages électroniques mis en quarantaine dans EOP et Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, la mise en quarantaine est disponible pour contenir les messages potentiellement dangereux ou indésirables.

Les stratégies anti-programme malveillant met automatiquement en quarantaine un message *si* des pièces jointes contiennent des programmes malveillants. Pour plus d’informations, voir [Configurer des stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

Par défaut, la protection anti-courrier indésirable met en quarantaine les messages de hameçonnage et de hameçonnage à haut niveau de confiance, et envoie le courrier indésirable, le courrier indésirable à niveau de confiance élevé et les messages électroniques en masse dans le dossier Courrier indésirable de l’utilisateur. Toutefois, vous pouvez également créer et personnaliser des stratégies anti-courrier indésirable pour mettre en quarantaine le courrier indésirable, le courrier indésirable à niveau de confiance élevé et les messages électroniques en nombre. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Les utilisateurs et les administrateurs peuvent travailler avec les messages mis en quarantaine :

- _Les stratégies de_ mise en quarantaine définissent ce que les utilisateurs sont autorisés à faire ou non pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prise en charge). Les stratégies de mise en quarantaine par défaut appliquent les fonctionnalités historiques comme décrit ci-dessous. Les administrateurs peuvent créer et appliquer des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs, ainsi que des notifications de mise en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Par défaut, seuls les administrateurs peuvent utiliser des messages mis en quarantaine en tant que programmes malveillants, hameçonnage à haut niveau de confiance ou suite à des règles de flux de messagerie (également appelées règles de transport). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

- Par défaut, les utilisateurs peuvent travailler avec des messages mis en quarantaine lorsqu’ils sont destinataires et que le message a été mis en quarantaine en tant que courrier indésirable, courrier électronique en masse ou hameçonnage (sans hameçonnage à haut niveau de confiance). Pour plus d’informations, voir Rechercher et libérer les messages mis en quarantaine en tant [qu’utilisateur dans EOP.](find-and-release-quarantined-messages-as-a-user.md)

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage mis en quarantaine,  les administrateurs peuvent affecter une stratégie de mise en quarantaine qui refuse l’accès aux messages mis en quarantaine à partir du verdict de filtrage du courrier de hameçonnage dans les stratégies anti-courrier indésirable. Pour plus d’informations, voir Attribuer des stratégies de mise en quarantaine dans les stratégies de mise en quarantaine des [stratégies anti-courrier](quarantine-policies.md#anti-spam-policies)[indésirable.](quarantine-policies.md)

- Les administrateurs et les utilisateurs peuvent signaler les faux positifs à Microsoft en quarantaine.

- La durée de mise en quarantaine des messages mis en quarantaine avant leur expiration varie en fonction de la raison pour laquelle le message a été mis en quarantaine. Les fonctionnalités qui met en quarantaine les messages et leurs périodes de rétention correspondantes sont décrites dans le tableau suivant :

  <br>

  ****

  |Raison de la mise en quarantaine :|Période de rétention par défaut|Personnalisable ?|Commentaires|
  |---|:---:|:---:|---|
  |Messages mis en quarantaine par des stratégies anti-courrier indésirable : courrier indésirable, courrier indésirable à niveau de confiance élevé, hameçonnage, hameçonnage à haut niveau de confiance ou en bloc.|30 jours|Oui|Vous pouvez configurer (plus bas) cette valeur dans les stratégies anti-courrier indésirable. Pour plus d’informations, consultez le paramètre Conserver le courrier indésirable en quarantaine pendant ce nombre de jours **(** _QuarantineRetentionPeriod_) dans Configurer des stratégies [anti-courrier indésirable.](configure-your-spam-filter-policies.md)|
  |Messages mis en quarantaine par les stratégies anti-hameçonnage : veille contre l’usurpation d’adresse dans EOP ; emprunt d’identité d’utilisateur, emprunt d’identité de domaine ou intelligence de boîte aux lettres dans Defender pour Office 365.|30 jours|Oui|Cette période de rétention est  également contrôlée par le paramètre Conserver le courrier indésirable en quarantaine pendant ce nombre de jours _(QuarantineRetentionPeriod_) dans les stratégies **anti-courrier** indésirable. La période de rétention utilisée est la valeur de la première stratégie **anti-courrier** indésirable correspondante dans qui le destinataire est défini.|
  |Messages mis en quarantaine par des stratégies anti-programme malveillant (messages malveillants).|15 jours|Non||
  |Messages mis en quarantaine par les stratégies Coffre pièces jointes dans Defender pour Office 365 (messages malveillants).|15 jours|Non||
  |Messages mis en quarantaine par des règles de flux de messagerie : l’action consiste à remettre le **message** en quarantaine hébergé _(mise en quarantaine)._|30 jours|Non||
  |Fichiers mis en quarantaine par Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams (fichiers malveillants).|15 jours|Non||
  |

  Lorsqu’un message arrive à expiration de la quarantaine, vous ne pouvez pas le récupérer.

Pour plus d’informations sur la mise en quarantaine, consultez [la FAQ sur la mise en quarantaine.](quarantine-faq.yml)
