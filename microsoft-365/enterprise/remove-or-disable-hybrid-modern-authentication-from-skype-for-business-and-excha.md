---
title: Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: Cet article explique comment supprimer ou désactiver l’authentification moderne hybride des Skype Entreprise et des Exchange.
ms.openlocfilehash: 6456873f7338b97b3255f3976e7520580ac2a142
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017785"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Suppression ou désactivation de l’authentification moderne hybride à partir de Skype Entreprise et Exchange

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Si vous avez activé l’authentification moderne hybride (HMA) uniquement pour trouver qu’elle n’est pas adaptée à votre environnement actuel, vous pouvez désactiver HMA. Cet article explique comment procéder.

## <a name="who-is-this-article-for"></a>Qui cet article est-il destiné à ?

Si vous avez activé l’authentification moderne dans Skype Entreprise En ligne ou localement, et/ou Exchange Online ou localement et que vous avez trouvé que vous devez désactiver HMA, ces étapes sont pour vous.

> [!IMPORTANT]
> Consultez l’article « [Skype Entreprise topologies prises en charge avec l’authentification moderne](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) » si vous êtes dans Skype Entreprise En ligne ou localement, si vous disposez d’un HMA de topologie mixte et que vous devez examiner les topologies prises en charge avant de commencer.

## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Comment désactiver l’authentification moderne hybride (Exchange)

1. **Exchange local** : [ouvrez l’interpréteur de commandes Exchange Management Shell](/powershell/exchange/open-the-exchange-management-shell) et exécutez les commandes suivantes :

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
   Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
   ```

2. **Exchange Online** : [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Exécutez la commande suivante pour désactiver l’authentification moderne :

   ```powershell
   Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
   ```

## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Comment désactiver l’authentification moderne hybride (Skype Entreprise)

1. **Skype Entreprise local** : exécutez les commandes suivantes dans Skype Entreprise Management Shell :

   ```powershell
   Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
   ```

2. **Skype Entreprise Online** : [Connecter à Skype Entreprise Online PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md). Exécutez la commande suivante pour désactiver l’authentification moderne :

   ```powershell
   Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
   ```

[Revenez à la vue d’ensemble de l’authentification moderne](hybrid-modern-auth-overview.md).
