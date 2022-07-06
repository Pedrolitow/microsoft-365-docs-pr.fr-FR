---
title: Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention
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
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: Utilisez un verrou de conservation avec les stratégies de rétention et les stratégies d’étiquette de conservation pour vous aider à respecter les exigences réglementaires et à vous protéger des administrateurs malveillants.
ms.openlocfilehash: 88f875b201dbfdb633985506aee29acf99e2adb7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622610"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>Utiliser le verrouillage de conservation pour restreindre les modifications apportées aux stratégies de rétention et d’étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> Actuellement, les [étendues de stratégie adaptative ne](retention.md#adaptive-or-static-policy-scopes-for-retention) sont pas en charge.

Le verrouillage de la conservation verrouille une stratégie de rétention ou une étiquette de rétention de sorte que personne, y compris l’administrateur général, ne puisse désactiver la stratégie, la supprimer ou la rendre moins restrictive. Cette configuration peut être nécessaire pour les exigences réglementaires et contribuer à la protection contre les administrateurs malveillants.

Lorsqu’une stratégie de rétention est verrouillée :

- Personne ne peut désactiver ou supprimer la stratégie
- Vous pouvez ajouter des emplacements, mais pas les supprimer
- Vous pouvez prolonger la période de rétention, mais pas la réduire

Lorsqu’une stratégie d’étiquette de rétention est verrouillée :

- Personne ne peut désactiver ou supprimer la stratégie
- Vous pouvez ajouter des emplacements, mais pas les supprimer
- Vous pouvez ajouter des étiquettes, mais pas les supprimer

En bref, vous pouvez augmenter ou prolonger une stratégie verrouillée, mais vous ne pouvez pas la réduire ou la désactiver.

> [!IMPORTANT]
> Avant de verrouiller une stratégie de rétention ou d’étiquette de rétention, il est essentiel de comprendre l’impact et de confirmer qu’il est exigé de votre organisation qu’elle respecte des exigences réglementaires. Par exemple, il peut être nécessaire de répondre à des exigences réglementaires. Les administrateurs ne pourront pas désactiver ou supprimer ces stratégies une fois le verrouillage de conservation appliqué.

Configurez le verrouillage de conservation après avoir créé une [stratégie de rétention](create-retention-policies.md) ou une stratégie d’étiquette de rétention que vous [publiez](create-apply-retention-labels.md) et qui contient uniquement des étiquettes qui [marquent les éléments comme des enregistrements réglementaires](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>Verrouillage d’une stratégie de rétention ou d’étiquette de rétention

Vous devez utiliser PowerShell si vous avez besoin d’utiliser le verrouillage de conservation. Les administrateurs ne pouvant pas désactiver ou supprimer une stratégie de rétention après application d’un verrouillage de conservation, l’activation de cette fonctionnalité n’est pas disponible dans l’interface utilisateur pour se protéger contre une configuration accidentelle.

Toutes les stratégies de rétention incluant une configuration prennent en charge le Verrouillage de conservation. Pour appliquer le verrouillage de conservation à une stratégie d'étiquettes de conservation, celle-ci ne doit contenir que des étiquettes qui marquent les éléments comme des documents réglementaires.

1. [Se connecter à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Recherchez le nom de la stratégie que vous voulez verrouiller en exécutant [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). Par exemple :
    
   ![Liste des stratégies de rétention dans PowerShell](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. Pour placer un verrou de conservation sur votre stratégie, exécutez l’applet de commande [RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) avec le nom de la stratégie et le paramètre *RestrictiveRetention* défini sur « true » :
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    ```
    
    Par exemple :
    
    ![Paramètre de rétention restrictive dans PowerShell](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     Lorsque vous y êtes invité, lisez et accusez réception des restrictions incluses dans cette configuration en entrant **Y** :
    
   ![Invite à confirmer que vous souhaitez verrouiller une stratégie de rétention dans PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

Un verrou de conservation est désormais placé sur la stratégie. Pour confirmer, réexécutez `Get-RetentionCompliancePolicy` , mais indiquez le nom de la stratégie et affichez les paramètres de stratégie :

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

Vous devriez voir que **RestrictiveRetention** est paramétré sur **True**. Par exemple :

![Stratégie verrouillée avec tous les paramètres affichés dans PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>Voir aussi

[Ressources pour vous aider à répondre aux exigences réglementaires en matière de gestion du cycle de vie des données et de gestion des dossiers](retention-regulatory-requirements.md)
