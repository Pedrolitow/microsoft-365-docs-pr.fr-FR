---
title: Désactiver les exigences de mot de passe fortes pour les utilisateurs
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
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Si vous êtes un administrateur qui gère la stratégie de mot de passe pour une entreprise, une école ou une organisation à but non lucratif, vous pouvez définir des exigences de mot de passe fortes à l’aide d’Azure AD PowerShell.
ms.openlocfilehash: e98c9a3f7b31cbb53d4c853487f4908a6dec72d5
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66010253"
---
# <a name="turn-off-strong-password-requirements-for-users"></a>Désactiver les exigences de mot de passe fortes pour les utilisateurs

Cet article explique comment désactiver les exigences de mot de passe fortes pour vos utilisateurs. Les exigences de mot de passe forts sont activées par défaut dans votre Microsoft 365 pour l’organisation commerciale. Votre organisation peut avoir des exigences pour désactiver les mots de passe forts. Suivez les étapes ci-dessous pour désactiver les exigences de mot de passe forts. Vous devez effectuer ces étapes à l’aide de PowerShell.

## <a name="before-you-begin"></a>Avant de commencer

Cet article est destiné aux personnes qui gèrent la stratégie de mot de passe pour une entreprise, une école ou une organisation à but non lucratif. Pour effectuer ces étapes, vous devez vous connecter avec votre compte d’administrateur Microsoft 365. [Qu’est-ce qu’un compte d’administrateur ?] (Vue d’ensemble de la Centre d'administration Microsoft 365](.. /admin-overview/admin-center-overview.md) Vous devez être [administrateur général ou administrateur de mot de passe](about-admin-roles.md) pour effectuer ces étapes.

Vous devez également vous connecter à Microsoft 365 avec PowerShell.

## <a name="set-strong-passwords"></a>Définir des mots de passe forts

1. [Connexion à Microsoft 365 à l’aide de PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

2. À l’aide de PowerShell, vous pouvez désactiver les exigences de mot de passe fortes pour tous les utilisateurs à l’aide de la commande suivante :

    ```powershell
    Get-MsolUser | Set-MsolUser -StrongPasswordRequired $false

3. You can turn **OFF** strong password requirements for specific users with this command:

    ```powershell
    Set-MsolUser –UserPrincipalName –StrongPasswordRequired  $false
    ```

> [!NOTE]
> UserPrincipalName doit être au format de connexion de style Internet, où le nom d’utilisateur est suivi du signe au début (@) et d’un nom de domaine. Par exemple : user@contoso.com.

## <a name="related-content"></a>Contenu connexe

[Comment se connecter à Microsoft 365 avec PowerShell](/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell)

[Plus d’informations sur les commandes PowerShell MsolUser](/powershell/azure/active-directory/install-adv2)

[Plus d’informations sur la stratégie de mot de passe](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts)
