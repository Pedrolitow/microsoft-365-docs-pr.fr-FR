---
title: Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online. Un grand nombre de ces paramètres sont disponibles pour les utilisateurs dans Outlook ou Outlook sur le Web.
ms.openlocfilehash: 632c6f37b80cdc38b513f66ad42e4a5c25b41f25
ms.sourcegitcommit: c083602dda3cdcb5b58cb8aa070d77019075f765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "48203346"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Configurer les paramètres de courrier indésirable dans les boîtes aux lettres Exchange Online

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, les paramètres anti-courrier indésirable de l’organisation sont contrôlés par Exchange Online Protection (EOP). Pour plus d’informations, consultez la rubrique [protection contre le courrier indésirable dans EOP](anti-spam-protection.md).

Toutefois, il existe également des paramètres de blocage du courrier indésirable que les administrateurs peuvent configurer sur des boîtes aux lettres individuelles dans Exchange Online :

- **Activer ou désactiver la règle de courrier indésirable**: la règle de courrier indésirable est une règle de boîte de réception masquée nommée « règle de courrier indésirable » activée par défaut dans toutes les boîtes aux lettres. La règle de courrier indésirable contrôle les fonctionnalités suivantes :

  - **Déplacer des messages vers le dossier courrier indésirable en fonction des stratégies de blocage**du courrier indésirable : lorsqu’une stratégie de blocage du courrier indésirable est configurée avec l’action **déplacer le message vers le dossier courrier indésirable** pour le filtrage du courrier indésirable, la règle de filtrage du courrier indésirable déplace le message vers le dossier courrier indésirable une fois que le Pour plus d’informations sur le filtrage du courrier indésirable dans les stratégies de blocage du courrier indésirable, consultez la rubrique [configurer des stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md). De même, si la purge automatique (ZAP) zéro heure détermine un message remis est courrier indésirable ou hameçon, la règle de filtrage du courrier indésirable déplace le message vers le dossier courrier indésirable pour **déplacer le message vers le dossier courrier indésirable** actions de filtrage du courrier indésirable. Pour plus d’informations sur ZAP, reportez-vous à la rubrique [vidage automatique des heures (ZAP) dans Exchange Online](zero-hour-auto-purge.md).

  - **Paramètres de courrier indésirable que les utilisateurs configurent pour eux-mêmes dans Outlook ou Outlook sur le Web**: la _collection_ de listes fiables est la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués de chaque boîte aux lettres. Les entrées de ces listes déterminent si la règle de courrier indésirable déplace le message vers la boîte de réception ou le dossier courrier indésirable. Les utilisateurs peuvent configurer la collection de listes fiables pour leur propre boîte aux lettres dans Outlook ou Outlook sur le Web (anciennement Outlook Web App). Les administrateurs peuvent configurer la collection de listes fiables sur la boîte aux lettres de l’utilisateur.

Lorsque la règle de courrier indésirable est activée dans la boîte aux lettres, EOP peut déplacer les messages vers le dossier courrier indésirable en fonction de l’action de filtrage du courrier indésirable **déplacer le message vers le dossier courrier indésirable** ou la liste des expéditeurs bloqués dans la boîte aux lettres, et empêcher la remise des messages dans le dossier courrier indésirable

 Lorsque la règle de courrier indésirable est désactivée sur la boîte aux lettres, EOP ne peut pas déplacer les messages vers le dossier courrier indésirable en fonction de l’action de filtrage du courrier indésirable **déplacer le message vers le dossier courrier indésirable** ou la collection de listes fiables sur la boîte aux lettres.

Les administrateurs peuvent utiliser Exchange Online PowerShell pour désactiver, activer et afficher l’état de la règle de courrier indésirable sur les boîtes aux lettres. Les administrateurs peuvent également utiliser Exchange Online PowerShell pour configurer les entrées de la collection de listes fiables sur les boîtes aux lettres (la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués).

