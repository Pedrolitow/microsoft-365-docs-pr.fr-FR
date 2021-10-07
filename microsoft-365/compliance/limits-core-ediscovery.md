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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Cet article décrit les limites du cas eDiscovery principal Microsoft 365.
ms.openlocfilehash: 82caa5214f777effb912ab1a2a3054b1e4432ae6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60190700"
---
# <a name="limits-in-core-ediscovery"></a>Limites dans core eDiscovery

Le tableau suivant répertorie les limites pour les cas eDiscovery principaux et les cas de découverte électronique principaux associés à un cas eDiscovery principal. Pour plus d’informations sur Core eDiscovery, voir [Overview of Core eDiscovery](./get-started-core-ediscovery.md).
    
  | Description de la limite | Limite |
  |:-----|:-----|
  |Nombre maximal de cas pour une organisation.  <br/> |Aucune limite  <br/> |
  |Nombre maximal de cas d’une organisation.  <br/> |10 000  <br/> |
  |Nombre maximal de boîtes aux lettres dans une seule et même boîte aux lettres. Cette limite inclut le total combiné de boîtes aux lettres utilisateur et les boîtes aux lettres associées aux groupes Microsoft 365, Microsoft Teams et Yammer groupes.  <br/> |1 000  <br/> |
  |Nombre maximal de sites dans une seule et même période d’attente. Cette limite inclut le total combiné des sites OneDrive Entreprise, des sites SharePoint et des sites associés aux groupes Microsoft 365, Microsoft Teams et Yammer groupes.  <br/> |100  <br/> |
  |Nombre maximal de cas affichés sur la page d’accueil eDiscovery principale, et nombre maximal d’éléments affichés dans les onglets En cours, Recherches et Exportation dans un cas. <sup>1</sup> |1 000|
  |||

   > [!NOTE]
   > <sup>1</sup> Pour afficher une liste de plus de 1 000 cas, de mise en attente, de recherches ou d’exportations, vous pouvez utiliser les cmdlets PowerShell de sécurité Office 365 & conformité correspondantes :
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Pour plus d’informations sur les limites liées aux recherches et aux exportations associées à un cas core eDiscovery, voir Limites pour la recherche de contenu et core [eDiscovery](limits-for-content-search.md).