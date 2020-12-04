---
title: Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à afficher, créer, modifier et supprimer des stratégies de liens fiables et des paramètres globaux de liens fiables dans Microsoft Defender pour Office 365.
ms.openlocfilehash: 550be48d5f1cae490c53c8f4a9fcedb0b9f21f73
ms.sourcegitcommit: d81c7cea85af6ad5fef81d3c930514a51464368c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49572716"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Cet article est destiné aux clients professionnels qui disposent [de Microsoft Defender pour Office 365](office-365-atp.md). Si vous êtes un utilisateur à domicile et que vous recherchez des informations sur Safelinks dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

La fonctionnalité liens fiables est une fonctionnalité de [Microsoft Defender pour Office 365](office-365-atp.md) qui permet d’analyser les messages électroniques entrants dans le flux de messagerie et de cliquer sur vérification des URL et des liens dans les messages électroniques et à d’autres emplacements. Pour plus d’informations, reportez-vous à [liens fiables dans Microsoft Defender pour Office 365](atp-safe-links.md).

Il n’existe pas de stratégie de liens de sécurité intégrée ou par défaut. Pour obtenir des liens fiables sur l’analyse des URL, vous devez créer une ou plusieurs stratégies de liens fiables, comme décrit dans cet article.

Vous pouvez configurer des stratégies de liens fiables dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange autonome EOP pour les organisations sans boîtes aux lettres Exchange Online, mais avec Microsoft Defender for Office 365 compléments d’abonnement).

Les éléments de base d’une stratégie de liens fiables sont les suivants :

