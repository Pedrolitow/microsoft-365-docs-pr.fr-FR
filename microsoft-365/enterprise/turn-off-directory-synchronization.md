---
title: Désactiver la synchronisation d’annuaires pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
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
ms.openlocfilehash: 5082f89032c17e549f11f8397126f6d059937c48
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077350"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Désactiver la synchronisation d’annuaires pour Microsoft 365
Vous pouvez utiliser PowerShell pour désactiver la synchronisation d’annuaires et convertir vos utilisateurs synchronisés en cloud uniquement. Toutefois, il n’est pas recommandé de désactiver la synchronisation d’annuaires en tant qu’étape de dépannage. Si vous avez besoin d’aide pour résoudre les problèmes de synchronisation d’annuaires, consultez la [rubrique Résolution des problèmes liés à la synchronisation d’annuaires pour Microsoft 365](fix-problems-with-directory-synchronization.md) article. 
  
[Contactez le support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) technique pour les produits d’entreprise si nécessaire.
  
## <a name="turn-off-directory-synchronization"></a>Désactiver la synchronisation d’annuaires  
Pour désactiver la synchronisation d’annuaires :
  
1. Tout d’abord, installez le logiciel requis et connectez-vous à votre abonnement Microsoft 365. Pour obtenir des instructions, consultez [Connecter avec le module Microsoft Azure Active Directory pour Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Utilisez [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) pour désactiver la synchronisation d’annuaires : 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Si vous utilisez cette commande, vous devez attendre 72 heures avant de pouvoir réactiver la synchronisation d’annuaires.
>
