---
title: Configurer des stratégies de pièces jointes fiables dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Découvrez comment définir des stratégies de pièces jointes fiables afin de protéger votre organisation contre les fichiers malveillants par courrier électronique.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a14f5a22795fc08b76165466d8e44ee38d8a2d81
ms.sourcegitcommit: d81c7cea85af6ad5fef81d3c930514a51464368c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49572636"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies de pièces jointes fiables dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Cet article est destiné aux clients professionnels qui disposent [de Microsoft Defender pour Office 365](office-365-atp.md). Si vous êtes un utilisateur à domicile et que vous recherchez des informations sur l’analyse des pièces jointes dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité pièces jointes fiables est une fonctionnalité de [Microsoft Defender pour Office 365](office-365-atp.md) qui utilise un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques entrants après qu’ils ont été analysés par la protection contre les [programmes malveillants dans Exchange Online Protection (EoP)](anti-malware-protection.md), mais avant remise aux destinataires. Pour plus d’informations, consultez la rubrique [pièces jointes fiables dans Microsoft Defender pour Office 365](atp-safe-attachments.md).

Il n’existe pas de stratégie de pièces jointes approuvées ou par défaut. Pour obtenir des pièces jointes fiables sur l’analyse des pièces jointes des messages électroniques, vous devez créer une ou plusieurs stratégies de pièces jointes fiables, comme décrit dans cet article.

Vous pouvez configurer des stratégies de pièces jointes fiables dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange autonome EOP PowerShell pour les organisations sans boîtes aux lettres Exchange Online, mais avec les abonnements de compléments pour Office 365.

Les éléments de base d’une stratégie de pièces jointes fiables sont les suivants :

