---
title: Protection contre le courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les contrôles de courrier indésirable sortant dans Exchange Online Protection (EOP) et ce que vous devez faire si vous devez envoyer des messages électroniques de masse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0fb6bfe5d83c551c0a93cc7b453b27a2d7b476bc
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204365"
---
# <a name="outbound-spam-protection-in-eop"></a>Protection contre le courrier indésirable sortant dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ou des organisations autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, nous prenons au sérieux la gestion du courrier indésirable sortant. Même si un client envoie intentionnellement ou involontairement du courrier indésirable à partir de son organisation, cette action peut dégrader la réputation de l’ensemble du service et affecter la remise du courrier électronique pour d’autres clients.

Cet article décrit les contrôles et les notifications conçus pour empêcher le courrier indésirable sortant et ce que vous pouvez faire si vous devez envoyer des messages électroniques de masse.

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Ce que les administrateurs peuvent faire pour contrôler le courrier indésirable sortant

- Utilisez les **notifications intégrées**: lorsqu’un utilisateur dépasse [](configure-the-outbound-spam-policy.md) les limites d’envoi du [service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou des  stratégies de courrier indésirable sortant et ne peut pas envoyer de courrier électronique, la stratégie d’alerte par défaut nommée Utilisateur restreint l’envoi de messages électroniques envoie des notifications par courrier électronique aux membres du groupe **TenantAdmins** (**Administrateurs** globaux). Pour configurer qui d’autre reçoit ces notifications, voir Vérifier les [paramètres d’alerte pour les utilisateurs restreints.](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users) En outre, les  stratégies d’alerte par défaut nommées Limite d’envoi de courrier électronique ont dépassé et les modèles d’envoi de courrier suspect **détectés** envoient des notifications par courrier électronique aux membres du groupe **TenantAdmins** (**Administrateurs** globaux). Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

- Examiner les **réclamations** de courrier indésirable de fournisseurs de messagerie tiers : de nombreux services de messagerie tels que Outlook.com, Yahoo et AOL fournissent une boucle de commentaires dans laquelle, si un utilisateur de son service marque un courrier électronique provenant de Microsoft 365 comme courrier indésirable, le message est mis en pack et renvoyé pour révision. Pour en savoir plus sur la prise en charge des expéditeurs Outlook.com, voir <https://sendersupport.olc.protection.outlook.com/pm/services.aspx> .

## <a name="how-eop-controls-outbound-spam"></a>Comment EOP contrôle le courrier indésirable sortant

- **Répartition du trafic de courrier sortant**: tous les messages sortants envoyés via le service sont analysés pour y trouver du courrier indésirable. Si le message est déterminé comme courrier indésirable, il est remis à partir d’un pool d’adresses IP secondaire moins fiable nommé pool de remise à _risque élevé._ Pour plus d’informations, voir [Pool de remise à risque élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).

- **Surveillance de la réputation de notre adresse IP source**: Microsoft 365 interroge diverses listes d’adresses IP tierces. Une alerte est générée si l’une des adresses IP que nous utilisons pour le courrier électronique sortant apparaît sur ces listes. Cette surveillance nous permet de réagir rapidement lorsque le courrier indésirable a dégradé notre réputation. Lorsqu’une alerte est générée, nous avons une documentation interne qui explique comment supprimer nos adresses IP (supprimées) des listes rouge.

- Désactivez les comptes qui envoient trop de courrier indésirable : même si nous séparons le courrier indésirable sortant dans le pool de remise à risque élevé, nous ne pouvons pas autoriser un compte (souvent, un compte compromis) à envoyer du courrier indésirable <sup>\*</sup> indéfiniment. Nous surveillons les comptes qui envoient du courrier indésirable et lorsqu’ils dépassent une limite non divulguée, l’envoi de courriers électroniques est bloqué pour le compte. Il existe différents seuils pour les utilisateurs individuels et l’ensemble du client.

- Désactivation de comptes qui envoient trop de messages électroniques trop rapidement : outre les limites qui recherchent les messages marqués comme courrier indésirable, il existe également des limites qui bloquent les comptes lorsqu’ils atteignent une limite globale de messages sortants, quel que soit le verdict de filtrage du courrier indésirable sur les <sup>\*</sup> messages sortants. Un compte compromis peut envoyer du courrier indésirable « zero-day » (précédemment non reconnu) qui est manqué par le filtre de courrier indésirable. Étant donné qu’il peut être difficile d’identifier une campagne de publipostage de masse légitime par rapport à une campagne de courrier indésirable, ces limites permettent de minimiser les dommages potentiels.

<sup>\*</sup> Nous n’publions pas les limites exactes afin que les expéditeurs de courrier indésirable ne peuvent pas jouer au système, et donc nous pouvons augmenter ou diminuer les limites si nécessaire. Les limites sont suffisamment élevées pour empêcher un utilisateur commercial moyen de les dépasser et suffisamment faibles pour vous aider à contenir les dommages causés par un expéditeur de courrier indésirable.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Recommandations clients qui souhaitent envoyer des publipostages de masse via EOP

Il est difficile de trouver un équilibre entre les clients qui souhaitent envoyer un grand volume de courriers électroniques par rapport à la protection du service contre les comptes compromis et les expéditeurs de courrier en masse ayant des pratiques d’acquisition médiocres de destinataires. Le coût d’une source Microsoft 365 courrier électronique à l’arrivée sur une liste d’adresses IP tierces est supérieur au blocage d’un utilisateur qui envoie trop de messages électroniques.

Comme décrit dans la description du service [Exchange Online,](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits)l’utilisation d’EOP pour envoyer des messages électroniques en bloc n’est pas une utilisation prise en charge du service et n’est autorisée que sur la base du « meilleur effort ». Pour les clients qui souhaitent envoyer des messages électroniques en masse, nous vous recommandons les solutions suivantes :

- **Envoyer des messages électroniques en** bloc via des serveurs de messagerie locaux : les clients conservent leur propre infrastructure de messagerie pour les publipostages de masse.

- **Utilisez un fournisseur de messagerie** en bloc tiers : il existe plusieurs fournisseurs tiers de solutions de messagerie en bloc que vous pouvez utiliser pour envoyer des messages de masse. Ces sociétés ont tout intérêt à collaborer avec leurs clients pour garantir de bonnes pratiques d’envoi de courrier électronique.

Le groupe de travail de messagerie, mobile, anti-abus de programmes malveillants (MAAWG) publie sa liste d’appartenance à <https://www.maawg.org/about/roster> l'. Plusieurs fournisseurs de messagerie en masse sont répertoriés et sont connus comme citoyens Internet responsables.
