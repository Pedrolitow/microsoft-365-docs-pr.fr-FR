---
title: Configuration de stratégies de filtrage du courrier indésirable
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 316544cb-db1d-4c25-a5b9-c73bbcf53047
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir comment afficher, créer, modifier et supprimer des stratégies anti-courrier indésirable dans Exchange Online Protection (EOP) autonome.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: fb4ba4f48d6f336444861b4407461efd4c8862d0
ms.sourcegitcommit: 5377b00703b6f559092afe44fb61462e97968a60
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2021
ms.locfileid: "52694508"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 ayant des boîtes aux lettres dans Exchange Online ou dans les organisations ayant Exchange Online Protection autonome (EOP) dépourvu de boîtes aux lettres Exchange Online, les courriers électroniques entrants sont automatiquement protégés contre le courrier indésirable par EOP. EOP utilise les stratégies anti-courrier indésirable (également appelées stratégies de filtrage de courrier indésirable ou stratégies de filtrage de contenu) dans le cadre de la défense globale de votre organisation contre le courrier indésirable. Pour plus d’informations, voir [Protection contre le courrier indésirable](anti-spam-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-courrier indésirable par défaut. Pour une précision accrue, vous pouvez également créer des stratégies de filtrage de courrier indésirable qui s’appliquent à des utilisateurs, à des groupes ou à des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-courrier indésirable dans le Centre de sécurité et de conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 sans boîtes aux lettres dans Exchange Online ; Exchange Online Protection PowerShell autonome pour les organisations sans boîtes aux lettres dans Exchange Online).

Les éléments de base d’une stratégie anti-courrier indésirable sont les suivants :

- **La stratégie de filtrage du courrier indésirable**: spécifie les actions de filtrage du courrier indésirable et les options de notification.
- **Une règle de filtrage de courrier indésirable**: spécifie la priorité et les filtres de destinataire (auxquels s’applique la stratégie) pour une stratégie de filtrage de courrier indésirable.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies contre le courrier indésirable dans le Centre de sécurité et conformité :

- Lorsque vous créez une stratégie contre le courrier indésirable, vous créez une règle de filtrage du courrier indésirable et la stratégie de filtrage de courrier indésirable associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie contre le courrier indésirable, les paramètres associés au nom, à la priorité, activée ou désactivée, et aux filtres de destinataire modifient réellement la règle de filtrage de courrier indésirable. Tous les autres paramètres modifient la stratégie associée de filtrage de courrier indésirable.
- Lorsque vous supprimez une stratégie anti-courrier indésirable, la règle de filtrage du courrier indésirable et la stratégie de filtrage du courrier indésirable correspondante sont supprimées.

Dans Exchange Online PowerShell ou EOP PowerShell autonome, vous gérez la stratégie et la règle séparément. Pour plus d’information, consultez la section [Utiliser Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome pour configurer les stratégies anti-courrier indésirable](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies) plus loin dans cet article.

Chaque organisation dispose d’une stratégie intégrée contre le courrier indésirable nommée Par défaut, qui contient ces propriétés :

