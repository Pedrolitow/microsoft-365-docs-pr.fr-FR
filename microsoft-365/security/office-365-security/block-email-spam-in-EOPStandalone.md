---
title: Bloquer le courrier indésirable dans EOP autonome
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
ms.reviewer: andypunt
manager: dansimp
ms.date: 2/25/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MOE150
- MET150
ms.assetid: da21c0b6-e8f0-4cc8-af2e-5029a9433d59
ms.collection:
- M365-security-compliance
description: Document pour les administrateurs autonomes d’EOP afin d’éviter le courrier indésirable faux négatifs
ms.openlocfilehash: b3b4005016d8a4192241299cac50eddf59f332d5
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42895416"
---
# <a name="customize-the-office-365-anti-spam-filter-with-these-settings"></a>Paramètres pour personnaliser le filtre anti-courrier indésirable Office 365

Un administrateur peut utiliser plusieurs paramètres du filtre anti-courrier indésirable Office 365 pour empêcher l’envoi de courrier indésirable dans la boîte de réception d’un utilisateur. Grâce aux options suivantes, le filtre anti-courrier indésirable Office 365 sera plus efficace pour bloquer le courrier indésirable et éviter les faux négatifs. Dans ce contexte, un faux négatif désigne un message indésirable envoyé dans une boîte de réception.

## <a name="block-ip-addresses-with-a-connection-filter"></a>Blocage des adresses IP avec un filtrage des connexions

Personnalisez votre filtre anti-courrier indésirable Office 365 en ajoutant l’adresse IP de l’expéditeur à la liste d’adresses IP bloquées du filtrage des connexions :

