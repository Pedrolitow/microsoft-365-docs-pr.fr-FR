---
title: Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment identifier les différents types de mise en attente qui peuvent être placés sur une boîte aux lettres Exchange Online dans Microsoft 365.
ms.openlocfilehash: c0f5d11066169181b524632c7a1340c54f0061f0
ms.sourcegitcommit: 33afa334328cc4e3f2474abd611c1411adabd39f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48370334"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online

Cet article explique comment identifier les mises en place de boîtes aux lettres Exchange Online dans Microsoft 365.

Microsoft 365 offre plusieurs façons pour votre organisation d’empêcher la suppression définitive du contenu des boîtes aux lettres. Cela permet à votre organisation de conserver le contenu pour répondre aux réglementations de conformité ou pendant les enquêtes juridiques et autres. Voici une liste des fonctionnalités de rétention (également *appelées conservations)* dans Office 365 :

- **[Attente pour litige](create-a-litigation-hold.md):** Les conserves appliquées aux boîtes aux lettres des utilisateurs dans Exchange Online.

- **[EDiscovery hold](create-ediscovery-holds.md):** Les dossiers qui sont associés à un cas eDiscovery principal dans le centre de sécurité et conformité. Les conserves eDiscovery peuvent être appliquées aux boîtes aux lettres des utilisateurs et à la boîte aux lettres correspondante pour les groupes Microsoft 365 et Microsoft Teams.