- La stratégie est appliquée à tous les destinataires dans l’organisation, même s’il n’existe aucune règle de filtrage de courrier indésirable (filtres de destinataire) associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour améliorer l’efficacité du filtrage du courrier indésirable, vous pouvez créer des stratégies anti-courrier indésirable personnalisées, avec des paramètres plus stricts appliqués à des utilisateurs ou groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **Paramètres anti-courrier indésirable**, utilisez <https://protection.office.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter, modifier et supprimer des stratégies anti-courrier indésirable, vous devez être membre des groupes de rôles **Management de l’organisation** ou **Administrateur de sécurité**.
  - Pour l’accès en lecture seule aux stratégies anti-courrier indésirable, vous devez être membre du groupe de rôles **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Si vous souhaitez connaître les paramètres recommandés pour l’utilisation des stratégies anti-courrier indésirable, veuillez consulter la section [Paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

## <a name="use-the-security--compliance-center-to-create-anti-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour créer des stratégies anti-courrier indésirable

En créant une stratégie contre le courrier indésirable dans le Centre de sécurité et de conformité, cela créé une règle de filtrage du courrier indésirable et la stratégie de filtrage de courrier indésirable associée en utilisant le même nom pour les deux.

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier indésirable**, choisissez l’onglet **Créer une stratégie**.

3. Dans la fenêtre **Nouvelle stratégie de filtrage de courrier indésirable** qui s’ouvre, configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie. N’utilisez pas les caractères suivants : `\ % & * + / = ? { } | < > ( ) ; : , [ ] "`.

      Si vous avez précédemment créé des stratégies anti-courrier indésirable dans le Centre d’administration Exchange (EAC) qui contient ces caractères, vous devez renommer la stratégie anti-courrier indésirable dans PowerShell. Pour consulter les instructions, voir la section [Utiliser PowerShell pour modifier les règles de filtrage du courrier indésirable](#use-powershell-to-modify-spam-filter-rules) plus loin dans cet article.

   - **Description** Entrez une description facultative pour la stratégie.

4. (Facultatif) Développez la section **Actions de courrier indésirable en bloc**, puis vérifiez ou configurez les paramètres suivants :

   - **Sélectionnez l’action à entreprendre pour le courrier indésirable entrant et le courrier en bloc**: sélectionnez ou examinez l’action à effectuer sur les messages en fonction des verdicts de filtrage de courrier indésirable suivants :

     - **Courrier indésirable**
     - **Courrier indésirable hautement fiable**
     - **Courriers hameçons**
     - **E-mail de hameçonnage haute confiance**
     - **Courrier en bloc**

     Les actions disponibles pour les verdicts de filtrage du courrier indésirable sont décrites dans le tableau suivant.

     - Une coche ( ![Coche](../../media/checkmark.png)) indique que l’action est disponible (toutes les actions ne sont pas disponibles pour les verdicts de filtrage du courrier indésirable).
     - Un astérisque ( <sup>\*</sup> ) après la coche indique l’action par défaut pour le verdict de filtrage du courrier indésirable.

     ****

     |Action|Courrier indésirable|Élevé<br>confiance<br>courrier indésirable|Hameçonnage<br>email|Élevé<br>confiance<br>hameçonnage<br>email|Courrier en nombre<br>email|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Déplacer le message vers le dossier Courrier indésirable**: le message est remis dans la boîte aux lettres et déplacé vers le dossier Courrier indésirable.<sup>1</sup>|![Coche](../../media/checkmark.png)<sup>\*</sup>|![Coche](../../media/checkmark.png)<sup>\*</sup>|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)<sup>\*</sup>|
     |**Ajouter un en-tête X** : ajoute un en-tête X à l’en-tête du message et remet le message dans la boîte aux lettres. <p> Vous devez entrer le nom du champ d’en-tête X (et non la valeur) plus loin dans la zone **Ajouter ce texte d’en-tête X**. <p> Pour les verdicts de **Courrier indésirable** et **Courrier indésirable à haute fiabilité**, le message est déplacé vers le dossier Courrier indésirable.<sup>1, 2</sup>|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)<sup>\*</sup>|
     |**Ajouter la ligne d’objet avec le texte**: ajoute du texte au début de la ligne d’objet du message. Le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable.<sup>1, 2</sup> <p> Vous devez entrer le texte plus loin dans la zone **Ligne d’objet préfixe avec ce texte**.|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)|
     |**Rediriger le message vers une adresse e-mail**: envoie le message à une adresse e-mail spécifiée au lieu des destinataires prévus. <p> Spécifiez l'adresse de redirection dans la zone d'entrée **Rediriger vers cette adresse de messagerie**.|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
     |**Supprimer le message**: supprime le message entier, pièces jointes comprises.|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)|
     |**Mettre en quarantaine le message**: Envoie le message en quarantaine au lieu de le remettre à ses destinataires. <p> Vous pouvez spécifier la durée de la mise en quarantaine ultérieure du message dans la boîte de dialogue de la mise en **Quarantaine**.|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)<sup>\*</sup>|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
     |**Aucune action**|||||![Coche](../../media/checkmark.png)|
     |

     > <sup>1</sup>Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > Dans les environnements hybrides où Exchange Online Protection protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local pour traduire le verdict de filtrage de courrier indésirable Exchange Online Protection de sorte que la règle de courrier indésirable puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Vous pouvez utiliser cette valeur comme condition dans les règles de flux de courrier (ou règles de transport) pour filtrer ou acheminer le message.

   - **Sélectionner le seuil**: indique le niveau de réclamation en bloc (BCL) d’un message déclenchant l’action spécifiée pour le verdict de filtrage du courrier indésirable **Courrier en bloc** (supérieur à la valeur spécifiée, non supérieur ou égal à). Une valeur plus élevée indique que le message est moins souhaité (ce qui peut ressembler au courrier indésirable). La valeur par défaut est 7. Pour plus d’informations, voir [Niveau de réclamation en bloc (BCL) dans Exchange Online PowerShell](bulk-complaint-level-values.md) et [Quelle est la différence entre le courrier indésirable et le courrier en bloc ?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Par défaut, le paramètre PowerShell uniquement _MarkAsSpamBulkMail_ est `On` dans les stratégies anti-courrier indésirable. Ce paramètre affecte radicalement les résultats d’un verdict de filtrage de **Courrier en bloc** :

     - **_MarkAsSpamBulkMail_ est activé**: un BCL dont la valeur est supérieure au seuil est convertie en seuil de valeur SCL 6 qui correspond à un seuil de filtrage de **Courrier indésirable**, et l’action pour le verdict de filtrage de **Courrier en bloc** est pris sur le message.

     - **_MarkAsSpamBulkMail_ est désactivé**: le message est estampillé avec le BCL, mais _aucune action_ n’est prise pour un verdict de filtrage de **Courrier en bloc**. En effet, le seuil de BCL et le verdict de filtrage du **Courrier en bloc** ne sont pas pertinents.

   - **Quarantaine** : indique la durée de la mise en quarantaine du message si vous avez sélectionné **Message de quarantaine** comme action pour le verdict de filtrage du courrier indésirable. Une fois la période écoulée, le message est supprimé. La valeur par défaut est de 30 jours. Une valeur valide est comprise entre 1 et 30 jours. Pour plus d'informations à propos de la quarantaine, consultez les rubriques suivantes :

     - [Messages mis en quarantaine dans Exchange Online PowerShell](quarantine-email-messages.md)
     - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell](manage-quarantined-messages-and-files.md)
     - [Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans Exchange Online PowerShell](find-and-release-quarantined-messages-as-a-user.md)

   - **Ajouter ce texte d’en-tête X**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné **Ajouter une en-tête X** comme verdict de filtrage du courrier indésirable. La valeur que vous spécifiez est le *nom* du champ d’en-tête ajouté à l’en-tête du message. La *valeur* du champ d’en-tête est toujours `This message appears to be spam`.

     La longueur maximale est de 255 caractères et la valeur ne peut pas contenir d’espaces ou de deux-points ( :).

     Par exemple, si vous entrez la valeur `X-This-is-my-custom-header`, l’en-tête X ajouté au message est `X-This-is-my-custom-header: This message appears to be spam.`

     Si vous entrez une valeur qui contient des espaces ou des deux-points ( :), la valeur que vous entrez est ignorée et l’en-tête X par défaut est ajouté au message (`X-This-Is-Spam: This message appears to be spam.`).

   - **Ajouter la ligne d’objet avec ce texte**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné **Ajouter une ligne d’objet avec un texte** comme action pour le filtrage du courrier indésirable. Entrez le texte à ajouter au début de la ligne d’objet du message.

   - **Rediriger vers cette adresse de courrier**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné le message de redirection **Rediriger vers l’adresse de courrier** comme action pour le verdict de filtrage du courrier indésirable. Entrez l’adresse de courrier à laquelle vous voulez envoyer le message. Vous pouvez saisir plusieurs valeurs séparées par des points-virgules (;).

   - **Conseils de sécurité**: par défaut, les Conseils de sécurité sont activés, mais vous pouvez les désactiver en désactivant la case à cocher **Activé**. Pour plus d’informations sur les conseils de sécurité, voir [Conseils de sécurité dans les messages électroniques](safety-tips-in-office-365.md).

   Paramètres **Purge automatique heure zéro (ZAP)** : ZAP détecte et effectue des actions sur les messages qui ont déjà été remis aux boîtes aux lettres Exchange Online. Pour plus d’informations sur la fonction ZAP, voir [Suppression automatique heure zéro - protection contre le courrier indésirable et les programmes malveillants](zero-hour-auto-purge.md).

   - **Courrier indésirable ZAP**: par défaut, l’option ZAP est activée pour les détections de courrier indésirable, mais vous pouvez la désactiver en désactivant la case à cocher **Activé**.

   - **Hameçon ZAP**: par défaut, l’option ZAP est activée pour les détections d’hameçons, mais vous pouvez la désactiver en désactivant la case à cocher **Activé**.

