---
title: Configurer les stratégies de la fonctionnalité Liens fiables dans Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: bdd5372d-775e-4442-9c1b-609627b94b5d
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Les administrateurs peuvent apprendre à afficher, créer, modifier et supprimer des stratégies de liens Coffre et des paramètres de liens Coffre globaux dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 867d055c44ba0d0ae0b7b763bc556a06f16e5cd8
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847086"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Configurer les stratégies de la fonctionnalité Liens fiables dans Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous êtes un utilisateur à la recherche d’informations sur Safelinks dans Outlook, consultez [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Coffre Liens dans [Microsoft Defender pour Office 365](defender-for-office-365.md) fournit l’analyse d’URL des messages électroniques entrants dans le flux de courrier, ainsi que l’heure de vérification des URL et des liens dans les messages électroniques et dans d’autres emplacements. Pour plus d’informations, consultez [Coffre Liens dans Microsoft Defender pour Office 365](safe-links.md).

Bien qu’il n’existe aucune stratégie de Coffre de liens par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit Coffre protection des liens à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de liens Coffre personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Vous pouvez également utiliser les procédures décrites dans cet article pour créer des stratégies Coffre Liens qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques.

> [!NOTE]
>
> Vous configurez les paramètres globaux pour la protection des liens Coffre **en dehors** des stratégies de liens Coffre. Pour obtenir des instructions, consultez [Configurer les paramètres globaux pour les liens Coffre dans Microsoft Defender pour Office 365](configure-global-settings-for-safe-links.md).
>
> Les administrateurs doivent prendre en compte les différents paramètres de configuration pour les liens Coffre. L’une des options disponibles consiste à inclure des informations d’identification de l’utilisateur dans Coffre Liens. Cette fonctionnalité permet aux équipes d’opérations de sécurité (SecOps) d’examiner les compromissions potentielles de l’utilisateur, de prendre des mesures correctives et de limiter les violations coûteuses.

Vous pouvez configurer les politiques Safe Links dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online, mais avec des abonnements complémentaires Microsoft Defender for Office 365).

Les éléments de base d’une stratégie de liens Coffre sont les suivants :

