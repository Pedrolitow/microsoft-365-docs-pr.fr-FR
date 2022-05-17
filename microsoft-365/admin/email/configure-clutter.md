---
title: Configurer courrier pêle-mêle pour votre organisation
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
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
description: 'Découvrez comment activer ou désactiver la fonctionnalité Courrier pêle-mêle pour tous les utilisateurs ou certains utilisateurs de votre organisation, à l’aide de Exchange PowerShell. '
ms.openlocfilehash: 64c11b2a8bbce3747727c458a4427f5c0e1b135b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437192"
---
# <a name="configure-microsoft-365-clutter-for-your-organization"></a>Configurer Microsoft 365 Courrier pêle-mêle pour votre organisation

> [!TIP]
> [La boîte de réception prioritaire](../setup/configure-focused-inbox.md) va remplacer courrier pêle-mêle. En savoir plus : [Mise à jour de la boîte de réception Prioritaire et de nos plans pour courrier pêle-mêle](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
En tant qu’administrateur, vous devrez peut-être gérer la fonctionnalité Courrier pêle-mêle dans Microsoft 365. Pour activer/désactiver la fonctionnalité Courrier pêle-mêle pour les utilisateurs de votre organisation, vous devez utiliser Exchange PowerShell. (Les personnes peuvent l’activer/la désactiver à l’aide des instructions suivantes : [Désactiver/activer le courrier pêle-mêle dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c).
  
Pour plus d’informations sur l’utilisation de Exchange PowerShell, consultez [l’utilisation de PowerShell avec Exchange Online](/powershell/exchange/exchange-online-powershell) et [Connecter pour Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Vous devez disposer d’un compte qui a au moins le rôle d’administrateur de service Exchange et la possibilité de se connecter à Exchange Online avec PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Activer le courrier pêle-mêle à l’aide de Exchange PowerShell

Vous pouvez activer le courrier pêle-mêle manuellement pour une boîte aux lettres en exécutant l’applet [de commande Set-Clutter](/powershell/module/exchange/set-clutter) . Vous pouvez également afficher les paramètres de courrier pêle-mêle pour les boîtes aux lettres de votre organisation en exécutant l’applet [de commande Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Activer Courrier pêle-mêle pour un seul utilisateur nommé Allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Désactiver le courrier pêle-mêle à l’aide de Exchange PowerShell

Vous pouvez désactiver le courrier pêle-mêle manuellement pour une boîte aux lettres en exécutant l’applet [de commande Set-Clutter](/powershell/module/exchange/set-clutter) . Vous pouvez également afficher les paramètres **de courrier pêle-mêle** pour les boîtes aux lettres de votre organisation en exécutant l’applet [de commande Get-Clutter](/powershell/module/exchange/get-clutter) . 
  
Désactivez Courrier pêle-mêle pour un seul utilisateur nommé Allie Bellew :
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Si vous utilisez PowerShell pour créer vos utilisateurs en bloc, vous devez exécuter [Set-Clutter](/powershell/module/exchange/set-clutter) sur la boîte aux lettres de chaque utilisateur pour gérer le courrier pêle-mêle. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Quand le commutateur pêle-mêle s’affiche-t-il aux utilisateurs dans Outlook sur le web ?
<a name="bkmk_onoff"> </a>

En tant qu’administrateur, vous pouvez réactiver le courrier pêle-mêle à l’aide de Exchange PowerShell. Une fois cette opération effectuée, la boîte de réception Prioritaire est désactivée et le courrier pêle-mêle est à nouveau actif. 
  
 **Si vous utilisez Outlook sur le web avec un abonnement Microsoft 365 Business Premium :**
  
- Si le courrier pêle-mêle est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de courrier pêle-mêle s’affichent
    
- Si la boîte de réception Prioritaire est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de courrier pêle-mêle ne s’affichent pas
    
- Si aucune boîte de réception pêle-mêle ou Boîte de réception prioritaire n’est activée : 
    
  - La boîte de réception pêle-mêle et la boîte de réception prioritaire s’affichent sous forme d’options dans la Paramètres courrier de l’utilisateur
    
 **Si vous utilisez Outlook.com :**
  
- Si le courrier pêle-mêle est actuellement activé pour l’utilisateur : 
    
  - Les paramètres de courrier pêle-mêle s’affichent
    
- Si la boîte de réception Prioritaire est actuellement activée pour l’utilisateur : 
    
  - Les paramètres de courrier pêle-mêle ne s’affichent pas
    
- Si aucune boîte de réception pêle-mêle ou Boîte de réception prioritaire n’est activée : 
    
  - La boîte de réception pêle-mêle et la boîte de réception prioritaire s’affichent sous forme d’options dans la Paramètres courrier de l’utilisateur
    
- Si l’utilisateur a activé la boîte de réception Prioritaire à un moment donné dans le passé :
    
  - Les paramètres de courrier pêle-mêle ne s’affichent jamais
    
    Sinon 
    
  - Les paramètres de courrier pêle-mêle s’affichent
    
## <a name="related-content"></a>Contenu connexe

[Utiliser le courrier pêle-mêle pour trier les messages de faible priorité dans Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0) (article)\
[Utiliser courrier pêle-mêle pour trier les messages de faible priorité dans OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce) (article)\
[Désactiver le courrier pêle-mêle dans Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c) (article)
