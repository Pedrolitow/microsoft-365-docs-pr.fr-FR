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
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à configurer le filtrage des connexions dans Exchange Online Protection (EOP) pour autoriser ou bloquer les messages électroniques provenant de serveurs de messagerie.
ms.openlocfilehash: d69ec30c9d6d812bf3bbcc6dc5b6df332d9dd0b5
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203370"
---
# <a name="configure-connection-filtering"></a>Configuration du filtrage des connexions

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîtes aux lettres Exchange Online, vous utilisez le filtrage des connexions dans EOP (en particulier la stratégie de filtrage des connexions par défaut) pour identifier les serveurs de messagerie source valides par leurs adresses IP. Les principaux composants de la stratégie de filtrage des connexions par défaut sont les suivants :

- **Liste d’adresses IP autorisées**: ignorez le filtrage du courrier indésirable pour tous les messages entrants provenant des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Pour les scénarios dans lesquels le filtrage du courrier indésirable peut toujours se produire sur les messages provenant de ces sources, consultez la section [scénarios dans lesquels les messages provenant de sources dans la liste d’adresses IP autorisées sont toujours filtrés](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) plus loin dans cette rubrique. Pour plus d’informations sur la façon dont la liste d’adresses IP autorisées doit tenir dans votre stratégie d’expéditeurs approuvés globale, consultez la rubrique [créer des listes d’expéditeurs approuvés dans EOP](create-safe-sender-lists-in-office-365.md).

- **Liste d’adresses IP bloquées**: bloquer tous les messages entrants provenant des serveurs de messagerie source que vous spécifiez par adresse IP ou plage d’adresses IP. Les messages entrants sont rejetés, ne sont pas marqués comme courrier indésirable et aucun filtrage supplémentaire n’est effectué. Pour plus d’informations sur la façon dont la liste d’adresses IP bloquées doit tenir dans votre stratégie d’expéditeurs bloqués global, voir [Create Block sender Lists in EOP](create-block-sender-lists-in-office-365.md).

- **Liste verte**: la *liste* verte est une liste verte dynamique dans le centre de contenu Microsoft qui ne requiert aucune configuration client. Microsoft identifie ces sources de messagerie approuvées à partir des abonnements à différentes listes tierces. Vous activez ou désactivez l’utilisation de la liste verte ; vous ne pouvez pas configurer les serveurs de messagerie source sur la liste sécurisée. Le filtrage du courrier indésirable est ignoré sur les messages entrants provenant des serveurs de messagerie de la liste verte.

Cette rubrique décrit comment configurer la stratégie de filtrage des connexions par défaut dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange autonome EOP pour les organisations sans boîtes aux lettres Exchange Online). Pour plus d’informations sur la façon dont EOP utilise le filtrage des connexions fait partie des paramètres anti-courrier indésirable globaux de votre organisation, consultez la rubrique [protection contre le courrier indésirable](anti-spam-protection.md).

