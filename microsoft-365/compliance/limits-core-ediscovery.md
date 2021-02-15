---
title: Limites dans le cas de découverte électronique principale
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article décrit les limites du cas eDiscovery principal dans Microsoft 365.
ms.openlocfilehash: 43d267acdb0c1fee0202c74832b376e066241d7c
ms.sourcegitcommit: 495b66b77d6dbe6d69e5b06b304089e4e476e568
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "49799661"
---
# <a name="limits-in-core-ediscovery"></a>Limites dans core eDiscovery

Le tableau suivant répertorie les limites pour les cas eDiscovery principaux et les cas de découverte électronique principaux associés à un cas eDiscovery principal. Pour plus d’informations sur Core eDiscovery, voir [Overview of Core eDiscovery](ediscovery-cases.md).
    
  | Description de la limite | Limite |
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation  <br/> |Sans limite  <br/> |
  |Nombre maximal de cas d’une organisation  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres dans une seule et même boîte aux lettres  <br/> |1 000  <br/> |
  |Nombre maximal de sites SharePoint et OneDrive Entreprise en une seule fois  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery principale, et nombre maximal d’éléments affichés dans les onglets En cours, Recherches et Exportation dans un cas. <sup>1</sup> |1 000|
  |||

   > [!NOTE]
   > <sup>1</sup> Pour afficher une liste de plus de 1 000 cas, de mise en attente, de recherches ou d’exportations, vous pouvez utiliser les cmdlets PowerShell de sécurité & conformité Office 365 correspondantes :
   > 
   > - [Get-ComplianceCase](https://docs.microsoft.com/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](https://docs.microsoft.com/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](https://docs.microsoft.com/powershell/module/exchange/get-compliancesearchaction)

Pour plus d’informations sur les limites liées aux recherches de contenu et aux exportations associées à un cas core eDiscovery, voir [Limits for Content Search and Core eDiscovery](limits-for-content-search.md).