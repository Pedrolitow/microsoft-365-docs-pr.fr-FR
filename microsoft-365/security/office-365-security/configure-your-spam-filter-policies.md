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
ms.openlocfilehash: f12a416a95f55a73bd0bbd80bfb1a4fe5121aeec
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58575899"
---
# <a name="configure-anti-spam-policies-in-eop"></a>Configuration de stratégies de blocage du courrier indésirable dans Exchange Online Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 ayant des boîtes aux lettres dans Exchange Online ou dans les organisations ayant Exchange Online Protection autonome (EOP) dépourvu de boîtes aux lettres Exchange Online, les courriers électroniques entrants sont automatiquement protégés contre le courrier indésirable par EOP. EOP utilise les stratégies anti-courrier indésirable (également appelées stratégies de filtrage de courrier indésirable ou stratégies de filtrage de contenu) dans le cadre de la défense globale de votre organisation contre le courrier indésirable. Pour plus d’informations, voir [Protection contre le courrier indésirable](anti-spam-protection.md).

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-courrier indésirable par défaut. Pour une précision accrue, vous pouvez également créer des stratégies de filtrage de courrier indésirable qui s’appliquent à des utilisateurs, à des groupes ou à des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-courrier indésirable dans le Portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 sans boîtes aux lettres dans Exchange Online ; Exchange Online Protection PowerShell autonome pour les organisations sans boîtes aux lettres dans Exchange Online).

Les éléments de base d’une stratégie anti-courrier indésirable sont les suivants :

