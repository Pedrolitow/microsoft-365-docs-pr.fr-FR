---
title: Configurer le courrier non trié pour votre organisation
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
description: 'Découvrez comment activer ou désactiver la fonctionnalité de courrier non trié pour tous les utilisateurs de votre organisation ou des utilisateurs spécifiques de votre organisation à l’aide d’Exchange PowerShell. '
ms.openlocfilehash: 069cf7569ebb3654e979100291f6754693b24def
ms.sourcegitcommit: 2d59b24b877487f3b84aefdc7b1e200a21009999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "44400135"
---
# <a name="configure-clutter-for-your-organization"></a>Configurer le courrier non trié pour votre organisation

> [!TIP]
> La [boîte de réception prioritaire](../setup/configure-focused-inbox.md) va remplacer le courrier non trié. En savoir plus : [mise à jour sur la boîte de réception prioritaire et nos offres d’encombrement](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448)
  
En tant qu’administrateur, vous pouvez être amené à gérer la fonctionnalité courrier non trié dans Microsoft 365. Pour activer/désactiver la fonctionnalité courrier non trié pour les utilisateurs de votre organisation, vous devez utiliser Exchange PowerShell. (Les utilisateurs peuvent activer/désactiver ces instructions en procédant comme suit : désactivez [/par courrier non trié dans Outlook](https://support.office.com/article/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c.aspx).) 
  
Pour plus d’informations sur l’utilisation d’Exchange PowerShell, consultez [l’aide de PowerShell avec Exchange Online](https://go.microsoft.com/fwlink/?LinkID=402831) et [Connectez-vous à Exchange Online PowerShell](https://go.microsoft.com/fwlink/?LinkID=722415) . Vous devez disposer d’un compte qui dispose au moins du rôle d’administrateur de services Exchange et de la possibilité de se connecter à Exchange Online avec PowerShell. 
  
## <a name="turn-clutter-on-using-exchange-powershell"></a>Activer l’utilisation d’Exchange PowerShell

Vous pouvez activer l’encombrement manuel pour une boîte aux lettres en exécutant la cmdlet [Set-désordre](https://go.microsoft.com/fwlink/?LinkID=834446) . Vous pouvez également afficher les paramètres de courrier non trié pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-désordre](https://go.microsoft.com/fwlink/?LinkID=834759) . 
  
Activer le courrier non trié pour un seul utilisateur nommé allie Bellew
    
`Set-Clutter -Identity "Allie Bellew" -Enable $true`


## <a name="turn-clutter-off-using-exchange-powershell"></a>Désactiver le courrier non trié à l’aide d’Exchange PowerShell

Vous pouvez désactiver l’encombrement manuellement pour une boîte aux lettres en exécutant la cmdlet [Set-désordre](https://go.microsoft.com/fwlink/?LinkID=834446) . Vous pouvez également afficher les paramètres de **courrier non trié** pour les boîtes aux lettres de votre organisation en exécutant la cmdlet [Get-désordre](https://go.microsoft.com/fwlink/?LinkID=834759) . 
  
Désactivez la fonctionnalité courrier non trié pour un seul utilisateur nommé allie Bellew :
    
`Set-Clutter -Identity "Allie Bellew" -Enable $false`

Si vous utilisez PowerShell pour créer vos utilisateurs en bloc, vous devrez exécuter [Set-désordre](https://go.microsoft.com/fwlink/?LinkID=834446) sur la boîte aux lettres de chaque utilisateur pour gérer le courrier non trié. 
  
## <a name="when-does-the-clutter-onoff-switch-appear-to-users-in-outlook-on-the-web"></a>Quand le commutateur de suppression de l’encombrement est-il visible par les utilisateurs dans Outlook sur le Web ?
<a name="bkmk_onoff"> </a>

En tant qu’administrateur, vous pouvez réactiver le courrier non trié à l’aide d’Exchange PowerShell. Une fois cette opération terminée, la boîte de réception prioritaire sera désactivée et l’encombrement sera réactivé. 
  
 **Si vous utilisez Outlook sur le Web avec un abonnement Microsoft 365 Business Premium :**
  
- Si l’utilisateur a activé le courrier inactif : 
    
  - Les paramètres de courrier non trié apparaissent
    
- Si l’utilisateur a actuellement activé la boîte de réception prioritaire : 
    
  - Les paramètres de courrier non trié ne s’affichent pas
    
- Si la boîte de réception prioritaire ou prioritaire n’est pas activée : 
    
  - La boîte de réception prioritaire et la boîte de réception prioritaire apparaissent en tant qu’options dans les paramètres de messagerie de l’utilisateur
    
 **Si vous utilisez Outlook.com :**
  
- Si l’utilisateur a activé le courrier inactif : 
    
  - Les paramètres de courrier non trié apparaissent
    
- Si l’utilisateur a actuellement activé la boîte de réception prioritaire : 
    
  - Les paramètres de courrier non trié ne s’affichent pas
    
- Si la boîte de réception prioritaire ou prioritaire n’est pas activée : 
    
  - La boîte de réception prioritaire et la boîte de réception prioritaire apparaissent en tant qu’options dans les paramètres de messagerie de l’utilisateur
    
- Si la boîte de réception prioritaire est activée par l’utilisateur à un moment donné :
    
  - Les paramètres de courrier non trié ne s’afficheront jamais
    
    Non 
    
  - Les paramètres de courrier non trié apparaissent
    
## <a name="related-articles"></a>Articles connexes
<a name="bkmk_onoff"> </a>

[Utiliser le courrier non trié pour trier les messages à priorité basse dans Outlook](https://support.office.com/article/use-clutter-to-sort-low-priority-messages-in-outlook-7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0)
    
[Utiliser le courrier non trié pour trier les messages à priorité basse dans Outlook Web App](https://support.office.com/article/fe4d64ca-bf73-48f1-91b4-9a659e008bce.aspx)
    
[Désactiver la fonctionnalité courrier non trié dans Outlook](https://support.office.com/article/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c.aspx)
    

