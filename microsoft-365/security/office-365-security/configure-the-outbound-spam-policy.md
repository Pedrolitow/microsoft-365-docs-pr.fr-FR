---
title: Configurer le filtrage du courrier indésirable sortant
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a44764e9-a5d2-4c67-8888-e7fb871c17c7
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Dans cet article, vous découvrirez comment configurer des stratégies de courrier indésirable sortant qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation.
ms.openlocfilehash: 644ffb51c92f4d71d3ae2cde1eba408289573f48
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036787"
---
# <a name="configure-outbound-spam-filtering"></a>Configurer le filtrage du courrier indésirable sortant

Si vous êtes un client Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, les messages électroniques sortants envoyés via EOP sont automatiquement vérifiés pour le courrier indésirable et l’activité d’envoi inhabituelle.

Le courrier indésirable sortant d’un utilisateur de votre organisation indique généralement un compte compromis. Les messages sortants suspects sont marqués comme courrier indésirable (quel que soit le seuil de probabilité de courrier indésirable ou SCL) et sont acheminés via le [pool de remise à haut risque](high-risk-delivery-pool-for-outbound-messages.md) afin de protéger la réputation du service (c’est-à-dire maintenir les serveurs de messagerie source Microsoft 365 hors des listes d’adresses IP bloquées). Les administrateurs sont automatiquement informés de l’activité e-mail sortante suspecte et des utilisateurs bloqués via des [stratégies d’alerte](../../compliance/alert-policies.md).

EOP utilise des stratégies de courrier indésirable sortant dans le cadre de la protection globale de votre organisation contre le courrier indésirable. Pour plus d’informations, voir [Protection contre le courrier indésirable](anti-spam-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie de courrier indésirable sortant par défaut. Pour une granularité accrue, vous pouvez également créer des stratégies de courrier indésirable sortant personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies de courrier indésirable sortant dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les clients Microsoft 365 ; Exchange Online Protection PowerShell pour les clients EOP autonomes).

## <a name="outbound-spam-policies-in-the-security--compliance-center-vs-exchange-online-powershell-or-exchange-online-protection-powershell"></a>Stratégies de courrier indésirable sortant dans le centre de sécurité & Compliance Center vs Exchange Online PowerShell ou Exchange Online Protection PowerShell

Les éléments de base d’une stratégie de courrier indésirable sortant dans EOP sont les suivants :

- **Stratégie de filtrage du courrier indésirable sortant**: spécifie les actions pour le filtrage du courrier indésirable sortant et les options de notification.

- **Règle de filtrage du courrier indésirable sortant**: spécifie la priorité et les filtres de destinataire (auxquels s’applique la stratégie) pour une stratégie de filtrage du courrier indésirable sortant.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies de courrier indésirable sortant dans le centre de sécurité & Compliance Center :

- Lorsque vous créez une stratégie de courrier indésirable sortant dans le centre de sécurité & conformité, vous créez en réalité une règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée en utilisant le même nom pour les deux.

- Lorsque vous modifiez une stratégie de courrier indésirable sortant dans le centre de sécurité & conformité, les paramètres relatifs aux filtres nom, priorité, activé ou désactivé et filtre de destinataires modifient la règle de filtrage du courrier indésirable sortant. Tous les autres paramètres modifient la stratégie de filtrage du courrier indésirable sortant associée.

- Lorsque vous supprimez une stratégie de courrier indésirable sortant du centre de sécurité & conformité, la règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant associée sont supprimées.

Dans Exchange Online PowerShell ou une version autonome d’Exchange Online Protection PowerShell, la différence entre les stratégies de filtrage du courrier indésirable sortant et les règles de filtrage du courrier indésirable sortant est apparente. Vous gérez les stratégies de filtrage du ** \*** courrier indésirable sortant à l’aide des cmdlets-HostedContentFilterPolicy et vous gérez les règles de ** \*** filtrage du courrier indésirable sortant à l’aide des cmdlets-hostedcontentfilterrule permet.

- Dans PowerShell, vous devez d’abord créer la stratégie de filtrage du courrier indésirable sortant, puis créer la règle de filtrage du courrier indésirable sortant qui identifie la stratégie à laquelle s’applique la règle.

