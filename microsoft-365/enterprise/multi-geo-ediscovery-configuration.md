---
title: Configurer Microsoft 365 Multi-Geo eDiscovery
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
ms.collection: Strat_SP_gtc
description: Découvrez comment utiliser le paramètre Region pour configurer eDiscovery pour une utilisation dans des emplacements satellites dans Microsoft 365 Multi-Geo.
ms.openlocfilehash: 640f5d4e6e8937e4dbcda1aaf2cfe48bf3d5ab22
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67698306"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Configuration eDiscovery dans Microsoft 365 Multi-Geo

Les [fonctionnalités eDiscovery (Premium)](../compliance/overview-ediscovery-20.md) permettent à un administrateur eDiscovery multigéographique de rechercher toutes les zones géographiques sans avoir à utiliser un filtre de sécurité « Région ». Les données sont exportées vers l’instance Azure de l’emplacement central du locataire multigéographique.

Sans fonctionnalités eDiscovery (Premium), un responsable eDiscovery ou un administrateur d’un locataire multigéographique ne pourra effectuer eDiscovery qu’à l’emplacement central de ce locataire. Pour prendre en charge la possibilité d’effectuer la découverte électronique pour les emplacements satellites, un nouveau paramètre de filtre de sécurité de conformité nommé « Region » est disponible via PowerShell. Ce paramètre peut être utilisé par les locataires dont l’emplacement central se trouve en Amérique du Nord, en Europe ou en Asie-Pacifique. eDiscovery (Premium) est recommandé pour les locataires dont l’emplacement central n’est pas dans Amérique du Nord, Europe ou Asie-Pacifique et qui doivent effectuer eDiscovery sur des emplacements géographiques satellites.

L’administrateur général microsoft 365 doit attribuer des autorisations eDiscovery Manager pour permettre à d’autres utilisateurs d’effectuer la découverte électronique et d’affecter un paramètre « Region » dans leur filtre de sécurité de conformité applicable pour spécifier la région pour la réalisation d’eDiscovery en tant qu’emplacement satellite. Sinon, aucune découverte électronique n’est effectuée pour l’emplacement satellite. Un seul filtre de sécurité « Région » par utilisateur est pris en charge.

Quand un gestionnaire ou un administrateur eDiscovery est défini pour un emplacement satellite particulier, ce gestionnaire ou cet administrateur eDiscovery peut uniquement effectuer des actions de recherche eDiscovery dans les sites SharePoint et OneDrive situés dans cet emplacement satellite. Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de l’emplacement satellite spécifié, aucun résultat n’est renvoyé. Par ailleurs, lorsque le gestionnaire ou l’administrateur eDiscovery d’un emplacement satellite déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Ainsi, les entreprises respectent les règles de conformité en interdisant l’exportation de contenu au-delà de frontières contrôlées.

> [!NOTE]
> Si un gestionnaire eDiscovery doit effectuer des recherches dans plusieurs emplacements satellites SharePoint, un autre compte d’utilisateur doit être créé pour ce gestionnaire, lequel doit indiquer un autre emplacement satellite où sont situés les sites OneDrive ou SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Pour définir le filtre de sécurité de conformité pour une région :

1. [Se connecter à Microsoft 365 Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Utilisez la syntaxe suivante :

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Par exemple :

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Consultez l’article [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) pour en savoir plus sur la syntaxe et les paramètres supplémentaires.
