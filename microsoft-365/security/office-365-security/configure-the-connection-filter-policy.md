---
title: Configurer la stratégie de filtrage des connexions par défaut
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à configurer le filtrage des connexions dans Exchange Online Protection (EOP) pour autoriser ou bloquer les e-mails provenant de serveurs de messagerie.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bdc8033996c41238bb1defe831eb8e8c7650bb44
ms.sourcegitcommit: 070724118be25cd83418d2a56863da95582dae65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "50406089"
---
# <a name="configure-connection-filtering"></a>Configurer le filtrage des connexions

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)


Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection autonome (EOP) sans boîtes aux lettres Exchange Online, vous utilisez le filtrage des connexions dans EOP (en particulier, la stratégie de filtrage des connexions par défaut) pour identifier les serveurs de messagerie source bons ou mauvais par leurs adresses IP. Les principaux composants de la stratégie de filtrage des connexions par défaut sont les suivants :

- **Liste d’adresses IP** permises : ignorez le filtrage du courrier indésirable pour tous les messages entrants provenant des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Pour les scénarios où le filtrage du courrier indésirable peut encore se produire sur les messages provenant de ces sources, consultez la section [Scénarios](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) dans lequel les messages provenant de sources de la liste d’adresses IP sont toujours filtrés plus loin dans cet article. Pour plus d’informations sur la façon dont la liste d’adresses IP permises doit s’intégrer dans votre stratégie globale d’expéditeurs sûrs, voir Créer des listes d’expéditeurs sûrs [dans EOP.](create-safe-sender-lists-in-office-365.md)

- **Liste d’adresses IP** bloqués : bloquez tous les messages entrants provenant des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Les messages entrants sont rejetés, ne sont pas marqués comme courrier indésirable et aucun filtrage supplémentaire ne se produit. Pour plus d’informations sur la façon dont la liste d’adresses IP bloquées doit tenir dans votre stratégie globale des expéditeurs bloqués, voir Créer des listes d’expéditeurs bloqués [dans EOP.](create-block-sender-lists-in-office-365.md)

- **Liste sécurisée**: la *liste sécurisée* est une liste d’informations dynamiques dans le centre de données Microsoft qui ne nécessite aucune configuration client. Microsoft identifie ces sources de courriers électroniques de confiance à partir d’abonnements à différentes listes tierces. Vous activez ou désactivez l’utilisation de la liste sécurisée ; vous ne pouvez pas configurer les serveurs de messagerie source dans la liste fiable. Le filtrage du courrier indésirable est ignoré sur les messages entrants provenant des serveurs de messagerie de la liste sécurisée.

Cette rubrique décrit comment configurer la stratégie de filtrage des connexions par défaut dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online). Pour plus d’informations sur la façon dont EOP utilise le filtrage des connexions fait partie des paramètres anti-courrier indésirable globaux de votre organisation, consultez la [protection anti-courrier indésirable.](anti-spam-protection.md)

