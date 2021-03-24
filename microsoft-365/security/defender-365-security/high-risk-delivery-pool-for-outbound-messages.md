---
title: Pools de livraison sortante
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Découvrez comment les pools de remise sont utilisés pour protéger la réputation des serveurs de messagerie dans les centres de données Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 461b5f9aa0407c5115ab84a075c793139a8b4305
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063369"
---
# <a name="outbound-delivery-pools"></a>Pools de livraison sortante

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les serveurs de messagerie dans les centres de données Microsoft 365 peuvent être temporairement en cours d’envoi de courrier indésirable. Par exemple, une attaque de programme malveillant ou de courrier indésirable malveillant dans une organisation de messagerie sur site qui envoie du courrier sortant via Microsoft 365 ou des comptes Microsoft 365 compromis. Les attaquants tentent également d’éviter la détection en relayant des messages via le forwarding Microsoft 365.

Ces scénarios peuvent entraîner l’apparition de l’adresse IP des serveurs de centre de données Microsoft 365 affectés sur des listes d’adresses IP tierces. Les organisations de messagerie de destination qui utilisent ces listes d’adresses bloqués rejettent les messages provenant de ces sources de messages.

## <a name="high-risk-delivery-pool"></a>Pool de remise à risque élevé
Pour éviter cela, tous les messages sortants provenant de serveurs de centre de données Microsoft 365 [](configure-the-outbound-spam-policy.md) qui sont déterminés comme courrier indésirable ou qui dépassent les limites d’envoi du [service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou des stratégies de courrier indésirable sortant sont envoyés via le _pool_ de remise à risque élevé.

Le pool de remise à risque élevé est un pool d’adresses IP distinct pour les messages sortants qui est uniquement utilisé pour envoyer des messages de « faible qualité » (par exemple, courrier indésirable et [backscatter).](backscatter-messages-and-eop.md) L’utilisation du pool de remise à risque élevé permet d’empêcher le pool d’adresses IP normal pour le courrier sortant d’envoyer du courrier indésirable. Le pool d’adresses IP normal pour le courrier sortant conserve la réputation d’envoi de messages de « haute qualité », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes d’adresses IP bloqués.

La possibilité réelle que les adresses IP du pool de remise à risque élevé soient placées sur des listes d’adresses IP bloqués demeure, mais cela est tout à fait possible. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages provenant du pool de remise à risque élevé.

Pour plus d’informations, voir [Contrôler le courrier indésirable sortant.](outbound-spam-controls.md)

> [!NOTE]
> Les messages dans lequel le domaine de messagerie source n’a pas d’enregistrement A et aucun enregistrement MX défini dans le DNS public sont toujours acheminés via le pool de remise à risque élevé, quel que soit leur courrier indésirable ou leur disposition de limite d’envoi.

### <a name="bounce-messages"></a>Messages de non-rebond

Le pool de remise à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés notifications de non-remise, notifications de non-remise, notifications d’état de remise ou notifications d’état de remise).

Les causes possibles d’une augmentation des NDR sont les suivantes :

- Une campagne d’usurpation qui affecte l’un des clients qui utilisent le service.
- Une attaque de la recherche dans l’annuaire.
- Une attaque de courrier indésirable.
- Un serveur de messagerie non fiable.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de NDR traitées par le service. De nombreuses fois, ces NDR semblent être du courrier indésirable pour d’autres serveurs et services de messagerie (également appelé _[backscatter).](backscatter-messages-and-eop.md)_

## <a name="relay-pool"></a>Pool de relais

Les messages qui sont transmis ou relayés à partir de Microsoft 365 sont envoyés à l’aide d’un pool de relais spécial, car la destination finale ne doit pas considérer Microsoft 365 comme l’expéditeur réel. Il est également important pour nous d’isoler ce trafic, car il existe des scénarios légitimes et non valides pour laforwarding automatique ou le relais du courrier électronique à partir de Microsoft 365. Comme pour le pool de remise à risque élevé, un pool d’adresses IP distinct est utilisé pour le courrier relayé. Ce pool d’adresses n’est pas publié, car il peut changer souvent.

Microsoft 365 doit vérifier que l’expéditeur d’origine est légitime afin de pouvoir remettre en toute confiance le message transmis. Pour ce faire, l’authentification de messagerie (SPF, DKIM et DMARC) doit être directe lorsque le message nous est envoyé. Dans les cas où nous pouvons authentifier l’expéditeur, nous utilisons la réécriture de l’expéditeur pour aider le destinataire à savoir que le message transmis est issu d’une source fiable. Vous pouvez en savoir plus sur le fonctionnement et ce que vous pouvez faire pour vous assurer que le domaine d’envoi passe l’authentification dans le schéma de réécriture de l’expéditeur [(SRS).](/office365/troubleshoot/antispam/sender-rewriting-scheme)