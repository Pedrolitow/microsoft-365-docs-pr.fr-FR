---
title: Collecter des informations de diagnostic eDiscovery
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Découvrez comment collecter des informations de diagnostic eDiscovery pour un cas Support Microsoft.
ms.openlocfilehash: 46c85e822daf82cc88e6bf89ceea97dede3e2276
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641809"
---
# <a name="collect-ediscovery-diagnostic-information"></a>Collecter des informations de diagnostic eDiscovery

Parfois, Support Microsoft ingénieurs ont besoin d’informations spécifiques sur votre problème lorsque vous ouvrez un cas de support lié à Microsoft Purview eDiscovery (Standard) ou Microsoft Purview eDiscovery (Premium). Cet article fournit des conseils sur la collecte d’informations de diagnostic pour aider les ingénieurs du support technique à examiner et à résoudre les problèmes. En règle générale, vous n’avez pas besoin de collecter ces informations tant qu’un ingénieur Support Microsoft n’a pas demandé de le faire.

> [!IMPORTANT]
> La sortie des applets de commande et des informations de diagnostic décrites dans cet article peut inclure des informations sensibles sur les litiges ou les enquêtes internes dans votre organisation. Avant d’envoyer les informations de diagnostic brutes à Support Microsoft, vous devez passer en revue les informations et rétablir les informations sensibles (telles que des noms ou d’autres informations sur les parties à un litige ou une enquête) en les `XXXXXXX`remplaçant par . Cette méthode indique également à l’ingénieur Support Microsoft que des informations ont été rédigées.

## <a name="collect-diagnostic-information-for-ediscovery-standard"></a>Collecter des informations de diagnostic pour eDiscovery (Standard)

La collecte d’informations de diagnostic pour eDiscovery (Standard) est basée sur des applets de commande. Vous devez donc utiliser Security & Compliance PowerShell. Les exemples PowerShell suivants exécutent des applets de commande, puis enregistrent la sortie dans un fichier texte spécifié. Dans la plupart des cas de support, vous ne devez exécuter qu’une seule de ces commandes.

Pour exécuter les applets de commande suivantes, [connectez-vous à Security & Compliance PowerShell</span>](/powershell/exchange/connect-to-scc-powershell). Une fois connecté, exécutez une ou plusieurs des commandes suivantes et veillez à remplacer les espaces réservés par les noms d’objets réels.

Après avoir examiné le fichier texte généré et rédigé des informations sensibles, envoyez-le à l’ingénieur Support Microsoft qui travaille sur votre cas.

> [!NOTE]
> Vous pouvez également exécuter les commandes de cette section pour collecter des informations de diagnostic pour les recherches et les exportations répertoriées sur la page **Recherche de contenu** dans le portail de conformité Microsoft Purview.

### <a name="collect-information-about-searches"></a>Collecter des informations sur les recherches

La commande suivante collecte des informations utiles lors de l’examen des problèmes liés à une recherche de contenu ou à une recherche associée à un cas eDiscovery (Standard).

```powershell
Get-ComplianceSearch "<Search name>" | FL > "ComplianceSearch.txt"
```

### <a name="collect-information-about-search-actions"></a>Collecter des informations sur les actions de recherche

La commande suivante collecte des informations pour examiner les problèmes d’aperçu, d’exportation ou de purge des résultats d’une recherche de contenu ou d’une recherche associée à un cas eDiscovery (Standard). Vous pouvez identifier le nom de l’action de recherche en cliquant sur une exportation répertoriée sous l’onglet **Exportations** . Pour identifier les noms des actions d’aperçu et de vidage, vous pouvez exécuter l’applet de commande **Get-ComplianceSearchAction** pour afficher une liste de toutes les actions. Le format du nom de l’action de recherche est construit en ajoutant `_Preview`, `_Export`ou `_Purge` au nom de la recherche correspondante.

```powershell
Get-ComplianceSearchAction "<Search action name>" | FL > "ComplianceSearchAction.txt"
```

### <a name="collect-information-about-ediscovery-holds"></a>Collecter des informations sur les conservations eDiscovery

Lorsqu’une conservation eDiscovery associée à un cas eDiscovery (Standard) ne fonctionne pas comme prévu, exécutez la commande suivante pour collecter des informations sur la stratégie de conservation des cas et la règle de conservation de cas associée pour la conservation eDiscovery. Le nom de la stratégie *de conservation* case dans la commande suivante est le même que le nom de la conservation eDiscovery. Vous pouvez identifier ce nom sous les onglets **Conservations** dans le cas eDiscovery (Standard).

```powershell
Get-CaseHoldPolicy "<Case hold policy name>" | %{"--CaseHoldPolicy--";$_|FL;"--CaseHoldRule--";Get-CaseHoldRule -Policy $_.Name | FL} > "eDiscoveryCaseHold.txt"
```

### <a name="collect-all-case-information"></a>Collecter toutes les informations de cas

Parfois, il n’est pas évident quelles informations sont requises par Support Microsoft pour examiner votre problème. Dans ce cas, vous pouvez collecter toutes les informations de diagnostic pour un cas eDiscovery (Standard). Le *nom de cas eDiscovery (Standard)* dans la commande suivante est identique au nom d’un cas affiché sur la page **eDiscovery (Standard)** dans le portail de conformité.

```powershell
Get-ComplianceCase "<eDiscovery (Standard) case name>"| %{$_|fl;"`t==Searches==";Get-ComplianceSearch -Case $_.Name | FL;"`t==Search Actions==";Get-ComplianceSearchAction -Case $_.Name |FL;"`t==Holds==";Get-CaseHoldPolicy -Case $_.Name | %{$_|FL;"`t`t ==$($_.Name) Rules==";Get-CaseHoldRule -Policy $_.Name | FL}} > "eDiscoveryCase.txt"
```

## <a name="collect-diagnostic-information-for-ediscovery-premium"></a>Collecter des informations de diagnostic pour eDiscovery (Premium)

L’onglet **Paramètres** d’un cas eDiscovery (Premium) vous permet de copier rapidement les informations de diagnostic pour le cas. Les informations de diagnostic sont enregistrées dans le Presse-papiers afin de pouvoir les coller dans un fichier texte et les envoyer à Support Microsoft.

1. Accédez au portail de conformité, puis sélectionnez **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**Advanced**</a>.

2. Sélectionnez un cas, puis cliquez sur l’onglet **Paramètres** .

3. Sous **Informations sur la casse**, cliquez sur **Sélectionner**.

4. Dans la page de menu volant, cliquez sur **Actions** > **Copy pour** copier les informations dans le Presse-papiers.

5. Ouvrez un fichier texte (dans le Bloc-notes), puis collez les informations dans le fichier texte.

6. Enregistrez le fichier texte et nommez-le comme `AeD Diagnostic Info YYYY.MM.DD` suit (par exemple, `AeD Diagnostic Info 2020.11.03`).

Après avoir examiné le fichier et rédigé des informations sensibles, envoyez-le à l’ingénieur Support Microsoft qui travaille sur votre cas.