- **La stratégie de filtrage du courrier indésirable**: spécifie les actions de filtrage du courrier indésirable et les options de notification.
- **Une règle de filtrage de courrier indésirable**: spécifie la priorité et les filtres de destinataire (auxquels s’applique la stratégie) pour une stratégie de filtrage de courrier indésirable.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies contre le courrier indésirable dans le Portail Microsoft 365 Defender :

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

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies anti-courrier indésirable**, utilisez <https://security.microsoft.com/antispam>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour ajouter, modifier et supprimer des stratégies anti-courrier indésirable, vous devez être membre des groupes de rôles **Management de l’organisation** ou **Administrateur de sécurité**.
  - Pour l’accès en lecture seule aux stratégies anti-courrier indésirable, vous devez être membre du groupe de rôles **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Si vous souhaitez connaître les paramètres recommandés pour l’utilisation des stratégies anti-courrier indésirable, veuillez consulter la section [Paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-spam-policies"></a>Utiliser le Portail Microsoft 365 Defender pour créer des stratégies anti-courrier indésirable

En créant une stratégie contre le courrier indésirable dans le Portail Microsoft 365 Defender, cela créé une règle de filtrage du courrier indésirable et la stratégie de filtrage de courrier indésirable associée en utilisant le même nom pour les deux.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable**, cliquez sur l’![icône Créer.](../../media/m365-cc-sc-create-icon.png) **Créer une stratégie**, puis sélectionnez **Entrant** dans la liste déroulante.

3. L’assistant d'application de stratégies s’ouvre. Sur la page **Nommer votre stratégie**, configurez les paramètres suivants :
   - **Nom** Entrez un nom unique et descriptif pour la stratégie.
   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Utilisateurs, groupes et domaines** qui s’affiche, identifiez les destinataires internes auxquels la stratégie s’applique (conditions de destinataire) :
   - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés dans votre organisation.
   - **Groupes** : groupes de distribution, groupes de sécurité à extension messagerie ou groupes Microsoft 365 spécifiés dans votre organisation.
   - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

   Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

   Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identificateurs (nom, nom d’affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant apparaît dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour afficher toutes les valeurs disponibles.

   Plusieurs valeurs dans la même condition utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   - **Exclure ces utilisateurs, groupes et domaines** : pour ajouter des exceptions pour les destinataires internes auxquels la stratégie s’applique (exceptions pour les destinataires), sélectionnez cette option et configurez les exceptions. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Seuil de courrier en nombre et propriétés de courrier indésirable** qui s’affiche, configurez les paramètres suivants :

   - **Seuil de courrier en bloc** : indique le niveau de réclamation en bloc (BCL) d’un message déclenchant l’action spécifiée pour le verdict de filtrage du courrier indésirable **en bloc** (supérieur à la valeur spécifiée, non supérieur ou égal à). Une valeur plus élevée indique que le message est moins souhaité (ce qui peut ressembler au courrier indésirable). La valeur par défaut est 7. Pour plus d’informations, voir [Niveau de réclamation en bloc (BCL) dans Exchange Online PowerShell](bulk-complaint-level-values.md) et [Quelle est la différence entre le courrier indésirable et le courrier en bloc ?](what-s-the-difference-between-junk-email-and-bulk-email.md).

     Par défaut, le paramètre PowerShell uniquement _MarkAsSpamBulkMail_ est `On` dans les stratégies anti-courrier indésirable. Ce paramètre affecte radicalement les résultats d’un verdict de filtrage **en bloc** :

     - **_MarkAsSpamBulkMail_ est activé**: un BCL dont la valeur est supérieure au seuil est convertie en seuil de valeur SCL 6 qui correspond à un seuil de filtrage de **Courrier indésirable**, et l’action pour le verdict de filtrage **en bloc** est pris sur le message.
     - **_MarkAsSpamBulkMail_ est désactivé**: le message est estampillé avec le BCL, mais _aucune action_ n’est prise pour un verdict de filtrage **en bloc**. En effet, le seuil de BCL et le verdict de filtrage **en bloc** ne sont pas pertinents.

   - **Augmentez le score de courrier indésirable**, **Marquez comme courrier indésirable**<sup>\*</sup> et **Mode de test** : contient les paramètres de filtre de courrier indésirable avancé (ASF) qui sont désactivés par défaut. Les paramètres ASF sont en cours de dépréciation et leurs fonctionnalités sont incorporées dans d’autres parties de la pile de filtrage. Nous vous recommandons de laisser tous ces paramètres ASF désactivés dans vos stratégies anti-courrier indésirable.

     Pour plus d’informations sur ces paramètres, voir [Paramètres de filtre anti-courrier indésirable avancés dans Exchange Online PowerShell](advanced-spam-filtering-asf-options.md).

      <sup>\*</sup> **Contient des langues spécifiques** et **À partir de ces pays** ne font pas partie des paramètres ASF.

   - **Contient des langues spécifiques** : cliquez sur la zone et sélectionnez **Activé** ou **Désactivé** dans la liste déroulante. Si vous l’activez, une zone s’affiche. Commencez à taper le nom d’une langue dans la zone. Une liste filtrée des langues prises en charge s’affiche. Lorsque vous avez trouvé la langue que vous recherchez, sélectionnez-la. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

   - **À partir de ces pays** _ : cliquez sur la zone et sélectionnez *Activé** ou **Désactivé** dans la liste déroulante. Si vous l’activez, une zone s’affiche. Commencez à taper le nom d’un pays dans la zone. Une liste filtrée des pays pris en charge s’affiche. Lorsque vous trouvez le pays que vous recherchez, sélectionnez-le. Répétez cette étape autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur l’![icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) suivant la valeur.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Action** qui s’affiche, configurez les paramètres suivants :

   - **Actions de message** : sélectionnez ou examinez l’action à effectuer sur les messages en fonction des verdicts de filtrage de courrier indésirable suivants :
     - **Courrier indésirable**
     - **Courrier indésirable hautement fiable**
     - **Hameçonnage**
     - **Hameçonnage à haute fiabilité**
     - **E-mail de masse**

     Les actions disponibles pour les verdicts de filtrage du courrier indésirable sont décrites dans le tableau suivant.

     - Une coche ( ![Marque de vérification.](../../media/checkmark.png)) indique que l’action est disponible (toutes les actions ne sont pas disponibles pour les verdicts).
     - Un astérisque ( <sup>\*</sup> ) après la coche indique l’action par défaut pour le verdict de filtrage du courrier indésirable.

     <br>

     ****

     |Action|Courrier indésirable|Élevé<br>confiance<br>courrier indésirable|Hameçonnage|Élevé<br>confiance<br>hameçonnage|Courrier en nombre|
     |---|:---:|:---:|:---:|:---:|:---:|
     |**Déplacer le message vers le dossier Courrier indésirable**: le message est remis dans la boîte aux lettres et déplacé vers le dossier Courrier indésirable.<sup>1</sup>|![Marque de vérification](../../media/checkmark.png)<sup>\*</sup>|![Marque de vérification](../../media/checkmark.png)<sup>\*</sup>|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)<sup>\*</sup>|
     |**Ajouter un en-tête X** : ajoute un en-tête X à l’en-tête du message et remet le message dans la boîte aux lettres. <p> Vous devez entrer le nom du champ d’en-tête X (et non la valeur) plus loin dans la zone **Ajouter ce texte d’en-tête X**. <p> Pour les verdicts de **Courrier indésirable** et **Courrier indésirable à haute fiabilité**, le message est déplacé vers le dossier Courrier indésirable.<sup>1, 2</sup>|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)|
     |**Ajouter la ligne d’objet avec le texte**: ajoute du texte au début de la ligne d’objet du message. Le message est remis à la boîte aux lettres et déplacé vers le dossier Courrier indésirable.<sup>1, 2</sup> <p> Vous devez entrer le texte plus loin dans la zone **Ligne d’objet préfixe avec ce texte**.|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)|
     |**Rediriger le message vers une adresse e-mail**: envoie le message à une adresse e-mail spécifiée au lieu des destinataires prévus. <p> Spécifiez l'adresse de redirection dans la zone d'entrée **Rediriger vers cette adresse de messagerie**.|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|
     |**Supprimer le message**: supprime le message entier, pièces jointes comprises.|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)||![Coche](../../media/checkmark.png)|
     |**Mettre en quarantaine le message**: Envoie le message en quarantaine au lieu de le remettre à ses destinataires. <p> Vous pouvez spécifier la durée de la mise en quarantaine ultérieure du message dans la boîte de dialogue de la mise en **Quarantaine**.|![Marque de vérification.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche](../../media/checkmark.png)<sup>\*</sup>|![Coche](../../media/checkmark.png)<sup>\*</sup>|![Coche](../../media/checkmark.png)|
     |**Aucune action**|||||![Coche](../../media/checkmark.png)|
     |

     > <sup>1</sup>Dans Exchange Online, le message est déplacé vers le dossier Courrier indésirable si la règle de courrier indésirable est activée sur la boîte aux lettres (elle est activée par défaut). Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).
     >
     > Dans les environnements hybrides où Exchange Online Protection protège les boîtes aux lettres Exchange locales, vous devez configurer des règles de flux de courrier (également appelées règles de transport) dans Exchange local pour traduire le verdict de filtrage de courrier indésirable Exchange Online Protection de sorte que la règle de courrier indésirable puisse déplacer le message vers le dossier Courrier indésirable. Pour les détails, voir [Configurer Exchange Online Protection (EOP) pour envoyer des courriers indésirables dans le dossier Courrier indésirable dans les environnements hybrides](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).
     >
     > <sup>2</sup> Vous pouvez utiliser cette valeur comme condition dans les règles de flux de courrier (ou règles de transport) pour filtrer ou acheminer le message.

   - **Conserver le courrier indésirable en quarantaine pendant ce nombre de jours** : indique la durée de la mise en quarantaine du message si vous avez sélectionné **Message de quarantaine** comme action pour le verdict de filtrage du courrier indésirable. Une fois la période écoulée, le message est supprimé. La valeur par défaut est de 30 jours. Une valeur valide est comprise entre 1 et 30 jours. Pour plus d'informations à propos de la quarantaine, consultez les rubriques suivantes:

     - [Messages mis en quarantaine dans Exchange Online PowerShell](quarantine-email-messages.md)
     - [Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell](manage-quarantined-messages-and-files.md)
     - [Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans Exchange Online PowerShell](find-and-release-quarantined-messages-as-a-user.md)

   - **Ajouter ce texte d’en-tête X**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné **Ajouter une en-tête X** comme verdict de filtrage du courrier indésirable. La valeur que vous spécifiez est le *nom* du champ d’en-tête ajouté à l’en-tête du message. La *valeur* du champ d’en-tête est toujours `This message appears to be spam`.

     La longueur maximale est de 255 caractères et la valeur ne peut pas contenir d’espaces ou de deux-points ( :).

     Par exemple, si vous entrez la valeur `X-This-is-my-custom-header`, l’en-tête X ajouté au message est `X-This-is-my-custom-header: This message appears to be spam.`

     Si vous entrez une valeur qui contient des espaces ou des deux-points ( :), la valeur que vous entrez est ignorée et l’en-tête X par défaut est ajouté au message (`X-This-Is-Spam: This message appears to be spam.`).

   - **Ajouter la ligne d’objet avec ce texte**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné **Ajouter une ligne d’objet avec un texte** comme action pour le filtrage du courrier indésirable. Entrez le texte à ajouter au début de la ligne d’objet du message.

   - **Rediriger vers cette adresse de courrier**: cette zone est obligatoire et disponible uniquement si vous avez sélectionné le message de redirection **Rediriger vers l’adresse de courrier** comme action pour le verdict de filtrage du courrier indésirable. Entrez l’adresse de courrier à laquelle vous voulez envoyer le message. Vous pouvez saisir plusieurs valeurs séparées par des points-virgules (;).

   - **Activer les conseils de sécurité** : par défaut, les Conseils de sécurité sont activés, mais vous pouvez les désactiver en désactivant la case à cocher.

   - **Activer la purge automatique zéro heure (PAZH)** : ZAP détecte et effectue des actions sur les messages qui ont déjà été remis aux boîtes aux lettres Exchange Online. Pour plus d’informations, consultez [Suppression automatique heure zéro - protection contre le courrier indésirable et les programmes malveillants](zero-hour-auto-purge.md).

     ZAP est activé par défaut. Lorsque ZAP est activé, les paramètres suivants sont disponibles :

     - **Activer ZAP pour les messages de hameçonnage** : par défaut, l’option ZAP est activée pour les détections d’hameçons, mais vous pouvez la désactiver en désactivant la case à cocher.
     - **Activer ZAP pour les courriers indésirables** : par défaut, l’option ZAP est activée pour les détections de courrier indésirable, mais vous pouvez la désactiver en désactivant la case à cocher.

   - **Activer les notifications de courrier indésirable de l’utilisateur final** : Pour plus d’informations, consultez la section [Configurer les notifications de courrier indésirable de l’utilisateur final](#configure-end-user-spam-notifications) plus loin dans cette rubrique.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

7. Dans la menu volant **Liste verte et rouge** qui s’affiche, vous pouvez configurer les expéditeurs de messages par adresse e-mail ou par domaine de courrier qui sont autorisés à ignorer le filtrage du courrier indésirable.

   Dans la section **Autorisé**, vous pouvez configurer les expéditeurs autorisés et les domaines autorisés. Dans la section **Bloqué**, vous pouvez ajouter des expéditeurs bloqués et des domaines bloqués.

   > [!IMPORTANT]
   >
   > Réfléchissez soigneusement avant d’ajouter des domaines à la liste des domaines autorisés. Si vous souhaitez en savoir plus, consultez la page [Créer des listes d’expéditeurs approuvés dans Exchange Online PowerShell](create-safe-sender-lists-in-office-365.md)
   >
   > N’ajoutez jamais vos propres [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) ou des domaines communs (par exemple, microsoft.com ou office.com) à la liste des domaines autorisés. Si ces domaines sont autorisés à contourner le filtrage du courrier indésirable, les attaquants peuvent facilement envoyer des messages usurpant ces domaines approuvés dans votre organisation.
   >
   > Le blocage manuel des domaines en ajoutant les domaines à la liste des domaines bloqués n’est pas dangereux, mais il peut augmenter votre charge de travail administratif. Pour plus d’informations, voir [Créer des listes d’expéditeurs bloqués dans Exchange Online PowerShell](create-block-sender-lists-in-office-365.md).
   >
   > Dans certains cas, nos filtres ne recevront pas un message, que vous n’acceptiez pas le verdict de filtrage ou que nos systèmes prennent du temps pour y parvenir. Dans ce cas, la liste verte et la liste rouge sont disponibles pour remplacer les verdicts de filtrage actuels. Toutefois, vous devez utiliser ces listes avec parcimonie et temporairement : les listes longs peuvent devenir ingérables et notre pile de filtrage doit faire ce qu’elle est supposée faire. Si vous prévoyez de conserver un domaine autorisé pendant une période prolongée, vous devez indiquer à l'expéditeur de vérifier que son domaine est authentifié et de le configurer pour qu'il soit rejeté par DMARC s'il ne l'est pas.

   Les étapes permettant d’ajouter des entrées à l’une des listes sont les mêmes :

   1. Cliquez sur le lien correspondant à la liste que vous souhaitez configurer :
      - **Autorisés** \> **Expéditeurs** : cliquez sur **Gérer (nn) expéditeur(s)**.
      - **Autorisés** \> **Domaines** : cliquez sur **Autoriser les domaines**.
      - **Bloqués** \> **Expéditeurs** : cliquez sur **Gérer (nn) expéditeur(s)**.
      - **Bloqués** \> **Domaines** : cliquez sur **Bloquer les domaines**.

   2. Dans le menu volant qui s’affiche, procédez comme suit :
      1. Cliquez sur ![Créer une icône](../../media/m365-cc-sc-create-icon.png) **Ajouter des expéditeurs** ou **Ajouter des domaines**.
      2. Dans le menu volant **Ajouter des expéditeurs** ou **Ajouter des domaines** qui s’affiche, entrez l’adresse e-mail de l’expéditeur dans la zone **Expéditeur** ou le domaine dans la zone **Domaine**. Lorsque vous tapez, la valeur s’affiche sous la zone. Lorsque vous avez fini de taper l’adresse e-mail ou le domaine, sélectionnez la valeur sous la zone.
      3. Répétez l’étape précédente autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

      Lorsque vous avez terminé, cliquez sur **Ajouter des expéditeurs** ou **Ajouter des domaines**.

      Dans le menu volant principal, les expéditeurs ou domaines que vous avez ajoutés sont répertoriés sur la page. Pour supprimer une entrée de cette page, procédez comme suit :

      1. Sélectionnez une ou plusieurs entrées dans la liste. Vous pouvez également utiliser la zone de **Recherche** pour rechercher des valeurs dans la liste.
      2. Après avoir sélectionné au moins une entrée, l’icône Supprimer ![Icône Effacer.](../../media/m365-cc-sc-delete-icon.png) s’affiche.
      3. Cliquez sur l’icône Supprimer ![Icône Effacer.](../../media/m365-cc-sc-delete-icon.png) pour supprimer les entrées sélectionnées.

      Lorsque vous avez terminé, cliquez sur **Terminé**.

      De retour sur la page **Liste rouge/verte**, cliquez sur **Suivant** lorsque vous êtes prêt à continuer.

8. Dans la page **Révision** qui s’affiche, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Créer**.

9. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-spam-policies"></a>Utiliser le Portail Microsoft 365 Defender pour afficher des stratégies anti-courrier indésirable

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable**, recherchez l’une des valeurs suivantes :
   - La valeur **Type** est **Stratégie anti-courrier indésirable personnalisée**
   - La valeur **Name** est **Stratégie de trafic entrant anti-courrier indésirable (par défaut)**

   Les propriétés suivantes sont affichées dans la liste des stratégies anti-courrier indésirable :

   - **Name**
   - **État**
   - **Priorité**
   - **Type (Type)**

3. Lorsque vous sélectionnez une stratégie anti-courrier indésirable en cliquant sur le nom, les paramètres de stratégie s’affichent dans un menu volant.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-spam-policies"></a>Utiliser le Portail Microsoft 365 Defender pour modifier des stratégies anti-courrier indésirable

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable**, sélectionnez une stratégie anti-courrier indésirable dans la liste en cliquant sur le nom :
   - Une stratégie personnalisée que vous avez créée où la valeur du **Type de** colonne est **stratégie anti-courrier indésirable personnalisée**.
   - La stratégie par défaut nommée **Stratégie de trafic entrant anti-courrier indésirable (par défaut)**.

3. Dans le menu volant des détails de stratégie qui s’affiche, sélectionnez **Modifier** dans chaque section pour modifier les paramètres de la section. Pour plus d’informations sur les paramètres, consultez la section précédente [Utiliser le Portail Microsoft 365 Defender pour créer des stratégies anti-courrier indésirable](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) de cet article.

   Pour la stratégie anti-courrier indésirable par défaut, la section **Appliqué à** n’est pas disponible (la stratégie s’applique à tout le monde) et vous ne pouvez pas renommer la stratégie.

Pour activer ou désactiver une stratégie, définir l’ordre de priorité de la stratégie ou configurer les notifications de mise en quarantaine de l’utilisateur final, voir les sections suivantes.

### <a name="enable-or-disable-anti-spam-policies"></a>Activer ou désactiver les stratégies anti-courrier indésirable

Vous ne pouvez pas désactiver la stratégie anti-courrier indésirable par défaut.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **stratégies anti-courrier indésirable**, sélectionnez une stratégie avec la **Valeur de type** de **Stratégie anti-courrier indésirable personnalisée** dans la liste en cliquant sur le nom.

3. En haut du menu volant des détails de stratégie qui s’affiche, vous verrez l’une des valeurs suivantes :
   - **Stratégie désactivée** : Pour activer la stratégie, cliquez sur l’![icône Activer.](../../media/m365-cc-sc-turn-on-off-icon.png) **Activer**.
   - **Stratégie sur**: Pour désactiver la stratégie,cliquez sur ![l’icône Désactiver.](../../media/m365-cc-sc-turn-on-off-icon.png) **Désactiver**.

4. Dans la boîte de dialogue de confirmation qui s’affiche, cliquez sur **Activer** ou **Désactiver**.

5. Cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

De retour sur la page principale de la stratégie, la valeur **État** de la stratégie sera **Activée** ou **Désactivée**.

### <a name="set-the-priority-of-custom-anti-spam-policies"></a>Définition de la priorité des stratégies anti-courrier indésirable personnalisées

Par défaut, les stratégies anti-courrier indésirable reçoivent une priorité qui dépend de l'ordre dans lequel elles ont été créées (les stratégies plus récentes sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité peu élevé indique une plus grande priorité (0 est le plus élevé), et les stratégies sont traitées par ordre de priorité (les stratégies à haute priorité sont traitées avant les stratégies de moindre priorité). Deux stratégies ne peuvent pas avoir la même priorité et le traitement de la stratégie s’arrête après l’application de la première stratégie.

Pour modifier la priorité d’une stratégie, cliquez sur **Augmenter la priorité** ou **Diminuer la priorité** dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro **Priorité** dans le Portail Microsoft 365 Defender). La modification de la priorité d’une stratégie n’a de sens que si vous avez plusieurs stratégies.

 **Remarques** :

