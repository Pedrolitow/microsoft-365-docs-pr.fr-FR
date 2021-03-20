---
title: Désactiver les exigences de mot de passe strictes pour les utilisateurs
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
description: Découvrez comment définir des exigences de mot de passe strictes pour vos utilisateurs, à l’aide Windows PowerShell.
ms.openlocfilehash: e2300e3c94de53cd04d0c1726538fdb8a86a1ccf
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50903535"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Désactiver les exigences de mot de passe strictes pour les utilisateurs

Cet article explique comment désactiver les exigences de mot de passe strictes pour vos utilisateurs. Des exigences de mot de passe strictes sont désactivées par défaut dans votre organisation Microsoft 365 pour les entreprises. Votre organisation peut avoir besoin de désactiver des mots de passe forts. Suivez les étapes ci-dessous pour désactiver les exigences de mot de passe strictes. Vous devez effectuer ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article est réservé aux personnes qui gèrent la stratégie de mot de passe pour une entreprise, une école ou une association. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?](../admin-overview/admin-overview.md) Vous devez être administrateur général ou administrateur de [mot de](about-admin-roles.md) passe pour effectuer ces étapes.

Vous devez également vous connecter à Microsoft 365 avec PowerShell.

## <a name="set-strong-passwords"></a>Définir des mots de passe forts

1. [Connectez-vous à Microsoft 365 avec PowerShell.](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

2. À l’aide de PowerShell, vous pouvez désactiver les exigences de mot de passe strictes pour tous les utilisateurs à l’aide de la commande suivante :

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn of strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> L’userPrincipalName doit être au format de connexion de style Internet où le nom d’utilisateur est suivi du signe at (@) et d’un nom de domaine. Par exemple : user@contoso.com.

## <a name="related-content"></a>Contenu connexe

[Comment se connecter à Microsoft 365 avec PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Plus d’informations sur les commandes PowerShell MsolUser](/powershell/module/msonline/set-msoluser?view=azureadps-1.0)

[Plus d’informations sur la stratégie de mot de passe](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)