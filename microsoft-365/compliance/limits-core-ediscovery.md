---
title: Limites dans le cas eDiscovery (Standard)
description: Cet article décrit les limites du cas eDiscovery (Standard) dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 6dac70d326f6d6c0480797bf7a7b00ec0ea2be7f
ms.sourcegitcommit: 4dfb5de8c61847b8ddd10410ad20d34860eed8f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68131980"
---
# <a name="limits-in-ediscovery-standard"></a>Limites dans eDiscovery (Standard)

Le tableau suivant répertorie les limites pour les cas eDiscovery (Standard) et les conservations associées à un cas eDiscovery (Standard). Pour plus d’informations sur Microsoft Purview eDiscovery (Standard), consultez [Vue d’ensemble d’eDiscovery (Standard).](./get-started-core-ediscovery.md)
    
  | Description de la limite | Limite |
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation.  <br/> |Aucune limite  <br/> |
  |Nombre maximal de conservations de cas pour une organisation.  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres en conservation unique. Cette limite inclut le total combiné des boîtes aux lettres utilisateur et les boîtes aux lettres associées aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer.  <br/> |1 000  <br/> |
  |Nombre maximal de sites dans une conservation unique. Cette limite inclut le total combiné des sites OneDrive Entreprise, des sites SharePoint et des sites associés aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer.  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery (Standard) et nombre maximal d’éléments affichés dans les onglets Conservations, Recherches et Exportation dans un cas. <sup>1</sup> |1 000|

   > [!NOTE]
   > <sup>1</sup> Pour afficher une liste de plus de 1 000 cas, conservations, recherches ou exportations, vous pouvez utiliser les applets de commande PowerShell de sécurité Office 365 & conformité correspondantes :
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Pour plus d’informations sur les limites liées aux recherches et aux exportations associées à un cas eDiscovery (Standard), consultez [Limits for Content search and eDiscovery (Standard).](limits-for-content-search.md)