---
title: Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
localization_priority: Priority
search.appverid:
- MOE150
- MET150
description: Utilisez un verrou de conservation avec les stratégies de rétention et les stratégies d’étiquette de conservation pour vous aider à respecter les exigences réglementaires et à vous protéger des administrateurs malveillants.
ms.openlocfilehash: 6f6cfc5bef9b93af08fcc9b703b29facb9a7c576
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920698"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Le verrouillage de la conservation verrouille une stratégie de rétention ou une étiquette de rétention de sorte que personne, y compris l’administrateur général, ne puisse désactiver la stratégie, la supprimer ou la rendre moins restrictive. Cette configuration peut être nécessaire pour les exigences réglementaires et contribuer à la protection contre les administrateurs malveillants.

Lorsqu’une stratégie de rétention est verrouillée :

- Personne ne peut la désactiver
- Vous pouvez ajouter des emplacements, mais pas les supprimer
- Vous pouvez prolonger une période de rétention, mais pas la réduire

En bref, une stratégie verrouillée peut être augmentée ou prolongée, mais elle ne peut pas être réduite ou désactivée.
  
> [!IMPORTANT]
> Avant de verrouiller une stratégie de rétention ou d’étiquette de rétention, il est essentiel de comprendre l’impact et de confirmer qu’il est exigé de votre organisation qu’elle respecte des exigences réglementaires. Par exemple, il peut être nécessaire de répondre à des exigences réglementaires. Les administrateurs ne pourront pas désactiver ou supprimer ces stratégies une fois le verrouillage de conservation appliqué.

Configurez un verrou de conservation une fois que vous avez créé une [stratégie de rétention](create-retention-policies.md) ou une stratégie d’étiquette de rétention que vous [publiez](create-apply-retention-labels.md) ou que vous [appliquez automatiquement](apply-retention-labels-automatically.md). 

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Verrouillage d’une stratégie de rétention ou d’étiquette de rétention

Vous devez utiliser PowerShell si vous avez besoin d’utiliser le verrouillage de conservation. Les administrateurs ne pouvant pas désactiver ou supprimer une stratégie de rétention après application d’un verrouillage de conservation, l’activation de cette fonctionnalité n’est pas disponible dans l’interface utilisateur pour se protéger contre une configuration accidentelle.

Toutes les stratégies de rétention et de prise en charge de la configuration verrouillage de la conservation.

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell).

2. Recherchez le nom de la stratégie que vous voulez verrouiller en exécutant [Get-RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/get-retentioncompliancepolicy). Par exemple :
    
   ![Liste des stratégies de rétention dans PowerShell](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Pour placer un verrou de conservation sur votre stratégie, exécutez l’applet de commande [RetentionCompliancePolicy](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancepolicy) avec le nom de la stratégie et le paramètre *RestrictiveRetention* défini sur « true » :
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" –RestrictiveRetention $true
    ```
    
    Par exemple :
    
    ![Paramètre RestrictiveRetention dans PowerShell](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Lorsque vous y êtes invité, lisez et accusez réception des restrictions incluses dans cette configuration en entrant **Y** :
    
   ![Invite à confirmer que vous souhaitez verrouiller une stratégie de rétention dans PowerShell](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Un verrou de conservation est désormais placé sur la stratégie. Pour confirmer, réexécutez `Get-RetentionCompliancePolicy` , mais indiquez le nom de la stratégie et affichez les paramètres de stratégie :

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Vous devriez voir que **RestrictiveRetention** est paramétré sur **True**. Par exemple :

![Stratégie verrouillée avec tous les paramètres affichés dans PowerShell](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Voir aussi

[Ressources pour vous aider à respecter les réglementations en matière de gouvernance des informations et de gestion des enregistrements](retention-regulatory-requirements.md)
