---
title: Configurer des stratégies Coffre pièces jointes dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Découvrez comment définir des stratégies Coffre pièces jointes pour protéger votre organisation contre les fichiers malveillants dans le courrier électronique.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2eefdbdfd9121bdc778425fe63ea35d3f97a4adc
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60196440"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies Coffre pièces jointes dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](whats-new-in-defender-for-office-365.md). Si vous êtes un utilisateur d’accueil à la recherche d’informations sur l’analyse des pièces jointes dans Outlook, voir [Advanced Outlook.com.](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2)

Coffre Les pièces jointes sont une fonctionnalité de [Microsoft Defender](whats-new-in-defender-for-office-365.md) pour Office 365 qui utilise un environnement virtuel pour vérifier les pièces jointes dans les messages électroniques entrants après qu’elles ont été analysées par la protection anti-programme malveillant dans [Exchange Online Protection (EOP),](anti-malware-protection.md)mais avant leur remise aux destinataires. Pour plus d’informations, [Coffre pièces jointes dans Microsoft Defender pour Office 365](safe-attachments.md).

Il n’existe aucune stratégie de pièces jointes intégrée ou Coffre par défaut. Pour obtenir Coffre pièces jointes des pièces jointes des messages électroniques, vous devez créer une ou plusieurs stratégies Coffre pièces jointes, comme décrit dans cet article.

Vous pouvez configurer des stratégies de pièces jointes Coffre dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online boîtes aux lettres, mais avec Defender pour les abonnements Office 365 modules.

Les éléments de base d’une stratégie Coffre pièces jointes sont :