- Dans PowerShell, vous pouvez modifier séparément les paramètres de la stratégie de filtrage du courrier indésirable sortant et de la règle de filtrage du courrier indésirable sortant.

- Lorsque vous supprimez une stratégie de filtrage du courrier indésirable sortant de PowerShell, la règle de filtrage du courrier indésirable sortant correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="default-outbound-spam-policy"></a>Stratégie anti-courrier indésirable sortant par défaut

Chaque organisation dispose d’une stratégie de courrier indésirable sortante intégrée nommée par défaut qui possède les propriétés suivantes :

- La stratégie de filtrage du courrier indésirable sortant nommée par défaut est appliquée à tous les destinataires de l’organisation, même si aucune règle de filtrage du courrier indésirable sortant (filtres de destinataires) n’est associée à la stratégie.

- La stratégie nommée Par défaut possède la valeur de priorité personnalisée **Plus faible** que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée que la stratégie nommée Par défaut.

- La stratégie nommée Par défaut est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour accroître l’efficacité du filtrage du courrier indésirable sortant, vous pouvez créer des stratégies de courrier indésirable sortant personnalisées avec des paramètres plus stricts appliqués à des utilisateurs ou à des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection autonome, voir [Se connecter à PowerShell d’Exchange Online Protection](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour ajouter, modifier et supprimer des stratégies de courrier indésirable sortant, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour un accès en lecture seule aux stratégies de courrier indésirable sortant, vous devez être membre du groupe de rôles **lecteur de sécurité** . Pour des informations supplémentaires sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité](permissions-in-the-security-and-compliance-center.md).

