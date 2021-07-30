---
title: Configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer les paramètres de courrier indésirable dans Exchange Online boîtes aux lettres. Bon nombre de ces paramètres sont disponibles pour les utilisateurs Outlook ou Outlook sur le web.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7c9a787c02273eeaf9e3db5174607f1b65a3c65a
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53652478"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online, les paramètres de courrier indésirable de l’organisation sont contrôlés par Exchange Online Protection (EOP). Pour plus d’informations, voir [Protection contre le courrier indésirable dans EOP.](anti-spam-protection.md)

Toutefois, il existe également des paramètres anti-courrier indésirable spécifiques que les administrateurs peuvent configurer sur des boîtes aux lettres individuelles dans Exchange Online :

- **Activez ou désactivez** la règle de courrier indésirable : la règle de courrier indésirable est une règle de boîte de réception masquée nommée Règle de courrier indésirable qui est activée par défaut dans chaque boîte aux lettres. La règle de courrier indésirable contrôle les fonctionnalités suivantes :

  - Déplacez les messages vers le dossier Courrier indésirable en fonction des stratégies **anti-courrier** indésirable : lorsqu’une stratégie anti-courrier indésirable est configurée avec l’action Déplacer **le message** vers le dossier Courrier indésirable pour un verdict de filtrage du courrier indésirable, la règle de filtrage du courrier indésirable déplace le message vers le dossier Courrier indésirable une fois le message remis à la boîte aux lettres. Pour plus d’informations sur les verdicts de filtrage du courrier indésirable dans les stratégies anti-courrier indésirable, voir [Configure anti-spam policies in EOP](configure-your-spam-filter-policies.md). De même, si la purge automatique d’heure zéro (ZAP) détermine qu’un message remis est un courrier indésirable ou un hameçonnage, la règle de filtrage du courrier indésirable déplace le message vers le dossier Courrier indésirable pour déplacer le **message** vers les actions de filtrage du courrier indésirable du dossier Courrier indésirable. Pour plus d’informations sur ZAP, voir la purge automatique d’heure zéro [(ZAP) dans Exchange Online](zero-hour-auto-purge.md).

  - Paramètres de courrier indésirable que les utilisateurs configurent eux-mêmes dans Outlook ou Outlook sur le web : la _collection_ de **listes** sécurisées est la liste des expéditeurs Coffre, la liste des destinataires Coffre et la liste des expéditeurs bloqués sur chaque boîte aux lettres. Les entrées de ces listes déterminent si la règle de courrier indésirable déplace le message vers la boîte de réception ou le dossier Courrier indésirable. Les utilisateurs peuvent configurer la collection de listes sécurisées pour leur propre boîte aux lettres dans Outlook ou Outlook sur le web (anciennement Outlook Web App). Les administrateurs peuvent configurer la collection de listes sécurisées sur la boîte aux lettres de n’importe quel utilisateur.

Lorsque la règle de courrier indésirable est activée sur la boîte aux lettres, EOP peut déplacer des messages vers le dossier Courrier indésirable en fonction de l’action de verdict de filtrage du courrier indésirable Déplacer le **message** vers le dossier Courrier indésirable ou la liste des expéditeurs bloqués de la boîte aux lettres, et empêcher la livraison des messages dans le dossier Courrier indésirable (en fonction de la liste des expéditeurs Coffre de la boîte aux lettres).

 Lorsque la règle de courrier indésirable est désactivée sur la boîte aux lettres, EOP ne peut pas déplacer les messages vers le dossier Courrier indésirable en fonction de l’action de verdict de filtrage du courrier indésirable Déplacer le **message** vers le dossier Courrier indésirable ou la collection de listes sécurisées de la boîte aux lettres.

Les administrateurs peuvent utiliser Exchange Online PowerShell pour désactiver, activer et afficher l’état de la règle de courrier indésirable sur les boîtes aux lettres. Les administrateurs peuvent également utiliser Exchange Online PowerShell pour configurer les entrées de la collection de listes sécurisées sur les boîtes aux lettres (la liste des expéditeurs Coffre, la liste des destinataires Coffre et la liste des expéditeurs bloqués).

