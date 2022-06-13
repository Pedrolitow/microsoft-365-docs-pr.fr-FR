---
title: Personnaliser une stratégie d’archivage et de suppression (MRM) pour les boîtes aux lettres
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
ms.assetid: ec3587e4-7b4a-40fb-8fb8-8aa05aeae2ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Comment créer une stratégie d’archivage et de suppression mrm (Messaging Records Management) personnalisée pour déplacer automatiquement des éléments vers la boîte aux lettres d’archivage d’un utilisateur.
ms.openlocfilehash: 9ea642dc9d6aa4e66938703b45a8af0bab53476f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012999"
---
# <a name="customize-an-archive-and-deletion-policy-for-mailboxes-in-your-organization"></a>Personnaliser une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Les administrateurs Microsoft Purview peuvent créer une stratégie d’archivage et de suppression qui déplace automatiquement les éléments vers la [boîte aux lettres d’archivage](archive-mailboxes.md) d’un utilisateur et supprime automatiquement les éléments de la boîte aux lettres.

Pour ce faire, vous créez une stratégie de rétention mrm (Messaging Records Management) que vous affectez ensuite aux boîtes aux lettres. Cette stratégie déplace les éléments vers la boîte aux lettres d’archivage d’un utilisateur après une période spécifiée et supprime également les éléments de la boîte aux lettres une fois qu’ils ont atteint une certaine limite d’âge.

Les règles réelles qui déterminent les éléments qui sont déplacés ou supprimés et quand cela se produit sont appelées balises de rétention. Les balises de rétention sont liées à une stratégie de rétention MRM, qui à son tour est affectée à la boîte aux lettres d’un utilisateur. Une balise de rétention applique des paramètres de rétention à des messages et dossiers individuels dans la boîte aux lettres d’un utilisateur. Il définit la durée pendant laquelle un message reste dans la boîte aux lettres et l’action effectuée lorsque le message atteint l’âge de rétention spécifié. Lorsqu’un message atteint son âge de rétention, il est déplacé vers la boîte aux lettres d’archivage de l’utilisateur ou supprimé.
  
Les étapes décrites dans cet article définissent une stratégie d’archivage et de rétention pour une organisation fictive nommée Alpine House. La configuration de cette stratégie comprend les tâches suivantes :
  
- Activez une boîte aux lettres d’archivage pour chaque utilisateur de l’organisation. Cette procédure offre aux utilisateurs davantage de stockage de boîtes aux lettres et est nécessaire pour qu’une stratégie de rétention puisse déplacer automatiquement les éléments vers la boîte aux lettres d’archivage. Un utilisateur peut également déplacer manuellement des éléments vers leur boîte aux lettres d’archivage pour le stockage d’archivage.

