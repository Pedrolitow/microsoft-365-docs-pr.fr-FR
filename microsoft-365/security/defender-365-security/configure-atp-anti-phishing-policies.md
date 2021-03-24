---
title: Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
localization_priority: Normal
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à créer, modifier et supprimer les stratégies anti-hameçonnage avancées disponibles dans les organisations avec Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1c8d61aee9afb332a8426890560ad221a9c87c7d
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51065385"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies anti-hameçonnage dans Microsoft Defender pour [Office 365](defender-for-office-365.md) peuvent aider à protéger votre organisation contre les attaques par hameçonnage basées sur l’emprunt d’identité malveillant et d’autres types d’attaques par hameçonnage. Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage dans Exchange Online Protection (EOP) et les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, voir [Protection anti-hameçonnage.](anti-phishing-protection.md)

Les administrateurs peuvent afficher, modifier et configurer (mais pas supprimer) la stratégie anti-hameçonnage par défaut. Pour plus de granularité, vous pouvez également créer des stratégies anti-hameçonnage personnalisées qui s’appliquent à des utilisateurs, des groupes ou des domaines spécifiques de votre organisation. Les stratégies personnalisées priment toujours sur la stratégie par défaut. Vous pouvez cependant modifier la priorité (l'ordre d'exécution) de vos stratégies personnalisées.

Vous pouvez configurer des stratégies anti-hameçonnage dans le Centre de sécurité & conformité ou dans Exchange Online PowerShell.

Pour plus d’informations sur la configuration des stratégies anti-hameçonnage les plus limitées disponibles dans les organisations Exchange Online Protection (c’est-à-dire, les organisations sans Microsoft Defender pour Office 365), voir Configurer des stratégies anti-hameçonnage dans [EOP.](configure-anti-phishing-policies-eop.md)

Les éléments de base d’une stratégie anti-hameçonnage sont :

- **La stratégie anti-hameçonnage :** spécifie les protections de hameçonnage à activer ou désactiver, ainsi que les actions à appliquer.
- **La règle anti-hameçonnage**: spécifie la priorité et les filtres de destinataires (à qui la stratégie s’applique) pour une stratégie anti-hameçonnage.

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez des stratégies anti-hameçonnage dans le Centre de sécurité & conformité :

- Lorsque vous créez une stratégie, vous créez en même temps une règle anti-hameçonnage et la stratégie anti-hameçonnage associée en utilisant le même nom pour les deux.
- Lorsque vous modifiez une stratégie, les paramètres liés au nom, à la priorité, activé ou désactivé, et aux filtres de destinataire modifient la règle anti-hameçonnage. Tous les autres paramètres modifient la stratégie anti-hameçonnage associée.
- Lorsque vous supprimez une stratégie, la règle anti-hameçonnage et la stratégie anti-hameçonnage associée sont supprimées.

