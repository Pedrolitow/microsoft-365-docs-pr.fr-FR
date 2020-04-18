---
title: Limites dans le cas eDiscovery de base
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article décrit les limites du cas de découverte électronique de base dans Microsoft 365.
ms.openlocfilehash: 4d91b81caee31e693ce29c6d8d629d563d973ae7
ms.sourcegitcommit: bd51f626f0c7788c2a3cf89deee25264659aebd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "43551398"
---
# <a name="limits-in-core-ediscovery"></a>Limites de la découverte électronique de base

Le tableau suivant répertorie les limites pour les cas de découverte électronique principaux et les blocages associés à un cas de découverte électronique principale. Pour plus d’informations sur la découverte électronique principale, voir [Overview of Core eDiscovery](ediscovery-cases.md).
    
  |**Description de la limite**|**Limite**|
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation  <br/> |Sans limite  <br/> |
  |Nombre maximal de blocages pour une organisation  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres en une seule suspension de cas  <br/> |1 000  <br/> |
  |Nombre maximal de sites SharePoint et OneDrive entreprise en une seule suspension de cas  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery principale et nombre maximal d’éléments affichés dans les onglets conservation, recherches et exportation dans un cas. <sup>0,1</sup> |1 000|
  |||

   > [!NOTE]
   > <sup>1</sup> pour afficher une liste de plus de 1 000 cas, de suspensions, de recherches ou d’exportations, vous pouvez utiliser la cmdlet Office 365 Security & Compliance PowerShell correspondante :<br/> [Get-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/get-compliancecase) <br/> [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-ediscovery/get-caseholdpolicy)<br/> [Get-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/get-compliancesearch)<br/> [Get-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/get-compliancesearchaction)
