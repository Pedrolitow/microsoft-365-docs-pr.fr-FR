---
title: Configurer la stratégie de filtre de connexion par défaut
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à configurer le filtrage des connexions dans Exchange Online Protection (EOP) pour autoriser ou bloquer les e-mails des serveurs de messagerie.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0c09f445bf3d204f9e22d116dc9fda4c3fea9735
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974122"
---
# <a name="configure-connection-filtering"></a>Configurer le filtrage des connexions

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection autonome (EOP) sans Exchange Online  boîtes aux lettres, vous utilisez le filtrage des connexions dans EOP (en particulier, la stratégie de filtre de connexion par défaut) pour identifier les serveurs de courrier source bons ou incorrects par leurs adresses IP. Les principaux composants de la stratégie de filtrage des connexions par défaut sont les suivants :

- **Liste verte IP** : ignorez le filtrage du courrier indésirable pour tous les messages entrants provenant des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Pour les scénarios où le filtrage du courrier indésirable peut toujours se produire sur les messages de ces sources, consultez les [scénarios où les messages provenant de sources dans la liste d’autorisations IP sont toujours filtrés](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) plus loin dans cet article. Pour plus d’informations sur la façon dont la liste d’autorisations IP doit s’intégrer à votre stratégie globale d’expéditeurs sécurisés, consultez [Créer des listes d’expéditeurs sécurisés dans EOP](create-safe-sender-lists-in-office-365.md).

- **Liste de blocage IP** : bloquez tous les messages entrants des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Les messages entrants sont rejetés, ne sont pas marqués comme courrier indésirable et aucun filtrage supplémentaire n’est effectué. Pour plus d’informations sur la façon dont la liste de blocs IP doit s’intégrer à votre stratégie globale d’expéditeurs bloqués, consultez [Créer des listes d’expéditeurs de blocs dans EOP](create-block-sender-lists-in-office-365.md).

- **Coffre liste** : la *liste sécurisée* est une liste verte dynamique dans le centre de données Microsoft qui ne nécessite aucune configuration du client. Microsoft identifie ces sources de messagerie approuvées à partir d’abonnements à différentes listes tierces. Vous activez ou désactivez l’utilisation de la liste sécurisée ; vous ne pouvez pas configurer les serveurs de messagerie source dans la liste sécurisée. Le filtrage du courrier indésirable est ignoré sur les messages entrants des serveurs de messagerie de la liste sécurisée.

Cet article explique comment configurer la stratégie de filtre de connexion par défaut dans le portail Microsoft 365 Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online ; PowerShell EOP autonome pour les organisations sans boîte aux lettres Exchange Online). Pour plus d’informations sur la façon dont EOP utilise le filtrage des connexions fait partie des paramètres anti-courrier indésirable globaux de votre organisation, consultez [La protection anti-courrier indésirable](anti-spam-protection.md).

