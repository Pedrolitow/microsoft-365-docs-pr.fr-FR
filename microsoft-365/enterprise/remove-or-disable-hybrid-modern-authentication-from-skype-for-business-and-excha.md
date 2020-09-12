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
description: Cet article explique comment supprimer ou désactiver l’authentification moderne hybride de Skype entreprise et d’Exchange.
ms.openlocfilehash: 70f62b9b2165464837aa1dea0e12854df116efe0
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547095"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez activé uniquement l’authentification moderne hybride (HMA) pour qu’elle ne soit pas appropriée pour votre environnement actuel, vous pouvez désactiver la HMA. Cet article explique comment procéder.
  
## <a name="who-is-this-article-for"></a>À qui est destiné cet article ?

Si vous avez activé l’authentification moderne dans Skype entreprise Online ou en local, et/ou Exchange Online ou en local et que vous avez besoin de désactiver la haute disponibilité, ces étapes sont pour vous.

> [!IMPORTANT]
> Reportez-vous à l’article «[topologies Skype entreprise prises en charge avec l’authentification moderne](https://technet.microsoft.com/library/mt803262.aspx)» si vous êtes dans Skype entreprise Online ou en local, que vous disposez d’une mémoire HMA mixte et que vous devez consulter les topologies prises en charge avant de commencer.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Désactivation de l’authentification moderne hybride (Exchange)

1. **Exchange local**: Ouvrez l’environnement de commande Exchange Management Shell et exécutez les commandes suivantes : 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [Connectez-vous à Exchange Online](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) à l’aide de PowerShell à distance. Exécutez la commande suivante pour transformer votre indicateur  *OAuth2ClientProfileEnabled*  en « false » :

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Procédure de désactivation de l’authentification moderne hybride (Skype entreprise)

1. **Skype entreprise en local**: exécutez les commandes suivantes dans Skype entreprise Management Shell :

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype entreprise Online**: [Connectez-vous à Skype entreprise Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) avec PowerShell à distance. Exécutez la commande suivante pour désactiver l’authentification moderne :

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Revenez à la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md) . 
  

