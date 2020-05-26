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
ms.openlocfilehash: 00df8cff683701ce5ee38dca12b6f7af5b31c8b0
ms.sourcegitcommit: 40ec697e27b6c9a78f2b679c6f5a8875dacde943
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44351895"
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
   > <sup>1</sup> pour afficher une liste de plus de 1 000 cas, de suspensions, de recherches ou d’exportations, vous pouvez utiliser la cmdlet Office 365 Security & Compliance PowerShell correspondante :<br/> [Get-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/get-compliancecase) <br/> [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy)<br/> [Get-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch)<br/> [Get-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction)
