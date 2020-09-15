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
ms.openlocfilehash: d50f35d7d5e81622eb8dfc3bbf8328a8c43e9676
ms.sourcegitcommit: aeb94601a81db3ead8610c2f36cff30eb9fe10e7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2020
ms.locfileid: "47430033"
---
# <a name="manage-skype-for-business-online-with-powershell"></a>Gestion de Skype Entreprise Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Les administrateurs Skype Entreprise Online sont responsables de la gestion des stratégies. Bien que vous puissiez effectuer certaines de ces tâches dans le Centre d’administration Microsoft 365, d’autres sont plus faciles à faire dans PowerShell.

## <a name="before-you-start"></a>Avant de commencer

Téléchargez et installez le [module Skype Entreprise Online Windows PowerShell](https://www.microsoft.com/download/details.aspx?id=39366), puis redémarrez votre ordinateur.


## <a name="connect-using-skype-for-business-online-admin-credentials"></a>Se connecter à l’aide des informations d’identification de l’administrateur Skype Entreprise Online

1. Ouvrez une fenêtre d’invite de commandes Windows PowerShell et exécutez les commandes suivantes :
    
   ```powershell
   Import-Module SkypeOnlineConnector
   $userCredential = Get-Credential
   $sfbSession = New-CsOnlineSession -Credential $userCredential
   Import-PSSession $sfbSession
   ```

2. Dans la boîte de dialogue **Demande d’informations d’identification Windows PowerShell**, saisissez le nom et le mot de passe de votre compte d'administrateur Skype Entreprise Online, puis sélectionnez **OK**.


## <a name="connect-using-an-admin-account-with-multi-factor-authentication"></a>Se connecter à l’aide d’un compte d’administrateur avec l’authentification multifacteur

1. Ouvrez une fenêtre d’invite de commandes Windows PowerShell et exécutez les commandes suivantes :

   ```powershell
   Import-Module SkypeOnlineConnector
   $sfbSession = New-CsOnlineSession
   Import-PSSession $sfbSession
   ```

2. Lorsque vous y êtes invité par la commande **New-CsOnlineSession**, entrez le nom de votre compte d'administrateur Skype Entreprise Online.

3. Dans la boîte de dialogue **Vous connecter à votre compte**, tapez votre mot de passe d’administrateur Skype Entreprise Online, puis sélectionnez **Connexion**.

4. Dans la boîte de dialogue **Vous connecter à votre compte** , suivez les instructions d’ajout d’informations d’authentification, telles qu’un code de vérification, puis sélectionnez **Vérifier**.

Pour plus d’informations, consultez :
  
- [Gestion des stratégies Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-policies-with-microsoft-365-powershell.md)
    
- [Affectation de stratégies Skype Entreprise Online propres à chaque utilisateur avec PowerShell](assign-per-user-skype-for-business-online-policies-with-microsoft-365-powershell.md)
    
## <a name="see-also"></a>Voir aussi

[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Références sur l’applet de commande Skype Entreprise PowerShell](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)
