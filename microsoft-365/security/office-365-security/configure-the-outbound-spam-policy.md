---
title: Configurer le filtrage du courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à afficher, créer, modifier et supprimer des stratégies de courrier indésirable sortant dans Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ceaf0d276aff4504dd34aa3229c28c9cb042742d
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204578"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Configurer le filtrage du courrier indésirable sortant dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou dans des organisations Exchange Online Protection autonomes (EOP) sans boîte aux lettres Exchange Online, les messages électroniques sortants envoyés via EOP sont automatiquement vérifiés pour le courrier indésirable et l’activité d’envoi inhabituelle.

Le courrier indésirable sortant provenant d’un utilisateur de votre organisation indique généralement un compte compromis. Les messages sortants suspects sont marqués comme courrier indésirable (quel que soit le niveau de confiance du courrier indésirable ou SCL) et sont acheminés via le pool de remise à risque élevé pour protéger la réputation du service [(c’est-à-dire,](high-risk-delivery-pool-for-outbound-messages.md) empêcher les serveurs de messagerie source Microsoft 365 des listes d’adresses IP bloqués). Les administrateurs sont automatiquement avertis de l’activité de courrier sortant suspecte et des utilisateurs bloqués via les stratégies [d’alerte.](../../compliance/alert-policies.md)

