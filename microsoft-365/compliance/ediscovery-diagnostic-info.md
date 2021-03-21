---
title: Collecter des informations de diagnostic eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Découvrez comment collecter des informations de diagnostic eDiscovery pour un cas de support Microsoft.
ms.openlocfilehash: 842f8baf770f178df3298bbfa911de26ce946ed0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50926554"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Collecter des informations de diagnostic eDiscovery

Parfois, les ingénieurs du support Microsoft ont besoin d’informations spécifiques sur votre problème lorsque vous ouvrez un cas de support lié à Core eDiscovery ou Advanced eDiscovery. Cet article fournit des instructions sur la collecte d’informations de diagnostic pour aider les ingénieurs du support technique à examiner et à résoudre les problèmes. En règle générale, vous n’avez pas besoin de collecter ces informations tant qu’un ingénieur du Support Microsoft ne vous y a pas demandé.

> [!IMPORTANT]
> Les résultats des cmdlets et des informations de diagnostic décrites dans cet article peuvent inclure des informations sensibles sur les litiges ou les enquêtes internes dans votre organisation. Avant d’envoyer les informations de diagnostic brutes au Support Microsoft, vous devez passer en revue ces informations et les rendre confidentielles (telles que des noms ou d’autres informations sur les parties à des litiges ou à des enquêtes) en les remplaçant par `XXXXXXX` . L’utilisation de cette méthode indique également à l’ingénieur du support Microsoft que les informations ont été expurgées.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>Collecter des informations de diagnostic pour core eDiscovery

La collecte d’informations de diagnostic pour core eDiscovery est basée sur les cmdlet. Vous devez donc utiliser le Centre de sécurité & conformité PowerShell. Les exemples PowerShell suivants exécutent des cmdlets, puis enregistrent la sortie dans un fichier texte spécifié. Dans la plupart des cas de prise en charge, vous ne devez exécuter qu’une de ces commandes.

Pour exécuter les cmdlets suivantes, [connectez-vous </span> au Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell). Une fois connecté, exécutez une ou plusieurs des commandes suivantes et assurez-vous de remplacer les espaces réservé par les noms d’objets réels.

Après avoir passé en revue le fichier texte généré et publié des informations sensibles, envoyez-le à l’ingénieur du support Microsoft qui travaille sur votre cas.

> [!NOTE]
> Vous pouvez également exécuter les commandes de cette section pour collecter des informations de diagnostic pour les recherches et les exportations répertoriées sur la **page** de recherche de contenu dans le Centre de conformité Microsoft 365.

### <a name="collect-information-about-searches"></a>Collecter des informations sur les recherches

La commande suivante collecte des informations utiles lors de l’étude de problèmes liés à une recherche de contenu ou à une recherche associée à un cas core eDiscovery.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Collecter des informations sur les actions de recherche

La commande suivante collecte des informations pour examiner les problèmes liés à l’aperçu, l’exportation ou la purge des résultats d’une recherche de contenu ou d’une recherche associée à un cas core eDiscovery. Vous pouvez identifier le nom de l’action de recherche en cliquant sur une exportation répertoriée sous **l’onglet Exportation.** Pour identifier les noms des actions d’aperçu et de purge, vous pouvez exécuter la cmdlet **Get-ComplianceSearchAction** pour afficher la liste de toutes les actions. Le format du nom de l’action de recherche est construit en attente, ou au nom `_Preview` `_Export` de la recherche `_Purge` correspondante.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Collecter des informations sur les holds eDiscovery

Lorsqu’une attente eDiscovery associée à un cas eDiscovery principal ne fonctionne pas comme prévu, exécutez la commande suivante pour collecter des informations sur la stratégie de cas de attente et la règle de cas associée pour la attente eDiscovery. Le *nom de la stratégie de la* case à conserver dans la commande suivante est identique au nom de la découverte électronique. Vous pouvez identifier ce nom sous les **onglets Holds** dans le cas core eDiscovery.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Collecter toutes les informations de cas

Parfois, il n’est pas évident de savoir quelles informations sont requises par le Support Microsoft pour examiner votre problème. Dans ce cas, vous pouvez collecter toutes les informations de diagnostic pour un cas core eDiscovery. Le nom du cas *core eDiscovery* dans la commande suivante est identique au nom d’un cas qui s’affiche sur la page Core **eDiscovery** dans le Centre de conformité Microsoft 365.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{"$($_.Name)";"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>Collecter des informations de diagnostic pour Advanced eDiscovery

**L’onglet Paramètres** dans un cas Advanced eDiscovery vous permet de copier rapidement les informations de diagnostic du cas. Les informations de diagnostic sont enregistrées dans le Presse-papiers afin que vous pouvez les coller dans un fichier texte et les envoyer au Support Microsoft.

1. Go to [https://compliance.microsoft.com](https://compliance.microsoft.com/) and then click Show all > **eDiscovery > Advanced**.

2. Sélectionnez un cas, puis cliquez sur **l’onglet Paramètres.**

3. Sous **Informations de cas,** cliquez sur **Sélectionner.**

4. Dans la page volante, cliquez sur **Copier les informations de diagnostic** pour copier les informations dans le Presse-papiers.

5. Ouvrez un fichier texte (dans le Bloc-notes), puis collez les informations dans le fichier texte.

6. Enregistrez le fichier texte et nommez-le comme vous le `AeD Diagnostic Info YYYY.MM.DD` souhaitez (par exemple, `AeD Diagnostic Info 2020.11.03` ).

Après avoir passé en revue le fichier et envoyé des informations sensibles, envoyez-le à l’ingénieur du support Microsoft qui travaille sur votre cas.