---
title: Notifications de courrier indésirable pour l’utilisateur final Microsoft 365
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
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les notifications de courrier indésirable pour les messages mis en quarantaine dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a07a4196b9ad936c6dc83d8eb300332ad9aaac47
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177331"
---
# <a name="use-user-spam-notifications-to-release-and-report-quarantined-messages"></a>Utiliser les notifications de courrier indésirable de l’utilisateur pour libérer et signaler les messages mis en quarantaine

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, [voir Messages mis en quarantaine dans EOP.](quarantine-email-messages.md)

Par défaut, les notifications de courrier indésirable de l’utilisateur final sont désactivées dans les stratégies anti-courrier indésirable. Lorsqu’un administrateur active les notifications de courrier indésirable à l’utilisateur final, les [destinataires](configure-your-spam-filter-policies.md#configure-end-user-spam-notifications)(y compris les boîtes aux lettres partagées) reçoivent des notifications périodiques concernant leurs messages mis en quarantaine comme courrier indésirable, courrier en masse ou hameçonnage (depuis avril 2020).

Pour les boîtes aux lettres partagées, les notifications de courrier indésirable à l’utilisateur final sont uniquement pris en charge pour les utilisateurs qui ont reçu l’autorisation Autorisation totale sur la boîte aux lettres partagée. Pour plus d’informations, voir [Utiliser le EAC pour modifier la délégation de boîte aux lettres partagée.](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation)

> [!NOTE]
> Les messages qui ont été mis en quarantaine en tant que hameçonnage à haut niveau de confiance, programmes malveillants ou par des règles de flux de messagerie (également appelées règles de transport) ne sont disponibles que pour les administrateurs. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).
>
> Les notifications de courrier indésirable de l’utilisateur final ne sont pas prises en charge pour les groupes.

Une notification de courrier indésirable à l’utilisateur final contient les informations suivantes pour chaque message mis en quarantaine :

- **Expéditeur :** nom d’envoi et adresse e-mail du message mis en quarantaine.
- **Objet**: texte de la ligne d’objet du message mis en quarantaine.
- **Date**: date et heure (au UTC) de mise en quarantaine du message.
- **Bloquer l’expéditeur**: cliquez sur ce lien pour ajouter l’expéditeur à la liste des expéditeurs bloqués sur votre boîte aux lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Release**: pour les messages de courrier indésirable (et non  de hameçonnage), vous pouvez libérer le message ici sans passer en quarantaine sur Microsoft 365 Defender portail.
- **Révision**: cliquez sur  ce lien pour passer en quarantaine dans le portail Microsoft 365 Defender, où vous pouvez (selon la raison de la mise en quarantaine du message) afficher, libérer, supprimer ou signaler vos messages mis en quarantaine. Pour plus d’informations, voir Rechercher et libérer les messages mis en quarantaine en tant [qu’utilisateur dans EOP.](find-and-release-quarantined-messages-as-a-user.md)

![Exemple de notification de courrier indésirable à l’utilisateur final.](../../media/end-user-spam-notification.png)

> [!NOTE]
> Un expéditeur bloqué peut toujours vous envoyer des messages électroniques. Tous les messages provenant de cet expéditeur qui se déplacent vers votre boîte aux lettres sont immédiatement déplacés vers le dossier Courrier indésirable. Les futurs messages de cet expéditeur seront placés dans votre dossier Courrier indésirable ou mis en quarantaine par l’utilisateur final. Si vous souhaitez supprimer ces messages à l’arrivée au lieu de les mettre en quarantaine, utilisez des règles de flux de messagerie [(également](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) appelées règles de transport) pour supprimer les messages à l’arrivée.