- Dans le Portail Microsoft 365 Defender, vous pouvez uniquement modifier la priorité de la stratégie de logiciel anti-courrier indésirable après l'avoir créée. Dans PowerShell, vous pouvez remplacer la priorité par défaut lors de la création de la règle de filtrage de courrier indésirable (ceci peut modifier la priorité de règles existantes).
- Les stratégies anti-courrier indésirable sont traitées dans l’ordre dans lequel elles sont affichées (la première stratégie possède la valeur **Priorité** 0). La stratégie anti-courrier indésirable par défaut contient la valeur priorité **la plus faible**, et vous ne pouvez pas la modifier.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **stratégies anti-courrier indésirable**, sélectionnez une stratégie avec la **Valeur de type** de **Stratégie anti-courrier indésirable personnalisée** dans la liste en cliquant sur le nom.

3. En haut du menu volant détails de la stratégie qui s’affiche, vous verrez **Augmenter la priorité** ou **Diminuer la priorité** en fonction de la valeur de priorité actuelle et du nombre de stratégies personnalisées :
   - La stratégie anti-courrier indésirable avec la valeur **Priorité** **0** a uniquement l’option **Diminuer la priorité** disponible.
   - La stratégie anti-courrier indésirable avec la valeur **Priorité** (par exemple, **3**) a uniquement l’option **Augmenter la priorité** disponible.
   - Si vous avez au moins trois stratégies anti-courrier indésirable, les stratégies entre les valeurs de priorité la plus élevée et la plus basse ont les options **Augmenter la priorité** et **Diminuer la priorité** disponibles.

   Cliquez sur l’![Icône Augmenter la priorité](../../media/m365-cc-sc-increase-icon.png) **Augmenter la priorité** ou ![Icône Diminuer la priorité](../../media/m365-cc-sc-decrease-icon.png) **Diminuer la priorité** pour modifier la valeur **Priorité**.