- **[In-Place Hold](https://docs.microsoft.com/Exchange/security-and-compliance/create-or-remove-in-place-holds):** Les conserves appliquées aux boîtes aux lettres des utilisateurs à l’aide de l’outil In-Place eDiscovery & Hold dans le Centre d’administration Exchange dans Exchange Online.

- **[Stratégies de rétention Microsoft 365](retention.md):** Peut être configuré pour conserver (ou conserver, puis supprimer) le contenu des boîtes aux lettres utilisateur dans Exchange Online et dans la boîte aux lettres correspondante pour les Groupes Microsoft 365 et Microsoft Teams. Vous pouvez également créer une stratégie de rétention pour conserver les conversations Skype Entreprise, qui sont stockées dans les boîtes aux lettres des utilisateurs.

  Deux types de stratégies de rétention Microsoft 365 peuvent être affectés à des boîtes aux lettres.

    - **Stratégies de rétention d’emplacement spécifiques :** Ce sont des stratégies qui sont affectées aux emplacements de contenu d’utilisateurs spécifiques. Vous utilisez la cmdlet **Get-Mailbox** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention attribuées à des boîtes aux lettres spécifiques. Pour plus d’informations sur ce type de stratégie de rétention, voir la section A policy [with specific inclusions or exclusions](create-retention-policies.md#a-policy-with-specific-inclusions-or-exclusions) from the retention policy documentation.

    - **Stratégies de rétention à l’échelle de l’organisation :** Ce sont des stratégies qui sont affectées à tous les emplacements de contenu de votre organisation. Vous utilisez la cmdlet **Get-OrganizationConfig** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation. Pour plus d’informations sur ce type de stratégie de rétention, voir la section [A](create-retention-policies.md#a-policy-that-applies-to-entire-locations) stratégie qui s’applique à des emplacements entiers à partir de la documentation de stratégie de rétention.

- **Étiquettes de rétention [Microsoft 365](retention.md)** : si un utilisateur applique une étiquette de rétention Microsoft 365  (configurée pour conserver du contenu ou conserver, puis supprimer du contenu) à n’importe quel dossier ou élément de sa boîte aux lettres, une conservation est placée sur la boîte aux lettres comme si elle avait été placée en conservation pour litige ou affectée à une stratégie de rétention Microsoft 365. Pour plus d’informations, voir la section Identification des boîtes aux lettres en attente, car une étiquette de rétention [a](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) été appliquée à un dossier ou à un élément dans cet article.

Pour gérer les boîtes aux lettres placées en conservation, vous pouvez être tenue d’identifier le type de conservation qui est placé sur une boîte aux lettres afin de pouvoir effectuer des tâches telles que la modification de la durée de la conservation, la suppression temporaire ou définitive de la conservation ou l’exclusion d’une boîte aux lettres d’une stratégie de rétention Microsoft 365. Dans ce cas, la première étape consiste à identifier le type de mise en attente placée sur la boîte aux lettres. Et comme plusieurs mises en attente (et différents types de mise en attente) peuvent être placées sur une seule boîte aux lettres, vous devez identifier toutes les mises en attente placées sur une boîte aux lettres si vous souhaitez supprimer ou modifier une mise en attente.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Étape 1 : Obtenir le GUID des mises en place sur une boîte aux lettres

Vous pouvez exécuter les deux cmdlets suivantes dans Exchange Online PowerShell pour obtenir le GUID des mises en place sur une boîte aux lettres. Une fois que vous avez obtenu un GUID, vous l’utilisez pour identifier le hold spécifique à l’étape 2. Une attente pour litige n’est pas identifiée par un GUID. Les en-cas de litige sont activés ou désactivés pour une boîte aux lettres.

- **Get-Mailbox :** Cette cmdlet permet de déterminer si la conservation pour litige est activée pour une boîte aux lettres et d’obtenir les GUID pour les conservations eDiscovery, les conservations In-Place et les stratégies de rétention Microsoft 365 spécifiquement affectées à une boîte aux lettres. Le résultat de cette cmdlet indique également si une boîte aux lettres a été explicitement exclue d’une stratégie de rétention à l’échelle de l’organisation.

- **Get-OrganizationConfig :** Utilisez cette cmdlet pour obtenir les GUID des stratégies de rétention à l’échelle de l’organisation.

Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Exécutez la commande suivante pour obtenir des informations sur les conservations et les stratégies de rétention Microsoft 365 appliquées à une boîte aux lettres.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> S’il y a trop de valeurs dans la propriété InPlaceHolds et qu’elles ne sont pas toutes affichées, vous pouvez exécuter la commande pour afficher chaque GUID sur une `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` ligne distincte.

Le tableau suivant décrit comment identifier différents types de boîtes aux lettres en fonction des valeurs de la propriété *InPlaceHolds* lorsque vous exécutez la cmdlet **Get-Mailbox.**


|Type de conservation  |Exemple de valeur  |Comment identifier le hold  |
|---------|---------|---------|
|Conservation pour litige     |    `True`     |     La mise en attente pour litige est activée pour une boîte aux lettres lorsque la *propriété LitigationHoldEnabled* est définie sur `True` .    |
|Hold eDiscovery     |  `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`       |   La *propriété InPlaceHolds* contient le GUID de toute mise en attente associée à un cas eDiscovery dans le centre de sécurité et conformité. Vous pouvez savoir qu’il s’agit d’une attente eDiscovery, car le GUID commence par le `UniH` préfixe (qui désigne une attente unifiée).      |
|Blocage local     |     `c0ba3ce811b6432a8751430937152491` <br/> ou <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`  |     La *propriété InPlaceHolds* contient le GUID de la In-Place qui est placée sur la boîte aux lettres. Vous pouvez savoir qu’il s’agit d’une In-Place car le GUID ne commence pas par un préfixe ou par `cld` le préfixe.     |
|Stratégie de rétention Microsoft 365 spécifiquement appliquée à la boîte aux lettres     |    `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> ou <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3`     |     La propriété InPlaceHolds contient les GUID de toute stratégie de rétention d’emplacement spécifique appliquée à la boîte aux lettres. Vous pouvez identifier les stratégies de rétention, car le GUID commence par `mbx` le `skp` préfixe ou le préfixe. Le préfixe indique que la stratégie de rétention est appliquée aux conversations Skype Entreprise dans la `skp` boîte aux lettres de l’utilisateur.    |
|Exclu d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation     |   `-mbxe9b52bf7ab3b46a286308ecb29624696`      |     Si une boîte aux lettres est exclue d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation, le GUID de la stratégie de rétention dont la boîte aux lettres est exclue s’affiche dans la propriété InPlaceHolds et est identifié par le `-mbx` préfixe.    |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Si la propriété *InPlaceHolds* est vide lorsque vous exécutez la cmdlet **Get-Mailbox,** il se peut qu’une ou plusieurs stratégies de rétention Microsoft 365 à l’échelle de l’organisation soient appliquées à la boîte aux lettres. Exécutez la commande suivante dans Exchange Online PowerShell pour obtenir la liste des GUID pour les stratégies de rétention Microsoft 365 à l’échelle de l’organisation.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> S’il y a trop de valeurs dans la propriété InPlaceHolds et qu’elles ne sont pas toutes affichées, vous pouvez exécuter la commande pour afficher chaque GUID sur une `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` ligne distincte.

Le tableau suivant décrit les différents types de retenues à l’échelle de l’organisation et indique comment identifier chaque type en fonction des GUID contenus dans la propriété *InPlaceHolds* lorsque vous exécutez la cmdlet **Get-OrganizationConfig.**


|Type de conservation  |Exemple de valeur  |Description  |
|---------|---------|---------|
|Stratégies de rétention Microsoft 365 appliquées aux boîtes aux lettres Exchange, aux dossiers publics Exchange et aux conversations Teams    |      `mbx7cfb30345d454ac0a989ab3041051209:2`   |   Les stratégies de rétention à l’échelle de l’organisation appliquées aux boîtes aux lettres Exchange, aux dossiers publics Exchange et aux conversations 1xN dans Microsoft Teams sont identifiées par des GUID qui commencent par le `mbx` préfixe. Remarque : les conversations 1xN sont stockées dans la boîte aux lettres des participants individuels.      |
|Stratégie de rétention Microsoft 365 appliquée aux groupes Microsoft 365 et aux messages de canal Teams     |   `grp1a0a132ee8944501a4bb6a452ec31171:3`      |    Les stratégies de rétention à l’échelle de l’organisation appliquées aux groupes et messages de canal Microsoft 365 dans Microsoft Teams sont identifiées par des GUID qui commencent par `grp` le préfixe. Notez que les messages de canal sont stockés dans la boîte aux lettres de groupe associée à Microsoft Team.     |

Pour plus d’informations sur les stratégies de rétention appliquées à Microsoft Teams, voir En savoir plus sur les stratégies de [rétention pour Microsoft Teams.](retention-policies-teams.md)

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Présentation du format de la valeur InPlaceHolds pour les stratégies de rétention

Outre le préfixe (mbx, skp ou grp) qui identifie un élément de la propriété InPlaceHolds en tant que stratégie de rétention Microsoft 365, la valeur contient également un suffixe qui identifie le type d’action de rétention configuré pour la stratégie. Par exemple, le suffixe d’action est mis en surbrillant en gras dans les exemples suivants :

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

Le tableau suivant définit les trois actions de rétention possibles :

|Valeur  |Description  |
|---------|---------|
|**1**     | Indique que la stratégie de rétention est configurée pour supprimer des éléments. La stratégie ne conserve pas les éléments.        |
|**2**    |    Indique que la stratégie de rétention est configurée pour contenir des éléments. La stratégie ne supprime pas les éléments à l’expiration de la période de rétention.     |
|**3**     |   Indique que la stratégie de rétention est configurée pour conserver les éléments, puis les supprimer après l’expiration de la période de rétention.      |

Pour plus d’informations sur les actions de rétention, voir la section Conservation du contenu pour une [période spécifique.](create-retention-policies.md#retaining-content-for-a-specific-period-of-time)
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Étape 2 : Utiliser le GUID pour identifier le hold

Une fois que vous avez obtenu le GUID d’une attente appliquée à une boîte aux lettres, l’étape suivante consiste à utiliser ce GUID pour identifier la boîte aux lettres. Les sections suivantes montrent comment identifier le nom de la attente (et d’autres informations) à l’aide du GUID de la attente.

### <a name="ediscovery-holds"></a>Conservations eDiscovery

Exécutez les commandes suivantes dans le Centre de sécurité & conformité PowerShell pour identifier une mise en attente eDiscovery appliquée à la boîte aux lettres. Utilisez le GUID (sans le préfixe UniH) pour le hold eDiscovery que vous avez identifié à l’étape 1. La première commande crée une variable qui contient des informations sur la attente. Cette variable est utilisée dans les autres commandes. La deuxième commande affiche le nom du cas eDiscovery à qui la hold est associée. La troisième commande affiche le nom de la boîte aux lettres et une liste des boîtes aux lettres à qui la boîte aux lettres s’applique.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

Pour vous connecter au Centre de sécurité & conformité PowerShell, voir Se connecter au Centre de sécurité [& conformité PowerShell.](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)

### <a name="in-place-holds"></a>Archives permanentes

Exécutez la commande suivante dans Exchange Online PowerShell pour identifier le In-Place qui est appliqué à la boîte aux lettres. Utilisez le GUID de la In-Place d’attente que vous avez identifiée à l’étape 1. La commande affiche le nom de la boîte aux lettres et une liste des boîtes aux lettres à qui la boîte aux lettres s’applique.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Si le GUID de la In-Place d’attente commence par le préfixe, veillez à inclure le préfixe lors de l’exécution `cld` de la commande précédente.

> [!IMPORTANT]
> À mesure que nous continuons d’investir de différentes manières pour conserver le contenu des boîtes aux lettres, nous andélisons le retrait des conservations In-Place dans le Centre d’administration Exchange (EAC). À compter du 1er juillet 2020, vous ne pourrez plus créer de In-Place en cours d’accès dans Exchange Online. Toutefois, vous pourrez toujours gérer les In-Place dans le EAC ou à l’aide de la cmdlet **Set-MailboxSearch** dans Exchange Online PowerShell. Toutefois, à compter du 1er octobre 2020, vous ne pourrez plus gérer les In-Place' Vous ne les supprimerez que dans le EAC ou à l’aide de la cmdlet **Remove-MailboxSearch.** Pour plus d’informations sur le retrait des In-Place, voir [Retrait des outils eDiscovery hérités.](legacy-ediscovery-retirement.md)

### <a name="microsoft-365-retention-policies"></a>Stratégies de rétention Microsoft 365

Exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell pour identifier la stratégie de rétention Microsoft 365 (à l’échelle de l’organisation ou un emplacement spécifique) appliquée à la boîte aux lettres. Utilisez le GUID (sans inclure le préfixe mbx, skp ou grp ou le suffixe d’action) que vous avez identifié à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identification des boîtes aux lettres en conservation car une étiquette de rétention a été appliquée à un dossier ou à un élément

Chaque fois qu’un utilisateur applique une étiquette de rétention configurée pour conserver du contenu ou conserver, puis supprimer du contenu dans un dossier ou un élément de sa boîte aux lettres, la propriété de boîte aux lettres *ComplianceTagHoldApplied* est définie sur **True**. Dans ce cas, la boîte aux lettres est considérée comme placée en conservation pour litige ou affectée à une stratégie de rétention Microsoft 365. Lorsque la *propriété ComplianceTagHoldApplied* est définie sur **True,** les choses suivantes peuvent se produire :

- Si la boîte aux lettres ou le compte d’utilisateur de l’utilisateur est supprimé, la boîte aux lettres devient [une boîte aux lettres inactive.](inactive-mailboxes-in-office-365.md)
- Vous ne pouvez pas désactiver la boîte aux lettres (la boîte aux lettres principale ou la boîte aux lettres d’archivage, si elle est activée).
- Les éléments de la boîte aux lettres peuvent être conservés plus longtemps que prévu. Cela est dû au fait que la boîte aux lettres est en attente et qu’aucun objet n’est supprimé définitivement (purgé).

Pour afficher la valeur de la *propriété ComplianceTagHoldApplied,* exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Pour plus d’informations sur les étiquettes de rétention, voir [étiquettes de rétention.](retention.md#retention-labels)

## <a name="managing-mailboxes-on-delay-hold"></a>Gestion des boîtes aux lettres en attente de retard

Une fois qu’un type de boîte aux lettres a été supprimé d’une boîte aux lettres, un *délai d’attente* est appliqué. Cela signifie que la suppression réelle de la boîte aux lettres est retardée de 30 jours pour empêcher la suppression définitive (purgée) des données de la boîte aux lettres. Cela permet aux administrateurs de rechercher ou de récupérer des éléments de boîte aux lettres qui seront purgés après la suppression d’une attente. Une mise en attente différée est placée sur une boîte aux lettres la prochaine fois que l’Assistant Dossier géré traite la boîte aux lettres et détecte qu’une mise en attente a été supprimée. Plus précisément, un délai d’attente est appliqué à une boîte aux lettres lorsque l’Assistant Dossier géré définit l’une des propriétés de boîte aux lettres suivantes sur **True**:

- **DelayHoldApplied :** Cette propriété s’applique au contenu de messagerie électronique (généré par des personnes utilisant Outlook et Outlook sur le web) stocké dans la boîte aux lettres d’un utilisateur.

- **DelayReleaseHoldApplied :** Cette propriété s’applique au contenu en nuage (généré par des applications non Outlook telles que Microsoft Teams, Microsoft Forms et Microsoft Yammer) stocké dans la boîte aux lettres d’un utilisateur. Les données cloud générées par une application Microsoft sont généralement stockées dans un dossier masqué dans la boîte aux lettres d’un utilisateur.
 
 Lorsqu’une mise en attente différée est placée sur la boîte aux lettres (lorsque l’une des propriétés précédentes est définie sur **True),** la boîte aux lettres est toujours considérée comme étant en attente pour une durée illimitée, comme si la boîte aux lettres était en attente pour litige. Au bout de 30 jours, le délai d’attente expire et Microsoft 365 tente automatiquement de supprimer le délai d’attente (en fixant la propriété DelayHoldApplied ou DelayReleaseHoldApplied sur **False)** afin que la mise en attente soit supprimée. Une fois que l’une de ces propriétés a la valeur **False,** les éléments correspondants marqués pour suppression sont purgés la prochaine fois que la boîte aux lettres est traitée par l’Assistant Dossier géré.

Pour afficher les valeurs des propriétés DelayHoldApplied et DelayReleaseHoldApplied d’une boîte aux lettres, exécutez la commande suivante dans Exchange Online PowerShell.

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Pour supprimer le délai d’attente avant son expiration, vous pouvez exécuter l’une des commandes suivantes (ou les deux) dans Exchange Online PowerShell, en fonction de la propriété que vous souhaitez modifier : 
 
```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Ou
 
```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Le rôle De mise en attente légale doit vous être attribué dans Exchange Online pour utiliser les paramètres *RemoveDelayHoldApplied* ou *RemoveDelayReleaseHoldApplied.* 

Pour supprimer le délai d’attente sur une boîte aux lettres inactive, exécutez l’une des commandes suivantes dans Exchange Online PowerShell :

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Ou

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> La meilleure façon de spécifier une boîte aux lettres inactive dans la commande précédente consiste à utiliser son nom distinguished name ou sa valeur GUID Exchange. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres. 

Pour plus d’informations sur l’utilisation de ces paramètres pour la gestion des délais d’attente, voir [Set-Mailbox](https://docs.microsoft.com/powershell/module/exchange/set-mailbox).

Gardez les points suivants à l’esprit lors de la gestion d’une boîte aux lettres en attente de retard :

- Si la propriété DelayHoldApplied ou DelayReleaseHoldApplied est définie sur **True** et qu’une boîte aux lettres (ou le compte d’utilisateur correspondant) est supprimée, la boîte aux lettres devient une boîte aux lettres inactive. Cela est dû au fait qu’une boîte aux lettres est considérée comme étant en attente si l’une des propriétés est définie sur **True** et que la suppression d’une boîte aux lettres en attente entraîne une boîte aux lettres inactive. Pour supprimer une boîte aux lettres et ne pas en faire une boîte aux lettres inactive, vous devez définir les deux propriétés sur **False**.

- Comme indiqué précédemment, une boîte aux lettres est considérée comme étant en attente pour une durée illimitée si la propriété DelayHoldApplied ou DelayReleaseHoldApplied est définie sur **True**. Toutefois, cela ne signifie pas *que* tout le contenu de la boîte aux lettres est conservé. Cela dépend de la valeur définie pour chaque propriété. Par exemple, supposons que les deux propriétés sont définies sur **True,** car les conserves sont supprimées de la boîte aux lettres. Ensuite, vous supprimez uniquement le délai d’attente appliqué aux données cloud non Outlook (à l’aide du paramètre *RemoveDelayReleaseHoldApplied).* Lors du prochain traitement de la boîte aux lettres par l’Assistant Dossier géré, les éléments non Outlook marqués pour suppression sont purgés. Tous les éléments Outlook marqués pour suppression ne seront pas purgés, car la propriété DelayHoldApplied est toujours définie sur **True**. L’inverse serait également vrai : si DelayHoldApplied est définie sur **False** et DelayReleaseHoldApplied est définie sur **True**, seuls les éléments Outlook marqués pour suppression seront purgés.

## <a name="next-steps"></a>Étapes suivantes

Après avoir identifié les conservations appliquées à une boîte aux lettres, vous pouvez effectuer des tâches telles que la modification de la durée de la conservation, la suppression temporaire ou définitive de la conservation ou l’exclusion d’une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365. Pour plus d’informations sur les tâches liées aux maintiens en cours, consultez l’une des rubriques suivantes :

- Exécutez la commande [Set-RetentionCompliancePolicy \<Policy Name> -Identity -AddExchangeLocationException \<user mailbox> ](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancepolicy) dans le Centre de sécurité & conformité PowerShell pour exclure une boîte aux lettres d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation. Cette commande ne peut être utilisée que pour les stratégies de rétention dont la valeur de la *propriété ExchangeLocation* est égale `All` à .

- Exécutez la commande [Set-Mailbox -ExcludeFromOrgHolds \<hold GUID without prefix or suffix> ](https://docs.microsoft.com/powershell/module/exchange/set-mailbox) dans Exchange Online PowerShell pour exclure une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation.

- [Modifier la durée de conservation pour une boîte aux lettres inactive](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md)

- [Supprimer des éléments en attente dans le dossier Éléments récupérables des boîtes aux lettres basées sur le cloud](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
