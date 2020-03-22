---
title: Pool de remise à risque élevé pour les messages sortants
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Découvrez comment le pool de remise à haut risque est utilisé pour protéger la réputation des serveurs de messagerie dans les centres de ressources Office 365.
ms.openlocfilehash: 5d1bd2b14eb17ed74ee1cf1e44967f660f4595b8
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42895358"
---
# <a name="high-risk-delivery-pool-for-outbound-messages-in-office-365"></a>Pool de remise à haut risque pour les messages sortants dans Office 365

Les serveurs de messagerie dans les centres de 365 Office peuvent être temporairement coupable d’envoyer du courrier indésirable. Par exemple, un programme malveillant ou une attaque de courrier indésirable malveillant dans une organisation de messagerie locale qui envoie des messages sortants via Office 365 ou des comptes Office 365 compromis. Ces scénarios peuvent entraîner l’affichage de l’adresse IP des serveurs Office 365 Datacenter concernés qui apparaissent sur des listes rouges tierces. Les organisations de messagerie de destination qui utilisent ces listes rouges rejettent les messages provenant de ces sources de messages.

Pour éviter ce problème, tous les messages sortants provenant de serveurs Office 365 Datacenter qui sont considérés comme des courriers indésirables ou qui dépassent les limites d’envoi du [service](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou les [stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) sont envoyés via le _pool de remise à haut risque_.

Le pool de remise à haut risque est un pool d’adresses IP secondaire pour le courrier électronique sortant, qui sert uniquement à envoyer des messages « de faible qualité » (par exemple, le courrier indésirable et [rétrodiffusion](backscatter-messages-and-eop.md)). Le pool de remise à haut risque empêche le pool d’adresses IP normal pour le courrier électronique sortant d’envoyer du courrier indésirable. Le pool d’adresses IP normales pour le courrier électronique sortant maintient la réputation envoyant des messages « de qualité supérieure », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes d’adresses IP bloquées.

La probabilité très réelle que les adresses IP dans le pool de remise à haut risque soient placées sur les listes d’adresses IP bloquées reste, mais cela est dû à la conception. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages du pool de remise à haut risque.

Pour plus d’informations, consultez la rubrique [contrôler le courrier indésirable sortant dans Office 365](outbound-spam-controls.md).

> [!NOTE]
> Messages dans lesquels le domaine de messagerie source n’a pas d’enregistrement a et aucun enregistrement MX défini dans DNS public n’est toujours routé via le pool de remise à haut risque, indépendamment de la disposition des limites d’envoi ou de courrier indésirable.

## <a name="bounce-messages"></a>Messages de retour

Le pool de remise à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés notifications d’échec de remise, messages de retransmission, notifications d’état de remise ou notifications d’échec de remise).

Voici les causes possibles d’une augmentation des notifications d’échec de remise :

- Une campagne d’usurpation d’identité qui affecte l’un des clients utilisant le service.

- Une attaque par extraction d’annuaire.

- Une attaque de courrier indésirable.

- Un serveur de messagerie non autorisé.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de notifications d’échec de remise traitées par le service. Bien souvent, ces notifications d’échec de remise semblent être du courrier indésirable pour les autres serveurs et services de messagerie (également appelés _[rétrodiffusion](backscatter-messages-and-eop.md)_).
