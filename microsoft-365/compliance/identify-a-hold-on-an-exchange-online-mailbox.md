---
title: Comment identifier la conservation d’une boîte aux lettres Exchange Online
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Découvrez comment identifier les différents types de conservation qui peuvent être placés sur une boîte aux lettres Exchange Online dans Microsoft 365.
ms.openlocfilehash: 9c18d2bc99fae93ae3b288475661872e5e6d49d9
ms.sourcegitcommit: 433f5b448a0149fcf462996bc5c9b45d17bd46c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67822702"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online

Cet article explique comment identifier les conservations placées sur Exchange Online boîtes aux lettres dans Microsoft 365.

Microsoft 365 offre plusieurs façons pour votre organisation d’empêcher la suppression définitive du contenu de boîte aux lettres. Cela permet à votre organisation de conserver le contenu pour répondre aux réglementations de conformité ou lors d’enquêtes légales et autres. Voici une liste des fonctionnalités de rétention (également appelées *conservations*) dans Office 365 :

- **[Conservation des litiges](create-a-litigation-hold.md) :** Conservations appliquées aux boîtes aux lettres utilisateur dans Exchange Online.

- **[Conservation eDiscovery](create-ediscovery-holds.md) :** Conservations associées à un cas Microsoft Purview eDiscovery (Standard) dans le centre de sécurité et de conformité. Les conservations eDiscovery peuvent être appliquées aux boîtes aux lettres utilisateur et à la boîte aux lettres correspondante pour Groupes Microsoft 365 et Microsoft Teams.