5. (Facultatif) Développez la section **Liste Autoriser** pour configurer les expéditeurs de messages par adresse de courrier ou domaine de courrier qui sont autorisés à ignorer le filtrage du courrier indésirable :

   > [!CAUTION]
   >
   > - Réfléchissez soigneusement avant d’ajouter des domaines ici. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés dans Exchange Online PowerShell](create-safe-sender-lists-in-office-365.md)
   >
   > - Ne jamais ajouter des domaines acceptés (domaines vous appartenant) ou des domaines courants (par exemple, microsoft.com ou office.com) à la liste des domaines autorisés. Cela permettrait aux attaquants d’envoyer des messages électroniques qui contournent le filtrage du courrier indésirable au sein de votre organisation.

   - **Autoriser l’expéditeur** : cliquez sur **Modifier**. Dans le menu **Liste d’expéditeurs autorisés** qui s’affiche :

      a. Entrez l’adresse de courrier de l’expéditeur. Vous pouvez spécifier plusieurs adresses e-mail séparées par des points-virgules (;).

      b. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les expéditeurs.

      Répétez ces étapes autant de fois que nécessaire.

      Les expéditeurs que vous avez ajoutés apparaissent dans la section **Expéditeur autorisé** de la fenêtre mobile. Pour supprimer un expéditeur, cliquez sur ![l’icône Supprimer](../../media/scc-remove-icon.png).

      Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Autoriser le domaine** : cliquez sur **Modifier**. Dans le menu **Liste de domaines autorisés** qui s’affiche, procédez comme suit :

      a. Entrez un domaine. Vous pouvez spécifier plusieurs domaines séparés par des points-virgules (;).

      b. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les domaines.

      Répétez ces étapes autant de fois que nécessaire.

      Les domaines que vous avez ajoutés apparaissent dans la section **Domaine autorisé** de la fenêtre mobile. Pour supprimer un domaine, cliquez sur ![l’icône Supprimer](../../media/scc-remove-icon.png).

      Lorsque vous avez terminé, cliquez sur **Enregistrer**.

6. (Facultatif) Développez la section **Liste Bloquer** pour configurer les expéditeurs de messages par adresse de courrier ou domaine de courrier qui seront toujours marqués comme courrier indésirable à forte confiance :

   > [!NOTE]
   > Le blocage manuel de domaines n’est pas dangereux, mais il peut augmenter votre charge de travail administratif. Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans Exchange Online PowerShell](create-block-sender-lists-in-office-365.md).

   - **Bloquer l’expéditeur** : cliquez sur **Modifier**. Dans le menu **Liste de d’expéditeurs bloqués** qui s’affiche, procédez comme suit :

      a. Entrez l’adresse de courrier de l’expéditeur. Vous pouvez spécifier plusieurs adresses e-mail séparées par des points-virgules (;). Les caractères génériques (*)ne sont pas autorisés.

      b. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les expéditeurs.

      Répétez ces étapes autant de fois que nécessaire.

      Les expéditeurs que vous avez ajoutés apparaissent dans la section **Expéditeur bloqué** de la fenêtre mobile. Pour supprimer un expéditeur, cliquez sur ![le bouton Supprimer](../../media/scc-remove-icon.png).

      Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Bloquer le domaine** : cliquez sur **Modifier**. Dans le menu **Liste des domaines bloqués** qui s’affiche :

      a. Entrez un domaine. Vous pouvez spécifier plusieurs domaines séparés par des points-virgules (;). Les caractères génériques (*) ne sont pas autorisés.

      b. Clic  ![Icône Ajouter](../../media/c2dd8b3a-5a22-412c-a7fa-143f5b2b5612.png) pour ajouter les domaines.

      Répétez ces étapes autant de fois que nécessaire.

      Les domaines que vous avez ajoutés apparaissent dans la liste **Domaine bloqué** de la fenêtre mobile. Pour supprimer un domaine, cliquez sur ![le bouton Supprimer](../../media/scc-remove-icon.png).

      Lorsque vous avez terminé, cliquez sur **Enregistrer**.