- **Stratégie de pièces jointes approuvées**: spécifie les actions pour les détections de programmes malveillants inconnues, l’envoi de messages avec des pièces jointes de programmes malveillants à une adresse e-mail spécifique et la remise des messages si l’analyse des pièces jointes fiables ne peut pas aboutir.
- **La règle de pièce jointe fiable**: spécifie la priorité et les filtres de destinataire (auxquels la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies de pièces jointes fiables dans le centre de sécurité & conformité :

- Lorsque vous créez une stratégie de pièces jointes approuvées, vous créez en réalité une règle de pièces jointes fiables et la stratégie de pièces jointes fiables associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie de pièces jointes approuvées, les paramètres associés aux filtres nom, priorité, activé ou désactivé et filtre de destinataires modifient la règle de pièce jointe fiable. Tous les autres paramètres modifient la stratégie de pièces jointes fiables associée.
- Lorsque vous supprimez une stratégie de pièces jointes fiables, la règle de pièce jointe fiable et la stratégie de pièces jointes fiables associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, reportez-vous à la section [utiliser Exchange Online PowerShell or standalone EOP PowerShell pour configurer les stratégies de pièces jointes approuvées](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) plus loin dans cet article.

> [!NOTE]
> Dans la zone Paramètres globaux des pièces jointes approuvées, vous configurez des fonctionnalités qui ne dépendent pas des stratégies de pièces jointes approuvées. Pour obtenir des instructions, voir Activer la protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md) et [documents approuvés dans Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **pièces jointes approuvées** , utilisez <https://protection.office.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Avant de pouvoir effectuer les procédures décrites dans cet article, vous devez disposer d’autorisations dans le centre de sécurité & Compliance Center :
  - Pour créer, modifier et supprimer des stratégies de pièces jointes approuvées, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** .
  - Pour un accès en lecture seule aux stratégies de pièces jointes approuvées, vous devez être membre des groupes de rôles **lecteur global** ou **lecteur de sécurité** .

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarques**:

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le centre d’administration 365 de Microsoft donne aux utilisateurs les autorisations requises dans le centre de sécurité & conformité _et_ des autorisations pour d’autres fonctionnalités de Microsoft 365. Si vous souhaitez en savoir plus, veuillez consulter la page [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).
  - Le groupe de rôles gestion de l' **Organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) offre également un accès en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies de pièces jointes approuvées, consultez la rubrique [Safe Attachments Settings](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings).

- Autoriser jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

## <a name="use-the-security--compliance-center-to-create-safe-attachments-policies"></a>Utiliser le centre de sécurité & conformité pour créer des stratégies de pièces jointes fiables

La création d’une stratégie de pièces jointes fiables personnalisée dans le centre de sécurité & conformité crée la règle de pièce jointe fiable et la stratégie de pièces jointes fiables associée en utilisant le même nom pour les deux.

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Dans la page **pièces jointes approuvées** , cliquez sur **créer**.

3. L’Assistant **nouvelle stratégie de pièces jointes fiables** s’ouvre. Sur la page **nommer votre stratégie** , configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Sur la page **paramètres** qui s’affiche, configurez les paramètres suivants :

   - **Pièces jointes approuvées réponse aux programmes malveillants inconnus**: sélectionnez l’une des valeurs suivantes :

     - **Off**: en règle générale, nous ne recommandons pas cette valeur.
     - **Moniteur**
     - **Block**: il s’agit de la valeur par défaut et de la valeur recommandée dans les stratégies de sécurité standard et rigoureuses [prédéfinies](preset-security-policies.md).
     - **Replace**
     - **Remise dynamique (fonctionnalité aperçu)**

     Ces valeurs sont expliquées dans [paramètres de stratégie de pièces jointes approuvées](atp-safe-attachments.md#safe-attachments-policy-settings).

   - **Envoyez la pièce jointe à l’adresse de messagerie suivante**: pour les valeurs d’action **bloquer**, **surveiller** ou **remplacer**, vous pouvez sélectionner **activer la redirection** pour envoyer des messages contenant des pièces jointes de programmes malveillants à l’adresse de messagerie interne ou externe spécifiée à des fins d’analyse et d’enquête.

     La recommandation pour les paramètres de stratégie standard et strict est d’activer la redirection. Pour plus d’informations, consultez la rubrique [paramètres de pièces jointes fiables](recommended-settings-for-eop-and-office365-atp.md#safe-attachments-settings).

   - **Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit**: l’action spécifiée par les **pièces jointes approuvées une réponse inconnue aux programmes malveillants** est prise sur les messages, même lorsque l’analyse Sélectionnez toujours cette option si vous sélectionnez **Rediriger activé**. Sinon, les messages peuvent être perdus.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur la page **appliqué à** qui s’affiche, identifiez les destinataires internes auxquels s’applique la stratégie.

   Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   Cliquez sur **Ajouter une condition**. Dans la liste déroulante qui apparaît, sélectionnez une condition sous **appliqué si**:

   - **Le destinataire est**: spécifie une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
   - **Le destinataire est membre de**: spécifie un ou plusieurs groupes dans votre organisation.
   - **Le domaine du destinataire est** : spécifie les destinataires dans un ou plusieurs domaines configurés et acceptés dans votre organisation.

   Une fois que vous avez sélectionné la condition, une liste déroulante correspondante apparaît avec **une case à** cocher.

   - Cliquez dans la zone et faites défiler la liste des valeurs à sélectionner.
   - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez une valeur.
   - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide de la zone.
   - Pour supprimer des entrées individuelles, cliquez sur **supprimer** ![ ](../../media/scc-remove-icon.png) l’icône de suppression sur la valeur.
   - Pour supprimer l’ensemble de la condition, cliquez sur **supprimer** l' ![ icône Supprimer ](../../media/scc-remove-icon.png) dans la condition.

   Pour ajouter une condition supplémentaire, cliquez sur **Ajouter une condition** et sélectionnez une valeur restante sous **appliqué**.

   Pour ajouter des exceptions, cliquez sur **Ajouter une condition** et sélectionnez une exception sous **sauf si**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Sur la page **vérifier vos paramètres** qui s’affiche, vérifiez vos paramètres. Vous pouvez cliquer sur **modifier** sur chaque paramètre pour le modifier.

   Lorsque vous avez terminé, cliquez sur **Terminer**.

## <a name="use-the-security--compliance-center-to-view-safe-attachments-policies"></a>Utiliser le centre de sécurité & conformité pour afficher les stratégies de pièces jointes fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Dans la page **pièces jointes approuvées** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

   Les détails de la stratégie apparaissent dans un survol

## <a name="use-the-security--compliance-center-to-modify-safe-attachments-policies"></a>Utiliser le centre de sécurité & conformité pour modifier les stratégies de pièces jointes fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Dans la page **pièces jointes approuvées** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volet Détails de la stratégie, cliquez sur **modifier la stratégie**.

Les paramètres disponibles dans le survol qui s’affiche sont identiques à ceux décrits dans la section [utiliser le centre de sécurité & conformité pour créer des stratégies de pièces jointes approuvées](#use-the-security--compliance-center-to-create-safe-attachments-policies) .

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité des stratégies, consultez les sections suivantes.

### <a name="enable-or-disable-safe-attachments-policies"></a>Activer ou désactiver les stratégies de pièces jointes approuvées

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Notez la valeur dans la colonne **État** :

   - Déplacer le bouton bascule vers la gauche ![Désactiver la stratégie](../../media/scc-toggle-off.png) pour désactiver la stratégie.

   - Déplacer le bouton bascule vers la droite ![Activer la stratégie](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) pour activer la stratégie.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Définir la priorité des stratégies de pièces jointes approuvées

Par défaut, les stratégies de pièces jointes approuvées reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies de pièces jointes approuvées sont affichées dans l’ordre dans lequel elles sont traitées (la première stratégie a la valeur de **priorité** 0).

**Remarque**: dans le centre de sécurité & conformité, vous pouvez uniquement modifier la priorité de la stratégie de pièces jointes fiables une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle de pièce jointe fiable (ce qui peut avoir une incidence sur la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Dans la page **pièces jointes approuvées** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volet Détails de la stratégie, cliquez sur le bouton priorité disponible.

   - La stratégie de pièces jointes approuvées avec la valeur de **priorité** **0** a uniquement le bouton **diminuer la priorité** disponible.

   - La stratégie de pièces jointes approuvées avec la valeur de **priorité** la plus faible (par exemple, **3**) n’a que le bouton **augmenter la priorité** disponible.

   - Si vous avez au moins trois stratégies de pièces jointes approuvées, les stratégies entre les valeurs de priorité la plus élevée et la plus faible ont les deux boutons **augmenter la priorité** et **diminuer la priorité** .

4. Cliquez sur **augmenter** la priorité ou sur **diminuer la priorité** pour modifier la valeur de **priorité** .

5. Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-remove-safe-attachments-policies"></a>Utiliser le centre de sécurité & conformité pour supprimer des stratégies de pièces jointes fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**.

2. Dans la page **pièces jointes approuvées** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans la boîte de dialogue détails de la stratégie, cliquez sur **Supprimer la stratégie**, puis cliquez sur **Oui** dans la boîte de dialogue d’avertissement qui s’affiche.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Utiliser Exchange Online PowerShell ou l’environnement de ligne de commande Exchange EOP PowerShell autonome pour configurer des stratégies de pièces jointes fiables

Comme décrit précédemment, une stratégie de pièces jointes fiables est constituée d’une stratégie de pièces jointes fiables et d’une règle de pièce jointe fiable.

Dans PowerShell, la différence entre les stratégies de pièces jointes fiables et les règles de pièces jointes fiables est apparente. Vous pouvez gérer les stratégies de pièces jointes fiables à l’aide des cmdlets **\* -safeattachmentpolicy permet** et gérer les règles de pièces jointes fiables à l’aide des cmdlets **\* -safeattachmentrule permet** .

- Dans PowerShell, vous devez d’abord créer la stratégie de pièces jointes fiables, puis créer la règle de pièce jointe fiable qui identifie la stratégie à laquelle s’applique la règle.
- Dans PowerShell, vous pouvez modifier séparément les paramètres de la stratégie de pièces jointes approuvées et de la règle de pièces jointes approuvées.
- Lorsque vous supprimez une stratégie de pièces jointes fiables à partir de PowerShell, la règle de pièce jointe fiable correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Utiliser PowerShell pour créer des stratégies de pièces jointes fiables

La création d’une stratégie de pièces jointes fiables dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de pièces jointes fiables.
2. Créer la règle de pièce jointe fiable qui spécifie la stratégie de pièces jointes fiables à laquelle la règle s’applique.

 **Remarques**:

- Vous pouvez créer une règle de pièce jointe fiable et lui affecter une stratégie de pièces jointes fiables existante non associée. Une règle de pièce jointe fiable ne peut pas être associée à plusieurs stratégies de pièces jointes fiables.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de pièces jointes fiables dans PowerShell qui ne sont pas disponibles dans le centre de sécurité & jusqu’à ce que vous ayez créé la stratégie :
  - Créez la nouvelle stratégie comme désactivé (_activé_ `$false` sur la cmdlet **New-safeattachmentrule permet** ).
  - Définir la priorité de la stratégie lors de la création (_priorité_ _\<Number\>_ ) sur la cmdlet **New-safeattachmentrule permet** ).

- Une nouvelle stratégie de pièces jointes approuvées que vous créez dans PowerShell n’est pas visible dans le centre de sécurité &, tant que vous n’avez pas affecté la stratégie à une règle de pièce jointe fiable.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie de pièces jointes fiables

Pour créer une stratégie de pièces jointes fiables, utilisez la syntaxe suivante :

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>]
```

Cet exemple crée une stratégie de pièces jointes approuvées nommée Contoso All avec les valeurs suivantes :

- Bloquer les messages qui contiennent des programmes malveillants par analyse des documents approuvés (nous n’utilisons pas le paramètre _action_ , et la valeur par défaut est `Block` ).
- La redirection est activée et les messages qui contiennent des programmes malveillants sont envoyés à sec-ops@contoso.com à des fins d’analyse et d’enquête.
- Si l’analyse des pièces jointes fiables n’est pas disponible ou rencontre des erreurs, ne fournissez pas le message (nous n’utilisons pas le paramètre _ActionOnError_ et la valeur par défaut est `$true` ).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Étape 2 : utiliser PowerShell pour créer une règle de pièce jointe fiable

Pour créer une règle de pièce jointe fiable, utilisez la syntaxe suivante :

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Cet exemple crée une règle de pièce jointe fiable nommée Contoso All avec les conditions suivantes :

- La règle est associée à la stratégie de pièces jointes approuvées nommée Contoso All.
- La règle s’applique à tous les destinataires dans le domaine contoso.com.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.
- La règle est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true` ).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Utiliser PowerShell pour afficher les stratégies de pièces jointes fiables

Pour afficher les stratégies de pièces jointes approuvées existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les stratégies de pièces jointes approuvées.

```PowerShell
Get-SafeAttachmentPolicy
```

Cet exemple renvoie des informations détaillées sur la stratégie de pièces jointes approuvées nommée Contoso Executives.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Utiliser PowerShell pour afficher les règles de pièces jointes fiables

Pour afficher les règles de pièces jointes approuvées existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les règles de pièces jointes fiables.

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

Cet exemple renvoie des informations détaillées sur la règle de pièces jointes approuvées nommée Contoso Executives.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Utiliser PowerShell pour modifier des stratégies de pièces jointes fiables

Vous ne pouvez pas renommer une stratégie de pièces jointes fiables dans PowerShell (l’applet de commande **Set-safeattachmentpolicy permet** n’a pas de paramètre _Name_ ). Lorsque vous renommez une stratégie de pièces jointes fiables dans le centre de sécurité & conformité, vous renommez uniquement la _règle_ de pièce jointe fiable.

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une stratégie de pièces jointes fiables, comme décrit dans la section [étape 1 : utiliser PowerShell pour créer une stratégie de pièces jointes fiables](#step-1-use-powershell-to-create-a-safe-attachment-policy) plus haut dans cet article.

Pour modifier une stratégie de pièces jointes fiables, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentpolicy).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Utiliser PowerShell pour modifier les règles de pièces jointes fiables

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de pièce jointe fiable dans PowerShell est le paramètre _activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de pièces jointes approuvées existantes, consultez la section suivante.

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une règle, comme décrit dans la section [étape 2 : utiliser PowerShell pour créer une règle de pièce jointe fiable](#step-2-use-powershell-to-create-a-safe-attachment-rule) plus haut dans cet article.

Pour modifier une règle de pièce jointe fiable, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de pièces jointes fiables

L’activation ou la désactivation d’une règle de pièce jointe fiable dans PowerShell active ou désactive la stratégie de pièces jointes approuvées (la règle de pièces jointes fiables et la stratégie de pièces jointes approuvées).

Pour activer ou désactiver une règle de pièce jointe fiable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de pièces jointes approuvées nommée Marketing Department.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/enable-safeattachmentrule) et [Disable-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Utiliser PowerShell pour définir la priorité des règles de pièces jointes fiables

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de pièce jointe fiable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Remarque**: pour définir la priorité d’une nouvelle règle lors de sa création, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-safeattachmentrule permet** .

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Utiliser PowerShell pour supprimer des stratégies de pièces jointes fiables

Lorsque vous utilisez PowerShell pour supprimer une stratégie de pièces jointes fiables, la règle de pièce jointe fiable correspondante n’est pas supprimée.

Pour supprimer une stratégie de pièces jointes fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de pièces jointes approuvées nommée Marketing Department.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Utiliser PowerShell pour supprimer des règles de pièces jointes fiables

Lorsque vous utilisez PowerShell pour supprimer une règle de pièce jointe fiable, la stratégie de pièces jointes fiables correspondante n’est pas supprimée.

Pour supprimer une règle de pièce jointe fiable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de pièce jointe fiable nommée Marketing Department.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-safeattachmentrule permet](https://docs.microsoft.com/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien créé, modifié ou supprimé des stratégies de pièces jointes fiables, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**. Vérifiez la liste des stratégies, leurs valeurs d' **État** et leurs valeurs de **priorité** . Pour afficher plus de détails, sélectionnez la stratégie dans la liste, puis affichez les détails dans le survol.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Pour vérifier que les pièces jointes fiables analysent les messages, consultez les rapports de Defender pour Office 365 disponibles. Pour plus d’informations, consultez la rubrique [afficher les rapports pour Defender pour Office 365](view-reports-for-atp.md) et [utiliser l’Explorateur dans le centre de sécurité & conformité](threat-explorer.md).