1. Obtenez les en-têtes du message que vous souhaitez bloquer dans votre client de messagerie tel qu’Outlook ou Outlook sur le web (anciennement connu sous le nom d’Outlook Web App), comme décrit dans [Afficher les en-têtes de messages Internet dans Outlook](https://support.office.com/article/cd039382-dc6e-4264-ac74-c048563d212c).

2. Recherchez l’adresse IP qui suit la balise CIP dans l’en-tête X-Forefront-Antispam-Report à l’aide de l’[analyseur d’en-têtes de message](https://testconnectivity.microsoft.com/?tabid=mha) ou manuellement.

3. Ajoutez l’adresse IP à la liste d’adresses IP bloquées en suivant les étapes décrites dans la section « Utilisation du Centre d’administration Exchange (CAE) pour modifier la stratégie par défaut de filtrage des connexions », dans l’article [Configuration de la stratégie de filtrage des connexions](configure-the-connection-filter-policy.md).

### <a name="block-bulk-mail-with-mail-flow-rules-transport-rules-or-the-spam-filter"></a>Blocage du courrier en nombre à l’aide des règles de flux de messagerie (règles de transport) ou du filtre anti-courrier indésirable

Le courrier indésirable que vous recevez comprend-il essentiellement du courrier en nombre, par exemple des bulletins d’informations ou des promotions ? Vous pouvez personnaliser le filtre anti-courrier indésirable dans Office 365 si vous [utilisez les règles de flux de messagerie pour configurer le filtrage du courrier en nombre](use-transport-rules-to-configure-bulk-email-filtering.md) ou activez le paramètre **Courrier en nombre** dans les [options de filtrage avancé du courrier indésirable dans Office 365](advanced-spam-filtering-asf-options.md) de votre filtre anti-courrier indésirable. Dans le Centre d’administration Exchange, cliquez sur **Protection** \> **Filtrage du contenu**, puis double-cliquez sur la stratégie de filtrage à ajuster. Cliquez sur **Actions du courrier indésirable** pour ajuster les paramètres, comme illustré ci-dessous.

![Définition du filtre de courrier en nombre dans Exchange Online](../../media/a45095c2-269d-45b8-a76c-999b5e78da68.png)

### <a name="block-email-spam-using-spam-filter-block-lists"></a>Blocage du courrier indésirable à l’aide des listes de blocage du filtre anti-courrier indésirable

[Configurez vos stratégies de filtrage du courrier indésirable dans Office 365](configure-your-spam-filter-policies.md) pour ajouter l’adresse de l’expéditeur à la liste des expéditeurs bloqués ou le domaine à la liste des domaines bloqués dans le filtre anti-courrier indésirable. Les e-mails provenant d’un expéditeur ou d’un domaine figurant dans l’une de ces listes seront marqués comme courrier indésirable.

## <a name="email-users-can-also-help-ensure-that-false-negative-and-email-spam-is-blocked-with-office-365-spam-filter"></a>Blocage des faux négatifs et du courrier indésirable par les utilisateurs eux-mêmes avec le filtre anti-courrier indésirable Office 365

Pour vous aider à bloquer les faux négatifs et le courrier indésirable dans Office 365, nous vous recommandons d’inviter vos utilisateurs à ajouter l’adresse de l’expéditeur du courrier indésirable à leur liste d’expéditeurs bloqués dans [Outlook](https://support.office.com/article/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) ou [Outlook sur le Web](https://support.office.com/article/db786e79-54e2-40cc-904f-d89d57b7f41d). Dans Outlook Web App, cliquez sur **Paramètres** \> **Options** \> **Bloquer ou autoriser**, puis ajoutez l’adresse à la liste des **Expéditeurs bloqués**, comme illustré ci-dessous.

![Blocage d’un expéditeur dans Outlook sur le Web ](../../media/fdf51381-2527-4819-ac2a-5dff84d2a36d.png)

> [!NOTE]
> Pour en savoir plus sur les listes d’expéditeurs autorisés, voir [Créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md).

## <a name="eop-only-customers-set-up-directory-synchronization"></a>Clients d’EOP : utilisez la synchronisation d’annuaires

Pour éviter les faux négatifs, nous vous recommandons de synchroniser les paramètres utilisateur avec le service via la synchronisation d’annuaires pour que la liste des expéditeurs bloqués soit respectée. Pour en savoir plus, consultez la section « Utilisation de la synchronisation d’annuaires pour gérer les utilisateurs de messagerie », dans l’article « Gestion des utilisateurs de messagerie dans EOP ».

## <a name="eop-only-customers-who-are-not-using-directory-synchronization"></a>Clients d’EOP qui n’utilisent pas la synchronisation d’annuaires

Le service EOP prend en compte les listes des expéditeurs autorisés et bloqués définies par l’utilisateur, si ces informations ont été transmises au service. Si vous êtes un client d’EOP qui utilise Outlook, et que la synchronisation d’annuaires n’est pas configurée pour synchroniser vos utilisateurs avec Office 365, vous pouvez quand même empêcher l’envoi de messages dans la boîte de réception de vos utilisateurs en utilisant la liste d’expéditeurs bloqués. En revanche, vous devrez peut-être configurer certaines règles de flux de messagerie Exchange dans les cas suivants :

- Si un message passe à travers le filtrage anti-courrier indésirable normal via EOP puis est remis dans un serveur Exchange local, et si EOP attribue un verdict SCL 1-4 (non indésirable), la liste des expéditeurs bloqués locale de vos utilisateurs remplace le verdict du filtre anti-courrier indésirable d’EOP et envoie le message dans leur dossier Courrier indésirable.

- Si le verdict SCL -1 est attribué à un message dans EOP par une règle de flux de messagerie Exchange ou parce que l’adresse IP ou le domaine figure dans votre liste d’expéditeurs autorisés, la valeur SCL se propage au serveur Exchange local via les connecteurs. Dans ce cas, la liste d’expéditeurs bloqués de votre utilisateur n’est pas prise en compte. Pour modifier ce paramètre, vous pouvez créer une règle de flux de messagerie locale qui définit la valeur SCL sur 0. Ainsi, Outlook sera obligé de prendre en compte la liste d’expéditeurs bloqués locale de votre utilisateur.

### <a name="to-set-up-a-mail-flow-rule-to-stop-messages-from-being-delivered-to-your-users-inbox-by-using-the-blocked-senders-list"></a>Pour configurer une règle de flux de courrier afin d’arrêter la remise de messages à la boîte de réception des utilisateurs à l’aide de la liste d’expéditeurs bloqués

1. Ouvrez l’Environnement de ligne de commande Exchange Management Shell de votre serveur local. Pour savoir comment ouvrir l’environnement de ligne de commande Exchange Management Shell dans votre organisation Exchange locale, consultez l’article [Ouverture de l’environnement de ligne de commande Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/exchange-server/open-the-exchange-management-shell).

2. Exécutez la commande suivante pour déplacer les messages indésirables dont le contenu a été filtré vers le dossier Courrier indésirable et attribuer la valeur SCL -1 à tous les messages :

   ```powershell
   New-TransportRule "NameForRule" -HeaderContainsMessageHeader "X-Forefront-Antispam-Report" -HeaderContainsWords "SCL:-1" -SetSCL 0
   ```

   Dans la mesure où la valeur SCL est égale à 0 dans votre serveur Exchange local, les messages non indésirables sont remis aux boîtes aux lettres de vos utilisateurs même si la liste des expéditeurs bloqués locale des utilisateurs peut toujours les envoyer dans le dossier Courrier indésirable. Si vous utilisez la mise en quarantaine du courrier indésirable dans EOP, il se peut que les expéditeurs figurant dans la liste fiable de vos utilisateurs soient identifiés comme courrier indésirable et mis en quarantaine. Néanmoins, si vous utilisez le dossier Courrier indésirable dans votre boîte aux lettres locale, les messages des expéditeurs autorisés parviendront jusqu’à la boîte de réception.

> [!WARNING]
> Si vous utilisez une règle de flux de messagerie pour attribuer la valeur SCL 0 (ou une valeur autre que -1), toutes les options de courrier indésirable d’Outlook sont appliquées au message. En d’autres termes, les listes des expéditeurs bloqués et autorisés sont prises en compte. De même, les messages qui ne proviennent pas d’adresses figurant dans les listes d’expéditeurs bloqués ou autorisés peuvent être marqués comme courrier indésirable par le filtre anti-courrier indésirable côté client. Pour qu’Outlook tienne compte des listes d’expéditeurs bloqués et autorisés sans utiliser le filtre anti-courrier indésirable côté client, définissez l’option sur « Aucun filtrage automatique » dans les options de courrier indésirable d’Outlook. Il s’agit de l’option par défaut dans les dernières versions d’Outlook. Vérifiez quand même que ce paramètre est bien défini pour interdire l’application du filtre anti-courrier indésirable côté client. Si vous êtes un administrateur, vous pouvez désactiver le filtre anti-courrier indésirable d’Outlook en suivant les instructions fournies dans l’article [Outlook : Paramètre de stratégie pour désactiver l’interface utilisateur de courrier électronique indésirable et le mécanisme de filtrage](https://support.microsoft.com/kb/2180568).

## <a name="see-also"></a>Voir aussi

[Protection contre le courrier indésirable pour Office 365](anti-spam-protection.md)
