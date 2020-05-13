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
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les contrôles de courrier indésirable sortants dans Exchange Online Protection (EOP) et la marche à suivre si vous devez envoyer des publipostages en masse.
ms.openlocfilehash: 99502e7fb55419dedb4d0f7d4a7e6c4591eff859
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208922"
---
# <a name="outbound-spam-protection-in-eop"></a>Protection contre le courrier indésirable sortant dans EOP

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîte aux lettres Exchange Online, nous prévoyons la gestion du courrier indésirable sortant. Un client qui envoie intentionnellement ou involontairement du courrier indésirable à partir de son organisation peut dégrader la réputation de l’ensemble du service et peut avoir une incidence sur la remise des messages pour d’autres clients.

Cette rubrique décrit les contrôles et les notifications conçus pour éviter le courrier indésirable sortant, et ce que vous pouvez faire si vous devez envoyer des publipostages en masse.

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Ce que les administrateurs peuvent faire pour contrôler le courrier indésirable sortant

- **Utiliser des notifications intégrées**: lorsqu’un utilisateur dépasse les limites d’envoi du [service](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou des [stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) et qu’il ne peut pas envoyer de courrier électronique, la stratégie d’alerte par défaut nommée **User Restricted from sending email** envoie des notifications par courrier électronique aux membres du groupe **TenantAdmins** (**administrateurs globaux**). Pour configurer les personnes qui reçoivent ces notifications, consultez [la rubrique vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Par ailleurs, les stratégies d’alerte par défaut nommées **e-mail Send Limit dépassées** et les **modèles d’envoi de courrier électronique suspects ont été détectés** envoyer des notifications par courrier électronique aux membres du groupe **TenantAdmins** (**administrateurs globaux**). Pour plus d’informations sur les stratégies d’alerte, accédez à [Stratégies d’alerte dans le centre de sécurité et conformité](../../compliance/alert-policies.md).

- **Passer en revue les plaintes de courrier indésirable émanant de fournisseurs de courrier tiers**: de nombreux services de messagerie comme Outlook.com, Yahoo et AOL fournissent une boucle de commentaires où, si un utilisateur de son service marque un E-mail de Microsoft 365 comme courrier indésirable, le message est empaqueté et renvoyé à nous pour révision. Pour en savoir plus sur la prise en charge de l’expéditeur pour Outlook.com, accédez à <https://sendersupport.olc.protection.outlook.com/pm/services.aspx> .

## <a name="how-eop-controls-outbound-spam"></a>Comment EOP contrôle le courrier indésirable sortant

- **Répartition du trafic de messagerie sortant**: tous les messages sortants envoyés via le service sont analysés pour rechercher le courrier indésirable. Si le message est identifié comme courrier indésirable, il est envoyé à partir d’un pool d’adresses IP secondaire, moins fiable, nommé _pool de remise à haut risque_. Pour plus d’informations, consultez la rubrique [pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).

- **Surveillance de notre réputation d’adresse IP source**: Microsoft 365 interroge différentes listes d’adresses IP bloquées. Une alerte est générée si l’une des adresses IP que nous utilisons pour le courrier électronique sortant apparaît sur ces listes. Cela nous permet de réagir rapidement quand le courrier indésirable a provoqué une dégradation de notre réputation. Lorsqu’une alerte est générée, nous disposons d’une documentation interne qui explique comment obtenir nos adresses IP supprimer (désinscrite) des listes rouges.

- **Désactiver les comptes qui envoient trop de courrier indésirable** <sup>\*</sup> : bien que nous puissions isoler le courrier indésirable sortant dans le pool de remise à haut risque, nous ne pouvons pas autoriser un compte (souvent un compte compromis) à envoyer indéfiniment du courrier indésirable. Nous Surveillez les comptes qui envoient du courrier indésirable, et lorsqu’ils dépassent une limite non divulguée, le compte ne peut pas envoyer de courrier électronique. Il existe différents seuils pour les utilisateurs individuels et l’ensemble du client.

- **Désactivation des comptes qui envoient trop de courriers électroniques trop rapidement** <sup>\*</sup> : en plus des limites qui recherchent les messages marqués comme courriers indésirables, il existe également des limites qui bloquent les comptes lorsqu’ils atteignent une limite globale de messages sortants, quel que soit le filtrage du courrier indésirable sur les messages sortants. Un compte compromis peut envoyer du courrier indésirable de zéro jour (non reconnu) par le filtre anti-courrier indésirable. Étant donné qu’il peut être difficile d’identifier une campagne de publipostage légitime contre une campagne de courrier indésirable, ces limites contribuent à minimiser les dommages potentiels.

<sup>\*</sup>Nous n’avons pas annoncé les limites exactes pour lesquelles les spammeurs ne peuvent pas jouer le système, et donc nous pouvons augmenter ou diminuer les limites en conséquence. Les limites sont suffisamment élevées pour empêcher un utilisateur d’entreprise moyen de les dépasser, et suffisamment bas pour aider à contenir les dommages causés par un expéditeur de courrier indésirable.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Recommandations pour les clients qui souhaitent envoyer des publipostages de masse via EOP

Il est difficile de trouver un équilibre entre les clients qui souhaitent envoyer un grand nombre de messages électroniques et la protection du service des comptes compromis et des expéditeurs de messages électroniques en masse avec des pratiques d’acquisition de destinataires médiocres. Le coût d’une source de courrier Microsoft 365 sur une liste d’adresses IP bloquées tierce est supérieur au blocage d’un utilisateur qui envoie trop de courriers électroniques.

Comme décrit dans la [Description du service Exchange Online](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits), l’utilisation d’EOP pour envoyer des messages en masse n’est pas prise en charge par le service, et n’est autorisée que sur la base du « meilleur effort ». Pour les clients qui souhaitent envoyer des courriers électroniques en masse, nous vous recommandons d’effectuer les solutions suivantes :

- **Envoyer des messages électroniques en masse via des serveurs de messagerie locaux**: cela signifie que les clients devront maintenir leur propre infrastructure de messagerie pour les publipostages.

- **Utiliser un fournisseur de courrier en nombre**tiers : il existe plusieurs fournisseurs de solutions de courrier en nombre tiers que vous pouvez utiliser pour envoyer des publipostages de masse. Ces sociétés ont un intérêt à collaborer avec les clients pour garantir de bonnes pratiques en matière d’envoi de courrier électronique.

Le groupe de travail de messagerie, mobile, anti-abus de programmes malveillants (MAAWG) publie sa liste d’appartenance sur <https://www.maawg.org/about/roster> . Plusieurs fournisseurs de courrier en masse figurent dans la liste et sont appelés citoyens Internet responsables.
