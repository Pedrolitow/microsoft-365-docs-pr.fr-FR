---
title: Configurer Microsoft 365 Multi-Geo eDiscovery
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
localization_priority: Normal
ms.collection: Strat_SP_gtc
description: Découvrez comment utiliser le paramètre region pour configurer la fonctionnalité eDiscovery à des fins d’utilisation dans des emplacements satellites dans Microsoft 365 multi-géo.
ms.openlocfilehash: d1d66a9e7953b540e318c8364bdcb8d72654b482
ms.sourcegitcommit: 628f195cbe3c00910f7350d8b09997a675dde989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2020
ms.locfileid: "48636804"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Configuration eDiscovery dans Microsoft 365 Multi-Geo

Les [fonctionnalités avancées eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20) permettent à un administrateur eDiscovery multi-géo de rechercher tous les régions centres sans avoir à utiliser un filtre de sécurité « Region ». Les données sont exportées vers l’instance Azure de l’emplacement central du client multi-géo. 

Sans les fonctionnalités avancées eDiscovery, un gestionnaire eDiscovery ou un administrateur d’un client multi-géo ne pourra effectuer de découverte électronique qu’à l’emplacement central de ce client. Pour prendre en charge la fonctionnalité eDiscovery pour les emplacements satellites, un nouveau paramètre de filtre de sécurité de conformité nommé « Region » est disponible via PowerShell. Ce paramètre peut être utilisé par les clients dont l’emplacement central est en Amérique du Nord, en Europe ou en Asie Pacifique. Advanced eDiscovery est recommandé pour les clients dont l’emplacement central n’est pas en Amérique du Nord, en Europe ou en Asie Pacifique et qui doivent effectuer des opérations eDiscovery sur des emplacements géographiques satellites. 

L’administrateur général Microsoft 365 doit affecter les autorisations de gestionnaire eDiscovery pour autoriser d’autres personnes à mettre en place un processus eDiscovery, et affecter un paramètre "Région" dans le filtre de sécurité de conformité correspondant pour définir la région concernée par le processus comme emplacement satellite. Sinon, aucun processus eDiscovery n’est mis en place à l’emplacement satellite.

Quand un gestionnaire ou un administrateur eDiscovery est défini pour un emplacement satellite particulier, ce gestionnaire ou cet administrateur eDiscovery peut uniquement effectuer des actions de recherche eDiscovery dans les sites SharePoint et OneDrive situés dans cet emplacement satellite. Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de l’emplacement satellite spécifié, aucun résultat n’est renvoyé. Par ailleurs, lorsque le gestionnaire ou l’administrateur eDiscovery d’un emplacement satellite déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Ainsi, les entreprises respectent les règles de conformité en interdisant l’exportation de contenu au-delà de frontières contrôlées.

> [!NOTE]
> Si un gestionnaire eDiscovery doit effectuer des recherches dans plusieurs emplacements satellites SharePoint, un autre compte d’utilisateur doit être créé pour ce gestionnaire, lequel doit indiquer un autre emplacement satellite où sont situés les sites OneDrive ou SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

Pour définir le filtre de sécurité de conformité pour une région :

1. [Connectez-vous au centre de conformité Microsoft 365 Security & PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell)

2. Utilisez la syntaxe suivante :

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Par exemple :

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Consultez l’article [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/new-compliancesecurityfilter) pour en savoir plus sur la syntaxe et les paramètres supplémentaires.
