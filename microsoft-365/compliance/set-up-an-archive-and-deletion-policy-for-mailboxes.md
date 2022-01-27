---
title: Personnaliser une stratégie d’archivage et de suppression (MRM) pour les boîtes aux lettres de votre organisation
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
description: Comment créer une stratégie personnalisée d’archivage et de suppression de gestion des enregistrements de messagerie (MRM) pour déplacer automatiquement des éléments vers la boîte aux lettres d’archivage d’un utilisateur.
ms.openlocfilehash: 192bed6be6c3129410f4e51144402c6c19e12d37
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62242070"
---
# <a name="customize-an-archive-and-deletion-policy-for-mailboxes-in-your-organization"></a>Personnaliser une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre organisation

Microsoft 365 de conformité peuvent créer une stratégie d’archivage et de suppression qui déplace automatiquement des éléments vers la boîte aux lettres [d’archivage](archive-mailboxes.md) d’un utilisateur et supprime automatiquement des éléments de la boîte aux lettres.

Pour ce faire, créez une stratégie de rétention MRM (Messaging Records Management) affectée aux boîtes aux lettres et déplacez les éléments vers la boîte aux lettres d’archivage d’un utilisateur après un certain laps de temps et supprimez également les éléments de la boîte aux lettres une fois qu’ils ont atteint une certaine limite d’âge. 

Les règles réelles qui déterminent quels éléments sont déplacés ou supprimés et quand cela se produit sont appelées balises de rétention. Les balises de rétention sont liées à une stratégie de rétention MRM, qui est à son tour attribuée à la boîte aux lettres d’un utilisateur. Une balise de rétention applique des paramètres de rétention à des messages et dossiers individuels dans la boîte aux lettres d’un utilisateur. Il définit la durée de conservation d’un message dans la boîte aux lettres et l’action à prendre lorsque le message atteint l’âge de rétention spécifié. Lorsqu’un message atteint son âge de rétention, il est déplacé vers la boîte aux lettres d’archivage de l’utilisateur ou supprimé.
  
Les étapes de cet article définissent une stratégie d’archivage et de rétention pour une organisation fictive nommée House House. La configuration de cette stratégie inclut les tâches suivantes :
  
- Activation d’une boîte aux lettres d’archivage pour chaque utilisateur de l’organisation. Cela permet aux utilisateurs de stocker davantage de boîtes aux lettres et est nécessaire pour qu’une stratégie de rétention puisse déplacer des éléments vers la boîte aux lettres d’archivage. Il permet également à un utilisateur de stocker des informations d’archivage en déplaçant des éléments vers sa boîte aux lettres d’archivage.

