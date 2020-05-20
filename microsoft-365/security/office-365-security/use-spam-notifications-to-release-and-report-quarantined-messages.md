---
title: Notifications de courrier indésirable à l’utilisateur final dans Microsoft 365
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
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les notifications de courrier indésirable de l’utilisateur final pour les messages mis en quarantaine dans Exchange Online Protection (EOP).
ms.openlocfilehash: 7d4cf21ade504e999dc5b53ad9062977369561c6
ms.sourcegitcommit: 4ce28ad4d17d336106c1720d65349f19f9e90e04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "44294240"
---
# <a name="use-user-spam-notifications-to-release-and-report-quarantined-messages"></a>Utiliser les notifications de courrier indésirable de l’utilisateur pour publier et signaler les messages mis en quarantaine

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, consultez la rubrique [messages en quarantaine dans EOP](quarantine-email-messages.md).

Par défaut, les notifications de courrier indésirable de l’utilisateur final sont désactivées dans les stratégies anti-courrier indésirable. Lorsqu’un administrateur [active les notifications de courrier indésirable de l’utilisateur final](configure-your-spam-filter-policies.md#configure-end-user-spam-notifications), les destinataires (y compris les boîtes aux lettres partagées) reçoivent des notifications périodiques sur leurs messages mis en quarantaine en tant que courrier indésirable, en masse ou (depuis avril 2020).

> [!NOTE]
> Les messages mis en quarantaine en tant que courriers indésirables de confiance élevée, programmes malveillants ou les règles de flux de messagerie (également appelées règles de transport) ne sont accessibles qu’aux administrateurs. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

Une notification de courrier indésirable de l’utilisateur final contient les informations suivantes pour chaque message en quarantaine :

- **Expéditeur**: le nom d’envoi et l’adresse de messagerie du message en quarantaine.

- **Objet**: texte de la ligne d’objet du message en quarantaine.

- **Date**: date et heure (UTC) auxquelles le message a été mis en quarantaine.

- **Bloquer l’expéditeur**: cliquez sur ce lien pour ajouter l’expéditeur à votre liste des expéditeurs bloqués. Pour plus d’informations, consultez [la rubrique bloquer un expéditeur de courrier dans Outlook](https://support.office.com/article/b29fd867-cac9-40d8-aed1-659e06a706e4).

- **Release**: pour les messages de courrier indésirable (pas de hameçonnage), vous pouvez diffuser le message sans mettre en quarantaine le centre de sécurité & conformité.

- **Révision**: cliquez sur ce lien pour accéder à la quarantaine dans le centre de sécurité & conformité, dans lequel vous pouvez libérer, supprimer ou signaler vos messages mis en quarantaine. Pour plus d’informations, consultez [la rubrique Rechercher et débloquer les messages mis en quarantaine en tant qu’utilisateur dans EOP](find-and-release-quarantined-messages-as-a-user.md).

![Exemple de notification de courrier indésirable pour l’utilisateur final](../../media/end-user-spam-notification.png)