Dans Exchange Online PowerShell, vous gérez la stratégie et la règle séparément. Pour plus d’informations, voir la section Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage dans Microsoft Defender pour [Office 365](#use-exchange-online-powershell-to-configure-anti-phishing-policies-in-microsoft-defender-for-office-365) plus loin dans cet article.

Chaque organisation Microsoft Defender pour Office 365 possède une stratégie anti-hameçonnage intégrée nommée Office365 AntiPhish Default qui possède les propriétés ci-après :

- La stratégie est appliquée à tous les destinataires de l’organisation, même si aucune règle anti-hameçonnage (filtres de destinataires) n’est associée à la stratégie.
- La stratégie a la valeur de priorité personnalisée la **plus petite**, que vous ne pouvez pas modifier (la stratégie est toujours appliquée en dernier). Les stratégies personnalisées que vous créez ont toujours une priorité plus élevée.
- La stratégie est la stratégie par défaut (la propriété **IsDefault** possède la valeur`True`) et vous ne pouvez pas supprimer la stratégie par défaut.

Pour accroître l’efficacité de la protection anti-hameçonnage dans Microsoft Defender pour Office 365, vous pouvez créer des stratégies anti-hameçonnage personnalisées avec des paramètres plus stricts qui sont appliqués à des utilisateurs ou des groupes d’utilisateurs spécifiques.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page **anti-hameçonnage ATP,** utilisez <https://protection.office.com/antiphishing> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour ajouter, modifier et supprimer des stratégies anti-hameçonnage,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour accéder en lecture seule aux stratégies anti-hameçonnage,  vous  devez être membre des groupes de rôles Lecteur global ou Lecteur de <sup>\*</sup> sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le **groupe de rôles** Gestion de l’organisation en affichage seul dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) donne également un accès en lecture seule à la <sup>\*</sup> fonctionnalité.
  - <sup>\*</sup> Dans le Centre de sécurité & conformité, l’accès en lecture seule permet aux utilisateurs d’afficher les paramètres des stratégies anti-hameçonnage personnalisées. Les utilisateurs en lecture seule ne peuvent pas voir les paramètres dans la stratégie anti-hameçonnage par défaut.

- Pour obtenir les paramètres recommandés pour les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, consultez stratégie anti-hameçonnage dans Les paramètres de [Defender pour Office 365.](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)

- Autorisez jusqu’à 30 minutes pour qu’une stratégie nouvelle ou mise à jour soit appliquée.

- Pour plus d’informations sur l’endroit où les stratégies anti-hameçonnage sont appliquées dans le pipeline de filtrage, voir Ordre et priorité de la [protection du courrier électronique.](how-policies-and-protections-are-combined.md)

## <a name="use-the-security--compliance-center-to-create-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le Centre de sécurité & conformité pour créer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

La création d’une stratégie anti-hameçonnage personnalisée dans le Centre de sécurité & conformité crée la règle anti-hameçonnage et la stratégie anti-hameçonnage associée en utilisant le même nom pour les deux.

Lorsque vous créez une stratégie anti-hameçonnage, vous ne pouvez spécifier que le nom, la description et le filtre de destinataires qui identifient à qui s’applique la stratégie. Après avoir créé la stratégie, vous pouvez la modifier pour modifier ou passer en revue les paramètres anti-hameçonnage par défaut.

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**.

2. Dans la page **Anti-hameçonnage,** cliquez sur **Créer.**

3. **L’Assistant Créer une stratégie anti-hameçonnage** s’ouvre. Dans la page **Nom de votre stratégie,** configurez les paramètres suivants :

   - **Nom** Entrez un nom unique et descriptif pour la stratégie.

   - **Description** Entrez une description facultative pour la stratégie.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Appliqué à** qui s’affiche, identifiez les destinataires internes à qui s’applique la stratégie.

   Vous pouvez uniquement utiliser une condition ou une exception une seule fois, mais vous pouvez spécifier plusieurs valeurs pour la condition ou l’exception. Plusieurs valeurs de la même condition ou exception utilisent la logique OU (par exemple, _\<recipient1\>_ ou _\<recipient2\>_). Des conditions ou des exceptions différentes utilisent la logique ET (par exemple, _\<recipient1\>_ et _\<member of group 1\>_).

   Cliquez **sur Ajouter une condition.** Dans ladown qui s’affiche, sélectionnez une condition sous **Applied si**:

   - **Le destinataire est**: Spécifie une ou plusieurs boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie dans votre organisation.
   - **Le destinataire est membre de**: Spécifie un ou plusieurs groupes dans votre organisation.
   - **Le domaine du destinataire** est : Spécifie les destinataires dans un ou plusieurs des domaines acceptés configurés dans l’organisation.

   Une fois que vous avez sélectionné la condition, une zone « Tout » apparaît dans la zone « **Tout le** monde ».

   - Cliquez dans la zone et faites défiler la liste des valeurs à sélectionner.
   - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionnez une valeur.
   - Pour ajouter des valeurs supplémentaires, cliquez dans une zone vide dans la zone.
   - Pour supprimer des entrées individuelles, cliquez **sur Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) sur la valeur.
   - Pour supprimer la condition entière, cliquez **sur Supprimer** ![ l’icône ](../../media/scc-remove-icon.png) sur la condition.

   Pour ajouter une condition supplémentaire, cliquez sur **Ajouter une condition** et sélectionnez une valeur restante sous Appliqué **si**.

   Pour ajouter des exceptions, cliquez **sur Ajouter une condition** et sélectionnez une exception sous Sauf **si**. Les paramètres et le comportement sont exactement comme les conditions.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Examiner vos paramètres** qui s’affiche, examinez vos paramètres. Vous pouvez cliquer **sur Modifier** sur chaque paramètre pour le modifier.

   Lorsque vous avez terminé, cliquez sur **Créer cette stratégie.**

6. Cliquez **sur OK** dans la boîte de dialogue de confirmation qui s’affiche.

Après avoir créé la stratégie anti-hameçonnage avec ces paramètres généraux, utilisez les instructions de la section suivante pour configurer les paramètres de protection dans la stratégie.

## <a name="use-the-security--compliance-center-to-modify-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le Centre de sécurité & conformité pour modifier les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Utilisez les procédures suivantes pour modifier les stratégies anti-hameçonnage : une nouvelle stratégie que vous avez créée ou des stratégies existantes que vous avez déjà personnalisées.