> [!NOTE]
> La liste d’adresses IP permises, la liste d’adresses IP sécurisées et la liste d’adresses IP bloqués font partie de votre stratégie globale pour autoriser ou bloquer le courrier électronique dans votre organisation. Pour plus d’informations, voir [Créer des listes d’expéditeurs](create-safe-sender-lists-in-office-365.md) sûrs et [Créer des listes d’expéditeurs bloqués.](create-block-sender-lists-in-office-365.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées dans **Exchange Online** avant de pouvoir suivre les procédures de cet article :
  - Pour modifier la stratégie de filtrage des connexions  par défaut, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur de** la sécurité.
  - Pour accéder en lecture seule à la stratégie de filtrage  des connexions par défaut, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité. 

  Pour plus d'informations, voir [Permissions en échange en ligne](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo).

  **Remarques**:

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux _utilisateurs_ les autorisations et autorisations requises pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour rechercher les adresses IP sources des serveurs de messagerie (expéditeurs) que vous souhaitez autoriser ou bloquer, vous pouvez vérifier le champ d’en-tête IP de connexion **(CIP)** dans l’en-tête du message. Pour afficher un en-tête de message dans différents clients de messagerie, voir Afficher les en-têtes [de message Internet dans Outlook.](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c)

- La liste d’adresses IP bloquées est prioritaire sur la liste d’adresses IP bloquées (une adresse sur les deux listes n’est pas bloquée).

- La liste d’adresses IP permises et la liste d’adresses IP bloqués peuvent chacune prendre en charge un maximum de 1 273 entrées, où une entrée est une adresse IP unique, une plage d’adresses IP ou une adresse IP de routage CIDR (Classless InterDomain Routing).

## <a name="use-the-security--compliance-center-to-modify-the-default-connection-filter-policy"></a>Utiliser le Centre de sécurité & conformité pour modifier la stratégie de filtrage des connexions par défaut

1. Dans le Centre de sécurité & conformité et allez à la stratégie de **gestion** des \> **menaces** \> **anti-courrier indésirable.**

2. Dans la page **Paramètres anti-courrier** indésirable, développez la stratégie de filtrage des connexions en cliquant sur Icône Développer, puis cliquez sur Modifier la  ![ ](../../media/scc-expand-icon.png) **stratégie.**

3. Dans le **volant par** défaut qui s’affiche, configurez l’un des paramètres suivants :

   - **Description**: entrez un texte descriptif facultatif.

   - **Liste d’adresses IP autoriser**: cliquez sur **Modifier.** Dans le volant **liste verte IP** qui s’affiche,  entrez une adresse IPV4 dans la zone Adresse ou plage d’adresses à l’aide de la syntaxe suivante :

     - Adresse IP unique : par exemple, 192.168.1.1.

     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.

     - ADRESSE IP CIDR : par exemple, 192.168.0.1/25. Les valeurs de masque réseau valides sont de /24 à /32. Pour ignorer le filtrage du courrier indésirable pour les valeurs de masque IP CIDR entre /1 et /23, consultez la section Ignorer le filtrage du courrier indésirable pour une [adresse IP CIDR](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) en dehors de la section de plage disponible plus loin dans cet article.

     Pour ajouter l’adresse IP ou la plage d’adresses, cliquez **sur Ajouter** ![ une ](../../media/ITPro-EAC-AddIcon.png) icône. Pour supprimer une entrée, sélectionnez-la dans **l’adresse IP autorisée,** puis cliquez sur  ![ ](../../media/scc-remove-icon.png) Supprimer. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Liste d’adresses IP bloqués**: cliquez sur **Modifier.** Dans le volant liste d’adresses **IP** bloqués qui s’affiche,  entrez une adresse IP, une plage IP ou une adresse IP CIDR unique dans la zone Adresse ou plage d’adresses, comme décrit précédemment dans le paramètre Liste verte **IP.**

     Pour ajouter l’adresse IP ou la plage d’adresses, cliquez **sur Ajouter** ![ une ](../../media/ITPro-EAC-AddIcon.png) icône. Pour supprimer une entrée, sélectionnez-la dans **Adresse IP** bloquée, puis cliquez sur  ![ ](../../media/scc-remove-icon.png) Supprimer. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Activer la liste sécurisée**: activez ou désactivez l’utilisation de la liste sécurisée pour identifier les expéditeurs connus et de qualité qui ignoreront le filtrage du courrier indésirable.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-view-the-default-connection-filter-policy"></a>Utiliser le Centre de sécurité & conformité pour afficher la stratégie de filtrage des connexions par défaut

1. Dans le Centre de sécurité & conformité et allez à la stratégie de **gestion** des \> **menaces** \> **anti-courrier indésirable.**

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur la liste suivante en haut de la stratégie par défaut nommée Stratégie de **filtrage des connexions.**

3. Les paramètres de stratégie sont affichés dans la baisse qui s’ouvre.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour modifier la stratégie de filtrage des connexions par défaut

Utilisez la syntaxe suivante :

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Remarques**:

- Les valeurs d’adresse IP ou de plage d’adresses valides sont :

  - Adresse IP unique : par exemple, 192.168.1.1.

  - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.

  - ADRESSE IP CIDR : par exemple, 192.168.0.1/25. Les valeurs de masque réseau valides sont de /24 à /32.

- Pour *réécrire les* entrées existantes avec les valeurs que vous spécifiez, utilisez la syntaxe suivante `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN` :

- Pour *ajouter ou supprimer des* adresses IP ou des plages d’adresses sans affecter les autres entrées existantes, utilisez la syntaxe suivante : `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`

- Pour vider la liste d’adresses IP permises ou la liste d’adresses IP bloqués, utilisez la valeur `$null` .

Cet exemple configure la liste d’adresses IP permises et la liste d’adresses IP bloqués avec les adresses IP et plages d’adresses spécifiées.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

Cet exemple ajoute et supprime les adresses IP et plages d’adresses spécifiées de la liste d’adresses IP permises.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedConnectionFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien modifié la stratégie de filtrage des connexions par défaut, faites l’une des étapes suivantes :

- Dans le Centre de sécurité &  conformité, consultez la stratégie de gestion des \>  \> menaces **Anti-Courrier** indésirable en cliquant sur la liste suivante en haut de la stratégie de filtrage des connexions (toujours en cours), puis vérifiez les \> paramètres. 

- Dans Exchange Online PowerShell ou EOP PowerShell autonome, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Envoyez un message de test à partir d’une entrée de la liste d’adresses IP permises.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Considérations supplémentaires pour la liste d’adresses IP permises

Les sections suivantes identifient les éléments supplémentaires que vous devez connaître lorsque vous configurez la liste d’adresses IP permises.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Ignorer le filtrage du courrier indésirable pour une adresse IP CIDR en dehors de la plage disponible

Comme décrit précédemment dans cet article, vous pouvez uniquement utiliser une adresse IP CIDR avec le masque réseau /24 à /32 dans la liste d’adresses IP permises. Pour ignorer le filtrage du courrier indésirable sur les messages provenant de serveurs de messagerie sources de la plage /1 à /23, vous devez utiliser des règles de flux de messagerie Exchange (également appelées règles de transport). Toutefois, nous vous recommandons de ne pas le faire dans la mesure du possible, car les messages seront bloqués si une adresse IP de la plage d’adresses IP CIDR /1 à /23 apparaît sur l’une des listes d’adresses IP bloquées propriétaires ou tierces de Microsoft.

Maintenant que vous êtes pleinement conscient des problèmes potentiels, vous pouvez créer une règle de flux de messagerie avec les paramètres suivants (au minimum) pour vous assurer que les messages provenant de ces adresses IP ignoreront le filtrage du courrier indésirable :

- Condition de  règle : appliquez cette règle si l’adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement (entrez votre adresse IP CIDR avec un masque réseau \>  \>  \> /1 à /23).

- Action de la règle **: modifier les propriétés du message** Définir le niveau de confiance du courrier indésirable \> **(SCL) Contourner** le filtrage du courrier \> **indésirable.**

Vous pouvez auditer la règle, la tester, l’activer pendant une période spécifique et d’autres sélections. Nous vous recommandons de tester la règle pendant un certain temps avant de l'appliquer. Pour plus d’informations, voir [Gérer les règles de flux de messagerie dans Exchange Online.](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules)

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Ignorer le filtrage du courrier indésirable sur les domaines de courrier sélectifs de la même source

En règle générale, l’ajout d’une adresse IP ou d’une plage d’adresses à la liste d’adresses IP permises signifie que vous faites confiance à tous les messages entrants provenant de cette source de courrier. Mais que se passe-t-il si cette source envoie du courrier électronique à partir de plusieurs domaines et que vous souhaitez ignorer le filtrage du courrier indésirable pour certains de ces domaines, mais pas pour d’autres ? Vous ne pouvez pas utiliser la liste d’adresses IP permises pour cela, mais vous pouvez utiliser la liste d’adresses IP autoriser en combinaison avec une règle de flux de messagerie.

Par exemple, le serveur de messagerie source 192.168.1.25 envoie du courrier électronique à partir des domaines contoso.com, fabrikam.com et tailspintoys.com, mais vous souhaitez uniquement ignorer le filtrage du courrier indésirable pour les messages provenant d’expéditeurs dans fabrikam.com. Pour ce faire, utilisez les étapes suivantes :

1. Ajoutez 192.168.1.25 à la liste d’adresses IP permises.

2. Configurez une règle de flux de messagerie avec les paramètres suivants (au minimum) :

   - Condition de  règle : appliquez cette règle si l’adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement à \>  \> 192.168.1.25 (la même adresse IP ou plage d’adresses que celle que vous avez ajoutée à la liste d’adresses IP  autoriser à l’étape \> précédente).

   - Action de la règle **: modifier les propriétés du message** Définissez le niveau de confiance du courrier indésirable \> **(SCL)** \> **0**.

   - Exception de règle **: le domaine de** l’expéditeur est fabrikam.com \>  \> (seuls les domaines que vous souhaitez ignorer le filtrage du courrier indésirable).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scénarios dans lequel les messages provenant de sources dans la liste d’adresses IP permises sont toujours filtrés

Les messages provenant d’un serveur de messagerie dans votre liste d’adresses IP sont toujours soumis au filtrage du courrier indésirable dans les scénarios suivants :

- Une adresse IP dans votre liste d’adresses IP permises est également  configurée dans un connecteur entrant local basé sur IP dans n’importe quel client dans Microsoft 365 (appelons ce client **A),** et le client A et le serveur EOP qui rencontre le message pour la première fois se trouve dans la même forêt *Active* Directory dans les centres de données Microsoft. Dans ce scénario, **IPV:CAL**  est ajouté aux [en-têtes de message anti-courrier](anti-spam-message-headers.md) indésirable du message (indiquant que le message a contourné le filtrage du courrier indésirable), mais le message est toujours soumis au filtrage du courrier indésirable.

- Votre client qui contient la liste d’adresses IP permises et le serveur EOP qui rencontre le message pour la première fois se trouve dans différentes forêts *Active* Directory dans les centres de données Microsoft. Dans ce scénario, **IPV:CAL**  n’est pas ajouté aux en-têtes de message, de sorte que le message est toujours soumis au filtrage du courrier indésirable.

Si vous rencontrez l’un de ces scénarios, vous pouvez créer une règle de flux de messagerie avec les paramètres suivants (au minimum) pour vous assurer que les messages provenant des adresses IP problématiques ignorent le filtrage du courrier indésirable :

- Condition de règle : **appliquez cette règle** si l’adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement (votre ou vos \>  \>  \> adresses IP).

- Action de la règle **: modifier les propriétés du message** Définir le niveau de confiance du courrier indésirable \> **(SCL) Contourner** le filtrage du courrier \> **indésirable.**

## <a name="new-to-microsoft-365"></a>Vous n’en 2010 que Microsoft 365 ?

****

![L’icône courte pour LinkedIn Learning ](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **New to Microsoft 365 ?** Découvrez les cours vidéo gratuits pour les **administrateurs Microsoft 365** et les professionnels de l’informatique, présentés par LinkedIn Learning.
