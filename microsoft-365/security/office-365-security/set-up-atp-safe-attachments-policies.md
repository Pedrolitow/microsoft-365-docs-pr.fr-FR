---
title: Configurer des stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Découvrez comment définir des stratégies de pièces jointes sécurisées pour protéger votre organisation contre les fichiers malveillants dans le courrier électronique.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5a26d214fe99d0053bf178d7d85a0b526d64f887
ms.sourcegitcommit: cbe8724bd71d1c002395d98f1451c5f578c824f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "49988079"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](office-365-atp.md). Si vous êtes un utilisateur d’accueil à la recherche d’informations sur l’analyse des pièces jointes dans Outlook, voir [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité Pièces jointes sécurisées de Microsoft Defender pour [Office 365](office-365-atp.md) utilise un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques entrants une fois qu’elles ont été analysées par la protection anti-programme malveillant dans [Exchange Online Protection (EOP),](anti-malware-protection.md)mais avant leur remise aux destinataires. Pour plus d’informations, [voir Pièces jointes sécurisées dans Microsoft Defender pour Office 365.](atp-safe-attachments.md)

Il n’existe aucune stratégie de pièces jointes sécurisées intégrée ou par défaut. Pour obtenir l’analyse des pièces jointes des messages électroniques, vous devez créer une ou plusieurs stratégies de pièces jointes sécurisées, comme décrit dans cet article.

Vous pouvez configurer des stratégies de pièces jointes sécurisées dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online, mais avec des abonnements de modules add-on Defender pour Office 365).

Les éléments de base d’une stratégie de pièces jointes sécurisées sont :

