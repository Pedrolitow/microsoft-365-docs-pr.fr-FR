---
title: Utiliser des fenêtres contextuelles maigres pour réduire la mémoire utilisée lors de la lecture des messages électroniques
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Cet article contient des informations sur l’utilisation de fenêtres contextuelles allégées pour améliorer les performances de téléchargement des messages dans Outlook sur le web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 40494b43438a491fc200fd19e3015eed58b17493
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096279"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>Utiliser des fenêtres contextuelles maigres pour réduire la mémoire utilisée lors de la lecture des messages électroniques

Cet article contient des informations pour améliorer les performances de téléchargement des messages dans Outlook sur le web. Cet article fait partie de la [planification réseau et de l’optimisation des performances pour Office 365](./network-planning-and-performance.md) projet.
  
En tant **qu’administrateur d’application** Office 365, **administrateur général** ou **administrateur d’utilisateur**, vous pouvez configurer Outlook sur le web pour fournir _des fenêtres contextuelles maigres_, une version plus petite et moins gourmande en mémoire de certains messages électroniques dans Microsoft Edge ou Internet Explorer. Lorsque des fenêtres contextuelles maigres sont configurées pour Outlook sur le web, les composants rendus côté serveur sont chargés pour optimiser les performances.
  
> [!NOTE]
> Depuis mars 2018, les fenêtres contextuelles allégées ne sont pas disponibles pour les messages qui spécifient des restrictions de droits d’utilisation, telles que la Gestion des droits relatifs à l’information (IRM).
  
Ces fonctionnalités continueront de fonctionner dans la fenêtre principale, mais ne sont pas disponibles dans les fenêtres contextuelles maigres :
  
- Compléments Outlook
  
- présence Skype Entreprise
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>Pour configurer des fenêtres contextuelles allégées pour tous les utilisateurs au sein de votre organisation Office 365
  
1. [Connecter à Exchange Online à l’aide de PowerShell à distance](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Exécutez [l’applet de commande Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) avec le paramètre LeanPopoutEnabled comme suit :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  Par exemple, pour activer les fenêtres contextuelles maigres pour tous les utilisateurs de votre organisation :
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  Pour désactiver les fenêtres contextuelles maigres pour tous les utilisateurs de votre organisation :

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
