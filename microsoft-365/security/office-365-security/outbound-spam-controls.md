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
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les contrôles de courrier indésirable sortant dans Exchange Online Protection (EOP) et sur ce qu’il faut faire si vous avez besoin d’envoyer des messages électroniques en masse.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 3fd225db90d245f03be3b7f5a8c5846c1c96cd25
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68060403"
---
# <a name="outbound-spam-protection-in-eop"></a>Protection contre le courrier indésirable sortant dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans Exchange Online boîtes aux lettres, nous prenons la gestion du courrier indésirable sortant au sérieux. Même si un client envoie intentionnellement ou involontairement du courrier indésirable de son organisation, cette action peut dégrader la réputation de l’ensemble du service et affecter la remise de courrier électronique pour d’autres clients.

Cet article décrit les contrôles et les notifications conçus pour empêcher le courrier indésirable sortant, et ce que vous pouvez faire si vous avez besoin d’envoyer des publipostages en masse.

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Ce que les administrateurs peuvent faire pour contrôler le courrier indésirable sortant

- **Utiliser des notifications intégrées** : lorsqu’un utilisateur dépasse les limites d’envoi du [service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou des [stratégies de courrier indésirable sortant](configure-the-outbound-spam-policy.md) et qu’il ne peut pas envoyer de courrier électronique, la stratégie d’alerte par défaut nommée **Utilisateur limité à l’envoi de notifications par e-mail** envoie des notifications par e-mail aux membres du groupe **TenantAdmins** (**administrateurs généraux**). Pour configurer qui d’autre reçoit ces notifications, consultez [Vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). En outre, les stratégies d’alerte par défaut nommées **Email limite d’envoi dépassée** et **les modèles d’envoi d’e-mails suspects détectés** envoient des notifications par e-mail aux membres du groupe **TenantAdmins** (**administrateurs généraux**). Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

- **Passez en revue les plaintes de courrier indésirable émanant de fournisseurs de courrier tiers** : de nombreux services de messagerie tels que Outlook.com, Yahoo et AOL fournissent une boucle de commentaires dans laquelle si un utilisateur de leur service marque un e-mail de Microsoft 365 comme courrier indésirable, le message est empaqueté et renvoyé à nous pour révision. Pour en savoir plus sur la prise en charge des expéditeurs pour Outlook.com, accédez à <https://sendersupport.olc.protection.outlook.com/pm/services.aspx>.

## <a name="how-eop-controls-outbound-spam"></a>Comment EOP contrôle le courrier indésirable sortant

- **Séparation du trafic de courrier sortant** : chaque message sortant envoyé via le service est analysé à la recherche de courrier indésirable. Si le message est déterminé comme courrier indésirable, il est remis à partir d’un pool d’adresses IP secondaires moins réputé nommé pool de _remises à haut risque_. Pour plus d’informations, voir [Pool de remise à risque élevé pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md).

- **Surveillance de notre réputation d’adresse IP source** : Microsoft 365 interroge différentes listes de blocs d’adresses IP tierces. Une alerte est générée si l’une des adresses IP que nous utilisons pour les e-mails sortants apparaît sur ces listes. Cette surveillance nous permet de réagir rapidement lorsque le courrier indésirable a causé une dégradation de notre réputation. Lorsqu’une alerte est générée, nous disposons d’une documentation interne qui explique comment supprimer nos adresses IP (supprimées) des listes de blocs.

- **Désactiver les comptes qui envoient trop de courrier indésirable**<sup>\*</sup> : même si nous séparons le courrier indésirable sortant dans le pool de remises à haut risque, nous ne pouvons pas autoriser un compte (souvent, un compte compromis) à envoyer indéfiniment du courrier indésirable. Nous surveillons les comptes qui envoient du courrier indésirable et, lorsqu’ils dépassent une limite non divulguée, le compte ne peut pas envoyer de courrier électronique. Il existe différents seuils pour les utilisateurs individuels et l’ensemble du locataire.

- **Désactivation des comptes qui envoient trop de courriers électroniques trop rapidement**<sup>\*</sup> : outre les limites qui recherchent les messages marqués comme courrier indésirable, il existe également des limites qui bloquent les comptes lorsqu’ils atteignent une limite globale de messages sortants, quel que soit le verdict de filtrage du courrier indésirable sur les messages sortants. Un compte compromis peut envoyer un courrier indésirable de jour zéro (précédemment non reconnu) qui est manqué par le filtre de courrier indésirable. Étant donné qu’il peut être difficile d’identifier une campagne de publipostage de masse légitime et une campagne de courrier indésirable, ces limites permettent de minimiser les dommages potentiels.

<sup>\*</sup> Nous ne publions pas les limites exactes afin que les spammeurs ne puissent pas jouer au système, et donc nous pouvons augmenter ou diminuer les limites si nécessaire. Les limites sont suffisamment élevées pour empêcher un utilisateur professionnel moyen de les dépasser, et suffisamment faibles pour aider à contenir les dommages causés par un spammeur.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Recommandations pour les clients qui souhaitent envoyer des publipostages en masse via EOP

Il est difficile de trouver un équilibre entre les clients qui souhaitent envoyer un grand volume de courriers électroniques et la protection du service contre les comptes compromis et les expéditeurs de courrier en bloc avec des pratiques d’acquisition de destinataires médiocres. Le coût de l’arrivée d’une source de messagerie Microsoft 365 sur une liste de blocage d’adresses IP tierces est supérieur au blocage d’un utilisateur qui envoie trop d’e-mails.

Comme décrit dans la [Exchange Online Description du service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits), l’utilisation d’EOP pour envoyer des e-mails en bloc n’est pas une utilisation prise en charge du service et n’est autorisée que sur la base du « meilleur effort ». Pour les clients qui souhaitent envoyer des e-mails en bloc, nous vous recommandons les solutions suivantes :

- **Envoyer des e-mails en bloc via des serveurs de messagerie locaux : les** clients gèrent leur propre infrastructure de messagerie pour les publipostages en masse.

- **Utilisez un fournisseur de messagerie en bloc tiers** : il existe plusieurs fournisseurs de solutions de courrier en bloc tiers que vous pouvez utiliser pour envoyer des publipostages en masse. Ces entreprises ont tout intérêt à collaborer avec les clients pour garantir de bonnes pratiques d’envoi de courrier électronique.

Le Groupe de travail de messagerie, mobile, anti-abus de logiciels malveillants (MAAWG) publie sa liste de membres à l’adresse <https://www.maawg.org/about/roster>. Plusieurs fournisseurs de courrier en bloc figurent sur la liste et sont connus pour être des citoyens internet responsables.
