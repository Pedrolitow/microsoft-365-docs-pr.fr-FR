---
title: Migration des recherches et des suspensions de découverte électronique héritées vers le centre de conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: db05b598fb0dab3cac9420b33b0bd4e12b6b7e9a
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41602791"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-microsoft-365-compliance-center"></a>Migration des recherches et des suspensions de découverte électronique héritées vers le centre de conformité Microsoft 365

Le centre de conformité Microsoft 365 offre une expérience améliorée pour l’utilisation de la fonctionnalité eDiscovery, notamment : une fiabilité plus élevée, de meilleures performances et de nombreuses fonctionnalités adaptées aux flux de travail eDiscovery, notamment des cas d’organisation de votre contenu, examiner les ensembles à Passez en revue le contenu et l’analyse pour vous aider à rechercher des données à des fins de révision, telles que le regroupement presque en double, le Threading de messagerie électronique, l’analyse des thèmes et le codage prédictif.

Pour aider les clients à tirer parti des fonctionnalités nouvelles et améliorées, cet article fournit des conseils de base sur la migration des recherches de découverte électronique inaltérable dans le centre d’administration Exchange vers le centre de conformité Microsoft 365.

> [!NOTE]
> Étant donné qu’il existe de nombreux scénarios différents, cet article fournit des conseils généraux pour effectuer des recherches et des suspensions dans un cas de découverte électronique de base dans le centre de conformité Microsoft 365. L’utilisation de cas de découverte électronique n’est pas toujours requise, mais elle ajoute une couche supplémentaire de sécurité en vous permettant d’attribuer des autorisations pour contrôler les personnes ayant accès aux cas eDiscovery dans votre organisation.

## <a name="before-you-begin"></a>Avant de commencer

- Pour exécuter les commandes PowerShell décrites dans cet article, vous devez être membre du groupe de rôles gestionnaire eDiscovery dans le centre de conformité Office 365 Security &. Vous devez également être membre du groupe de rôles gestion de la découverte dans le centre d’administration Exchange.

- Cet article fournit des instructions sur la création d’une conservation eDiscovery. La stratégie de blocage sera appliquée aux boîtes aux lettres par le biais d’un processus asynchrone. Lors de la création d’une conservation de découverte électronique, vous devez créer un CaseHoldPolicy et CaseHoldRule, sinon la conservation ne sera pas créée et les emplacements de contenu ne seront pas mis en attente.

## <a name="step-1-connect-to-exchange-online-powershell-and-office-365-security--compliance-center-powershell"></a>Étape 1 : Connectez-vous à Exchange Online PowerShell et à Office 365 Security & Compliance Center PowerShell

La première étape consiste à vous connecter au centre de sécurité Exchange Online PowerShell et Office 365 Security & PowerShell. Vous pouvez copier le script suivant, le coller dans une fenêtre PowerShell, puis l’exécuter. Vous serez invité à fournir les informations d’identification de l’organisation à laquelle vous souhaitez vous connecter. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $Session -AllowClobber -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

Vous devez exécuter les commandes dans les étapes suivantes de cette session PowerShell.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>Étape 2 : obtenir la liste des recherches de découverte électronique inaltérable à l’aide de Get-MailboxSearch

Une fois que vous avez effectué l’authentification, vous pouvez obtenir la liste des recherches de découverte électronique inaltérable en exécutant la cmdlet **Get-MailboxSearch** . Copiez et collez la commande suivante dans PowerShell, puis exécutez-la. Une liste des recherches s’affiche avec leur nom et l’état des conservations inaltérables.

```powershell
Get-MailboxSearch
```

La sortie de la cmdlet sera semblable à ce qui suit :