> [!NOTE]
> Les messages provenant d’expéditeurs que les utilisateurs ont ajoutés à leurs propres listes d’expéditeurs approuvés ignorent le filtrage des connexions dans le cadre d’EOP (le SCL est-1). Pour empêcher les utilisateurs d’ajouter des entrées à leur liste des expéditeurs approuvés dans Outlook, utilisez la stratégie de groupe comme mentionné dans la section  [à propos des paramètres du courrier indésirable dans Outlook](#about-junk-email-settings-in-outlook) plus loin dans cette rubrique. Le filtrage des stratégies, le filtrage du contenu et les vérifications de protection avancée contre les menaces seront toujours appliqués aux messages.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous pouvez utiliser Exchange Online PowerShell uniquement pour effectuer ces procédures. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer ces procédures. Plus précisément, vous avez besoin du rôle **destinataires de messagerie** (qui est affecté par défaut aux groupes de rôles gestion de l' **organisation**, **gestion des destinataires**et **destinataires de messages personnalisés** ) ou aux **options utilisateur** (qui sont affectées par défaut aux groupes de rôles gestion de l' **organisation** et **support technique** ). Pour ajouter des utilisateurs à des groupes de rôles dans Exchange Online, consultez la rubrique [modifier des groupes de rôles dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups#modify-role-groups). Notez qu’un utilisateur disposant des autorisations par défaut peut effectuer ces mêmes procédures sur sa propre boîte aux lettres, à condition qu’il ait [accès à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/disable-access-to-exchange-online-powershell).

- Dans les environnements de EOP autonomes où EOP protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local pour traduire le verdict de filtrage de courrier indésirable EOP de sorte que la règle de courrier indésirable puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer une protection Exchange Online (EOP) autonome pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md).

- Les expéditeurs approuvés pour les boîtes aux lettres partagées ne sont pas synchronisés avec Azure AD et EOP par conception.

## <a name="use-exchange-online-powershell-to-enable-or-disable-the-junk-email-rule-in-a-mailbox"></a>Utiliser Exchange Online PowerShell pour activer ou désactiver la règle de courrier indésirable dans une boîte aux lettres

