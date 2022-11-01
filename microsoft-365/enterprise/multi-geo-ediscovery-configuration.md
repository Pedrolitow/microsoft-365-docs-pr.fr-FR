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
ms.openlocfilehash: f46699221c257319dbe9bba356c9487e74d0dd2a
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804384"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Configuration eDiscovery dans Microsoft 365 Multi-Geo

Les [fonctionnalités eDiscovery (Premium)](../compliance/overview-ediscovery-20.md) permettent à un administrateur eDiscovery multigéographique d’effectuer des recherches dans toutes les _zones géographiques_ sans avoir à utiliser un filtre de sécurité « Région ». Les données sont exportées vers l’instance Azure de l’emplacement _géographique approvisionné principal_ du _locataire multigéographique_.

Sans fonctionnalités eDiscovery (Premium), un gestionnaire eDiscovery ou un administrateur d’un _locataire_ multigéographique ne peut effectuer eDiscovery que dans l’emplacement _géographique approvisionné principal_ de ce _locataire_. Pour prendre en charge la possibilité d’effectuer eDiscovery pour les emplacements _géographiques satellites_ , un nouveau paramètre de filtre de sécurité de conformité nommé « Region » est disponible via PowerShell. Ce paramètre peut être utilisé par _les locataires dont l’emplacement_ _géographique approvisionné principal_ est en Amérique du Nord, en Europe ou en Asie-Pacifique. eDiscovery (Premium) est recommandé pour _les locataires dont l’emplacement_ _géographique approvisionné principal_ n’est pas en Amérique du Nord, en Europe ou en Asie-Pacifique et qui doivent effectuer une découverte électronique sur des emplacements _géographiques satellites_.

L’administrateur général Microsoft 365 doit attribuer des autorisations eDiscovery Manager pour permettre à d’autres utilisateurs d’effectuer eDiscovery et attribuer un paramètre « Region » dans leur filtre de sécurité de conformité applicable pour spécifier la _zone geography_ pour effectuer eDiscovery comme emplacement _géographique satellite_ . Sinon, aucune découverte électronique n’est effectuée pour l’emplacement _géographique satellite_ . Un seul filtre de sécurité « Région » par utilisateur est pris en charge.

Lorsque le rôle Gestionnaire ou Administrateur eDiscovery est défini pour un emplacement _géographique satellite_ particulier, le gestionnaire eDiscovery ou l’administrateur peut uniquement effectuer des actions de recherche eDiscovery sur les sites SharePoint et les sites OneDrive situés dans cet emplacement _géographique satellite_ . Si un gestionnaire ou un administrateur eDiscovery tente de rechercher des sites SharePoint ou OneDrive en dehors de l’emplacement _géographique satellite_ spécifié, aucun résultat ne sera retourné. En outre, lorsque le gestionnaire eDiscovery ou l’administrateur d’un emplacement _géographique satellite_ déclenche une exportation, les données sont exportées vers l’instance Azure de cette région. Cela permet aux organisations de rester en conformité en n’autorisant pas l’exportation de contenu au-delà des frontières contrôlées.

> [!NOTE]
> S’il est nécessaire qu’un Gestionnaire eDiscovery effectue une recherche dans plusieurs emplacements _géographiques satellites_ SharePoint, un autre compte d’utilisateur doit être créé pour le Gestionnaire eDiscovery qui spécifie l’emplacement _géographique satellite_ de remplacement où se trouvent les sites OneDrive ou SharePoint.

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
