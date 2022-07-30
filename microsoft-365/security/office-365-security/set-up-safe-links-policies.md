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
description: Les administrateurs peuvent apprendre à afficher, créer, modifier et supprimer des stratégies liens sécurisés et des paramètres de liens sécurisés globaux dans Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 48e873550c83154827d7deaa430b75d82ff80acc
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67087262"
---
# <a name="set-up-safe-links-policies-in-microsoft-defender-for-office-365"></a>Configurer les stratégies de la fonctionnalité Liens fiables dans Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Microsoft Defender pour Office 365](defender-for-office-365.md). Si vous êtes un utilisateur à la recherche d’informations sur safelinks dans Outlook, consultez [Advanced Outlook.com security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Les liens sécurisés dans [Microsoft Defender pour Office 365](defender-for-office-365.md) fournissent l’analyse d’URL des messages électroniques entrants dans le flux de courrier, ainsi que l’heure de vérification des URL et des liens dans les messages électroniques et à d’autres emplacements. Pour plus d’informations, consultez [Liens sécurisés dans Microsoft Defender pour Office 365](safe-links.md).

Bien qu’il n’existe aucune stratégie de liens fiables par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens sécurisés à tous les destinataires (utilisateurs qui ne sont pas définis dans des stratégies de sécurité personnalisées ou standard ou strictes). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Vous pouvez également utiliser les procédures décrites dans cet article pour créer des stratégies de liens fiables qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques.

> [!NOTE]
>
> Vous configurez la liste « Bloquer les URL suivantes » dans les paramètres globaux pour la protection des liens sécurisés **en dehors** des stratégies liens sécurisés. Pour obtenir des instructions, consultez [Configurer les paramètres globaux des liens sécurisés dans Microsoft Defender pour Office 365](configure-global-settings-for-safe-links.md).
>
> Les administrateurs doivent prendre en compte les différents paramètres de configuration des liens sécurisés. L’une des options disponibles consiste à inclure des informations d’identification des utilisateurs dans liens sécurisés. Cette fonctionnalité permet aux équipes d’opérations de sécurité (SecOps) d’examiner les compromissions potentielles de l’utilisateur, de prendre des mesures correctives et de limiter les violations coûteuses.

Vous pouvez configurer les politiques Safe Links dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 éligibles avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online, mais avec des abonnements complémentaires Microsoft Defender for Office 365).

Les éléments de base d’une stratégie de liens fiables sont les suivants :

- **Stratégie de liens sécurisés** : activez la protection des liens sécurisés, activez l’analyse des URL en temps réel, spécifiez s’il faut attendre la fin de l’analyse en temps réel avant de remettre le message, activer l’analyse des messages internes, spécifier s’il faut suivre les clics de l’utilisateur sur les URL et spécifier s’il faut autoriser les utilisateurs à cliquer sur l’URL d’origine.
- **Règle de liens sécurisés** : spécifie les filtres de priorité et de destinataire (auxquels la stratégie s’applique).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies liens sécurisés dans le portail Microsoft 365 Defender :