7. (Facultatif) Développez la section **Courrier indésirable international** pour configurer les langues de messagerie ou les pays source bloqués par le filtrage du courrier indésirable :

   - **Filtrer les messages électroniques rédigés dans les langues suivantes**: ce paramètre est désactivé par défaut (**État : désactivé**). Cliquez sur **Modifier**. Dans le menu **Paramètres de courrier indésirable international** qui apparaît, configurez les paramètres suivants :

     - **Filtrer les messages électroniques rédigés dans les langues suivantes**: activez la case à cocher pour activer ce paramètre. Décochez la case pour désactiver ce paramètre.

     - Cliquez dans la zone et commencez à taper le *nom* de la langue. Une liste filtrée des langues prises en charge s’affiche, ainsi que le code de langue ISO 639-2 correspondant. Lorsque vous avez trouvé la langue que vous recherchez, sélectionnez-la. Répétez cette étape autant de fois que nécessaire.

       La liste des langues que vous avez sélectionnées s’affiche dans le menu volant. Pour supprimer une langue, cliquez ![Bouton Supprimer](../../media/scc-remove-icon.png).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Filtrer les messages électroniques envoyés depuis les pays ou régions suivants**: ce paramètre est désactivé par défaut (**État : désactivé**). Pour l’activer, cliquez sur **Modifier**. Dans le menu **Paramètres de courrier indésirable international** qui apparaît, configurez les paramètres suivants :

     - **Filtrer les courriers électroniques envoyés à partir des pays ou régions suivants**: cochez la case pour activer ce paramètre. Décochez la case pour désactiver ce paramètre.

     - Cliquez dans la zone et commencez à taper le *nom* du pays ou région. Une liste filtrée des pays pris en charge s’affiche, ainsi que le code de pays à deux lettres ISO 3166-1 correspondant. Lorsque vous trouvez le pays ou la région que vous recherchez, sélectionnez-le. Répétez cette étape autant de fois que nécessaire.

       La liste des pays que vous avez sélectionnés s’affiche dans le menu volant. Pour supprimer un pays ou une région, cliquez ![Bouton Supprimer](../../media/scc-remove-icon.png).

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

8. La section facultative **Propriétés de courrier indésirable** contient les paramètres de Filtre de courrier indésirable avancés (ASF) qui sont désactivés par défaut. Les paramètres ASF sont en cours de dépréciation et leurs fonctionnalités sont incorporées dans d’autres parties de la pile de filtrage. Nous vous recommandons de laisser tous ces paramètres ASF désactivés dans vos stratégies anti-courrier indésirable.

   Pour plus d’informations sur ces paramètres, voir [Paramètres de filtre anti-courrier indésirable avancés dans Exchange Online PowerShell](advanced-spam-filtering-asf-options.md).

9. (Obligatoire) Développez la section **Appliqué à** pour identifier les destinataires internes auxquels la stratégie s’applique.

    Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

    Il est plus facile de cliquer sur **Ajouter une condition** trois fois pour afficher toutes les conditions disponibles. Vous pouvez cliquer sur le ![bouton Supprimer](../../media/scc-remove-icon.png) pour supprimer les conditions que vous ne voulez pas configurer.

    - **Le domaine du destinataire est** : spécifie les destinataires dans un ou plusieurs domaines configurés et acceptés dans votre organisation. Cliquez dans la zone **Ajouter un indicateur** pour afficher et sélectionner un domaine. Cliquez de nouveau sur la zone **Ajouter un indicateur** pour sélectionner d’autres domaines si plusieurs domaines sont disponibles.

    - **Le destinataire est** : spécifie une ou plusieurs boîtes aux lettres, utilisateurs ou contacts de messagerie dans votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez de nouveau sur la zone **Ajouter un indicateur** pour sélectionner d’autres destinataires.

    - **Le destinataire est membre de**: spécifie un ou plusieurs groupes dans votre organisation. Cliquez sur **Ajouter un indicateur** et commencez à taper pour filtrer la liste. Cliquez de nouveau sur la zone **Ajouter un indicateur** pour sélectionner d’autres destinataires.

    - **Sauf si**: pour ajouter des exceptions à la règle, cliquez sur **Ajouter une condition** trois fois pour afficher toutes les exceptions disponibles. Les paramètres et le comportement sont exactement comme les conditions.

10. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-view-anti-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour afficher des stratégies anti-courrier indésirable

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier indésirable**, cliquez sur l’![Icône développer](../../media/scc-expand-icon.png) pour développer une stratégie anti-courrier indésirable :

   - La stratégie par défaut nommée **Stratégie de filtrage de courrier indésirable par défaut**.

   - Une stratégie personnalisée que vous avez créée où la valeur du **Type de** colonne est **stratégie anti-courrier indésirable personnalisée**.

3. Les paramètres de stratégie importants s’affichent dans les détails de stratégie développés qui s’affichent. Pour plus d’informations, cliquez sur **Modifier la stratégie**.

