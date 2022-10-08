---
title: Configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- m365-security
description: Les administrateurs peuvent apprendre à configurer les paramètres de courrier indésirable dans Exchange Online boîtes aux lettres. La plupart de ces paramètres sont disponibles pour les utilisateurs dans Outlook ou Outlook sur le web.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 2a96902e16ef372e5d9cd1198f15ce2541943aa1
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68060513"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online, les paramètres anti-courrier indésirable de l’organisation sont contrôlés par Exchange Online Protection (EOP). Pour plus d’informations, consultez [protection anti-courrier indésirable dans EOP](anti-spam-protection.md).

Toutefois, il existe également des paramètres anti-courrier indésirable spécifiques que les administrateurs peuvent configurer sur des boîtes aux lettres individuelles dans Exchange Online :

> [!NOTE]
> EOP utilise désormais son propre agent de distribution de flux de courrier pour acheminer les messages vers le dossier Junk Email au lieu d’utiliser la règle de courrier indésirable. Le paramètre _Enabled_ de la cmdlet **Set-MailboxJunkEmailConfiguration** n'a plus d'effet sur le flux de messagerie. EOP route les messages en fonction des actions définies dans les stratégies anti-courrier indésirable. La liste d’expéditeurs approuvés et la liste des expéditeurs bloqués de l’utilisateur continueront de fonctionner comme d’habitude.

- **Déplacer des messages vers le dossier Junk Email en fonction des stratégies anti-courrier indésirable** : lorsqu’une stratégie anti-courrier indésirable est configurée avec l’action **Déplacer le message vers le dossier Courrier indésirable Email** pour un verdict de filtrage du courrier indésirable, le message est déplacé vers le dossier Courrier indésirable Email une fois le message remis à la boîte aux lettres. Pour plus d’informations sur les verdicts de filtrage du courrier indésirable dans les stratégies anti-courrier indésirable, consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md). De même, si le vidage automatique de zéro heure (ZAP) détermine qu’un message remis est du courrier indésirable ou du hameçonnage, le message est déplacé vers le dossier Courrier indésirable Email pour **déplacer le message vers le courrier indésirable Email** dossier pour filtrer le courrier indésirable des actions de verdict. Pour plus d’informations sur ZAP, consultez [La purge automatique de zéro heure (ZAP) dans Exchange Online](zero-hour-auto-purge.md).

- **Paramètres de courrier indésirable que les utilisateurs configurent pour eux-mêmes dans Outlook ou Outlook sur le web** : la collection de listes _sécurisées_ est la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués sur chaque boîte aux lettres. Les entrées de ces listes déterminent si le message est déplacé vers la boîte de réception ou le dossier Courrier indésirable Email. Les utilisateurs peuvent configurer la collection de listes sécurisées pour leur propre boîte aux lettres dans Outlook ou Outlook sur le web (anciennement Outlook Web App). Les administrateurs peuvent configurer la collection de listes sécurisées sur la boîte aux lettres de n’importe quel utilisateur.

EOP est en mesure de déplacer les messages vers le dossier Courrier indésirable Email en fonction de l’action de filtrage du courrier indésirable **Déplacer le message vers le dossier Courrier indésirable Email** ou la liste expéditeurs bloqués sur la boîte aux lettres, et d’empêcher la remise des messages au dossier Courrier indésirable Email (en fonction de la liste Expéditeurs approuvés sur la boîte aux lettres).

Les administrateurs peuvent utiliser Exchange Online PowerShell pour configurer des entrées dans la collection de listes sécurisées sur les boîtes aux lettres (liste des expéditeurs approuvés, liste des destinataires approuvés et liste des expéditeurs bloqués).

