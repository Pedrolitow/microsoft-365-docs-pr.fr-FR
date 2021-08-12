---
title: Utiliser des fenêtres publicitaires légères pour réduire la mémoire utilisée lors de la lecture des messages électroniques
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Cet article contient des informations sur l’utilisation de fenêtres popout légères pour améliorer les performances de téléchargement des messages Outlook sur le web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 612774478f5b649901d6eae9dccf332299fa53d38331c6ced847ea8d05be104e
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53840766"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Utiliser des fenêtres publicitaires légères pour réduire la mémoire utilisée lors de la lecture des messages électroniques

Cet article contient des informations pour améliorer les performances de téléchargement des messages Outlook sur le web. Cet article fait partie de la planification réseau et de l’optimisation des performances [pour Office 365](./network-planning-and-performance.md) projet.
  
En tant qu’administrateur Office 365 général, vous pouvez configurer Outlook sur le web pour fournir des fenêtres _publicitaires légères,_ une version plus petite et moins intensive en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer. Lorsque des fenêtres popout légères sont configurées pour Outlook sur le web, les composants restituer côté serveur sont chargés afin d’optimiser les performances.
  
> [!NOTE]
> Depuis mars 2018, les fenêtres publicitaires légères ne sont pas disponibles pour les messages qui spécifient des restrictions de droits d’utilisation, tels que la Gestion des droits d’information (IRM).
  
Ces fonctionnalités continueront de fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans les fenêtres popout légères :
  
- Compléments Outlook
  
- Skype Entreprise présence
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Pour configurer des fenêtres pop-out allégées pour tous les utilisateurs au sein de votre Office 365 organisation
  
1. [Connecter à Exchange Online à l’aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Exécutez la cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) avec le paramètre LeanPopoutEnabled comme suit :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Par exemple, pour activer les fenêtres pop-out allégées pour tous les utilisateurs de votre organisation :
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Pour désactiver les fenêtres pop-out allégées pour tous les utilisateurs de votre organisation :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```