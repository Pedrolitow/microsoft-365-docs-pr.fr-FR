---
title: Définir une condition de mot de passe fort pour les utilisateurs
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
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez comment définir des exigences de mots de passe forts pour vos utilisateurs, à l’aide de Windows PowerShell.
ms.openlocfilehash: 1634e2f0de2cdd2cac5e1928adbef54457e50716
ms.sourcegitcommit: e17fd18b01d70e6428263c20cbce4b92e2a97765
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "48626142"
---
# <a name="set-strong-password-requirement-for-users"></a>Définir une condition de mot de passe fort pour les utilisateurs

Cet article explique comment définir les exigences de mots de passe forts pour vos utilisateurs. Vous devez effectuer ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article est destiné aux personnes qui gèrent la stratégie de mot de passe pour une entreprise, une école ou une organisation caritative. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../admin-overview/admin-overview.md) Pour effectuer ces étapes, vous devez être [administrateur général ou administrateur de mots de passe](about-admin-roles.md) .

Vous devez également vous connecter à Microsoft 365 avec PowerShell.

## <a name="set-strong-passwords"></a>Définir des mots de passe forts

1. [Connectez-vous à Microsoft 365 avec PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

2. À l’aide de PowerShell, vous pouvez activer les exigences de mot de passe fort pour tous les utilisateurs à l’aide de la commande suivante :

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $true

3. You can turn on strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $true
    ```

> [!NOTE]
> Le userPrincipalName doit être au format de connexion de style Internet, où le nom d’utilisateur est suivi par le signe arobase (@) et un nom de domaine. Par exemple : user@contoso.com.

## <a name="related-content"></a>Contenu connexe

[Comment se connecter à Microsoft 365 avec PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Plus d’informations sur les commandes MsolUser de PowerShell](https://docs.microsoft.com/powershell/module/msonline/set-msoluser?view=azureadps-1.0)

[Plus d’informations sur la stratégie de mot de passe](https://docs.microsoft.com/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)