---
title: Migrer les recherches et conservations eDiscovery héritées vers le portail de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: 3b80db06faea9c76c7df671468b94fc11f0c63df
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010085"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-compliance-portal"></a>Migrer les recherches et conservations eDiscovery héritées vers le portail de conformité

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Le portail de conformité Microsoft Purview offre une expérience améliorée pour l’utilisation d’eDiscovery, notamment : une fiabilité plus élevée, de meilleures performances et de nombreuses fonctionnalités adaptées aux flux de travail eDiscovery, notamment des cas d’organisation de votre contenu par matière, des ensembles de révision pour passer en revue le contenu et l’analytique afin d’éliminer les données à examiner, telles que le regroupement en quasi-double, le thread de messagerie, l’analyse des thèmes et le codage prédictif.

Pour aider les clients à tirer parti des fonctionnalités nouvelles et améliorées, cet article fournit des conseils de base sur la façon de migrer In-Place recherches eDiscovery et les conservations du <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> vers le portail de conformité.

> [!NOTE]
> Étant donné qu’il existe de nombreux scénarios différents, cet article fournit des conseils généraux sur la transition des recherches et les conservations vers un cas eDiscovery (Standard) dans le portail de conformité. L’utilisation de cas eDiscovery n’est pas toujours nécessaire, mais elle ajoute une couche de sécurité supplémentaire en vous permettant d’attribuer des autorisations pour contrôler qui a accès aux cas eDiscovery dans votre organisation.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez installer le module Exchange Online V2. Pour les instructions, consultez [Installer et gérer le module EXO v2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- Vous devez être membre du groupe de rôles eDiscovery Manager dans le portail de conformité pour exécuter les commandes PowerShell décrites dans cet article. Vous devez également être membre du groupe de rôles Gestion de la découverte dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>.

- Cet article fournit des conseils sur la création d’une conservation eDiscovery. La stratégie de conservation sera appliquée aux boîtes aux lettres via un processus asynchrone. Lors de la création d’une conservation eDiscovery, vous devez créer une CaseHoldPolicy et caseHoldRule, sinon la conservation ne sera pas créée et les emplacements de contenu ne seront pas mis en attente.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-powershell"></a>Étape 1 : Connecter pour Exchange Online PowerShell et la sécurité & conformité PowerShell

La première étape consiste à se connecter à Exchange Online PowerShell et à Security & Compliance PowerShell dans la même fenêtre PowerShell. Vous pouvez copier les commandes suivantes, les coller dans une fenêtre PowerShell, puis les exécuter. Vous serez invité à entrer des informations d’identification.

```powershell
Connect-IPPSSession
Connect-ExchangeOnline -UseRPSSession
```

Pour obtenir des instructions détaillées, consultez [Connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et [Connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>Étape 2 : Obtenir la liste des recherches In-Place eDiscovery à l’aide de Get-MailboxSearch

Une fois connecté, vous pouvez obtenir la liste des recherches In-Place eDiscovery en exécutant l’applet de commande **Get-MailboxSearch** . Copiez et collez la commande suivante dans la fenêtre PowerShell, puis exécutez-la.

```powershell
Get-MailboxSearch
```

Une liste de recherches est répertoriée avec leur nom et l’état de toute In-Place Conservations.

La sortie de l’applet de commande sera similaire à ce qui suit :

![Exemple PowerShell Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>Étape 3 : Obtenir des informations sur les recherches In-Place eDiscovery et les In-Place conservations que vous souhaitez migrer

Là encore, vous allez utiliser l’applet de commande **Get-MailboxSearch** , mais cette fois pour obtenir les propriétés de la recherche. Vous pouvez stocker ces propriétés dans une variable pour une utilisation ultérieure. L’exemple suivant stocke les résultats de l’applet de commande **Get-MailboxSearch** dans une variable, puis affiche les propriétés de la recherche.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | Format-List
```

La sortie de ces deux commandes sera similaire à ce qui suit :

![Exemple de sortie PowerShell de l’utilisation de Get-MailboxSearch pour une recherche individuelle.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> La durée de la conservation In-Place dans cet exemple est indéfinie (*ItemHoldPeriod : Illimité*). Cela est courant pour les scénarios d’eDiscovery et d’investigation juridique. Si la durée de conservation a une valeur différente de celle indéfinie, cela est probablement dû au fait que la conservation est utilisée pour conserver le contenu dans un scénario de rétention. Au lieu d’utiliser les applets de commande eDiscovery dans Security & Compliance PowerShell pour les scénarios de rétention, nous vous recommandons d’utiliser [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) et [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) pour conserver le contenu. Le résultat de l’utilisation de ces applets de commande sera similaire à l’utilisation de **New-CaseHoldPolicy** et **de New-CaseHoldRule**, mais vous pourrez spécifier une période de rétention et une action de rétention, comme la suppression de contenu après l’expiration de la période de rétention. En outre, l’utilisation des applets de commande de rétention ne vous oblige pas à associer les conservations de rétention à un cas eDiscovery.

## <a name="step-4-create-a-case-in-the-microsoft-purview-compliance-portal"></a>Étape 4 : Créer un cas dans le portail de conformité Microsoft Purview

Pour créer une conservation eDiscovery, vous devez créer un cas eDiscovery à associer à la conservation. L’exemple suivant crée un cas eDiscovery à l’aide d’un nom de votre choix. Nous stockerons les propriétés du nouveau cas dans une variable à utiliser ultérieurement. Vous pouvez afficher ces propriétés en exécutant la `$case | FL` commande après avoir créé le cas.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```

![Exemple d’exécution de la commande New-ComplianceCase.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>Étape 5 : Créer la conservation eDiscovery

Une fois le cas créé, vous pouvez créer la conservation et l’associer au cas que vous avez créé à l’étape précédente. Il est important de se rappeler que vous devez créer à la fois une stratégie de conservation des cas et une règle de conservation des cas. Si la règle de conservation de cas n’est pas créée après la création de la stratégie de conservation de cas, la conservation eDiscovery n’est pas créée et aucun contenu n’est mis en attente.

Exécutez les commandes suivantes pour recréer la conservation eDiscovery que vous souhaitez migrer. Ces exemples utilisent les propriétés de In-Place Hold de l’étape 3 que vous souhaitez migrer. La première commande crée une stratégie de conservation de cas et enregistre les propriétés dans une variable. La deuxième commande crée la règle de conservation de la casse correspondante.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![Exemple d’utilisation des applets de commande NewCaseHoldPolicy et NewCaseHoldRule.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>Étape 6 : Vérifier la conservation eDiscovery

Pour vous assurer qu’il n’y a aucun problème lors de la création de la conservation, il est bon de vérifier que l’état de distribution de la conservation est réussi. La distribution signifie que la conservation a été appliquée à tous les emplacements de contenu spécifiés dans le paramètre *ExchangeLocation* à l’étape précédente. Pour ce faire, vous pouvez exécuter l’applet **de commande Get-CaseHoldPolicy** . Étant donné que les propriétés enregistrées dans la *variable $policy* que vous avez créée à l’étape précédente ne sont pas automatiquement mises à jour dans la variable, vous devez réexécuter l’applet de commande pour vérifier que la distribution a réussi. La distribution des stratégies de conservation des cas peut prendre entre 5 minutes et 24 heures.

Exécutez la commande suivante pour vérifier que la conservation eDiscovery a été correctement distribuée.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

La valeur **Success** pour la propriété *DistributionStatus* indique que la conservation a été correctement placée sur les emplacements de contenu. Si la distribution n’est pas encore terminée, la valeur **En attente** s’affiche.

![Exemple de Get-CaseHoldPolicy PowerShell.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>Étape 7 : Créer la recherche

La dernière étape consiste à recréer la recherche que vous avez identifiée à l’étape 3 et à l’associer au cas. Après avoir créé la recherche, vous pouvez l’exécuter à l’aide de l’applet de commande **Start-ComplianceSearch** ou l’exécuter ultérieurement.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![Exemple de New-ComplianceSearch PowerShell.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-compliance-portal"></a>Étape 8 : Vérifier la casse, la conservation et la recherche dans le portail de conformité

Pour vous assurer que tout est correctement configuré, accédez au portail de conformité à [https://compliance.microsoft.com](https://compliance.microsoft.com)l’adresse **eDiscovery > Core**.

![Portail de conformité Microsoft Purview eDiscovery.](../media/MigrateLegacyeDiscovery7.png)

Le cas que vous avez créé à l’étape 3 est répertorié sur la page **eDiscovery (Standard).** Ouvrez le cas, puis notez la conservation que vous avez créée à l’étape 4 dans la liste sous l’onglet **Conservation** . Vous pouvez sélectionner la conservation pour afficher les détails sur la page de menu volant, y compris le nombre de boîtes aux lettres aux lesquelles la conservation est appliquée et l’état de distribution.

![eDiscovery se trouve dans le portail de conformité.](../media/MigrateLegacyeDiscovery8.png)

La recherche que vous avez créée à l’étape 7 est répertoriée sous l’onglet **Recherches** du cas.

![Recherche de cas eDiscovery dans le portail de conformité.](../media/MigrateLegacyeDiscovery9.png)

Si vous migrez une recherche In-Place eDiscovery, mais que vous ne l’associez pas à un cas eDiscovery, elle est répertoriée dans la page Recherche de contenu dans le portail de conformité.

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur In-Place & de découverte électronique dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, consultez :

  - [Découverte électronique locale](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Conservation inaltérable et conservation pour litige](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Pour plus d’informations sur les applets de commande PowerShell utilisées dans l’article, consultez :

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)

  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)

  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)

  - [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Pour plus d’informations sur le portail de conformité, consultez [Vue d’ensemble du portail de conformité Microsoft Purview](microsoft-365-compliance-center.md).