> [!NOTE]
> La liste d’adresses IP autorisées, la liste verte et la liste d’adresses IP bloquées font partie de votre stratégie globale pour autoriser ou bloquer les messages électroniques au sein de votre organisation. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés](create-safe-sender-lists-in-office-365.md) et [créer des listes d’expéditeurs bloqués](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. décrites dans cette rubrique :

  - Pour modifier la stratégie de filtrage des connexions par défaut, vous devez être membre de l’un des groupes de rôles suivants :

    - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation** ou **Gestion de l’hygiène** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

  - Pour un accès en lecture seule à la stratégie de filtrage des connexions par défaut, vous devez être membre de l’un des groupes de rôles suivants :

    - **Lecteur de sécurité** dans le [Centre de conformité et sécurité](permissions-in-the-security-and-compliance-center.md).
    - **Gestion de l’organisation en affichage seul** dans[Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups).

- Pour rechercher les adresses IP sources des serveurs de messagerie (expéditeurs) que vous souhaitez autoriser ou bloquer, vous pouvez vérifier le champ d’en-**tête de connexion**IP dans l’en-tête du message. Pour afficher un en-tête de message dans différents clients de messagerie, consultez la rubrique [afficher les en-têtes de message Internet dans Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- La liste d’adresses IP autorisées est prioritaire sur la liste d’adresses IP bloquées (une adresse sur les deux listes n’est pas bloquée).

- La liste d’adresses IP autorisées et la liste d’adresses IP bloquées prennent en charge un maximum de 1273 entrées, où une entrée est une adresse IP unique, une plage d’adresses IP ou une adresse IP de routage CIDR (Classless Interdomain Routing).

## <a name="use-the-security--compliance-center-to-modify-the-default-connection-filter-policy"></a>Utiliser le centre de sécurité & conformité pour modifier la stratégie de filtrage des connexions par défaut

1. Dans le centre de sécurité & conformité et accédez **Threat management** à \> **Policy** \> **protection contre le courrier indésirable**de la stratégie de gestion des menaces.

2. Sur la page **paramètres de blocage du courrier indésirable** , développez **stratégie de filtrage des connexions** en cliquant sur ![ développer, puis ](../../media/scc-expand-icon.png) sur modifier la **stratégie**.

3. Dans le menu volant **par défaut** qui s’affiche, configurez l’un des paramètres suivants :

   - **Description**: saisissez un texte descriptif facultatif.

   - **Liste d’adresses IP autorisées**: cliquez sur **modifier**. Dans la fenêtre mobile liste d’adresses **IP autorisées** qui s’affiche, entrez une adresse IPv4 dans la zone **adresse ou plage d’adresses** à l’aide de la syntaxe suivante :

     - Adresse IP unique : par exemple, 192.168.1.1.

     - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.

     - Adresse IP CIDR : par exemple, 192.168.0.1/25. Les valeurs valides du masque réseau sont de/24 à 32. Pour ignorer le filtrage du courrier indésirable pour les valeurs de masque IP CIDR/1 à/23, consultez la section [ignorer le filtrage du courrier indésirable pour une adresse IP CIDR en dehors de la plage disponible](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) plus loin dans cette rubrique.

     Pour ajouter l’adresse IP ou la plage d’adresses, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Pour supprimer une entrée, sélectionnez-la dans **adresse IP autorisée** , puis cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) . Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Liste d’adresses IP bloquées**: cliquez sur **modifier**. Dans le menu **déroulant de liste d’adresses IP bloquées** qui s’affiche, entrez une adresse IP, une plage d’adresses IP ou une adresse IP CIDR dans la zone **adresse ou plage d’adresses** comme décrit précédemment dans le paramètre de liste d’adresses **IP autorisées** .

     Pour ajouter l’adresse IP ou la plage d’adresses, cliquez sur **Ajouter** une ![ icône Ajouter ](../../media/ITPro-EAC-AddIcon.png) . Pour supprimer une entrée, sélectionnez-la dans **adresse IP bloquée** , puis cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) . Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Activer la liste verte**: activez ou désactivez l’utilisation de la liste approuvée pour identifier les expéditeurs connus et de bonne qualité qui ignoreront le filtrage du courrier indésirable.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-view-the-default-connection-filter-policy"></a>Utiliser le centre de sécurité & conformité pour afficher la stratégie de filtrage des connexions par défaut

1. Dans le centre de sécurité & conformité et accédez **Threat management** à \> **Policy** \> **protection contre le courrier indésirable**de la stratégie de gestion des menaces.

2. Dans la page **paramètres du blocage du courrier indésirable** , cliquez sur le menu déroulant en regard de la stratégie par défaut nommée **stratégie de filtrage des connexions**.

3. Les paramètres de stratégie s’affichent dans la liste déroulante qui s’ouvre.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Utiliser Exchange Online PowerShell ou l’environnement de ligne de commande Exchange EOP PowerShell autonome pour modifier la stratégie de filtrage des connexions par défaut

