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
localization_priority: Normal
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
ms.openlocfilehash: f0ca5a61a7e71a2414fcaf1c0b02aec04820ca17
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58258271"
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

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent utiliser des messages mis en quarantaine en tant que programmes malveillants, hameçonnage à haut niveau de confiance ou suite à des règles de flux de messagerie (également appelées règles de transport). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

- Les utilisateurs peuvent utiliser des messages mis en quarantaine lorsqu’ils sont destinataires si le message a été mis en quarantaine en tant que courrier indésirable, courrier en nombre ou hameçonnage (depuis avril 2020). Pour plus d’informations, voir Rechercher et libérer les messages mis en quarantaine en tant [qu’utilisateur dans EOP.](find-and-release-quarantined-messages-as-a-user.md)

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage  mis en quarantaine, les administrateurs peuvent configurer une action différente pour le verdict de filtrage du courrier d’hameçonnage dans les stratégies anti-courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- Les administrateurs et les utilisateurs peuvent signaler les faux positifs à Microsoft en quarantaine.

Pour plus d’informations sur la mise en quarantaine, consultez la [faq sur la mise en quarantaine.](quarantine-faq.yml)