> [!NOTE]
> Messages provenant d’expéditeurs que les utilisateurs ont ajoutés à leur propre Coffre Les listes des expéditeurs ignorent le filtrage des connexions dans le cadre d’EOP (le SCL est -1). Pour empêcher les utilisateurs d’ajouter des entrées à leur liste des expéditeurs Coffre dans Outlook, utilisez la stratégie de groupe comme mentionné dans la section à propos des [paramètres](#about-junk-email-settings-in-outlook) du courrier indésirable dans Outlook plus loin dans cet article. Le filtrage des stratégies, le filtrage du contenu et defender pour Office 365 contrôles de stratégie seront toujours appliqués aux messages.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous pouvez uniquement utiliser Exchange Online PowerShell pour suivre les procédures de cet article. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées Exchange Online avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Destinataires de messagerie (attribué par défaut aux groupes de  **rôles** Gestion de l’organisation, Gestion des destinataires et Destinataires de messagerie **personnalisés)** ou Options utilisateur (attribué aux groupes de rôles Gestion de l’organisation et Help **Desk** par défaut).   Pour ajouter des utilisateurs à des groupes de rôles dans Exchange Online, voir Modifier les groupes de [rôles dans Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Notez que les utilisateurs ayant des autorisations par défaut peuvent suivre ces procédures sur leur propre boîte aux lettres, à condition qu’ils ont accès [à Exchange Online PowerShell.](/powershell/exchange/disable-access-to-exchange-online-powershell)

- Dans les environnements hybrides où Exchange Online Protection protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local pour traduire le verdict de filtrage de courrier indésirable Exchange Online Protection de sorte que la règle de courrier indésirable puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Coffre Les expéditeurs des boîtes aux lettres partagées ne sont pas synchronisés par conception avec Azure AD et EOP.

## <a name="use-exchange-online-powershell-to-enable-or-disable-the-junk-email-rule-in-a-mailbox"></a>Utiliser Exchange Online PowerShell pour activer ou désactiver la règle de courrier indésirable dans une boîte aux lettres

> [!NOTE]
> Vous pouvez uniquement utiliser la cmdlet **Set-MailboxJunkEmailConfiguration** pour désactiver la règle de courrier indésirable sur une boîte aux lettres ouverte dans Outlook (en mode Exchange mis en cache) ou Outlook sur le web. Si la boîte aux lettres n’a pas été ouverte, vous recevez l’erreur : si vous souhaitez supprimer cette erreur pour les opérations en bloc, vous pouvez l’ajouter à la commande `The Junk Email configuration couldn't be set. The user needs to sign in to Outlook Web App before they can modify their Safe Senders and Recipients or Blocked Senders lists.` `-ErrorAction SilentlyContinue` **Set-MailboxJunkEmailConfiguration.**

Pour activer ou désactiver la règle de courrier indésirable dans une boîte aux lettres, utilisez la syntaxe suivante :

```PowerShell
Set-MailboxJunkEmailConfiguration -Identity <MailboxIdentity> -Enabled <$true | $false>
```

Cet exemple désactive la règle de courrier indésirable dans la boîte aux lettres d'Ori Epstein.

```PowerShell
Set-MailboxJunkEmailConfiguration -Identity "Ori Epstein" -Enabled $false
```

Cet exemple désactive la règle de courrier indésirable sur toutes les boîtes aux lettres de l'organisation.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -Enabled $false}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Si l’utilisateur n’a jamais ouvert sa boîte aux lettres, vous pouvez recevoir une erreur lorsque vous exécutez la commande précédente. Pour supprimer cette erreur pour les opérations en bloc, ajoutez-la à la commande `-ErrorAction SilentlyContinue` **Set-MailboxJunkEmailConfiguration.**
>
> - Même si vous désactivez la règle de courrier indésirable, le filtre de courrier indésirable Outlook (selon sa configuration) peut également déterminer si un message est du courrier indésirable et peut déplacer des messages vers le dossier Boîte de réception ou Courrier indésirable en fonction de son propre verdict de courrier indésirable et de la collection de listes sécurisées de la boîte aux lettres. Pour plus d’informations, voir la section à propos des [paramètres](#about-junk-email-settings-in-outlook) du courrier indésirable Outlook dans cet article.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour savoir si vous avez réussi à activer ou désactiver la règle de courrier indésirable sur une boîte aux lettres, suivez l’une des procédures suivantes :

- Remplacez-le par le nom, l’alias ou l’adresse e-mail de la boîte aux lettres, puis exécutez la commande suivante pour vérifier la valeur _\<MailboxIdentity\>_ **de la propriété Enabled** :

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List Enabled
  ```

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Utiliser Exchange Online PowerShell pour configurer la collection de listes sécurisées sur une boîte aux lettres

La collection de listes fiables d'une boîte aux lettres comprend la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués. Par défaut, les utilisateurs peuvent configurer la collection de listes sécurisées sur leur propre boîte aux lettres Outlook ou Outlook sur le web. Les administrateurs peuvent utiliser les paramètres correspondants avec la cmdlet **Set-MailboxJunkEmailConfiguration** pour configurer la collection de listes fiables sur la boîte aux lettres d'un utilisateur. Ces paramètres sont décrits dans le tableau suivant :

****

|Paramètre sur Set-MailboxJunkEmailConfiguration|Outlook sur le web paramètre|
|---|---|
|_BlockedSendersAndDomains_|**Déplacer les messages de ces expéditeurs ou domaines vers mon dossier Courrier indésirable**|
|_ContactsTrusted_|**Approuver le courrier en provenance de mes contacts**|
|_TrustedListsOnly_|**Ne faire confiance qu’aux e-mails provenant d’adresses Coffre mes expéditeurs et listes de domaines et Coffre listes de publipostage**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Ne pas déplacer le courrier de ces expéditeurs vers mon dossier Courrier indésirable**|
|

<sup>\*</sup>**Remarques**:

- Dans **Exchange Online,** les entrées de domaine dans la liste des expéditeurs Coffre ou le paramètre _TrustedSendersAndDomains_ ne sont pas reconnues. Utilisez donc uniquement des adresses de messagerie. Dans EOP autonome avec synchronisation d’annuaires, les entrées de domaine ne sont pas synchronisées par défaut, mais vous pouvez activer la synchronisation pour les domaines. Pour plus d’informations, [voir KB3019657.](https://support.microsoft.com/help/3019657)

- Vous ne pouvez pas modifier directement la liste des destinataires Coffre à l’aide de la cmdlet **Set-MailboxJunkEmailConfiguration** (le paramètre _TrustedRecipientsAndDomains_ ne fonctionne pas). Vous devez modifier la liste des expéditeurs approuvés qui est ensuite synchronisée avec la liste des destinataires approuvés.

Pour configurer la collection de listes fiables sur une boîtes aux lettres, utilisez la syntaxe suivante :

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Pour entrer plusieurs valeurs et annuler les entrées existantes pour les _paramètres BlockedSendersAndDomains_ et _TrustedSendersAndDomains,_ utilisez la syntaxe suivante `"<Value1>","<Value2>"...` : Pour ajouter ou supprimer une ou plusieurs valeurs sans affecter les autres entrées existantes, utilisez la syntaxe suivante : `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

Cet exemple configure les paramètres suivants pour la collection de listes fiables de la boîte aux lettres d'Ori Epstein :

- Ajoutez la valeur shopping@fabrikam.com à la liste des expéditeurs bloqués.

- Supprimez la valeur chris@fourthcoffee.com de la liste Coffre expéditeurs et de la liste Coffre destinataires.

- Configure les contacts du dossier Contacts pour qu'ils soient traités comme des expéditeurs approuvés.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

Cet exemple supprime le domaine contoso.com de la liste des expéditeurs bloqués dans toutes les boîtes aux lettres de l'organisation.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Si l’utilisateur n’a jamais ouvert sa boîte aux lettres, vous pouvez recevoir une erreur lorsque vous exécutez les commandes précédentes. Pour supprimer cette erreur pour les opérations en bloc, ajoutez-la à la commande `-ErrorAction SilentlyContinue` **Set-MailboxJunkEmailConfiguration.**
>
> - Même si la règle de courrier indésirable est désactivée sur la boîte aux lettres, vous pouvez toujours configurer la collection de listes sécurisées et le filtre de courrier indésirable Outlook est en mesure de déplacer des messages vers la boîte de réception ou le dossier Courrier indésirable. Pour plus d’informations, voir la section à propos des [paramètres](#about-junk-email-settings-in-outlook) du courrier indésirable Outlook dans cet article.
>
> - Le Outlook de courrier indésirable a des paramètres de collection de listes sécurisées supplémentaires (par exemple, ajouter automatiquement les personnes que j’envoie à la **Coffre liste des expéditeurs).** Pour plus d'informations, voir [Utiliser les filtres de courrier indésirable pour contrôler les messages affichés](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien configuré la collection de listes fiables d’une boîte aux lettres, suivez l’une des procédures suivantes :

- Remplacez-le par le nom, l’alias ou l’adresse e-mail de la boîte aux lettres, puis exécutez la commande suivante pour vérifier les _\<MailboxIdentity\>_ valeurs des propriétés :

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Si la liste de valeurs est trop longue, utilisez la syntaxe suivante :

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>À propos des paramètres de courrier indésirable dans Outlook

Pour activer, désactiver et configurer les paramètres de filtrage du courrier indésirable côté client disponibles dans Outlook, utilisez la stratégie de groupe. Pour plus d’informations, voir Fichiers de modèles d’administration [(ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030) et Outil de personnalisation Office pour Applications Microsoft 365 pour les grandes entreprises, Office 2019 et Office 2016 et Comment déployer des paramètres de courrier indésirable, tels que la liste des [expéditeurs Coffre,](https://support.microsoft.com/help/2252421)à l’aide de la stratégie de groupe .

Lorsque le filtre de courrier indésirable Outlook  est définie sur  la valeur par défaut Aucun filtrage automatique dans options d’options du courrier indésirable à la maison, Outlook ne tente pas de classer les messages comme courrier indésirable, mais utilise toujours la collection de listes sécurisées (liste des expéditeurs Coffre, liste des destinataires Coffre et liste des \>  \>  \> expéditeurs bloqués) pour déplacer les messages vers le dossier Courrier indésirable après la remise. Pour plus d’informations sur ces paramètres, voir [Vue d’ensemble du filtre de courrier indésirable.](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089)

Lorsque le filtre de courrier indésirable Outlook est défini sur **Faible** ou **Élevé**, le filtre de courrier indésirable Outlook utilise sa propre technologie de filtrage SmartScreen pour identifier et déplacer le courrier indésirable vers le dossier Courrier indésirable. Cette classification du courrier indésirable est distincte du niveau de confiance du courrier indésirable (SCL) déterminé par EOP. En fait, Outlook ignore le SCL d’EOP (sauf si EOP a marqué le message pour ignorer le filtrage du courrier indésirable) et utilise ses propres critères pour déterminer s’il s’agit d’un courrier indésirable. Bien entendu, il est possible que le verdict de courrier indésirable d’EOP Outlook soit le même. Pour plus d’informations sur ces paramètres, voir Modifier le niveau [de protection dans le filtre de courrier indésirable.](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)

> [!NOTE]
> En novembre 2016, Microsoft a cessé de produire des mises à jour des définitions de courrier indésirable pour les filtres SmartScreen dans Exchange et Outlook. Les définitions de courrier indésirable SmartScreen existantes ont été laissées en place, mais leur efficacité se dégradera probablement au fil du temps. Pour plus d’informations, voir l’[Arrêt de la prise en charge de SmartScreen dans Outlook et Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Ainsi, le filtre de courrier indésirable Outlook peut utiliser la collection de listes sécurisées de la boîte aux lettres et sa propre classification de courrier indésirable pour déplacer les messages vers le dossier Courrier indésirable, même si la règle de courrier indésirable est désactivée dans la boîte aux lettres.

Outlook et Outlook sur le web la collection de listes sécurisées. La collection de listes sécurisées est enregistrée dans la boîte aux lettres Exchange Online, de sorte que les modifications apportées à la collection de listes sécurisées dans Outlook apparaissent dans Outlook sur le web, et inversement.

## <a name="limits-for-junk-email-settings"></a>Limites pour les paramètres de courrier indésirable

La collection de listes sécurisées (la liste des expéditeurs Coffre, la liste des destinataires Coffre et la liste des expéditeurs bloqués) stockée dans la boîte aux lettres de l’utilisateur est également synchronisée avec EOP. Avec la synchronisation d’annuaires, la collection de listes sécurisées est synchronisée avec Azure AD.

- La collection de listes sécurisées dans la boîte aux lettres de l’utilisateur a une limite de 510 Ko, qui inclut toutes les listes, ainsi que des paramètres de filtre de courrier indésirable supplémentaires. Si un utilisateur dépasse cette limite, il reçoit une erreur Outlook qui ressemble à ceci :

  > Ajout impossible/impossible aux listes de courrier indésirable du serveur. Vous êtes au-dessus de la taille autorisée sur le serveur. Le filtre de courrier indésirable sur le serveur sera désactivé jusqu’à ce que vos listes de courrier indésirable soient réduites à la taille autorisée par le serveur.

  Pour plus d’informations sur cette limite et sur la façon de la modifier, voir [KB2669081](https://support.microsoft.com/help/2669081).

- La collection de listes sécurisées synchronisées dans EOP présente les limites de synchronisation suivantes :

  - 1 024 entrées au total dans la liste des expéditeurs Coffre, la liste des destinataires Coffre et les contacts externes si le courrier électronique d’Coffre de mes **contacts** est activé.
  - 500 entrées au total dans la liste des expéditeurs bloqués et la liste Domaines bloqués.

  Lorsque la limite d’entrée 1024 est atteinte, les choses suivantes se produisent :

  - La liste cesse d’accepter les entrées dans PowerShell et Outlook sur le web, mais aucune erreur n’est affichée.

    Outlook utilisateurs peuvent continuer à ajouter plus de 1 024 entrées jusqu’à ce qu’ils atteignent la Outlook de 510 Ko. Outlook pouvez utiliser ces entrées supplémentaires, tant qu’un filtre EOP ne bloque pas le message avant sa remise à la boîte aux lettres (règles de flux de messagerie, anti-usurpation, etc.).

- Avec la synchronisation d’annuaires, les entrées sont synchronisées avec Azure AD dans l’ordre suivant :

  1. Contacts de messagerie si **les messages d’confiance provenant de** mes contacts sont activés.
  2. La liste Coffre expéditeurs et la liste des destinataires Coffre sont combinées, dépliquées et triées par ordre alphabétique chaque fois qu’une modification est faite pour les 1 024 premières entrées.

  Les 1 024 premières entrées sont utilisées et les informations pertinentes sont estampillées dans les en-têtes de message.

  Les entrées de plus de 1024 qui n’ont pas été synchronisées avec Azure AD sont traitées par Outlook (et non par Outlook sur le web) et aucune information n’est estampillée dans les en-têtes de message.

Comme vous pouvez le voir, l’activation du message d’Coffre à partir de mes **contacts** réduit le nombre d’expéditeurs et de destinataires Coffre qui peuvent être synchronisés. Si cela est un problème, nous vous recommandons d’utiliser la stratégie de groupe pour désactiver cette fonctionnalité :

- Nom de fichier : outlk16.opax
- Paramètre de stratégie : **faire confiance au courrier électronique des contacts**