> [!NOTE]
> Les messages des expéditeurs que les utilisateurs ont ajoutés à leurs propres listes d’expéditeurs approuvés ignorent le filtrage de contenu dans le cadre d’EOP (la liste SCL est -1). Pour empêcher les utilisateurs d’ajouter des entrées à leur liste d’expéditeurs approuvés dans Outlook, utilisez stratégie de groupe comme indiqué dans la section [À propos de l’e-mail indésirable dans](#about-junk-email-settings-in-outlook) la section Outlook plus loin dans cet article. Le filtrage des stratégies, le filtrage de contenu et les vérifications de Defender pour Office 365 sont toujours appliqués aux messages.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous pouvez uniquement utiliser Exchange Online PowerShell pour effectuer les procédures décrites dans cet article. Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous devez disposer d’autorisations dans Exchange Online avant de pouvoir effectuer les procédures décrites dans cet article. Plus précisément, vous avez besoin du rôle **Destinataires du courrier** (qui est attribué aux groupes de rôles Gestion de l’organisation, **Gestion** **des destinataires et Destinataires du courrier personnalisé** par défaut) ou du rôle **Options utilisateur** (qui est attribué aux groupes de rôles Gestion de **l’organisation** et **Support** technique par défaut). Pour ajouter des utilisateurs à des groupes de rôles dans Exchange Online, consultez [Modifier les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Notez que les utilisateurs disposant d’autorisations par défaut peuvent effectuer ces mêmes procédures sur leur propre boîte aux lettres, tant qu’ils ont [accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

- In hybrid environments where EOP protects on-premises Exchange mailboxes, you need to configure mail flow rules (also known as transport rules) in on-premises Exchange. These mail flow rules translate the EOP spam filtering verdict so the junk email rule in the mailbox can move the message to the Junk Email folder. For details, see [Configure EOP to deliver spam to the Junk Email folder in hybrid environments](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Les expéditeurs approuvés pour les boîtes aux lettres partagées ne sont pas synchronisés avec Azure AD et EOP par conception.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Utiliser Exchange Online PowerShell pour configurer la collection de listes de sécurité sur une boîte aux lettres

La collection de listes fiables d'une boîte aux lettres comprend la liste des expéditeurs approuvés, la liste des destinataires approuvés et la liste des expéditeurs bloqués. Par défaut, les utilisateurs peuvent configurer la collection de listes sécurisées sur leur propre boîte aux lettres dans Outlook ou Outlook sur le web. Les administrateurs peuvent utiliser les paramètres correspondants avec la cmdlet **Set-MailboxJunkEmailConfiguration** pour configurer la collection de listes fiables sur la boîte aux lettres d'un utilisateur. Ces paramètres sont décrits dans le tableau suivant :

|Paramètre sur Set-MailboxJunkEmailConfiguration|paramètre Outlook sur le web|
|---|---|
|_BlockedSendersAndDomains_|**Déplacer les messages de ces expéditeurs ou domaines vers mon dossier Courrier indésirable**|
|_ContactsTrusted_|**Approuver le courrier en provenance de mes contacts**|
|_TrustedListsOnly_|**Approuver uniquement les e-mails provenant d’adresses dans ma liste d’expéditeurs et de domaines approuvés et mes listes de diffusion sécurisées**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Ne déplacez pas l’e-mail de ces expéditeurs vers mon dossier Junk Email**|

<sup>\*</sup>**Remarques** :

- Dans Exchange Online, les **entrées de domaine** dans la liste des expéditeurs approuvés ou le paramètre _TrustedSendersAndDomains_ ne sont pas reconnues. Utilisez donc uniquement des adresses e-mail. Dans EOP autonome avec synchronisation d’annuaires, les entrées de domaine ne sont pas synchronisées par défaut, mais vous pouvez activer la synchronisation pour les domaines. Pour plus d’informations, consultez [KB3019657](https://support.microsoft.com/help/3019657).
- Vous ne pouvez pas modifier directement la liste des destinataires approuvés à l’aide de l’applet **de commande Set-MailboxJunkEmailConfiguration** (le paramètre _TrustedRecipientsAndDomains_ ne fonctionne pas). Vous devez modifier la liste des expéditeurs approuvés qui est ensuite synchronisée avec la liste des destinataires approuvés.

Pour configurer la collection de listes fiables sur une boîtes aux lettres, utilisez la syntaxe suivante :

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Pour entrer plusieurs valeurs et remplacer toutes les entrées existantes pour les _paramètres BlockedSendersAndDomains_ et _TrustedSendersAndDomains_ , utilisez la syntaxe suivante : `"<Value1>","<Value2>"...`. Pour ajouter ou supprimer une ou plusieurs valeurs sans affecter d’autres entrées existantes, utilisez la syntaxe suivante : `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

Cet exemple configure les paramètres suivants pour la collection de listes fiables de la boîte aux lettres d'Ori Epstein :

- Ajoutez la valeur shopping@fabrikam.com à la liste des expéditeurs bloqués.
- Supprimez la valeur chris@fourthcoffee.com de la liste Des expéditeurs approuvés et de la liste des destinataires approuvés.
- Configure les contacts du dossier Contacts pour qu'ils soient traités comme des expéditeurs approuvés.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

Cet exemple supprime le domaine contoso.com de la liste des expéditeurs bloqués dans toutes les boîtes aux lettres de l'organisation.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Si l’utilisateur n’a jamais ouvert sa boîte aux lettres, vous pouvez recevoir une erreur lorsque vous exécutez les commandes précédentes. Pour supprimer cette erreur pour les opérations en bloc, ajoutez `-ErrorAction SilentlyContinue` à la commande **Set-MailboxJunkEmailConfiguration** .
> - Le filtre Outlook Junk Email contient des paramètres de collecte de liste de sécurité supplémentaires (par exemple, **ajouter automatiquement des personnes que j’envoie par e-mail à la liste des expéditeurs approuvés**). Pour plus d'informations, voir [Utiliser les filtres de courrier indésirable pour contrôler les messages affichés](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien configuré la collection de listes fiables d’une boîte aux lettres, suivez l’une des procédures suivantes :

- Remplacez _\<MailboxIdentity\>_ par le nom, l’alias ou l’adresse e-mail de la boîte aux lettres, puis exécutez la commande suivante pour vérifier les valeurs de propriété :

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Si la liste des valeurs est trop longue, utilisez cette syntaxe :

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>À propos des paramètres de courrier indésirable dans Outlook

Pour activer, désactiver et configurer les paramètres de filtrage du courrier indésirable côté client disponibles dans Outlook, utilisez la stratégie de groupe. Pour plus d’informations, consultez les fichiers de modèle d’administration [(ADMX/ADML) et l’outil de personnalisation Office pour Applications Microsoft 365 pour les grandes entreprises, Office 2019 et Office 2016](https://www.microsoft.com/download/details.aspx?id=49030), ainsi [que comment déployer des paramètres de courrier indésirable, tels que la liste des expéditeurs approuvés, à l’aide de stratégie de groupe](https://support.microsoft.com/help/2252421).

 Lorsque le filtre Outlook Junk Email est défini sur la valeur par défaut **Aucun filtrage automatique** dans les **options** De courrier indésirable à **domicile** \>  \> \>, Outlook ne tente pas de classer les messages comme courrier indésirable, mais utilise toujours la collection de listes sécurisées (liste des expéditeurs approuvés, liste des destinataires approuvés et liste des expéditeurs bloqués) pour déplacer les messages vers le dossier Courrier indésirable Email après la remise. Pour plus d’informations sur ces paramètres, consultez [Vue d’ensemble du filtre Junk Email](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

> [!NOTE]
> Dans les organisations Microsoft 365, nous vous recommandons de laisser le filtre Junk Email dans Outlook défini sur **Aucun filtrage automatique** pour éviter les conflits inutiles (positifs et négatifs) avec les verdicts de filtrage du courrier indésirable d’EOP.

Lorsque le filtre de courrier indésirable Outlook est défini sur **Faible** ou **Élevé**, le filtre de courrier indésirable Outlook utilise sa propre technologie de filtrage SmartScreen pour identifier et déplacer le courrier indésirable vers le dossier Courrier indésirable. Cette classification du courrier indésirable est distincte du niveau de confiance du courrier indésirable (SCL) déterminé par EOP. En fait, Outlook ignore la liste SCL d’EOP (sauf si EOP a marqué le message pour ignorer le filtrage du courrier indésirable) et utilise ses propres critères pour déterminer si le message est du courrier indésirable. Bien sûr, il est possible que le verdict de courrier indésirable d’EOP et d’Outlook soit le même. Pour plus d’informations sur ces paramètres, consultez [Modifier le niveau de protection dans le filtre junk Email](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> En novembre 2016, Microsoft a cessé de produire des mises à jour de définition de courrier indésirable pour les filtres SmartScreen dans Exchange et Outlook. Les définitions de courrier indésirable SmartScreen existantes ont été conservées, mais leur efficacité se dégradera probablement au fil du temps. Pour plus d’informations, voir l’[Arrêt de la prise en charge de SmartScreen dans Outlook et Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Par conséquent, le filtre Outlook Junk Email peut utiliser la collection de listes sécurisées de la boîte aux lettres et sa propre classification de courrier indésirable pour déplacer les messages vers le dossier Junk Email.

Outlook et Outlook sur le web prennent tous les deux en charge la collection de listes de sécurité. La collection de listes sécurisées est enregistrée dans la boîte aux lettres Exchange Online, de sorte que les modifications apportées à la collection de listes sécurisées dans Outlook apparaissent dans Outlook sur le web, et inversement.

## <a name="limits-for-junk-email-settings"></a>Limites pour les paramètres de courrier indésirable

La collection de listes sécurisées (liste des expéditeurs approuvés, liste des destinataires approuvés et liste des expéditeurs bloqués) stockée dans la boîte aux lettres de l’utilisateur est également synchronisée avec EOP. Avec la synchronisation d’annuaires, la collection de listes sécurisées est synchronisée avec Azure AD.

- La collection de listes sécurisées dans la boîte aux lettres de l’utilisateur a une limite de 510 Ko, ce qui inclut toutes les listes, ainsi que des paramètres de filtre de courrier indésirable supplémentaires. Si un utilisateur dépasse cette limite, il reçoit une erreur Outlook qui ressemble à ceci :

  > Impossible/Impossible d’ajouter aux listes de courrier indésirable du serveur. Vous dépassez la taille autorisée sur le serveur. Le filtre courrier indésirable sur le serveur est désactivé jusqu’à ce que vos listes de courrier indésirable aient été réduites à la taille autorisée par le serveur.

  Pour plus d’informations sur cette limite et sur la façon de la modifier, consultez [KB2669081](https://support.microsoft.com/help/2669081).

- La collection de listes sécurisées synchronisées dans EOP a les limites de synchronisation suivantes :
  - 1 024 entrées totales dans la liste Des expéditeurs approuvés, la liste des destinataires approuvés et les contacts externes si **l’adresse e-mail d’approbation de mes contacts** est activée.
  - 500 entrées totales dans la liste Des expéditeurs bloqués et la liste Domaines bloqués.

  Lorsque la limite d’entrée 1024 est atteinte, les événements suivants se produisent :

  - La liste cesse d’accepter les entrées dans PowerShell et Outlook sur le web, mais aucune erreur n’est affichée.

    Les utilisateurs Outlook peuvent continuer à ajouter plus de 1 024 entrées jusqu’à ce qu’ils atteignent la limite Outlook de 510 Ko. Outlook peut utiliser ces entrées supplémentaires, tant qu’un filtre EOP ne bloque pas le message avant la remise à la boîte aux lettres (règles de flux de messagerie, anti-usurpation d’identité, etc.).

- Avec la synchronisation d’annuaires, les entrées sont synchronisées avec Azure AD dans l’ordre suivant :
  1. Contacts de messagerie si **l’adresse e-mail d’approbation de mes contacts** est activée.
  2. La liste d’expéditeurs approuvés et la liste des destinataires approuvés sont combinées, dédupliquées et triées par ordre alphabétique chaque fois qu’une modification est apportée aux premières entrées 1024.

  Les 1 024 premières entrées sont utilisées et les informations pertinentes sont marquées dans les en-têtes de message.

  Les entrées de plus de 1024 qui n’ont pas été synchronisées avec Azure AD sont traitées par Outlook (pas Outlook sur le web) et aucune information n’est horodatage dans les en-têtes de message.

Comme vous pouvez le voir, l’activation **de l’e-mail d’approbation à partir de mon paramètre contacts** réduit le nombre d’expéditeurs approuvés et de destinataires approuvés qui peuvent être synchronisés. S’il s’agit d’un problème, nous vous recommandons d’utiliser stratégie de groupe pour désactiver cette fonctionnalité :

- Nom du fichier : outlk16.opax
- Paramètre de stratégie : **Approuver le courrier électronique des contacts**
