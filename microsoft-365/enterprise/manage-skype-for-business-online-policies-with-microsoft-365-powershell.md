---
title: Gestion des stratégies Skype Entreprise Online avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Résumé : Utilisez PowerShell pour gérer vos propriétés de compte d’utilisateur Skype Entreprise Online avec des stratégies.'
ms.openlocfilehash: 1ea469ec5477ea90fc6e8086360db724eddf3863
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185356"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Gestion des stratégies Skype Entreprise Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour gérer de nombreuses propriétés de compte d’utilisateur pour Skype Entreprise Online, vous devez les spécifier comme propriétés des stratégies avec PowerShell pour Microsoft 365.
  
## <a name="before-you-begin"></a>Avant de commencer

Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :

  > [!Note]
  > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.

1. Installer le [module PowerShell Teams](/microsoftteams/teams-powershell-install).
    
2. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.
    
## <a name="manage-user-account-policies"></a>Gestion de stratégies de compte d’utilisateur

Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Vous devriez obtenir en retour un élément semblable au suivant :
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

Dans cet exemple, les valeurs au sein de cette stratégie déterminent ce qu'un utilisateur peut ou ne peut pas faire en matière de communication avec des utilisateurs fédérés. Par exemple, la propriété EnableOutsideAccess doit être définie sur True pour qu'un utilisateur puisse communiquer avec des personnes extérieures à l'organisation. Notez que cette propriété n’apparaît pas dans le Centre d'administration Microsoft 365. Elle est automatiquement définie sur True ou False en fonction des autres sélections que vous effectuez. Les deux autres propriétés qui vous intéressent sont les suivantes :
  
- **EnableFederationAccess** indique si l'utilisateur peut communiquer avec des personnes à partir de domaines fédérés.
    
- **EnablePublicCloudAccess** indique si l'utilisateur peut communiquer avec des utilisateurs Windows Live.
    
Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.
  
Pour savoir si quelqu’un peut communiquer avec des utilisateurs externes à l’organisation, vous devez :
  
- déterminer la stratégie d’accès externe qui a été attribuée à cet utilisateur ;
    
- déterminer les capacités autorisées ou non par cette stratégie.
    
Pour ce faire, vous pouvez par exemple utiliser la commande suivante :
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Cette commande trouve la stratégie attribuée à l’utilisateur, puis les fonctionnalités activées ou désactivées dans cette stratégie.
  
Pour gérer Skype Entreprise stratégies en ligne avec PowerShell, consultez les applets de commande pour :

- [Stratégie du client](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Stratégie de conférence](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Stratégie mobile](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Stratégie de messagerie vocale en ligne](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Stratégie de routage vocal](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange. 
  
Par exemple, pour voir toutes les stratégies de voix que vous pouvez utiliser, il suffit d’exécuter la commande suivante :
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](/previous-versions/azure/dn194136(v=azure.100)).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies. 
  
Dans certains cas, les propriétés des stratégies ne sont pas utilisées avec Microsoft 365, tandis que d’autres ne peuvent être gérées que par le personnel du support technique Microsoft. 
  
With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Voir aussi

[Gestion de Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)