- Pour connaître les paramètres recommandés pour les stratégies de courrier indésirable sortant, voir [EOP Outbound Outbound Filter Policy Settings](recommended-settings-for-eop-and-office365-atp.md#eop-outbound-spam-policy-settings).

- Les [stratégies d’alerte](../../compliance/alert-policies.md) par défaut nommées limite d’envoi de **courrier électronique sont dépassées**, des **modèles de courrier électronique suspects détectés**et l’utilisateur ne peut pas envoyer **de courriers** électroniques aux membres du groupe **TenantAdmins** (**administrateurs globaux**) à propos de l’activité de courrier électronique sortant inhabituel et des utilisateurs bloqués en raison du courrier indésirable sortant. Pour plus d’informations, consultez [la rubrique vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Nous vous recommandons d’utiliser ces stratégies d’alerte à la place des options de notification dans les stratégies de courrier indésirable sortant.

## <a name="use-the-security--compliance-center-to-create-outbound-spam-policies"></a>Utiliser le centre de sécurité & conformité pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant personnalisé dans le centre de sécurité & conformité crée la règle de filtrage du courrier indésirable et la stratégie de filtrage du courrier indésirable en même temps en utilisant le même nom pour les deux.

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **paramètres du blocage du courrier indésirable** , cliquez sur **créer une stratégie sortante**.

3. Dans la **stratégie de filtrage du courrier indésirable sortant** qui s’ouvre, configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

4. Module Développez la section **notifications** pour configurer des utilisateurs supplémentaires qui doivent recevoir des copies et des notifications de messages électroniques sortants suspects :

   - **Envoyer une copie des messages électroniques sortants suspects à des personnes spécifiques**: ce paramètre ajoute les utilisateurs spécifiés en tant que destinataires CCI aux messages sortants suspects. Pour activer ce paramètre :

     a. Activez la case à cocher pour activer le paramètre.

     b. Cliquez sur **Ajouter des personnes**. Dans la fenêtre mobile **Ajouter ou supprimer des destinataires** qui s’affiche :

     c. Entrez l’adresse de courrier de l’expéditeur. Vous pouvez spécifier plusieurs adresses de messagerie séparées par des points-virgules (;) ou un destinataire par ligne.

     d. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les destinataires.

        Répétez ces étapes autant de fois que nécessaire.

        Les destinataires que vous avez ajoutés apparaissent dans la section **liste des destinataires** du menu volant. Pour supprimer un destinataire, cliquez ![sur le](../../media/scc-remove-icon.png)bouton supprimer.

     e. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

     Pour désactiver ce paramètre, désactivez la case à cocher.

   - **Informer des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant**:

     > [!NOTE]
     > La [stratégie d’alerte](../../compliance/alert-policies.md) par défaut nommée **User Restricted from sending email** envoie déjà des notifications par courrier électronique aux membres du groupe **TenantAdmins** (**administrateurs globaux**) lorsque les utilisateurs sont bloqués en raison du dépassement des limites de la section **limites des destinataires** . Nous vous recommandons d’utiliser la stratégie d’alerte au lieu de ce paramètre dans la stratégie anti-courrier indésirable sortant pour avertir les administrateurs et les autres utilisateurs. Pour obtenir des instructions, consultez [la rubrique vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).

     Pour activer ce paramètre :

     a. Activez la case à cocher pour activer le paramètre.

     b. Cliquez sur **Ajouter des personnes**. Dans la fenêtre mobile **Ajouter ou supprimer des destinataires** qui s’affiche :

     c. Entrez l’adresse de courrier de l’expéditeur. Vous pouvez spécifier plusieurs adresses de messagerie séparées par des points-virgules (;) ou un destinataire par ligne.

     d. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les destinataires.

        Répétez ces étapes autant de fois que nécessaire.

        Les destinataires que vous avez ajoutés apparaissent dans la section **liste des destinataires** du menu volant. Pour supprimer un destinataire, cliquez ![sur le](../../media/scc-remove-icon.png)bouton supprimer.

     e. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

     Pour désactiver ce paramètre, désactivez la case à cocher.

5. Module Développez la section **limites des destinataires** pour configurer les limites et les actions pour les messages électroniques sortants suspects :

   > [!NOTE]
   > Ces paramètres ne s’appliquent qu’aux boîtes aux lettres en nuage.
     
   - **Nombre maximal de destinataires par utilisateur**

     Une valeur valide est comprise entre 0 et 10000. La valeur par défaut est 0, ce qui signifie que les valeurs par défaut du service sont utilisées. Pour plus d’informations, consultez la rubrique [limites d’envoi dans les options Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

     - **Limite horaire externe**: nombre maximal de destinataires externes par heure.

     - **Limite horaire interne**: nombre maximal de destinataires internes par heure.

     - **Limite journalière**: nombre total maximal de destinataires par jour.

   - **Action lorsqu’un utilisateur dépasse les limites ci-dessus**: configurez l’action à effectuer lorsque l’une des **limites de destinataires** est dépassée. Pour toutes les actions, les destinataires spécifiés dans l’utilisateur ne peuvent pas **Envoyer de stratégie d’alerte par courrier électronique** (et dans le paramètre à présent, **avertir les personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant** dans la stratégie de courrier indésirable sortant reçoit des notifications par courrier électronique.

     - **Empêcher l’utilisateur d’envoyer des messages jusqu’au jour suivant**: il s’agit de la valeur par défaut. Les notifications par courrier électronique sont envoyées et l’utilisateur ne peut plus envoyer de messages avant le jour suivant, en fonction de l’heure UTC. L’administrateur n’a aucun moyen de remplacer ce bloc.

       - L’activité alerte nommée **utilisateur restreint de l’envoi de courrier électronique** avertit les administrateurs (par e-mail et sur la page **afficher les alertes** ).

       - Tous les destinataires spécifiés dans le paramètre **informer des personnes spécifiques si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant** dans la stratégie sont également avertis.

       - L’utilisateur ne peut plus envoyer de messages avant le jour suivant, en fonction de l’heure UTC. L’administrateur n’a aucun moyen de remplacer ce bloc.

     - **Empêcher l’utilisateur d’envoyer des courriers**électroniques : les notifications par courrier électronique sont envoyées, l’utilisateur est ajouté au portail **[utilisateurs restreints]<https://sip.protection.office.com/restrictedusers> ** dans le centre de sécurité & conformité et l’utilisateur ne peut pas envoyer de courrier électronique tant qu’il n’a pas été supprimé du portail **utilisateurs restreints** par un administrateur. Une fois qu’un administrateur a supprimé l’utilisateur de la liste, l’utilisateur n’est plus relimité pour ce jour. Pour obtenir des instructions, consultez [la rubrique Suppression d’un utilisateur du portail utilisateurs restreints après l’envoi du courrier indésirable](removing-user-from-restricted-users-portal-after-spam.md).

     - **Aucune action, alerte uniquement**: les notifications par courrier électronique sont envoyées.

6. Exige Développez la section **appliqué à** pour identifier les expéditeurs internes auxquels la stratégie s’applique.

    Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou de l’utilisation ou de la logique d’exception (par exemple, _ \<sender1\> _ ou _ \<sender2\>_). Différentes conditions ou exceptions utilisent et logique (par exemple, _ \<sender1\> _ et _ \<membre du groupe 1\>_).

    Il est plus facile de cliquer sur**Ajouter une condition** trois fois pour afficher toutes les conditions disponibles. Vous pouvez cliquer sur le ![bouton Supprimer](../../media/scc-remove-icon.png) pour supprimer les conditions que vous ne voulez pas configurer.

    - **Le domaine de l’expéditeur est**: spécifie les expéditeurs dans un ou plusieurs des domaines acceptés configurés dans Office 365. Cliquez dans la zone **Ajouter un indicateur** pour afficher et sélectionner un domaine. Cliquez de nouveau sur la zone **Ajouter un indicateur** pour sélectionner d’autres domaines si plusieurs domaines sont disponibles.

    - L' **expéditeur est**: spécifie un ou plusieurs utilisateurs de votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez de nouveau sur la zone **Ajouter une balise** pour sélectionner des expéditeurs supplémentaires.

    - L' **expéditeur est membre de**: spécifie un ou plusieurs groupes dans votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez de nouveau sur la zone **Ajouter une balise** pour sélectionner des expéditeurs supplémentaires.

    - **Sauf si**: pour ajouter des exceptions à la règle, cliquez sur **Ajouter une condition** trois fois pour afficher toutes les exceptions disponibles. Les paramètres et le comportement sont exactement comme les conditions.

7. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-view-outbound-spam-policies"></a>Utiliser le centre de sécurité & conformité pour afficher les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Sur la page **paramètres de blocage du courrier indésirable** , cliquez sur ![développer une icône](../../media/scc-expand-icon.png) pour développer une stratégie de courrier indésirable sortant :

   - Stratégie par défaut nommée **stratégie de filtrage du courrier indésirable sortant**.

   - Une stratégie personnalisée que vous avez créée où la valeur dans la colonne **type** est **personnalisée stratégie anti-courrier indésirable sortant**.

3. Les paramètres de stratégie sont affichés dans les détails de stratégie développés qui s’affichent, ou vous pouvez cliquer sur **modifier la stratégie**.

## <a name="use-the-security--compliance-center-to-modify-outbound-spam-policies"></a>Utiliser le centre de sécurité & conformité pour modifier les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Sur la page **paramètres de blocage du courrier indésirable** , cliquez sur ![développer une icône](../../media/scc-expand-icon.png) pour développer une stratégie de courrier indésirable sortant :

   - Stratégie par défaut nommée **stratégie de filtrage du courrier indésirable sortant**.

   - Une stratégie personnalisée que vous avez créée où la valeur dans la colonne **type** est **personnalisée stratégie anti-courrier indésirable sortant**.

3. Cliquez sur **Modifier une stratégie**.

Pour les stratégies de courrier indésirable sortant personnalisé, les paramètres disponibles dans le menu volant qui s’affiche sont identiques à ceux décrits dans la section [utiliser le centre de sécurité & conformité pour créer des stratégies de courrier indésirable sortant](#use-the-security--compliance-center-to-create-outbound-spam-policies) .

Pour la stratégie de courrier indésirable sortant par défaut nommée **stratégie de filtrage du courrier indésirable sortant**, la section **appliqué à** n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie, définir l’ordre de priorité de la stratégie ou configurer les notifications de mise en quarantaine de l’utilisateur final, voir les sections suivantes.

### <a name="enable-or-disable-outbound-spam-policies"></a>Activer ou désactiver les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **paramètres de blocage du courrier indésirable** , cliquez sur ![développer une icône](../../media/scc-expand-icon.png) pour développer une stratégie personnalisée que vous avez créée (la valeur dans la colonne **type** est **stratégie courrier indésirable sortant personnalisé**).

3. Dans les détails de la stratégie développée qui s’affichent, notez la valeur dans la colonne**Activé**.

   Déplacez le bouton bascule vers la gauche pour désactiver la stratégie : ![Désactiver](../../media/scc-toggle-off.png)

   Déplacez le bouton bascule vers la droite pour activer la stratégie : ![Activer](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png)

Vous ne pouvez pas désactiver la stratégie de courrier indésirable sortant par défaut.

### <a name="set-the-priority-of-custom-outbound-spam-policies"></a>Définir la priorité des stratégies de courrier indésirable sortant personnalisé

Par défaut, les stratégies de courrier indésirable sortant reçoivent une priorité basée sur l’ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Deux stratégies ne peuvent pas avoir la même priorité.

Les stratégies de courrier indésirable sortant personnalisé sont affichées dans l’ordre dans lequel elles sont traitées (la première stratégie a la valeur de **priorité** 0). La stratégie de courrier indésirable sortant par défaut nommée **stratégie de filtrage du courrier indésirable sortant** a la valeur Priority la **plus faible**et vous ne pouvez pas la modifier.

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **paramètres de blocage du courrier indésirable** , recherchez les stratégies pour lesquelles la valeur dans la colonne **type** est **Custom courrier indésirable sortant**. Notez les valeurs de la colonne**Priorité** :

   - La stratégie de courrier indésirable sortant personnalisé avec la priorité la ![plus élevée a](../../media/ITPro-EAC-DownArrowIcon.png) la valeur flèche vers le bas **0**.

   - La stratégie de courrier indésirable sortant personnalisé avec la priorité la ![plus faible est](../../media/ITPro-EAC-UpArrowIcon.png) dotée de l’icône ![de flèche haut](../../media/ITPro-EAC-UpArrowIcon.png) **n** (par exemple, icône flèche haut **3**).

   - Si vous avez au moins trois stratégies de courrier indésirable sortant personnalisées, les stratégies comprises entre ![la priorité la](../../media/ITPro-EAC-UpArrowIcon.png)![plus élevée et](../../media/ITPro-EAC-DownArrowIcon.png) la priorité la plus faible ont une icône](../../media/ITPro-EAC-UpArrowIcon.png)![flèche vers le](../../media/ITPro-EAC-DownArrowIcon.png) bas de l’icône **n** (par exemple, icône flèche vers le bas, ![icône **2**).

3. Clic  ![Icône de flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png) ou ![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) pour déplacer la stratégie de courrier indésirable sortant personnalisé vers le haut ou vers le bas dans la liste priorité.

## <a name="use-the-security--compliance-center-to-remove-outbound-spam-policies"></a>Utiliser le centre de sécurité & conformité pour supprimer les stratégies de courrier indésirable sortant

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **paramètres de blocage du courrier indésirable** , cliquez sur ![développer](../../media/scc-expand-icon.png) pour développer la stratégie personnalisée à supprimer (la colonne **type** est **personnalisée courrier indésirable sortant**).

3. Dans les détails de la stratégie développée qui s’affichent, cliquez sur **Supprimer la stratégie**.

4. Cliquez sur **Oui** lorsque la boîte de dialogue d’avertissement s’affiche.

Vous ne pouvez pas supprimer la stratégie par défaut.

## <a name="use-exchange-online-powershell-or-exchange-online-protection-powershell-to-configure-outbound-spam-policies"></a>Utiliser Exchange Online PowerShell ou Exchange Online Protection PowerShell pour configurer des stratégies de courrier indésirable sortant

### <a name="use-powershell-to-create-outbound-spam-policies"></a>Utiliser PowerShell pour créer des stratégies de courrier indésirable sortant

La création d’une stratégie de courrier indésirable sortant dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de filtrage du courrier indésirable sortant.

2. Créez la règle de filtrage du courrier indésirable sortant qui spécifie la stratégie de filtrage du courrier indésirable sortant à laquelle la règle s’applique.

 **Remarques** :

- Vous pouvez créer une règle de filtrage du courrier indésirable sortant et lui affecter une stratégie de filtrage du courrier indésirable sortant existante non associée. Une règle de filtrage du courrier indésirable sortant ne peut pas être associée à plusieurs stratégies de filtrage du courrier indésirable sortant.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de filtrage du courrier indésirable sortant dans PowerShell qui ne sont pas disponibles dans le centre de sécurité & de sécurité tant que vous n’avez pas créé la stratégie :

  - Créez la nouvelle stratégie comme désactivé (_activé_ `$false` sur la cmdlet **New-HostedOutboundSpamFilterRule** ).

  - Définir la priorité de la stratégie lors de la création ( _ \<numéro\>_ de_priorité_ ) sur la cmdlet **New-HostedOutboundSpamFilterRule** ).

- Une nouvelle stratégie de filtrage du courrier indésirable sortant que vous créez dans PowerShell n’est pas visible dans le centre de sécurité & de conformité tant que vous n’affectez pas la stratégie à une règle de filtrage du courrier indésirable.

#### <a name="step-1-use-powershell-to-create-an-outbound-spam-filter-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie de filtrage des courriers indésirables sortants

Pour créer une stratégie de filtrage des courriers indésirables sortants, utilisez la syntaxe suivante :

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres suivants :

- Les limites de taux de destinataires sont limitées aux valeurs plus petites que celles par défaut. Pour plus d’informations, consultez la rubrique [limites d’envoi dans les options Microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).

- Une fois que l’une des limites est atteinte, l’utilisateur ne peut pas envoyer de messages.

```PowerShell
New-HostedOutboundSpamFilterPolicy -Name "Contoso Executives" -RecipientLimitExternalPerHour 400 -RecipientLimitInternalPerHour 800 -RecipientLimitPerDay 800 -ActionWhenThresholdReached BlockUser
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/new-hostedoutboundspamfilterpolicy).

#### <a name="step-2-use-powershell-to-create-an-outbound-spam-filter-rule"></a>Étape 2 : utiliser PowerShell pour créer une règle de filtrage des courriers indésirables sortants

Pour créer une règle de filtrage des courriers indésirables sortants, utilisez la syntaxe suivante :

```PowerShell
New-HostedOutboundSpamFilterRule -Name "<RuleName>" -HostedOutboundSpamFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle de filtrage du courrier indésirable sortant nommée Contoso Executives avec les paramètres suivants :

- La stratégie de filtrage du courrier indésirable sortant nommé Contoso Executives est associée à la règle.

- La règle s’applique aux membres du groupe nommé Groupe Responsables Contoso.

```PowerShell
New-HostedOutboundSpamFilterRule -Name "Contoso Executives" -HostedOutboundSpamFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/new-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-view-outbound-spam-filter-policies"></a>Utiliser PowerShell pour afficher les stratégies de filtrage du courrier indésirable sortant

Pour renvoyer une liste récapitulative de toutes les stratégies de filtrage du courrier indésirable sortant, exécutez la commande suivante :

```PowerShell
Get-HostedOutboundSpamFilterPolicy
```

Pour renvoyer des informations détaillées sur une stratégie de filtrage du courrier indésirable sortant spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie de filtrage du courrier indésirable sortant nommée Executives.

```PowerShell
Get-HostedOutboundSpamFilterPolicy -Identity "Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-view-outbound-spam-filter-rules"></a>Utiliser PowerShell pour afficher les règles de filtrage du courrier indésirable sortant

Pour afficher les règles de filtrage de courrier indésirable sortant existantes, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Pour renvoyer une liste récapitulative de toutes les règles de filtrage du courrier indésirable sortant, exécutez la commande suivante :

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

Pour renvoyer des informations détaillées sur une règle de filtrage du courrier indésirable sortant spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété pour la règle de filtrage du courrier indésirable sortant nommée Contoso Executives.

```PowerShell
Get-HostedOutboundSpamFilterRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/get-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-modify-outbound-spam-filter-policies"></a>Utiliser PowerShell pour modifier les stratégies de filtrage du courrier indésirable sortant

Les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie de filtrage des programmes malveillants dans PowerShell comme lors de la création de la stratégie, comme décrit dans la section [étape 1 : utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable sortant](#step-1-use-powershell-to-create-an-outbound-spam-filter-policy) plus haut dans cette rubrique.

**Remarque**: vous ne pouvez pas renommer une stratégie de filtrage du courrier indésirable sortant (la cmdlet **Set-HostedOutboundSpamFilterPolicy** n’a pas de paramètre _Name_ ). Lorsque vous renommez une stratégie de courrier indésirable sortant dans le centre de sécurité & conformité, vous renommez uniquement la _règle_de filtrage du courrier indésirable sortant.

Pour modifier une stratégie de filtrage des courriers indésirables sortants, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-modify-outbound-spam-filter-rules"></a>Utiliser PowerShell pour modifier les règles de filtrage du courrier indésirable sortant

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle de filtrage du courrier indésirable sortant dans PowerShell est le paramètre _activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de filtrage de courrier indésirable sortant existantes, consultez la section suivante.

Dans le cas contraire, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle de filtrage du courrier indésirable sortant dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle, comme décrit dans la section [étape 2 : utiliser PowerShell pour créer une règle de filtrage du courrier indésirable sortant](#step-2-use-powershell-to-create-an-outbound-spam-filter-rule) plus haut dans cette rubrique.

Pour modifier une règle de filtrage du courrier indésirable sortant, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/set-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-enable-or-disable-outbound-spam-filter-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de filtrage du courrier indésirable sortant

L’activation ou la désactivation d’une règle de filtrage du courrier indésirable sortant dans PowerShell active ou désactive la totalité de la stratégie anti-courrier indésirable sortant (la règle de filtrage du courrier indésirable sortant et la stratégie de filtrage du courrier indésirable sortant affecté). Vous ne pouvez pas activer ou désactiver la stratégie de courrier indésirable sortant par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/enable-hostedoutboundspamfilterrule) et [Disable-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/disable-hostedoutboundspamfilterrule).

### <a name="use-powershell-to-set-the-priority-of-outbound-spam-filter-rules"></a>Utiliser PowerShell pour définir la priorité des règles de filtrage du courrier indésirable sortant

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-HostedOutboundSpamFilterRule -Identity "Marketing Department" -Priority 2
```

**Remarques** :

- Pour définir la priorité d’une nouvelle règle lors de sa création, utilisez plutôt le paramètre _Priority_ sur la cmdlet **New-HostedOutboundSpamFilterRule** .

- La stratégie de filtrage du courrier indésirable par défaut sortante n’a pas de règle de filtrage du courrier indésirable correspondante et a toujours la valeur de priorité non modifiable la **plus faible**.

### <a name="use-powershell-to-remove-outbound-spam-filter-policies"></a>Utiliser PowerShell pour supprimer les stratégies de filtrage du courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une stratégie de filtrage du courrier indésirable sortant, la règle de filtrage du courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une stratégie de filtrage des courriers indésirables sortants dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-HostedOutboundSpamFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/remove-hostedoutboundspamfilterpolicy).

### <a name="use-powershell-to-remove-outbound-spam-filter-rules"></a>Utiliser PowerShell pour supprimer les règles de filtrage du courrier indésirable sortant

Lorsque vous utilisez PowerShell pour supprimer une règle de filtrage du courrier indésirable sortant, la stratégie de filtrage du courrier indésirable sortant correspondante n’est pas supprimée.

Pour supprimer une règle de filtrage du courrier indésirable sortant dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de filtrage du courrier indésirable sortant nommée Marketing Department.

```PowerShell
Remove-HostedOutboundSpamFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-HostedOutboundSpamFilterRule](https://docs.microsoft.com/powershell/module/exchange/antispam-antimalware/remove-hostedoutboundspamfilterrule).

## <a name="for-more-information"></a>Pour plus d'informations

[Retirer les utilisateurs bloqués du portail des utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md)

[Pool de remise à haut risque pour les messages sortants](high-risk-delivery-pool-for-outbound-messages.md)

[Forum Aux Questions sur la protection anti-courrier indésirable](anti-spam-protection-faq.md)
