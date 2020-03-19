---
title: Notifications de courrier indésirable à l’utilisateur final dans Office 36
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
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
description: Lorsqu’un administrateur Active les notifications de courrier indésirable de l’utilisateur final dans les stratégies de blocage du courrier indésirable, les destinataires des messages reçoivent régulièrement des notifications sur leurs messages mis en quarantaine.
ms.openlocfilehash: 67dbf311c37ae61c007b78110522033d79c0b161
ms.sourcegitcommit: fe4beef350ef9f39b1098755cff46fa2b8e7dc4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "42857144"
---
# <a name="end-user-spam-notifications-in-office-365"></a>Notifications de courrier indésirable à l’utilisateur final dans Office 365

La mise en quarantaine bloque les messages potentiellement dangereux ou indésirables dans les organisations Office 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online. Pour plus d’informations, consultez la rubrique [mise en quarantaine dans Office 365](quarantine-email-messages.md).

Par défaut, les notifications de courrier indésirable de l’utilisateur final sont désactivées dans les stratégies anti-courrier indésirable. Lorsqu’un administrateur [active les notifications de courrier indésirable de l’utilisateur final](configure-your-spam-filter-policies.md), les destinataires des messages reçoivent régulièrement des notifications sur leurs messages mis en quarantaine en tant que courrier indésirable, en masse ou (depuis avril 2020).

> [!NOTE]
> En octobre 2019, nous avons supprimé la possibilité de débloquer les messages mis en quarantaine directement à partir des notifications de courrier indésirable de l’utilisateur final. Au lieu de cela, les utilisateurs peuvent désormais accéder au centre de conformité Office 365 Security & pour libérer leurs messages mis en quarantaine (soit directement, soit en cliquant sur **examiner** dans la notification). Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans Office 365](find-and-release-quarantined-messages-as-a-user.md). <br/><br/> Les messages mis en quarantaine en tant que courriers indésirables de confiance élevée, programmes malveillants ou les règles de flux de messagerie (également appelées règles de transport) ne sont accessibles qu’aux administrateurs. Pour plus d’informations, consultez la rubrique [Rechercher et débloquer les messages mis en quarantaine en tant qu’administrateur dans Office 365](find-and-release-quarantined-messages-as-an-administrator.md).

Une notification de courrier indésirable de l’utilisateur final contient les informations suivantes pour chaque message en quarantaine :

- **Expéditeur**: le nom d’envoi et l’adresse de messagerie du message en quarantaine.

- **Objet**: texte de la ligne d’objet du message en quarantaine.

- **Date**: date et heure (UTC) auxquelles le message a été mis en quarantaine.

- **Bloquer l’expéditeur**: cliquez sur ce lien pour ajouter l’expéditeur à votre liste des expéditeurs bloqués.

- **Révision**: cliquez sur ce lien pour accéder à la mise en quarantaine dans le centre de sécurité & conformité, dans lequel vous pouvez libérer, supprimer ou signaler vos messages mis en quarantaine.

![Exemple de notification de courrier indésirable pour l’utilisateur final](../../media/end-user-spam-notification.png)