- Création de trois balises de rétention personnalisées qui font les étapes suivantes :

  - Déplace automatiquement les éléments de 3 ans vers la boîte aux lettres d’archivage de l’utilisateur. Le déplacement d’éléments vers la boîte aux lettres d’archivage libère de l’espace dans la boîte aux lettres principale d’un utilisateur.

  - Supprime automatiquement les éléments qui ont 5 ans du dossier Éléments supprimés. Cela libère également de l’espace dans la boîte aux lettres principale de l’utilisateur. L’utilisateur aura la possibilité de récupérer ces éléments si nécessaire. Pour plus d’informations, voir la note de bas de page dans la [section](#more-information) Plus d’informations. 

  - Supprime automatiquement (et définitivement) les éléments qui ont 7 ans de la boîte aux lettres principale et d’archivage. En raison des réglementations de conformité, certaines organisations sont tenues de conserver le courrier électronique pendant une certaine période. Une fois cette période expirée, une organisation peut vouloir supprimer définitivement ces éléments des boîtes aux lettres utilisateur.

- Création d’une stratégie de rétention et ajout de balises de rétention personnalisées à celui-ci. En outre, vous allez également ajouter des balises de rétention intégrées à la nouvelle stratégie de rétention. Cela inclut les balises personnelles que les utilisateurs peuvent affecter à des éléments dans leur boîte aux lettres. Vous allez également ajouter une balise de rétention qui déplace les éléments du dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur vers le dossier Éléments récupérables de sa boîte aux lettres d’archivage. Cela permet de libérer de l’espace dans le dossier Éléments récupérables d’un utilisateur lorsque sa boîte aux lettres est placée en attente.

Vous pouvez suivre une partie ou l’ensemble des étapes de cet article pour configurer une stratégie d’archivage et de suppression pour les boîtes aux lettres de votre propre organisation. Nous vous recommandons de tester ce processus sur quelques boîtes aux lettres avant de l’implémenter sur toutes les boîtes aux lettres de votre organisation.
  
## <a name="before-you-set-up-an-archive-and-deletion-policy"></a>Avant de configurer une stratégie d’archivage et de suppression

- Vous devez être un administrateur général de votre organisation pour effectuer les étapes de cette rubrique. 

- Lorsque vous créez un compte d’utilisateur et attribuez à l’utilisateur une licence Exchange Online, une boîte aux lettres est automatiquement créée pour l’utilisateur. Une fois la boîte aux lettres créée, une stratégie de rétention par défaut nommée Stratégie MRM par défaut lui est automatiquement attribuée. Dans cet article, vous allez créer une stratégie de rétention, puis l’affecter aux boîtes aux lettres des utilisateurs, en remplaçant la stratégie MRM par défaut. Une boîte aux lettres ne peut être affectée qu’à une seule stratégie de rétention à la fois.

- Pour en savoir plus sur les balises de rétention et les stratégies de rétention dans Exchange Online, voir [Balises de rétention et stratégies de rétention.](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)

## <a name="step-1-enable-archive-mailboxes-for-users"></a>Étape 1 : Activer les boîtes aux lettres d’archivage pour les utilisateurs

La première étape consiste à activer la boîte aux lettres d’archivage pour chaque utilisateur de votre organisation. La boîte aux lettres d’archivage d’un utilisateur doit être activée afin qu’une balise de rétention avec une action de rétention « Déplacer vers l’archive » puisse déplacer l’élément après l’expiration de l’âge de rétention.
  
> [!NOTE]
> Vous pouvez activer les boîtes aux lettres d’archivage à tout moment au cours de ce processus, tant qu’elles sont activées à un moment donné avant de terminer le processus. Si une boîte aux lettres d’archivage n’est pas activée, aucune action n’est prise sur les éléments qui ont une stratégie d’archivage ou de suppression qui lui est affectée.
  
1. Accédez à <https://compliance.microsoft.com>.

2. Connectez-vous à l’aide de votre compte d’administrateur général.
    
3. Dans la Centre de conformité Microsoft 365, cliquez sur **Gouvernance** des informations, puis cliquez sur **l’onglet** Archive.

    Une liste des boîtes aux lettres de votre organisation s’affiche et si la boîte aux lettres d’archivage correspondante est activée ou désactivée.

4. Sélectionnez toutes les boîtes aux lettres en cliquant sur  la première de la liste, en maintenant la touche Shift plus bas, puis en cliquant sur la dernière de la liste.

    > [!TIP]
    > Cette étape suppose qu’aucune boîte aux lettres d’archivage n’est activée. Si l’archivage est activé pour des boîtes aux lettres, maintenez la touche **Ctrl** en main, puis cliquez sur chaque boîte aux lettres dont la boîte aux lettres d’archivage est désactivée. Vous pouvez également  cliquer sur l’en-tête de colonne boîte aux lettres d’archivage pour trier les lignes selon que la boîte aux lettres d’archivage est activée ou désactivée pour faciliter la sélection des boîtes aux lettres.
  
5. Dans le volet d’informations, sous **Modification en** bloc, cliquez sur **Activer.**

    Un avertissement s’affiche et vous avertit que les éléments de plus de deux ans seront déplacés vers la nouvelle boîte aux lettres d’archivage. Cela est dû au fait que la stratégie de rétention par défaut affectée à une nouvelle boîte aux lettres utilisateur lors de sa création possède une balise de stratégie par défaut d’archivage dont l’âge de rétention est de 2 ans. La balise de stratégie d’archivage par défaut personnalisée que vous allez créer à l’étape 2 a un âge de rétention de 3 ans. Cela signifie que les éléments de 3 ans ou plus sont déplacés vers la boîte aux lettres d’archivage.

6. Cliquez **sur Oui** pour fermer le message d’avertissement et démarrer le processus d’activer la boîte aux lettres d’archivage pour chaque boîte aux lettres sélectionnée.

7. Lorsque le processus est terminé, cliquez sur **Actualiser.** ![](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) pour mettre à jour la liste sur la page **Archive.**

    La boîte aux lettres d’archivage est activée pour tous les utilisateurs de votre organisation.

    ![Liste des boîtes aux lettres dont la boîte aux lettres d’archivage est activée.](../media/61a7cb97-1bed-4808-aa5f-b6b761cfa8de.png)

## <a name="step-2-create-new-retention-tags-for-the-archive-and-deletion-policies"></a>Étape 2 : Créer des balises de rétention pour les stratégies d’archivage et de suppression

Dans cette étape, vous allez créer les trois balises de rétention personnalisées qui ont été décrites précédemment.
  
- Move to Archive (custom archive policy) de House 3 Year Move to Archive (custom archive policy)

- Suppression définitive de House 7 Year (stratégie de suppression personnalisée)

- Supprimer et autoriser la récupération des éléments supprimés de House House 5 ans (balise personnalisée pour le dossier Éléments supprimés)

Pour créer de nouvelles balises de rétention, vous utiliserez le Centre d’administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange dans</a> votre organisation Exchange Online rétention. N’oubliez pas d’utiliser la version classique du EAC.
  
1. Connectez-vous [https://admin.protection.outlook.com/ecp/](https://admin.protection.outlook.com/ecp/) à l’aide de vos informations d’identification.
  
2. Dans le CCE, allez aux balises de rétention **de gestion** de  >  **la conformité**

    Une liste des balises de rétention de votre organisation s’affiche.

### <a name="create-a-custom-archive-default-policy-tag"></a>Créer une balise de stratégie d’archivage par défaut personnalisée
  
Tout d’abord, vous allez créer une balise de stratégie d’archivage par défaut personnalisée qui déplacera les éléments vers la boîte aux lettres d’archivage après 3 ans.
  
1. Dans la page **Balises de** rétention, cliquez sur **Icône** Nouvelle balise, puis sélectionnez Appliqué automatiquement à la boîte aux lettres entière ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) **(par défaut).**

2. Dans la balise Nouveau appliquée automatiquement à l’intégralité de la boîte aux lettres **(par défaut),** complétez les champs suivants : 

    ![Paramètres créer une balise de stratégie par défaut d’archivage.](../media/41c0a43c-9c72-44e0-8947-da0831896432.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Action de rétention** Sélectionnez **Déplacer vers l’archive** pour déplacer des éléments vers la boîte aux lettres d’archivage à l’expiration de la période de rétention.

   3. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Dans ce scénario, les éléments sont déplacés vers la boîte aux lettres d’archivage après 1 095 jours (3 ans).

   4. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée.

3. Cliquez **sur Enregistrer** pour créer la DPT d’archivage personnalisée.

    La nouvelle balise de stratégie par balise de stratégie d’archivage s’affiche dans la liste des balises de rétention.

### <a name="create-a-custom-deletion-default-policy-tag"></a>Créer une balise de stratégie par défaut de suppression personnalisée
  
Ensuite, vous allez créer une autre DPT personnalisée, mais celle-ci sera une stratégie de suppression qui supprime définitivement les éléments au bout de 7 ans.
  
1. Dans la page **Balises de** rétention, cliquez sur **Icône** Nouvelle balise, puis sélectionnez Appliqué automatiquement à la boîte aux lettres entière ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) **(par défaut).**

2. Dans la balise Nouveau appliquée automatiquement à l’intégralité de la boîte aux lettres **(par défaut),** complétez les champs suivants : 

    ![Paramètres créer une balise de stratégie par défaut de suppression.](../media/f1f0ff62-eec9-4824-8e7c-d93dcfb09a79.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Action de rétention** Sélectionnez **Supprimer définitivement pour** vider les éléments de la boîte aux lettres à l’expiration de la période de rétention.

   3. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Dans ce scénario, les éléments seront purgés au bout de 2555 jours (7 ans).

   4. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée. 

3. Cliquez **sur Enregistrer** pour créer la DPT de suppression personnalisée. 

    La nouvelle balise de stratégie par stratégie de rétention de suppression s’affiche dans la liste des balises de rétention.

### <a name="create-a-custom-retention-policy-tag-for-the-deleted-items-folder"></a>Créer une balise de stratégie de rétention personnalisée pour le dossier Éléments supprimés
  
La dernière balise de rétention que vous allez créer est une balise de stratégie de rétention personnalisée (RPT) pour le dossier Éléments supprimés. Cette balise supprime les éléments du dossier Éléments supprimés au bout de 5 ans et fournit une période de récupération lorsque les utilisateurs peuvent utiliser l’outil Récupérer les éléments supprimés pour récupérer un élément.
  
1. Dans la page **Balises de** rétention, cliquez sur **Icône** Nouvelle balise, puis sélectionnez Appliqué automatiquement ![ à un dossier par ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) **défaut.**

2. Dans la balise Nouveau appliquée automatiquement à une page **de dossiers** par défaut, complétez les champs suivants :

    ![Paramètres créer une balise de stratégie de rétention pour le dossier Éléments supprimés.](../media/6f3104bd-5edb-48ac-884d-5fe13d81dd1d.png)
  
   1. **Nom** Tapez un nom pour la nouvelle balise de rétention. 

   2. **Appliquer cette balise au dossier par défaut suivant** Dans la liste de listes, sélectionnez **Éléments supprimés.**

   3. **Action de rétention** **Sélectionnez** Supprimer et autoriser la récupération pour supprimer des éléments à l’expiration de la période de rétention, mais autorisez les utilisateurs à récupérer un élément supprimé au cours de la période de rétention des éléments supprimés (qui est de 14 jours par défaut).

   4. **Période de rétention** Sélectionnez **Lorsque l’élément atteint l’âge suivant (en jours),** puis entrez la durée de la période de rétention. Dans ce scénario, les éléments seront supprimés au bout de 1 825 jours (5 ans).

   5. **Commentaire** (facultatif) Tapez un commentaire qui explique l’objectif de la balise de rétention personnalisée. 

3. Cliquez **sur Enregistrer** pour créer la rpt personnalisée pour le dossier Éléments supprimés.

    La nouvelle balise de stratégie de rétention s’affiche dans la liste des balises de rétention.

## <a name="step-3-create-a-new-retention-policy"></a>Étape 3 : Créer une stratégie de rétention

Après avoir créé les balises de rétention personnalisées, l’étape suivante consiste à créer une stratégie de rétention et à ajouter les balises de rétention. Vous allez ajouter les trois balises de rétention personnalisées que vous avez créées à l’étape 2 et les balises intégrées mentionnées dans la première section. À l’étape 4, vous allez affecter cette nouvelle stratégie de rétention aux boîtes aux lettres des utilisateurs.
  
1. Dans le EAC, allez aux **stratégies de rétention de gestion** de la  >  **conformité.**

2. Dans la page **Stratégies de** rétention, cliquez **sur Nouvelle** ![ icône. ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif)

3. Dans la **zone Nom,** tapez un nom pour la nouvelle stratégie de rétention . par exemple, **archive house et stratégie de suppression Deletion**.

4. Sous **Balises de rétention,** cliquez **sur Ajouter** une nouvelle ![ icône. ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif)

    Une liste des balises de rétention de votre organisation s’affiche. Notez que les balises personnalisées que vous avez créées à l’étape 2 sont affichées.

5. Ajoutez les 9 balises de rétention mises en évidence dans la capture d’écran suivante (ces balises sont décrites plus en détail dans la section [Plus d’informations).](#more-information) Pour ajouter une balise de rétention, sélectionnez-la, puis cliquez sur **Ajouter.**

    ![Ajoutez des balises de rétention à la nouvelle stratégie de rétention.](../media/d8e87176-0716-4238-9e6a-7c4af35541dc.png)
  
    > [!TIP]
    > Vous pouvez sélectionner plusieurs balises de rétention en maintenant la **touche Ctrl** plus bas, puis en cliquant sur chaque balise. 
  
6. Une fois que vous avez ajouté les balises de rétention, cliquez sur **OK**.

7. Dans la page **Nouvelle stratégie de rétention,** cliquez sur **Enregistrer** pour créer la nouvelle stratégie.

    La nouvelle stratégie de rétention s’affiche dans la liste. Sélectionnez-le pour afficher les balises de rétention qui lui sont liées dans le volet d’informations.

    ![La nouvelle stratégie de rétention et la liste des balises de rétention liées.](../media/63bc45e6-110b-4dc9-a85f-8eb1961a8258.png)
  
## <a name="step-4-assign-the-new-retention-policy-to-user-mailboxes"></a>Étape 4 : Attribuer la nouvelle stratégie de rétention aux boîtes aux lettres des utilisateurs

Lorsqu’une nouvelle boîte aux lettres est créée, une stratégie de rétention nommée Stratégie MRM par défaut lui est affectée par défaut. Dans cette étape, vous allez remplacer cette stratégie de rétention (car une boîte aux lettres ne peut être affectée qu’à une seule stratégie de rétention) en attribuant la nouvelle stratégie de rétention que vous avez créée à l’étape 3 aux boîtes aux lettres utilisateur de votre organisation. Cette étape suppose que vous allez affecter la nouvelle stratégie à toutes les boîtes aux lettres de votre organisation.
  
1. Dans le EAC, allez à **Boîtes aux lettres** de  >  **destinataires.**

    La liste de toutes les boîtes aux lettres utilisateur de votre organisation s’affiche.

2. Sélectionnez toutes les boîtes aux lettres en cliquant sur  la première de la liste, en maintenant la touche Shift plus bas, puis en cliquant sur la dernière de la liste. 

3. Dans le volet d’informations sur le côté droit du EAC, sous **Modification** en bloc, cliquez sur **Plus d’options.**

4. Sous **Stratégie de rétention**, cliquez sur **Mettre à jour**.

5. Dans la page **Affecter en**  bloc une stratégie de rétention, dans la liste liste de listes listes de sélection de la stratégie de rétention, sélectionnez la stratégie de rétention que vous avez créée à l’étape 3 . par exemple, **Archive house de House Et stratégie de rétention**.

6. Cliquez **sur Enregistrer** pour enregistrer la nouvelle attribution de stratégie de rétention.

7. Pour vérifier que la nouvelle stratégie de rétention a été affectée aux boîtes aux lettres, vous pouvez :

   1. Sélectionnez une boîte aux lettres dans la page **Boîtes** aux lettres, puis cliquez **sur Modifier.** ![ ](../media/d7dc7e5f-17a1-4eb9-b42d-487db59e2e21.png)

   2. Dans la page des propriétés de boîte aux lettres de l’utilisateur sélectionné, cliquez sur **Fonctionnalités de boîte aux lettres.**

   Le nom de la nouvelle stratégie attribuée à  la boîte aux lettres s’affiche dans la liste de listes de rétention de la stratégie de rétention.

## <a name="optional-step-5-run-the-managed-folder-assistant-to-apply-the-new-settings"></a>(Facultatif) Étape 5 : Exécuter l’Assistant Dossier géré pour appliquer les nouveaux paramètres

Après avoir appliqué la nouvelle stratégie de rétention aux boîtes aux lettres à l’étape 4, l’application des nouveaux paramètres de rétention aux boîtes aux lettres peut prendre jusqu’à 7 jours en Exchange Online. Cela est dû au fait qu’un processus appelé *Assistant Dossier* géré traite les boîtes aux lettres au moins une fois tous les 7 jours. Au lieu d’attendre l’exécution de l’Assistant Dossier géré, vous pouvez forcer cette exécution en exécutant la cmdlet **Start-ManagedFolderAssistant** dans Exchange Online PowerShell.

 **Que se passe-t-il lorsque vous exécutez l’Assistant Dossier géré ?** Il applique les paramètres de la stratégie de rétention en inspectant les éléments de la boîte aux lettres et en déterminant s’ils sont soumis à la rétention. Il marque ensuite les éléments soumis à la rétention avec la balise de rétention appropriée, puis prend l’action de rétention spécifiée sur les éléments qui ont passé leur âge de rétention.
  
Voici les étapes à suivre pour vous connecter à Exchange Online PowerShell, puis exécuter l’Assistant Dossier géré sur chaque boîte aux lettres de votre organisation.

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Exécutez les deux commandes suivantes pour démarrer l’Assistant Dossier géré pour toutes les boîtes aux lettres utilisateur de votre organisation.

    ```powershell
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    ```

    ```powershell
    $Mailboxes.Identity | Start-ManagedFolderAssistant
    ```

Voilà ! Vous avez mis en place une stratégie d’archivage et de suppression pour l’organisation House House.

> [!NOTE]
> Comme indiqué précédemment, l’Assistant Dossier géré traite les boîtes aux lettres au moins une fois tous les 7 jours. Il est donc possible qu’une boîte aux lettres puisse être traitée plus fréquemment par l’Assistant Dossier géré. En outre, les administrateurs ne peuvent pas prévoir la prochaine fois qu’une boîte aux lettres est traitée par l’Assistant Dossier géré, ce qui est l’une des raisons pour lesquelles vous pouvez l’exécuter manuellement. Toutefois, si vous souhaitez empêcher temporairement l’Assistant Dossier géré d’appliquer les nouveaux paramètres de rétention à une boîte aux lettres, vous pouvez exécuter la commande pour désactiver temporairement l’Assistant Dossier géré du traitement d’une boîte aux `Set-Mailbox -ElcProcessingDisabled $true` lettres. Pour ré-activer l’Assistant Dossier géré pour une boîte aux lettres, exécutez la `Set-Mailbox -ElcProcessingDisabled $false` commande. Enfin, si un utilisateur de boîte aux lettres possède un compte désactivé, nous ne traiterons pas les éléments de déplacement pour archiver l’action pour cette boîte aux lettres.
  
## <a name="optional-step-6-make-the-new-retention-policy-the-default-for-your-organization"></a>(Facultatif) Étape 6 : faire de la nouvelle stratégie de rétention la stratégie par défaut pour votre organisation

À l’étape 4, vous devez affecter la nouvelle stratégie de rétention aux boîtes aux lettres existantes. Toutefois, vous pouvez configurer Exchange Online afin que la nouvelle stratégie de rétention soit affectée aux nouvelles boîtes aux lettres créées à l’avenir. Pour ce faire, utilisez Exchange Online PowerShell pour mettre à jour le plan de boîte aux lettres par défaut de votre organisation. Un *plan de boîte* aux lettres est un modèle qui configure automatiquement les propriétés des nouvelles boîtes aux lettres.  Dans cette étape facultative, vous pouvez remplacer la stratégie de rétention actuelle affectée au plan de boîte aux lettres (par défaut, la stratégie MRM par défaut) par la stratégie de rétention que vous avez créée à l’étape 3. Une fois que vous avez mis à jour le plan de boîte aux lettres, la nouvelle stratégie de rétention est affectée aux nouvelles boîtes aux lettres.

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande suivante pour afficher des informations sur les plans de boîte aux lettres de votre organisation.

    ```powershell
    Get-MailboxPlan | Format-Table DisplayName,RetentionPolicy,IsDefault
    ```

    Notez le plan de boîte aux lettres qui est définie comme plan par défaut.

3. Exécutez la commande suivante pour affecter la nouvelle stratégie de rétention que vous avez créée à l’étape 3 (par exemple, Archive House House et stratégie de **rétention)** au plan de boîte aux lettres par défaut. Cet exemple suppose que le nom du plan de boîte aux lettres par défaut **est ExchangeOnlineEnterprise**.

    ```powershell
    Set-MailboxPlan "ExchangeOnlineEnterprise" -RetentionPolicy "Alpine House Archive and Retention Policy"
    ```

4. Vous pouvez réexécuter la commande à l’étape 2 pour vérifier que la stratégie de rétention affectée au plan de boîte aux lettres par défaut a été modifiée.

## <a name="more-information"></a>Plus d’informations

- Comment l’âge de rétention est-il calculé ? L’âge de rétention des éléments de boîte aux lettres est calculé à partir de la date de remise ou de création des éléments tels que les brouillons qui ne sont pas envoyés mais créés par l’utilisateur. Quand l'Assistant Dossier géré traite les éléments d'une boîte aux lettres, il appose une date de début et une date d'expiration pour tous les éléments présentant des balises de rétention avec l'action de rétention Supprimer et autoriser la récupération ou Supprimer définitivement. Les éléments qui ont une balise d’archivage sont marqués avec une date de déplacement. 

- Le tableau suivant fournit plus d’informations sur chaque balise de rétention ajoutée à la stratégie de rétention personnalisée créée en suivant les étapes de cette rubrique.

    | Balise de rétention | Ce que fait cette balise | Intégré ou personnalisé ? | Type |
    |:-----|:-----|:-----|:-----|
    |Alpine House 3 Year Move to Archive  <br/> |Déplace les éléments de 1 095 jours (3 ans) vers la boîte aux lettres d’archivage.  <br/> |Personnalisé (voir Étape 2 : Créer des balises de rétention [pour les stratégies d’archivage](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies)et de suppression)  <br/> |Balise de stratégie par défaut (archive) ; Cette balise est automatiquement appliquée à l’ensemble de la boîte aux lettres.  <br/> |
    |Alpine House 7 Year Permanently Delete  <br/> |Supprime définitivement les éléments de la boîte aux lettres principale ou de la boîte aux lettres d’archivage lorsqu’ils ont 7 ans.  <br/> |Personnalisé (voir Étape 2 : Créer des balises de rétention [pour les stratégies d’archivage](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies)et de suppression)  <br/> |Balise de stratégie par défaut (suppression) ; Cette balise est automatiquement appliquée à l’ensemble de la boîte aux lettres.  <br/> |
    |Supprimer et autoriser la récupération des éléments supprimés de la maison de House 5 ans  <br/> |Supprime les éléments du dossier Éléments supprimés qui ont 5 ans. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Personnalisé (voir Étape 2 : Créer des balises de rétention [pour les stratégies d’archivage](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies)et de suppression)  <br/> |Balise de stratégie de rétention (éléments supprimés) ; Cette balise est automatiquement appliquée aux éléments du dossier Éléments supprimés.  <br/> |
    |Éléments récupérables de 14 jours Déplacer vers l’archive  <br/> |Déplace les éléments qui se sont produits dans le dossier Éléments récupérables pendant 14 jours vers le dossier Éléments récupérables de la boîte aux lettres d’archivage.  <br/> |Intégré  <br/> |Balise de stratégie de rétention (éléments récupérables) ; Cette balise est automatiquement appliquée aux éléments du dossier Éléments récupérables.  <br/> |
    |Courrier indésirable  <br/> |Supprime définitivement les éléments qui se sont produits dans le dossier Courrier indésirable pendant 30 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Balise de stratégie de rétention (courrier indésirable) ; Cette balise est automatiquement appliquée aux éléments du dossier Courrier indésirable.  <br/> |
    |Suppression après 1 mois  <br/> |Supprime définitivement les éléments qui ont 30 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Personnel ; Cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Suppression après 1 an  <br/> |Supprime définitivement les éléments qui ont 365 jours. Les utilisateurs peuvent récupérer ces éléments pendant 14 jours après leur suppression.<sup>\*</sup> <br/> |Intégré  <br/> |Personnel ; Cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Ne jamais supprimer  <br/> |Cette balise empêche la suppression d’éléments par une stratégie de rétention.  <br/> |Intégré  <br/> |Personnel ; Cette balise peut être appliquée par les utilisateurs.  <br/> |
    |Déplacement vers l’archive après 1 ans - Personnel  <br/> |Déplace les éléments vers la boîte aux lettres d’archivage après 1 an.  <br/> |Intégré  <br/> |Personnel ; Cette balise peut être appliquée par les utilisateurs.  <br/> |

    > <sup>\*</sup>Les utilisateurs peuvent utiliser l’outil Récupérer les éléments supprimés dans Outlook et Outlook sur le web (anciennement Outlook Web App) pour récupérer un élément supprimé au cours de la période de rétention des éléments supprimés, qui, par défaut, est de 14 jours dans Exchange Online. Un administrateur peut utiliser Windows PowerShell pour augmenter la période de rétention des éléments supprimés à un maximum de 30 jours. Pour plus d’informations, voir : Récupérer des éléments supprimés dans Outlook pour [Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce) et modifier la période de rétention des éléments supprimés pour une boîte aux lettres [dans Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention)
  
- L’utilisation de la balise de rétention Déplacer vers l’archive des éléments **récupérables de 14** jours permet de libérer de l’espace de stockage dans le dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur. Cela est utile lorsque la boîte aux lettres d’un utilisateur est placée en attente, ce qui signifie que rien n’est jamais supprimé définitivement de la boîte aux lettres de l’utilisateur. Sans déplacer d’éléments vers la boîte aux lettres d’archivage, il est possible que le quota de stockage du dossier Éléments récupérables de la boîte aux lettres principale soit atteint. Pour plus d’informations à ce sujet et pour savoir comment l’éviter, voir Augmenter le quota d’éléments [récupérables](./increase-the-recoverable-quota-for-mailboxes-on-hold.md)pour les boîtes aux lettres en attente.
