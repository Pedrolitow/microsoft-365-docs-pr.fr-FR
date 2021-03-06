---
title: Gestion de Skype Entreprise Online avec PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 054c16e6-9fd1-4e85-a0e6-81788b8410ea
description: Utilisez PowerShell pour Microsoft 365 pour gérer des stratégies Skype Entreprise Online, des stratégies par utilisateur et des paramètres de réunion.
ms.openlocfilehash: 1992edfb6d1c141c7ed4db22064960873b768865
ms.sourcegitcommit: babbba2b5bf69fd3facde2905ec024b753dcd1b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2021
ms.locfileid: "50514955"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Gestion de Skype Entreprise Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les administrateurs Skype Entreprise Online sont responsables de la gestion des stratégies. Bien que vous puissiez effectuer certaines de ces tâches dans le Centre d’administration Microsoft 365, d’autres sont plus faciles à faire dans PowerShell.

## <a name="before-you-start"></a>Avant de commencer

  > [!Note]
   > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.
   
Installer le [module PowerShell Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-install).


## <a name="connect-using-admin-credentials"></a>Se connecter à l’aide des informations d’identification d’administrateur

1. Ouvrez une fenêtre d’invite de commandes Windows PowerShell et exécutez les commandes suivantes :
    
   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

2. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez le nom et le mot de passe de votre compte d'administrateur, puis sélectionnez **OK**.


## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Se connecter à l’aide d’un compte d’administrateur avec l’authentification multifacteur

1. Ouvrez une fenêtre d’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

2. Lorsque vous y êtes invité, entrez le nom utilisateur de votre compte d'administrateur Skype Entreprise Online.

3. Dans la boîte de dialogue **Vous connecter à votre compte**, tapez votre mot de passe d’administrateur Skype Entreprise Online, puis sélectionnez **Connexion**.

4. Dans la boîte de dialogue **Vous connecter à votre compte** , suivez les instructions d’ajout d’informations d’authentification, telles qu’un code de vérification, puis sélectionnez **Vérifier**.

Pour plus d’informations, consultez :
  
- [Gestion des stratégies Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)
    
- [Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)
    
## <a name="see-also"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Références sur l’applet de commande Skype Entreprise PowerShell](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)
