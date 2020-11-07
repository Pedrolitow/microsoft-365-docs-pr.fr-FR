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
description: Découvrez Comment collecter des informations de diagnostic eDiscovery pour un cas de support Microsoft.
ms.openlocfilehash: 107309748e2f27b50be5f8e8fc76afcb693989f9
ms.sourcegitcommit: dab50e1cc5bba920720b80033c93457f5ca1c330
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "48944391"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Collecter des informations de diagnostic eDiscovery

Parfois, les ingénieurs du support Microsoft ont besoin d’informations spécifiques sur votre problème lorsque vous ouvrez une demande de support liée à Core eDiscovery ou Advanced eDiscovery. Cet article fournit des conseils sur la façon de collecter des informations de diagnostic pour aider les ingénieurs à examiner et résoudre les problèmes. En règle générale, vous n’avez pas besoin de collecter ces informations jusqu’à ce qu’un ingénieur du support technique Microsoft vous demande de le faire.

> [!IMPORTANT]
> La sortie des applets de commande et des informations de diagnostic décrites dans cet article peut inclure des informations sensibles sur les litiges ou les investigations internes de votre organisation. Avant d’envoyer les informations de diagnostic brutes au support Microsoft, vous devez passer en revue les informations et biffer les informations sensibles (telles que les noms ou autres informations relatives aux parties au litige ou à l’enquête) en les remplaçant par `XXXXXXX` . Cette méthode indique également à l’ingénieur du support Microsoft que des informations ont été rédigées.

## <a name="collect-diagnostic-information-for-core-ediscovery"></a>Collecter les informations de diagnostic pour la découverte électronique principale

La collecte des informations de diagnostic pour la découverte électronique principale est basée sur les cmdlets, de sorte que vous devez utiliser la sécurité & PowerShell du centre de conformité. Les exemples PowerShell suivants exécuteront des cmdlets, puis enregistreront la sortie dans un fichier texte spécifié. Dans la plupart des cas de prise en charge, vous devez uniquement exécuter l’une de ces commandes.

Pour exécuter les applets de commande suivantes, [Connectez-vous à la </span> sécurité & Centre de conformité PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell). Une fois que vous êtes connecté, exécutez une ou plusieurs des commandes suivantes et assurez-vous de remplacer les espaces réservés par les noms d’objet réels.

Une fois que vous avez vérifié le fichier texte généré et redacting les informations sensibles, envoyez-le à l’ingénieur du support technique Microsoft en travaillant sur votre cas.

> [!NOTE]
> Vous pouvez également exécuter les commandes de cette section pour collecter des informations de diagnostic pour les recherches et les exportations figurant sur la page **recherche de contenu** dans le centre de conformité Microsoft 365.

### <a name="collect-information-about-searches"></a>Collecter des informations sur les recherches

La commande suivante collecte des informations utiles lors de l’étude des problèmes liés à une recherche de contenu ou à une recherche associée à un cas de découverte électronique principale.

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Collecter des informations sur les actions de recherche

La commande suivante collecte des informations pour identifier les problèmes liés à l’aperçu, à l’exportation ou au vidage des résultats d’une recherche de contenu ou d’une recherche associée à un cas de découverte électronique principale. Vous pouvez identifier le nom de l’action de recherche en cliquant sur une exportation qui est indiquée sous l’onglet **exportations** . Pour identifier les noms des actions d’aperçu et de purge, vous pouvez exécuter la cmdlet **Get-ComplianceSearchAction** pour afficher la liste de toutes les actions. Le format du nom de l’action de recherche est construit en ajoutant `_Preview` , `_Export` ou `_Purge` au nom de la recherche correspondante.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Collecte d’informations sur les conservations eDiscovery

Lorsqu’une conservation de découverte électronique associée à un cas de découverte électronique principale ne fonctionne pas comme prévu, exécutez la commande suivante pour collecter des informations sur la stratégie de blocage de la casse et la règle de blocage de la découverte électronique associée. Le *nom* de la stratégie de conservation de la casse dans la commande suivante est le même que le nom du blocage eDiscovery. Vous pouvez identifier ce nom dans les onglets de **suspensions** dans le cas de découverte électronique principale.

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Collecter toutes les informations de cas

Parfois, il n’est pas évident que les informations requises par le support Microsoft pour enquêter sur votre problème. Dans ce cas, vous pouvez collecter toutes les informations de diagnostic pour un cas de découverte électronique de base. Le *nom principal du cas eDiscovery* dans la commande suivante est identique au nom d’un cas qui est affiché sur la page **principale de découverte électronique** dans le centre de conformité Microsoft 365.

```powershell
Get-ComplianceCase "<Core eDiscovery case name>"| %{"$($_.Name)";"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-advanced-ediscovery"></a>Collecter des informations de diagnostic pour Advanced eDiscovery

L’onglet **paramètres** dans un cas avancé de découverte électronique vous permet de copier rapidement les informations de diagnostic pour le cas. Les informations de diagnostic sont enregistrées dans le presse-papiers afin que vous puissiez les coller dans un fichier texte et les envoyer au support Microsoft.

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com/) , puis cliquez sur **Afficher tous les > EDiscovery > Advanced**.

2. Sélectionnez un cas, puis cliquez sur l’onglet **paramètres** .

3. Sous **informations** sur le cas, cliquez sur **Sélectionner**.

4. Sur la page de menu volant, cliquez sur **copier les informations de diagnostic** pour copier les informations dans le presse-papiers.

5. Ouvrez un fichier texte (dans le bloc-notes), puis collez les informations dans le fichier texte.

6. Enregistrez le fichier texte et nommez-le comme vous le souhaitez `AeD Diagnostic Info YYYY.MM.DD` (par exemple, `AeD Diagnostic Info 2020.11.03` ).

Une fois que vous avez consulté le fichier et redacting informations sensibles, envoyez-le à l’ingénieur du support technique Microsoft en travaillant sur votre cas.