- La stratégie de pièces jointes fiables : spécifie les actions pour les détections de programmes malveillants inconnus, s’il faut envoyer des messages avec des pièces jointes à une adresse e-mail spécifiée et s’il faut remettre des messages si l’analyse des pièces jointes Coffre ne peut pas se terminer.
- **La règle de pièce jointe sécurisée**: spécifie la priorité et les filtres de destinataires (à qui la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez les stratégies Coffre pièces jointes dans le portail Microsoft 365 Defender:

- Lorsque vous créez une stratégie de pièces jointes Coffre, vous créez en fait une règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisée associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie Coffre pièces jointes, les paramètres liés au nom, à la priorité, activé ou désactivé, et aux filtres de destinataire modifient la règle de pièce jointe sécurisée. Tous les autres paramètres modifient la stratégie de pièce jointe sécurisée associée.
- Lorsque vous supprimez une stratégie Coffre pièces jointes, la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, voir la section Utiliser Exchange Online PowerShell ou [EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) autonome pour configurer des stratégies Coffre pièces jointes plus loin dans cet article.

> [!NOTE]
> Dans la zone paramètres globaux des paramètres Coffre pièces jointes, vous configurez les fonctionnalités qui ne dépendent pas des stratégies Coffre pièces jointes. Pour obtenir des instructions, voir Activer Coffre pièces jointes pour [SharePoint, OneDrive et](turn-on-mdo-for-spo-odb-and-teams.md) Microsoft Teams et Coffre documents dans [Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **Coffre pièces jointes,** utilisez <https://security.microsoft.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Vous avez besoin d’autorisations avant de pouvoir suivre les procédures de cet article :
  - Pour créer, modifier et supprimer des stratégies de pièces jointes  Coffre,  vous devez être membre des  groupes de rôles Gestion de l’organisation ou Administrateur de la sécurité dans le portail Microsoft 365 Defender et membre du groupe de rôles Gestion de l’organisation dans Exchange Online. 
  - Pour accéder en lecture seule aux stratégies Coffre pièces jointes,  vous  devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité dans le portail Microsoft 365 Defender.

  Pour plus d’informations, [voir Autorisations dans le portail Microsoft 365 Defender et](permissions-microsoft-365-security-center.md) [autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender et les autorisations pour d’autres fonctionnalités dans Microsoft 365.  Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir les paramètres recommandés pour les stratégies Coffre pièces jointes, voir Coffre [paramètres de pièces jointes.](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)

- Autorisez jusqu’à 30 minutes pour qu’une stratégie nouvelle ou mise à jour soit appliquée.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies Coffre pièces jointes

La création d’une stratégie Coffre pièces jointes personnalisée dans le portail Microsoft 365 Defender crée la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées associée en utilisant le même nom pour les deux.

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes,** cliquez sur ![ Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Création**.

3. L’assistant d'application de stratégies s’ouvre. Dans la page **Nom de votre stratégie,** configurez les paramètres suivants :
   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs** et domaines qui s’affiche, identifiez les destinataires internes à qui la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés dans votre organisation.
   - **Groupes** : groupes de distribution, groupes de sécurité à extension messagerie ou groupes Microsoft 365 spécifiés dans votre organisation.
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identificateurs (nom, nom d’affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant apparaît dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour afficher toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s’applique (exceptions pour les destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur la **Paramètres** page, configurez les paramètres suivants :

   - **Coffre de programmes malveillants inconnus des** pièces jointes : sélectionnez l’une des valeurs suivantes :
     - **Off**: En règle générale, nous ne recommandons pas cette valeur.
     - **Moniteur**
     - **Bloc**: il s’agit de la valeur par défaut et de la valeur recommandée dans les stratégies de sécurité standard [et](preset-security-policies.md)stricte.
     - **Replace**
     - **Remise dynamique (fonctionnalité d’aperçu)**

     Ces valeurs sont expliquées dans les [paramètres Coffre pièces jointes.](safe-attachments.md#safe-attachments-policy-settings)

   - **Stratégie de mise** en quarantaine : sélectionnez la stratégie de mise en quarantaine qui s’applique aux messages mis en quarantaine par Coffre pièces jointes (**bloquer,** remplacer ou **remise dynamique).** Les stratégies de mise en quarantaine définissent ce que les utilisateurs peuvent faire pour mettre les messages en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

     Une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée (AdminOnlyAccessPolicy pour les détections de messages électroniques par Coffre pièces jointes). Lorsque vous modifiez ultérieurement la stratégie Coffre pièces jointes ou que vous affichez les paramètres, le nom de la stratégie de mise en quarantaine par défaut s’affiche.

   - Rediriger les messages contenant des pièces **jointes détectées**: si vous sélectionnez Activer la **redirection,** vous pouvez spécifier une adresse de messagerie dans les messages d’envoi qui contiennent des pièces **jointes bloquées, surveillées** ou remplacées dans la zone d’adresse de messagerie spécifiée pour envoyer des messages contenant des pièces jointes contenant des programmes malveillants à des besoins d’analyse et d’examen.

     La recommandation pour les paramètres de stratégie Standard et Strict consiste à activer la redirection. Pour plus d’informations, [voir Coffre Paramètres des pièces jointes.](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)

   - Appliquez la réponse de détection des pièces jointes Coffre si l’analyse ne peut pas se terminer (délai ou **erreurs) : l’action** spécifiée par Coffre La réponse anti-programme malveillant inconnue pièces **jointes** est appliquée aux messages même lorsque l’analyse des pièces jointes Coffre ne peut pas se terminer. Si vous avez sélectionné cette option, sélectionnez toujours Activer la **redirection** et spécifiez une adresse de messagerie pour envoyer des messages contenant des pièces jointes contenant des programmes malveillants. Dans le cas contraire, les messages peuvent être perdus.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

7. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies Coffre pièces jointes

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes, les propriétés suivantes** sont affichées dans la liste des stratégies :
   - **Name**
   - **État**
   - **Priorité**

3. Lorsque vous sélectionnez une stratégie en cliquant sur le nom, les paramètres de stratégie s’affichent dans un volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les stratégies Coffre pièces jointes

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes,** sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, voir la section Utiliser le portail Microsoft 365 Defender pour créer des stratégies Coffre [pièces jointes](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) plus tôt dans cet article.

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-safe-attachments-policies"></a>Activer ou désactiver les stratégies Coffre pièces jointes

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes,** sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Définir la priorité des stratégies Coffre pièces jointes

Par défaut, Coffre les stratégies de pièces jointes ont une priorité basée sur l’ordre de leur création (les stratégies les plus nouvelles sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Coffre Les stratégies de pièces jointes sont affichées dans l’ordre de traitement (la première stratégie a la **valeur** priority 0).

**Remarque**: dans le portail Microsoft 365 Defender, vous pouvez uniquement modifier la priorité de la stratégie Coffre pièces jointes une fois que vous l’avez créé. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle de pièce jointe sécurisée (ce qui peut affecter la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro **Priorité** dans le Portail Microsoft 365 Defender). La modification de la priorité d’une stratégie n’a de sens que si vous avez plusieurs stratégies.

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes,** sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du volant des détails de stratégie  qui s’affiche, vous verrez Augmenter la priorité ou Diminuer la priorité en fonction de la valeur de priorité actuelle et du nombre de stratégies : 
   - La stratégie dont la valeur **de** priorité **est 0** ne dispose que de l’option Diminuer **la** priorité disponible.
   - La stratégie dont la valeur **de** priorité est la plus faible (par exemple, **3**) n’a que l’option Augmenter **la** priorité disponible.
   - Si vous avez au moins trois stratégies, les stratégies  entre les valeurs de priorité les plus élevées et les plus faibles ont les options Augmenter la priorité et Diminuer **la** priorité disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les stratégies Coffre pièces jointes

1. Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section.

2. Dans la page **Coffre pièces jointes,** sélectionnez une stratégie personnalisée dans la liste en cliquant sur le nom de la stratégie.

3. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

4. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies Coffre pièces jointes

Comme décrit précédemment, une stratégie Coffre pièces jointes se compose d’une stratégie de pièces jointes sécurisées et d’une règle de pièces jointes sécurisées.

Dans PowerShell, la différence entre les stratégies de pièces jointes sécurisées et les règles de pièces jointes sécurisées est évidente. Vous gérez les stratégies de pièces jointes sécurisées à l’aide des cmdlets **\* -SafeAttachmentPolicy** et vous gérez les règles de pièces jointes sécurisées à l’aide des cmdlets **\* -SafeAttachmentRule.**

- Dans PowerShell, vous créez d’abord la stratégie de pièces jointes sécurisées, puis vous créez la règle de pièce jointe sécurisée qui identifie la stratégie à qui s’applique la règle.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie de pièces jointes sécurisées et de la règle de pièce jointe sécurisée.
- Lorsque vous supprimez une stratégie de pièces jointes sécurisées de PowerShell, la règle de pièce jointe sécurisée correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Utiliser PowerShell pour créer des stratégies Coffre pièces jointes

La création d Coffre de pièces jointes dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de pièces jointes sécurisées.
2. Créez la règle de pièce jointe sécurisée qui spécifie la stratégie de pièces jointes sécurisées à l’application de la règle.

 **Remarques** :

- Vous pouvez créer une règle de pièce jointe sécurisée et lui attribuer une stratégie de pièces jointes sécurisées existante non attachée. Une règle de pièce jointe sécurisée ne peut pas être associée à plusieurs stratégies de pièces jointes sécurisées.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de pièces jointes sécurisées dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
  - Créez la stratégie comme _désactivée_ ( activée sur la `$false` cmdlet **New-SafeAttachmentRule).**
  - Définissez la priorité de la stratégie lors de la création (_Priorité_ ) sur la _\<Number\>_ cmdlet **New-SafeAttachmentRule).**

- Une nouvelle stratégie de pièces jointes sécurisées que vous créez dans PowerShell n’est pas visible dans le portail Microsoft 365 Defender tant que vous n’avez pas attribué la stratégie à une règle de pièce jointe sécurisée.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de pièces jointes sécurisées

Pour créer une stratégie de pièces jointes sécurisées, utilisez la syntaxe suivante :

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

Cet exemple crée une stratégie de pièce jointe sécurisée nommée Contoso All avec les valeurs suivantes :

- Bloquez les messages qui contiennent des programmes malveillants par l’analyse Coffre documents (nous n’utilisons pas le paramètre _Action_ et la valeur par défaut est `Block` ).
- La stratégie [de mise en](quarantine-policies.md) quarantaine par défaut est utilisée (AdminOnlyAccessPolicy), car nous n’utilisons pas le paramètre _QuarantineTag._
- La redirection est activée et les messages qui contiennent des programmes malveillants sont envoyés sec-ops@contoso.com pour analyse et examen.
- Si Coffre’analyse des pièces jointes n’est pas disponible ou rencontre des erreurs, ne remettre pas le message (nous n’utilisons pas le paramètre _ActionOnError_ et la valeur par défaut est `$true` ).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Pour obtenir des instructions [](quarantine-policies.md) détaillées sur la stratégie de mise en quarantaine à utiliser dans une stratégie de pièces jointes sécurisées, voir Utiliser PowerShell pour spécifier la stratégie de mise en quarantaine dans Coffre [stratégies de pièces jointes.](quarantine-policies.md#safe-attachments-policies-in-powershell)

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Utiliser PowerShell pour afficher les règles de pièces jointes sécurisées

Pour afficher les règles de pièces jointes sécurisées existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les règles de pièces jointes sécurisées.

```PowerShell
Get-SafeAttachmentRule
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Utiliser PowerShell pour modifier des stratégies de pièces jointes sécurisées

Vous ne pouvez pas renommer une stratégie de pièces jointes sécurisées dans PowerShell (la cmdlet **Set-SafeAttachmentPolicy** n’a pas de _paramètre_ Name). Lorsque vous renommez une stratégie Coffre pièces jointes dans le portail Microsoft 365 Defender, vous renommez uniquement la règle de pièces jointes _sécurisées._

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une stratégie de pièces jointes sécurisées, comme décrit à l’étape 1 : Utiliser [PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) pour créer une section sur la stratégie de pièces jointes sécurisées plus tôt dans cet article.

Pour modifier une stratégie de pièces jointes sécurisées, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Pour obtenir des instructions [](quarantine-policies.md) détaillées sur la stratégie de mise en quarantaine à utiliser dans une stratégie de pièces jointes sécurisées, voir Utiliser PowerShell pour spécifier la stratégie de mise en quarantaine dans Coffre [stratégies de pièces jointes.](quarantine-policies.md#safe-attachments-policies-in-powershell)

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Utiliser PowerShell pour modifier des règles de pièces jointes sécurisées

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de pièce jointe sécurisée dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver des règles de pièces jointes sécurisées existantes, consultez la section suivante.

Dans le cas contraire, les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à l’étape 2 : Utiliser [PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) pour créer une section de règle de pièce jointe sécurisée plus tôt dans cet article.

Pour modifier une règle de pièce jointe sécurisée, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Utiliser PowerShell pour activer ou désactiver des règles de pièces jointes sécurisées

L’activation ou la désactivation d’une règle de pièce jointe sécurisée dans PowerShell active ou désactive l’ensemble de la stratégie de pièces jointes Coffre (la règle de pièces jointes sécurisées et la stratégie de pièces jointes sécurisées affectée).

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) et [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Utiliser PowerShell pour définir la priorité des règles de pièces jointes sécurisées

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d'une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de pièce jointe sécurisée dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Remarque**: pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-SafeAttachmentRule.**

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement créé, modifié ou supprimé des stratégies Coffre pièces jointes, faites l’une des étapes suivantes :

- Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section. Vérifiez la liste des stratégies, leurs **valeurs d’état** et leurs **valeurs de** priorité. Pour afficher plus de détails, sélectionnez la stratégie dans la liste en cliquant sur le nom, puis affichez les détails dans le volant.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les \<Name\> paramètres :

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Pour vérifier que la Coffre pièces jointes analyse les messages, recherchez les rapports de Office 365 defender disponibles. Pour plus d’informations, voir [Afficher les rapports pour Defender pour Office 365](view-reports-for-mdo.md) et Utiliser l’Explorateur dans le portail [Microsoft 365 Defender.](threat-explorer.md)
