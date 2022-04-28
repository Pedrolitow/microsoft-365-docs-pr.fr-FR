---
title: Supprimer des éléments dans le dossier Éléments récupérables
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
- MET150
ms.assetid: a85e1c87-a48e-4715-bfa9-d5275cde67b0
description: Découvrez comment les administrateurs peuvent supprimer des éléments dans le dossier Éléments récupérables d’un utilisateur pour une boîte aux lettres Exchange Online, même si cette boîte aux lettres est mise en attente légale.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 808bc02eb711ff72ec8bd329b1367145d2d991a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091740"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Supprimer des éléments en attente dans le dossier Éléments récupérables des boîtes aux lettres basées sur le cloud

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Le dossier Éléments récupérables d’une boîte aux lettres Exchange Online existe pour vous protéger contre les suppressions accidentelles ou malveillantes. Il est également utilisé pour stocker les éléments qui sont conservés et accessibles par les fonctionnalités de conformité, telles que les conservations et les recherches eDiscovery. Toutefois, dans certaines situations, les organisations peuvent avoir des données qui ont été conservées involontairement dans le dossier Éléments récupérables qu’elles doivent supprimer. Par exemple, un utilisateur peut envoyer ou transférer sans le savoir un message électronique contenant des informations sensibles ou des informations susceptibles d’avoir de graves conséquences commerciales. Même si le message est supprimé définitivement, il peut être conservé indéfiniment, car une conservation légale a été placée sur la boîte aux lettres. Ce scénario est connu sous le nom de *débordement de données*, car des données ont été *accidentellement propagées* dans Office 365. Dans ces situations, vous pouvez supprimer des éléments dans le dossier Éléments récupérables d’un utilisateur pour une boîte aux lettres Exchange Online, même si cette boîte aux lettres est mise en attente avec l’une des différentes fonctionnalités de conservation dans Office 365. Ces types de conservations incluent les conservations de litige, les conservations In-Place, les conservations eDiscovery et les stratégies de rétention créées dans le centre de sécurité et de conformité dans Office 365 ou Microsoft 365.

Cet article explique comment les administrateurs peuvent supprimer des éléments du dossier Éléments récupérables pour les boîtes aux lettres basées sur le cloud qui sont en attente. Cette procédure implique la désactivation de l’accès à la boîte aux lettres et la désactivation de la récupération d’élément unique, la désactivation du traitement de la boîte aux lettres par l’Assistant Dossier géré, la suppression temporaire de la conservation, la suppression des éléments du dossier Éléments récupérables, puis le rétablissement de la boîte aux lettres vers sa configuration précédente. Voici le processus :
  