> [!NOTE]
> La liste d’adresses IP autorisées, la liste sécurisée et la liste des blocs d’adresses IP font partie de votre stratégie globale pour autoriser ou bloquer les e-mails dans votre organisation. Pour plus d’informations, consultez [Créer des listes d’expéditeurs sécurisés](create-safe-sender-lists-in-office-365.md) et [Créer des listes d’expéditeurs bloqués](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie de filtre de connexion par défaut, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule à la stratégie de filtre de connexion par défaut, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour rechercher les adresses IP sources des serveurs de messagerie (expéditeurs) que vous souhaitez autoriser ou bloquer, vous pouvez vérifier le champ d’en-tête d’adresse IP de connexion (**CIP**) dans l’en-tête de message. Pour afficher un en-tête de message dans différents clients de messagerie, consultez [Afficher les en-têtes de message Internet dans Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- La liste verte IP est prioritaire sur la liste de blocs IP (une adresse des deux listes n’est pas bloquée).

- La liste d’adresses IP autorisées et la liste de blocs IP prennent chacune en charge un maximum de 1 273 entrées, où une entrée est une adresse IP unique, une plage d’adresses IP ou une adresse IP CIDR (Classless InterDomain Routing).

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Utiliser le portail Microsoft 365 Defender pour modifier la stratégie de filtre de connexion par défaut

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez Stratégie de **filtre de connexion (par défaut)** dans la liste en cliquant sur le nom de la stratégie.

3. Dans le menu volant des détails de stratégie qui s’affiche, configurez l’un des paramètres suivants :

   - **Section Description** : Cliquez sur **Modifier le nom et la description**. Dans le menu volant **Modifier le nom et la description** qui s’affiche, entrez le texte descriptif facultatif dans la zone **Description** .

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Filtrage de connexion** : Cliquez sur **Modifier la stratégie de filtre de connexion**. Dans le menu volant qui s’affiche, configurez les paramètres suivants :

     - **Autorisez toujours les messages provenant des adresses IP ou de la plage d’adresses suivantes** : il s’agit de la liste d’adresses IP autorisées. Cliquez dans la zone, entrez une valeur, puis appuyez sur Entrée ou sélectionnez la valeur complète affichée sous la zone. Les valeurs valides sont les suivantes :
       - Adresse IP unique : par exemple, 192.168.1.1.
       - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
       - ADRESSE IP CIDR : par exemple, 192.168.0.1/25. Les valeurs de masque de sous-réseau valides sont comprises entre /24 et /32. Pour ignorer le filtrage du courrier indésirable pour /1 à /23, consultez la section [Ignorer le filtrage du courrier indésirable pour une adresse IP CIDR en dehors de la section plage disponible](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) plus loin dans cet article.

       Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     Pour ajouter l’adresse IP ou la plage d’adresses, cliquez dans la zone et **tapez** itclick Add ![Icon.](../../media/ITPro-EAC-AddIcon.png). Pour supprimer une entrée, sélectionnez l’entrée dans **l’adresse IP autorisée** , puis cliquez sur **Supprimer** ![supprimer](../../media/scc-remove-icon.png). Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Toujours bloquer les messages à partir des adresses IP ou de la plage d’adresses suivantes** : il s’agit de la liste de blocs IP. Entrez une adresse IP unique, une plage d’adresses IP ou une adresse IP CIDR dans la zone, comme décrit précédemment dans les **messages Toujours autoriser à partir des adresses IP ou du paramètre de plage d’adresses ip suivants** .

   - **Activer la liste sécurisée** : activez ou désactivez l’utilisation de la liste sécurisée pour identifier les expéditeurs connus et appropriés qui ignorent le filtrage du courrier indésirable. Pour utiliser la liste sécurisée, activez la case à cocher.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Dans le menu volant des détails de la stratégie, cliquez sur **Fermer**.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Utiliser le portail Microsoft 365 Defender pour afficher la stratégie de filtre de connexion par défaut

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , les propriétés suivantes sont affichées dans la liste des stratégies :

   - **Nom** : cette valeur est la stratégie de **filtre de connexion (par défaut)** pour la stratégie de filtre de connexion par défaut.
   - **État** : cette valeur est **Toujours activée** pour la stratégie de filtre de connexion par défaut.
   - **Priorité** : cette valeur est **la plus basse** pour la stratégie de filtre de connexion par défaut.
   - **Type** : cette valeur est vide pour la stratégie de filtre de connexion par défaut.

3. Lorsque vous sélectionnez la stratégie de filtre de connexion par défaut, les paramètres de stratégie sont affichés dans un menu volant.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Utiliser Exchange Online PowerShell ou PowerShell EOP autonome pour modifier la stratégie de filtre de connexion par défaut

Utilisez la syntaxe suivante :

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Remarques** :

- Les valeurs d’adresse IP ou de plage d’adresses valides sont les suivantes :
  - Adresse IP unique : par exemple, 192.168.1.1.
  - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.
  - ADRESSE IP CIDR : par exemple, 192.168.0.1/25. Les valeurs de masque réseau valides sont comprises entre /24 et /32.
- Pour *remplacer* toutes les entrées existantes par les valeurs que vous spécifiez, utilisez la syntaxe suivante : `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Pour *ajouter ou supprimer* des adresses IP ou des plages d’adresses sans affecter d’autres entrées existantes, utilisez la syntaxe suivante : `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- Pour vider la liste d’adresses IP autorisées ou la liste de blocs IP, utilisez la valeur `$null`.

Cet exemple configure la liste d’adresses IP autorisées et la liste de blocs d’adresses IP avec les adresses IP et plages d’adresses spécifiées.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

Cet exemple montre comment ajouter et supprimer les adresses IP et plages d’adresses spécifiées de la liste d’adresses IP autorisées.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez correctement modifié la stratégie de filtre de connexion par défaut, effectuez l’une des étapes suivantes :

- Dans la page **Anti-courrier indésirable** dans le portail <https://security.microsoft.com/antispam>Microsoft 365 Defender, sélectionnez Stratégie de filtre de connexion **(par défaut)** dans la liste en cliquant sur le nom de la stratégie, puis vérifiez les paramètres.

- Dans Exchange Online PowerShell ou PowerShell EOP autonome, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Envoyez un message de test à partir d’une entrée de la liste d’autorisations IP.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Considérations supplémentaires relatives à la liste d’autorisations IP

Les sections suivantes identifient les éléments supplémentaires que vous devez connaître lors de la configuration de la liste d’autorisations IP.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Ignorer le filtrage du courrier indésirable pour une adresse IP CIDR en dehors de la plage disponible

Comme décrit précédemment dans cet article, vous pouvez uniquement utiliser une adresse IP CIDR avec le masque réseau /24 à /32 dans la liste d’autorisations IP. Pour ignorer le filtrage du courrier indésirable sur les messages des serveurs de messagerie source de la plage /1 à /23, vous devez utiliser Exchange règles de flux de courrier (également appelées règles de transport). Toutefois, nous vous recommandons de ne pas le faire si possible, car les messages seront bloqués si une adresse IP de la plage d’adresses IP CIDR /1 à /23 apparaît sur l’une des listes de blocs propriétaires ou tierces de Microsoft.

Maintenant que vous êtes pleinement conscient des problèmes potentiels, vous pouvez créer une règle de flux de courrier avec les paramètres suivants (au minimum) pour vous assurer que les messages de ces adresses IP ignorent le filtrage du courrier indésirable :

- Condition de règle : **appliquez cette règle si** \> l’adresse IP de **l’expéditeur** \> **se trouve dans l’une de ces plages ou correspond** \> exactement (entrez votre adresse IP CIDR avec un masque réseau /1 à /23).
- Action de règle : **modifier les propriétés** \> du message **Définir le niveau de confiance du courrier indésirable (SCL)** \> **Ignorer le filtrage du courrier indésirable**.

Vous pouvez auditer la règle, tester la règle, activer la règle pendant une période spécifique et d’autres sélections. Nous vous recommandons de tester la règle pendant un certain temps avant de l'appliquer. Pour plus d’informations, consultez [Gérer les règles de flux de messagerie dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Ignorer le filtrage du courrier indésirable sur les domaines de courrier sélectifs à partir de la même source

En règle générale, l’ajout d’une adresse IP ou d’une plage d’adresses à la liste d’autorisations IP signifie que vous approuvez tous les messages entrants de cette source de messagerie. Mais que se passe-t-il si cette source envoie des e-mails à partir de plusieurs domaines et que vous souhaitez ignorer le filtrage du courrier indésirable pour certains de ces domaines, mais pas pour d’autres ? Vous ne pouvez pas utiliser la liste d’autorisation IP seule pour ce faire, mais vous pouvez utiliser la liste d’autorisation IP en combinaison avec une règle de flux de messagerie.

Par exemple, le serveur de messagerie source 192.168.1.25 envoie des e-mails à partir des domaines contoso.com, fabrikam.com et tailspintoys.com, mais vous ne souhaitez ignorer le filtrage du courrier indésirable pour les messages des expéditeurs dans fabrikam.com. Pour ce faire, procédez comme suit :

1. Ajoutez 192.168.1.25 à la liste d’autorisations IP.

2. Configurez une règle de flux de messagerie avec les paramètres suivants (au minimum) :
   - Condition de règle : **appliquez cette règle si** \> l’adresse IP de **l’expéditeur** \> **se trouve dans l’une de ces plages ou correspond exactement** à 192.168.1.25 (même adresse IP ou plage d’adresses \> que celle que vous avez ajoutée à la liste d’autorisations IP à l’étape précédente).
   - Action de règle : **modifier les propriétés** \> du message **Définir le niveau de confiance du courrier indésirable (SCL)** \> **0**.
   - Exception de règle : **le domaine de l’expéditeur** \> **est** \> fabrikam.com (seul le ou les domaines que vous souhaitez ignorer le filtrage du courrier indésirable).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scénarios où les messages provenant de sources dans la liste d’autorisations IP sont toujours filtrés

Les messages d’un serveur de messagerie dans votre liste d’autorisations IP sont toujours soumis au filtrage du courrier indésirable dans les scénarios suivants :

- Une adresse IP dans votre liste d’autorisations IP est également configurée dans un connecteur entrant local basé sur IP dans *n’importe quel* locataire de Microsoft 365 (appelons ce locataire A), **et** le locataire A et le serveur EOP qui rencontrent d’abord le message se trouve dans *la même* forêt Active Directory dans les centres de données Microsoft. Dans ce scénario, **IPV:CAL** *est* ajouté aux [en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md) du message (indiquant que le message a contourné le filtrage du courrier indésirable), mais le message est toujours soumis au filtrage du courrier indésirable.

- Votre locataire qui contient la liste d’autorisations IP et le serveur EOP qui rencontre le message se trouve dans *différentes* forêts Active Directory dans les centres de données Microsoft. Dans ce scénario, **IPV:CAL** *n’étant pas* ajouté aux en-têtes de message, le message est toujours soumis au filtrage du courrier indésirable.

Si vous rencontrez l’un de ces scénarios, vous pouvez créer une règle de flux de courrier avec les paramètres suivants (au minimum) pour vous assurer que les messages des adresses IP problématiques ignorent le filtrage du courrier indésirable :

- Condition de règle : **appliquez cette règle si** \> l’adresse IP de **l’expéditeur** \> **se trouve dans l’une de ces plages ou correspond** \> exactement (votre adresse IP ou adresses).
- Action de règle : **modifier les propriétés** \> du message **Définir le niveau de confiance du courrier indésirable (SCL)** \> **Ignorer le filtrage du courrier indésirable**.

## <a name="new-to-microsoft-365"></a>Vous débutez avec Microsoft 365 ?

****

![Petit icône de LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Vous débutez avec Microsoft 365 ?** Découvrez des cours vidéo gratuits pour **les administrateurs Microsoft 365 et les professionnels de l’informatique, proposés** par LinkedIn Learning.
