---
title: Limites dans le cas eDiscovery principal
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article décrit les limites du cas eDiscovery principal dans Microsoft 365.
ms.openlocfilehash: 2d920fbe5973d07b7da656d6247038ab785bbe5c
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64822647"
---
# <a name="limits-in-core-ediscovery"></a>Limites dans Core eDiscovery

Le tableau suivant répertorie les limites pour les cas eDiscovery principaux et les conservations associées à un cas eDiscovery de base. Pour plus d’informations sur Core eDiscovery, consultez [Vue d’ensemble de Core eDiscovery](./get-started-core-ediscovery.md).
    
  | Description de la limite | Limite |
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation.  <br/> |Aucune limite  <br/> |
  |Nombre maximal de conservations de cas pour une organisation.  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres dans une conservation unique. Cette limite inclut le total combiné des boîtes aux lettres utilisateur et les boîtes aux lettres associées aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer.  <br/> |1 000  <br/> |
  |Nombre maximal de sites dans une conservation unique. Cette limite inclut le total combiné des sites OneDrive Entreprise, des sites SharePoint et des sites associés aux groupes Groupes Microsoft 365, Microsoft Teams et Yammer.  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery principale et nombre maximal d’éléments affichés dans les onglets Conservations, Recherches et Exportation dans un cas. <sup>1</sup> |1 000|

   > [!NOTE]
   > <sup>1</sup> Pour afficher une liste de plus de 1 000 cas, conservations, recherches ou exportations, vous pouvez utiliser les applets de commande PowerShell de sécurité Office 365 & conformité correspondantes :
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Pour plus d’informations sur les limites liées aux recherches et aux exportations associées à un cas Core eDiscovery, consultez [Limits for Content search et Core eDiscovery](limits-for-content-search.md).