![Exemple PowerShell Get-MailboxSearch](media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>Étape 3 : obtenir des informations sur les recherches de découverte électronique inaltérable et les conservations inaltérables que vous souhaitez migrer

Une fois encore, vous allez utiliser la cmdlet **Get-MailboxSearch** , mais cette fois pour obtenir les propriétés de la recherche. Vous pouvez stocker ces propriétés dans une variable pour une utilisation ultérieure. L’exemple suivant stocke les résultats de la cmdlet **Get-MailboxSearch** dans une variable, puis affiche les propriétés de la recherche.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

La sortie de ces deux commandes est similaire à ce qui suit :

![Exemple de sortie PowerShell de l’utilisation de Get-MailboxSearch pour une recherche individuelle](media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> La durée de la conservation inaltérable dans cet exemple est indéfinie (*ItemHoldPeriod : Unlimited*). C’est généralement le cas pour la découverte électronique et les scénarios d’enquête légale. Si la durée de la conservation est différente de la valeur indéfinie, la raison est probablement le fait que la conservation est utilisée pour conserver le contenu dans un scénario de rétention. Au lieu d’utiliser les applets de commande eDiscovery dans Office 365 Security & Centre de conformité PowerShell pour les scénarios de rétention, nous vous recommandons d’utiliser [New-retentioncompliancepolicy permet](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-retentioncompliancepolicy) et [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-retention/new-retentioncompliancerule) pour conserver le contenu. Le résultat de l’utilisation de ces cmdlets est similaire à celui de **New-CaseHoldPolicy** et **New-CaseHoldRule**, mais vous pouvez spécifier une période de rétention et une action de rétention, telles que la suppression de contenu après l’expiration de la période de rétention. En outre, l’utilisation des cmdlets de rétention n’exige pas que vous associiez les conservations de rétention à un cas eDiscovery.

## <a name="step-4-create-a-case-in-the-microsoft-365-compliance-center"></a>Étape 4 : créer un cas dans le centre de conformité Microsoft 365

Pour créer une conservation de découverte électronique, vous devez créer un cas de découverte électronique pour associer le blocage à. L’exemple suivant crée un cas de découverte électronique à l’aide d’un nom de votre choix. Nous allons stocker les propriétés du nouveau cas dans une variable pour une utilisation ultérieure. Vous pouvez afficher ces propriétés en exécutant la `$case | FL` commande après avoir créé le cas.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```

![Exemple d’exécution de la commande New-ComplianceCase](media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>Étape 5 : créer le blocage eDiscovery

Une fois le cas créé, vous pouvez créer la conservation et l’associer au cas que vous avez créé à l’étape précédente. N’oubliez pas que vous devez créer une stratégie de blocage de cas et une règle de conservation des cas. Si la règle de conservation des dossiers n’est pas créée après la création de la stratégie de blocage de cas, la conservation de la découverte électronique n’est pas créée et aucun contenu n’est placé en conservation.

Exécutez les commandes suivantes pour recréer le blocage eDiscovery que vous souhaitez migrer. Ces exemples utilisent les propriétés du blocage sur place de l’étape 3 que vous souhaitez migrer.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
$rule = New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![Exemple d’utilisation des applets de commande NewCaseHoldPolicy et NewCaseHoldRule](media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>Étape 6 : vérifier la conservation de la découverte électronique

Pour vous assurer qu’il n’y a aucun problème lors de la création de la suspension, il est conseillé de vérifier que l’état de distribution de suspension est réussi. La distribution signifie que la conservation a été appliquée à tous les emplacements de contenu spécifiés dans le paramètre *exchangelocation permet* à l’étape précédente. Pour ce faire, vous pouvez exécuter la cmdlet **Get-CaseHoldPolicy** . Étant donné que les propriétés enregistrées dans la variable *$Policy* que vous avez créée à l’étape précédente ne sont pas automatiquement mises à jour dans la variable, vous devez réexécuter l’applet de commande pour vérifier que la distribution a réussi. La distribution des stratégies de conservation des dossiers peut prendre entre 5 minutes et 24 heures.

Exécutez la commande suivante pour vérifier que la conservation de découverte électronique a été correctement distribuée.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

La valeur de **Success** pour la propriété *DistributionStatus* indique que la conservation a été correctement placée sur les emplacements de contenu. Si la distribution n’est pas encore terminée, la valeur **en attente** est affichée.

![Exemple PowerShell Get-CaseHoldPolicy](media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>Étape 7 : créer la recherche

La dernière étape consiste à recréer la recherche que vous avez identifiée à l’étape 3 et à l’associer au cas. Une fois la recherche créée, vous pouvez l’exécuter à l’aide de la cmdlet **Start-ComplianceSearch** ou de l’exécuter ultérieurement.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![PowerShell New-ComplianceSearch-exemple](media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-microsoft-365-compliance-center"></a>Étape 8 : vérifier le cas, la mise en attente et la recherche dans le centre de conformité Microsoft 365

Pour vous assurer que tout est correctement configuré, accédez au centre de conformité Microsoft 365 à l' [https://compliance.microsoft.com](https://compliance.microsoft.com)adresse, puis cliquez sur **eDiscovery > Core**.

![Découverte électronique du centre de conformité Microsoft 365](media/MigrateLegacyeDiscovery7.png)

Le cas que vous avez créé à l’étape 3 est affiché dans la page de **découverte électronique principale** . Ouvrez le cas, puis notez le blocage que vous avez créé à l’étape 4 de la figure de l’onglet **suspensions** . Vous pouvez cliquer sur le blocage pour afficher les détails, notamment le nombre de boîtes aux lettres auxquelles la conservation est appliquée et l’état de la distribution.

![conservations eDiscovery dans le centre de conformité Microsoft 365](media/MigrateLegacyeDiscovery8.png)

La recherche que vous avez créée à l’étape 7 est indiquée dans la boîte de l’onglet **recherches** du cas eDiscovery.

![recherche de cas eDiscovery dans le centre de conformité Microsoft 365](media/MigrateLegacyeDiscovery9.png)

Si vous migrez une recherche de découverte électronique inaltérable, mais que vous ne l’associez pas à un cas de découverte électronique, celle-ci est indiquée sur la page recherche de contenu dans le centre de conformité Microsoft 365.

## <a name="more-information"></a>Plus d’informations

- Pour plus d’informations sur les conservations de la découverte électronique inaltérable & dans le centre d’administration Exchange, voir :
  
  - [Découverte électronique locale](https://docs.microsoft.com/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Conservation inaltérable et conservation pour litige](https://docs.microsoft.com/exchange/security-and-compliance/in-place-and-litigation-holds)

- Pour plus d’informations sur les applets de commande PowerShell utilisées dans l’article, voir :

  - [Get-MailboxSearch](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/get-mailboxsearch)
  
  - [New-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/new-compliancecase)

  - [New-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/new-caseholdpolicy)
  
  - [New-CaseHoldRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/new-caseholdrule)

  - [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/get-caseholdpolicy)
  
  - [New-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesearch)

  - [Start-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/start-compliancesearch)

- Pour plus d’informations sur le centre de conformité Microsoft 365, consultez [la rubrique Overview of the microsoft 365 Compliance Center](microsoft-365-compliance-center.md).
