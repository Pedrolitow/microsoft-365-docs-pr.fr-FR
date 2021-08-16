---
title: Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Cet article explique comment supprimer ou désactiver l’authentification moderne hybride de Skype Entreprise et Exchange.
ms.openlocfilehash: dd663c1178f2f7008917f944c6e641a696c81bdb0c9ce8d325267d861910f4c5
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53904658"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez activé l’authentification moderne hybride (HMA) uniquement pour trouver qu’elle ne convient pas à votre environnement actuel, vous pouvez désactiver HMA. Cet article explique comment.
  
## <a name="who-is-this-article-for"></a>Qui cet article est-il pour ?

Si vous avez activé l’authentification moderne dans Skype Entreprise Online ou en local, et/ou Exchange Online ou en local et que vous avez trouvé que vous devez désactiver HMA, ces étapes sont à votre place.

> [!IMPORTANT]
> Consultez l’article «[topologies](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)Skype Entreprise pris en charge avec l’authentification moderne » si vous êtes dans Skype Entreprise Online ou en local, que vous avez un HMA de topologie mixte et que vous devez examiner les topologies pris en charge avant de commencer.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Comment désactiver l’authentification moderne hybride (Exchange)

1. **Exchange local**: ouvrez l’Exchange Management Shell et exécutez les commandes suivantes : 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Connecter à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) avec Remote PowerShell. Exécutez la commande suivante pour transformer votre  *indicateur OAuth2ClientProfileEnabled*  en « false » :

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Comment désactiver l’authentification moderne hybride (Skype Entreprise)

1. **Skype Entreprise local**: exécutez les commandes suivantes dans Skype Entreprise Management Shell :

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype Entreprise Online :** [Connecter à Skype Entreprise Online avec](manage-skype-for-business-online-with-microsoft-365-powershell.md) Remote PowerShell. Exécutez la commande suivante pour désactiver l’authentification moderne :

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Lien vers la vue d’ensemble de l’authentification moderne.](hybrid-modern-auth-overview.md) 