> [!NOTE]
> Vous pouvez uniquement utiliser la cmdlet **Set-MailboxJunkEmailConfiguration** pour désactiver la règle de courrier indésirable sur une boîte aux lettres ouverte dans Outlook (en mode Exchange mis en cache) ou Outlook sur le web. Si la boîte aux lettres n’a pas été ouverte, vous recevez l’erreur suivante : `The Junk Email configuration couldn't be set. The user needs to sign in to Outlook Web App before they can modify their Safe Senders and Recipients or Blocked Senders lists.` si vous souhaitez supprimer cette erreur pour les opérations en bloc, vous pouvez ajouter `-ErrorAction SilentlyContinue` à la commande **Set-MailboxJunkEmailConfiguration** .

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Si l’utilisateur n’a jamais ouvert sa boîte aux lettres, il se peut que vous receviez une erreur lors de l’exécution de la commande précédente. Pour supprimer cette erreur pour les opérations en bloc, ajoutez `-ErrorAction SilentlyContinue` à la commande **Set-MailboxJunkEmailConfiguration** .
>
> - Même si vous désactivez la règle de courrier indésirable, le filtre de courrier indésirable d’Outlook (en fonction de sa configuration) peut également déterminer si un message est un courrier indésirable et déplacer des messages vers le dossier boîte de réception ou courrier indésirable en fonction de son verdict de courrier indésirable et de la collection de listes fiables sur la boîte aux lettres Pour plus d’informations, consultez la section [À propos des paramètres de courrier indésirable dans Outlook](#about-junk-email-settings-in-outlook) dans cette rubrique.

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour savoir si vous avez réussi à activer ou désactiver la règle de courrier indésirable sur une boîte aux lettres, suivez l’une des procédures suivantes :

- Remplacez _\<MailboxIdentity\>_ par le nom, l’alias ou l’adresse de messagerie de la boîte aux lettres, puis exécutez la commande suivante pour vérifier la valeur de la propriété **Enabled** :

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List Enabled
  ```

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Utiliser Exchange Online PowerShell pour configurer la collection de listes fiables sur une boîte aux lettres

La collection de listes fiables d'une boîte aux lettres comprend la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués. Par défaut, les utilisateurs peuvent configurer la collection de listes fiables sur leur boîte aux lettres dans Outlook ou Outlook sur le Web. Les administrateurs peuvent utiliser les paramètres correspondants avec la cmdlet **Set-MailboxJunkEmailConfiguration** pour configurer la collection de listes fiables sur la boîte aux lettres d'un utilisateur. Ces paramètres sont décrits dans le tableau suivant :

****

|Paramètre sur Set-MailboxJunkEmailConfiguration|Paramètre Outlook sur le Web|
|---|---|
|_BlockedSendersAndDomains_|**Déplacer les messages de ces expéditeurs ou domaines vers mon dossier Courrier indésirable**|
|_ContactsTrusted_|**Approuver le courrier en provenance de mes contacts**|
|_TrustedListsOnly_|**Approuver uniquement les messages provenant d’adresses figurant dans la liste des expéditeurs et des domaines approuvés et les listes de publipostage sûres**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Ne pas déplacer le courrier électronique de ces expéditeurs vers mon dossier courrier indésirable**|
|

<sup>\*</sup>**Remarques**:

- Dans Exchange Online, les **entrées de domaine** de la liste des expéditeurs approuvés ou du paramètre _TrustedSendersAndDomains_ ne sont pas reconnues, donc Utilisez uniquement des adresses de messagerie. Dans EOP autonome avec synchronisation d’annuaires, les entrées de domaine ne sont pas synchronisées par défaut, mais vous pouvez activer la synchronisation pour les domaines. Pour plus d’informations, consultez la rubrique [KB3019657](https://support.microsoft.com/help/3019657).

- Vous ne pouvez pas modifier directement la liste des destinataires approuvés à l’aide de la cmdlet **Set-MailboxJunkEmailConfiguration** (le paramètre _TrustedRecipientsAndDomains_ ne fonctionne pas). Vous devez modifier la liste des expéditeurs approuvés qui est ensuite synchronisée avec la liste des destinataires approuvés.

Pour configurer la collection de listes fiables sur une boîtes aux lettres, utilisez la syntaxe suivante :

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Pour entrer plusieurs valeurs et remplacer toutes les entrées existantes pour les paramètres _BlockedSendersAndDomains_ et _TrustedSendersAndDomains_ , utilisez la syntaxe suivante : `"<Value1>","<Value2>"...` . Pour ajouter ou supprimer une ou plusieurs valeurs sans affecter les autres entrées existantes, utilisez la syntaxe suivante : `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

Cet exemple configure les paramètres suivants pour la collection de listes fiables de la boîte aux lettres d'Ori Epstein :

- Ajoutez la valeur shopping@fabrikam.com à la liste des expéditeurs bloqués.

- Supprimez la valeur chris@fourthcoffee.com de la liste des expéditeurs approuvés et de la liste des destinataires fiables.

- Configure les contacts du dossier Contacts pour qu'ils soient traités comme des expéditeurs approuvés.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

Cet exemple supprime le domaine contoso.com de la liste des expéditeurs bloqués dans toutes les boîtes aux lettres de l'organisation.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MailboxJunkEmailConfiguration](https://docs.microsoft.com/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Si l’utilisateur n’a jamais ouvert sa boîte aux lettres, il se peut que vous receviez une erreur lors de l’exécution des commandes précédentes. Pour supprimer cette erreur pour les opérations en bloc, ajoutez `-ErrorAction SilentlyContinue` à la commande **Set-MailboxJunkEmailConfiguration** .
>
> - Même si la règle de courrier indésirable est désactivée sur la boîte aux lettres, vous pouvez toujours configurer la collection de listes fiables et le filtre de courrier indésirable Outlook est capable de déplacer des messages vers la boîte de réception ou le dossier courrier indésirable. Pour plus d'informations, consultez la section [À propos des paramètres de courrier indésirable dans Outlook](#about-junk-email-settings-in-outlook) dans cette rubrique.
>
> - Le filtre de courrier indésirable d’Outlook comporte des paramètres de collection de listes fiables supplémentaires (par exemple, **Ajouter automatiquement les personnes auxquelles j’envoie un message électronique à la liste des expéditeurs approuvés**). Pour plus d'informations, voir [Utiliser les filtres de courrier indésirable pour contrôler les messages affichés](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien configuré la collection de listes fiables d’une boîte aux lettres, suivez l’une des procédures suivantes :

- Remplacez _\<MailboxIdentity\>_ par le nom, l’alias ou l’adresse de messagerie de la boîte aux lettres, puis exécutez la commande suivante pour vérifier les valeurs de la propriété :

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Si la liste de valeurs est trop longue, utilisez la syntaxe suivante :

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>À propos des paramètres de courrier indésirable dans Outlook

Pour activer, désactiver et configurer les paramètres de filtrage du courrier indésirable côté client disponibles dans Outlook, utilisez la stratégie de groupe. Pour plus d’informations, reportez-vous à la rubrique [Administrative Template Files (ADMX/adml) and Office Customization Tool for Microsoft 365 Apps for Enterprise, office 2019, and office 2016](https://www.microsoft.com/download/details.aspx?id=49030) et [comment déployer les paramètres de courrier indésirable, tels que la liste des expéditeurs approuvés, à l’aide de la stratégie de groupe](https://support.microsoft.com/help/2252421).

Lorsque le filtre de courrier indésirable Outlook est défini sur la valeur par défaut **aucun filtrage automatique** dans les options options de courrier indésirable du **domicile** \> **Junk** \> **Junk E-Mail Options** \> **Options**, Outlook ne tente pas de classer les massage comme courrier indésirable, mais il utilise toujours l’ensemble de listes fiables (la liste des expéditeurs approuvés, la liste des destinataires fiables et la liste des expéditeurs bloqués) pour déplacer les Pour plus d’informations sur ces paramètres, consultez [la rubrique vue d’ensemble du filtre de courrier indésirable](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

Lorsque le filtre de courrier indésirable Outlook est défini sur **Faible** ou **Élevé**, le filtre de courrier indésirable Outlook utilise sa propre technologie de filtrage SmartScreen pour identifier et déplacer le courrier indésirable vers le dossier Courrier indésirable. Cette classification de courrier indésirable est distincte du seuil de probabilité de courrier indésirable (SCL) déterminé par EOP. En fait, Outlook ignore la valeur SCL d’EOP (sauf si EOP a marqué le message pour ignorer le filtrage du courrier indésirable) et utilise ses propres critères pour déterminer si le message est un courrier indésirable. Bien entendu, il est possible que le verdict de courrier indésirable de EOP et Outlook soit le même. Pour plus d’informations sur ces paramètres, consultez [la rubrique modifier le niveau de protection dans le filtre de courrier indésirable](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> En novembre 2016, Microsoft a cessé de produire des mises à jour de définition de courrier indésirable pour les filtres SmartScreen dans Exchange et Outlook. Les définitions de courrier indésirable SmartScreen existantes étaient conservées, mais leur efficacité sera vraisemblablement dégradée au fil du temps. Pour plus d’informations, voir l’[Arrêt de la prise en charge de SmartScreen dans Outlook et Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Par conséquent, le filtre de courrier indésirable d’Outlook peut utiliser la collection de listes fiables de la boîte aux lettres et sa propre classification de courrier indésirable pour déplacer des messages vers le dossier courrier indésirable, même si la règle de courrier indésirable est désactivée dans la boîte aux lettres.

Outlook et Outlook sur le Web prennent tous deux en charge la collection de listes fiables. La collection de listes fiables étant enregistrée dans la boîte aux lettres Exchange Online, les modifications apportées à la collection de listes fiables dans Outlook apparaissent dans Outlook sur le Web, et inversement.

## <a name="limits-for-junk-email-settings"></a>Limites pour les paramètres du courrier indésirable

La collection de listes fiables (la liste des expéditeurs approuvés, la liste des destinataires fiables et la liste des expéditeurs bloqués) stockée dans la boîte aux lettres de l’utilisateur est également synchronisée avec EOP. Avec la synchronisation d’annuaires, la collection de listes fiables est synchronisée avec Azure AD.

- La collection de listes fiables dans la boîte aux lettres de l’utilisateur a une limite de 510 Ko, qui inclut toutes les listes, ainsi que d’autres paramètres de filtrage du courrier indésirable. Si un utilisateur dépasse cette limite, un message d’erreur Outlook semblable à celui-ci s’affiche :

  > Impossible/impossible d’ajouter des listes de courrier indésirable au serveur. Vous avez dépassé la taille autorisée sur le serveur. Le filtre de courrier indésirable sur le serveur est désactivé jusqu’à ce que vos listes de courrier indésirable aient été réduites à la taille autorisée par le serveur.

  Pour plus d’informations sur cette limite et sur la façon de la modifier, voir [KB2669081](https://support.microsoft.com/help/2669081).

- La collection de listes fiables synchronisées dans EOP a les limites de synchronisation suivantes :

  - 1024 total des entrées de la liste des expéditeurs approuvés, de la liste des destinataires approuvés et des contacts externes si l’option **approuver le courrier de mes contacts** est activée.
  - 500 Total des entrées de la liste des expéditeurs bloqués et de la liste des domaines bloqués.

  Lorsque la limite d’entrée 1024 est atteinte, les événements suivants se produisent :

  - La liste cesse d’accepter les entrées dans PowerShell et Outlook sur le Web, mais aucune erreur n’est affichée.

    Les utilisateurs d’Outlook peuvent continuer à ajouter plus de 1024 entrées jusqu’à ce qu’ils atteignent la limite de 510 Ko pour Outlook. Outlook peut utiliser ces entrées supplémentaires, tant qu’un filtre EOP ne bloque pas le message avant la remise à la boîte aux lettres (règles de flux de messagerie, protection contre l’usurpation, etc.).

- Avec la synchronisation d’annuaires, les entrées sont synchronisées avec Azure AD dans l’ordre suivant :

  1. Contacts de messagerie si l’option **approuver le courrier de mes contacts** est activée.
  2. La liste des expéditeurs approuvés et la liste des destinataires fiables sont combinées, dédupliquées et triées par ordre alphabétique chaque fois qu’une modification est apportée aux 1024 premières entrées.

  Les premières entrées 1024 sont utilisées et les informations pertinentes sont marquées dans les en-têtes de message.

  Les entrées supérieures à 1024 et qui n’ont pas été synchronisées avec Azure AD sont traitées par Outlook (pas Outlook sur le Web), et aucune information n’est indiquée dans les en-têtes des messages.

Comme vous pouvez le constater, l’activation du paramètre **approuver le courrier électronique à partir de mes contacts** réduit le nombre d’expéditeurs approuvés et de destinataires approuvés pouvant être synchronisés. S’il s’agit d’un problème, nous vous recommandons d’utiliser la stratégie de groupe pour désactiver cette fonctionnalité :

- Nom de fichier : outlk16. opax
- Paramètre de stratégie : **approuver la messagerie des contacts**
