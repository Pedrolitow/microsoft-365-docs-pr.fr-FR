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
ms.openlocfilehash: ac3469150ef5cf5c1040fcddf7f0bc95e7a18805
ms.sourcegitcommit: 7ee50882cb4ed37794a3cd82dac9b2f9e0a1f14a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2021
ms.locfileid: "51599910"
---
# <a name="outbound-delivery-pools"></a>Pools de livraison sortante

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les serveurs de messagerie dans les centres de données Microsoft 365 peuvent ne pas pouvoir envoyer de courrier indésirable temporairement. Par exemple, une attaque de programme malveillant ou de courrier indésirable dans une organisation de messagerie sur site qui envoie du courrier sortant via Microsoft 365 ou des comptes Microsoft 365 compromis. Les attaquants tentent également d’éviter la détection en relayant des messages via le forwarding Microsoft 365.

Ces scénarios peuvent entraîner l’apparition de l’adresse IP des serveurs de centre de données Microsoft 365 affectés sur des listes de blocage tierces. Les organisations de messagerie de destination qui utilisent ces listes de blocage rejetteront les messages provenant de ces sources de messages.

## <a name="high-risk-delivery-pool"></a>Pool de remise à risque élevé
Pour éviter cela, tous les messages sortants provenant de serveurs de centre de données Microsoft 365 [](configure-the-outbound-spam-policy.md) qui sont déterminés comme courrier indésirable ou qui dépassent les limites d’envoi du [service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou des stratégies de courrier indésirable sortant sont envoyés via le _pool_ de remise à risque élevé.

Le pool de remise à risque élevé est un pool d’adresses IP distinct pour les messages sortants qui est uniquement utilisé pour envoyer des messages de « faible qualité » (par exemple, courrier indésirable et [backscatter).](backscatter-messages-and-eop.md) L’utilisation du pool de remise à risque élevé permet d’empêcher le pool d’adresses IP normal pour le courrier sortant d’envoyer du courrier indésirable. Le pool d’adresses IP normal pour le courrier sortant conserve la réputation d’envoi de messages de « haute qualité », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes d’adresses IP bloqués.

La possibilité réelle que les adresses IP du pool de remise à risque élevé soient placées sur des listes d’adresses IP bloqués demeure, mais cela est tout à fait possible. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages provenant du pool de remise à risque élevé.

Pour plus d’informations, voir [Contrôler le courrier indésirable sortant.](outbound-spam-controls.md)

> [!NOTE]
> Les messages pour lequel le domaine de messagerie source n’a pas d’enregistrement A et aucun enregistrement MX défini dans le DNS public sont toujours acheminés via le pool de remise à risque élevé, quel que soit leur courrier indésirable ou leur disposition de limite d’envoi.

### <a name="bounce-messages"></a>Messages de non-rebond

Le pool de remise à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés notifications de non-remise, notifications de non-remise, notifications d’état de remise ou notifications d’état de remise).

Les causes possibles d’une augmentation des NDR sont les suivantes :

- Une campagne d’usurpation qui affecte l’un des clients qui utilisent le service.
- Une attaque de la recherche dans l’annuaire.
- Une attaque de courrier indésirable.
- Un serveur de messagerie non fiable.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de NDR traitées par le service. De nombreuses fois, ces NDR semblent être du courrier indésirable pour d’autres serveurs et services de messagerie (également appelé _[backscatter).](backscatter-messages-and-eop.md)_
