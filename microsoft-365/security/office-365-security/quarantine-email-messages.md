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
ms.openlocfilehash: 48509dbc6f422a8de2ab0ee2e75fd5456087fc6f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60199416"
---
# <a name="quarantined-email-messages-in-eop"></a>Messages électroniques mis en quarantaine dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, la mise en quarantaine est disponible pour contenir les messages potentiellement dangereux ou indésirables.

Les stratégies anti-programme malveillant met automatiquement en quarantaine un message *si* des pièces jointes contiennent des programmes malveillants. Pour plus d’informations, voir [Configurer des stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

Par défaut, la protection anti-courrier indésirable met en quarantaine les messages de hameçonnage et de hameçonnage à haut niveau de confiance, et envoie le courrier indésirable, le courrier indésirable à niveau de confiance élevé et les messages électroniques en nombre dans le dossier Courrier indésirable de l’utilisateur. Toutefois, vous pouvez également créer et personnaliser des stratégies anti-courrier indésirable pour mettre en quarantaine le courrier indésirable, le courrier indésirable à niveau de confiance élevé et les messages électroniques en nombre. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Les utilisateurs et les administrateurs peuvent travailler avec les messages mis en quarantaine :

- _Les stratégies de_ mise en quarantaine définissent ce que les utilisateurs sont autorisés à faire ou non pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prise en charge). Les stratégies de mise en quarantaine par défaut appliquent les fonctionnalités historiques comme décrit ci-dessous. Les administrateurs peuvent créer et appliquer des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Par défaut, seuls les administrateurs peuvent utiliser des messages mis en quarantaine en tant que programmes malveillants, hameçonnage à haut niveau de confiance ou suite à des règles de flux de messagerie (également appelées règles de transport). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

- Par défaut, les utilisateurs peuvent travailler avec des messages mis en quarantaine lorsqu’ils sont destinataires et que le message a été mis en quarantaine en tant que courrier indésirable, courrier électronique en masse ou hameçonnage (sans hameçonnage à haut niveau de confiance). Pour plus d’informations, voir Rechercher et libérer les messages mis en quarantaine en tant [qu’utilisateur dans EOP.](find-and-release-quarantined-messages-as-a-user.md)

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage  mis en quarantaine, les administrateurs peuvent configurer une action différente pour le verdict de filtrage du courrier d’hameçonnage dans les stratégies anti-courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- Les administrateurs et les utilisateurs peuvent signaler les faux positifs à Microsoft en quarantaine.

Pour plus d’informations sur la mise en quarantaine, consultez la [faq sur la mise en quarantaine.](quarantine-faq.yml)