- La stratégie de pièces jointes fiables : spécifie les actions pour les détections de programmes malveillants inconnus, s’il faut envoyer des messages avec des pièces jointes à une adresse e-mail spécifiée et s’il faut remettre des messages si l’analyse des pièces jointes fiables ne peut pas se terminer.
- **La règle de pièce jointe sécurisée**: spécifie la priorité et les filtres de destinataires (à qui la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez les polices de pièces jointes sécurisées dans le Centre de sécurité & conformité :

- Lorsque vous créez une stratégie de pièces jointes sécurisées, vous créez en fait une règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie de pièces jointes sécurisées, les paramètres liés au nom, à la priorité, activé ou désactivé, et aux filtres de destinataire modifient la règle de pièce jointe sécurisée. Tous les autres paramètres modifient la stratégie de pièce jointe sécurisée associée.
- Lorsque vous supprimez une stratégie de pièces jointes sécurisées, la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, voir la section Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de pièces [jointes sécurisées](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) plus loin dans cet article.

> [!NOTE]
> Dans la zone des paramètres globaux des paramètres de pièces jointes sécurisées, vous configurez les fonctionnalités qui ne dépendent pas des stratégies de pièces jointes sécurisées. Pour obtenir des instructions, voir Activer les pièces [jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-atp-for-spo-odb-and-teams.md) et les documents sécurisés dans Microsoft [365 E5.](safe-docs.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour aller directement à la page **Pièces jointes sécurisées,** utilisez <https://protection.office.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier et supprimer des stratégies de liens  sécurisés, vous devez être membre des groupes  de rôles  Gestion de l’organisation ou Administrateur de la sécurité dans le Centre de sécurité & conformité et membre du groupe de rôles Gestion de l’organisation dans Exchange Online. 
  - Pour accéder en lecture seule aux stratégies de liens  sécurisés, vous devez être membre des groupes de rôles Lecteur global ou Lecteur sécurité dans le Centre de sécurité & et conformité. 

  Pour plus d’informations, [voir Autorisations](permissions-in-the-security-and-compliance-center.md) dans le Centre de sécurité & conformité et [autorisations dans Exchange Online.](https://docs.microsoft.com/exchange/permissions-exo/permissions-exo)

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir nos paramètres recommandés pour les stratégies de pièces jointes sécurisées, voir [Paramètres des pièces jointes sécurisées.](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings)

- Autorisez jusqu’à 30 minutes pour qu’une stratégie nouvelle ou mise à jour soit appliquée.

## <a name="use-the-security--compliance-center-to-create-safe-attachments-policies"></a>Utiliser le Centre de sécurité & conformité pour créer des stratégies de pièces jointes sécurisées

La création d’une stratégie de pièces jointes sécurisées personnalisée dans le Centre de sécurité & conformité crée la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées associée en utilisant le même nom pour les deux.

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Dans la page **Pièces jointes sécurisées,** cliquez sur **Créer.**

3. **L’Assistant Nouvelle stratégie de pièces jointes sécurisées** s’ouvre. Dans la page **Nom de votre stratégie,** configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Paramètres** qui s’affiche, configurez les paramètres suivants :

   - **Réponse aux programmes malveillants inconnus** pour les pièces jointes sécurisées : sélectionnez l’une des valeurs suivantes :

     - **Off**: En règle générale, nous ne recommandons pas cette valeur.
     - **Moniteur**
     - **Bloc**: il s’agit de la valeur par défaut et de la valeur recommandée dans les stratégies de sécurité standard [et](preset-security-policies.md)stricte.
     - **Replace**
     - **Remise dynamique (fonctionnalité d’aperçu)**

     Ces valeurs sont expliquées dans les paramètres de stratégie de pièces [jointes sécurisées.](atp-safe-attachments.md#safe-attachments-policy-settings)

   - Envoyez la pièce jointe à l’adresse de messagerie suivante : Pour les valeurs d’action **Bloquer,** Surveiller ou **Remplacer,** vous pouvez sélectionner Activer la **redirection** pour envoyer des messages contenant des pièces jointes de programmes malveillants à l’adresse de messagerie interne ou externe spécifiée pour analyse et examen.

     La recommandation pour les paramètres de stratégie Standard et Strict consiste à activer la redirection. Pour plus d’informations, [voir Paramètres des pièces jointes sécurisées.](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings)

   - Appliquez la sélection ci-dessus si l’analyse des programmes **malveillants** pour les pièces jointes arrive à arriver ou si une erreur se produit : l’action spécifiée par la réponse de programmes malveillants inconnus de pièces **jointes sécurisées** est appliquée aux messages même lorsque l’analyse des pièces jointes sécurisées ne peut pas se terminer. Si vous avez sélectionné cette option, sélectionnez toujours **Redirection activée.** Dans le cas contraire, les messages peuvent être perdus.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Appliqué à** qui s’affiche, identifiez les destinataires internes à qui s’applique la stratégie.

   Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   Cliquez **sur Ajouter une condition.** Dans ladown qui s’affiche, sélectionnez une condition sous **Applied si**:

   - **Le destinataire est**: Spécifie une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
   - **Le destinataire est membre de**: Spécifie un ou plusieurs groupes dans votre organisation.
   - **Le domaine du destinataire est** : spécifie les destinataires dans un ou plusieurs domaines configurés et acceptés dans votre organisation.

   Une fois que vous avez sélectionné la condition, une zone « Tout » apparaît dans la zone « **Tout le** monde ».

   - Cliquez dans la zone et faites défiler la liste des valeurs à sélectionner.
   - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez une valeur.
   - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide dans la zone.
   - Pour supprimer des entrées individuelles, cliquez **sur Supprimer** ![ ](../../media/scc-remove-icon.png) l’icône sur la valeur.
   - Pour supprimer la condition entière, cliquez **sur Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) sur la condition.

   Pour ajouter une condition supplémentaire, cliquez sur **Ajouter une condition** et sélectionnez une valeur restante sous Appliqué **si**.

   Pour ajouter des exceptions, cliquez sur **Ajouter une condition** et sélectionnez une exception sous Sauf **si**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Examiner vos paramètres** qui s’affiche, examinez vos paramètres. Vous pouvez cliquer **sur Modifier** sur chaque paramètre pour le modifier.

   Lorsque vous avez terminé, cliquez sur **Terminer**.

## <a name="use-the-security--compliance-center-to-view-safe-attachments-policies"></a>Utiliser le Centre de sécurité & conformité pour afficher les stratégies de pièces jointes sécurisées

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Dans la page **Pièces jointes sécurisées,** sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

   Les détails de la stratégie apparaissent dans un volant

## <a name="use-the-security--compliance-center-to-modify-safe-attachments-policies"></a>Utiliser le Centre de sécurité & conformité pour modifier les stratégies de pièces jointes sécurisées

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Dans la page **Pièces jointes sécurisées,** sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volant des détails de stratégie qui s’affiche, cliquez **sur Modifier la stratégie.**

Les paramètres disponibles dans le volant qui s’affiche sont identiques à ceux décrits dans la section Utiliser le Centre de sécurité & conformité pour créer des stratégies de pièces [jointes sécurisées.](#use-the-security--compliance-center-to-create-safe-attachments-policies)

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-safe-attachments-policies"></a>Activer ou désactiver les stratégies de pièces jointes sécurisées

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Notez la valeur dans la **colonne État** :

   - Déplacer le basculement vers la gauche ![Désactiver la stratégie](../../media/scc-toggle-off.png) pour désactiver la stratégie.

   - Déplacer le basculement vers la droite ![Activer la stratégie](../../media/scc-toggle-on.png) pour activer la stratégie.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Définir la priorité des stratégies de pièces jointes sécurisées

Par défaut, les stratégies de pièces jointes sécurisées ont une priorité qui est basée sur l’ordre dans quoi elles ont été créées (les stratégies les plus nouvelles sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies de pièces jointes sécurisées sont affichées dans  l’ordre de traitement (la première stratégie a la valeur priority 0).

**Remarque**: dans le Centre de sécurité & conformité, vous ne pouvez modifier la priorité de la stratégie de pièces jointes sécurisées qu’une fois que vous l’avez créé. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle de pièce jointe sécurisée (ce qui peut affecter la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Dans la page **Pièces jointes sécurisées,** sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volant des détails de stratégie qui s’affiche, cliquez sur le bouton de priorité disponible.

   - La stratégie pièces jointes sécurisées avec la valeur **de** priorité **0** ne dispose que **du** bouton Diminuer la priorité disponible.

   - La stratégie pièces jointes sécurisées dont la valeur **de** priorité est la plus faible **(par** exemple, 3 ) ne dispose que du bouton **Augmenter** la priorité.

   - Si vous avez au moins trois stratégies de pièces jointes sécurisées,  les stratégies entre les valeurs de priorité les plus élevées et les plus faibles disposent des boutons Augmenter la priorité et Diminuer la priorité. 

4. Cliquez **sur Augmenter la priorité** ou Diminuer la **priorité** pour modifier la **valeur** Priorité.

5. Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-remove-safe-attachments-policies"></a>Utiliser le Centre de sécurité & conformité pour supprimer des stratégies de pièces jointes sécurisées

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**.

2. Dans la page **Pièces jointes sécurisées,** sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans la boîte de dialogue d’avertissement qui s’affiche, cliquez sur Supprimer la **stratégie,** puis cliquez sur **Oui.**

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de pièces jointes sécurisées

Comme décrit précédemment, une stratégie de pièces jointes sécurisées se compose d’une stratégie de pièces jointes sécurisées et d’une règle de pièces jointes sécurisées.

Dans PowerShell, la différence entre les stratégies de pièces jointes sécurisées et les règles de pièces jointes sécurisées est évidente. Vous gérez les stratégies de pièces jointes sécurisées à l’aide des cmdlets **\* -SafeAttachmentPolicy** et vous gérez les règles de pièces jointes sécurisées à l’aide des cmdlets **\* -SafeAttachmentRule.**

- Dans PowerShell, vous créez d’abord la stratégie de pièces jointes sécurisées, puis vous créez la règle de pièce jointe sécurisée qui identifie la stratégie à qui s’applique la règle.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie de pièces jointes sécurisées et de la règle de pièce jointe sécurisée.
- Lorsque vous supprimez une stratégie de pièces jointes sécurisées de PowerShell, la règle de pièce jointe sécurisée correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Utiliser PowerShell pour créer des stratégies de pièces jointes sécurisées

La création d’une stratégie de pièces jointes sécurisées dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de pièces jointes sécurisées.
2. Créez la règle de pièce jointe sécurisée qui spécifie la stratégie de pièces jointes sécurisées à l’application de la règle.

 **Remarques** :

- Vous pouvez créer une règle de pièce jointe sécurisée et lui attribuer une stratégie de pièces jointes sécurisées existante non attachée. Une règle de pièce jointe sécurisée ne peut pas être associée à plusieurs stratégies de pièces jointes sécurisées.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de pièces jointes sécurisées dans PowerShell qui ne sont pas disponibles dans le Centre de sécurité & conformité tant que vous n’avez pas créé la stratégie :
  - Créez la stratégie comme _désactivée_ ( activée sur la `$false` cmdlet **New-SafeAttachmentRule).**
  - Définissez la priorité de la stratégie lors de la création (_Priorité_ ) sur la _\<Number\>_ cmdlet **New-SafeAttachmentRule).**

- Une nouvelle stratégie de pièces jointes sécurisées que vous créez dans PowerShell n’est pas visible dans le Centre de sécurité & conformité tant que vous n’avez pas attribué la stratégie à une règle de pièces jointes sécurisées.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de pièces jointes sécurisées

Pour créer une stratégie de pièces jointes sécurisées, utilisez la syntaxe suivante :

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>]
```

Cet exemple crée une stratégie de pièce jointe sécurisée nommée Contoso All avec les valeurs suivantes :

- Bloquer les messages qui contiennent des programmes malveillants par l’analyse des documents sécurisés (nous n’utilisons pas le paramètre _Action,_ et la valeur par défaut est `Block` ).
- La redirection est activée et les messages qui contiennent des programmes malveillants sont envoyés sec-ops@contoso.com pour analyse et examen.
- Si l’analyse des pièces jointes sécurisées n’est pas disponible ou rencontre des erreurs, ne remettre pas le message (nous n’utilisons pas le paramètre _ActionOnError_ et la valeur par défaut est `$true` ).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle de pièce jointe sécurisée

Pour créer une règle de pièce jointe sécurisée, utilisez la syntaxe suivante :

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Cet exemple crée une règle de pièce jointe sécurisée nommée Contoso All avec les conditions suivantes :

- La règle est associée à la stratégie de pièces jointes sécurisée nommée Contoso All.
- La règle s’applique à tous les destinataires du contoso.com domaine.
- Étant donné que nous n’utilisons pas le _paramètre Priority,_ la priorité par défaut est utilisée.
- La règle est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true` ).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Utiliser PowerShell pour afficher les stratégies de pièces jointes sécurisées

Pour afficher les stratégies de pièces jointes sécurisées existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les stratégies de pièces jointes sécurisées.

```PowerShell
Get-SafeAttachmentPolicy
```

Cet exemple renvoie des informations détaillées sur la stratégie de pièces jointes sécurisée nommée Contoso Executives.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Utiliser PowerShell pour afficher les règles de pièces jointes sécurisées

Pour afficher les règles de pièces jointes sécurisées existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les règles de pièces jointes sécurisées.

```PowerShell
Get-SafeAttachmentRule
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

Cet exemple renvoie des informations détaillées sur la règle de pièce jointe sécurisée nommée Contoso Executives.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Utiliser PowerShell pour modifier des stratégies de pièces jointes sécurisées

Vous ne pouvez pas renommer une stratégie de pièces jointes sécurisées dans PowerShell (la cmdlet **Set-SafeAttachmentPolicy** n’a pas de _paramètre_ Name). Lorsque vous renommez une stratégie de pièces jointes sécurisées dans le Centre de sécurité & conformité, vous renommez uniquement la règle de pièces jointes _sécurisées._

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une stratégie de pièces jointes sécurisées, comme décrit à l’étape 1 : Utiliser [PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) pour créer une section sur la stratégie de pièces jointes sécurisées plus tôt dans cet article.

Pour modifier une stratégie de pièces jointes sécurisées, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentpolicy).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Utiliser PowerShell pour modifier des règles de pièces jointes sécurisées

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de pièce jointe sécurisée dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver des règles de pièces jointes sécurisées existantes, consultez la section suivante.

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à l’étape 2 : Utiliser [PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) pour créer une section de règle de pièce jointe sécurisée plus tôt dans cet article.

Pour modifier une règle de pièce jointe sécurisée, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de pièces jointes sécurisées

L’activation ou la désactivation d’une règle de pièce jointe sécurisée dans PowerShell active ou désactive l’ensemble de la stratégie de pièces jointes sécurisées (la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées affectée).

Pour activer ou désactiver une règle de pièce jointe sécurisée dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de pièce jointe sécurisée nommée Marketing Department.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/enable-safeattachmentrule) et [Disable-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Utiliser PowerShell pour définir la priorité des règles de pièces jointes sécurisées

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de pièce jointe sécurisée dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Remarque**: pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-SafeAttachmentRule.**

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Utiliser PowerShell pour supprimer des stratégies de pièces jointes sécurisées

Lorsque vous utilisez PowerShell pour supprimer une stratégie de pièces jointes sécurisées, la règle de pièce jointe sécurisée correspondante n’est pas supprimée.

Pour supprimer une stratégie de pièces jointes sécurisées dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de pièces jointes sécurisée nommée Marketing Department.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Utiliser PowerShell pour supprimer des règles de pièces jointes sécurisées

Lorsque vous utilisez PowerShell pour supprimer une règle de pièce jointe sécurisée, la stratégie de pièces jointes sécurisées correspondante n’est pas supprimée.

Pour supprimer une règle de pièce jointe sécurisée dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de pièce jointe sécurisée nommée Marketing Department.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SafeAttachmentRule](https://docs.microsoft.com/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement créé, modifié ou supprimé des stratégies de pièces jointes sécurisées, faites l’une des étapes suivantes :

- Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP Safe Attachments**. Vérifiez la liste des stratégies, leurs **valeurs d’état** et leurs **valeurs de** priorité. Pour afficher plus de détails, sélectionnez la stratégie dans la liste et affichez les détails dans le volant.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez \<Name\> les paramètres :

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Pour vérifier que les pièces jointes sécurisées analysent les messages, vérifiez les rapports Defender pour Office 365 disponibles. Pour plus d’informations, voir Afficher les rapports pour Defender pour [Office 365](view-reports-for-atp.md) et Utiliser l’Explorateur dans le Centre de sécurité [& conformité.](threat-explorer.md)
