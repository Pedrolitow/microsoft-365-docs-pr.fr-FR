---
title: Messages électroniques mis en quarantaine
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 4c234874-015e-4768-8495-98fcccfc639b
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la mise en quarantaine dans Exchange Online Protection (EOP) qui contient des messages potentiellement dangereux ou indésirables.
ms.openlocfilehash: 71a5f32fe6888d751bf2c4020fca4df671ac96d1
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208281"
---
# <a name="quarantined-email-messages-in-eop"></a>Messages électroniques mis en quarantaine dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, la mise en quarantaine est disponible pour le blocage des messages potentiellement dangereux ou indésirables.

Les stratégies de protection contre les programmes malveillants configurent automatiquement un message si *une* pièce jointe contient un programme malveillant. Pour plus d’informations, consultez la rubrique [configure anti-malware Policies in EOP](configure-anti-malware-policies.md).

Par défaut, les stratégies de blocage du courrier indésirable mettent en quarantaine les messages d’hameçonnage et délivrent les messages de courrier indésirable et de courrier en nombre dans le dossier de courrier indésirable de l’utilisateur. Toutefois, vous pouvez également créer et personnaliser des stratégies de blocage du courrier indésirable pour mettre en quarantaine le courrier indésirable et les messages électroniques en bloc. Pour plus d’informations, consultez la rubrique [configurer des stratégies de blocage du courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Les utilisateurs et les administrateurs peuvent travailler avec des messages mis en quarantaine :

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent travailler avec des messages mis en quarantaine en tant que programme malveillant, hameçonnage à haute fiabilité ou suite à des règles de flux de messagerie (également appelées règles de transport). Pour plus d’informations, consultez la rubrique [gestion des messages et des fichiers mis en quarantaine en tant qu’administrateur dans EOP](manage-quarantined-messages-and-files.md).

- Les utilisateurs peuvent travailler avec des messages mis en quarantaine, où ils sont destinataires si le message a été mis en quarantaine en tant que courrier indésirable, en masse ou (depuis avril 2020). Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md).

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage mis en quarantaine, les administrateurs peuvent configurer une autre action pour le verdict de filtrage du **courrier électronique de hameçonnage** dans les stratégies de blocage du courrier indésirable. Pour plus d’informations, consultez la rubrique [configurer des stratégies de blocage du courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- Les administrateurs et les utilisateurs peuvent signaler des faux positifs à Microsoft en quarantaine.

Pour plus d’informations sur la mise en quarantaine, consultez la rubrique [mise en quarantaine](quarantine-faq.md).
