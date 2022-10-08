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
- m365-security
description: Découvrez comment les pools de remise sont utilisés pour protéger la réputation des serveurs de messagerie dans les centres de données Microsoft 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 7e36798475041f454e7ba41c49e94a87cff38cc6
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68090616"
---
# <a name="outbound-delivery-pools"></a>Pools de livraison sortante

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Email serveurs dans les centres de données Microsoft 365 peuvent être temporairement coupables d’envoi de courrier indésirable. Par exemple, un programme malveillant ou une attaque de courrier indésirable malveillant dans une organisation de messagerie locale qui envoie des messages sortants via Microsoft 365 ou des comptes Microsoft 365 compromis. Les attaquants essaient également d’éviter la détection en relayant des messages via le transfert Microsoft 365.

Ces scénarios peuvent entraîner l’apparition de l’adresse IP des serveurs de centre de données Microsoft 365 concernés sur des listes de blocage tierces. Les organisations de messagerie de destination qui utilisent ces listes de blocage rejettent les e-mails provenant de ces sources de messages Microsoft 365.

## <a name="high-risk-delivery-pool"></a>Pool de remises à haut risque

Pour empêcher le blocage de nos adresses IP, tous les messages sortants des serveurs de centre de données Microsoft 365 qui sont déterminés comme courrier indésirable sont envoyés via le _pool de remises à haut risque_.

Le pool de remises à haut risque est un pool d’adresses IP distinct pour les e-mails sortants qui est utilisé uniquement pour envoyer des messages de « faible qualité » (par exemple, courrier indésirable et [rétrodiffusion](backscatter-messages-and-eop.md)). L’utilisation du pool de remise à haut risque permet d’empêcher le pool d’adresses IP normal pour les e-mails sortants d’envoyer du courrier indésirable. Le pool d’adresses IP normal pour les e-mails sortants conserve la réputation d’envoyer des messages de « haute qualité », ce qui réduit la probabilité que ces adresses IP apparaissent sur les listes de blocage IP.

La possibilité très réelle que les adresses IP dans le pool de remise à haut risque soient placées sur des listes de blocage d’adresses IP reste, mais c’est par conception. La remise aux destinataires prévus n’est pas garantie, car de nombreuses organisations de messagerie n’acceptent pas les messages du pool de remise à haut risque.

Pour plus d’informations, consultez [Contrôler le courrier indésirable sortant](outbound-spam-controls.md).

> [!NOTE]
> Les messages où le domaine de messagerie source n’a pas d’enregistrement A et aucun enregistrement MX défini dans le DNS public sont toujours routés via le pool de remise à haut risque, quel que soit leur courrier indésirable ou leur disposition de limite d’envoi.
>
> Les messages qui dépassent les limites suivantes sont bloqués, de sorte qu’ils ne sont pas envoyés via le pool de remise à haut risque :
>
> - [Limites d’envoi du service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).
> - [Stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) dans lesquelles les expéditeurs sont limités à l’envoi de courriers.

### <a name="bounce-messages"></a>Messages de rebond

Le pool de remises à haut risque sortant gère la remise de tous les rapports de non-remise (également appelés NDR, messages de rebond, notifications d’état de remise ou DSN).

Les causes possibles d’une augmentation des DNR sont les suivantes :

- Une campagne d’usurpation d’identité qui affecte l’un des clients utilisant le service.
- Une attaque de récolte de répertoires.
- Une attaque par courrier indésirable.
- Un serveur de courrier non fiable.

Tous ces problèmes peuvent entraîner une augmentation soudaine du nombre de DNR traités par le service. De nombreuses fois, ces DNR semblent être du courrier indésirable pour d’autres serveurs et services de messagerie (également _[appelés rétrodiffusion](backscatter-messages-and-eop.md)_).

### <a name="relay-pool"></a>Pool de relais

Les messages transférés ou relayés via Microsoft 365 dans certains scénarios seront envoyés à l’aide d’un pool de relais spécial, car la destination ne doit pas considérer Microsoft 365 comme l’expéditeur réel. Il est important pour nous d’isoler ce trafic de messagerie, car il existe des scénarios légitimes et non valides pour le transfert automatique ou le relais de courrier électronique à partir de Microsoft 365. Comme pour le pool de remises à haut risque, un pool d’adresses IP distinct est utilisé pour le courrier relayé. Ce pool d’adresses n’est pas publié, car il peut changer souvent et ne fait pas partie de l’enregistrement SPF publié pour Microsoft 365.

Microsoft 365 doit vérifier que l’expéditeur d’origine est légitime afin que nous puissions remettre le message transféré en toute confiance.

Le message transféré ou relayé doit répondre à l’un des critères suivants pour éviter d’utiliser le pool de relais :

- L’expéditeur sortant se trouve dans un [domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- SPF est transmis lorsque le message arrive à Microsoft 365.
- DKIM sur le domaine de l’expéditeur passe lorsque le message est envoyé à Microsoft 365.

Vous pouvez indiquer qu’un message a été envoyé via le pool de relais en examinant l’adresse IP du serveur sortant (le pool de relais se trouve dans la plage 40.95.0.0/16) ou en examinant le nom du serveur sortant (le nom du serveur sortant est « rly »).

Dans les cas où nous pouvons authentifier l’expéditeur, nous utilisons le schéma de réécriture de l’expéditeur (SRS) pour aider le système de messagerie du destinataire à savoir que le message transféré provient d’une source approuvée. Vous pouvez en savoir plus sur le fonctionnement et sur ce que vous pouvez faire pour vous assurer que le domaine d’envoi réussit l’authentification dans le [schéma de réécriture de l’expéditeur (SRS) dans Office 365](/office365/troubleshoot/antispam/sender-rewriting-scheme).

Pour que DKIM fonctionne, veillez à activer DKIM pour l’envoi du domaine. Par exemple, fabrikam.com fait partie de contoso.com et est défini dans les domaines acceptés de l’organisation. Si l’expéditeur du message est sender@fabrikam.com, DKIM doit être activé pour fabrikam.com. Vous pouvez lire comment activer l’option [Utiliser DKIM pour valider les e-mails sortants envoyés à partir de votre domaine personnalisé](use-dkim-to-validate-outbound-email.md).

Pour ajouter un domaine personnalisé, suivez les étapes décrites dans [Ajouter un domaine à Microsoft 365](../../admin/setup/add-domain.md).

Si l’enregistrement MX de votre domaine pointe vers un service tiers ou un serveur de messagerie local, vous devez utiliser le [filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). Le filtrage amélioré garantit que la validation SPF est correcte pour les messages entrants et évitera d’envoyer des e-mails via le pool de relais.