EOP utilise des stratégies de courrier indésirable sortant dans le cadre de la protection globale de votre organisation contre le courrier indésirable. Pour plus d’informations, voir [Protection contre le courrier indésirable](anti-spam-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie de courrier indésirable sortant par défaut. Pour plus de granularité, vous pouvez également créer des stratégies de courrier indésirable sortant personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies de courrier indésirable sortant dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

Les éléments de base d’une stratégie de courrier indésirable sortant dans EOP sont :

- **La stratégie de filtrage du** courrier indésirable sortant : spécifie les actions pour les verdicts de filtrage du courrier indésirable sortant et les options de notification.
- **La règle de filtrage du** courrier indésirable sortant : spécifie la priorité et les filtres de destinataires (à qui la stratégie s’applique) pour une stratégie de filtrage du courrier indésirable sortant.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez les polices de courrier indésirable sortant dans le Centre de sécurité & conformité :

- Lorsque vous créez une stratégie, vous créez en fait une règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres liés au nom, à la priorité, activé ou désactivé et aux filtres de destinataire modifient la règle de filtrage du courrier indésirable sortant. Tous les autres paramètres modifient la stratégie de filtrage du courrier indésirable sortant associée.
- Lorsque vous supprimez une stratégie, la règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, voir la section Utiliser Exchange Online PowerShell ou [EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) autonome pour configurer les stratégies de courrier indésirable sortant plus loin dans cet article.

Chaque organisation dispose d’une stratégie de courrier indésirable sortant intégrée nommée Default qui possède les propriétés ci-après :

- La stratégie est appliquée à tous les destinataires de l’organisation, même si aucune règle de filtrage du courrier indésirable sortant (filtres de destinataires) n’est associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée que la stratégie nommée Par défaut.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour accroître l’efficacité du filtrage du courrier indésirable sortant, vous pouvez créer des stratégies de courrier indésirable sortant personnalisées avec des paramètres plus stricts qui sont appliqués à des utilisateurs ou des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter, modifier et supprimer des stratégies de courrier  indésirable sortant, vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour accéder en lecture seule aux stratégies de courrier  indésirable sortant, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité. 

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour obtenir nos paramètres recommandés pour les stratégies de courrier indésirable sortant, consultez les paramètres de stratégie de filtrage du courrier indésirable sortant [EOP.](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings)

- Les [](../../compliance/alert-policies.md) stratégies d’alerte par défaut nommées Limite d’envoi de courrier électronique ont été **dépassées,** des modèles d’envoi de courrier suspects ont été détectés et l’utilisateur ne peut pas envoyer de courrier électronique envoie déjà des notifications par courrier électronique aux membres du groupe  **TenantAdmins** (Administrateurs globaux) concernant l’activité inhabituelle de courrier sortant et les **utilisateurs** bloqués en raison du courrier indésirable sortant. Pour plus d’informations, [voir Vérifier les paramètres d’alerte pour les utilisateurs restreints.](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users) Nous vous recommandons d’utiliser ces stratégies d’alerte au lieu des options de notification dans les stratégies de courrier indésirable sortant.

## <a name="use-the-security--compliance-center-to-create-outbound-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant personnalisée dans le Centre de sécurité & conformité crée la règle de filtrage du courrier indésirable et la stratégie de filtrage du courrier indésirable associée en utilisant le même nom pour les deux.

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur **Créer une stratégie sortante.**

3. Dans la **stratégie de filtrage du courrier indésirable** sortant qui s’ouvre, configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

4. (Facultatif) Développez la section **Notifications** pour configurer des utilisateurs supplémentaires devant recevoir des copies et des notifications de messages électroniques sortants suspects :

   - **Envoyer une copie des messages** électroniques sortants suspects à des personnes spécifiques : ce paramètre ajoute les utilisateurs spécifiés en tant que destinataires Bcc aux messages sortants suspects.

     > [!NOTE]
     > Ce paramètre fonctionne uniquement dans la stratégie de courrier indésirable sortant par défaut. Elle ne fonctionne pas dans les stratégies de courrier indésirable sortant personnalisées que vous créez.

     Pour activer ce paramètre :

     1. Activez la case à cocher pour activer le paramètre.

     1. Cliquez **sur Ajouter des personnes.** Dans le **volant Ajouter ou supprimer des destinataires** qui s’affiche :

     1. Entrez l’adresse de courrier de l’expéditeur. Vous pouvez spécifier plusieurs adresses de messagerie séparées par des points-virgules (;) ou un destinataire par ligne.

     1. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les destinataires.

        Répétez ces étapes autant de fois que nécessaire.

        Les destinataires que vous avez ajoutés apparaissent dans la section **Liste des** destinataires du volet volant. Pour supprimer un destinataire, cliquez sur ![ Supprimer le bouton ](../../media/scc-remove-icon.png) .

     1. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

        Pour désactiver ce paramètre, désactivez la case à cocher.

   - **Informez des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant**:

     > [!IMPORTANT]
     >
     > - Ce paramètre est en train d’être supprimé des stratégies de courrier indésirable sortant.
     >
     > - La [](../../compliance/alert-policies.md) stratégie d’alerte par défaut nommée User **restricted from sending email** already sends email notifications to members of the **TenantAdmins** (**Global admins**) group when users are blocked due to exceeding the limits in the **Recipient Limits** section. **Nous vous recommandons vivement d’utiliser** la stratégie d’alerte plutôt que ce paramètre dans la stratégie de courrier indésirable sortant pour avertir les administrateurs et les autres utilisateurs. Pour obtenir des instructions, [voir Vérifier les paramètres d’alerte pour les utilisateurs restreints.](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users)

5. (Facultatif) Développez la section **Limites des destinataires** pour configurer les limites et les actions pour les messages électroniques sortants suspects :

   > [!NOTE]
   > Ces paramètres s’appliquent uniquement aux boîtes aux lettres en nuage.

   - **Nombre maximal de destinataires par utilisateur**

     Une valeur valide est de 0 à 10 000. La valeur par défaut est 0, ce qui signifie que les valeurs par défaut du service sont utilisées. Pour plus d’informations, voir [Limites d’envoi.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1)

     - **Limite horaire externe :** nombre maximal de destinataires externes par heure.

     - **Limite horaire interne :** nombre maximal de destinataires internes par heure.

     - **Limite quotidienne**: nombre total maximal de destinataires par jour.

   - **Action lorsqu’un utilisateur dépasse** les limites ci-dessus : Configurez l’action à prendre lorsqu’une des **limites** de destinataire est dépassée. Pour toutes les actions, les  destinataires spécifiés dans l’utilisateur ne  peuvent pas envoyer de stratégie d’alerte de courrier électronique (et, désormais, redondants, notifier des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant dans la stratégie de courrier indésirable sortant reçoivent des notifications par courrier électronique.

     - **Empêchez l’utilisateur d’envoyer des messages jusqu’au jour suivant**: il s’agit de la valeur par défaut. Des notifications par courrier électronique sont envoyées et l’utilisateur ne pourra plus envoyer de messages avant le jour suivant, en fonction de l’heure UTC. Il n’existe aucun moyen pour l’administrateur de remplacer ce bloc.

       - L’alerte d’activité nommée **Utilisateur limité à l’envoi** de courriers électroniques avertit les administrateurs (par courrier électronique et sur la page Afficher **les alertes).**

       - Tous les destinataires spécifiés dans la stratégie **Notifier** des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant dans la stratégie sont également avertis.

       - L’utilisateur ne pourra plus envoyer de messages avant le jour suivant, en fonction de l’heure UTC. Il n’existe aucun moyen pour l’administrateur de remplacer ce bloc.

     - Empêcher l’utilisateur d’envoyer des messages électroniques : des notifications par courrier électronique sont envoyées, l’utilisateur est ajouté au portail [Utilisateurs  **restreints] <https://sip.protection.office.com/restrictedusers>** dans le Centre de sécurité & conformité et l’utilisateur ne peut pas envoyer de courrier tant qu’il n’a pas été supprimé du portail Utilisateurs restreints par un administrateur. Une fois qu’un administrateur a supprimé l’utilisateur de la liste, il ne sera plus restreint pour ce jour. Pour obtenir des instructions, consultez La suppression d’un utilisateur du portail Utilisateurs restreints [après l’envoi de courrier indésirable.](removing-user-from-restricted-users-portal-after-spam.md)

     - **Aucune action, alerte uniquement :** les notifications par courrier électronique sont envoyées.

6. (Facultatif) Développez la section **De forwarding automatique** pour contrôler le forwarding automatique des messages électroniques par les utilisateurs vers des expéditeurs externes. Pour plus d’informations, voir [Control automatic external email forwarding in Microsoft 365](external-email-forwarding.md).

   > [!NOTE]
   >
   > - Avant septembre 2020, ces paramètres sont disponibles mais ne sont pas appliqués.
   >
   > - Ces paramètres s’appliquent uniquement aux boîtes aux lettres en nuage.
   >
   > - Lorsque le forwarding automatique est désactivé, le destinataire reçoit une note de non-remise (également appelée NDR ou bounce message) si des expéditeurs externes envoient des courriers électroniques à une boîte aux lettres sur place. Si le message est envoyé  par un expéditeur interne et que la méthode de forwarding est le [forwarding](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) de boîte aux lettres (également appelé « _forwarding SMTP_», l’expéditeur interne reçoit la NDR. L’expéditeur interne ne reçoit pas de rapport de non-réception si le forwarding s’est produit en raison d’une règle de boîte de réception.

   Les valeurs disponibles sont :

   - **Automatique - Contrôlé par le système**: permet au filtrage du courrier indésirable sortant de contrôler le transport automatique du courrier externe. Il s’agit de la valeur par défaut.
   - **On**: le forwarding automatique du courrier externe n’est pas désactivé par la stratégie.
   - **Désactivé**: tous les envois automatiques de courrier externe sont désactivés par la stratégie.

7. (Obligatoire) Développez la section **Appliqué à** pour identifier les expéditeurs internes à qui la stratégie s’applique.

    Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<sender1\>_ ou _\<sender2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<sender1\>_ et _\<member of group 1\>_).

    Il est plus facile de cliquer sur **Ajouter une condition** trois fois pour afficher toutes les conditions disponibles. Vous pouvez cliquer sur le ![bouton Supprimer](../../media/scc-remove-icon.png) pour supprimer les conditions que vous ne voulez pas configurer.

    - **Le domaine de l’expéditeur** est : Spécifie les expéditeurs dans un ou plusieurs des domaines acceptés configurés dans l’organisation. Cliquez dans la zone **Ajouter un indicateur** pour afficher et sélectionner un domaine. Cliquez de nouveau sur la zone **Ajouter un indicateur** pour sélectionner d’autres domaines si plusieurs domaines sont disponibles.

    - **L’expéditeur est**: spécifie un ou plusieurs utilisateurs dans votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez à nouveau **sur la zone Ajouter une** balise pour sélectionner des expéditeurs supplémentaires.

    - **L’expéditeur est membre de**: Spécifie un ou plusieurs groupes dans votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez à nouveau **sur la zone Ajouter une** balise pour sélectionner des expéditeurs supplémentaires.

    - **Sauf si**: pour ajouter des exceptions à la règle, cliquez sur **Ajouter une condition** trois fois pour afficher toutes les exceptions disponibles. Les paramètres et le comportement sont exactement comme les conditions.

8. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-view-outbound-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour afficher les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur Développer l’icône ![ pour développer une stratégie de courrier indésirable sortant ](../../media/scc-expand-icon.png) :

   - Stratégie par défaut nommée **Stratégie de filtrage du courrier indésirable sortant.**

   - Une stratégie personnalisée que vous avez créée lorsque la valeur dans la colonne **Type** est **Stratégie personnalisée de** courrier indésirable sortant .

3. Les paramètres de stratégie s’affichent dans les détails de stratégie étendus qui s’affichent, ou vous pouvez cliquer sur **Modifier la stratégie.**

## <a name="use-the-security--compliance-center-to-modify-outbound-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour modifier les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur Développer l’icône ![ pour développer une stratégie de courrier indésirable sortant ](../../media/scc-expand-icon.png) :

   - Stratégie par défaut nommée **Stratégie de filtrage du courrier indésirable sortant.**

   - Une stratégie personnalisée que vous avez créée lorsque la valeur dans la colonne **Type** est **Stratégie personnalisée de** courrier indésirable sortant .

3. Cliquez sur **Modifier une stratégie**.

Pour les stratégies de courrier indésirable sortant personnalisées, les paramètres disponibles dans le volant qui s’affiche sont identiques à ceux décrits dans la section Utiliser le Centre de sécurité [&](#use-the-security--compliance-center-to-create-outbound-spam-policies) conformité pour créer des stratégies de courrier indésirable sortant.

Pour la stratégie de courrier indésirable sortant par défaut nommée Stratégie de filtrage du courrier indésirable **sortant,** la **section** Appliqué à n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie, définir l’ordre de priorité de la stratégie ou configurer les notifications de mise en quarantaine de l’utilisateur final, voir les sections suivantes.

### <a name="enable-or-disable-outbound-spam-policies"></a>Activer ou désactiver les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur Développer l’icône pour développer une stratégie personnalisée que vous avez créée (la valeur dans la colonne Type est Stratégie personnalisée de courrier indésirable ![ ](../../media/scc-expand-icon.png) **sortant).** 

3. Dans les détails de la stratégie développée qui s’affichent, notez la valeur dans la colonne **Activé**.

   Déplacez le bouton bascule vers la gauche pour désactiver la stratégie : ![Désactiver](../../media/scc-toggle-off.png)

   Déplacez le bouton bascule vers la droite pour activer la stratégie : ![Activer](../../media/scc-toggle-on.png)

Vous ne pouvez pas désactiver la stratégie de courrier indésirable sortant par défaut.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Définir la priorité des stratégies de courrier indésirable sortant personnalisées

Par défaut, les stratégies de courrier indésirable sortant se voient donner une priorité basée sur l’ordre de leur création (les stratégies plus nouvelles sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Les stratégies de courrier indésirable sortant personnalisées sont affichées dans  l’ordre de traitement (la première stratégie a la valeur Priorité 0). La stratégie de courrier indésirable sortant par défaut nommée **Stratégie** de filtrage du courrier indésirable sortant a la valeur de priorité **La** plus faible et vous ne pouvez pas la modifier.

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, recherchez les stratégies dont la valeur dans la colonne **Type** est Stratégie personnalisée de courrier **indésirable sortant.** Notez les valeurs de la colonne **Priorité** :

   - La stratégie personnalisée de courrier indésirable sortant avec la priorité la plus élevée a la valeur Flèche vers le ![ ](../../media/ITPro-EAC-DownArrowIcon.png) **bas 0**.

   - La stratégie personnalisée de courrier indésirable sortant avec la priorité la plus faible a la valeur n flèche vers le haut (par exemple, icône flèche vers le ![ ](../../media/ITPro-EAC-UpArrowIcon.png)  ![ haut ](../../media/ITPro-EAC-UpArrowIcon.png) **3**).

   - Si vous avez trois stratégies de courrier indésirable sortant personnalisées ou plus, les stratégies entre la priorité la plus élevée et la plus basse ont des valeurs icône flèche vers le haut vers le bas icône flèche vers le bas ![ ](../../media/ITPro-EAC-UpArrowIcon.png)![ ](../../media/ITPro-EAC-DownArrowIcon.png) **n** (par exemple, icône flèche vers le haut vers le bas icône ![ ](../../media/ITPro-EAC-UpArrowIcon.png)![ ](../../media/ITPro-EAC-DownArrowIcon.png) **2**).

3. Clic  ![Icône de flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png) ou ![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) pour déplacer la stratégie de courrier indésirable sortant personnalisée vers le haut ou vers le bas dans la liste de priorités.

## <a name="use-the-security--compliance-center-to-remove-outbound-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour supprimer des stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier** indésirable, cliquez sur Développer l’icône pour développer la stratégie personnalisée à supprimer (la colonne Type est stratégie personnalisée de courrier ![ ](../../media/scc-expand-icon.png) indésirable **sortant).** 

3. Dans les détails de la stratégie développée qui s’affichent, cliquez sur **Supprimer la stratégie**.

4. Cliquez sur **Oui** lorsque la boîte de dialogue d’avertissement s’affiche.

Vous ne pouvez pas supprimer la stratégie par défaut.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de courrier indésirable sortant

Comme décrit précédemment, une stratégie de courrier indésirable sortant se compose d’une stratégie de filtrage du courrier indésirable sortant et d’une règle de filtrage du courrier indésirable sortant.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, la différence entre les stratégies de filtrage du courrier indésirable sortant et les règles de filtrage du courrier indésirable sortant est évidente. Vous gérez les stratégies de filtrage du courrier indésirable sortant à l’aide des cmdlets **\* -HostedOutboundSpamFilterPolicy** et vous gérez les règles de filtrage du courrier indésirable sortant à l’aide des cmdlets **\* -HostedOutboundSpamFilterRule.**

- Dans PowerShell, vous créez d’abord la stratégie de filtrage du courrier indésirable sortant, puis vous créez la règle de filtrage du courrier indésirable sortant qui identifie la stratégie à qui s’applique la règle.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie de filtrage du courrier indésirable sortant et de la règle de filtrage du courrier indésirable sortant.
- Lorsque vous supprimez une stratégie de filtrage du courrier indésirable sortant de PowerShell, la règle de filtrage du courrier indésirable sortant correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Utiliser PowerShell pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de filtrage du courrier indésirable sortant.
2. Créez la règle de filtrage du courrier indésirable sortant qui spécifie la stratégie de filtrage du courrier indésirable sortant à l’application de la règle.

 **Remarques** :

- Vous pouvez créer une règle de filtrage du courrier indésirable sortant et lui attribuer une stratégie de filtrage du courrier indésirable sortant existante, non dissociée. Une règle de filtrage du courrier indésirable sortant ne peut pas être associée à plusieurs stratégies de filtrage du courrier indésirable sortant.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de filtrage du courrier indésirable sortant dans PowerShell qui ne sont pas disponibles dans le Centre de sécurité & conformité tant que vous n’avez pas créé la stratégie :

  - Créez la stratégie comme _désactivée_ ( activée sur la `$false` cmdlet **New-HostedOutboundSpamFilterRule).**
  - Définissez la priorité de la stratégie lors de la création _(priorité)_ sur la _\<Number\>_ cmdlet **New-HostedOutboundSpamFilterRule).**

- Une nouvelle stratégie de filtrage du courrier indésirable sortant que vous créez dans PowerShell n’est pas visible dans le Centre de sécurité & conformité tant que vous n’avez pas attribué la stratégie à une règle de filtrage du courrier indésirable.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable sortant

Pour créer une stratégie de filtrage du courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres suivants :

- Les limites de taux de destinataires sont limitées aux valeurs plus petites que les valeurs par défaut. Pour plus d’informations, voir [Limites d’envoi dans les options Microsoft 365.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options)

- Une fois l’une des limites atteinte, l’utilisateur ne peut plus envoyer de messages.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle de filtrage du courrier indésirable sortant

Pour créer une règle de filtrage du courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres ci-après :

- La stratégie de filtrage du courrier indésirable sortant nommée Cadres Contoso est associée à la règle.
- La règle s’applique aux membres du groupe nommé Groupe Responsables Contoso.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Utiliser PowerShell pour afficher les stratégies de filtrage du courrier indésirable sortant

Pour renvoyer une liste récapitulatif de toutes les stratégies de filtrage du courrier indésirable sortant, exécutez la commande ci-dessous :

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Pour renvoyer des informations détaillées sur une stratégie de filtrage du courrier indésirable sortant spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie de filtrage du courrier indésirable sortant nommée Executives.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Utiliser PowerShell pour afficher les règles de filtrage du courrier indésirable sortant

Pour afficher les règles de filtrage du courrier indésirable sortant existantes, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Pour renvoyer une liste récapitulatif de toutes les règles de filtrage du courrier indésirable sortant, exécutez la commande ci-dessous :

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Pour renvoyer des informations détaillées sur une règle de filtrage du courrier indésirable sortant spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété pour la règle de filtrage du courrier indésirable sortant nommée Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Utiliser PowerShell pour modifier les stratégies de filtrage du courrier indésirable sortant

Les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie de filtrage des programmes malveillants dans PowerShell que lorsque vous créez la stratégie comme décrit à l’étape 1 : Utiliser [PowerShell](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) pour créer une section de stratégie de filtrage du courrier indésirable sortant plus tôt dans cet article.

> [!NOTE]
> Vous ne pouvez pas renommer une stratégie de filtrage du courrier indésirable sortant (la cmdlet **Set-HostedOutboundSpamFilterPolicy** n’a pas de _paramètre Name)._ Lorsque vous renommez une stratégie de courrier indésirable sortant dans le Centre de sécurité & conformité, vous renommez uniquement la règle de filtrage du courrier _indésirable sortant._

Pour modifier une stratégie de filtrage du courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Utiliser PowerShell pour modifier les règles de filtrage du courrier indésirable sortant

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de filtrage du courrier indésirable sortant dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de filtrage du courrier indésirable sortant existantes, consultez la section suivante.

Sinon, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle de filtrage du courrier indésirable sortant dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à l’étape 2 : Utiliser [PowerShell](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) pour créer une section de règle de filtrage du courrier indésirable sortant plus tôt dans cet article.

Pour modifier une règle de filtrage du courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de filtrage du courrier indésirable sortant

L’activation ou la désactivation d’une règle de filtrage du courrier indésirable sortant dans PowerShell active ou désactive l’ensemble de la stratégie de courrier indésirable sortant (la règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant affectée). Vous ne pouvez pas activer ou désactiver la stratégie de courrier indésirable sortant par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) et [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Utiliser PowerShell pour définir la priorité des règles de filtrage du courrier indésirable sortant

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

> [!NOTE]
>
> - Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez le paramètre _Priority_ sur la cmdlet **New-HostedOutboundSpamFilterRule** à la place.
>
> - La stratégie de filtrage du courrier indésirable par défaut sortante n’a pas de règle de filtrage de courrier indésirable correspondante et elle a toujours la valeur de priorité nonmodifiable La plus **faible**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Utiliser PowerShell pour supprimer des stratégies de filtrage du courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une stratégie de filtrage du courrier indésirable sortant, la règle de filtrage du courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une stratégie de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Utiliser PowerShell pour supprimer des règles de filtrage du courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une règle de filtrage du courrier indésirable sortant, la stratégie de filtrage du courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Pour plus d’informations

[Supprimer les utilisateurs bloqués du portail des utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md)

[Pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md)

[Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.md)

[Rapport des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)