- **Stratégie de liens sécurisés** : activez Coffre protection des liens, activez l’analyse des URL en temps réel, spécifiez s’il faut attendre la fin de l’analyse en temps réel avant de remettre le message, activez l’analyse des messages internes, spécifiez s’il faut suivre les clics de l’utilisateur sur les URL et spécifiez s’il faut autoriser les utilisateurs à cliquer sur l’URL d’origine.
- **Règle de liens sécurisés** : spécifie les filtres de priorité et de destinataire (auxquels la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies de liens Coffre dans le portail Microsoft 365 Defender :

- Lorsque vous créez une stratégie de liens Coffre, vous créez en fait une règle de liens sécurisés et la stratégie de liens sécurisés associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie de liens Coffre, les paramètres liés au nom, à la priorité, activé ou désactivé, et les filtres de destinataire modifient la règle de liens sécurisés. Tous les autres paramètres modifient la stratégie de liens sécurisés associée.
- Lorsque vous supprimez une stratégie de liens Coffre, la règle liens sécurisés et la stratégie de liens sécurisés associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, consultez la section [Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies Coffre Links](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) plus loin dans cet article.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Coffre Liens**, utilisez <https://security.microsoft.com/safelinksv2>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Vous devez disposer d’autorisations pour pouvoir effectuer les procédures décrites dans cet article :
  - Pour créer, modifier et supprimer des stratégies de liens Coffre, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur** de la sécurité dans le portail Microsoft 365 Defender **et** membre du groupe de **rôles Gestion de l’organisation** dans Exchange Online.
  - Pour accéder en lecture seule aux stratégies Coffre Liens, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité**.

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) et [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle de Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  . - Le groupe de rôles **Gestion de l’organisation en mode affichage uniquement** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) donne également un accès en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies de liens Coffre, consultez [Coffre Paramètres de stratégie Liens](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Autorisez jusqu’à 6 heures l’application d’une stratégie nouvelle ou mise à jour.

- [De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements à vos stratégies de liens Coffre existantes.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies de liens Coffre

La création d’une stratégie de liens Coffre personnalisée dans le portail Microsoft 365 Defender crée la règle de liens sécurisés et la stratégie de liens sécurisés associée en même temps en utilisant le même nom pour les deux.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Coffre Links** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Liens**, utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **liens Coffre**, cliquez sur ![l’icône Créer.](../../media/m365-cc-sc-create-icon.png) **Création**.

3. **L’Assistant Nouvelle stratégie de liens Coffre** s’ouvre. Dans la page **Nommer votre** stratégie, configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs et domaines** qui s’affiche, identifiez les destinataires internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
   - **Groupes** :
     - Membres des groupes de distribution spécifiés ou des groupes de sécurité à extension messagerie.
     - Groupes Microsoft 365 spécifiée.
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : Pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s'applique (exceptions des destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Paramètres de protection** qui s’affiche, configurez les paramètres suivants :
   - **Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages** : sélectionnez **Activé** pour activer Coffre Protection des liens pour les liens dans les messages électroniques. Si vous activez ce paramètre, les paramètres suivants sont disponibles :
     - **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** : sélectionnez cette option pour activer l’analyse en temps réel des liens dans les messages électroniques. Si vous activez ce paramètre, le paramètre suivant est disponible :
       - **Attendez la fin de l’analyse d’URL avant de remettre le message** : sélectionnez cette option pour attendre la fin de l’analyse d’URL en temps réel avant de remettre le message.
     - **Appliquer Coffre liens vers les messages électroniques envoyés au sein de l’organisation** : sélectionnez cette option pour appliquer la stratégie Coffre Liens aux messages entre les expéditeurs internes et les destinataires internes.
   - **Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft Teams** : Sélectionnez **Activé** pour activer Coffre Protection des liens pour les liens dans Teams. Notez que l’application de ce paramètre peut prendre jusqu’à 24 heures.
   - **Suivre les clics de l’utilisateur** : laissez cette option sélectionnée pour activer le suivi des clics de l’utilisateur sur les URL dans les messages électroniques.
   - **Permettre aux utilisateurs de cliquer sur l’URL d’origine** : désactivez cette option pour empêcher les utilisateurs de cliquer sur l’URL d’origine dans les [pages d’avertissement](safe-links.md#warning-pages-from-safe-links).
   - **Ne réécrivez pas les URL suivantes** : autorise l’accès aux URL spécifiées qui seraient autrement bloquées par Coffre Liens.

     Dans la zone, tapez l’URL ou la valeur souhaitée, puis cliquez sur **Ajouter**. Répétez cette étape autant de fois que nécessaire.

     Pour supprimer une entrée existante, cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de l’entrée.

     Pour la syntaxe d’entrée, consultez [la syntaxe Entrée pour la liste « Ne pas réécrire les URL suivantes](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list) ».

   Pour plus d’informations sur ces paramètres, consultez [les paramètres Coffre Liens pour les messages électroniques](safe-links.md#safe-links-settings-for-email-messages) et [les paramètres Coffre Liens pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).

   Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict, consultez [Coffre Paramètres de stratégie Liens](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Notification** qui s’affiche, sélectionnez l’une des valeurs suivantes pour **savoir comment informer vos utilisateurs :**
   - **Utiliser le texte de notification par défaut**
   - **Utilisez le texte de notification personnalisé** : si vous sélectionnez cette valeur (la longueur ne peut pas dépasser 200 caractères), les paramètres suivants s’affichent :
     - **Utiliser Traducteur Microsoft pour la localisation automatique**
     - **Texte de notification personnalisé** : entrez le texte de notification personnalisé dans cette zone.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

8. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies de liens Coffre

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Coffre Links** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Liens**, utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **liens Coffre**, les propriétés suivantes s’affichent dans la liste des stratégies de liens Coffre :
   - **Name**
   - **État**
   - **Priorité**

3. Lorsque vous sélectionnez une stratégie en cliquant sur le nom, les paramètres de stratégie s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les stratégies de liens Coffre

1. Dans le portail Microsoft 365 Defender, accédez à **la section** \> **Stratégies & règles sur les stratégies** \> de **menace** \> **Coffre liens**.

2. Dans la page **Coffre Liens**, sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez la section [précédente Utiliser le portail Microsoft 365 Defender pour créer des stratégies Coffre Liens](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) dans cet article.

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-safe-links-policies"></a>Activer ou désactiver les stratégies de liens Coffre

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Coffre Links** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Liens**, utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Coffre Liens**, sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-safe-links-policies"></a>Définir la priorité des stratégies de liens Coffre

Par défaut, Coffre les liens reçoivent une priorité basée sur l’ordre dans lequel ils ont été créés (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour modifier la priorité d'une stratégie, vous cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de **priorité** dans le portail Microsoft 365 Defender). Changer la priorité d'une stratégie n'a de sens que si vous avez plusieurs stratégies.

**Remarque** :

- Dans le portail Microsoft 365 Defender, vous ne pouvez modifier la priorité de la stratégie de liens Coffre qu’une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle de liaisons sécurisées (qui peut affecter la priorité des règles existantes).
- Coffre les stratégies de liens sont traitées dans l’ordre dans lequel elles sont affichées (la première stratégie a la valeur **De priorité** 0). Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Coffre Links** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Liens**, utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Coffre Liens**, sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie avec la valeur **de priorité** **0** a uniquement l’option **Réduire la priorité** disponible.
   - La stratégie avec la valeur **de priorité** la plus basse (par exemple, **3**) a uniquement l’option **Augmenter la priorité** disponible.
   - Si vous avez au moins trois stratégies, les stratégies entre les valeurs de priorité la plus élevée et la plus basse ont les options **Augmenter la priorité** et Diminuer la **priorité** disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les stratégies de liens Coffre

1. Dans le portail Microsoft 365 Defender, accédez à & stratégies de collaboration \> par **e-mail** & stratégies de **menace** \> **de règles** \> **Coffre liens** dans la section **Stratégies**.

2. Dans la page **Coffre Liens**, sélectionnez une stratégie dans la liste en cliquant sur le nom. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

3. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de liens Coffre

Comme décrit précédemment, une stratégie de liens Coffre se compose d’une stratégie de liens sécurisés et d’une règle de liens sécurisés.

Dans PowerShell, la différence entre les stratégies de liens sécurisés et les règles de liens sécurisés est évidente. Vous gérez les stratégies de liens sécurisés à l’aide **\*des applets de commande -SafeLinksPolicy** , et vous gérez les règles de liens sécurisés à l’aide **\*des applets de commande -SafeLinksRule** .

- Dans PowerShell, vous créez d’abord la stratégie de liens sécurisés, puis vous créez la règle de liens sécurisés qui identifie la stratégie à laquelle la règle s’applique.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie de liens sécurisés et de la règle de liens sécurisés.
- Lorsque vous supprimez une stratégie de liaisons sécurisées de PowerShell, la règle de liens sécurisés correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-safe-links-policies"></a>Utiliser PowerShell pour créer des stratégies de liens Coffre

La création d’une stratégie de liens Coffre dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de liens sécurisés.
2. Créez la règle de liens sécurisés qui spécifie la stratégie de liens sécurisés à laquelle la règle s’applique.

> [!NOTE]
>
> - Vous pouvez créer une règle de liens sécurisés et lui attribuer une stratégie de liens sécurisés non associée existante. Une règle de liens sécurisés ne peut pas être associée à plusieurs stratégies de liens sécurisés.
>
> - Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de liens sécurisés dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
>   - Créez la nouvelle stratégie comme désactivée (_activée_ `$false` sur l’applet de commande **New-SafeLinksRule** ).
>   - Définissez la priorité de la stratégie lors de la création (_priorité__\<Number\>_) sur l’applet de commande **New-SafeLinksRule**).
>
> - Une nouvelle stratégie de liens sécurisés que vous créez dans PowerShell n’est pas visible dans le portail Microsoft 365 Defender tant que vous n’avez pas affecté la stratégie à une règle de liens sécurisés.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de liens sécurisés

Pour créer une stratégie de liens sécurisés, utilisez cette syntaxe :

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Pour plus d’informations sur la syntaxe d’entrée à utiliser pour le paramètre _DoNotRewriteUrls_ , consultez [la syntaxe Entry pour la liste « Ne pas réécrire les URL suivantes](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list) ».
>
> - Pour obtenir une syntaxe supplémentaire que vous pouvez utiliser pour le paramètre _DoNotRewriteUrls_ lorsque vous modifiez des stratégies de liens sécurisés existantes à l’aide de l’applet de commande **Set-SafeLinksPolicy** , consultez la section [Utiliser PowerShell pour modifier les stratégies de liens sécurisés](#use-powershell-to-modify-safe-links-policies) plus loin dans cet article.

Cet exemple crée une stratégie de liens sécurisés nommée Contoso All avec les valeurs suivantes :

- Activez l’analyse et la réécriture d’URL dans les messages électroniques.
- Activez l’analyse d’URL dans Teams.
- Activez l’analyse en temps réel des URL cliqués, y compris les liens cliqués qui pointent vers des fichiers.
- Attendez que l’analyse d’URL se termine avant de remettre le message.
- Activez l’analyse et la réécriture d’URL pour les messages internes.
- Suivez les clics des utilisateurs liés à Coffre Protection des liens (nous n’utilisons pas le paramètre _TrackUserClicks_, et la valeur par défaut est $true).
- N’autorisez pas les utilisateurs à cliquer sur l’URL d’origine.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle de liens sécurisés

Pour créer une règle de liens sécurisés, utilisez cette syntaxe :

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Cet exemple crée une règle de liens sécurisés nommée Contoso All avec les conditions suivantes :

- La règle est associée à la stratégie de liens sécurisés nommée Contoso All.
- La règle s’applique à tous les destinataires du domaine contoso.com.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.
- La règle est activée (nous n’utilisons pas le paramètre _Activé_ , et la valeur par défaut est `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez New-SafeLinksRule](/powershell/module/exchange/new-safelinksrule).

### <a name="use-powershell-to-view-safe-links-policies"></a>Utiliser PowerShell pour afficher les stratégies de liens sécurisés

Pour afficher les stratégies de liens fiables existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeLinksPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple retourne une liste récapitulative de toutes les stratégies de liens sécurisés.

```PowerShell
Get-SafeLinksPolicy | Format-Table Name
```

Cet exemple retourne des informations détaillées pour la stratégie de liens sécurisés nommée Contoso Executives.

```PowerShell
Get-SafeLinksPolicy -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Get-SafeLinksPolicy](/powershell/module/exchange/get-safelinkspolicy).

### <a name="use-powershell-to-view-safe-links-rules"></a>Utiliser PowerShell pour afficher les règles de liens sécurisés

Pour afficher les règles de liens fiables existantes, utilisez la syntaxe suivante :

```PowerShell
Get-SafeLinksRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple retourne une liste récapitulative de toutes les règles de liens fiables.

```PowerShell
Get-SafeLinksRule | Format-Table Name,State
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-SafeLinksRule -State Disabled
```

```PowerShell
Get-SafeLinksRule -State Enabled
```

Cet exemple retourne des informations détaillées sur la règle de liens sécurisés nommée Contoso Executives.

```PowerShell
Get-SafeLinksRule -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez Get-SafeLinksRule](/powershell/module/exchange/get-safelinksrule).

### <a name="use-powershell-to-modify-safe-links-policies"></a>Utiliser PowerShell pour modifier des stratégies de liens sécurisés

Vous ne pouvez pas renommer une stratégie de liens sécurisés dans PowerShell (l’applet **de commande Set-SafeLinksPolicy** n’a aucun paramètre _Name_ ). Lorsque vous renommez une stratégie de liens Coffre dans le portail Microsoft 365 Defender, vous renommez uniquement la _règle_ de liens sécurisés.

La seule considération supplémentaire pour modifier les stratégies de liens sécurisés dans PowerShell est la syntaxe disponible pour le paramètre _DoNotRewriteUrls_ (la [liste « Ne pas réécrire les URL suivantes »)](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) :

- Pour ajouter des valeurs qui remplaceront les entrées existantes, utilisez la syntaxe suivante : `"Entry1","Entry2,..."EntryN"`.
- Pour ajouter ou supprimer des valeurs sans affecter d’autres entrées existantes, utilisez la syntaxe suivante : `@{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}`

Sinon, les mêmes paramètres sont disponibles lorsque vous créez une stratégie de liens sécurisés, comme décrit à [l’étape 1 : Utiliser PowerShell pour créer une section de stratégie de liens sécurisés](#step-1-use-powershell-to-create-a-safe-links-policy) plus haut dans cet article.

Pour modifier une stratégie de liens sécurisés, utilisez cette syntaxe :

```PowerShell
Set-SafeLinksPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy).

### <a name="use-powershell-to-modify-safe-links-rules"></a>Utiliser PowerShell pour modifier les règles de liens sécurisés

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de liens sécurisés dans PowerShell est le paramètre _Activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver des règles de liens fiables existantes, consultez la section suivante.

Sinon, les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à [l’étape 2 : Utiliser PowerShell pour créer une section de règle de liens sécurisés](#step-2-use-powershell-to-create-a-safe-links-rule) plus haut dans cet article.

Pour modifier une règle de liens sécurisés, utilisez cette syntaxe :

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Utiliser PowerShell pour activer ou désactiver des règles de liens sécurisés

L’activation ou la désactivation d’une règle de liens sécurisés dans PowerShell active ou désactive l’ensemble de la stratégie de liens Coffre (la règle de liaisons sécurisées et la stratégie de liens sécurisés affectée).

Pour activer ou désactiver une règle de liens sécurisés dans PowerShell, utilisez cette syntaxe :

```PowerShell
<Enable-SafeLinksRule | Disable-SafeLinksRule> -Identity "<RuleName>"
```

Cet exemple montre comment désactiver la règle de liaisons sécurisées nommée Marketing Department.

```PowerShell
Disable-SafeLinksRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-SafeLinksRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Enable-SafeLinksRule](/powershell/module/exchange/enable-safelinksrule) et [Disable-SafeLinksRule](/powershell/module/exchange/disable-safelinksrule).

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Utiliser PowerShell pour définir la priorité des règles de liaison sécurisée

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d'une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de liens sécurisés dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ sur l’applet de commande **New-SafeLinksRule** .

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-remove-safe-links-policies"></a>Utiliser PowerShell pour supprimer les stratégies de liens sécurisés

Lorsque vous utilisez PowerShell pour supprimer une stratégie de liens sécurisés, la règle de liens sécurisés correspondante n’est pas supprimée.

Pour supprimer une stratégie de liens sécurisés dans PowerShell, utilisez cette syntaxe :

```PowerShell
Remove-SafeLinksPolicy -Identity "<PolicyName>"
```

Cet exemple montre comment supprimer la stratégie de liens sécurisés nommée Marketing Department.

```PowerShell
Remove-SafeLinksPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez Remove-SafeLinksPolicy](/powershell/module/exchange/remove-safelinkspolicy).

### <a name="use-powershell-to-remove-safe-links-rules"></a>Utiliser PowerShell pour supprimer les règles de liens sécurisés

Lorsque vous utilisez PowerShell pour supprimer une règle de liens sécurisés, la stratégie de liens sécurisés correspondante n’est pas supprimée.

Pour supprimer une règle de liens sécurisés dans PowerShell, utilisez cette syntaxe :

```PowerShell
Remove-SafeLinksRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de liens sécurisés nommée Marketing Department.

```PowerShell
Remove-SafeLinksRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez Remove-SafeLinksRule](/powershell/module/exchange/remove-safelinksrule).

Pour vérifier que Coffre Liens analyse les messages, vérifiez les rapports Microsoft Defender pour Office 365 disponibles. Pour plus d’informations, consultez [Afficher les rapports pour Defender pour Office 365](view-reports-for-mdo.md) et [Utiliser l’Explorateur dans le portail Microsoft 365 Defender](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez créé, modifié ou supprimé des stratégies Coffre Liens, effectuez l’une des étapes suivantes :

- Dans la page **liens Coffre** dans le portail <https://security.microsoft.com/safelinksv2>Microsoft 365 Defender, vérifiez la liste des stratégies, leurs valeurs **d’état** et leurs valeurs **de priorité**. Pour afficher plus de détails, sélectionnez la stratégie dans la liste et affichez les détails dans le menu volant.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
