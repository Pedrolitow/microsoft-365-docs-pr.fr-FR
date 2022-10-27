---
title: Configurer l’encombrement pour votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier3
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'Découvrez comment activer ou désactiver la fonctionnalité Courrier pêle-mêle pour tous les utilisateurs ou des utilisateurs spécifiques de votre organisation, à l’aide d’Exchange PowerShell. '
ms.openlocfilehash: 6858f96c20f7d3028891aae421199379521b5798
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68718179"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>Configurer Microsoft 365 Courrier pêle-mêle pour votre organisation

> [!TIP]
> [La boîte de réception Prioritaire](../setup/configure-focused-inbox.md) va remplacer l’encombrement. En savoir plus : [Mise à jour de la boîte de réception prioritaire et de nos plans pour l’encombrement](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
En tant qu’administrateur, vous devrez peut-être gérer la fonctionnalité Courrier pêle-mêle dans Microsoft 365. Pour activer/désactiver la fonctionnalité Courrier pêle-mêle pour les utilisateurs de votre organisation, vous devez utiliser Exchange PowerShell. (Les personnes peuvent l’activer/la désactiver en suivant les instructions suivantes : [Désactiver/désactiver le désordre dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Consultez [Utilisation de PowerShell avec Exchange Online](/powershell/exchange/exchange-online-powershell) et [Se connecter à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour plus d’informations sur l’utilisation d’Exchange PowerShell. Vous devez disposer d’un compte disposant au moins du rôle d’administrateur de service Exchange et de la possibilité de vous connecter à Exchange Online avec PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Activer l’encombrement à l’aide d’Exchange PowerShell

Vous pouvez activer l’encombrement manuellement pour une boîte aux lettres en exécutant l’applet [de commande Set-Clutter](/powershell/module/exchange/set-clutter) . Vous pouvez également afficher les paramètres d’encombrement des boîtes aux lettres de votre organisation en exécutant l’applet [de commande Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Activer le courrier pêle-mêle pour un seul utilisateur nommé Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Désactiver l’encombrement à l’aide d’Exchange PowerShell

Vous pouvez désactiver l’encombrement manuellement pour une boîte aux lettres en exécutant l’applet [de commande Set-Clutter](/powershell/module/exchange/set-clutter) . Vous pouvez également afficher les paramètres **d’encombrement** des boîtes aux lettres de votre organisation en exécutant l’applet [de commande Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Désactivez l’encombrement pour un seul utilisateur nommé Allie Bellew :
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Si vous utilisez PowerShell pour créer vos utilisateurs en bloc, vous devez exécuter [Set-Clutter](/powershell/module/exchange/set-clutter) sur la boîte aux lettres de chaque utilisateur pour gérer le courrier pêle-mêle. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Quand le commutateur d’activation/de désactivation du courrier s’affiche-t-il aux utilisateurs dans Outlook sur le web ?
<a name="bkmk_onoff"> </a>

En tant qu’administrateur, vous pouvez réactiver le courrier pêle-mêle à l’aide d’Exchange PowerShell. Une fois cette opération effectuée, la boîte de réception Prioritaire est désactivée et l’encombrement est à nouveau actif. 
  
 **Si vous utilisez Outlook sur le web avec un abonnement Microsoft 365 Business Premium :**
  
- Si l’utilisateur a actuellement activé le courrier pêle-mêle : 
    
  - Les paramètres d’encombrement s’affichent
    
- Si la boîte de réception Prioritaire est activée pour l’utilisateur : 
    
  - Les paramètres d’encombrement ne s’affichent pas
    
- Si ni la boîte de réception pêle-mêle ni la boîte de réception prioritaire n’est activée : 
    
  - La boîte de réception encombrée et la boîte de réception prioritaire apparaissent sous forme d’options dans les paramètres de messagerie de l’utilisateur
    
 **Si vous utilisez Outlook.com :**
  
- Si l’utilisateur a actuellement activé le courrier pêle-mêle : 
    
  - Les paramètres d’encombrement s’affichent
    
- Si la boîte de réception Prioritaire est activée pour l’utilisateur : 
    
  - Les paramètres d’encombrement ne s’affichent pas
    
- Si ni la boîte de réception pêle-mêle ni la boîte de réception prioritaire n’est activée : 
    
  - La boîte de réception encombrée et la boîte de réception prioritaire apparaissent sous forme d’options dans les paramètres de messagerie de l’utilisateur
    
- Si l’utilisateur a activé la boîte de réception Prioritaire à un moment donné dans le passé :
    
  - Les paramètres d’encombrement n’apparaîtront jamais
    
    Sinon 
    
  - Les paramètres d’encombrement s’affichent
    
## <a name="related-content"></a>Contenu associé

[Utiliser l’encombrement pour trier les messages de faible priorité dans Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (article)\
[Utiliser l’encombrement pour trier les messages de faible priorité dans OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (article)\
[Désactiver l’encombrement dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (article)
