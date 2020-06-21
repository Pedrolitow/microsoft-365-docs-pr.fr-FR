---
title: Informations sur la correction du domaine de l’expéditeur
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur la rubrique Fix sender Domain Insight dans le tableau de bord du flux de messagerie dans le centre de sécurité & Compliance Center.
ms.openlocfilehash: c4cf4a87ad770325ca6ad2f0b87ac8ce52c345c2
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818830"
---
# <a name="fix-sender-domain-insight"></a>Informations sur la correction du domaine de l’expéditeur

Microsoft 365 nécessite des messages envoyés à partir d’environnements de messagerie internes locaux à Microsoft 365 pour répondre à certains critères de sécurité :

- Vous avez créé un connecteur entrant dans Microsoft 365 pour authentifier les connexions SMTP à partir de votre serveur de messagerie local à l’aide de l’adresse IP source ou d’un certificat.

- Vous avez configuré votre serveur de messagerie local de sorte qu’il relaie le courrier électronique via Microsoft 365 vers le monde externe.

- Dans votre configuration, l’une des affirmations suivantes est vraie :

  - Le domaine de messagerie de l’expéditeur est enregistré dans votre organisation. Pour plus d’informations, consultez l’article Ajouter un domaine à Office 365.

  - Votre serveur de messagerie local est configuré pour utiliser un certificat pour envoyer un message électronique à Microsoft 365, le certificat contient ou correspond exactement à un nom de domaine que vous avez enregistré dans Microsoft 365, et vous avez créé un connecteur basé sur un certificat dans Microsoft 365 avec ce domaine. 

Les messages qui ne répondent pas aux critères ne sont pas attribués à l’organisation et peuvent être rejetés.

L’article **Fix sender Domain** Insight affiche les messages électroniques provenant de votre environnement local qui ne répondent pas aux critères, vous permet d’identifier les ordinateurs et les comptes d’utilisateur potentiellement compromis dans votre environnement de messagerie local et vous aide à prendre des mesures correctives.

![Le tableau de bord des expéditeurs du tableau de bord du flux de messagerie dans le centre de sécurité & conformité](../../media/sender-domain-insight-selected.png)

Lorsque vous cliquez sur **afficher les détails**, vous êtes dirigé vers un autre widget avec plus de détails, comme illustré dans le diagramme suivant :

![Le widget détails de la solution Fix sender Domain Insight](../../media/sender-domain-view-details.png)

Vous verrez le connecteur entrant qui a été utilisé pour livrer les messages à Office 365. Vous pouvez également cliquer sur **afficher un exemple d’ID de message** pour afficher les détails des messages qui ont été envoyés à partir de votre environnement de messagerie local. Étant donné que ces messages ont été rejetés par Office 365, vous ne pouvez pas utiliser le suivi des messages, mais vous pouvez utiliser l’exemple d’ID de message pour suivre les messages dans votre environnement de messagerie local.

![Afficher des exemples d’ID de message dans la fenêtre Fix sender Domain Insight](../../media/sender-domain-view-sample-message-ids.png)

## <a name="related-topics"></a>Voir aussi

Pour plus d’informations sur les autres flux de messagerie dans le tableau de bord de flux de messagerie, voir [mail Flow Insights in the Security & Compliance Center](mail-flow-insights-v2.md).