- Créez trois balises de rétention personnalisées pour effectuer les actions suivantes :

  - Déplacez automatiquement les éléments âgés de 3 ans vers la boîte aux lettres d’archivage de l’utilisateur. Le déplacement d’éléments vers la boîte aux lettres d’archivage libère de l’espace dans la boîte aux lettres principale d’un utilisateur.

  - Supprimez automatiquement les éléments âgés de 5 ans du dossier Éléments supprimés. Cela libère également de l’espace dans la boîte aux lettres principale de l’utilisateur. Les utilisateurs auront la possibilité de récupérer ces éléments si nécessaire. Pour plus d’informations, consultez la note de bas de page de la section [Plus d’informations](#more-information) . 

  - Supprimez automatiquement (et définitivement) les éléments âgés de 7 ans à la fois de la boîte aux lettres primaire et de la boîte aux lettres d’archivage. En raison des réglementations de conformité, certaines organisations sont tenues de conserver le courrier électronique pendant une période spécifique. Lorsque cette période expire, une organisation peut vouloir supprimer définitivement ces éléments des boîtes aux lettres utilisateur.

- Créez une stratégie de rétention et ajoutez-y les nouvelles balises de rétention personnalisées. En outre, vous allez également ajouter des balises de rétention intégrées à la nouvelle stratégie de rétention. Cela inclut les balises personnelles que les utilisateurs peuvent affecter aux éléments de leur boîte aux lettres. Vous allez également ajouter une balise de rétention qui déplace les éléments du dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur vers le dossier Éléments récupérables dans leur boîte aux lettres d’archivage. Cette action permet de libérer de l’espace dans le dossier Éléments récupérables d’un utilisateur lorsque sa boîte aux lettres est mise en attente.

Vous pouvez suivre une partie ou l’ensemble des étapes décrites dans cet article pour configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre propre organisation. Nous vous recommandons de tester ce processus sur quelques boîtes aux lettres avant de l’implémenter sur toutes les boîtes aux lettres de votre organisation.
  
## <a name="before-you-set-up-an-archive-and-deletion-policy"></a>Avant de configurer une stratégie d’archivage et de suppression

- Vous devez être un administrateur général de votre organisation pour effectuer les étapes décrites dans cet article.

- Lorsque vous créez un compte d’utilisateur et attribuez à l’utilisateur une licence Exchange Online, une boîte aux lettres est automatiquement créée pour l’utilisateur. Lorsque la boîte aux lettres est créée, une stratégie de rétention par défaut, nommée Stratégie MRM par défaut, lui est automatiquement affectée. Dans cet article, vous allez créer une stratégie de rétention MRM, puis l’affecter aux boîtes aux lettres utilisateur, en remplaçant la stratégie MRM par défaut. Une boîte aux lettres ne peut avoir qu’une seule stratégie de rétention MRM à la fois.

- Pour en savoir plus sur les balises de rétention et les stratégies de rétention MRM dans Exchange Online, consultez [Balises de rétention et stratégies de rétention](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

## <a name="step-1-enable-archive-mailboxes-for-users"></a>Étape 1 : Activer les boîtes aux lettres d’archivage pour les utilisateurs

La première étape consiste à vérifier que chaque utilisateur de votre organisation dispose d’une boîte aux lettres d’archivage. La boîte aux lettres d’archivage d’un utilisateur doit être activée afin qu’une balise de rétention avec une action de rétention « Déplacer vers l’archive » puisse déplacer l’élément après l’expiration de l’âge de rétention.

Pour obtenir des instructions sur l’activation des boîtes aux lettres [d’archivage, consultez Activer les boîtes aux lettres d’archivage dans le portail de conformité Microsoft Purview](enable-archive-mailboxes.md).
  
> [!NOTE]
> Vous pouvez activer les boîtes aux lettres d’archivage à tout moment pendant ce processus, à condition qu’elles soient activées à un moment donné avant de terminer le processus. Si une boîte aux lettres d’archivage n’est pas activée, aucune action n’est effectuée sur les éléments auxquels une stratégie d’archivage ou de suppression lui est affectée.

## <a name="step-2-create-new-retention-tags-for-the-archive-and-deletion-policies"></a>Étape 2 : Créer de nouvelles balises de rétention pour les stratégies d’archivage et de suppression

Dans cette étape, vous allez créer les trois balises de rétention personnalisées qui ont été décrites précédemment.
  
- Alpine House 3 Year Move to Archive (stratégie d’archive personnalisée)

- Alpine House 7 Year Permanently Delete (stratégie de suppression personnalisée)

- Alpine House Deleted Items 5 Years Delete and Allow Recovery (étiquette personnalisée pour le dossier Éléments supprimés)

Pour créer de nouvelles balises de rétention, vous allez utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange dans</a> votre organisation Exchange Online. Veillez à utiliser la version classique de l’EAC.
  
1. Accédez à [https://admin.protection.outlook.com/ecp/](https://admin.protection.outlook.com/ecp/) et connectez-vous à l’aide de vos informations d’identification.
  
2. Dans le CAE, accédez aux **balises de rétention** de **la gestion de la conformité** > 

    Une liste des balises de rétention de votre organisation s’affiche.

### <a name="create-a-custom-archive-default-policy-tag"></a>Créer une balise de stratégie d’archive personnalisée par défaut
  
Tout d’abord, vous allez créer une balise de stratégie par défaut (DPT) d’archivage personnalisée qui déplacera les éléments vers la boîte aux lettres d’archivage après 3 ans.
  
1. Dans la page **Étiquettes de rétention**, sélectionnez **Nouvelle étiquette**![Nouvelle icône](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif), puis sélectionnez **Appliqué automatiquement à la boîte aux lettres entière (par défaut).**

2. Dans la **nouvelle balise appliquée automatiquement à la page de boîte aux lettres entière (par défaut),** renseignez les champs suivants : 

    ![Paramètres pour créer une balise de stratégie d’archive par défaut.](../media/41c0a43c-9c72-44e0-8947-da0831896432.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Action de rétention** Sélectionnez **Déplacer vers l’archive** pour déplacer des éléments vers la boîte aux lettres d’archivage à l’expiration de la période de rétention.

   3. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Pour ce scénario, les éléments seront déplacés vers la boîte aux lettres d’archivage après 1 095 jours (3 ans).

   4. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée.

3. Sélectionnez **Enregistrer** pour créer le DPT d’archive personnalisé.

    Le nouveau DPT d’archive s’affiche dans la liste des balises de rétention.

### <a name="create-a-custom-deletion-default-policy-tag"></a>Créer une balise de stratégie par défaut de suppression personnalisée
  
Ensuite, vous allez créer un autre DPT personnalisé, mais celui-ci sera une stratégie de suppression qui supprime définitivement les éléments après 7 ans.
  
1. Dans la page **Étiquettes de rétention**, sélectionnez **Nouvelle étiquette**![Nouvelle icône](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif), puis sélectionnez **Appliqué automatiquement à la boîte aux lettres entière (par défaut).**

2. Dans la **nouvelle balise appliquée automatiquement à la page de boîte aux lettres entière (par défaut),** renseignez les champs suivants : 

    ![Paramètres créer une balise de stratégie par défaut de suppression.](../media/f1f0ff62-eec9-4824-8e7c-d93dcfb09a79.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Action de rétention** Sélectionnez **Supprimer définitivement** pour vider les éléments de la boîte aux lettres à l’expiration de la période de rétention.

   3. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Pour ce scénario, les éléments seront purgés après 2555 jours (7 ans).

   4. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée. 

3. Sélectionnez **Enregistrer** pour créer le DPT de suppression personnalisé. 

    Le nouveau DPT de suppression s’affiche dans la liste des balises de rétention.

### <a name="create-a-custom-retention-policy-tag-for-the-deleted-items-folder"></a>Créer une balise de stratégie de rétention personnalisée pour le dossier Éléments supprimés
  
La dernière balise de rétention à créer est une balise de stratégie de rétention personnalisée (RPT) pour le dossier Éléments supprimés. Cette balise supprime les éléments du dossier Éléments supprimés après 5 ans et fournit une période de récupération pendant laquelle les utilisateurs peuvent utiliser l’outil Récupérer les éléments supprimés pour récupérer un élément.
  
1. Dans la page **Balises de rétention** , sélectionnez **Nouvelle étiquette** ![Nouvelle icône](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif), puis sélectionnez **Appliqué automatiquement à un dossier par défaut**.

2. Dans la **nouvelle balise appliquée automatiquement à une page de dossiers par défaut** , renseignez les champs suivants :

    ![Paramètres créer une balise de stratégie de rétention pour le dossier Éléments supprimés.](../media/6f3104bd-5edb-48ac-884d-5fe13d81dd1d.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Appliquer cette balise au dossier par défaut suivant** Dans la liste déroulante, sélectionnez **Éléments supprimés**.

   3. **Action de rétention** Sélectionnez **Supprimer et Autoriser la récupération** pour supprimer des éléments à l’expiration de la période de rétention, mais autorisez les utilisateurs à récupérer un élément supprimé dans la période de rétention des éléments supprimés (qui est par défaut de 14 jours).

   4. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Pour ce scénario, les éléments seront supprimés après 1825 jours (5 ans).

   5. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée. 

3. Sélectionnez **Enregistrer** pour créer le RPT personnalisé pour le dossier Éléments supprimés.

    Le nouveau RPT s’affiche dans la liste des balises de rétention.

## <a name="step-3-create-a-new-retention-policy"></a>Étape 3 : Créer une stratégie de rétention

Après avoir créé les balises de rétention personnalisées, l’étape suivante consiste à créer une stratégie de rétention et à ajouter les balises de rétention. Vous allez ajouter les trois balises de rétention personnalisées que vous avez créées à l’étape 2 et les balises intégrées mentionnées dans la première section. À l’étape 4, vous allez affecter cette nouvelle stratégie de rétention aux boîtes aux lettres utilisateur.
  
1. Dans le CAE, accédez aux **stratégies de rétention** **de la gestion de la conformité** > .

2. Dans la page **Stratégies de rétention**, sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif)

3. Dans la zone **Nom** , tapez un nom pour la nouvelle stratégie de rétention ; par exemple, **alpine House Archive and De suppression Policy**.

4. Sous **Balises de rétention**, sélectionnez **Ajouter** ![une nouvelle icône.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif)

    Une liste des balises de rétention dans votre organisation s’affiche. Notez que les balises personnalisées que vous avez créées à l’étape 2 sont affichées.

5. Ajoutez les 9 balises de rétention mises en surbrillance dans la capture d’écran suivante (ces balises sont décrites plus en détail dans la section [Plus d’informations](#more-information) ). Pour ajouter une balise de rétention, sélectionnez-la, puis **sélectionnez Ajouter**.

    ![Ajoutez des balises de rétention à la nouvelle stratégie de rétention.](../media/d8e87176-0716-4238-9e6a-7c4af35541dc.png)
  
    > [!TIP]
    > Vous pouvez sélectionner plusieurs balises de rétention en maintenant la touche **Ctrl** enfoncée, puis en cliquant sur chaque balise. 
  
6. Une fois que vous avez ajouté les balises de rétention, sélectionnez **OK**.

7. Dans la page **Nouvelle stratégie de rétention** , **sélectionnez Enregistrer** pour créer la nouvelle stratégie.

    La nouvelle stratégie de rétention s’affiche dans la liste. Sélectionnez-la pour afficher les balises de rétention qui lui sont liées dans le volet d’informations.

    ![Nouvelle stratégie de rétention et liste de balises de rétention liées.](../media/63bc45e6-110b-4dc9-a85f-8eb1961a8258.png)
  
## <a name="step-4-assign-the-new-retention-policy-to-user-mailboxes"></a>Étape 4 : Affecter la nouvelle stratégie de rétention aux boîtes aux lettres utilisateur

Lorsqu’une boîte aux lettres est créée, une stratégie de rétention nommée stratégie MRM par défaut lui est affectée par défaut. Dans cette étape, vous allez remplacer cette stratégie de rétention en affectant la nouvelle stratégie de rétention que vous avez créée à l’étape 3 aux boîtes aux lettres utilisateur de votre organisation. Un remplacement est nécessaire, car une boîte aux lettres ne peut avoir qu’une seule stratégie de rétention MRM à la fois. Cette étape suppose que vous allez affecter la nouvelle stratégie à toutes les boîtes aux lettres de votre organisation.
  
1. Dans le CAE, accédez aux **boîtes aux lettres** **des destinataires** > .

    Une liste de toutes les boîtes aux lettres utilisateur de votre organisation s’affiche.

2. Sélectionnez toutes les boîtes aux lettres en cliquant sur la première de la liste, en maintenant la touche **Maj** enfoncée, puis en cliquant sur la dernière dans la liste. 

3. Dans le volet d’informations du CAE, sous **Modifier en bloc**, sélectionnez **Autres options**.

4. Sous **Stratégie de rétention**, sélectionnez **Mettre à jour**.

5. Dans la page **d’affectation en bloc** de la stratégie de rétention, dans la liste déroulante **Sélectionner la** stratégie de rétention, sélectionnez la stratégie de rétention que vous avez créée à l’étape 3 ; par exemple, **alpine House Archive and Retention Policy**.

6. Sélectionnez **Enregistrer** pour enregistrer la nouvelle affectation de stratégie de rétention.

7. Pour vérifier que la nouvelle stratégie de rétention a été affectée aux boîtes aux lettres :

   1. Sélectionnez une boîte aux lettres dans la page **Boîtes aux lettres**, puis **sélectionnez Modifier**![](../media/d7dc7e5f-17a1-4eb9-b42d-487db59e2e21.png).

   2. Dans la page des propriétés de boîte aux lettres de l’utilisateur sélectionné, sélectionnez **Fonctionnalités de boîte aux lettres**.

   Le nom de la nouvelle stratégie affectée à la boîte aux lettres s’affiche dans la liste déroulante **stratégie de rétention** .

## <a name="optional-step-5-run-the-managed-folder-assistant-to-apply-the-new-settings"></a>(Facultatif) Étape 5 : Exécuter l’Assistant Dossier géré pour appliquer les nouveaux paramètres

Une fois que vous avez appliqué la nouvelle stratégie de rétention aux boîtes aux lettres à l’étape 4, l’application des nouveaux paramètres de rétention aux boîtes aux lettres peut prendre jusqu’à 7 jours dans Exchange Online. Cela est dû au fait qu’un processus appelé *Assistant Dossier géré* traite les boîtes aux lettres au moins une fois tous les 7 jours. Au lieu d’attendre l’exécution de l’Assistant Dossiers managés, vous pouvez forcer cette opération en exécutant l’applet de commande **Start-ManagedFolderAssistant** dans Exchange Online PowerShell.

 **Que se passe-t-il lorsque vous exécutez l’Assistant Dossier géré ?** Il applique les paramètres de la stratégie de rétention en inspectant les éléments de la boîte aux lettres et en déterminant s’ils sont soumis à rétention. Il marque ensuite les éléments soumis à la rétention avec la balise de rétention appropriée, puis prend l’action de rétention spécifiée sur les éléments qui ont dépassé leur âge de rétention.
  
Voici les étapes à suivre pour vous connecter à Exchange Online PowerShell, puis exécuter l’Assistant Dossiers managés sur chaque boîte aux lettres de votre organisation.

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Exécutez les deux commandes suivantes pour démarrer l’Assistant Dossier géré pour toutes les boîtes aux lettres utilisateur de votre organisation.

    ```powershell
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    ```

    ```powershell
    $Mailboxes.Identity | Start-ManagedFolderAssistant
    ```

Voilà ! Vous avez configuré une stratégie d’archivage et de suppression pour l’organisation Alpine House.

### <a name="more-information-about-the-managed-folder-assistant"></a>Plus d’informations sur l’Assistant Dossier géré

Comme indiqué précédemment, l’Assistant Dossiers managés traite les boîtes aux lettres au moins une fois tous les 7 jours. Il est donc possible qu’une boîte aux lettres puisse être traitée plus fréquemment par l’Assistant Dossier géré. En outre, les administrateurs ne peuvent pas prédire la prochaine fois qu’une boîte aux lettres est traitée par l’Assistant Dossier géré, ce qui est l’une des raisons pour lesquelles vous souhaiterez peut-être l’exécuter manuellement. 

Toutefois, si vous souhaitez empêcher temporairement l’Assistant Dossier géré d’appliquer les nouveaux paramètres de rétention à une boîte aux lettres, vous pouvez exécuter la `Set-Mailbox -ElcProcessingDisabled $true` commande pour désactiver temporairement l’Assistant Dossier géré du traitement d’une boîte aux lettres. 

Pour réactiver l’Assistant Dossier géré pour une boîte aux lettres, exécutez la `Set-Mailbox -ElcProcessingDisabled $false` commande. 

Enfin, si un utilisateur de boîte aux lettres a un compte désactivé, les éléments ne sont pas déplacés vers la boîte aux lettres d’archivage de cette boîte aux lettres.
  
## <a name="optional-step-6-make-the-new-retention-policy-the-default-for-your-organization"></a>(Facultatif) Étape 6 : faire de la nouvelle stratégie de rétention la stratégie par défaut pour votre organisation

À l’étape 4, vous devez affecter la nouvelle stratégie de rétention aux boîtes aux lettres existantes. Toutefois, vous pouvez configurer Exchange Online afin que la nouvelle stratégie de rétention soit affectée aux nouvelles boîtes aux lettres créées à l’avenir. 

Pour ce faire, utilisez Exchange Online PowerShell pour mettre à jour le plan de boîte aux lettres par défaut de votre organisation. Un *plan de boîte aux lettres* est un modèle qui configure automatiquement les propriétés sur les nouvelles boîtes aux lettres.  Dans cette étape facultative, vous pouvez remplacer la stratégie de rétention actuelle affectée au plan de boîte aux lettres (par défaut, la stratégie MRM par défaut) par la stratégie de rétention MRM que vous avez créée à l’étape 3. Après avoir mis à jour le plan de boîte aux lettres, la nouvelle stratégie de rétention MRM est affectée aux nouvelles boîtes aux lettres.

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande suivante pour afficher des informations sur les plans de boîte aux lettres de votre organisation.

    ```powershell
    Get-MailboxPlan | Format-Table DisplayName,RetentionPolicy,IsDefault
    ```
    
    Notez le plan de boîte aux lettres défini comme valeur par défaut.

3. Exécutez la commande suivante pour affecter la nouvelle stratégie de rétention MRM que vous avez créée à l’étape 3 (par exemple, **Alpine House Archive and Retention Policy**) au plan de boîte aux lettres par défaut. Cet exemple suppose que le nom du plan de boîte aux lettres par défaut est **ExchangeOnlineEnterprise**.
    
    ```powershell
    Set-MailboxPlan "ExchangeOnlineEnterprise" -RetentionPolicy "Alpine House Archive and Retention Policy"
    ```

4. Vous pouvez réexécuter la commande à l’étape 2 pour vérifier que la stratégie de rétention MRM affectée au plan de boîte aux lettres par défaut a été modifiée.

## <a name="more-information"></a>Plus d’informations

- L’âge de rétention des éléments de boîte aux lettres est calculé à partir de la date de remise. Ou à partir de la date de création des éléments tels que les brouillons de messages qui ne sont pas envoyés mais qui sont créés par l’utilisateur. Quand l'Assistant Dossier géré traite les éléments d'une boîte aux lettres, il appose une date de début et une date d'expiration pour tous les éléments présentant des balises de rétention avec l'action de rétention Supprimer et autoriser la récupération ou Supprimer définitivement. Les éléments qui ont une balise d’archive sont marqués avec une date de déplacement.

- Le tableau suivant fournit plus d’informations sur chaque balise de rétention pour la stratégie de rétention MRM personnalisée dans cet article.

    | Balise de rétention | Ce que fait cette balise | Intégré ou personnalisé ? | Type |
    |:-----|:-----|:-----|:-----|
    |Alpine House 3 Year Move to Archive  <br/> |Déplace les éléments âgés de 1 095 jours (3 ans) vers la boîte aux lettres d’archivage.  <br/> |Personnalisé (Voir [l’étape 2 : Créer de nouvelles balises de rétention pour les stratégies d’archivage et de suppression](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Balise de stratégie par défaut (archive) ; cette balise est automatiquement appliquée à l’ensemble de la boîte aux lettres.  <br/> |
    |Alpine House 7 Year Permanently Delete  <br/> |Supprime définitivement les éléments de la boîte aux lettres primaire ou de la boîte aux lettres d’archivage lorsqu’ils ont 7 ans.  <br/> |Personnalisé (Voir [l’étape 2 : Créer de nouvelles balises de rétention pour les stratégies d’archivage et de suppression](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Balise de stratégie par défaut (suppression) ; cette balise est automatiquement appliquée à l’ensemble de la boîte aux lettres.  <br/> |
    |Alpine House Deleted Items 5 Years Delete and Allow Recovery  <br/> |Supprime des éléments du dossier Éléments supprimés âgés de 5 ans. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Personnalisé (Voir [l’étape 2 : Créer de nouvelles balises de rétention pour les stratégies d’archivage et de suppression](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Balise de stratégie de rétention (éléments supprimés) ; cette balise est automatiquement appliquée aux éléments du dossier Éléments supprimés.  <br/> |
    |Éléments récupérables 14 jours Passer à l’archive  <br/> |Déplace les éléments qui se sont retrouvés dans le dossier Éléments récupérables pendant 14 jours vers le dossier Éléments récupérables dans la boîte aux lettres d’archivage.  <br/> |Intégré  <br/> |Balise de stratégie de rétention (éléments récupérables) ; cette balise est automatiquement appliquée aux éléments du dossier Éléments récupérables.  <br/> |
    |Courrier indésirable  <br/> |Supprime définitivement les éléments qui ont été dans le dossier Courrier indésirable pendant 30 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Balise de stratégie de rétention (courrier indésirable) ; cette balise est automatiquement appliquée aux éléments du dossier Courrier indésirable.  <br/> |
    |Suppression après 1 mois  <br/> |Supprime définitivement les éléments qui datent de 30 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Personnel; cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Suppression après 1 an  <br/> |Supprime définitivement les éléments qui datent de 365 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Personnel; cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Ne jamais supprimer  <br/> |Cette balise empêche la suppression d’éléments par une stratégie de rétention.  <br/> |Intégré  <br/> |Personnel; cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Déplacement vers l’archive après 1 ans - Personnel  <br/> |Déplace les éléments vers la boîte aux lettres d’archivage après 1 an.  <br/> |Intégré  <br/> |Personnel; cette balise peut être appliquée par les utilisateurs.  <br/> |

    > <sup>\*</sup>Les utilisateurs peuvent utiliser l’outil Récupérer les éléments supprimés dans Outlook et Outlook sur le web (anciennement Outlook Web App) pour récupérer un élément supprimé au cours de la période de rétention des éléments supprimés, qui est par défaut de 14 jours dans Exchange Online. Un administrateur peut utiliser Exchange Online PowerShell pour augmenter la période de rétention des éléments supprimés à un maximum de 30 jours. Pour plus d’informations, consultez : [Récupérer les éléments supprimés dans Outlook pour Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce) et [modifier la période de rétention des éléments supprimés pour une boîte aux lettres dans Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).
  
- L’utilisation de la balise de rétention **Déplacer vers archive des éléments récupérables 14 jours** permet de libérer de l’espace de stockage dans le dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur. Cela est utile lorsque la boîte aux lettres d’un utilisateur est mise en attente, ce qui signifie que rien n’est supprimé définitivement de la boîte aux lettres de l’utilisateur. Sans déplacer des éléments vers la boîte aux lettres d’archivage, il est possible que le quota de stockage pour le dossier Éléments récupérables dans la boîte aux lettres primaire soit atteint. Pour plus d’informations à ce sujet et sur la façon de l’éviter, consultez [Augmenter le quota d’éléments récupérables pour les boîtes aux lettres en attente](./increase-the-recoverable-quota-for-mailboxes-on-hold.md).
