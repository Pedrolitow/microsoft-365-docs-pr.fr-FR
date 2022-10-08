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
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à afficher, créer, modifier et supprimer des stratégies de courrier indésirable sortant dans Exchange Online Protection (EOP).
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a39fd3fa850ffa82c5ff0d44b61d1828bf1dbf4a
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082634"
---
# <a name="configure-outbound-spam-filtering-in-eop"></a>Configurer le filtrage du courrier indésirable sortant dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans des organisations Exchange Online ou autonomes Exchange Online Protection (EOP) sans boîtes aux lettres Exchange Online, les e-mails sortants envoyés via EOP sont automatiquement vérifiés pour le courrier indésirable et l’activité d’envoi inhabituelle.

Le courrier indésirable sortant d’un utilisateur de votre organisation indique généralement un compte compromis. Les messages sortants suspects sont marqués comme courrier indésirable (quel que soit le niveau de confiance du courrier indésirable ou la liste SCL) et sont acheminés via le pool de remises à haut risque pour aider à protéger la réputation du service ( [c’est-à-dire](high-risk-delivery-pool-for-outbound-messages.md) , empêcher les serveurs de messagerie source Microsoft 365 de se trouver hors des listes de blocs IP). Les administrateurs sont automatiquement avertis de l’activité de messagerie sortante suspecte et des utilisateurs bloqués via des [stratégies d’alerte](../../compliance/alert-policies.md).

EOP utilise des stratégies de courrier indésirable sortant dans le cadre de la défense globale de votre organisation contre le courrier indésirable. Pour plus d’informations, voir [Protection contre le courrier indésirable](anti-spam-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie de courrier indésirable sortant par défaut. Pour une plus grande granularité, vous pouvez également créer des stratégies de courrier indésirable sortantes personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies de courrier indésirable sortant dans le portail Microsoft 365 Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online; EOP PowerShell autonome pour les organisations sans Exchange Online boîtes aux lettres).

Les éléments de base d’une stratégie de courrier indésirable sortant dans EOP sont les suivants :

- **Stratégie de filtrage du courrier indésirable sortant** : spécifie les actions pour les verdicts de filtrage du courrier indésirable sortant et les options de notification.
- **Règle de filtrage du courrier indésirable sortant** : spécifie la priorité et les filtres d’expéditeur (auxquels la stratégie s’applique) pour une stratégie de filtrage du courrier indésirable sortant.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez les stratégies de courrier indésirable sortant dans le portail Microsoft 365 Defender :

- Lorsque vous créez une stratégie, vous créez en fait une règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée en même temps en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres liés au nom, à la priorité, activé ou désactivé, et les filtres d’expéditeur modifient la règle de filtre de courrier indésirable sortant. Tous les autres paramètres modifient la stratégie de filtrage du courrier indésirable sortant associée.
- Lorsque vous supprimez une stratégie, la règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’informations, consultez la section [Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer les stratégies de courrier indésirable sortant](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies) plus loin dans cet article.

Chaque organisation dispose d’une stratégie de courrier indésirable sortant intégrée nommée Default qui a les propriétés suivantes :