Utilisez la syntaxe suivante :

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Remarques** :

- Les valeurs d’adresse IP ou de plage d’adresses valides sont les suivantes :

  - Adresse IP unique : par exemple, 192.168.1.1.

  - Plage d’adresses IP : par exemple, 192.168.0.1-192.168.0.254.

  - Adresse IP CIDR : par exemple, 192.168.0.1/25. Les valeurs valides du masque réseau sont de/24 à 32.

- Pour *remplacer* les entrées existantes par les valeurs que vous spécifiez, utilisez la syntaxe suivante : `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN` .

- Pour *Ajouter ou supprimer* des adresses IP ou des plages d’adresses sans affecter les autres entrées existantes, utilisez la syntaxe suivante : `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}` .

- Pour vider la liste d’adresses IP autorisées ou d’adresses IP bloquées, utilisez la valeur `$null` .

Cet exemple montre comment configurer la liste d’adresses IP autorisées et la liste d’adresses IP bloquées avec les plages d’adresses et adresses IP spécifiées.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

Cet exemple ajoute et supprime les plages d’adresses et adresses IP spécifiées dans la liste d’adresses IP autorisées.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-HostedConnectionFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien modifié la stratégie de filtrage des connexions par défaut, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez **Threat management** à \> **Policy** \> **protection contre le courrier indésirable** de la stratégie de gestion des menaces \> cliquez sur le menu déroulant en regard de **stratégie de filtrage des connexions (Always on**) et vérifiez les paramètres.

- Dans Exchange Online PowerShell ou dans le PowerShell autonome EOP, exécutez la commande suivante et vérifiez les paramètres :

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Envoyer un message de test à partir d’une entrée dans la liste d’adresses IP autorisées.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Considérations supplémentaires pour la liste d’adresses IP autorisées

Les sections suivantes identifient les éléments supplémentaires que vous devez connaître lors de la configuration de la liste d’adresses IP autorisées.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Ignorer le filtrage du courrier indésirable pour une adresse IP CIDR en dehors de la plage disponible

Comme décrit précédemment dans cette rubrique, vous ne pouvez utiliser qu’une adresse IP CIDR avec le masque réseau/24/32 dans la liste d’adresses IP autorisées. Pour ignorer le filtrage du courrier indésirable sur les messages provenant de serveurs de messagerie source dans la plage/1/23, vous devez utiliser des règles de flux de messagerie Exchange (également appelées règles de transport). Toutefois, nous vous recommandons de ne pas faire cela si cela est possible, car les messages seront bloqués si une adresse IP figurant dans la plage IP/1 à/23 CIDR apparaît sur l’une des listes de blocage propriétaires ou tierces de Microsoft.

Maintenant que vous avez pris connaissance des problèmes potentiels, vous pouvez créer une règle de flux de messagerie avec les paramètres suivants (au minimum) pour vous assurer que les messages provenant de ces adresses IP ignorent le filtrage du courrier indésirable :

- Condition de règle : **appliquez cette règle si** \> **l'** \> **adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement** \> (entrez votre adresse IP CIDR avec le masque réseau a/1 vers/23).

- Action **de la règle : modifier les propriétés du message** \> **définir le seuil de probabilité de courrier indésirable (SCL) ignorer le filtrage du** courrier \> **indésirable**.

Vous pouvez auditer la règle, tester la règle, activer la règle pendant une période spécifique, ainsi que d’autres sélections. Nous vous recommandons de tester la règle pendant un certain temps avant de l'appliquer. Pour plus d’informations, consultez la rubrique [gestion des règles de flux de messagerie dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Ignorer le filtrage du courrier indésirable sur les domaines de messagerie sélectifs de la même source

