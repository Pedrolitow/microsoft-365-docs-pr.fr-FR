---
title: Gestion des stratégies Skype Entreprise Online avec PowerShell
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Résumé : Utilisez PowerShell pour gérer vos propriétés Skype Entreprise compte d’utilisateur En ligne avec des stratégies.'
ms.openlocfilehash: 674ea6daba498279537f7c302f4bf4d791ee00f5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60189080"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Gestion des stratégies Skype Entreprise Online avec PowerShell

*Cet article est valable pour Microsoft 365 Entreprise et Office 365 Entreprise.*

Pour gérer de nombreuses propriétés du compte d’utilisateur Skype Entreprise Online, vous devez les spécifier en tant que propriétés de stratégies avec PowerShell pour Microsoft 365.
  
## <a name="before-you-begin"></a>Avant de commencer

Suivez ces instructions pour exécuter les commandes (sautez les étapes que vous avez déjà effectuées) :

  > [!Note]
  > Le connecteur Skype Entreprise Online fait actuellement partie du dernier module PowerShell Teams. Si vous utilisez la version publique la plus récente de PowerShell Teams, vous n’avez pas besoin d’installer le connecteur Skype Entreprise Online.

1. Installer le [module PowerShell Teams](/microsoftteams/teams-powershell-install).
    
2. Ouvrez l’invite de commandes Windows PowerShell et exécutez les commandes suivantes : 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   Lorsque vous y êtes invité, entrez le nom utilisateur et le mot de passe de votre compte d'administrateur Skype Entreprise Online.
    
## <a name="manage-user-account-policies"></a>Gestion de stratégies de compte d’utilisateur

De nombreuses propriétés de compte d'utilisateur Skype Entreprise Online sont configurées à l'aide de stratégies. Les stratégies sont simplement des ensembles de paramètres qui peuvent être appliqués à un ou plusieurs utilisateurs. Pour voir comment la stratégie a été configurée, vous pouvez exécuter cet exemple de commande, qui porte sur la stratégie FederationAndPICDefault :
  
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

Dans cet exemple, les valeurs au sein de cette stratégie déterminent ce qu'un utilisateur peut ou ne peut pas faire en matière de communication avec des utilisateurs fédérés. Par exemple, la propriété EnableOutsideAccess doit être définie sur True pour qu'un utilisateur puisse communiquer avec des personnes extérieures à l'organisation. Notez que cette propriété n’apparaît pas dans la Centre d'administration Microsoft 365. Elle est automatiquement définie sur True ou False en fonction des autres sélections que vous effectuez. Les deux autres propriétés qui vous intéressent sont les suivantes :
  
- **EnableFederationAccess** indique si l'utilisateur peut communiquer avec des personnes à partir de domaines fédérés.
    
- **EnablePublicCloudAccess** indique si l'utilisateur peut communiquer avec des utilisateurs Windows Live.
    
Ainsi, vous ne modifiez pas directement les propriétés liées à la fédération sur les comptes d'utilisateur (par exemple, **Set-CsUser -EnableFederationAccess $True**). Vous attribuez à un compte une stratégie d'accès externe où les valeurs de propriété souhaitées sont déjà préconfigurées. Pour qu'un utilisateur puisse communiquer avec des utilisateurs fédérés et des utilisateurs Windows Live, une stratégie permettant ces types de communication doit être attribuée à son compte.
  
Pour savoir si quelqu’un peut communiquer avec des utilisateurs externes à l’organisation, vous devez :
  
- déterminer la stratégie d’accès externe qui a été attribuée à cet utilisateur ;
    
- déterminer les capacités autorisées ou non par cette stratégie.
    
Pour ce faire, vous pouvez par exemple utiliser la commande suivante :
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Cette commande trouve la stratégie attribuée à l’utilisateur, puis les fonctionnalités activées ou désactivées dans cette stratégie.
  
Pour gérer Skype Entreprise stratégies En ligne avec PowerShell, consultez les cmdlets pour :

- [Stratégie du client](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Stratégie de conférence](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Stratégie mobile](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Stratégie de messagerie vocale en ligne](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Stratégie de routage des voix](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Un plan de numérotation Skype Entreprise Online ne diffère d'une stratégie que par le nom. Le nom « plan de numérotation » a été préféré à « stratégie de numérotation » (par exemple) afin d'assurer la compatibilité descendante avec Office Communications Server et Exchange. 
  
Par exemple, pour voir toutes les stratégies de voix que vous pouvez utiliser, il suffit d’exécuter la commande suivante :
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Cette action renvoie la liste de toutes les stratégies de voix dont vous disposez. Toutefois, gardez à l'esprit que toutes les stratégies ne peuvent pas être attribuées à tous les utilisateurs, en raison des diverses restrictions impliquant la gestion des licences et l'emplacement géographique (le dénommé « [emplacement d'utilisation](/previous-versions/azure/dn194136(v=azure.100)) »). Si vous souhaitez connaître les stratégies d'accès externe et les stratégies de conférence qui peuvent être attribuées à un utilisateur particulier, utilisez des commandes semblables à celles-ci : 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

Le paramètre ApplicableTo limite les données renvoyées aux stratégies qui peuvent être attribuées à l’utilisateur indiqué (par exemple, Alex Darrow). Selon les restrictions liées à la gestion des licences et à l’emplacement d’utilisation, cela pourrait représenter un sous-ensemble de toutes les stratégies disponibles. 
  
Dans certains cas, les propriétés des stratégies ne sont pas utilisées avec les Microsoft 365, tandis que d’autres ne peuvent être gérées que par le personnel du support technique Microsoft. 
  
Avec Skype Entreprise Online, les utilisateurs doivent être gérés par une stratégie ou une autre. Si une propriété portant sur les stratégies est vide, cela signifie que l'utilisateur en question est géré par une stratégie globale, c'est-à-dire une stratégie qui est appliquée automatiquement à un utilisateur, sauf si une stratégie individuelle est appliquée à cet utilisateur. Si aucune stratégie de client n'est répertoriée pour un compte d'utilisateur, cela signifie qu'il est géré par la stratégie globale. Vous pouvez déterminer la stratégie de client globale avec cette commande :
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Voir aussi

[Gestion de Skype Entreprise Online avec PowerShell](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[Gestion de Microsoft 365 à l’aide de PowerShell](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Prise en main de PowerShell pour Microsoft 365](getting-started-with-microsoft-365-powershell.md)