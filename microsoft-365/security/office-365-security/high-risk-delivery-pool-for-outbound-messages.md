---
title: Pools de remise sortants
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
description: Découvrez comment les pools de remise sont utilisés pour protéger la réputation des serveurs de messagerie dans les centres de connaissances Microsoft 365.
ms.openlocfilehash: 213149eda3dd121b65b64e3bddbb4bd73d66f57c
ms.sourcegitcommit: 6746fae2f68400fd985711b1945b66766d2a59a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "44419159"
---
# <a name="outbound-delivery-pools"></a>Pools de remise sortants

Les serveurs de messagerie dans les centres de connaissances Microsoft 365 peuvent être temporairement coupable d’envoyer du courrier indésirable. Par exemple, un programme malveillant ou une attaque de courrier indésirable malveillant dans une organisation de messagerie locale qui envoie des messages sortants via Microsoft 365 ou des comptes Microsoft 365 compromis. Les agresseurs essaient également d’éviter la détection en relayant les messages via le transfert de Microsoft 365.

Ces scénarios peuvent entraîner l’affichage de l’adresse IP des serveurs de centre de de session Microsoft 365 concernés qui apparaissent sur des listes rouges tierces. Les organisations de messagerie de destination qui utilisent ces listes rouges rejettent les messages provenant de ces sources de messages.

## <a name="high-risk-delivery-pool"></a>Pool de remise à haut risque
Pour éviter ce problème, tous les messages sortants des serveurs de centre de distribution Microsoft 365 définis comme courrier indésirable ou qui dépassent les limites d’envoi du [service](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou les [stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) sont envoyés via le _pool de remise à haut risque_.

Le pool de remise à haut risque est un pool d’adresses IP distinct pour le courrier électronique sortant, qui sert uniquement à envoyer des messages « de faible qualité » (par exemple, le courrier indésirable et [rétrodiffusion](backscatter-messages-and-eop.md)). Le pool de remise à haut risque empêche le pool d’adresses IP normal pour le courrier électronique sortant d’envoyer du courrier indésirable. Le pool d’adresses IP normales pour le courrier électronique sortant maintient la réputation envoyant des messages « de qualité supérieure », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes d’adresses IP bloquées.

La probabilité très réelle que les adresses IP dans le pool de remise à haut risque soient placées sur les listes d’adresses IP bloquées reste, mais cela est dû à la conception. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages du pool de remise à haut risque.

Pour plus d’informations, consultez la rubrique [contrôler le courrier indésirable sortant](outbound-spam-controls.md).

> [!NOTE]
> Messages dans lesquels le domaine de messagerie source n’a pas d’enregistrement a et aucun enregistrement MX défini dans DNS public n’est toujours routé via le pool de remise à haut risque, indépendamment de la disposition des limites d’envoi ou de courrier indésirable.

### <a name="bounce-messages"></a>Messages de retour

Le pool de remise à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés notifications d’échec de remise, messages de retransmission, notifications d’état de remise ou notifications d’échec de remise).

Voici les causes possibles d’une augmentation des notifications d’échec de remise :

- Une campagne d’usurpation d’identité qui affecte l’un des clients utilisant le service.
- Une attaque par extraction d’annuaire.
- Une attaque de courrier indésirable.
- Un serveur de messagerie non autorisé.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de notifications d’échec de remise traitées par le service. Bien souvent, ces notifications d’échec de remise semblent être du courrier indésirable pour les autres serveurs et services de messagerie (également appelés _[rétrodiffusion](backscatter-messages-and-eop.md)_).

## <a name="relay-pool"></a>Pool de relais

Les messages qui sont transférés ou relayés à partir de Microsoft 365 sont envoyés à l’aide d’un pool de relais spécial, étant donné que la destination finale ne doit pas considérer Microsoft 365 comme l’expéditeur réel. Il est également important pour nous d’isoler ce trafic, car il existe des scénarios légitimes et illegitmate pour le transfert de courriers électroniques à partir de Microsoft 365. À l’instar du pool de remise à haut risque, un pool d’adresses IP distinct est utilisé pour le courrier relayé. Ce pool d’adresses n’est pas publié, car il peut être modifié fréquemment. 

Microsoft 365 doit vérifier que l’expéditeur d’origine est légitime, afin que nous puissions le transmettre en toute confiance. Pour ce faire, l’authentification de messagerie (SPF, DKIM et DMARC) doit être transmise lorsque le message est envoyé à nous. Dans les cas où nous pouvons authentifier l’expéditeur, nous utilisons la réécriture de l’expéditeur pour aider le destinataire à savoir que le message transféré provient d’une source approuvée. Vous pouvez en savoir plus sur la façon dont cela fonctionne et sur les actions que vous pouvez effectuer pour vous assurer que le domaine d’envoi transmet l’authentification dans le [modèle de réécriture d’expéditeur (SRS)](https://docs.microsoft.com/office365/troubleshoot/antispam/sender-rewriting-scheme).
