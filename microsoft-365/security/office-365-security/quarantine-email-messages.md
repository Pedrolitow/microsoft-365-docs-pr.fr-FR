---
title: Quarantaine dans Office 365
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
description: Cet article explique la mise en quarantaine dans Microsoft 365. La mise en quarantaine bloque les messages potentiellement dangereux ou indésirables.
ms.openlocfilehash: 396be17e07a347ab4d28a3e0b67dd137bda999db
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44033865"
---
# <a name="quarantine-email-messages"></a>Mettre en quarantaine les messages électroniques

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, la mise en quarantaine est disponible pour le blocage des messages potentiellement dangereux ou indésirables.

Les stratégies de protection contre les programmes malveillants configurent automatiquement un message si *une* pièce jointe contient un programme malveillant. Pour plus d’informations, consultez la rubrique [configure anti-malware Policies in Office 365](configure-anti-malware-policies.md).

Par défaut, les stratégies de blocage du courrier indésirable mettent en quarantaine les messages d’hameçonnage et délivrent les messages de courrier indésirable et de courrier en nombre dans le dossier de courrier indésirable de l’utilisateur. Toutefois, vous pouvez également créer et personnaliser des stratégies de blocage du courrier indésirable pour mettre en quarantaine le courrier indésirable et les messages électroniques en bloc. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

Les utilisateurs et les administrateurs peuvent travailler avec des messages mis en quarantaine :

- Les administrateurs peuvent utiliser tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent travailler avec des messages mis en quarantaine en tant que programme malveillant, hameçonnage à haute fiabilité ou suite à des règles de flux de messagerie (également appelées règles de transport). Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans Office 365](manage-quarantined-messages-and-files.md).

- Les utilisateurs peuvent travailler avec des messages mis en quarantaine, où ils sont destinataires si le message a été mis en quarantaine en tant que courrier indésirable, message électronique en masse ou (depuis avril, 2020). Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Office 365](find-and-release-quarantined-messages-as-a-user.md).

  Pour empêcher les utilisateurs de gérer leurs propres messages de hameçonnage mis en quarantaine, les administrateurs peuvent configurer une autre action pour le verdict de filtrage du **courrier électronique de hameçonnage** dans les stratégies de blocage du courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

- Les administrateurs et les utilisateurs peuvent signaler des faux positifs à Microsoft en quarantaine.

Pour plus d’informations sur la mise en quarantaine, consultez la rubrique [mise en quarantaine](quarantine-faq.md).