- **Stratégie de liens fiables**: activer la protection des liens fiables, activer l’analyse des URL en temps réel, spécifier s’il faut attendre la fin de l’analyse en temps réel avant de remettre le message, activer l’analyse des messages internes, spécifier s’il faut effectuer le suivi des clics des utilisateurs sur les URL et spécifier si les utilisateurs peuvent cliquer sur le bac à l’URL d’origine.
- **La règle de liens fiables**: spécifie la priorité et les filtres de destinataire (auxquels la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies de liens fiables dans le centre de sécurité & Compliance Center :

- Lorsque vous créez une stratégie de liens fiables, vous créez en réalité une règle de liens fiables et la stratégie de liens approuvés associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie de liens fiables, les paramètres associés aux filtres nom, priorité, activé ou désactivé et filtre de destinataires modifient la règle de liens approuvés. Tous les autres paramètres modifient la stratégie de liens approuvés associée.
- Lorsque vous supprimez une stratégie de liens fiables, la règle de liens fiables et la stratégie de liens approuvés associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, reportez-vous à la section [utiliser Exchange Online PowerShell or standalone EOP PowerShell pour configurer les stratégies de liens fiables](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) plus loin dans cet article.

> [!NOTE]
> Vous configurez les paramètres globaux pour la protection des liens fiables **en dehors** des stratégies de liens fiables. Pour obtenir des instructions, consultez la rubrique [configure Global Settings for Safe Links in Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **liens approuvés** , utilisez <https://protection.office.com/safelinksv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Avant de pouvoir effectuer les procédures décrites dans cet article, vous devez disposer d’autorisations dans le centre de sécurité & Compliance Center :
  - Pour créer, modifier et supprimer des stratégies de liens approuvés, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** .
  - Pour un accès en lecture seule aux stratégies de liens fiables, vous devez être membre des groupes de rôles **lecteur global** ou **lecteur de sécurité** .

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  **Remarques**:

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le centre d’administration 365 de Microsoft donne aux utilisateurs les autorisations requises dans le centre de sécurité & conformité _et_ des autorisations pour d’autres fonctionnalités de Microsoft 365. Si vous souhaitez en savoir plus, veuillez consulter la page [À propos des rôles d’administrateur](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles).
  - Le groupe de rôles gestion de l' **Organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) offre également un accès en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies de liens fiables, consultez la rubrique [Safe Links Policy Settings](recommended-settings-for-eop-and-office365-atp.md#safe-links-policy-settings).

- Autoriser jusqu’à 30 minutes pour l’application d’une stratégie nouvelle ou mise à jour.

- De [nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](office-365-atp.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements aux stratégies de liens fiables existantes.

## <a name="use-the-security--compliance-center-to-create-safe-links-policies"></a>Utiliser le centre de sécurité & conformité pour créer des stratégies de liens fiables

La création d’une stratégie de liens fiables personnalisée dans le centre de sécurité & conformité crée simultanément la règle de liens fiables et la stratégie de liens approuvés associée en utilisant le même nom pour les deux.

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Sur la page **liens approuvés** , cliquez sur **créer**.

3. L’Assistant **nouvelle stratégie de liens fiables** s’ouvre. Sur la page **nommer votre stratégie** , configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Sur la page **paramètres** qui s’affiche, configurez les paramètres suivants :

   - **Sélectionnez l’action pour les URL potentiellement malveillantes dans les messages**: sélectionnez **activé** pour activer la protection des liens fiables dans les messages électroniques.

   - **Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams**: sélectionnez **activé** pour activer la protection des liens fiables dans Teams.

   - **Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers**: sélectionnez ce paramètre pour activer l’analyse en temps réel des liens dans les messages électroniques.

   - **Patientez jusqu’à la fin de l’analyse des URL avant de remettre le message**: sélectionnez ce paramètre pour attendre la fin de l’analyse des URL en temps réel avant de remettre le message.

   - **Appliquer des liens fiables aux messages électroniques envoyés au sein de l’organisation**: sélectionnez ce paramètre pour appliquer la stratégie de liens fiables aux messages entre les expéditeurs internes et les destinataires internes.

   - **Ne pas suivre les clics des utilisateurs**: laissez ce paramètre non sélectionné pour permettre au suivi de cliquer sur les URL dans les messages électroniques.

   - **Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine**: sélectionnez ce paramètre pour empêcher les utilisateurs de cliquer sur l’URL d’origine dans les [pages d’avertissement](atp-safe-links.md#warning-pages-from-safe-links).

   - **Ne réécrivez pas les URL suivantes**: permet d’accéder aux URL spécifiées qui seraient sinon bloquées par les liens fiables.

     Dans la zone, tapez l’URL ou la valeur souhaitée, puis cliquez sur ![Icône Ajouter un bouton](../../media/ITPro-EAC-AddIcon.png).

     Pour supprimer une entrée existante, sélectionnez-la, puis cliquez sur ![Icône de bouton supprimer](../../media/ITPro-EAC-DeleteIcon.png).

     Pour la syntaxe d’entrée, consultez [la syntaxe d’entrée pour la liste « ne pas réécrire les URL suivantes »](atp-safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

   Pour plus d’informations sur ces paramètres, consultez les [rubriques paramètres de liens approuvés pour les messages électroniques](atp-safe-links.md#safe-links-settings-for-email-messages) et les [paramètres de liens fiables pour Microsoft teams](atp-safe-links.md#safe-links-settings-for-microsoft-teams).

   Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie standard et stricte, consultez la rubrique [Safe Links Policy Settings](recommended-settings-for-eop-and-office365-atp.md#safe-links-policy-settings).

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

## <a name="use-the-security--compliance-center-to-view-safe-links-policies"></a>Utiliser le centre de sécurité & conformité pour afficher les stratégies de liens fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Sur la page **liens approuvés** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

   Les détails de la stratégie apparaissent dans un survol

## <a name="use-the-security--compliance-center-to-modify-safe-links-policies"></a>Utiliser le centre de sécurité & conformité pour modifier les stratégies de liens fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Sur la page **liens approuvés** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volet Détails de la stratégie, cliquez sur **modifier la stratégie**.

Les paramètres disponibles dans le survol qui s’affiche sont identiques à ceux décrits dans la section [utiliser le centre de sécurité & conformité pour créer des stratégies de liens fiables](#use-the-security--compliance-center-to-create-safe-links-policies) .

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité des stratégies, consultez les sections suivantes.

### <a name="enable-or-disable-safe-links-policies"></a>Activer ou désactiver les stratégies de liens fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Notez la valeur dans la colonne **État** :

   - Déplacez le bouton bascule vers la gauche pour désactiver la stratégie : ![Désactiver la stratégie](../../media/scc-toggle-off.png).

   - Déplacez le bouton bascule vers la droite pour activer la stratégie : ![Activer la stratégie](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png).

### <a name="set-the-priority-of-safe-links-policies"></a>Définir la priorité des stratégies de liens fiables

Par défaut, les stratégies de liens fiables reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies de liens fiables sont affichées dans l’ordre dans lequel elles sont traitées (la première stratégie a la valeur de **priorité** 0).

**Remarque**: dans le centre de sécurité & conformité, vous pouvez uniquement modifier la priorité de la stratégie de liens fiables une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle de liens fiables (ce qui peut avoir une incidence sur la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Sur la page **liens approuvés** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans le volet Détails de la stratégie, cliquez sur le bouton priorité disponible :

   - La stratégie de liens fiables avec la valeur de **priorité** **0** a uniquement le bouton **diminuer la priorité** disponible.

   - La stratégie de liens fiables avec la valeur de **priorité** la plus faible (par exemple, **3**) n’a que le bouton **augmenter la priorité** disponible.

   - Si vous avez trois stratégies de liens fiables ou plus, les stratégies entre les valeurs de priorité la plus élevée et la plus faible ont les deux boutons **augmenter la priorité** et **diminuer la priorité** .

4. Cliquez sur **augmenter** la priorité ou sur **diminuer la priorité** pour modifier la valeur de **priorité** .

5. Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-remove-safe-links-policies"></a>Utiliser le centre de sécurité & conformité pour supprimer des stratégies de liens fiables

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**.

2. Sur la page **liens approuvés** , sélectionnez une stratégie dans la liste et cliquez dessus (ne cochez pas la case).

3. Dans la boîte de dialogue détails de la stratégie, cliquez sur **Supprimer la stratégie**, puis cliquez sur **Oui** dans la boîte de dialogue d’avertissement qui s’affiche.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Utiliser Exchange Online PowerShell ou l’environnement de ligne de commande Exchange EOP PowerShell autonome pour configurer les stratégies de liens fiables

Comme décrit précédemment, une stratégie de liens fiables est constituée d’une stratégie de liens fiables et d’une règle de liens fiables.

Dans PowerShell, la différence entre les stratégies de liens fiables et les règles de liens fiables est apparente. Vous pouvez gérer les stratégies de liens fiables à l’aide des cmdlets **\* -safelinkspolicy permet** et gérer les règles de liens fiables à l’aide des cmdlets **\* -safelinksrule permet** .

- Dans PowerShell, vous devez d’abord créer la stratégie de liens fiables, puis créer la règle de liens fiables qui identifie la stratégie à laquelle la règle s’applique.
- Dans PowerShell, vous pouvez modifier séparément les paramètres de la stratégie de liens fiables et de la règle de liens approuvés.
- Lorsque vous supprimez une stratégie de liens fiables de PowerShell, la règle de liens approuvés correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-safe-links-policies"></a>Utiliser PowerShell pour créer des stratégies de liens fiables

La création d’une stratégie de liens fiables dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de liens fiables.
2. Créer la règle de liens fiables qui spécifie la stratégie de liens approuvés à laquelle la règle s’applique.

 **Remarques**:

- Vous pouvez créer une règle de liens fiables et lui affecter une stratégie de liens approuvés existante non associée. Une règle de liens fiables ne peut pas être associée à plusieurs stratégies de liens fiables.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de liens fiables dans PowerShell qui ne sont pas disponibles dans le centre de sécurité & de conformité tant que vous n’avez pas créé la stratégie :

  - Créez la nouvelle stratégie comme désactivé (_activé_ `$false` sur la cmdlet **New-safelinksrule permet** ).
  - Définir la priorité de la stratégie lors de la création (_priorité_ _\<Number\>_ ) sur la cmdlet **New-safelinksrule permet** ).

- Une nouvelle stratégie de liens approuvés que vous créez dans PowerShell n’est pas visible dans le centre de sécurité &, tant que vous n’avez pas affecté la stratégie à une règle de liens fiables.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie de liens fiables

Pour créer une stratégie de liens fiables, utilisez la syntaxe suivante :

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-IsEnabled <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-DoNotAllowClickThrough <$true | $false>] [-DoNotTrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

**Remarques**:

- Pour plus d’informations sur la syntaxe d’entrée à utiliser pour le paramètre _DoNotRewriteUrls_ , voir [entrée Syntax pour la liste « ne pas réécrire les URL suivantes »](atp-safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list).

- Pour obtenir une syntaxe supplémentaire que vous pouvez utiliser pour le paramètre _DoNotRewriteUrls_ lorsque vous modifiez des stratégies de liens fiables existantes à l’aide de l’applet de commande **Set-safelinkspolicy permet** , voir la section [Utiliser PowerShell pour modifier les stratégies de liens approuvés](#use-powershell-to-modify-safe-links-policies) plus loin dans cet article.

Cet exemple crée une stratégie de liens fiables nommée Contoso All avec les valeurs suivantes :

- Activer l’analyse et la réécriture d’URL dans les messages électroniques.
- Activer l’analyse des URL dans Teams (appuyez sur Aperçu uniquement).
- Activer l’analyse en temps réel des URL cliquées, y compris les liens sur lesquels pointent vers des fichiers.
- Patientez jusqu’à la fin de l’analyse des URL avant de remettre le message.
- Activez l’analyse des URL et la réécriture pour les messages internes.
- Suivi des clics d’utilisateur liés à la protection des liens fiables (nous n’utilisons pas le paramètre _DoNotTrackUserClicks_ et la valeur par défaut est $false, ce qui signifie que les clics utilisateur font l’élément d’un suivi).
- Ne pas autoriser les utilisateurs à cliquer à travers l’URL d’origine.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -IsEnabled $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -DoNotAllowClickThrough $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Étape 2 : utiliser PowerShell pour créer une règle de liens fiables

Pour créer une règle de liens fiables, utilisez la syntaxe suivante :

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Cet exemple crée une règle de liens fiables nommée Contoso All avec les conditions suivantes :

- La règle est associée à la stratégie de liens approuvés nommée Contoso All.
- La règle s’applique à tous les destinataires dans le domaine contoso.com.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.
- La règle est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true` ).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Utiliser PowerShell pour afficher les stratégies de liens fiables

Pour afficher les stratégies de liens fiables existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les stratégies de liens fiables.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

Cet exemple renvoie des informations détaillées sur la stratégie de liens approuvés nommée Contoso Executives.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Utiliser PowerShell pour afficher les règles de liens fiables

Pour afficher les règles de liens fiables existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie la liste récapitulative de toutes les règles de liens fiables.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

Cet exemple renvoie des informations détaillées sur la règle de liens approuvés nommée Contoso Executives.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Utiliser PowerShell pour modifier les stratégies de liens fiables

Vous ne pouvez pas renommer une stratégie de liens fiables dans PowerShell (l’applet de commande **Set-safelinkspolicy permet** n’a pas de paramètre _Name_ ). Lorsque vous renommez une stratégie de liens fiables dans le centre de sécurité & conformité, vous renommez uniquement la _règle_ de liens fiables.

La seule considération supplémentaire pour la modification des stratégies de liens fiables dans PowerShell est la syntaxe disponible pour le paramètre _DoNotRewriteUrls_ (la [liste « ne pas réécrire les URL suivantes »](atp-safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)) :

- Pour ajouter des valeurs qui remplaceront toutes les entrées existantes, utilisez la syntaxe suivante : `"Entry1","Entry2,..."EntryN"` .
- Pour ajouter ou supprimer des valeurs sans affecter les entrées existantes, utilisez la syntaxe suivante : `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une stratégie de liens fiables, comme décrit dans la section [étape 1 : utiliser PowerShell pour créer une stratégie de liens fiables](#step-1-use-powershell-to-create-a-safe-links-policy) plus haut dans cet article.

Pour modifier une stratégie de liens fiables, utilisez la syntaxe suivante :

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Utiliser PowerShell pour modifier les règles de liens fiables

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de liens fiables dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de liens approuvés existantes, consultez la section suivante.

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une règle, comme décrit dans la section [étape 2 : utiliser PowerShell pour créer une règle de liens fiables](#step-2-use-powershell-to-create-a-safe-links-rule) plus haut dans cet article.

Pour modifier une règle de liens fiables, utilisez la syntaxe suivante :

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de liens fiables

L’activation ou la désactivation d’une règle de liens fiables dans PowerShell active ou désactive la stratégie de liens fiables entières (la règle de liens fiables et la stratégie de liens fiables affectés).

Pour activer ou désactiver une règle de liens fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de liens approuvés nommée Marketing Department.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/enable-safelinksrule) et [Disable-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Utiliser PowerShell pour définir la priorité des règles de liens fiables

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de liens fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

**Remarque**: pour définir la priorité d’une nouvelle règle lors de sa création, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-safelinksrule permet** .

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Utiliser PowerShell pour supprimer des stratégies de liens fiables

Lorsque vous utilisez PowerShell pour supprimer une stratégie de liens fiables, la règle de liens fiables correspondante n’est pas supprimée.

Pour supprimer une stratégie de liens fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de liens approuvés nommée Marketing Department.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Utiliser PowerShell pour supprimer des règles de liens fiables

Lorsque vous utilisez PowerShell pour supprimer une règle de liens fiables, la stratégie de liens fiables correspondante n’est pas supprimée.

Pour supprimer une règle de liens fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de liens approuvés nommée Marketing Department.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-safelinksrule permet](https://docs.microsoft.com/powershell/module/exchange/remove-safelinksrule).

Pour vérifier que les liens fiables analysent les messages, consultez les rapports Microsoft Defender pour Office 365 disponibles. Pour plus d’informations, consultez la rubrique [afficher les rapports pour Defender pour Office 365](view-reports-for-atp.md) et [utiliser l’Explorateur dans le centre de sécurité & conformité](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez bien créé, modifié ou supprimé des stratégies de liens fiables, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **liens fiables ATP**. Vérifiez la liste des stratégies, leurs valeurs d' **État** et leurs valeurs de **priorité** . Pour afficher plus de détails, sélectionnez la stratégie dans la liste, puis affichez les détails dans le survol.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
