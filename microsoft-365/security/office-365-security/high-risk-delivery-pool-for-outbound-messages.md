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
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Découvrez comment les pools de remise sont utilisés pour protéger la réputation des serveurs de messagerie dans Microsoft 365 centres de données.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 273d105ca600face4d79d70fc1622dfce8bf9f5e
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403836"
---
# <a name="outbound-delivery-pools"></a>Pools de livraison sortante

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les serveurs de messagerie dans Microsoft 365 centres de données peuvent être temporairement en raison de l’envoi de courrier indésirable. Par exemple, une attaque de programme malveillant ou de courrier indésirable malveillant dans une organisation de messagerie sur site qui envoie des messages sortants via Microsoft 365 ou compromis Microsoft 365 comptes. Les attaquants tentent également d’éviter la détection en relayant des messages via Microsoft 365 de messages.

Ces scénarios peuvent entraîner l’apparition de l’adresse IP Microsoft 365 serveurs de centres de données affectés sur des listes de blocage tierces. Les organisations de messagerie de destination qui utilisent ces listes d’adresses bloqués rejettent les messages provenant de Microsoft 365 sources de messages.

## <a name="high-risk-delivery-pool"></a>Pool de remise à risque élevé

Pour empêcher le blocage de nos adresses IP, tous les messages sortants provenant de serveurs de centres de données Microsoft 365 qui sont déterminés comme courrier indésirable sont envoyés via le pool de remise à _risque élevé_.

Le pool de remise à risque élevé est un pool d’adresses IP distinct pour les messages sortants qui est uniquement utilisé pour envoyer des messages de « faible qualité » (par exemple, courrier indésirable et [backscatter](backscatter-messages-and-eop.md)). L’utilisation du pool de remise à risque élevé permet d’empêcher le pool d’adresses IP normal pour le courrier sortant d’envoyer du courrier indésirable. Le pool d’adresses IP normal pour le courrier sortant conserve la réputation d’envoi de messages de « haute qualité », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes d’adresses IP bloqués.

La possibilité très réelle que les adresses IP du pool de remise à risque élevé soient placées sur des listes d’adresses IP bloqués demeure, mais cela est tout à fait possible. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages provenant du pool de remise à risque élevé.

Pour plus d’informations, voir [Contrôler le courrier indésirable sortant](outbound-spam-controls.md).

> [!NOTE]
> Les messages dans lequel le domaine de messagerie source n’a pas d’enregistrement A et aucun enregistrement MX défini dans le DNS public sont toujours acheminés via le pool de remise à risque élevé, quel que soit leur courrier indésirable ou leur disposition de limite d’envoi.
>
> Les messages qui dépassent les limites suivantes sont bloqués, de sorte qu’ils ne sont pas envoyés via le pool de remise à risque élevé :
>
> - [Limites d’envoi du service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).
> - [Stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) dans le cas où les expéditeurs ne peuvent pas envoyer de messages électroniques.

### <a name="bounce-messages"></a>Messages de non-rebond

Le pool de remise à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés notifications de non-remise, notifications de non-remise, notifications d’état de remise ou notifications d’état de remise).

Les causes possibles d’une augmentation des NDR sont les suivantes :

- Une campagne d’usurpation qui affecte l’un des clients qui utilisent le service.
- Une attaque de la recherche dans l’annuaire.
- Une attaque de courrier indésirable.
- Un serveur de messagerie non fiable.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de NDR traitées par le service. De nombreuses fois, ces NDR semblent être du courrier indésirable pour d’autres serveurs et services de messagerie (également appelé _[backscatter](backscatter-messages-and-eop.md)_).

### <a name="relay-pool"></a>Pool de relais

Les messages qui sont transmis ou relayés via Microsoft 365 dans certains scénarios sont envoyés à l’aide d’un pool de relais spécial, car la destination ne doit pas considérer Microsoft 365 comme l’expéditeur réel. Il est important pour nous d’isoler ce trafic de messagerie, car il existe des scénarios légitimes et non valides pour le transport automatique ou le relais du courrier électronique hors Microsoft 365. Comme pour le pool de remise à risque élevé, un pool d’adresses IP distinct est utilisé pour le courrier relayé. Ce pool d’adresses n’est pas publié car il peut changer souvent et ne fait pas partie de l’enregistrement SPF publié pour Microsoft 365.

Microsoft 365 doit vérifier que l’expéditeur d’origine est légitime afin de pouvoir remettre en toute confiance le message transmis.

Le message transmis ou relayé doit répondre à l’un des critères suivants pour éviter d’utiliser le pool de relais :

- L’expéditeur sortant se trouve dans [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- SPF passe lorsque le message s’Microsoft 365.
- DKIM sur le domaine de l’expéditeur est passé lorsque le message arrive Microsoft 365.

Vous pouvez savoir qu’un message a été envoyé via le pool de relais en regardant l’adresse IP du serveur sortant (le pool de relais sera compris dans la plage 40.95.0.0/16) ou en regardant le nom du serveur sortant (le nom du pool de relais sera « rly »).

Dans les cas où nous pouvons authentifier l’expéditeur, nous utilisons le schéma de réécriture de l’expéditeur (SRS) pour aider le système de messagerie du destinataire à savoir que le message transmis est issu d’une source fiable. Vous pouvez en savoir plus sur le fonctionnement et ce que vous pouvez faire pour vous assurer que le domaine d’envoi réussit l’authentification dans le schéma de réécriture d’expéditeurs [(SRS) dans Office 365](/office365/troubleshoot/antispam/sender-rewriting-scheme).

Pour que DKIM fonctionne, veillez à activer DKIM pour l’envoi du domaine. Par exemple, fabrikam.com fait partie de contoso.com et est défini dans les domaines acceptés de l’organisation. Si l’expéditeur du message sender@fabrikam.com, DKIM doit être activé pour fabrikam.com. Vous pouvez découvrir comment activer l’utilisation de DKIM pour valider les messages sortants [envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).

Pour ajouter un domaine personnalisé, suivez les étapes de [l’étape Ajouter un domaine à Microsoft 365](../../admin/setup/add-domain.md).

Si l’enregistrement MX de votre domaine pointe vers un service tiers ou un serveur de messagerie local, vous devez utiliser le filtrage amélioré pour [les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). Le filtrage amélioré garantit que la validation SPF est correcte pour le courrier entrant et évite d’envoyer des messages électroniques via le pool de relais.
