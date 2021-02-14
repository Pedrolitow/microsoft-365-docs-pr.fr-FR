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
description: 'Découvrez comment activer ou désactiver la fonctionnalité De la fonction Denterr, pour tous les utilisateurs ou des utilisateurs spécifiques de votre organisation, à l’aide d’Exchange PowerShell. '
ms.openlocfilehash: 67267b0865dfcfd6c0ba66d59ce1d0d111d59325
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780276"
---
# <a name="configure-clutter-for-your-organization"></a>Configurer l’encombrement pour votre organisation

> [!TIP]
> [La boîte de réception Focused](../setup/configure-focused-inbox.md) remplacera le clutter. En savoir plus : Mise à jour de la boîte de réception Focus [et de nos plans pour le clutter](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
En tant qu’administrateur, vous pouvez être dans l’devoir de gérer la fonctionnalité De la pylème dans Microsoft 365. Pour activer/désactiver la fonctionnalité De l’encombrement pour les utilisateurs de votre organisation, vous devez utiliser Exchange PowerShell. (Les individus peuvent l’activer/le désactiver à l’aide des instructions suivantes : Désactiver/activer la fonction De [la pylasse dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Consultez [l’utilisation de PowerShell avec Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) et [connectez-vous](https://go.microsoft.com/fwlink/?LinkID=722415) à Exchange Online PowerShell pour plus d’informations sur l’utilisation d’Exchange PowerShell. Vous devez avoir un compte ayant au moins le rôle d’administrateur du service Exchange et la possibilité de vous connecter à Exchange Online avec PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Activer le clutter à l’aide d’Exchange PowerShell

Vous pouvez activer l’encombrement manuellement pour une boîte aux lettres en exécutant la cmdlet [Set-Clutter.](https://go.microsoft.com/fwlink/?LinkID=834446) Vous pouvez également afficher les paramètres de courrier non pylasse pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-Clutter.](https://go.microsoft.com/fwlink/?LinkID=834759) 
  
Activer le clutter pour un seul utilisateur nommé Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Désactiver l’encombrement à l’aide d’Exchange PowerShell

Vous pouvez désactiver l’encombrement manuellement pour une boîte aux lettres en exécutant la cmdlet [Set-Clutter.](https://go.microsoft.com/fwlink/?LinkID=834446) Vous pouvez également afficher les paramètres **de** courrier non plédet pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-Clutter.](https://go.microsoft.com/fwlink/?LinkID=834759) 
  
Dés désactiver le clutter pour un seul utilisateur nommé Allie Bellew :
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Si vous utilisez PowerShell pour créer en bloc vos utilisateurs, vous devrez exécuter [Set-Clutter](https://go.microsoft.com/fwlink/?LinkID=834446) sur la boîte aux lettres de chaque utilisateur pour gérer le courrier pable. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Quand le commutateur Clutter on/off s’affiche-t-il pour les utilisateurs dans Outlook sur le web ?
<a name="bkmk_onoff"> </a>

En tant qu’administrateur, vous pouvez ré-activer l’encombrement à l’aide d’Exchange PowerShell. Une fois cette mise à jour effectuée, la boîte de réception Focused est désactivée et le clutter est de nouveau actif. 
  
 **Si vous utilisez Outlook sur le web avec un abonnement Microsoft 365 Business Premium :**
  
- Si le clutter est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de l’encombrement apparaissent
    
- Si la boîte de réception Focus est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de l’encombrement n’apparaissent pas
    
- Si ni la boîte de réception De l’encombrement ni la boîte de réception Focused n’est activée : 
    
  - La boîte de réception Courrier non courrier et La boîte de réception Focused apparaissent en tant qu’options dans les paramètres de messagerie de l’utilisateur
    
 **Si vous utilisez Outlook.com :**
  
- Si le clutter est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de l’encombrement s’affichent
    
- Si la boîte de réception Focus est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de l’encombrement n’apparaissent pas
    
- Si ni la boîte de réception De l’encombrement, ni la boîte de réception Focused n’est activée : 
    
  - La boîte de réception Courrier non courrier et La boîte de réception Focused apparaissent en tant qu’options dans les paramètres de messagerie de l’utilisateur
    
- Si l’utilisateur a activé la boîte de réception Focused à un moment donné dans le passé :
    
  - Les paramètres de l’encombrement n’apparaîtront jamais
    
    Dans le cas contraire, 
    
  - Les paramètres de l’encombrement s’affichent
    
## <a name="related-articles"></a>Articles connexes
<a name="bkmk_onoff"> </a>

[Utiliser le clutter pour trier les messages de faible priorité dans Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0)
    
[Utiliser le clutter pour trier les messages de faible priorité dans OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce)
    
[Désactiver l’encombrement dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c)
    