4. Lorsque vous avez terminé, cliquez sur **Fermer** dans le menu volant des détails de la stratégie.

### <a name="configure-end-user-spam-notifications"></a>Configurer des notifications de courrier indésirable pour l’utilisateur final

> [!NOTE]
> Les notifications de courrier indésirable de l’utilisateur final ne sont pas prises en charge pour les groupes.

Lorsqu’un verdict de filtre anti-courrier indésirable met un message en quarantaine, vous pouvez configurer les notifications de courrier indésirable de l’utilisateur final pour informer les destinataires de qu’il est advenu des messages qui leur ont été envoyés. Pour plus d’informations sur ces notifications, voir [Notifications de courrier indésirable à l’utilisateur final dans Exchange Online PowerShell](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **Stratégies anti-courrier indésirable**, sélectionnez une stratégie anti-courrier indésirable dans la liste en cliquant sur le nom :
   - Une stratégie personnalisée que vous avez créée où la valeur du **Type de** colonne est **stratégie anti-courrier indésirable personnalisée**.
   - La stratégie par défaut nommée **Stratégie de trafic entrant anti-courrier indésirable (par défaut)**.

3. Dans le menu volant des détails de stratégie qui s’affiche, cliquez sur **Modifier** dans la section **Actions**. Dans le menu volant **Action** qui s’affiche, configurez les paramètres suivants :

   - **Activer les notifications de courrier indésirable pour l’utilisateur final** : sélectionnez la case à cocher pour activer les notifications ou décochez la case pour désactiver les notifications. Lorsque vous cochez la case, les paramètres supplémentaires suivants s’affichent :

     - **Envoyez des notifications de courrier indésirable à l’utilisateur final chaque (jours)**: sélectionnez la fréquence d’envoi des notifications. La valeur par défaut est de 3 jours. Vous pouvez entrer 1 à 15 jours.

       Il existe trois cycles de notification de courrier indésirable pour l’utilisateur final sur une période de 24 heures qui commencent aux heures suivantes : 01:00 UTC, 08:00 UTC et 16:00 UTC.

       > [!NOTE]
       > Si une notification du cycle précédent n’a pas été envoyée, un cycle ultérieur enverra la notification. Vous aurez alors l’impression de recevoir plusieurs notifications pour une même journée.

     - **Langue** : cliquez sur la liste déroulante et sélectionnez une langue disponible dans la liste. La valeur par défaut est **Par défaut**, autrement dit l’anglais.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. Dans le menu volant des détails de la stratégie, cliquez sur **Fermer**.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-spam-policies"></a>Utiliser le Portail Microsoft 365 Defender pour supprimer des stratégies anti-courrier indésirable personnalisées

Lorsque vous utilisez le Portail Microsoft 365 Defender pour supprimer une stratégie anti-courrier indésirable personnalisée, la règle de filtrage du courrier indésirable et la stratégie de filtrage du courrier indésirable correspondante sont toutes deux supprimées. Vous ne pouvez pas supprimer la stratégie anti-courrier indésirable par défaut.

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Stratégies et règles** \> **Stratégies de menace** \> **Stratégies Anti-courrier indésirable** dans la section **Stratégies**.

2. Dans la page **stratégies anti-courrier indésirable**, sélectionnez une stratégie avec la **Valeur de type** de **Stratégie anti-courrier indésirable personnalisée** dans la liste en cliquant sur le nom. En haut du menu volant des détails de la stratégie qui s’affiche, cliquez sur l’![icône Autres actions. ](../../media/m365-cc-sc-more-actions-icon.png) **Plus d’actions**\>![icône Supprimer la stratégie](../../media/m365-cc-sc-delete-icon.png)**Supprimer la stratégie**.

3. Dans la boîte de dialogue de confirmation qui s'affiche, cliquez sur **Oui**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-spam-policies"></a>Utiliser Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome pour configurer les stratégies anti-courrier indésirable

Comme décrit précédemment, une stratégie anti-courrier indésirable consiste en une stratégie de filtrage du courrier indésirable et une règle de filtrage anti-courrier indésirable.

Dans Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome, la différence entre les stratégies de filtrage du courrier indésirable et les règles de filtrage du courrier indésirable est évidente. Vous pouvez gérer les stratégies de filtrage du courrier indésirable à l’aide des applets de commande **\*-HostedContentFilterPolicy** et gérer les règles de filtrage du courrier indésirable à l’aide des applets de commande **\*-HostedContentFilterRule**.

- Dans PowerShell, commencez par créer la stratégie de filtrage du courrier indésirable, puis créez la règle de filtrage de courrier indésirable qui détermine la stratégie à laquelle s’applique à la règle.
- Dans PowerShell, modifiez séparément les paramètres de la stratégie de filtrage de courrier indésirable et la règle de filtrage de courrier indésirable.
- Lorsque vous supprimez une stratégie de filtrage de courrier indésirable de PowerShell, la règle de filtrage de courrier indésirable correspondante n’est pas automatiquement supprimée, et inversement.

Les paramètres de stratégie anti-courrier indésirable suivants sont disponibles uniquement dans PowerShell :

- Le paramètre _MarkAsSpamBulkMail_ est `On` par défaut. Les effets de ce paramètre ont été expliqués dans la section [Utiliser le Portail Microsoft 365 Defender pour créer des stratégies anti-courrier indésirable](#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) plus haut dans cet article.

- Les paramètres suivants pour les notifications de quarantaine de courrier indésirable de l’utilisateur final :
  - Le paramètre _DownloadLink_ qui affiche ou masque le lien vers l’Outil de création de rapports de Courrier indésirable pour Outlook.
  - Le paramètre _EndUserSpamNotificationCustomSubject_ que vous pouvez utiliser pour personnaliser la ligne d’objet de la notification.

### <a name="use-powershell-to-create-anti-spam-policies"></a>Utiliser PowerShell pour créer des stratégies anti-courrier indésirable

La création d’une stratégie anti-courrier indésirable dans PowerShell est un processus en deux étapes :

1. Créez la stratégie de filtrage du courrier indésirable.
2. Créez la règle de filtrage du courrier indésirable qui spécifie la stratégie de filtrage du courrier indésirable à laquelle la règle s’applique.

 **Remarques** :

- Vous pouvez créer une règle de filtrage de courrier indésirable et lui affecter une stratégie de filtrage de courrier indésirable existante, non associée. Une règle de filtrage anti-courrier indésirable ne peut pas être associée à plusieurs stratégies de filtrage de courrier indésirable.
- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies de filtrage anti-courrier indésirable dans PowerShell qui ne sont pas disponibles dans le Portail Microsoft 365 Defender tant que vous n’avez pas créé la stratégie :
  - Créez la nouvelle stratégie en tant que désactivée (_Activé_ `$false` sur l’applet de commande **New-HostedContentFilterRule**).
  - Définissez la priorité de la stratégie lors de la création (_Priorité_ _\<Number\>_) sur l’applet de commande **New-HostedContentFilterRule**).

- Une nouvelle stratégie de filtrage de courrier indésirable que vous créez dans PowerShell n’est pas visible dans le Portail Microsoft 365 Defender tant que vous n’avez pas affecté la stratégie à une règle de filtrage de courrier indésirable.

#### <a name="step-1-use-powershell-to-create-a-spam-filter-policy"></a>Étape 1 : utiliser PowerShell pour créer une stratégie de filtrage du courrier indésirable

Pour créer une stratégie de filtrage du courrier indésirable, utilisez la syntaxe suivante :

```PowerShell
New-HostedContentFilterPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie de filtrage du courrier indésirable appelée Responsables contoso avec les paramètres suivants :

- Mettre en quarantaine les messages lorsque le verdict du filtrage du courrier indésirable est indésirable ou du courrier indésirable a probabilité élevée.
- BCL 7, 8 ou 9 déclenche l’action pour un verdict de filtrage de courrier indésirable en bloc.

```PowerShell
New-HostedContentFilterPolicy -Name "Contoso Executives" -HighConfidenceSpamAction Quarantine -SpamAction Quarantine -BulkThreshold 6
```

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
- Vous ne pouvez pas renommer une stratégie de filtrage de courrier indésirable (l’applet de commande **Set-HostedContentFilterPolicy** ne possède pas de _Nom_). Lorsque vous renommez une stratégie anti-courrier indésirable dans le Portail Microsoft 365 Defender, vous renommez uniquement la _règle_ de filtre anti-courrier indésirable.

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

Cet exemple renomme la règle de filtrage du courrier indésirable existante nommée `{Fabrikam Spam Filter}`.

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

**Remarques** :

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
