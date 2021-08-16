---
title: Désactiver la synchronisation d’annuaires pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Dans cet article, recherchez des informations sur l’utilisation de PowerShell pour désactiver la synchronisation d’annuaires pour Microsoft 365.
ms.openlocfilehash: 28e0a83bba1a63a7cd1d2f449b9bf3ba34e4862a
ms.sourcegitcommit: e269371de759a1a747c9f292775463aa11415f25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2021
ms.locfileid: "58354199"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Désactiver la synchronisation d’annuaires pour Microsoft 365
Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires et convertir vos utilisateurs synchronisés en nuage uniquement. Toutefois, il n’est pas recommandé de désactiver la synchronisation d’annuaires en tant qu’étape de dépannage. Si vous avez besoin d’aide pour résoudre les problèmes de synchronisation d’annuaires, consultez l’article résolution des problèmes liés à la synchronisation [d’annuaires](fix-problems-with-directory-synchronization.md) Microsoft 365'article. 
  
[Contactez le support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) technique pour les produits d’entreprise si nécessaire.
  
## <a name="turn-off-directory-synchronization"></a>Désactiver la synchronisation d’annuaires  
Pour désactiver la synchronisation d’annuaires :
  
1. Tout d’abord, installez le logiciel requis et connectez-vous à Microsoft 365 abonnement. Pour obtenir des instructions, [voir Connecter avec le module Microsoft Azure Active Directory pour Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Utilisez [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) pour désactiver la synchronisation d’annuaires : 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Si vous utilisez cette commande, vous devez patienter 72 heures avant de pouvoir activer de nouveau la synchronisation d’annuaires.
>