1. Si vous n’y êtes pas déjà, ouvrez le  Centre de sécurité & conformité et allez à l’anti-hameçonnage ATP de la stratégie de gestion \>  \> **des menaces.**

2. Sélectionnez la stratégie anti-hameçonnage personnalisée à modifier. S’il est déjà sélectionné, désélectionnez-le et sélectionnez-le à nouveau.

3. Le **volant \<name\> Modifier votre** stratégie s’affiche. Cliquer sur **Modifier** dans n’importe quelle section vous permet d’accéder aux paramètres de cette section.

   - Les étapes suivantes sont présentées dans l’ordre d’apparition des sections, mais elles ne sont pas séquentielles (vous pouvez sélectionner et modifier les sections dans n’importe quel ordre).

   - Une fois  que vous avez cliqué sur Modifier dans une section, les paramètres disponibles sont présentés dans un  format  d’Assistant, mais vous pouvez passer dans les pages dans n’importe quel ordre et vous pouvez cliquer sur Enregistrer sur n’importe quelle page (ou  ![ ](../../media/scc-remove-icon.png) **\<name\>** sur l’icône Annuler ou Fermer pour revenir à la page Modifier votre stratégie (vous n’êtes pas obligé de visiter la dernière page de l’Assistant pour enregistrer ou quitter).

4. **Paramètre de stratégie**: cliquez **sur Modifier** pour modifier les paramètres qui étaient disponibles lorsque vous [avez](#use-the-security--compliance-center-to-create-anti-phishing-policies-in-microsoft-defender-for-office-365) créé la stratégie dans la section précédente :

   - **Name**
   - **Description**
   - **Appliqué à**
   - **Passer en revue vos paramètres**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur n’importe quelle page.

5. **Emprunt d’identité**: cliquez **sur Modifier** pour modifier les expéditeurs protégés et les domaines protégés dans la stratégie. Ces paramètres sont une condition de la stratégie qui identifie les expéditeurs usurpés à rechercher (individuellement ou par domaine) dans l’adresse De des messages entrants. Pour plus d’informations, voir Paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

   - **Ajouter des utilisateurs à protéger**: la valeur par défaut est **Off**. Pour l’activer, faites glisser le bouton bascule sur **Activer,** puis cliquez sur le bouton **Ajouter** un utilisateur qui s’affiche.

     Dans le **volant Ajouter un** utilisateur qui s’affiche, configurez les valeurs suivantes :

     - **Adresse e-mail**:

       - Cliquez dans la zone et faites défiler la liste des utilisateurs à sélectionner.
       - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionner un utilisateur.
       - Pour supprimer une entrée, cliquez **sur Supprimer** ![ ](../../media/scc-remove-icon.png) l’icône sur l’utilisateur.

     - **Nom**: cette valeur est remplie en fonction de l’adresse de messagerie que vous avez sélectionnée, mais vous pouvez la modifier.

     Lorsque vous avez terminé, cliquez sur **Enregistrer** sur n’importe quelle page.

     Pour modifier une entrée existante, sélectionnez l’utilisateur protégé dans la liste.

     > [!NOTE]
     >
     > - Dans chaque stratégie anti-hameçonnage, vous pouvez spécifier un maximum de 60 utilisateurs protégés (adresses e-mail de l’expéditeur). Vous ne pouvez pas spécifier le même utilisateur protégé dans plusieurs stratégies.
     >
     > - La protection contre l’emprunt d’identité d’utilisateur ne fonctionne pas si l’expéditeur et le destinataire ont précédemment communiqué par courrier électronique. Si l’expéditeur et le destinataire n’ont jamais communiqué par courrier électronique, le message est identifié comme une tentative d’emprunt d’identité.

   - **Ajouter des domaines à protéger**: configurez l’un des paramètres suivants ou les deux :

     - **Incluez automatiquement les domaines dont je suis propriétaire**: la valeur par défaut est **Off**. Pour l’activer, faites glisser le curseur sur **Activer.**
     - **Inclure des domaines personnalisés**: la valeur par défaut est **Off**. Pour l’activer, faites glisser le curseur  sur **Activer** et, dans la zone Ajouter des domaines, entrez le nom de domaine (par exemple, contoso.com), appuyez sur Entrée et répétez l’étape si nécessaire.

     > [!NOTE]
     > Vous pouvez avoir un maximum de 50 domaines dans toutes les stratégies anti-hameçonnage.

   - **Actions**: cliquez sur **Modifier**

     - Si des messages électroniques sont envoyés par un utilisateur dont l’identité est usurpée : configurez l’une des actions suivantes pour les messages dont l’expéditeur usurpé est l’un des utilisateurs protégés que vous avez spécifiés dans Ajouter des utilisateurs à **protéger**:

       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre le message en quarantaine**
       - **Remettre le message et ajouter d’autres adresses à la ligne Bcc**
       - **Supprimer le message avant sa livraison**

     - Si le courrier électronique est envoyé par un domaine dont l’identité est usurpée : configurez l’une des actions **suivantes** pour les messages dont l’expéditeur usurpé se trouve dans l’un des domaines protégés que vous avez spécifiés dans Ajouter des domaines à protéger :

       - **Ne pas appliquer d’action**
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre le message en quarantaine**
       - **Remettre le message et ajouter d’autres adresses à la ligne Bcc**
       - **Supprimer le message avant sa livraison**

   - Cliquez **sur Activer les conseils de sécurité d’emprunt** d’identité et configurez l’un des paramètres suivants :

     - **Afficher le conseil pour les utilisateurs dont l’identité** est usurpée : la valeur par défaut est **Désactivé.** Pour l’activer, faites glisser le curseur sur **Activer.**
     - **Afficher le conseil pour les domaines dont l’identité est emprunt** d’identité : la valeur par défaut est **Désactivé.** Pour l’activer, faites glisser le curseur sur **Activer.**
     - **Afficher la conseil pour les caractères inhabituels**: la valeur par défaut est **Off**. Pour l’activer, faites glisser le curseur sur **Activer.**

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Intelligence des boîtes aux lettres**:

     - **Activer l’intelligence de boîte** aux lettres ? : la valeur par défaut est **Activé**. Pour le désactiver, faites glisser le curseur sur **Désactiver.**

     - **Activer la protection contre l’emprunt** d’identité basée sur l’intelligence des boîtes aux **lettres**? : ce paramètre est disponible uniquement si l’intelligence de boîte **aux** lettres est activée . Activer ce paramètre pour spécifier l’action à prendre sur les messages pour les détections d’emprunt d’identité à partir des résultats de l’intelligence de boîte aux lettres.

       Dans **Si le courrier** électronique est envoyé par un utilisateur dont l’identité est usurpée, vous pouvez spécifier l’une des actions suivantes (les mêmes actions disponibles pour les utilisateurs protégés et les domaines protégés) :

       - **N’appliquez** aucune action : notez que cette valeur a le même résultat que l’activer pour activer l’intelligence de boîte aux lettres **,** mais la désaxion de la protection contre l’usurpation d’identité basée sur l’intelligence des boîtes aux **lettres ?**.
       - **Rediriger le message vers d’autres adresses de messagerie**
       - **Déplacer le message dans le dossier Courrier indésirable**
       - **Mettre le message en quarantaine**
       - **Remettre le message et ajouter d’autres adresses à la ligne Bcc**
       - **Supprimer le message avant sa livraison**

   - **Ajouter des expéditeurs et des domaines de confiance**: spécifiez des exceptions pour la stratégie :

     - **Expéditeurs fiables**:

       - Cliquez dans la zone et faites défiler la liste des utilisateurs à sélectionner.
       - Cliquez dans la zone et commencez à taper pour filtrer la liste et sélectionner un utilisateur.
       - Pour supprimer une entrée, cliquez **sur Supprimer** ![ ](../../media/scc-remove-icon.png) l’icône sur l’utilisateur.

     - **Domaines de confiance**: entrez le nom de domaine (par exemple, contoso.com), appuyez sur Entrée et répétez les étapes nécessaires.

   - **Consultez vos paramètres**: au lieu de cliquer sur chaque étape individuelle, les paramètres sont affichés dans un résumé.

     - Vous pouvez cliquer **sur Modifier** dans chaque section pour revenir à la page concernée.
     - Vous pouvez basculer les paramètres  suivants **directement** sur cette page :

       - **Utilisateurs protégés**
       - **Domaines protégés** \> **Inclure les domaines que je possède**
       - **Domaines protégés** \> **Domaines protégés** (domaines personnalisés)
       - **Veille des boîtes aux lettres**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur n’importe quelle page.

6. Usurpation d’identité : cliquez sur Modifier pour activer ou désactiver la veille contre l’usurpation d’identité, activer ou désactiver l’identification des expéditeurs non authentifiés dans Outlook et configurer l’action à appliquer aux messages provenant d’expéditeurs usurpés bloqués.  Pour plus d’informations, voir Paramètres d’usurpation [d’informations dans les stratégies anti-hameçonnage.](set-up-anti-phishing-policies.md#spoof-settings)

   Notez que ces mêmes paramètres sont également disponibles dans les stratégies anti-hameçonnage dans EOP.

   - **Paramètres du filtre** d’usurpation : la valeur par défaut est **Sur** et nous vous recommandons de la laisser. Pour le désactiver, faites glisser le curseur sur **Désactiver.** Pour plus d’informations, voir [Configurer la veille contre l’usurpation d’adresse dans EOP.](learn-about-spoof-intelligence.md)

     > [!NOTE]
     > Vous n’avez pas besoin de désactiver la protection contre l’usurpation d’usurpation si votre enregistrement MX ne pointe pas vers Microsoft 365 ; vous activez le filtrage amélioré pour les connecteurs à la place. Pour obtenir des instructions, voir [Filtrage amélioré pour les connecteurs dans Exchange Online.](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)

   - **Activer la fonctionnalité Expéditeur** non authentifié : la valeur par défaut est **Activé.** Pour le désactiver, faites glisser le curseur sur **Désactiver.**

   - **Actions**: spécifiez l’action à prendre sur les messages qui échouent à la veille contre l’usurpation d’informations :

     **Si un e-mail est envoyé par une personne qui n’est** pas autorisée à usurper votre domaine :

     - **Déplacer le message vers les dossiers Courrier indésirable des destinataires**
     - **Mettre le message en quarantaine**

   - **Consultez vos paramètres**: au lieu de cliquer sur chaque étape individuelle, les paramètres sont affichés dans un résumé.

     - Vous pouvez cliquer **sur Modifier** dans chaque section pour revenir à la page concernée.
     - Vous pouvez basculer les paramètres  suivants **directement** sur cette page :
       - **Activer la protection contre l’usurpation d’usurpation**
       - **Activer la fonctionnalité Expéditeur non authentifié**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur n’importe quelle page.

7. **Paramètres avancés :** cliquez **sur Modifier** pour configurer les seuils de hameçonnage avancés. Pour plus d’informations, voir Seuils de hameçonnage avancés dans les [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)

   - **Seuils de hameçonnage avancés**: sélectionnez l’une des valeurs suivantes :

   - **1 - Standard** (il s’agit de la valeur par défaut.)
   - **2 - Agressif**
   - **3 - Plus agressif**
   - **4 - Plus agressif**

   - **Consultez vos paramètres**: cliquez sur **Modifier** pour revenir à la page **Seuils d’hameçonnage** avancés.

   Lorsque vous avez terminé, cliquez sur **Enregistrer** sur l’une ou l’autre page.

8. De retour sur la page **Modifier votre \<Name\> stratégie,** consultez vos paramètres, puis cliquez sur **Fermer.**

### <a name="use-the-security--compliance-center-to-modify-the-default-anti-phishing-policy-in-microsoft-defender-for-office-365"></a>Utiliser le Centre de sécurité & conformité pour modifier la stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365

La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 est nommée Par défaut anti-hameçonnage Office365 et n’apparaît pas dans la liste des stratégies. Pour modifier la stratégie anti-hameçonnage par défaut, étapes suivantes :

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**.

2. Dans la page **Anti-hameçonnage,** cliquez sur **Stratégie par défaut.**

3. La page **Modifier votre stratégie Office 365 par** défaut s’affiche. Les sections suivantes sont disponibles, qui contiennent des paramètres identiques lorsque vous [modifiez une stratégie personnalisée](#use-the-security--compliance-center-to-modify-anti-phishing-policies-in-microsoft-defender-for-office-365):

   - **Emprunt d’identité**
   - **Usurpation d’usurpation**
   - **Paramètres avancés**

   Les paramètres suivants ne sont pas disponibles lorsque vous modifiez la stratégie par défaut :

   - Vous pouvez voir la **section** paramètre de stratégie  et les valeurs, mais il n’existe aucun lien Modifier, vous ne pouvez donc pas modifier les paramètres (nom de stratégie, description et à qui s’applique la stratégie (elle s’applique à tous les destinataires)).
   - Vous ne pouvez pas supprimer la stratégie par défaut.
   - Vous ne pouvez pas modifier la priorité de la stratégie par défaut (elle est toujours appliquée en dernier).

4. Dans la page **Modifier votre stratégie Par défaut, consultez** vos paramètres, puis cliquez sur **Fermer.**

### <a name="enable-or-disable-custom-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Activer ou désactiver des stratégies anti-hameçonnage personnalisées dans Microsoft Defender pour Office 365

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**.

2. Notez la valeur dans la **colonne État** :

   - Faites glisser le curseur sur **Désactivé** pour désactiver la stratégie.

   - Faites glisser le curseur sur **Activé** pour activer la stratégie.

Vous ne pouvez pas désactiver la stratégie anti-hameçonnage par défaut.

### <a name="set-the-priority-of-custom-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Définir la priorité des stratégies anti-hameçonnage personnalisées dans Microsoft Defender pour Office 365

Par défaut, les stratégies anti-hameçonnage se voir donner une priorité basée sur l’ordre de leur création (les nouvelles stratégies sont moins prioritaires que les stratégies plus anciennes). Un numéro de priorité inférieur indique une priorité plus élevée pour la stratégie (la valeur 0 est la plus élevée) et les stratégies sont traitées dans l’ordre de priorité (les stratégies de priorité supérieure sont traitées avant les stratégies de priorité inférieure). Aucune stratégie ne peut avoir la même priorité, et le traitement de stratégie s’arrête une fois la première stratégie appliquée.

Pour plus d’informations sur l’ordre de priorité et l’évaluation et l’application de plusieurs stratégies, consultez [Ordre et la priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

Les stratégies anti-hameçonnage personnalisées sont affichées dans l’ordre  de traitement (la première stratégie a la valeur Priorité 0). La stratégie anti-hameçonnage par défaut nommée Office365 AntiPhish Default a la valeur de priorité personnalisée **La** plus faible et vous ne pouvez pas la modifier.

 **Remarque**: dans le Centre de sécurité & conformité, vous ne pouvez modifier la priorité de la stratégie anti-hameçonnage qu’une fois que vous l’avez créé. Dans PowerShell, vous pouvez remplacer la priorité par défaut lorsque vous créez la règle anti-hameçonnage (ce qui peut affecter la priorité des règles existantes).

Pour modifier la priorité d’une stratégie, cliquez sur Augmenter la priorité ou Diminuer la  priorité dans les propriétés de la stratégie (vous ne pouvez pas modifier directement le numéro de priorité dans le Centre de sécurité & conformité).   La modification de la priorité d’une stratégie n’a de sens que si vous avez plusieurs stratégies.

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**.

2. Sélectionnez la stratégie à modifier. S’il est déjà sélectionné, désélectionnez-le et sélectionnez-le à nouveau.

3. Le **volant \<name\> Modifier votre** stratégie s’affiche.

   - La stratégie anti-hameçonnage  personnalisée dont la valeur de priorité **est 0** ne dispose que **du** bouton Diminuer la priorité disponible.

   - La stratégie anti-hameçonnage personnalisée  dont la valeur de priorité est la plus faible (par exemple, **3**) ne dispose que du bouton **Augmenter** la priorité disponible.

   - Si vous disposez de trois stratégies anti-hameçonnage personnalisées ou plus, les  stratégies entre les valeurs de priorité les plus élevées et les plus faibles disposent à la fois des boutons Augmenter la priorité et Diminuer la priorité. 

4. Cliquez **sur Augmenter la priorité** ou Diminuer la **priorité** pour modifier la **valeur** Priorité.

5. Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="use-the-security--compliance-center-to-view-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le Centre de sécurité & conformité pour afficher les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

1. Dans le Centre de sécurité & conformité, puis allez à  l’anti-hameçonnage ATP de la stratégie de gestion \>  \> **des menaces.**

2. Effectuez l’une des étapes suivantes :

   - Sélectionnez une stratégie anti-hameçonnage personnalisée à afficher. S’il est déjà sélectionné, désélectionnez-le et sélectionnez-le à nouveau.

   - Cliquez **sur Stratégie par** défaut pour afficher la stratégie anti-hameçonnage par défaut.

3. Le **volant \<name\> Modifier votre stratégie** s’affiche, où vous pouvez afficher les paramètres et les valeurs.

## <a name="use-the-security--compliance-center-to-remove-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser le Centre de sécurité & conformité pour supprimer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**.

2. Sélectionnez la stratégie à supprimer. S’il est déjà sélectionné, désélectionnez-le et sélectionnez-le à nouveau.

3. Dans le **volant \<name\> Modifier votre stratégie** qui s’affiche, cliquez sur Supprimer la **stratégie,** puis cliquez sur **Oui** dans la boîte de dialogue d’avertissement qui s’affiche.

Vous ne pouvez pas supprimer la stratégie par défaut.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Comme décrit précédemment, une stratégie anti-courrier indésirable se compose d’une stratégie anti-hameçonnage et d’une règle anti-hameçonnage.

Dans Exchange Online PowerShell, la différence entre les stratégies anti-hameçonnage et les règles anti-hameçonnage est évidente. Vous gérez les stratégies anti-hameçonnage à l’aide des cmdlets **\* -AntiPhishPolicy** et vous gérez les règles anti-hameçonnage à l’aide des cmdlets **\* -AntiPhishRule.**

- Dans PowerShell, vous créez d’abord la stratégie anti-hameçonnage, puis vous créez la règle anti-hameçonnage qui identifie la stratégie à qui s’applique la règle.
- Dans PowerShell, vous modifiez séparément les paramètres de la stratégie anti-hameçonnage et de la règle anti-hameçonnage.
- Lorsque vous supprimez une stratégie anti-hameçonnage de PowerShell, la règle anti-hameçonnage correspondante n’est pas automatiquement supprimée, et inversement.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Utiliser PowerShell pour créer des stratégies anti-hameçonnage

La création d’une stratégie anti-hameçonnage dans PowerShell est un processus en deux étapes :

1. Créez la stratégie anti-hameçonnage.
2. Créez la règle anti-hameçonnage qui spécifie la stratégie anti-hameçonnage à l’application de la règle.

 **Remarques** :

- Vous pouvez créer une règle anti-hameçonnage et lui attribuer une stratégie anti-hameçonnage existante et non dissociée. Une règle anti-hameçonnage ne peut pas être associée à plusieurs stratégies anti-hameçonnage.

- Vous pouvez configurer les paramètres suivants sur les nouvelles stratégies anti-hameçonnage dans PowerShell qui ne sont pas disponibles dans le Centre de sécurité & conformité tant que vous n’avez pas créé la stratégie :

  - Créez la stratégie comme _désactivée_ ( activée sur la `$false` cmdlet **New-AntiPhishRule).**
  - Définissez la priorité de la stratégie lors de la création (_Priorité_ ) sur la _\<Number\>_ cmdlet **New-AntiPhishRule).**

- Une nouvelle stratégie anti-hameçonnage que vous créez dans PowerShell n’est pas visible dans le Centre de sécurité & conformité tant que vous n’avez pas attribué la stratégie à une règle anti-hameçonnage.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>Étape 1 : Utiliser PowerShell pour créer une stratégie anti-hameçonnage

Pour créer une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Cet exemple crée une stratégie anti-hameçonnage nommée Research Quarantine avec les paramètres suivants :

- La stratégie est activée (nous n’utilisons pas le paramètre _Enabled_ et la valeur par défaut est `$true` ).
- La description est la suivante : stratégie du service de recherche.
- Active la protection des domaines d’organisation pour tous les domaines acceptés et la protection des domaines ciblés pour fabrikam.com.
- Spécifie Mai Fujito (mfujito@fabrikam.com) en tant qu’utilisateur pour empêcher l’emprunt d’identité.
- Active la boîte aux lettres décisionnelle.
- Active la protection de l’intelligence des boîtes aux lettres et spécifie l’action de mise en quarantaine.
- Active les conseils de sécurité.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>Étape 2 : Utiliser PowerShell pour créer une règle anti-hameçonnage

Pour créer une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Cet exemple crée une règle anti-hameçonnage nommée Research Department avec les conditions suivantes :

- La règle est associée à la stratégie anti-hameçonnage nommée Research Quarantine.
- La règle s’applique aux membres du groupe nommé Research Department.
- Étant donné que nous n’utilisons pas le _paramètre Priority,_ la priorité par défaut est utilisée.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Utiliser PowerShell pour afficher les stratégies anti-hameçonnage

Pour afficher les stratégies anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les stratégies anti-hameçonnage, ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Cet exemple renvoie toutes les valeurs de propriété pour la stratégie anti-hameçonnage nommée Executives.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Utiliser PowerShell pour afficher les règles anti-hameçonnage

Pour afficher les règles anti-hameçonnage existantes, utilisez la syntaxe suivante :

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Cet exemple renvoie une liste récapitulatif de toutes les règles anti-hameçonnage ainsi que les propriétés spécifiées.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Pour filtrer la liste par règles activées ou désactivées, exécutez les commandes suivantes :

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Cet exemple renvoie toutes les valeurs de propriété pour la règle anti-hameçonnage nommée Contoso Executives.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Utiliser PowerShell pour modifier des stratégies anti-hameçonnage

Outre les éléments suivants, les mêmes paramètres sont disponibles lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell que lorsque vous créez la stratégie comme décrit à l’étape 1 : Utiliser PowerShell pour créer une section de stratégie [anti-hameçonnage](#step-1-use-powershell-to-create-an-anti-phish-policy) plus tôt dans cet article.

- Le _commutateur MakeDefault_ qui transforme la stratégie spécifiée en  stratégie par défaut (appliquée à tout le monde, toujours la plus faible priorité et que vous ne pouvez pas supprimer) est disponible uniquement lorsque vous modifiez une stratégie anti-hameçonnage dans PowerShell.

- Vous ne pouvez pas renommer une stratégie anti-hameçonnage (la cmdlet **Set-AntiPhishPolicy** n’a pas de _paramètre Name)._ Lorsque vous renommez une stratégie anti-hameçonnage dans le Centre de sécurité & conformité, vous renommez uniquement la règle _anti-hameçonnage._

Pour modifier une stratégie anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Utiliser PowerShell pour modifier des règles anti-hameçonnage

Le seul paramètre qui n’est pas disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell est le paramètre _Enabled_ qui vous permet de créer une règle désactivée. Pour activer ou désactiver des règles anti-hameçonnage existantes, consultez la section suivante.

Sinon, aucun paramètre supplémentaire n’est disponible lorsque vous modifiez une règle anti-hameçonnage dans PowerShell. Les mêmes paramètres sont disponibles lorsque vous créez une règle comme décrit à l’étape 2 : Utiliser PowerShell pour créer une section de règle [anti-hameçonnage](#step-2-use-powershell-to-create-an-anti-phish-rule) plus tôt dans cet article.

Pour modifier une règle anti-hameçonnage, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Utiliser PowerShell pour activer ou désactiver des règles anti-hameçonnage

L’activation ou la désactivation d’une règle anti-hameçonnage dans PowerShell active ou désactive l’ensemble de la stratégie anti-hameçonnage (la règle anti-hameçonnage et la stratégie anti-hameçonnage affectée). Vous ne pouvez pas activer ou désactiver la stratégie anti-hameçonnage par défaut (elle est toujours appliquée à tous les destinataires).

Pour activer ou désactiver une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Cet exemple désactive la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Cet exemple montre comment activer la même règle.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) et [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Utiliser PowerShell pour définir la priorité des règles anti-hameçonnage

La valeur 0 est la priorité la plus élevée que vous pouvez définir sur une règle. La valeur la plus basse que vous pouvez définir dépend du nombre de règles. Par exemple, si vous avez cinq règles, vous pouvez utiliser les valeurs de priorité 0 à 4. Tout changement de priorité d’une règle existante peut avoir un effet en cascade sur les autres règles. Par exemple, si vous avez cinq règles personnalisées (priorités de 0 à 4) et que vous modifiez la priorité d'une règle sur 2, la règle existante de priorité 2 passe en priorité 3, et la règle de priorité 3 passe en priorité 4.

Pour définir la priorité d’une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Cet exemple définit la priorité de la règle nommée Marketing Department sur 2. Toutes les règles existantes dont la priorité est inférieure ou égale à 2 sont diminuées d’une unité (leurs numéros de priorité sont augmentés de 1).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Remarques** :

- Pour définir la priorité d’une nouvelle règle lorsque vous la créez, utilisez plutôt le paramètre _Priority_ de la cmdlet **New-AntiPhishRule.**

- La stratégie anti-hameçonnage par défaut n’a pas de règle anti-hameçonnage correspondante et elle a toujours la valeur de priorité nonmodifiable La plus **faible**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Utiliser PowerShell pour supprimer des stratégies anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une stratégie anti-hameçonnage, la règle anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une stratégie anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Cet exemple supprime la stratégie anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Utiliser PowerShell pour supprimer des règles anti-hameçonnage

Lorsque vous utilisez PowerShell pour supprimer une règle anti-hameçonnage, la stratégie anti-hameçonnage correspondante n’est pas supprimée.

Pour supprimer une règle anti-hameçonnage dans PowerShell, utilisez la syntaxe suivante :

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Cet exemple supprime la règle anti-hameçonnage nommée Marketing Department.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez correctement configuré les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365, faites l’une des opérations suivantes :

- Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **ATP anti-phishing**. Vérifiez la liste des stratégies, leurs **valeurs d’état** et leurs **valeurs de** priorité. Pour afficher plus de détails, vous pouvez suivre l’une des étapes suivantes :

  - Sélectionnez la stratégie dans la liste et affichez les détails dans le volant.
  - Cliquez **sur Stratégie par** défaut et affichez les détails dans le volant.

- Dans Exchange Online PowerShell, remplacez par le nom de la stratégie ou de la règle, puis exécutez la commande suivante \<Name\> et vérifiez les paramètres :

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```