## <a name="use-the-security--compliance-center-to-modify-anti-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour modifier des stratégies anti-courrier indésirable

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier indésirable**, cliquez sur l’![Icône développer](../../media/scc-expand-icon.png) pour développer une stratégie anti-courrier indésirable :

   - La stratégie par défaut nommée **Stratégie de filtrage de courrier indésirable par défaut**.

   - Une stratégie personnalisée que vous avez créée où la valeur du **Type de** colonne est **stratégie anti-courrier indésirable personnalisée**.

3. Cliquez sur **Modifier une stratégie**.

Pour les stratégies anti-courrier indésirable personnalisées, les paramètres disponibles dans le menu volant qui s’affiche sont identiques à ceux décrits dans la section [Utiliser le Centre de sécurité & conformité pour créer des stratégies anti-courrier indésirable](#use-the-security--compliance-center-to-create-anti-spam-policies).

Pour la stratégie anti-courrier indésirable par défaut nommée **Stratégie de filtrage de courrier indésirable par défaut**, la section **Appliqué à** n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie, définir l’ordre de priorité de la stratégie ou configurer les notifications de mise en quarantaine de l’utilisateur final, voir les sections suivantes.

### <a name="enable-or-disable-anti-spam-policies"></a>Activer ou désactiver les stratégies anti-courrier indésirable

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier indésirable**, cliquez sur ![l’icône Développer](../../media/scc-expand-icon.png) pour développer une stratégie personnalisée que vous avez créée (la valeur dans la colonne **Type** est **Stratégie anti-courrier indésirable personnalisée**).

3. Dans les détails de la stratégie développée qui s’affichent, notez la valeur dans la colonne **Activé**.

   Déplacez le bouton bascule vers la gauche pour désactiver la stratégie : ![Désactiver](../../media/scc-toggle-off.png)

   Déplacez le bouton bascule vers la droite pour activer la stratégie : ![Activer](../../media/scc-toggle-on.png)

Vous ne pouvez pas désactiver la stratégie anti-courrier indésirable par défaut.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Définition de la priorité des stratégies anti-courrier indésirable personnalisées

Par défaut, les stratégies anti-courrier indésirable reçoivent une priorité qui dépend de l'ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité peu élevé indique une plus grande priorité (0 est le plus élevé), et les stratégies sont traitées par ordre de priorité (les stratégies à haute priorité sont traitées avant les stratégies de moindre priorité). Deux stratégies ne peuvent pas avoir la même priorité et le traitement de la stratégie s’arrête après l’application de la première stratégie.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies anti-courrier indésirable personnalisées s’affichent dans l’ordre dans lequel elles sont traitées (la première stratégie possède la valeur **Priorité** 0). La stratégie anti-courrier indésirable par défaut nommée **Stratégie de filtrage anti-courrier indésirable par défaut** contient la valeur priorité **la plus faible**, et vous ne pouvez pas la modifier.

 **Remarque**: dans le Centre de sécurité & conformité, vous pouvez uniquement modifier la priorité de la stratégie anti-courrier indésirable après sa création. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle de filtrage de courrier indésirable (ceci peut modifier la priorité de règles existantes).

Pour modifier la priorité d’une stratégie, déplacez-la vers le haut ou vers le bas de la liste (vous ne pouvez pas modifier directement le numéro de **priorité** dans le Centre de sécurité & conformité).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Sur la page **Paramètres anti-courrier indésirable**, recherchez les stratégies pour lesquelles la valeur du **Type** de colonne est **Stratégie anti-courrier indésirable personnalisée**. Notez les valeurs de la colonne **Priorité** :

   - La stratégie anti-courrier indésirable personnalisée dont la priorité est la plus élevée a la valeur ![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) **0**.

   - La stratégie anti-courrier indésirable personnalisée dont la priorité est la plus élevée a la valeur ![Icône de flèche vers le bas](../../media/ITPro-EAC-UpArrowIcon.png) **3**. (par exemple, ![Icône flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png) **3**).

   - Si vous avez au moins trois stratégies anti-courrier indésirable personnalisées, les stratégies comprises entre la priorité la plus élevée et la plus faible ont des valeurs ![Icône de flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png)![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) **n** (par exemple, ![icône de flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png)![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) **2**).

3. Clic  ![Icône de flèche vers le haut](../../media/ITPro-EAC-UpArrowIcon.png) ou ![Icône de flèche vers le bas](../../media/ITPro-EAC-DownArrowIcon.png) pour déplacer la stratégie anti-courrier indésirable personnalisée vers le haut ou le haut de la liste des priorités.

### <a name="configure-end-user-spam-notifications"></a>Configurer des notifications de courrier indésirable pour l’utilisateur final

Lorsqu’un verdict de filtre anti-courrier indésirable met un message en quarantaine, vous pouvez configurer les notifications de courrier indésirable de l’utilisateur final pour informer les destinataires de qu’il est advenu des messages qui leur ont été envoyés. Pour plus d’informations sur ces notifications, voir [Notifications de courrier indésirable à l’utilisateur final dans Exchange Online PowerShell](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Dans la page **Paramètres anti-courrier indésirable**, cliquez sur l’![Icône développer](../../media/scc-expand-icon.png) pour développer une stratégie anti-courrier indésirable :

   - La stratégie par défaut nommée **Stratégie de filtrage de courrier indésirable par défaut**.

   - Une stratégie personnalisée que vous avez créée où la valeur du **Type de** colonne est **stratégie anti-courrier indésirable personnalisée**.

3. Dans les détails de la stratégie développée qui s’affichent, cliquez sur **Configurer les notifications de courrier indésirable pour l’utilisateur final**.

4. Dans la boîte de dialogue **\<Policy Name\>** qui s’ouvre, configurez les paramètres suivants :

   - **Activer les notifications de courrier indésirable pour l’utilisateur final** : sélectionnez la case à cocher pour activer les notifications. Décochez la case pour désactiver les notifications.

   - **Envoyez des notifications de courrier indésirable à l’utilisateur final chaque (jours)**: sélectionnez la fréquence d’envoi des notifications. La valeur par défaut est de 3 jours. Vous pouvez entrer 1 à 15 jours.

     Il existe trois cycles de notification de courrier indésirable pour l’utilisateur final sur une période de 24 heures qui commencent aux heures suivantes : 01:00 UTC, 08:00 UTC et 16:00 UTC.

     > [!NOTE]
     > Si une notification du cycle précédent n’a pas été envoyée, un cycle ultérieur enverra la notification. Vous aurez alors l’impression de recevoir plusieurs notifications pour une même journée.

   - **Langue de notification**: cliquez sur la liste déroulante et sélectionnez une langue disponible dans la liste. La valeur par défaut est **Par défaut**, autrement dit l’anglais.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="use-the-security--compliance-center-to-remove-anti-spam-policies"></a>Utiliser le Centre de sécurité & conformité pour supprimer des stratégies anti-courrier indésirable

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Stratégie** \> **Anti-courrier indésirable**.

2. Sur la page **Paramètres anti-courrier indésirable**, cliquez sur ![l’icône Développer](../../media/scc-expand-icon.png) pour développer une stratégie personnalisée que vous voulez supprimer (la valeur dans la colonne **Type** est **Stratégie anti-courrier indésirable personnalisée**).

3. Dans les détails de la stratégie développée qui s’affichent, cliquez sur **Supprimer la stratégie**.

4. Cliquez sur **Oui** lorsque la boîte de dialogue d’avertissement s’affiche.

Vous ne pouvez pas supprimer la stratégie par défaut.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Utiliser Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome pour configurer les stratégies anti-courrier indésirable

Comme décrit précédemment, une stratégie anti-courrier indésirable consiste en une stratégie de filtrage du courrier indésirable et une règle de filtrage anti-courrier indésirable.

Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome, la différence entre les stratégies de filtrage du courrier indésirable et les règles de filtrage du courrier indésirable est évidente. Vous pouvez gérer les stratégies de filtrage du courrier indésirable à l’aide des applets de commande **\*-HostedContentFilterPolicy** et gérer les règles de filtrage du courrier indésirable à l’aide des applets de commande **\*-HostedContentFilterRule**.

- Dans PowerShell, commencez par créer la stratégie de filtrage du courrier indésirable, puis créez la règle de filtrage de courrier indésirable qui détermine la stratégie à laquelle s’applique à la règle.
- Dans PowerShell, modifiez séparément les paramètres de la stratégie de filtrage de courrier indésirable et la règle de filtrage de courrier indésirable.
- Lorsque vous supprimez une stratégie de filtrage de courrier indésirable de PowerShell, la règle de filtrage de courrier indésirable correspondante n’est pas automatiquement supprimée, et inversement.

Les paramètres de stratégie anti-courrier indésirable suivants sont disponibles uniquement dans PowerShell :

- Le paramètre _MarkAsSpamBulkMail_ est `On` par défaut. Les effets de ce paramètre ont été expliqués dans la section [Utiliser le Centre de sécurité et de conformité pour créer des stratégies anti-courrier indésirable](#use-the-security--compliance-center-to-create-anti-spam-policies) plus haut dans cet article.

- Les paramètres suivants pour les notifications de quarantaine de courrier indésirable de l’utilisateur final :

  - Le paramètre _DownloadLink_ qui affiche ou masque le lien vers l’Outil de création de rapports de Courrier indésirable pour Outlook.

  - Le paramètre _EndUserSpamNotificationCustomSubject_ que vous pouvez utiliser pour personnaliser la ligne d’objet de la notification.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Utiliser PowerShell pour créer des stratégies anti-courrier indésirable

La création d’une stratégie anti-courrier indésirable dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de filtrage du courrier indésirable.
2. Créez la règle de filtrage du courrier indésirable qui spécifie la stratégie de filtrage du courrier indésirable à laquelle la règle s’applique.

 **Remarques** :

- Vous pouvez créer une règle de filtrage de courrier indésirable et lui affecter une stratégie de filtrage de courrier indésirable existante, non associée. Une règle de filtrage anti-courrier indésirable ne peut pas être associée à plusieurs stratégies de filtrage de courrier indésirable.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de filtrage anti-courrier indésirable dans PowerShell qui ne sont pas disponibles dans le Centre de sécurité & de conformité tant que vous n’avez pas créé la stratégie :

  - Créez la nouvelle stratégie en tant que désactivée (_Activé_ `$false` sur l’applet de commande **New-HostedContentFilterRule**).
  - Définissez la priorité de la stratégie lors de la création (_Priorité_ _\<Number\>_) sur l’applet de commande **New-HostedContentFilterRule**).

- Une nouvelle stratégie de filtrage de courrier indésirable que vous créez dans PowerShell n’est pas visible dans le Centre de conformité & de sécurité tant que vous n’avez pas affecté la stratégie à une règle de filtrage de courrier indésirable.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable

Pour créer une stratégie de filtrage du courrier indésirable, utilisez la syntaxe suivante :

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie de filtrage du courrier indésirable appelée Responsables contoso avec les paramètres suivants :

- Mettre en quarantaine les messages lorsque le verdict du filtrage du courrier indésirable est indésirable ou du courrier indésirable a probabilité élevée.

- BCL 6 déclenche l’action pour un verdict de filtrage de courrier indésirable en bloc.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

> [!NOTE]
> **New-HostedContentFilterPolicy** et **HostedContentFilterPolicy** contiennent un ancien paramètre _ZapEnabled_, ainsi que les paramètres plus récents _PhishZapEnabled_ et _SpamZapEnabled_  . Le paramètre _ZapEnabled_ a été supprimé en février 2020. Les paramètres _PhishZapEnabled_ et _SpamZapEnabled_ héritaient de leurs valeurs du paramètre _ZapEnabled_. Mais si vous utilisez les paramètres _PhishZapEnabled_ et _SpamZapEnabled_ dans une commande ou si vous utilisez les paramètres **Courrier indésirable ZAP** ou **Hameçon ZAP** dans la stratégie anti-courrier indésirable dans le Centre de sécurité & conformité, la valeur du paramètre _ZapEnabled_ est ignorée. En d’autres termes, n’utilisez pas le paramètre _ZapEnabled_ ; utilisez les paramètres _PhishZapEnabled_ et _SpamZapEnabled_ à la place.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

#### <a name="step-2-use-powershell-to-create-a-spam-filter-rule"></a>Étape 2 : utiliser PowerShell pour créer une règle de filtrage anti-courrier indésirable

Pour créer une règle de filtrage du courrier indésirable, utilisez la syntaxe suivante :

```PowerShell
New-HostedContentFilterRule -Name "<RuleName>" -HostedContentFilterPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une nouvelle règle de filtrage anti-courrier indésirable appelée Responsables Contoso avec ces paramètres :

- La stratégie de filtrage du courrier indésirable appelée Responsables Contoso est associée à la règle.

- La règle s’applique aux membres du groupe nommé Groupe Responsables Contoso.

```PowerShell
New-HostedContentFilterRule -Name "Contoso Executives" -HostedContentFilterPolicy "Contoso Executives" -SentToMemberOf "Contoso Executives Group"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedContentFilterRule](/powershell/module/exchange/new-hostedcontentfilterrule).

### <a name="use-powershell-to-view-spam-filter-policies"></a>Utiliser PowerShell pour afficher les stratégies de filtrage du courrier indésirable

Pour renvoyer une liste récapitulative des stratégies de filtrage de courrier indésirable, exécutez la commande suivante :

```PowerShell
Get-HostedContentFilterPolicy
```

Pour renvoyer des informations détaillées sur une stratégie de filtrage de courrier indésirable spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedContentFilterPolicy -Identity "<PolicyName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie de filtrage du courrier indésirable nommée Responsables.

```PowerShell
Get-HostedContentFilterPolicy -Identity "Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

### <a name="use-powershell-to-view-spam-filter-rules"></a>Utiliser PowerShell pour afficher les règles de filtrage du courrier indésirable

Pour afficher les règles de filtrage de courrier indésirable existantes, utilisez la syntaxe suivante :

```PowerShell
Get-HostedContentFilterRule [-Identity "<RuleIdentity>] [-State <Enabled | Disabled]
```

Pour renvoyer une liste récapitulative des règles de filtrage de courrier indésirable, exécutez la commande suivante :

```PowerShell
Get-HostedContentFilterRule
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-HostedContentFilterRule -State Disabled
```

```PowerShell
Get-HostedContentFilterRule -State Enabled
```

Pour renvoyer des informations détaillées sur une règle de filtrage de courrier indésirable spécifique, utilisez la syntaxe suivante :

```PowerShell
Get-HostedContentFilterRule -Identity "<RuleName>" | Format-List [<Specific properties to view>]
```

Cet exemple renvoie toutes les valeurs de propriété de la règle de filtrage anti-courrier indésirable nommé Responsables Contoso.

```PowerShell
Get-HostedContentFilterRule -Identity "Contoso Executives" | Format-List
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedContentFilterRule](/powershell/module/exchange/get-hostedcontentfilterrule).

### <a name="use-powershell-to-modify-spam-filter-policies"></a>Utiliser PowerShell pour modifier les stratégies de filtrage du courrier indésirable

Outre les éléments suivants, les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie de filtrage du courrier indésirable dans PowerShell que lorsque vous créez une stratégie comme décrit dans la section [Étape 1 : utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable](#step-1-use-powershell-to-create-a-spam-filter-policy) plus haut dans cet article.

- Le commutateur _MakeDefault_ qui convertit la stratégie spécifiée en stratégie par défaut (appliquée à tout le monde, toujours priorité **La moins élevée**, et vous ne pouvez pas le supprimer) est disponible uniquement lorsque vous modifiez une stratégie de filtrage de courrier indésirable dans PowerShell.

- Vous ne pouvez pas renommer une stratégie de filtrage de courrier indésirable (l’applet de commande **Set-HostedContentFilterPolicy** ne possède pas de _Nom_). Lorsque vous renommez une stratégie anti-courrier indésirable dans le Centre de sécurité & conformité, vous renommez uniquement la _règle_ de filtre anti-courrier indésirable.

Pour modifier une stratégie de filtrage du courrier indésirable, utilisez la syntaxe suivante :

```PowerShell
Set-HostedContentFilterPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="use-powershell-to-modify-spam-filter-rules"></a>Utiliser PowerShell pour modifier les règles de filtrage du courrier indésirable

Le seul paramètre non disponible lorsque vous modifiez une règle de filtrage du courrier indésirable dans PowerShell est le paramètre _Activé_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver les règles de filtrage de courrier indésirable existantes, consultez la section suivante.

Dans le cas contraire, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle de filtrage du courrier indésirable dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle, comme décrit dans la section [Étape 2 : utiliser PowerShell pour créer une règle de filtrage du courrier indésirable](#step-2-use-powershell-to-create-a-spam-filter-rule) plus haut dans cet article.

Pour modifier une règle de filtrage du courrier indésirable, utilisez la syntaxe suivante :

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" <Settings>
```

Cet exemple renomme la règle de filtrage de courrier indésirable existante nommée `{Fabrikam Spam Filter}` qui peut causer des problèmes dans le Centre de sécurité & conformité.

```powershell
Set-HostedContentFilterRule -Identity "{Fabrikam Spam Filter}" -Name "Fabrikam Spam Filter"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedContentFilterRule](/powershell/module/exchange/set-hostedcontentfilterrule).

### <a name="use-powershell-to-enable-or-disable-spam-filter-rules"></a>Utiliser PowerShell pour activer ou désactiver les règles de filtrage du courrier indésirable

L’activation ou la désactivation d’une règle de filtrage du courrier indésirable dans PowerShell active ou désactive l’intégralité de la stratégie anti-courrier indésirable (la règle de filtrage anti-courrier indésirable et la stratégie de filtrage du courrier indésirable). Vous ne pouvez pas activer ou désactiver la stratégie anti-courrier indésirable par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle de filtrage des programmes malveillants dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-HostedContentFilterRule | Disable-HostedContentFilterRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle de filtrage du courrier indésirable appelée Service marketing.

```PowerShell
Disable-HostedContentFilterRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-HostedContentFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations de syntaxe et de paramètre détaillées, voir [Enable-HostedContentFilterRule](/powershell/module/exchange/enable-hostedcontentfilterrule) et [Disable-HostedContentFilterRule](/powershell/module/exchange/disable-hostedcontentfilterrule).

### <a name="use-powershell-to-set-the-priority-of-spam-filter-rules"></a>Utiliser PowerShell pour déterminer la priorité des règles de filtrage du courrier indésirable

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d'une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour déterminer la priorité d’une règle de filtrage du courrier indésirable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-HostedContentFilterRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-HostedContentFilterRule -Identity "Marketing Department" -Priority 2
```

**Remarques** :

- Remarque: pour définir la priorité d'une nouvelle règle lors de sa création, utilisez le paramètre _Priorité_ dans l’applet de commandes **New-HostedContentFilterRule**.

- La stratégie de filtrage anti-courrier indésirable par défaut ne possède pas de règle de filtrage de courrier indésirable correspondante et contient toujours la valeur de priorité non modifiable **La plus faible**.

### <a name="use-powershell-to-remove-spam-filter-policies"></a>Utiliser PowerShell pour supprimer les stratégies de filtrage du courrier indésirable

Lorsque vous utilisez PowerShell pour supprimer une stratégie de filtrage de courrier indésirable, la règle de filtrage de courrier indésirable correspondante n’est pas supprimée.

Pour supprimer une stratégie de filtrage du courrier indésirable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedContentFilterPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie de filtrage du courrier indésirable appelée Service marketing.

```PowerShell
Remove-HostedContentFilterPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-HostedContentFilterPolicy](/powershell/module/exchange/remove-hostedcontentfilterpolicy).

### <a name="use-powershell-to-remove-spam-filter-rules"></a>Utiliser PowerShell pour supprimer les règles de filtrage du courrier indésirable

Lorsque vous utilisez PowerShell pour supprimer une règle de filtrage de courrier indésirable, la stratégie de filtrage de courrier indésirable correspondante n’est pas supprimée.

Pour supprimer une règle de filtrage du courrier indésirable dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-HostedContentFilterRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle de filtrage du courrier indésirable appelée Service marketing.

```PowerShell
Remove-HostedContentFilterRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-HostedContentFilterRule](/powershell/module/exchange/remove-hostedcontentfilterrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

### <a name="send-a-gtube-message-to-test-your-spam-policy-settings"></a>Envoyez un message GTUBE pour tester vos paramètres de stratégie anti-courrier indésirable

> [!NOTE]
> Ces étapes ne fonctionnent que si l’organisation de courrier électronique à partir de laquelle vous envoyez le message GTUBE n’analyse pas le courrier indésirable sortant. Si c’est le cas, le message texte ne peut pas être envoyé.

Le test générique pour le courrier en bloc non sollicité (GTUBE) est une chaîne de texte que vous incluez dans un message de test pour vérifier les paramètres anti-courrier indésirable de votre organisation. Un message GTUBE est semblable au fichier texte EICAR (European Institute for Computer Virus Research) pour tester les paramètres des programmes malveillants.

Incluez le texte GTUBE suivant dans une ligne d'un message électronique, sans espaces ni sauts de ligne :

```text
XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
```

## <a name="allowblock-lists"></a>Listes autorisé/bloqué

Dans certains cas, nos filtres ne recevront pas le message ou l’accès à nos systèmes prend du temps. Dans ce cas, la stratégie anti-courrier indésirable inclut une liste verte et une liste rouge qui permettent de remplacer le verdict actuel. Cette option doit être utilisée avec modération uniquement dans la mesure où les listes peuvent être ingérables et temporaires dans la mesure où la pile de filtrage doit faire ce qu’elles sont censées faire.

> [!TIP]
> Dans certains cas, il est possible que votre organisation n’accepte pas le verdict fourni par le service. Dans ce cas, vous souhaiterez peut-être conserver le contenu permanent de la liste verte ou rouge. Toutefois, si vous comptez placer un domaine sur la liste verte pendant une période prolongée, demandez à l’expéditeur de vérifier que le domaine est authentifié et qu’il est paramétré sur DMARC refuser si ce n’est pas le cas.