- **[Conservation sur place](/Exchange/security-and-compliance/create-or-remove-in-place-holds) :** conservation appliquée aux boîtes aux lettres utilisateur à l’aide de l’outil In-Place eDiscovery & Hold dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> dans Exchange Online. 

   > [!NOTE]
   > In-Place les conservations ont été mises hors service et vous ne pouvez plus créer In-Place conservations ou les appliquer aux boîtes aux lettres. Toutefois, In-Place les conservations peuvent toujours être appliquées aux boîtes aux lettres de votre organisation, c’est pourquoi elles sont incluses dans cet article. Pour plus d’informations, consultez [Retrait des outils eDiscovery hérités](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Stratégies de rétention Microsoft 365](retention.md) :** Peut être configuré pour conserver (ou conserver, puis supprimer) du contenu dans les boîtes aux lettres des utilisateurs dans Exchange Online et dans la boîte aux lettres correspondante pour Groupes Microsoft 365 et Microsoft Teams. Vous pouvez également créer une stratégie de rétention pour conserver Skype Entreprise conversations, qui sont stockées dans des boîtes aux lettres utilisateur.

  Il existe deux types de stratégies de rétention Microsoft 365 qui peuvent être affectées aux boîtes aux lettres.

    - **Stratégies de rétention d’emplacement spécifiques :** Il s’agit de stratégies qui sont affectées aux emplacements de contenu de certains utilisateurs. Vous utilisez l’applet **de commande Get-Mailbox** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention affectées à des boîtes aux lettres spécifiques. Pour plus d’informations sur ce type de stratégie de rétention, consultez la section [A avec des inclusions ou exclusions spécifiques](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) de la documentation de la stratégie de rétention.

    - **Stratégies de rétention à l’échelle de l’organisation :** Il s’agit de stratégies qui sont affectées à tous les emplacements de contenu de votre organisation. Vous utilisez l’applet de commande **Get-OrganizationConfig** dans Exchange Online PowerShell pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation. Pour plus d’informations sur ce type de stratégie de rétention, consultez la section [A qui s’applique à des emplacements entiers](retention-settings.md#a-policy-that-applies-to-entire-locations) à partir de la documentation de la stratégie de rétention.

- **[Étiquettes de rétention Microsoft 365](retention.md) :** si un utilisateur applique une étiquette de rétention Microsoft 365 (configurée pour conserver du contenu ou conserver, puis supprimer du contenu) à *un* dossier ou un élément de sa boîte aux lettres, une conservation est placée sur la boîte aux lettres comme si la boîte aux lettres était mise en attente pour litige ou affectée à une stratégie de rétention Microsoft 365. Pour plus d’informations, consultez la section [Identifier les boîtes aux lettres en attente, car une étiquette de rétention a été appliquée à un dossier ou à une section d’élément](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) dans cet article.

Pour gérer les boîtes aux lettres en attente, vous devrez peut-être identifier le type de conservation placé sur une boîte aux lettres afin de pouvoir effectuer des tâches telles que la modification de la durée de conservation, la suppression temporaire ou définitive de la conservation ou l’exclusion d’une boîte aux lettres d’une stratégie de rétention Microsoft 365. Dans ces cas, la première étape consiste à identifier le type de conservation placé sur la boîte aux lettres. Étant donné que plusieurs conservations (et différents types de conservations) peuvent être placées sur une seule boîte aux lettres, vous devez identifier toutes les conservations placées sur une boîte aux lettres si vous souhaitez supprimer ou modifier une conservation.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>Étape 1 : Obtenir le GUID pour les conservations placées sur une boîte aux lettres

Vous pouvez exécuter les deux applets de commande suivantes dans Exchange Online PowerShell pour obtenir le GUID des conservations placées sur une boîte aux lettres. Une fois que vous avez obtenu un GUID, vous l’utilisez pour identifier la conservation spécifique à l’étape 2. Un blocage de litige n’est pas identifié par un GUID. Les conservations de litige sont activées ou désactivées pour une boîte aux lettres.

- **Get-Mailbox :** Utilisez cette applet de commande pour déterminer si la conservation des litiges est activée pour une boîte aux lettres et obtenir les GUID pour les conservations eDiscovery, les conservations In-Place et les stratégies de rétention Microsoft 365 qui sont spécifiquement affectées à une boîte aux lettres. La sortie de cette applet de commande indique également si une boîte aux lettres a été explicitement exclue d’une stratégie de rétention à l’échelle de l’organisation.

- **Get-OrganizationConfig :** Utilisez cette applet de commande pour obtenir les GUID des stratégies de rétention à l’échelle de l’organisation.

Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Exécutez la commande suivante pour obtenir des informations sur les conservations et les stratégies de rétention Microsoft 365 appliquées à une boîte aux lettres.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> S’il y a trop de valeurs dans la propriété InPlaceHolds et que toutes ne sont pas affichées, vous pouvez exécuter la `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` commande pour afficher chaque GUID sur une ligne distincte.

Le tableau suivant explique comment identifier différents types de conservations en fonction des valeurs de la propriété *InPlaceHolds* lorsque vous exécutez l’applet **de commande Get-Mailbox** .

| Type de conservation                                                          | Exemple de valeur                                                                                  | Comment identifier la conservation                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Conservation pour litige                                                    | `True`                                                                                         | La conservation du litige est activée pour une boîte aux lettres lorsque la propriété *LitigationHoldEnabled* est définie `True`sur .                                                                                                                                                                                                                                         |
| Mise en suspens d’eDiscovery                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | La *propriété InPlaceHolds* contient le GUID de toute conservation associée à un cas eDiscovery dans le centre de sécurité et de conformité. Vous pouvez dire qu’il s’agit d’une conservation eDiscovery, car le GUID commence par le `UniH` préfixe (qui désigne une conservation unifiée).                                                                                   |
| Blocage local                                                      | `c0ba3ce811b6432a8751430937152491` <br/> ou <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | La propriété *InPlaceHolds* contient le GUID du In-Place Hold placé sur la boîte aux lettres. Vous pouvez indiquer qu’il s’agit d’une In-Place En attente, car le GUID ne commence pas par un préfixe ou commence par le `cld` préfixe.                                                                                                               |
| Stratégie de rétention Microsoft 365 spécifiquement appliquée à la boîte aux lettres | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> ou <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | La propriété InPlaceHolds contient les GUID de toute stratégie de rétention d’emplacement spécifique appliquée à la boîte aux lettres. Vous pouvez identifier les stratégies de rétention, car le GUID commence par le préfixe ou le `mbx` `skp` préfixe. Le `skp` préfixe indique que la stratégie de rétention est appliquée à Skype Entreprise conversations dans la boîte aux lettres de l’utilisateur. |
| Exclu d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Si une boîte aux lettres est exclue d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation, le GUID de la stratégie de rétention dont la boîte aux lettres est exclue est affiché dans la propriété InPlaceHolds et est identifié par le `-mbx` préfixe.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
Si la propriété *InPlaceHolds* est vide lorsque vous exécutez l’applet de commande **Get-Mailbox** , une ou plusieurs stratégies de rétention Microsoft 365 à l’échelle de l’organisation peuvent toujours être appliquées à la boîte aux lettres. Exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour obtenir la liste des GUID pour les stratégies de rétention Microsoft 365 à l’échelle de l’organisation.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> S’il y a trop de valeurs dans la propriété InPlaceHolds et que toutes ne sont pas affichées, vous pouvez exécuter la `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` commande pour afficher chaque GUID sur une ligne distincte.

Le tableau suivant décrit les différents types de conservations à l’échelle de l’organisation et comment identifier chaque type en fonction des GUID contenus dans la propriété *InPlaceHolds* lorsque vous **exécutez l’applet de commande Get-OrganizationConfig** .

| Type de conservation                                                                                                | Exemple de valeur                           | Description                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Stratégies de rétention Microsoft 365 appliquées aux boîtes aux lettres Exchange, aux dossiers publics Exchange et aux conversations Teams | `mbx7cfb30345d454ac0a989ab3041051209:2` | Les stratégies de rétention à l’échelle de l’organisation appliquées aux boîtes aux lettres Exchange, aux dossiers publics Exchange et aux conversations 1xN dans Microsoft Teams sont identifiées par les GUID qui commencent par le `mbx` préfixe. Notez que les conversations 1xN sont stockées dans la boîte aux lettres des participants individuels à la conversation.  |
| Stratégie de rétention Microsoft 365 appliquée aux messages de canal Groupes Microsoft 365 et Teams                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Les stratégies de rétention à l’échelle de l’organisation appliquées aux groupes Microsoft 365 et aux messages de canal dans Microsoft Teams sont identifiées par les GUID qui commencent par le `grp` préfixe. Les messages de canal de note sont stockés dans la boîte aux lettres de groupe associée à une équipe Microsoft. |

Pour plus d’informations sur les stratégies de rétention appliquées à Microsoft Teams, consultez [En savoir plus sur les stratégies de rétention pour Microsoft Teams](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Présentation du format de la valeur InPlaceHolds pour les stratégies de rétention

Outre le préfixe (mbx, skp ou grp) qui identifie un élément de la propriété InPlaceHolds en tant que stratégie de rétention Microsoft 365, la valeur contient également un suffixe qui identifie le type d’action de rétention configuré pour la stratégie. Par exemple, le suffixe d’action est mis en surbrillance en gras dans les exemples suivants :

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

Le tableau suivant définit les trois actions de rétention possibles :

| Valeur | Description                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Indique que la stratégie de rétention est configurée pour supprimer des éléments. La stratégie ne conserve pas les éléments.                                  |
| **2** | Indique que la stratégie de rétention est configurée pour contenir des éléments. La stratégie ne supprime pas les éléments après l’expiration de la période de rétention. |
| **3** | Indique que la stratégie de rétention est configurée pour contenir les éléments, puis les supprimer après l’expiration de la période de rétention.             |

Pour plus d’informations sur les actions de rétention, consultez la section [Conservation du contenu pour une période spécifique](retention-settings.md#retaining-content-for-a-specific-period-of-time) .
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>Étape 2 : Utiliser le GUID pour identifier la conservation

Une fois que vous avez obtenu le GUID d’une conservation appliquée à une boîte aux lettres, l’étape suivante consiste à utiliser ce GUID pour identifier la conservation. Les sections suivantes montrent comment identifier le nom de la conservation (et d’autres informations) à l’aide du GUID de conservation.

### <a name="ediscovery-holds"></a>Conservations eDiscovery

Exécutez les commandes suivantes dans Security & Compliance PowerShell pour identifier une conservation eDiscovery appliquée à la boîte aux lettres. Utilisez le GUID (sans inclure le préfixe UniH) pour la conservation eDiscovery que vous avez identifiée à l’étape 1. 

Pour vous connecter à Security & Compliance PowerShell, consultez [Connect to Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

La première commande crée une variable qui contient des informations sur la conservation. Cette variable est utilisée dans les autres commandes. La deuxième commande affiche le nom de la casse eDiscovery à qui la conservation est associée. La troisième commande affiche le nom de la conservation et une liste des boîtes aux lettres aux qui s’appliquent.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>Archives permanentes

Exécutez la commande suivante dans Exchange Online PowerShell pour identifier le In-Place Hold appliqué à la boîte aux lettres. Utilisez le GUID du In-Place Hold que vous avez identifié à l’étape 1. La commande affiche le nom de la conservation et une liste des boîtes aux lettres aux qui s’appliquent à la conservation.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Si le GUID du In-Place Hold commence par le `cld` préfixe, veillez à inclure le préfixe lors de l’exécution de la commande précédente.

> [!IMPORTANT]
> Alors que nous continuons d’investir de différentes façons pour préserver le contenu de la boîte aux lettres, nous annoncions le retrait de In-Place Conservations dans le Centre d’administration Exchange (EAC). À compter du 1er juillet 2020, vous ne pourrez pas créer de In-Place Conservations dans Exchange Online. Toutefois, vous pourrez toujours gérer In-Place conservations dans le CAE ou à l’aide de l’applet de commande **Set-MailboxSearch** dans Exchange Online PowerShell. Toutefois, à compter du 1er octobre 2020, vous ne pourrez pas gérer In-Place conservations. Vous ne les supprimerez que dans le CAE ou à l’aide de l’applet de commande **Remove-MailboxSearch** . Pour plus d’informations sur la mise hors service de In-Place Conservations, consultez [La mise hors service des outils eDiscovery hérités](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Stratégies de rétention Microsoft 365

[Connectez-vous à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante pour identifier la stratégie de rétention Microsoft 365 (emplacement spécifique ou à l’échelle de l’organisation) appliquée à la boîte aux lettres. Utilisez le GUID (sans inclure le préfixe mbx, skp ou grp ou le suffixe d’action) que vous avez identifié à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Identification des boîtes aux lettres en attente, car une étiquette de rétention a été appliquée à un dossier ou un élément

Chaque fois qu’un utilisateur applique une étiquette de rétention configurée pour *conserver* ou *conserver, puis supprimer* du contenu dans un dossier ou un élément de sa boîte aux lettres, la propriété de boîte aux lettres *ComplianceTagHoldApplied* est définie sur **True**. Dans ce cas, la boîte aux lettres est traitée de la même façon que si elle a été mise en attente, par exemple lorsqu’elle est affectée à une stratégie de rétention Microsoft 365 ou mise en attente du contentieux, mais avec certaines mises en garde. Lorsque la propriété *ComplianceTagHoldApplied* a la valeur **True**, les éléments suivants se produisent :

- Si la boîte aux lettres ou le compte Microsoft 365 de l’utilisateur est supprimé, la boîte aux lettres devient une [boîte aux lettres inactive](inactive-mailboxes-in-office-365.md).
- Vous ne pouvez pas désactiver la boîte aux lettres (la boîte aux lettres principale ou la boîte aux lettres d’archive, si elle est activée).
- Les éléments qui ont été supprimés de la boîte aux lettres suivent l’un des deux chemins d’accès selon qu’ils sont étiquetés ou non :
    - **Les éléments sans étiquette** suivent le même chemin d’accès que celui suivi par les éléments supprimés lorsqu’aucune conservation ne s’applique à la boîte aux lettres.  Le temps nécessaire à la suppression définitive de ces éléments est déterminé par la configuration de rétention des [éléments supprimés](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) et par l’activation ou non de la [récupération d’élément unique](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) pour la boîte aux lettres.
    - **Les éléments étiquetés** seront conservés dans le [dossier d’éléments récupérables](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) de la même façon que si une stratégie de rétention Microsoft 365 était appliquée, mais au niveau de chaque élément.  Si plusieurs éléments ont des étiquettes différentes configurées pour *conserver* ou *conserver, puis supprimer* du contenu à des intervalles différents, chaque élément est conservé en fonction de la configuration de l’étiquette appliquée.
- D’autres conservations, telles que les stratégies de rétention Microsoft 365, les conservations eDiscovery ou les conservations en litige, peuvent prolonger la durée pendant laquelle les éléments étiquetés sont conservés en fonction [des principes de rétention](retention.md#the-principles-of-retention-or-what-takes-precedence).

Pour afficher la valeur de la propriété *ComplianceTagHoldApplied* pour une seule boîte aux lettres, exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Pour plus d’informations sur les étiquettes de rétention, consultez [les étiquettes de rétention](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Gestion des boîtes aux lettres en attente de délai

Une fois que n’importe quel type de conservation est supprimé d’une boîte aux lettres, une *conservation différée* est appliquée. Cela signifie que la suppression réelle de la conservation est retardée de 30 jours pour empêcher la suppression définitive des données (purgées) de la boîte aux lettres. Cela donne aux administrateurs la possibilité de rechercher ou de récupérer des éléments de boîte aux lettres qui seront purgés après la suppression d’une conservation. Une conservation différée est placée sur une boîte aux lettres la prochaine fois que l’Assistant Dossier géré traite la boîte aux lettres et détecte qu’une conservation a été supprimée. Plus précisément, une conservation différée est appliquée à une boîte aux lettres lorsque l’Assistant Dossier géré définit l’une des propriétés de boîte aux lettres suivantes sur **True** :

- **DelayHoldApplied :** Cette propriété s’applique au contenu lié à l’e-mail (généré par des personnes utilisant Outlook et Outlook sur le web) stocké dans la boîte aux lettres d’un utilisateur.

- **DelayReleaseHoldApplied :** Cette propriété s’applique au contenu cloud (généré par des applications non Outlook telles que Microsoft Teams, Microsoft Forms et Microsoft Yammer) stocké dans la boîte aux lettres d’un utilisateur. Les données cloud générées par une application Microsoft sont généralement stockées dans un dossier masqué dans la boîte aux lettres d’un utilisateur.

Lorsqu’une conservation différée est placée sur la boîte aux lettres (lorsque l’une des propriétés précédentes est définie sur **True**), la boîte aux lettres est toujours considérée comme étant en attente pendant une durée de conservation illimitée, comme si la boîte aux lettres était en attente de litige. Au bout de 30 jours, le délai d’attente expire et Microsoft 365 tente automatiquement de supprimer la conservation différée (en définissant la propriété DelayHoldApplied ou DelayReleaseHoldApplied sur **False**) afin que la conservation soit supprimée. Une fois l’une de ces propriétés définie sur **False**, les éléments correspondants marqués pour suppression sont supprimés lors du prochain traitement de la boîte aux lettres par l’Assistant Dossier géré.

Pour afficher les valeurs des propriétés DelayHoldApplied et DelayReleaseHoldApplied d’une boîte aux lettres, exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Pour supprimer le délai d’attente avant son expiration, vous pouvez exécuter une (ou les deux) commandes suivantes dans Exchange Online PowerShell, en fonction de la propriété à modifier :

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Ou

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Le rôle De suspension légale doit vous être attribué dans Exchange Online pour utiliser les paramètres *RemoveDelayHoldApplied* ou *RemoveDelayReleaseHoldApplied*. 

Pour supprimer le délai d’attente sur une boîte aux lettres inactive, exécutez l’une des commandes suivantes dans Exchange Online PowerShell :

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Ou

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> La meilleure façon de spécifier une boîte aux lettres inactive dans la commande précédente consiste à utiliser son nom unique ou sa valeur DE GUID Exchange. L'une de ces valeurs permet d'empêcher de spécifier par inadvertance la mauvaise boîte aux lettres. 

Pour plus d’informations sur l’utilisation de ces paramètres pour la gestion des conservations de délai, consultez [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Gardez à l’esprit les éléments suivants lors de la gestion d’une boîte aux lettres en attente de délai :

- Si la propriété DelayHoldApplied ou DelayReleaseHoldApplied a la valeur **True** et qu’une boîte aux lettres (ou le compte d’utilisateur correspondant) est supprimée, la boîte aux lettres devient une boîte aux lettres inactive. Cela est dû au fait qu’une boîte aux lettres est considérée comme étant en attente si l’une des propriétés est définie sur **True**, et la suppression d’une boîte aux lettres en attente entraîne une boîte aux lettres inactive. Pour supprimer une boîte aux lettres et ne pas la rendre inactive, vous devez définir les deux propriétés sur **False**.

- Comme indiqué précédemment, une boîte aux lettres est considérée comme étant en attente pendant une durée de conservation illimitée si la propriété DelayHoldApplied ou DelayReleaseHoldApplied a la valeur **True**. Toutefois, cela ne signifie pas que *tout* le contenu de la boîte aux lettres est conservé. Cela dépend de la valeur définie pour chaque propriété. Par exemple, supposons que les deux propriétés sont définies sur **True** , car les conservations sont supprimées de la boîte aux lettres. Ensuite, vous supprimez uniquement la conservation différée appliquée aux données cloud non Outlook (à l’aide du paramètre *RemoveDelayReleaseHoldApplied* ). La prochaine fois que l’Assistant Dossier géré traite la boîte aux lettres, les éléments non Outlook marqués pour suppression sont purgés. Les éléments Outlook marqués pour suppression ne seront pas purgés, car la propriété DelayHoldApplied est toujours définie sur **True**. L’inverse serait également vrai : si DelayHoldApplied est défini sur **False** et DelayReleaseHoldApplied sur **True**, seuls les éléments Outlook marqués pour suppression sont supprimés.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Comment vérifier qu’une stratégie de rétention à l’échelle de l’organisation est appliquée à une boîte aux lettres

Lorsqu’une stratégie de rétention à l’échelle de l’organisation est appliquée ou supprimée dans une boîte aux lettres, l’exportation des journaux de diagnostic de boîte aux lettres peut vous aider à être certain que Exchange Online a réellement appliqué ou supprimé la stratégie de rétention dans la boîte aux lettres. Pour afficher ces informations, vous devez d’abord valider quelques éléments à l’aide [de Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Obtenir les GUID pour toutes les stratégies de rétention explicitement appliquées à une boîte aux lettres

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Obtenir les GUID pour toutes les stratégies de rétention à l’échelle de l’organisation appliquées aux boîtes aux lettres

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>Obtenir les diagnostics de boîte aux lettres pour HoldTracking

Les journaux de diagnostic de boîte aux lettres de suivi de la conservation conservent l’historique des conservations appliquées à une boîte aux lettres utilisateur.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Passer en revue les résultats des journaux de diagnostic de boîte aux lettres

Si vous collectez des données à l’étape précédente, les données obtenues peuvent ressembler à ceci :

> **Ed**`  : 0001-01-01T00:00:00.0000000`
>  **Caché**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **Ht**`  : 4`
>  **Lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **Osd**` : 2020-03-23T18:24:37.1884606Z`

Utilisez le tableau suivant pour vous aider à comprendre chacune des valeurs précédentes répertoriées dans le journal de diagnostic.

| Valeur   | Description |
|:------- |:----------- |
| **non**  | Indique la date de fin, qui est la date à laquelle la stratégie de rétention a été désactivée. MinValue signifie que la stratégie est toujours affectée à la boîte aux lettres. |
| **Caché** | Indique le GUID de la stratégie de rétention. Cette valeur est corrélée aux GUID que vous avez collectés pour les stratégies de rétention explicites ou à l’échelle de l’organisation affectées à la boîte aux lettres.|
| **Lsd** | Indique la date du dernier début, qui est la date à laquelle la stratégie de rétention a été affectée à la boîte aux lettres.|
| **Osd** | Indique la date de début d’origine, c’est-à-dire la date à laquelle Exchange a enregistré pour la première fois des informations sur la stratégie de rétention. |
|||

Lorsqu’une stratégie de rétention n’est plus appliquée à une boîte aux lettres, nous mettons un délai temporaire de suspension sur l’utilisateur pour empêcher le vidage du contenu. Une conservation différée peut être désactivée en exécutant la `Set-Mailbox -RemoveDelayHoldApplied` commande.

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez identifié les conservations appliquées à une boîte aux lettres, vous pouvez effectuer des tâches telles que la modification de la durée de la conservation, la suppression temporaire ou définitive de la conservation ou l’exclusion d’une boîte aux lettres inactive d’une stratégie de rétention Microsoft 365. Pour plus d’informations sur l’exécution de tâches liées aux conservations, consultez l’une des rubriques suivantes :

- Exécutez la commande [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) dans [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) pour exclure une boîte aux lettres d’une stratégie de rétention Microsoft 365 à l’échelle de l’organisation. Cette commande ne peut être utilisée que pour les stratégies de rétention où la valeur de la propriété *ExchangeLocation* est égale `All`.

- [Modifier la durée de conservation pour une boîte aux lettres inactive](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Supprimer une boîte aux lettres inactive](delete-an-inactive-mailbox.md)

- [Supprimer des éléments en attente dans le dossier Éléments récupérables des boîtes aux lettres basées sur le cloud](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