En règle générale, l’ajout d’une adresse IP ou d’une plage d’adresses à la liste d’adresses IP autorisées signifie que vous approuvez tous les messages entrants provenant de cette source de messagerie. Que se passe-t-il si cette source envoie du courrier électronique à partir de plusieurs domaines et que vous souhaitez ignorer le filtrage du courrier indésirable pour certains de ces domaines, mais pas pour d’autres ? Vous ne pouvez pas utiliser la liste d’adresses IP autorisées seule pour ce faire, mais vous pouvez utiliser la liste d’adresses IP autorisées en combinaison avec une règle de flux de messagerie.

Par exemple, le serveur de messagerie source 192.168.1.25 envoie un courrier électronique à partir des domaines contoso.com, fabrikam.com et tailspintoys.com, mais vous souhaitez uniquement ignorer le filtrage du courrier indésirable pour les messages provenant d’expéditeurs dans fabrikam.com. Pour ce faire, procédez comme suit :

1. Ajoutez 192.168.1.25 à la liste d’adresses IP autorisées.

2. Configurez une règle de flux de messagerie avec les paramètres suivants (au minimum) :

   - Condition de la règle : **appliquez cette règle si** \> **l'** \> **adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement** à \> 192.168.1.25 (la même adresse IP ou plage d’adresses que vous avez ajoutée à la liste d’adresses IP autorisées à l’étape précédente).

   - Action **de la règle : modifier les propriétés du message** \> **Définissez le seuil de probabilité de courrier indésirable (SCL)** \> **0**.

   - Exception de règle : le domaine de **l’expéditeur** \> **est** \> fabrikam.com (uniquement le domaine ou les domaines pour lesquels vous souhaitez ignorer le filtrage du courrier indésirable).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scénarios dans lesquels les messages provenant de sources dans la liste d’adresses IP autorisées sont toujours filtrés

Les messages provenant d’un serveur de messagerie de votre liste d’adresses IP autorisées sont toujours soumis au filtrage du courrier indésirable dans les scénarios suivants :

- Une adresse IP de votre liste d’adresses IP autorisées est également configurée dans un connecteur entrant basé sur IP sur site de *n’importe quel* client de Microsoft 365 (appelons ce locataire a), **et** le locataire a et le serveur EOP qui rencontre pour la première fois le message se trouvent dans *la même* forêt Active Directory dans les centres de contenu Microsoft. Dans ce scénario, **IPV : la licence d’accès client** *est* ajoutée aux [en-têtes de message anti-courrier indésirable](anti-spam-message-headers.md) du message (indiquant le filtrage de courrier indésirable ignoré), mais le message est toujours soumis au filtrage du courrier indésirable.

- Votre client qui contient la liste d’adresses IP autorisées et le serveur EOP qui rencontre tout d’abord le message se trouvent dans des forêts Active Directory *différentes* dans les centres de contenu Microsoft. Dans ce scénario, **IPV : la licence d’accès client** *n’est pas* ajoutée aux en-têtes de message, de sorte que le message est toujours soumis au filtrage du courrier indésirable.

Si vous rencontrez l’un de ces scénarios, vous pouvez créer une règle de flux de messagerie avec les paramètres suivants (au minimum) pour vous assurer que les messages provenant des adresses IP problématiques ignorent le filtrage du courrier indésirable :

- Condition de la règle : **appliquez cette règle si** \> **l'** \> **adresse IP de l’expéditeur se trouve dans l’une de ces plages ou correspond exactement à** \> (votre ou vos adresses IP).

- Action **de la règle : modifier les propriétés du message** \> **définir le seuil de probabilité de courrier indésirable (SCL) ignorer le filtrage du** courrier \> **indésirable**.

## <a name="new-to-microsoft-365"></a>Nouveauté de Microsoft 365 ?

|<!-- a -->|
|---|
|![Icône rapide pour LinkedIn Learning ](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **New de Microsoft 365 ?** Découvrez les cours vidéo gratuits pour les **administrateurs et les professionnels**de l’informatique, proposés par LinkedIn Learning.|
|