- La stratégie est appliquée à tous les expéditeurs de l’organisation, même s’il n’existe aucune règle de filtre de courrier indésirable sortant (filtres d’expéditeur) associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée que la stratégie nommée Par défaut.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour augmenter l’efficacité du filtrage du courrier indésirable sortant, vous pouvez créer des stratégies de courrier indésirable sortant personnalisées avec des paramètres plus stricts qui sont appliqués à des utilisateurs ou groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter, modifier et supprimer des stratégies de courrier indésirable sortant, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux stratégies de courrier indésirable sortant, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions _and_ permissions for other features in Microsoft 365. For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Pour connaître les paramètres recommandés pour les stratégies de courrier indésirable sortant, consultez [les paramètres de stratégie de filtrage du courrier indésirable sortant EOP](recommended-settings-for-eop-and-office365.md#eop-outbound-spam-policy-settings).

- Les [stratégies d’alerte par défaut nommées](../../compliance/alert-policies.md) **Email limite d’envoi dépassée**, **les modèles d’envoi de courriers suspects détectés** et **l’utilisateur restreint à l’envoi de messages électroniques** envoient déjà des notifications par e-mail aux membres du groupe **TenantAdmins** (**administrateurs généraux**) concernant l’activité de courrier sortant inhabituelle et les utilisateurs bloqués en raison d’un courrier indésirable sortant. Pour plus d’informations, consultez [Vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Nous vous recommandons d’utiliser ces stratégies d’alerte plutôt que les options de notification dans les stratégies de courrier indésirable sortant.

## <a name="use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies"></a>Utiliser le portail Microsoft 365 Defender pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant personnalisée dans le portail Microsoft 365 Defender crée la règle de filtrage du courrier indésirable et la stratégie de filtrage de courrier indésirable associée en même temps en utilisant le même nom pour les deux.

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , cliquez sur ![l’icône Créer.](../../media/m365-cc-sc-create-icon.png) **Créez une stratégie** , puis sélectionnez **Sortant dans** la liste déroulante.

3. L’assistant d'application de stratégies s’ouvre. Sur la page **Nommer votre stratégie**, configurez les paramètres suivants :
   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs, groupes et domaines** qui s’affiche, identifiez les expéditeurs internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
   - **Groupes** :
     - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
     - Groupes Microsoft 365 spécifiée
   - **Domaines** : tous les expéditeurs dans les [domaines acceptés spécifiés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.), but the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<sender1\>_ ou _\<sender2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<sender1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : pour ajouter des exceptions pour les expéditeurs internes auxquels la stratégie s’applique (exceptions de destinataire), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   > [!IMPORTANT]
   > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. La stratégie est appliquée _uniquement_ aux destinataires qui correspondent à _tous les_ filtres de destinataires spécifiés. Par exemple, vous configurez une condition de filtre de destinataire dans la stratégie avec les valeurs suivantes :
   >
   > - Utilisateurs : romain@contoso.com
   > - Groupes : Cadres supérieurs
   >
   > La stratégie s'applique à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie ne lui est pas appliquée.
   >
   > De même, si vous utilisez le même filtre de destinataires comme exception à la stratégie, la stratégie n'est pas appliquée à romain@contoso.com _uniquement_ s'il est également membre du groupe Cadres. S’il n’est pas membre du groupe, la stratégie s’applique toujours à lui.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Paramètres de protection** qui s’ouvre, configurez les paramètres suivants :
   - **Limites des** messages : les paramètres de cette section configurent les limites des messages électroniques sortants provenant de boîtes aux lettres **Exchange Online** :
     - **Définir une limite de messages externes** : nombre maximal de destinataires externes par heure.
     - **Définir une limite de messages internes** : nombre maximal de destinataires internes par heure.
     - **Définir une limite de messages quotidiens** : nombre total maximal de destinataires par jour.

     Une valeur valide est comprise entre 0 et 1 0000. La valeur par défaut est 0, ce qui signifie que les valeurs par défaut du service sont utilisées. Pour plus d’informations, consultez [Limites d’envoi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

    Entrez une valeur dans la zone ou utilisez les flèches d’augmentation/diminution sur la zone.

   - **Restriction imposée aux utilisateurs qui atteignent la limite de messages** : sélectionnez une action dans la liste déroulante lorsque l’une des limites de la section **Paramètres de protection** est dépassée.

     Pour toutes les actions, les expéditeurs spécifiés dans **l’utilisateur ne peuvent pas envoyer de** stratégie d’alerte par e-mail (et dans le désormais redondant **Notifier ces utilisateurs et groupes si un expéditeur est bloqué en raison de l’envoi d’un paramètre de courrier indésirable sortant** plus loin sur cette page) reçoivent des notifications par e-mail.

     - **Empêchez l’utilisateur d’envoyer des messages électroniques jusqu’au jour suivant** : il s’agit de la valeur par défaut. Email notifications sont envoyées et l’utilisateur ne pourra plus envoyer de messages avant le lendemain, en fonction de l’heure UTC. Il n’existe aucun moyen pour l’administrateur de remplacer ce bloc.
       - La stratégie d’alerte nommée **User restricted from sending email** notifie les administrateurs (par e-mail et sur la page **Incidents & alerts** \> **View alerts** ).
       - Tous les destinataires spécifiés dans la stratégie **Avertir des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi d’un paramètre de courrier indésirable sortant** dans la stratégie sont également avertis.
       - L’utilisateur ne pourra pas envoyer d’autres messages jusqu’au lendemain, en fonction de l’heure UTC. Il n’existe aucun moyen pour l’administrateur de remplacer ce bloc.
     - **Empêcher l’utilisateur d’envoyer des messages électroniques** : Email notifications sont envoyées, l’utilisateur est ajouté aux **utilisateurs restreints** <https://security.microsoft.com/restrictedusers> dans le portail Microsoft 365 Defender et l’utilisateur ne peut pas envoyer d’e-mail tant qu’il n’a pas été supprimé des **utilisateurs restreints** par un administrateur. Une fois qu’un administrateur a supprimé l’utilisateur de la liste, il ne sera plus limité pour ce jour-là. Pour obtenir des instructions, consultez [Suppression d’un utilisateur du portail Utilisateurs restreints après l’envoi d’un courrier indésirable](removing-user-from-restricted-users-portal-after-spam.md).
     - **Aucune action, alerte uniquement** : Email notifications sont envoyées.

   - **Règles de transfert** : utilisez les paramètres de cette section pour contrôler le transfert automatique d’e-mails par **Exchange Online boîtes aux lettres** aux expéditeurs externes. Pour plus d’informations, consultez [Control automatic external email forwarding in Microsoft 365](external-email-forwarding.md).

     > [!NOTE]
     > Lorsque le transfert automatique est désactivé, le destinataire reçoit un rapport de non-remise (également appelé NDR ou message de rebond) si les expéditeurs externes envoient un e-mail à une boîte aux lettres sur laquelle le transfert est en place. Si le message est envoyé par un expéditeur interne **et** que la méthode de transfert est le [transfert de boîte aux lettres](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (également appelé _transfert SMTP_), l’expéditeur interne obtient la valeur NDR. L’expéditeur interne n’obtient pas de NDR si le transfert s’est produit en raison d’une règle de boîte de réception.

     Sélectionnez l’une des actions suivantes dans la liste déroulante **des règles de transfert automatique** :

     - **Automatique - Contrôlé par le système** : autorise le filtrage du courrier indésirable sortant pour contrôler le transfert automatique de courriers externes. Il s’agit de la valeur par défaut.
     - **Activé** : le transfert automatique de courrier externe n’est pas désactivé par la stratégie.
     - **Désactivé** : tous les transferts automatiques de courriers externes sont désactivés par la stratégie.

   - **Notifications** : utilisez les paramètres de la section pour configurer des destinataires supplémentaires qui doivent recevoir des copies et des notifications de messages électroniques sortants suspects :

     - **Envoyer une copie de trafic sortant suspect qui dépasse ces limites à ces utilisateurs et groupes** : ce paramètre ajoute les destinataires spécifiés au champ CCI des messages sortants suspects.

       > [!NOTE]
       > Ce paramètre fonctionne uniquement dans la stratégie de courrier indésirable sortant par défaut. Cela ne fonctionne pas dans les stratégies de courrier indésirable sortant personnalisées que vous créez.

       Pour activer ce paramètre, cochez la case. Dans la zone qui s’affiche, cliquez dans la zone, entrez une adresse e-mail valide, puis appuyez sur Entrée ou sélectionnez la valeur complète affichée sous la zone.

       Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   - **Notifier ces utilisateurs et groupes si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant**

     > [!IMPORTANT]
     >
     > - Ce paramètre est en cours de dépréciation des stratégies de courrier indésirable sortant.
     >
     > - La [stratégie d’alerte](../../compliance/alert-policies.md) par défaut nommée **Utilisateur limité à l’envoi de messages électroniques** envoie déjà des notifications par e-mail aux membres du groupe **TenantAdmins** (**administrateurs généraux**) lorsque les utilisateurs sont bloqués en raison du dépassement des limites dans la section **Limites des destinataires** . **Nous vous recommandons vivement d’utiliser la stratégie d’alerte plutôt que ce paramètre dans la stratégie de courrier indésirable sortant pour informer les administrateurs et d’autres utilisateurs**. Pour obtenir des instructions, consultez [Vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Créer**.

7. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-outbound-spam-policies"></a>Utiliser le portail Microsoft 365 Defender pour afficher les stratégies de courrier indésirable sortant

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable**, recherchez l’une des valeurs suivantes :
   - La valeur **type** est **la stratégie de courrier indésirable sortant personnalisé**
   - La valeur **name** est **la stratégie de trafic sortant anti-courrier indésirable (par défaut)**

   Les propriétés suivantes sont affichées dans la liste des stratégies anti-courrier indésirable :

   - **Name**
   - **État**
   - **Priorité**
   - **Type (Type)**

3. Lorsque vous sélectionnez une stratégie de courrier indésirable sortant en cliquant sur le nom, les paramètres de stratégie s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-outbound-spam-policies"></a>Utiliser le portail Microsoft 365 Defender pour modifier les stratégies de courrier indésirable sortant

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez une stratégie de courrier indésirable sortant dans la liste en cliquant sur le nom :
   - Stratégie personnalisée que vous avez créée où la valeur de la colonne **Type** est **une stratégie de courrier indésirable sortant personnalisé**.
   - Stratégie par défaut nommée **stratégie sortante anti-courrier indésirable (par défaut).**

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez la section [précédente Utiliser le portail Microsoft 365 Defender pour créer des stratégies de courrier indésirable sortant](#use-the-microsoft-365-defender-portal-to-create-outbound-spam-policies) dans cet article.

   Pour la stratégie de courrier indésirable sortant par défaut, la section **Appliqué à** n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie, définissez l’ordre de priorité de la stratégie ou configurez les notifications de l’utilisateur final, consultez les sections suivantes.

### <a name="enable-or-disable-custom-outbound-spam-policies"></a>Activer ou désactiver des stratégies de courrier indésirable sortantes personnalisées

Vous ne pouvez pas désactiver la stratégie de courrier indésirable sortant par défaut.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez une stratégie avec la **valeur Type** de stratégie de **courrier indésirable sortant personnalisé** dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Policy off**: To turn on the policy, click ![Turn on icon.](../../media/m365-cc-sc-turn-on-off-icon.png) **Turn on** .
   - **Policy on**: To turn off the policy, click ![Turn off icon.](../../media/m365-cc-sc-turn-on-off-icon.png) **Turn off**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Définir la priorité des stratégies de courrier indésirable sortantes personnalisées

Par défaut, les stratégies de courrier indésirable sortant reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

To change the priority of a policy, you click **Increase priority** or **Decrease priority** in the properties of the policy (you can't directly modify the **Priority** number in the Microsoft 365 Defender portal). Changing the priority of a policy only makes sense if you have multiple policies.

 **Remarques** :

- Dans le portail Microsoft 365 Defender, vous ne pouvez modifier la priorité de la stratégie de courrier indésirable sortant qu’une fois que vous l’avez créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle de filtrage de courrier indésirable (ceci peut modifier la priorité de règles existantes).
- Les stratégies de courrier indésirable sortant sont traitées dans l’ordre dans lequel elles sont affichées (la première stratégie a la valeur **Priorité** 0). La stratégie de courrier indésirable sortant par défaut a la valeur de priorité **la plus basse**, et vous ne pouvez pas la modifier.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez une stratégie avec la **valeur Type** de stratégie de **courrier indésirable sortant personnalisé** dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie de courrier indésirable sortant avec la valeur **de priorité** **0** a uniquement l’option **Réduire la priorité** disponible.
   - La stratégie de courrier indésirable sortant avec la valeur **de priorité** la plus basse (par exemple, **3**) dispose uniquement de l’option **Augmenter la priorité** disponible.
   - Si vous avez au moins trois stratégies de courrier indésirable sortant, les stratégies entre les valeurs de priorité les plus élevées et les plus basses ont les options **Augmenter la priorité** et Réduire la **priorité** disponibles.

   Cliquez sur l’icône ![Augmenter la priorité.](../../media/m365-cc-sc-increase-icon.png) **Icône Augmenter la priorité** ou ![Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **de priorité** .

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-outbound-spam-policies"></a>Utiliser le portail Microsoft 365 Defender pour supprimer les stratégies de courrier indésirable sortant personnalisées

Lorsque vous utilisez le portail Microsoft 365 Defender pour supprimer une stratégie de courrier indésirable sortant personnalisée, la règle de filtrage du courrier indésirable et la stratégie de filtre de courrier indésirable correspondante sont toutes deux supprimées. Vous ne pouvez pas supprimer la stratégie de courrier indésirable sortant par défaut.

1. Dans le Portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , sélectionnez une stratégie avec la **valeur Type** de stratégie de **courrier indésirable sortant personnalisé** dans la liste en cliquant sur le nom. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

3. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-outbound-spam-policies"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de courrier indésirable sortant

Comme décrit précédemment, une stratégie de courrier indésirable sortant se compose d’une stratégie de filtrage du courrier indésirable sortant et d’une règle de filtre de courrier indésirable sortant.

Dans Exchange Online PowerShell ou PowerShell EOP autonome, la différence entre les stratégies de filtrage du courrier indésirable sortant et les règles de filtrage du courrier indésirable sortant est évidente. Vous gérez les stratégies de filtrage du courrier indésirable sortant à l’aide **\*des applets de commande -HostedOutboundSpamFilterPolicy** , et vous gérez les règles de filtrage du courrier indésirable sortant à l’aide **\*des applets de commande -HostedOutboundSpamFilterRule** .

- Dans PowerShell, vous créez d’abord la stratégie de filtrage du courrier indésirable sortant, puis vous créez la règle de filtrage du courrier indésirable sortant qui identifie la stratégie à laquelle la règle s’applique.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie de filtrage du courrier indésirable sortant et de la règle de filtrage du courrier indésirable sortant.
- Lorsque vous supprimez une stratégie de filtre de courrier indésirable sortant de PowerShell, la règle de filtre de courrier indésirable sortant correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Utiliser PowerShell pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de filtrage du courrier indésirable sortant.
2. Créez la règle de filtrage du courrier indésirable sortant qui spécifie la stratégie de filtrage du courrier indésirable sortant à laquelle la règle s’applique.

   **Remarques** :

   - Vous pouvez créer une règle de filtrage du courrier indésirable sortant et lui attribuer une stratégie de filtre de courrier indésirable sortant non associée existante. Une règle de filtre de courrier indésirable sortant ne peut pas être associée à plusieurs stratégies de filtrage du courrier indésirable sortant.
   - Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de filtre de courrier indésirable sortant dans PowerShell qui ne sont pas disponibles dans le portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
     - Créez la nouvelle stratégie comme désactivée (_activée_ `$false` sur l’applet de commande **New-HostedOutboundSpamFilterRule** ).
     - Définissez la priorité de la stratégie lors de la création (_Priorité__\<Number\>_) sur l’applet de commande **New-HostedOutboundSpamFilterRule**).
   - Une nouvelle stratégie de filtrage du courrier indésirable sortant que vous créez dans PowerShell n’est pas visible dans le portail Microsoft 365 Defender tant que vous n’avez pas affecté la stratégie à une règle de filtre de courrier indésirable sortant.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable sortant

Pour créer une stratégie de filtre de courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres suivants :

- Les limites de débit des destinataires sont limitées aux valeurs plus petites que les valeurs par défaut. Pour plus d’informations, consultez [Les limites d’envoi dans les options Microsoft 365](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Une fois que l’une des limites est atteinte, l’utilisateur n’est pas autorisé à envoyer des messages.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle de filtre de courrier indésirable sortant

Pour créer une règle de filtre de courrier indésirable sortant, utilisez cette syntaxe :

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Sender filters> [<Sender filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres suivants :

- La stratégie de filtrage du courrier indésirable sortant nommée Contoso Executives est associée à la règle.
- La règle s’applique aux membres du groupe nommé Groupe Responsables Contoso.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -FromMemberOf "Contoso Executives Group"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-HostedOutboundSpamFilterRule](/powershell/module/exchange/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Utiliser PowerShell pour afficher les stratégies de filtrage du courrier indésirable sortant

Pour renvoyer une liste récapitulative de toutes les stratégies de filtrage du courrier indésirable sortant, exécutez cette commande :

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Pour retourner des informations détaillées sur une stratégie de filtrage du courrier indésirable sortant spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Cet exemple retourne toutes les valeurs de propriété pour la stratégie de filtrage du courrier indésirable sortant nommée Executives.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Utiliser PowerShell pour afficher les règles de filtrage du courrier indésirable sortant

Pour afficher les règles de filtre de courrier indésirable sortant existantes, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>]
```

Pour renvoyer une liste récapitulative de toutes les règles de filtre de courrier indésirable sortant, exécutez la commande suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-HostedOutboundSpamFilterRule -State Disabled
```

```PowerShell
Get-HostedOutboundSpamFilterRule -State Enabled
```

Pour retourner des informations détaillées sur une règle de filtre de courrier indésirable sortante spécifique, utilisez cette syntaxe :

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Cet exemple retourne toutes les valeurs de propriété pour la règle de filtre de courrier indésirable sortante nommée Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-HostedOutboundSpamFilterRule](/powershell/module/exchange/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Utiliser PowerShell pour modifier les stratégies de filtrage du courrier indésirable sortant

Les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie de filtre de programmes malveillants dans PowerShell que lorsque vous créez la stratégie comme décrit à [l’étape 1 : Utiliser PowerShell pour créer une section de stratégie de filtrage du courrier indésirable sortant](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) plus haut dans cet article.

> [!NOTE]
> Vous ne pouvez pas renommer une stratégie de filtre de courrier indésirable sortant (l’applet de commande **Set-HostedOutboundSpamFilterPolicy** n’a aucun paramètre _Name_ ). Lorsque vous renommez une stratégie de courrier indésirable sortant dans le portail Microsoft 365 Defender, vous renommez uniquement la _règle_ de filtre de courrier indésirable sortant.

Pour modifier une stratégie de filtre de courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Utiliser PowerShell pour modifier les règles de filtre de courrier indésirable sortant

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de filtre de courrier indésirable sortant dans PowerShell est le paramètre _Activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de filtre de courrier indésirable sortant existantes, consultez la section suivante.

Sinon, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle de filtre de courrier indésirable sortant dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à [l’étape 2 : Utiliser PowerShell pour créer une section de règle de filtre de courrier indésirable sortant](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) plus haut dans cet article.

Pour modifier une règle de filtre de courrier indésirable sortant, utilisez cette syntaxe :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-HostedOutboundSpamFilterRule](/powershell/module/exchange/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de filtre de courrier indésirable sortant

L’activation ou la désactivation d’une règle de filtre de courrier indésirable sortant dans PowerShell active ou désactive l’ensemble de la stratégie de courrier indésirable sortant (règle de filtrage du courrier indésirable sortant et stratégie de filtrage du courrier indésirable sortant attribuée). Vous ne pouvez pas activer ou désactiver la stratégie de courrier indésirable sortant par défaut (elle est toujours appliquée à tous les expéditeurs).

Pour activer ou désactiver une règle de filtre de courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-HostedOutboundSpamFilterRule | Disable-HostedOutboundSpamFilterRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de filtre de courrier indésirable sortante nommée Service marketing.

```PowerShell
Disable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Enable-HostedOutboundSpamFilterRule](/powershell/module/exchange/enable-hostedoutboundspamfilterrule) et [Disable-HostedOutboundSpamFilterRule](/powershell/module/exchange/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Utiliser PowerShell pour définir la priorité des règles de filtrage du courrier indésirable sortant

The highest priority value you can set on a rule is 0. The lowest value you can set depends on the number of rules. For example, if you have five rules, you can use the priority values 0 through 4. Changing the priority of an existing rule can have a cascading effect on other rules. For example, if you have five custom rules (priorities 0 through 4), and you change the priority of a rule to 2, the existing rule with priority 2 is changed to priority 3, and the rule with priority 3 is changed to priority 4.

Pour définir la priorité d’une règle de filtre de courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

This example sets the priority of the rule named Marketing Department to 2. All existing rules that have a priority less than or equal to 2 are decreased by 1 (their priority numbers are increased by 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Remarques** :

- Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ sur l’applet de commande **New-HostedOutboundSpamFilterRule** .
- La stratégie de filtrage de courrier indésirable par défaut sortante n’a pas de règle de filtre de courrier indésirable correspondante, et elle a toujours la valeur de priorité non modifiable **la plus basse**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Utiliser PowerShell pour supprimer les stratégies de filtrage du courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une stratégie de filtrage du courrier indésirable sortant, la règle de filtre de courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une stratégie de filtre de courrier indésirable sortant dans PowerShell, utilisez cette syntaxe :

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

Cet exemple montre comment supprimer la stratégie de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-HostedOutboundSpamFilterPolicy](/powershell/module/exchange/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Utiliser PowerShell pour supprimer les règles de filtre de courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une règle de filtre de courrier indésirable sortant, la stratégie de filtrage du courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une règle de filtre de courrier indésirable sortant dans PowerShell, utilisez cette syntaxe :

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de filtre de courrier indésirable sortante nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-HostedOutboundSpamFilterRule](/powershell/module/exchange/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Pour plus d'informations

[Supprimer les utilisateurs bloqués du portail Utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md)

[Pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md)

[Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.yml)

[Rapport des messages transférés automatiquement](mfi-auto-forwarded-messages-report.md)