- Lorsque vous créez une stratégie de liens fiables, vous créez en fait une règle de liens fiables et la stratégie de liens fiables associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie de liens fiables, les paramètres liés au nom, à la priorité, activés ou désactivés, et les filtres de destinataire modifient la règle de liens fiables. Tous les autres paramètres modifient la stratégie de liens fiables associée.
- Lorsque vous supprimez une stratégie de liens fiables, la règle de liens fiables et la stratégie de liens fiables associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, consultez la section [Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de liens fiables](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies) plus loin dans cet article.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Vous devez disposer d’autorisations pour pouvoir effectuer les procédures décrites dans cet article :
  - Pour créer, modifier et supprimer des stratégies de liens fiables, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** dans le portail Microsoft 365 Defender **et** membre du groupe de **rôles Gestion de l’organisation** dans Exchange Online.
  - Pour accéder en lecture seule aux stratégies Liens sécurisés, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md) et [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  . - Le groupe de rôles **Gestion de l’organisation en mode affichage uniquement** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) donne également un accès en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies liens fiables, consultez [les paramètres de stratégie Liens sécurisés](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- Autorisez jusqu’à 6 heures l’application d’une stratégie nouvelle ou mise à jour.

- [De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft Defender pour Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). À mesure que de nouvelles fonctionnalités sont ajoutées, vous devrez peut-être apporter des ajustements à vos stratégies de liens fiables existantes.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies de liens fiables

La création d’une stratégie de liens fiables personnalisée dans le portail Microsoft 365 Defender crée la règle de liens sécurisés et la stratégie de liens sécurisés associée en même temps en utilisant le même nom pour les deux.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies **de menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Liens sécurisés** , cliquez sur ![l’icône Créer.](../../media/m365-cc-sc-create-icon.png) **Création**.

3. L’assistant **Nouvelle stratégie de liens fiables** s’ouvre. Dans la page **Nommer votre** stratégie, configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs et domaines** qui s’affiche, identifiez les destinataires internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
   - **Groupes** :
     - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
     - Groupes Microsoft 365 spécifiée
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : Pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s'applique (exceptions des destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   > [!IMPORTANT]
   > Plusieurs types différents de conditions ou d’exceptions ne sont pas additifs ; ils sont inclusifs. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
   >
   > - Le destinataire est : romain@contoso.com
   > - Le destinataire est membre de : Exécutifs
   >
   > La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
   >
   > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur **l’URL & cliquez sur la page des paramètres de protection** qui s’affiche, configurez les paramètres suivants :

   - **Action sur les URL potentiellement malveillantes dans la section e-mails** :
     - **Activé : liens sécurisés vérifie une liste de liens connus et malveillants lorsque les utilisateurs cliquent sur des liens dans l’e-mail** : sélectionnez cette option pour activer la protection des liens sécurisés pour les liens dans les messages électroniques. Si vous sélectionnez cette option, les paramètres suivants sont disponibles :
       - **Appliquer des liens sécurisés aux messages électroniques envoyés au sein de l’organisation** : sélectionnez cette option pour appliquer la stratégie Liens sécurisés aux messages entre les expéditeurs internes et les destinataires internes.
       - **Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** : sélectionnez cette option pour activer l’analyse en temps réel des liens dans les messages électroniques. Si vous sélectionnez cette option, le paramètre suivant est disponible :
         - **Attendez la fin de l’analyse d’URL avant de remettre le message** : sélectionnez cette option pour attendre la fin de l’analyse d’URL en temps réel avant de remettre le message.
       - **Ne réécrivez pas les URL, effectuez des vérifications via l’API SafeLinks uniquement** : sélectionnez cette option pour empêcher l’habillage d’URL. Les liens sécurisés sont appelés exclusivement par le biais d’API au moment du clic d’URL par les clients Outlook qui la prennent en charge.

       - **Ne réécrivez pas les URL suivantes dans la section e-mail** : Cliquez sur **Gérer (nn) URL** pour autoriser l’accès à des URL spécifiques qui seraient autrement bloquées par des liens fiables.

         > [!NOTE]
         > Les entrées de la liste « Ne pas réécrire les URL suivantes » ne sont pas analysées ou encapsulées par des liens fiables pendant le flux de courrier. Utilisez [les entrées d’URL d’autorisation dans la liste d’autorisations/blocages du locataire](allow-block-urls.md#create-allow-url-entries) afin que les URL ne soient pas analysées ou encapsulées par des liens sécurisés pendant le flux de messagerie _et_ au moment du clic.

     1. Dans gérer **les URL pour ne pas réécrire** le menu volant qui s’affiche, cliquez sur ![l’icône Ajouter des URL.](../../media/m365-cc-sc-create-icon.png) **Ajoutez des URL**.
     2. Dans le menu volant **Ajouter des URL** qui s’affiche, tapez l’URL ou la valeur souhaitée, sélectionnez l’entrée qui apparaît sous la zone, puis cliquez sur **Enregistrer**. Répétez cette étape autant de fois que nécessaire.

        Pour la syntaxe d’entrée, consultez [la syntaxe Entrée pour la liste « Ne pas réécrire les URL suivantes](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list) ».

        Pour supprimer une entrée, cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de l’entrée.

        Lorsque vous avez terminé, cliquez sur **Enregistrer**.

     3. De retour sur les **URL Gérer pour ne pas réécrire** le menu volant, cliquez sur **Terminé** ou effectuez la maintenance dans la liste des entrées :

        Pour supprimer des entrées de la liste, vous pouvez utiliser l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher l’entrée.

        Pour sélectionner une seule entrée, cliquez sur la valeur dans la colonne **URL** .

        Pour sélectionner plusieurs entrées une par une, cliquez sur la zone vide à gauche de la valeur.

        Pour sélectionner toutes les entrées, cliquez sur la zone vide à gauche de l’en-tête de colonne **URL** .

        Une ou plusieurs entrées sélectionnées, cliquez sur le bouton ![Icône Ajouter des URL.](../../media/m365-cc-sc-create-icon.png) ou ![Icône Effacer.](../../media/m365-cc-sc-delete-icon.png) icônes qui s’affichent.

        Lorsque vous avez terminé, cliquez sur **Terminé**.

   - **Actions pour les URL potentiellement malveillantes dans la section Microsoft Teams** :
     - **Activé : Liens fiables vérifie une liste de liens connus et malveillants lorsque les utilisateurs cliquent sur des liens dans Microsoft Teams** : sélectionnez cette option pour activer la protection des liens sécurisés pour les liens dans Teams. Notez que l’application de ce paramètre peut prendre jusqu’à 24 heures.

     > [!NOTE]
     > Actuellement, la protection des liens sécurisés pour Microsoft Teams n’est pas disponible dans Microsoft 365 GCC High ou Microsoft 365 DoD.

   - **Actions pour les URL potentiellement malveillantes dans la section Applications Microsoft Office** :
     - **Activé : Liens fiables vérifie une liste de liens connus et malveillants lorsque les utilisateurs cliquent sur des liens dans les applications Microsoft Office** : sélectionnez cette option pour activer la protection des liens sécurisés pour les liens dans les fichiers dans les applications de bureau, mobiles et web Office prises en charge.

   - **Cliquez sur la section Paramètres de protection** :
     - **Suivre les clics de l’utilisateur** : laissez cette option sélectionnée pour activer le suivi des clics de l’utilisateur sur les URL. Si vous sélectionnez cette option, les options suivantes sont disponibles :
       - **Permettre aux utilisateurs de cliquer sur l’URL d’origine** : désactivez cette option pour empêcher les utilisateurs de cliquer sur l’URL d’origine dans les [pages d’avertissement](safe-links.md#warning-pages-from-safe-links).
       - **Afficher la personnalisation de l’organisation sur les pages de notification et d’avertissement** : pour plus d’informations sur la personnalisation de la personnalisation, consultez [Personnaliser le thème Microsoft 365 pour votre organisation](../../admin/setup/customize-your-organization-theme.md).

   Pour plus d’informations sur ces paramètres, consultez :

   - [Paramètres liens sécurisés pour les messages électroniques](safe-links.md#safe-links-settings-for-email-messages).
   - [Paramètres liens sécurisés pour Microsoft Teams](safe-links.md#safe-links-settings-for-microsoft-teams).
   - [Paramètres liens sécurisés pour les applications Office](safe-links.md#safe-links-settings-for-office-apps).
   - [Cliquez sur paramètres de protection dans les stratégies Liens fiables](safe-links.md#click-protection-settings-in-safe-links-policies)

   Pour plus d’informations sur les valeurs recommandées pour les paramètres de stratégie Standard et Strict, consultez [les paramètres de stratégie Liens sécurisés](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Notification** qui s’affiche, sélectionnez l’une des valeurs suivantes pour **Comment voulez-vous informer vos utilisateurs ?** :
   - **Utiliser le texte de notification par défaut**
   - **Utilisez le texte de notification personnalisé** : si vous sélectionnez cette valeur, les paramètres suivants s’affichent :
     - **Utiliser Traducteur Microsoft pour la localisation automatique**
     - **Texte de notification personnalisée** : entrez le texte de notification personnalisé dans cette zone (la longueur ne peut pas dépasser 200 caractères).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

8. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies liens fiables

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies **de menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Liens sécurisés** , les propriétés suivantes s’affichent dans la liste des stratégies liens fiables :
   - **Name**
   - **État**
   - **Priorité**

3. Lorsque vous sélectionnez une stratégie en cliquant sur le nom, les paramètres de stratégie s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les stratégies liens fiables

1. Dans le portail Microsoft 365 Defender, accédez à la section **Stratégies & règles sur les stratégies** \> de **menace** \> **,** liens \> **sécurisés**.

2. Dans la page **Liens sécurisés** , sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez la section [Précédente Utiliser le portail Microsoft 365 Defender pour créer des stratégies liens fiables](#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) dans cet article.

Pour activer ou désactiver une stratégie ou définir l’ordre de priorité de la stratégie, consultez les sections suivantes.

### <a name="enable-or-disable-safe-links-policies"></a>Activer ou désactiver des stratégies de liens fiables

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies **de menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Liens sécurisés** , sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-safe-links-policies"></a>Définir la priorité des stratégies de liens fiables

Par défaut, les liens sécurisés reçoivent une priorité basée sur l’ordre dans lequel ils ont été créés (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour modifier la priorité d'une stratégie, vous cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de **priorité** dans le portail Microsoft 365 Defender). Changer la priorité d'une stratégie n'a de sens que si vous avez plusieurs stratégies.

**Remarque** :

- Dans le portail Microsoft 365 Defender, vous ne pouvez modifier la priorité de la stratégie Liens sécurisés qu’une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle de liaisons sécurisées (qui peut affecter la priorité des règles existantes).
- Les stratégies liens sécurisés sont traitées dans l’ordre dans lequel elles sont affichées (la première stratégie a la valeur **Priorité** 0). Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> & stratégies **de menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**. Pour accéder directement à la page **Liens fiables** , utilisez <https://security.microsoft.com/safelinksv2>.

2. Dans la page **Liens sécurisés** , sélectionnez une stratégie dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie avec la valeur **de priorité** **0** a uniquement l’option **Réduire la priorité** disponible.
   - La stratégie avec la valeur **de priorité** la plus basse (par exemple, **3**) a uniquement l’option **Augmenter la priorité** disponible.
   - Si vous avez au moins trois stratégies, les stratégies entre les valeurs de priorité la plus élevée et la plus basse ont les options **Augmenter la priorité** et Diminuer la **priorité** disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-links-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les stratégies liens sécurisés

1. Dans le portail Microsoft 365 Defender, accédez à Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **des règles** \> **liens sécurisés** dans la section **Stratégies**.

2. Dans la page **Liens sécurisés** , sélectionnez une stratégie dans la liste en cliquant sur le nom. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

3. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-links-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de liens fiables

Comme décrit précédemment, une stratégie liens sécurisés se compose d’une stratégie de liens sécurisés et d’une règle de liens sécurisés.

Dans PowerShell, la différence entre les stratégies de liens sécurisés et les règles de liens sécurisés est évidente. Vous gérez les stratégies de liens fiables à l’aide **\*des applets de commande -Stratégie de liens fiables**, et vous gérez les règles de liens fiables à l’aide **\*des applets de commande -Règle de liens fiables** .

- Dans PowerShell, vous créez d'abord la stratégie de liens fiables, puis vous créez la règle de liens fiables qui identifie la stratégie à laquelle la règle s'applique.
- Dans PowerShell, vous modifiez les paramètres de la stratégie et de la règle des liens fiables séparément.
- Lorsque vous supprimez une stratégie de liens fiables dans PowerShell, la règle de liens fiables correspondante n'est pas automatiquement supprimée, et vice versa.

### <a name="use-powershell-to-create-safe-links-policies"></a>Utiliser PowerShell pour créer des stratégies de liens fiables

La création d'une stratégie de liens fiables dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de liens fiables.
2. Créez la règle de liens sécurisés qui spécifie la stratégie de liens sécurisés à laquelle la règle s’applique.

> [!NOTE]
>
> - Vous pouvez créer une nouvelle règle de liens fiables et lui attribuer une stratégie de liens fiables existante et non associée. Une règle de liens sécurisés ne peut pas être fiables à plusieurs stratégies de liens fiables.
>
> - Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de liens fiables dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender jusqu'à ce que vous créiez la stratégie :
>   - Créez la nouvelle stratégie comme désactivée (_activée_ `$false` sur l’applet de commande **New-SafeLinksRule** ).
>   - Définissez la priorité de la stratégie lors de la création (_priorité__\<Number\>_) sur l’applet de commande **New-SafeLinksRule**).
>
> - Une nouvelle stratégie de liens fiables que vous créez dans PowerShell n'est pas visible dans le portail Microsoft 365 Defender tant que vous n'attribuez pas la stratégie à une règle de liens fiables.

#### <a name="step-1-use-powershell-to-create-a-safe-links-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de liens sécurisés

Pour créer une stratégie de liens sécurisés, utilisez cette syntaxe :

```PowerShell
New-SafeLinksPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] [-EnableSafeLinksForEmail <$true | $false>] [-EnableSafeLinksForOffice <$true | $false>] [-EnableSafeLinksForTeams <$true | $false>] [-ScanUrls <$true | $false>] [-DeliverMessageAfterScan <$true | $false>] [-EnableForInternalSenders <$true | $false>] [-AllowClickThrough <$true | $false>] [-TrackUserClicks <$true | $false>] [-DoNotRewriteUrls "Entry1","Entry2",..."EntryN"]
```

> [!NOTE]
>
> - Pour plus d’informations sur la syntaxe d’entrée à utiliser pour le paramètre _DoNotRewriteUrls_ , consultez [la syntaxe Entry pour la liste « Ne pas réécrire les URL suivantes](safe-links.md#entry-syntax-for-the-do-not-rewrite-the-following-urls-list) ».
>
> - Pour obtenir une syntaxe supplémentaire que vous pouvez utiliser pour le paramètre _DoNotRewriteUrls_ lorsque vous modifiez des stratégies de liens sécurisés existantes à l’aide de l’applet de commande **Set-SafeLinksPolicy** , consultez la section [Utiliser PowerShell pour modifier les stratégies de liens sécurisés](#use-powershell-to-modify-safe-links-policies) plus loin dans cet article.

Cet exemple crée une stratégie de liens sécurisés nommée Contoso All avec les valeurs suivantes :

- Activez l’analyse d’URL et la réécriture d’URL dans les messages électroniques.
  - Activez l’analyse et la réécriture d’URL pour les messages internes.
  - Activez l’analyse en temps réel des URL cliqués, y compris les liens cliqués qui pointent vers des fichiers.
    - Attendez la fin de l'analyse des URL avant de délivrer le message.
- Activez l’analyse d’URL dans Teams.
- Activez l’analyse des URL dans les applications Office prises en charge.
- Suivez les clics utilisateur liés à la protection des liens sécurisés (nous n’utilisons pas le paramètre _TrackUserClicks_ , et la valeur par défaut est $true).
- N’autorisez pas les utilisateurs à cliquer sur l’URL d’origine.

```PowerShell
New-SafeLinksPolicy -Name "Contoso All" -EnableSafeLinksForEmail $true -EnableSafeLinksForOffice $true -EnableSafeLinksForTeams $true -ScanUrls $true -DeliverMessageAfterScan $true -EnableForInternalSenders $true -AllowClickThrough $false
```

Pour obtenir des informations détaillées sur la syntaxe et les [paramètres, consultez New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy).

#### <a name="step-2-use-powershell-to-create-a-safe-links-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle de liens sécurisés

Pour créer une règle de liens sécurisés, utilisez cette syntaxe :

```PowerShell
New-SafeLinksRule -Name "<RuleName>" -SafeLinksPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

Cet exemple crée une règle de liens sécurisés nommée Contoso All avec les conditions suivantes :

- La règle est associée à la stratégie de liens fiables nommée Contoso All.
- La règle s'applique à tous les destinataires dans le domaine contoso.com.
- Étant donné que nous n’utilisons pas le paramètre _Priority_ , la priorité par défaut est utilisée.
- La règle est activée (nous n’utilisons pas le paramètre _Activé_ , et la valeur par défaut est `$true`).

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Cet exemple crée une règle de liens sécurisés similaire à l’exemple précédent, mais dans cet exemple, la règle s’applique aux destinataires dans tous les domaines acceptés de l’organisation.

```powershell
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

Cet exemple crée une règle de liens sécurisés similaire aux exemples précédents, mais dans cet exemple, la règle s’applique aux destinataires dans les domaines spécifiés dans un fichier .csv.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
New-SafeLinksRule -Name "Contoso All" -SafeLinksPolicy "Contoso All" -RecipientDomainIs $SLDomains
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

Vous ne pouvez pas renommer une stratégie de liens sécurisés dans PowerShell (l’applet **de commande Set-SafeLinksPolicy** n’a aucun paramètre _Name_ ). Lorsque vous renommez une stratégie Liens sécurisés dans le portail Microsoft 365 Defender, vous renommez uniquement la _règle_ des liens sécurisés.

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

Cet exemple ajoute tous les domaines acceptés dans l’organisation en tant que condition à la règle de liens sécurisés nommée Contoso All.

```powershell
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs (Get-AcceptedDomain).Name
```

Cet exemple montre comment ajouter les domaines du .csv spécifié en tant que condition à la règle de liaisons sécurisées nommée Contoso All.

```powershell
$Data = Import-Csv -Path "C:\Data\SafeLinksDomains.csv"
$SLDomains = $Data.Domains
Set-SafeLinksRule -Identity "Contoso All" -RecipientDomainIs $SLDomains
```

Pour obtenir des informations détaillées sur la syntaxe et [les paramètres, consultez Set-SafeLinksRule](/powershell/module/exchange/set-safelinksrule).

### <a name="use-powershell-to-enable-or-disable-safe-links-rules"></a>Utiliser PowerShell pour activer ou désactiver des règles de liens sécurisés

L’activation ou la désactivation d’une règle de liens sécurisés dans PowerShell active ou désactive l’ensemble de la stratégie liens fiables (la règle de liens sécurisés et la stratégie de liens fiables attribuée).

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

### <a name="use-powershell-to-set-the-priority-of-safe-links-rules"></a>Utiliser PowerShell pour déterminer la priorité des règles de liens fiables.

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d'une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour déterminer la priorité d’une règle de liens fiables dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-SafeLinksRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-SafeLinksRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
> Pour définir la priorité d'une nouvelle règle lors de sa création, utilisez le paramètre _Priorité_ dans la cmdlet **New-SafeLinksRule**.

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

Pour vérifier que les liens fiables analysent les messages, vérifiez les rapports Microsoft Defender pour Office 365 disponibles. Pour plus d’informations, consultez [Afficher les rapports pour Defender pour Office 365](view-reports-for-mdo.md) et [Utiliser l’Explorateur dans le portail Microsoft 365 Defender](threat-explorer.md).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement créé, modifié ou supprimé des stratégies liens fiables, effectuez l’une des étapes suivantes :

- Dans la page **Liens sécurisés** du portail <https://security.microsoft.com/safelinksv2>Microsoft 365 Defender, vérifiez la liste des stratégies, leurs valeurs **d’état** et leurs valeurs **de priorité**. Pour afficher plus de détails, sélectionnez la stratégie dans la liste et affichez les détails dans le menu volant.

- Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell, remplacez \<Name\> par le nom de la stratégie ou de la règle, exécutez la commande suivante et vérifiez les paramètres :

  ```PowerShell
  Get-SafeLinksPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-SafeLinksRule -Identity "<Name>"
  ```