[Étape 1 : Collecter des informations sur la boîte aux lettres](#step-1-collect-information-about-the-mailbox)

[Étape 2 : Préparer la boîte aux lettres](#step-2-prepare-the-mailbox)

[Étape 3 : Supprimer toutes les conservations de la boîte aux lettres](#step-3-remove-all-holds-from-the-mailbox)

[Étape 4 : Supprimer le délai d’attente de la boîte aux lettres](#step-4-remove-the-delay-hold-from-the-mailbox)

[Étape 5 : Supprimer des éléments dans le dossier Éléments récupérables](#step-5-delete-items-in-the-recoverable-items-folder)

[Étape 6 : Rétablir l’état précédent de la boîte aux lettres](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Les procédures décrites dans cet article entraînent la suppression définitive (vidage) des données d’une boîte aux lettres Exchange Online. Cela signifie que les messages que vous supprimez du dossier Éléments récupérables ne peuvent pas être récupérés et ne seront pas disponibles à des fins de découverte légale ou de conformité. Si vous souhaitez supprimer des messages d’une boîte aux lettres qui est mise en attente dans le cadre d’une conservation pour litige, In-Place conservation, conservation eDiscovery ou stratégie de rétention créée dans le portail de conformité Microsoft Purview, vérifiez auprès de vos services juridiques ou de gestion des enregistrements avant de supprimer la conservation. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire.
  
## <a name="before-you-delete-items"></a>Avant de supprimer des éléments

- Pour créer et exécuter une recherche de contenu, vous devez être membre du groupe de rôles de gestionnaire de découverte électronique ou disposer du rôle de gestion de recherche de contenu. Pour supprimer des messages, vous devez être membre du groupe de rôles de gestion de l’organisation ou disposer du rôle de gestion de recherche et de purge. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, consultez Affecter des autorisations eDiscovery](./assign-ediscovery-permissions.md).

- Si une boîte aux lettres est affectée à une stratégie de rétention à l’échelle de l’organisation, vous devez exclure la boîte aux lettres de la stratégie avant de pouvoir supprimer des éléments du dossier Éléments récupérables. La synchronisation de la modification de stratégie et la suppression de la boîte aux lettres de la stratégie peuvent prendre jusqu’à 24 heures. Pour plus d’informations, consultez « Stratégies de rétention à l’échelle de l’organisation » dans la section [Supprimer toutes les conservations de la boîte aux lettres](#organization-wide-retention-policies) de cet article.

- Vous ne pouvez pas effectuer cette procédure pour une boîte aux lettres qui a reçu des paramètres de rétention avec une stratégie de rétention verrouillée à l’aide du verrou de conservation. En effet, ce verrou vous empêche de supprimer ou d’exclure la boîte aux lettres de la stratégie et de désactiver l’Assistant Dossier géré sur la boîte aux lettres. Pour plus d’informations sur le verrouillage des stratégies de rétention, consultez [Utiliser le verrou de conservation pour limiter les modifications apportées aux stratégies de rétention et aux stratégies d’étiquette de rétention](retention-preservation-lock.md).

- La procédure décrite dans cet article n’est pas prise en charge pour les boîtes aux lettres inactives. Cela est dû au fait que vous ne pouvez pas réappliquer une conservation (ou une stratégie de rétention) dans une boîte aux lettres inactive après l’avoir supprimée. Lorsque vous supprimez une conservation d’une boîte aux lettres inactive, elle est remplacée par une boîte aux lettres supprimée de manière réversible normale et sera définitivement supprimée de votre organisation après son traitement par l’Assistant Dossier géré.

- Si une boîte aux lettres n’est pas mise en attente (ou si la récupération d’élément unique n’est pas activée), vous pouvez supprimer les éléments du dossier Éléments récupérables. Pour plus d’informations sur la façon de procéder, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](./search-for-and-delete-messages-in-your-organization.md).

## <a name="step-1-collect-information-about-the-mailbox"></a>Étape 1 : Collecter des informations sur la boîte aux lettres

Cette première étape consiste à collecter les propriétés sélectionnées à partir de la boîte aux lettres cible qui affecteront cette procédure. Veillez à écrire ces paramètres ou à les enregistrer dans un fichier texte, car vous allez modifier certaines de ces propriétés, puis revenir aux valeurs d’origine à l’étape 6, après avoir supprimé des éléments du dossier Éléments récupérables. Voici une liste des propriétés de boîte aux lettres que vous devez collecter.
  
- *SingleItemRecoveryEnabled*  et  *RetainDeletedItemsFor*. Si nécessaire, vous allez désactiver la récupération unique et augmenter la période de rétention des éléments supprimés à l’étape 3.

- *LitigationHoldEnabled*  et  *InPlaceHolds*. Vous devez identifier toutes les conservations placées sur la boîte aux lettres afin de pouvoir les supprimer temporairement à l’étape 3. Consultez la section [Plus d’informations](#more-information) pour obtenir des conseils sur l’identification de la conservation de type qui peut être placée sur une boîte aux lettres.

En outre, vous devez obtenir les paramètres d’accès client de boîte aux lettres afin de pouvoir les désactiver temporairement afin que le propriétaire (ou d’autres utilisateurs) ne puisse pas accéder à la boîte aux lettres pendant cette procédure. Enfin, vous pouvez obtenir la taille actuelle et le nombre d’éléments dans le dossier Éléments récupérables. Après avoir supprimé des éléments dans le dossier Éléments récupérables à l’étape 5, vous allez utiliser ces informations pour vérifier que les éléments ont été supprimés.
  
1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Veillez à utiliser un nom d’utilisateur et un mot de passe pour un compte administrateur auquel les rôles de gestion appropriés ont été attribués dans Exchange Online.

2. Exécutez la commande suivante pour obtenir des informations sur la récupération d’élément unique et la période de rétention des éléments supprimés.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Si la récupération d’élément unique est activée, vous devez la désactiver à l’étape 2. Si la période de rétention des éléments supprimés n’est pas définie pendant 30 jours (valeur maximale dans Exchange Online), vous pouvez l’augmenter à l’étape 2.

3. Exécutez la commande suivante pour obtenir les paramètres d’accès à la boîte aux lettres pour la boîte aux lettres.

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

   Vous allez désactiver toutes ces méthodes d’accès à l’étape 2.

4. Exécutez la commande suivante pour obtenir des informations sur les conservations et les stratégies de rétention appliquées à la boîte aux lettres.

    ```powershell
    Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
    ```

    > [!TIP]
    > S’il y a trop de valeurs dans la propriété  *InPlaceHolds*  et que toutes ne sont pas affichées, vous pouvez exécuter la  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` commande pour afficher chaque valeur sur une ligne distincte.
  
5. Exécutez la commande suivante pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Si votre organisation a des stratégies de rétention à l’échelle de l’organisation, vous devez exclure la boîte aux lettres de ces stratégies à l’étape 3. La réplication de la modification peut prendre jusqu’à 24 heures.

    > [!TIP]
    > S’il y a trop de valeurs dans la propriété  *InPlaceHolds*  et que toutes ne sont pas affichées, vous pouvez exécuter la  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` commande pour afficher chaque valeur sur une ligne distincte. 
  
6. Exécutez la commande suivante pour déterminer si une conservation différée est appliquée à la boîte aux lettres.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Si la valeur de la propriété *DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True**, une conservation différée est appliquée à la boîte aux lettres et doit être supprimée. Pour plus d’informations sur les conservations de délai, consultez [l’étape 4 : Supprimer la conservation différée de la boîte aux lettres](#step-4-remove-the-delay-hold-from-the-mailbox).

   Si la valeur de l’une ou l’autre des propriétés est **définie sur False**, une conservation différée n’est pas appliquée à la boîte aux lettres et vous pouvez ignorer l’étape 4.

7. Exécutez la commande suivante pour obtenir la taille actuelle et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables dans la boîte aux lettres principale de l’utilisateur.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Si la boîte aux lettres d’archivage de l’utilisateur est activée, exécutez la commande suivante pour obtenir la taille et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables dans leur boîte aux lettres d’archivage. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Lorsque vous supprimez des éléments à l’étape 5, vous pouvez choisir de supprimer ou de ne pas supprimer des éléments dans le dossier Éléments récupérables de la boîte aux lettres d’archive principale de l’utilisateur. Si l’archivage à extension automatique est activé pour la boîte aux lettres, les éléments d’une boîte aux lettres d’archive auxiliaire ne sont pas supprimés.
  
## <a name="step-2-prepare-the-mailbox"></a>Étape 2 : Préparer la boîte aux lettres

Après avoir collecté et enregistré des informations sur la boîte aux lettres, l’étape suivante consiste à préparer la boîte aux lettres en effectuant les tâches suivantes :
  
- **Désactivez l’accès client à la boîte aux lettres** afin que le propriétaire de la boîte aux lettres ne puisse pas accéder à sa boîte aux lettres et apportez des modifications aux données de la boîte aux lettres pendant cette procédure.

- **Augmentez la période de rétention des éléments supprimés** à 30 jours (valeur maximale dans Exchange Online) afin que les éléments ne soient pas supprimés du dossier Éléments récupérables avant de pouvoir les supprimer à l’étape 5.

- **Désactivez la récupération d’élément unique** afin que les éléments ne soient pas conservés (pendant la durée de la période de rétention des éléments supprimés) après les avoir supprimés du dossier Éléments récupérables à l’étape 5.

- **Désactivez l’Assistant Dossier géré** afin qu’il ne traite pas la boîte aux lettres et conserve les éléments que vous supprimez à l’étape 5.

Effectuez les étapes suivantes dans Exchange Online PowerShell.
  
1. Exécutez la commande suivante pour désactiver tout accès client à la boîte aux lettres. La syntaxe de commande suppose que toutes les méthodes d’accès client ont été activées sur la boîte aux lettres.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > La désactivation de toutes les méthodes d’accès client à la boîte aux lettres peut prendre jusqu’à 60 minutes. Notez que la désactivation de ces méthodes d’accès ne déconnecte pas le propriétaire de la boîte aux lettres si elles sont actuellement connectées. Si le propriétaire n’est pas connecté, il ne pourra plus accéder à sa boîte aux lettres une fois ces méthodes d’accès désactivées.
  
2. Exécutez la commande suivante pour augmenter la période de rétention des éléments supprimés de 30 jours au maximum. Cela suppose que le paramètre actuel est inférieur à 30 jours.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Exécutez la commande suivante pour désactiver la récupération d’élément unique.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > La désactivation de la récupération d’un élément peut prendre jusqu’à 240 minutes. Ne supprimez pas les éléments du dossier Éléments récupérables tant que cette période n’est pas écoulée.
  
4. Exécutez la commande suivante pour empêcher l’Assistant Dossier géré de traiter la boîte aux lettres. Comme expliqué précédemment, vous ne pouvez désactiver l’Assistant Dossier géré que si une stratégie de rétention avec un verrou de conservation n’est pas appliquée à la boîte aux lettres.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Étape 3 : Supprimer toutes les conservations de la boîte aux lettres

La dernière étape avant de pouvoir supprimer des éléments du dossier Éléments récupérables consiste à supprimer toutes les conservations (que vous avez identifiées à l’étape 1) placées sur la boîte aux lettres. Toutes les conservations doivent être supprimées afin que les éléments ne soient pas conservés après les avoir supprimés du dossier Éléments récupérables. Les sections suivantes contiennent des informations sur la suppression de différents types de conservations sur une boîte aux lettres. Consultez la section [Plus d’informations](#more-information) pour obtenir des conseils sur l’identification de la conservation de type qui peut être placée sur une boîte aux lettres. Pour plus d’informations, consultez [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md).
  
> [!CAUTION]
> Comme indiqué précédemment, vérifiez auprès de vos services juridiques ou de gestion des enregistrements avant de supprimer une conservation d’une boîte aux lettres.
  
### <a name="litigation-hold"></a>Conservation pour litige
  
Exécutez la commande suivante dans Exchange Online PowerShell pour supprimer une conservation des litiges de la boîte aux lettres.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> À l’instar de la désactivation de la récupération d’élément unique, la suppression de la conservation du litige peut prendre jusqu’à 240 minutes. Ne supprimez pas les éléments du dossier Éléments récupérables tant que cette période n’est pas écoulée.
  
### <a name="in-place-hold"></a>Blocage local
  
Exécutez la commande suivante dans Exchange Online PowerShell pour identifier la In-Place Conservation placée sur la boîte aux lettres. Utilisez le GUID du In-Place Hold que vous avez identifié à l’étape 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Après avoir identifié le In-Place Hold, vous pouvez utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange (EAC)</a> ou Exchange Online PowerShell pour supprimer la boîte aux lettres de la conservation. Pour plus d'informations, voir [Créer ou supprimer une conservation inaltérable](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Stratégies de rétention appliquées à des boîtes aux lettres spécifiques
  
Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell) pour identifier la stratégie de rétention appliquée à la boîte aux lettres. Cette commande retourne également toutes les stratégies de rétention de conversation Teams appliquées à une boîte aux lettres. Utilisez le GUID (sans inclure le ou `skp` le `mbx` préfixe) pour la stratégie de rétention que vous avez identifiée à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Après avoir identifié la stratégie de rétention, accédez à la page **Gestionretention** >  du **cycle de vie des données** dans le portail de conformité, modifiez la stratégie de rétention que vous avez identifiée à l’étape précédente et supprimez la boîte aux lettres de la liste des destinataires inclus dans la stratégie de rétention.
  
### <a name="organization-wide-retention-policies"></a>Stratégies de rétention à l’échelle de l’organisation
  
Les stratégies de rétention à l’échelle de l’organisation, Exchange et Teams sont appliquées à chaque boîte aux lettres de l’organisation. Elles sont appliquées au niveau de l’organisation (et non au niveau de la boîte aux lettres) et sont retournées lorsque vous **exécutez l’applet de commande Get-OrganizationConfig** à l’étape 1. Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/exchange-online-powershell) pour identifier les stratégies de rétention à l’échelle de l’organisation. Utilisez le GUID (sans inclure le  `mbx` préfixe) pour les stratégies de rétention à l’échelle de l’organisation que vous avez identifiées à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Après avoir identifié les stratégies de rétention à l’échelle de l’organisation, accédez à la page **GestionRetention** >  du **cycle de vie des données** dans le portail de conformité, modifiez chaque stratégie de rétention à l’échelle de l’organisation que vous avez identifiée à l’étape précédente, puis ajoutez la boîte aux lettres à la liste des destinataires exclus. Cette opération supprime la boîte aux lettres de l’utilisateur de la stratégie de rétention.

> [!IMPORTANT]
> Après avoir exclu une boîte aux lettres d’une stratégie de rétention à l’échelle de l’organisation, la synchronisation de cette modification et la suppression de la boîte aux lettres de la stratégie peuvent prendre jusqu’à 24 heures.

### <a name="retention-labels"></a>Étiquettes de rétention

Chaque fois qu’un utilisateur applique une étiquette configurée pour conserver du contenu ou conserver, puis supprimer du contenu dans un dossier ou un élément de sa boîte aux lettres, la propriété de boîte aux lettres *ComplianceTagHoldApplied* est définie sur **True**. Dans ce cas, la boîte aux lettres est considérée comme étant en attente, comme si elle avait été mise en attente pour litige ou affectée à une stratégie de rétention.

Pour afficher la valeur de la propriété *ComplianceTagHoldApplied, exécutez* la commande suivante dans Exchange Online PowerShell :

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Une fois que vous avez identifié qu’une boîte aux lettres est en attente parce qu’une étiquette de rétention est appliquée à un dossier ou un élément, vous pouvez utiliser l’outil de recherche de contenu dans le portail de conformité pour rechercher des éléments étiquetés à l’aide de la condition **d’étiquette rétention** . Pour plus d’informations, voir :

- Section « Utilisation de la recherche de contenu pour rechercher tout le contenu avec une étiquette de rétention spécifique » dans [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)

- Section « Conditions de recherche » dans [les requêtes de mots clés et les conditions de recherche pour la recherche de contenu](keyword-queries-and-search-conditions.md#conditions-for-common-properties).

Pour plus d’informations sur les étiquettes, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md).

### <a name="ediscovery-holds"></a>Conservations eDiscovery
  
Exécutez les commandes suivantes dans [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) pour identifier la conservation associée à un cas *eDiscovery (appelé conservations eDiscovery*) appliqué à la boîte aux lettres. Utilisez le GUID (sans inclure le  `UniH` préfixe) pour la conservation eDiscovery que vous avez identifiée à l’étape 1. La deuxième commande affiche le nom de la casse eDiscovery à qui la conservation est associée ; la troisième commande affiche le nom de la conservation.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Une fois que vous avez identifié le nom du cas eDiscovery et la conservation, accédez à la page **eDiscovery eDiscovery**  \> dans le centre de conformité, ouvrez le cas et supprimez la boîte aux lettres de la conservation. Pour plus d’informations sur l’identification des conservations eDiscovery, consultez la section « conservations eDiscovery » dans [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Étape 4 : Supprimer le délai d’attente de la boîte aux lettres

Une fois que tout type de conservation est supprimé d’une boîte aux lettres, la valeur de la propriété de boîte aux lettres *DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True**. Cela se produit la prochaine fois que l’Assistant Dossier géré traite la boîte aux lettres et détecte qu’une conservation a été supprimée. Cela s’appelle une *conservation différée* et signifie que la suppression réelle de la conservation est retardée de 30 jours pour empêcher la suppression définitive des données de la boîte aux lettres. (L’objectif d’une conservation différée est de donner aux administrateurs la possibilité de rechercher ou de récupérer des éléments de boîte aux lettres qui seront purgés après la suppression d’une conservation.)  Lorsqu’un délai d’attente est placé sur la boîte aux lettres, la boîte aux lettres est toujours considérée comme étant en attente pendant une durée illimitée, comme si la boîte aux lettres était en attente de litige. Au bout de 30 jours, la suspension du délai expire et Microsoft 365 tente automatiquement de supprimer la conservation différée (en définissant la propriété *DelayHoldApplied* ou *DelayReleaseHoldApplied* sur **False**) afin que la conservation soit supprimée. Pour plus d’informations sur un délai d’attente, consultez la section « Gestion des boîtes aux lettres en attente de délai » dans [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold).

Si la valeur de la propriété *DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True**, exécutez l’une des commandes suivantes pour supprimer la conservation différée :

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Ou

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Le rôle De suspension légale doit vous être attribué dans Exchange Online pour utiliser le paramètre *RemoveDelayHoldApplied* ou *RemoveDelayReleaseHoldApplied*.

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Étape 5 : Supprimer des éléments dans le dossier Éléments récupérables

Vous êtes maintenant prêt à supprimer des éléments dans le dossier Éléments récupérables à l’aide des applets de commande [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) et [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) du Centre de sécurité & conformité PowerShell.

Pour rechercher des éléments situés dans le dossier Éléments récupérables, nous vous recommandons d’effectuer une *collection ciblée*. Cela signifie que vous limitez l’étendue de votre recherche uniquement aux éléments situés dans le dossier Éléments récupérables. Pour ce faire, exécutez le script dans l’article [Utiliser la recherche de contenu pour les collections ciblées](use-content-search-for-targeted-collections.md) . Ce script retourne la valeur de la propriété ID de dossier pour tous les sous-dossiers du dossier Éléments récupérables cible. Vous utilisez ensuite l’ID de dossier dans une requête de recherche pour renvoyer les éléments situés dans ce dossier.

Voici une vue d’ensemble du processus de recherche et de suppression d’éléments dans le dossier Éléments récupérables d’un utilisateur :

1. Exécutez le script de regroupement ciblé qui retourne les ID de dossier pour tous les dossiers de la boîte aux lettres de l’utilisateur cible. Le script se connecte à Exchange Online PowerShell et Security & Compliance PowerShell dans la même session PowerShell. Pour plus d’informations, consultez [Exécuter le script pour obtenir la liste des dossiers d’une boîte aux lettres](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site).

2. Copiez les ID de dossier pour tous les sous-dossiers du dossier Éléments récupérables. Vous pouvez également rediriger la sortie du script vers un fichier texte.

   Voici une liste et une description des sous-dossiers du dossier Éléments récupérables à partir de laquelle vous pouvez rechercher et supprimer des éléments :

   - **Suppressions** : contient des éléments supprimés de manière réversible dont la période de rétention des éléments supprimés n’a pas expiré. Les utilisateurs peuvent récupérer des éléments supprimés de manière réversible à partir de ce sous-dossier à l’aide de l’outil Récupérer les éléments supprimés dans Outlook.

   - **DiscoveryHolds** : contient des éléments supprimés en dur qui ont été conservés par une conservation eDiscovery ou une stratégie de rétention. Ce sous-dossier n’est pas visible par les utilisateurs finaux.

   - **SubstrateHolds** : contient des éléments supprimés en dur de Teams et d’autres applications cloud qui ont été conservées par une stratégie de rétention ou un autre type de conservation. Ce sous-dossier n’est pas visible par les utilisateurs finaux.

3. Utilisez l’applet de commande **New-ComplianceSearch** (dans Security & Compliance Center PowerShell) ou utilisez l’outil de recherche de contenu dans le centre de conformité pour créer une recherche de contenu qui retourne des éléments du dossier Éléments récupérables de l’utilisateur cible. Pour ce faire, vous pouvez inclure folderId dans la requête de recherche pour tous les sous-dossiers que vous souhaitez rechercher. Par exemple, la requête suivante retourne tous les messages dans les sous-dossiers Deletions et eDiscoveryHolds :

   ```text
   folderid:<folder ID of Deletions subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Pour plus d’informations et des exemples sur l’exécution de recherches de contenu qui utilisent la propriété ID de dossier, consultez [Utiliser un ID de dossier ou effectuer une collection ciblée](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection).

   > [!NOTE]
   > Si vous utilisez l’applet de commande **New-ComplianceSearch** pour rechercher dans le dossier Éléments récupérables, veillez à utiliser l’applet de commande **Start-ComplianceSearch** pour exécuter la recherche.

4. Une fois que vous avez créé une recherche de contenu et vérifié qu’elle retourne les éléments que vous souhaitez supprimer, utilisez la commande (dans Le `New-ComplianceSearchAction -Purge -PurgeType HardDelete` Centre de sécurité & conformité PowerShell) pour supprimer définitivement les éléments retournés par la recherche de contenu que vous avez créée à l’étape précédente. Par exemple, vous pouvez exécuter une commande similaire à la commande suivante :

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Un maximum de 10 éléments par boîte aux lettres sont supprimés lorsque vous exécutez la commande précédente. Cela signifie que vous devrez peut-être exécuter la `New-ComplianceSearchAction -Purge` commande plusieurs fois pour supprimer tous les éléments que vous souhaitez supprimer dans le dossier Éléments récupérables. Pour supprimer des éléments supplémentaires, vous devez d’abord supprimer l’action précédente de vidage de la recherche de conformité. Pour ce faire, exécutez l’applet `Remove-ComplianceSearchAction` de commande. Par exemple, pour supprimer l’action de vidage exécutée à l’étape précédente, exécutez la commande suivante :

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Après cela, vous pouvez créer une action de vidage de recherche de conformité pour supprimer d’autres éléments. Vous devrez supprimer chaque action de vidage avant d’en créer une.

   Pour obtenir la liste des actions de recherche de conformité, vous pouvez exécuter l’applet de `Get-ComplianceSearchAction` commande. Les actions de vidage sont identifiées par `_Purge` ajout au nom de recherche.

### <a name="verify-that-items-were-deleted"></a>Vérifier que les éléments ont été supprimés

Pour vérifier que vous avez correctement supprimé des éléments du dossier Éléments récupérables d’une boîte aux lettres, utilisez l’applet de commande **Get-MailboxFolderStatistics** dans Exchange Online PowerShell pour vérifier la taille et le nombre d’éléments dans le dossier Éléments récupérables. Vous pouvez comparer ces statistiques avec celles que vous avez collectées à l’étape 1.
  
Exécutez la commande suivante pour obtenir la taille actuelle et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables dans la boîte aux lettres principale de l’utilisateur.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Exécutez la commande suivante pour obtenir la taille et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables dans la boîte aux lettres d’archivage de l’utilisateur.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Étape 6 : Rétablir l’état précédent de la boîte aux lettres

La dernière étape consiste à rétablir la configuration précédente de la boîte aux lettres. Cela signifie réinitialiser les propriétés que vous avez modifiées à l’étape 2 et réappliquer les conservations que vous avez supprimées à l’étape 3. Cela inclut les opérations suivantes :
  
- Modification de la période de rétention des éléments supprimés à sa valeur précédente. Vous pouvez également laisser cet ensemble à 30 jours, la valeur maximale dans Exchange Online.

- Réactiver la récupération d’élément unique.

- Réactiver les méthodes d’accès client afin que le propriétaire puisse accéder à sa boîte aux lettres.

- Réappliquer les conservations et les stratégies de rétention que vous avez supprimées.

- Réactiver l’Assistant Dossiers managés pour traiter la boîte aux lettres.

> [!IMPORTANT]
> Nous vous recommandons d’attendre 24 heures après avoir réappliquer une stratégie de conservation ou de rétention (et avoir vérifié qu’elle est en place) avant de réactiver l’Assistant Dossier géré pour traiter la boîte aux lettres.
  
Effectuez les étapes suivantes (dans la séquence spécifiée) dans Exchange Online PowerShell.
  
1. Exécutez la commande suivante pour revenir à la période de rétention de l’élément supprimé à sa valeur d’origine. Cela suppose que le paramètre précédent est inférieur à 30 jours ; par exemple, 14 jours.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Exécutez la commande suivante pour réactiver la récupération d’élément unique.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Exécutez la commande suivante pour réactiver toutes les méthodes d’accès client à la boîte aux lettres.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Réappliquez les conservations que vous avez supprimées à l’étape 3. Selon le type de conservation, utilisez l’une des procédures suivantes.

    **Conservation pour litige**

    Exécutez la commande suivante pour réactiver une conservation des litiges pour la boîte aux lettres.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **In-Place Hold**

    Utilisez l’EAC (ou Exchange Online PowerShell) pour rajouter la boîte aux lettres à la In-Place Hold.

    **Stratégies de rétention appliquées à des boîtes aux lettres spécifiques**

    Utilisez le portail de conformité pour rajouter la boîte aux lettres à la stratégie de rétention. Accédez à la page **Gestion** >  **du** cycle de vie des données dans le centre de conformité, modifiez la stratégie de rétention et ajoutez la boîte aux lettres à la liste des destinataires auxquels la stratégie de rétention est appliquée.

    **Stratégies de rétention à l’échelle de l’organisation**

    Si vous avez supprimé une stratégie de rétention à l’échelle de l’organisation ou Exchange en l’excluant de la stratégie, utilisez le portail de conformité pour supprimer la boîte aux lettres de la liste des utilisateurs exclus. Accédez à la page **Gestion** >  **du** cycle de vie des données dans le Centre de conformité, modifiez la stratégie de rétention à l’échelle de l’organisation et supprimez la boîte aux lettres de la liste des destinataires exclus. Cette opération réapplique la stratégie de rétention dans la boîte aux lettres de l’utilisateur.

    **Conservations de cas eDiscovery**

    Utilisez le portail de conformité pour ajouter la boîte aux lettres à la conservation associée à un cas eDiscovery. Accédez à la page **eDiscoveryCore** > , ouvrez le cas et ajoutez la boîte aux lettres à la conservation. 

5. Exécutez la commande suivante pour permettre à l’Assistant Dossier géré de traiter à nouveau la boîte aux lettres. Comme indiqué précédemment, nous vous recommandons d’attendre 24 heures après avoir réappliquer une stratégie de conservation ou de rétention (et de vérifier qu’elle est en place) avant de réactiver l’Assistant Dossier géré.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Pour vérifier que la boîte aux lettres a été rétablie à sa configuration précédente, vous pouvez exécuter les commandes suivantes, puis comparer les paramètres à celles que vous avez collectées à l’étape 1.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Plus d’informations

Voici un tableau qui explique comment identifier différents types de conservations en fonction des valeurs de la propriété  *InPlaceHolds*  lorsque vous exécutez les applets de commande **Get-Mailbox** ou **Get-OrganizationConfig** . Pour plus d’informations, consultez [Comment identifier le type de conservation placé sur une boîte aux lettres Exchange Online](identify-a-hold-on-an-exchange-online-mailbox.md).

Comme expliqué précédemment, vous devez supprimer toutes les conservations et stratégies de rétention d’une boîte aux lettres avant de pouvoir supprimer des éléments dans le dossier Éléments récupérables.
  
| Type de conservation | Exemple de valeur | Comment identifier la conservation |
|:-----|:-----|:-----|
|Conservation pour litige  <br/> | `True` <br/> |La propriété  *LitigationHoldEnabled*  est définie sur  `True`.  <br/> |
|Blocage local  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |La propriété  *InPlaceHolds*  contient le GUID du In-Place Hold placé sur la boîte aux lettres. Vous pouvez indiquer qu’il s’agit d’une In-Place en attente, car le GUID ne commence pas par un préfixe.  <br/> Vous pouvez utiliser la `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` commande dans Exchange Online PowerShell pour obtenir des informations sur la In-Place la boîte aux lettres.  <br/> |
| Stratégies de rétention dans le portail de conformité appliquées à des boîtes aux lettres spécifiques  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> ou  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Lorsque vous exécutez l’applet **de commande Get-Mailbox** , la propriété  *InPlaceHolds*  contient également les GUID des stratégies de rétention appliquées à la boîte aux lettres. Vous pouvez identifier les stratégies de rétention, car le GUID commence par le  `mbx` préfixe. Si le GUID de la stratégie de rétention commence par le `skp` préfixe, cela indique que la stratégie de rétention est appliquée à Skype Entreprise conversations.  <br/> Pour identifier la stratégie de rétention appliquée à la boîte aux lettres, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell : <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>N'oubliez pas de supprimer le préfixe  `mbx` ou  `skp` lorsque vous exécutez cette commande.  <br/> |
|Stratégies de rétention à l’échelle de l’organisation dans le portail de conformité  <br/> |Aucune valeur  <br/> ou  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (indique que la boîte aux lettres est exclue d’une stratégie à l’échelle de l’organisation)  <br/> |Même si la propriété  *InPlaceHolds*  est vide lorsque vous exécutez l’applet de commande **Get-Mailbox** , il peut toujours y avoir une ou plusieurs stratégies de rétention à l’échelle de l’organisation appliquées à la boîte aux lettres.  <br/> Pour vérifier cela, vous pouvez exécuter la `Get-OrganizationConfig | FL InPlaceHolds` commande dans Exchange Online PowerShell pour obtenir la liste des GUID pour les stratégies de rétention à l’échelle de l’organisation. Le GUID pour les stratégies de rétention à l’échelle de l’organisation appliquées aux boîtes aux lettres Exchange commence par le `mbx` préfixe ; par exemple, `mbxa3056bb15562480fadb46ce523ff7b02`.  <br/> Pour identifier la stratégie de rétention à l’échelle de l’organisation appliquée à la boîte aux lettres, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell : <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Si une boîte aux lettres est exclue d’une stratégie de rétention à l’échelle de l’organisation, le GUID de la stratégie de rétention s’affiche dans la propriété  *InPlaceHolds*  de la boîte aux lettres de l’utilisateur lorsque vous exécutez l’applet **de commande Get-Mailbox** ; il est identifié par le préfixe  `-mbx`; par exemple,  `-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|Conservation du cas eDiscovery dans le portail de conformité  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |La propriété  *InPlaceHolds*  contient également le GUID de toute conservation associée à un cas eDiscovery dans le portail de conformité qui peut être placé sur la boîte aux lettres. Vous pouvez déterminer qu'il s'agit d'une mise en conservation de cas eDiscovery, car le GUID commence par le préfixe  `UniH`.  <br/> Vous pouvez utiliser l’applet  `Get-CaseHoldPolicy` de commande du Centre de sécurité & conformité PowerShell pour obtenir des informations sur le cas eDiscovery auquel la conservation de la boîte aux lettres est associée. Par exemple, vous pouvez exécuter la commande  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` pour afficher le nom de la conservation de la casse qui se trouve sur la boîte aux lettres. Be sure to remove the  `UniH` lorsque vous exécutez cette commande.  <br/><br/> Pour identifier le cas eDiscovery auquel la conservation de la boîte aux lettres est associée, exécutez les commandes suivantes :<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
