---
title: Configurer l’encombrement pour votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 832276bd-d024-47b6-a80a-a6b884907a5b
description: 'Découvrez comment activer ou désactiver la fonctionnalité De la fonction De la fonction De pylène pour tous les utilisateurs ou des utilisateurs spécifiques de votre organisation, à l’aide Exchange PowerShell. '
ms.openlocfilehash: 059fb8e626a0b05e0224fc89931453aaae43be0b
ms.sourcegitcommit: a05f61a291eb4595fa9313757a3815b7f217681d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "52706109"
---
# <a name="configure-clutter-for-your-organization"></a>Configurer l’encombrement pour votre organisation

> [!TIP]
> [La boîte de réception Focused](../setup/configure-focused-inbox.md) va remplacer l’encombrement. En savoir plus : Mise à jour sur la boîte de réception [Focused et nos plans pour le clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
En tant qu’administrateur, vous pouvez être dans l’devoir de gérer la fonctionnalité De p Microsoft 365. Pour activer/désactiver la fonctionnalité De l’encombrement pour les utilisateurs de votre organisation, vous devez utiliser Exchange PowerShell. (Les individus peuvent l’activer/le désactiver à l’aide des instructions suivantes : [Désactiver/activer le](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c)clutter dans Outlook .
  
Découvrez comment [utiliser PowerShell avec Exchange Online](/powershell/exchange/exchange-online-powershell) et Connecter pour Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour plus d’informations sur l’utilisation Exchange PowerShell. Vous devez avoir un compte qui dispose au moins du rôle d’administrateur Exchange service et de la possibilité de se connecter à Exchange Online avec PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Activer le clutter à l’Exchange PowerShell

Vous pouvez activer l’encombrement manuellement pour une boîte aux lettres en exécutant la cmdlet [Set-Clutter.](/powershell/module/exchange/set-clutter) Vous pouvez également afficher les paramètres de courrier non plédet pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-Clutter.](/powershell/module/exchange/get-clutter) 
  
Activer le clutter pour un seul utilisateur nommé Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Désactiver l’encombrement à l’Exchange PowerShell

Vous pouvez désactiver l’encombrement manuellement pour une boîte aux lettres en exécutant la cmdlet [Set-Clutter.](/powershell/module/exchange/set-clutter) Vous pouvez également afficher les paramètres **de** courrier non pylasse pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-Clutter.](/powershell/module/exchange/get-clutter) 
  
Dés désactiver le clutter pour un seul utilisateur nommé Allie Bellew :
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Si vous utilisez PowerShell pour créer en bloc vos utilisateurs, vous devrez exécuter [Set-Clutter](/powershell/module/exchange/set-clutter) sur la boîte aux lettres de chaque utilisateur pour gérer le courrier pable. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Quand le commutateur Clutter on/off s’affiche-t-il pour les utilisateurs Outlook sur le web ?
<a name="bkmk_onoff"> </a>

En tant qu’administrateur, vous pouvez ré-activer le clutter à l’aide Exchange PowerShell. Une fois cette mise à jour effectuée, la boîte de réception Focused est désactivée et le clutter est de nouveau actif. 
  
 **Si vous utilisez Outlook sur le web avec un abonnement Microsoft 365 Business Premium :**
  
- Si le clutter est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de l’encombrement s’affichent
    
- Si la boîte de réception Focus est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de l’encombrement n’apparaissent pas
    
- Si ni la boîte de réception De l’encombrement ni la boîte de réception Focused n’est activée : 
    
  - La boîte de réception Courrier non paginé et la boîte de réception Focus apparaissent en tant qu’options dans le courrier électronique de l’Paramètres
    
 **Si vous utilisez Outlook.com :**
  
- Si le clutter est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de l’encombrement s’affichent
    
- Si la boîte de réception Focus est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de l’encombrement n’apparaissent pas
    
- Si ni la boîte de réception De l’encombrement ni la boîte de réception Focused n’est activée : 
    
  - La boîte de réception Courrier non paginé et la boîte de réception Focus apparaissent en tant qu’options dans le courrier électronique de l’Paramètres
    
- Si l’utilisateur a activé la boîte de réception Focus à un moment donné dans le passé :
    
  - Les paramètres de l’encombrement n’apparaissent jamais
    
    Dans le cas contraire, 
    
  - Les paramètres de l’encombrement s’affichent
    
## <a name="related-content"></a>Contenu associé

[Utiliser le clutter pour trier les messages de](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) faible priorité dans Outlook (article)\
[Utiliser le clutter pour trier les messages de](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) faible priorité dans OWA (article)\
[Désactiver l’encombrement dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (article)
