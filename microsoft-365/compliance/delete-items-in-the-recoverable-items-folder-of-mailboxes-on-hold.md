---
title: Supprimer des éléments du dossier Éléments récupérables de la boîte aux lettres cloud en attente
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Découvrez comment les administrateurs peuvent supprimer des éléments dans le dossier Éléments récupérables d’un utilisateur pour une boîte aux lettres Exchange Online, même si cette boîte aux lettres est placée en attente légale.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aedd887caed1ffd4484ea55561aa77562869726a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60189428"
---
# <a name="delete-items-in-the-recoverable-items-folder-of-cloud-based-mailboxes-on-hold"></a>Supprimer des éléments en attente dans le dossier Éléments récupérables des boîtes aux lettres basées sur le cloud

Le dossier Éléments récupérables d’Exchange Online boîte aux lettres de sécurité existe pour vous protéger contre les suppressions accidentelles ou malveillantes. Il est également utilisé pour stocker les éléments qui sont conservés et accessibles par les fonctionnalités de conformité, telles que les rétentions et les recherches eDiscovery. Toutefois, dans certains cas, les organisations peuvent avoir des données qui ont été involontairement conservées dans le dossier Éléments récupérables qu’elles doivent supprimer. Par exemple, un utilisateur peut sans le savoir envoyer ou transmettre un message électronique contenant des informations sensibles ou des informations qui peuvent avoir de graves conséquences professionnelles. Même si le message est définitivement supprimé, il peut être conservé indéfiniment car une mise en attente légale a été placée sur la boîte aux lettres. Ce scénario est appelé *débordement de* données, car les données ont été accidentellement répandus *dans* Office 365. Dans ces situations, vous pouvez supprimer des éléments dans le dossier Éléments récupérables d’un utilisateur pour une boîte aux lettres Exchange Online, même si cette boîte aux lettres est placée en attente avec l’une des différentes fonctionnalités de mise en attente dans Office 365. Ces types de conservations incluent les conservations pour litige, les conservations In-Place, les conservations eDiscovery et les stratégies de rétention créées dans le centre de sécurité et conformité dans Office 365 ou Microsoft 365.

Cet article explique comment les administrateurs peuvent supprimer des éléments du dossier Éléments récupérables pour les boîtes aux lettres informatiques en attente. Cette procédure implique la désactivation de l’accès à la boîte aux lettres et la désactivation de la récupération d’élément unique, la désactivation du traitement de la boîte aux lettres par l’Assistant Dossier géré, la suppression temporaire de la mise en attente, la suppression d’éléments du dossier Éléments récupérables, puis le rétablissement de la configuration précédente de la boîte aux lettres. Voici le processus :
  
[Étape 1 : Collecter des informations sur la boîte aux lettres](#step-1-collect-information-about-the-mailbox)

[Étape 2 : Préparer la boîte aux lettres](#step-2-prepare-the-mailbox)

[Étape 3 : Supprimer toutes les ententes de la boîte aux lettres](#step-3-remove-all-holds-from-the-mailbox)

[Étape 4 : Supprimer le délai d’attente de la boîte aux lettres](#step-4-remove-the-delay-hold-from-the-mailbox)

[Étape 5 : Supprimer des éléments dans le dossier Éléments récupérables](#step-5-delete-items-in-the-recoverable-items-folder)

[Étape 6 : Revenir à l’état précédent de la boîte aux lettres](#step-6-revert-the-mailbox-to-its-previous-state)
  
> [!CAUTION]
> Les procédures décrites dans cet article entraînent la suppression définitive (purgée) des données d’une boîte aux lettres Exchange Online’utilisateur. Cela signifie que les messages que vous supprimez du dossier Éléments récupérables ne peuvent pas être récupérés et ne seront pas disponibles à des fins de découverte légale ou de conformité. Si vous souhaitez supprimer des messages d’une boîte aux lettres placée en conservation dans le cadre d’une conservation pour litige, d’une conservation In-Place, d’une conservation eDiscovery ou d’une stratégie de rétention créée dans le centre de sécurité et conformité, consultez vos services juridiques ou de gestion des enregistrements avant de supprimer la conservation. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire.
  
## <a name="before-you-delete-items"></a>Avant de supprimer des éléments

- Pour créer et exécuter une recherche de contenu, vous devez être membre du groupe de rôles de gestionnaire de découverte électronique ou disposer du rôle de gestion de recherche de contenu. Pour supprimer des messages, vous devez être membre du groupe de rôles de gestion de l’organisation ou disposer du rôle de gestion de recherche et de purge. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, voir Attribuer des autorisations eDiscovery](./assign-ediscovery-permissions.md).

- La procédure décrite dans cet article n’est pas prise en charge pour les boîtes aux lettres inactives. Cela est dû au fait que vous ne pouvez pas réappliquer une conservation (ou une stratégie de rétention) à une boîte aux lettres inactive après l’avoir supprimée. Lorsque vous supprimez une boîte aux lettres inactive, elle devient une boîte aux lettres normale supprimée (suppression temporaire) et est définitivement supprimée de votre organisation après son traitement par l’Assistant Dossier géré.

- Vous ne pouvez pas effectuer cette procédure pour une boîte aux lettres à qui des paramètres de rétention ont été affectés avec une stratégie verrouillée à l’aide du verrouillage de conservation. En effet, ce verrou vous empêche de supprimer ou d’exclure la boîte aux lettres de la stratégie et de désactiver l’Assistant Dossier géré sur la boîte aux lettres. Pour plus d’informations sur les stratégies de verrouillage pour la rétention, voir Utiliser le verrouillage de conservation pour limiter les modifications apportées aux stratégies de rétention et aux stratégies [d’étiquette de rétention.](retention-preservation-lock.md)

- Si une boîte aux lettres n’est pas placée en attente (ou si la récupération d’élément unique n’est pas activée), vous pouvez supprimer les éléments du dossier Éléments récupérables. Pour plus d’informations sur la façon de le faire, voir Rechercher et supprimer des [messages électroniques dans votre organisation.](./search-for-and-delete-messages-in-your-organization.md)
  
## <a name="step-1-collect-information-about-the-mailbox"></a>Étape 1 : Collecter des informations sur la boîte aux lettres

Cette première étape consiste à collecter les propriétés sélectionnées de la boîte aux lettres cible qui affecteront cette procédure. N’oubliez pas d’écrire ces paramètres ou de les enregistrer dans un fichier texte, car vous allez modifier certaines de ces propriétés, puis revenir aux valeurs d’origine à l’étape 6, après avoir supprimé des éléments du dossier Éléments récupérables. Voici une liste des propriétés de boîte aux lettres que vous devez collecter.
  
- *SingleItemRecoveryEnabled*  et  *RetainDeletedItemsFor*. Si nécessaire, vous désactivez la récupération unique et augmentez la période de rétention des éléments supprimés à l’étape 3.

- *LitigationHoldEnabled et*  *InPlaceHolds*. Vous devez identifier toutes les mises en place sur la boîte aux lettres afin de pouvoir les supprimer temporairement à l’étape 3. Consultez la section [Plus d’informations](#more-information) pour obtenir des conseils sur l’identification du type de mise en attente qui peut être placé sur une boîte aux lettres.

En outre, vous devez obtenir les paramètres d’accès client de boîte aux lettres afin de pouvoir les désactiver temporairement afin que le propriétaire (ou d’autres utilisateurs) ne puisse pas accéder à la boîte aux lettres au cours de cette procédure. Enfin, vous pouvez obtenir la taille actuelle et le nombre d’éléments dans le dossier Éléments récupérables. Après avoir supprimé des éléments du dossier Éléments récupérables à l’étape 5, vous utiliserez ces informations pour vérifier que les éléments ont été supprimés.
  
1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). N’oubliez pas d’utiliser un nom d’utilisateur et un mot de passe pour un compte d’administrateur qui a reçu les rôles de gestion appropriés dans Exchange Online.

2. Exécutez la commande suivante pour obtenir des informations sur la récupération d’élément unique et la période de rétention des éléments supprimés.

    ```powershell
    Get-Mailbox <username> | FL SingleItemRecoveryEnabled,RetainDeletedItemsFor
    ```

   Si la récupération d’élément unique est activée, vous devez la désactiver à l’étape 2. Si la période de rétention des éléments supprimés n’est pas définie pendant 30 jours (la valeur maximale dans Exchange Online), vous pouvez l’augmenter à l’étape 2.

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
    > S’il y a trop de valeurs dans la propriété  *InPlaceHolds*  et qu’elles ne sont pas toutes affichées, vous pouvez exécuter la commande pour afficher chaque valeur sur une  `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` ligne distincte.
  
5. Exécutez la commande suivante pour obtenir des informations sur les stratégies de rétention à l’échelle de l’organisation. 

    ```powershell
    Get-OrganizationConfig | FL InPlaceHolds
    ```

   Si votre organisation dispose de stratégies de rétention à l’échelle de l’organisation, vous devez exclure la boîte aux lettres de ces stratégies à l’étape 3. La réplication de la modification peut prendre jusqu’à 24 heures.

    > [!TIP]
    > S’il y a trop de valeurs dans la propriété  *InPlaceHolds*  et qu’elles ne sont pas toutes affichées, vous pouvez exécuter la commande pour afficher chaque valeur sur une  `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` ligne distincte. 
  
6. Exécutez la commande suivante pour déterminer si un délai d’attente est appliqué à la boîte aux lettres.

   ```powershell
   Get-Mailbox <username> | FL DelayHoldApplied,DelayReleaseHoldApplied
   ```

   Si la valeur de la propriété *DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True**, un délai d’attente est appliqué à la boîte aux lettres et doit être supprimé. Pour plus d’informations sur les délais d’attente, consultez [l’étape 4 : Supprimer le délai d’attente de la boîte aux lettres.](#step-4-remove-the-delay-hold-from-the-mailbox)

   Si la valeur de l’une ou l’autre des propriétés est définie sur **False,** un délai d’attente n’est pas appliqué à la boîte aux lettres et vous pouvez ignorer l’étape 4.

7. Exécutez la commande suivante pour obtenir la taille actuelle et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur.

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Si la boîte aux lettres d’archivage de l’utilisateur est activée, exécutez la commande suivante pour obtenir la taille et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables de leur boîte aux lettres d’archivage. 

    ```powershell
    Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
    ```

   Lorsque vous supprimez des éléments à l’étape 5, vous pouvez choisir de supprimer ou de ne pas supprimer les éléments du dossier Éléments récupérables de la boîte aux lettres d’archivage principale de l’utilisateur. Si l’archivage à extension automatique est activé pour la boîte aux lettres, les éléments d’une boîte aux lettres d’archivage auxiliaire ne sont pas supprimés.
  
## <a name="step-2-prepare-the-mailbox"></a>Étape 2 : Préparer la boîte aux lettres

Après avoir collecté et enregistrement des informations sur la boîte aux lettres, l’étape suivante consiste à préparer la boîte aux lettres en effectuer les tâches suivantes :
  
- **Désactivez l’accès client à** la boîte aux lettres afin que le propriétaire de la boîte aux lettres ne puisse pas accéder à sa boîte aux lettres et apporter des modifications aux données de la boîte aux lettres au cours de cette procédure.

- Augmentez la période **de** rétention des éléments supprimés à 30 jours (la valeur maximale dans Exchange Online) afin que les éléments ne sont pas purgés du dossier Éléments récupérables avant de pouvoir être supprimés à l’étape 5.

- **Désactivez** la récupération d’élément unique afin que les éléments ne soient pas conservés (pendant la période de rétention des éléments supprimés) après les avoir supprimés du dossier Éléments récupérables à l’étape 5.

- **Désactivez l’Assistant Dossier** géré afin qu’il ne gère pas la boîte aux lettres et conserve les éléments que vous supprimez à l’étape 5.

Effectuez les étapes suivantes dans Exchange Online PowerShell.
  
1. Exécutez la commande suivante pour désactiver tout accès client à la boîte aux lettres. La syntaxe de commande suppose que toutes les méthodes d’accès client ont été activées sur la boîte aux lettres.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $false -ActiveSyncEnabled $false -MAPIEnabled $false -OWAEnabled $false -ImapEnabled $false -PopEnabled $false
    ```

    > [!NOTE]
    > La désactivation de toutes les méthodes d’accès client à la boîte aux lettres peut prendre jusqu’à 60 minutes. Notez que la désactivation de ces méthodes d’accès ne déconnecte pas le propriétaire de la boîte aux lettres s’il est actuellement déconnecté. Si le propriétaire n’est pas signé, il ne pourra pas accéder à sa boîte aux lettres une fois ces méthodes d’accès désactivées.
  
2. Exécutez la commande suivante pour augmenter la période de rétention des éléments supprimés au maximum de 30 jours. Cela suppose que le paramètre actuel est inférieur à 30 jours.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 30
    ```

3. Exécutez la commande suivante pour désactiver la récupération d’élément unique.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $false
    ```

    > [!NOTE]
    > La désactivation de la récupération d’élément unique peut prendre jusqu’à 60 minutes. Ne supprimez pas les éléments du dossier Éléments récupérables tant que cette période n’est pas écoulée. 
  
4. Exécutez la commande suivante pour empêcher l’Assistant Dossier géré de traiter la boîte aux lettres. Comme indiqué précédemment, vous pouvez désactiver l’Assistant Dossier géré uniquement si une stratégie de rétention avec un verrouillage de conservation n’est pas appliquée à la boîte aux lettres. 

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $true
    ```

## <a name="step-3-remove-all-holds-from-the-mailbox"></a>Étape 3 : Supprimer toutes les ententes de la boîte aux lettres

La dernière étape avant de pouvoir supprimer des éléments du dossier Éléments récupérables consiste à supprimer toutes les mises en place (que vous avez identifiées à l’étape 1) placées sur la boîte aux lettres. Toutes les rétentions doivent être supprimées afin que les éléments ne soient pas conservés après leur suppression du dossier Éléments récupérables. Les sections suivantes contiennent des informations sur la suppression de différents types de boîtes aux lettres. Consultez la section [Plus d’informations](#more-information) pour obtenir des conseils sur l’identification du type de mise en attente qui peut être placé sur une boîte aux lettres. Pour plus d’informations, voir Comment identifier le type de mise en attente placée sur [Exchange Online boîte aux lettres.](identify-a-hold-on-an-exchange-online-mailbox.md)
  
> [!CAUTION]
> Comme indiqué précédemment, consultez vos services juridiques ou de gestion des enregistrements avant de supprimer une archive d’une boîte aux lettres. 
  
### <a name="litigation-hold"></a>Conservation pour litige
  
Exécutez la commande suivante dans Exchange Online PowerShell pour supprimer une attente pour litige de la boîte aux lettres.

```powershell
Set-Mailbox <username> -LitigationHoldEnabled $false
```

> [!NOTE]
> Tout comme la désactivation des méthodes d’accès client et de la récupération d’élément unique, la suppression de la attente pour litige peut prendre jusqu’à 60 minutes. Ne supprimez pas d’éléments du dossier Éléments récupérables tant que cette période n’est pas écoulée. 
  
### <a name="in-place-hold"></a>Blocage local
  
Exécutez la commande suivante dans Exchange Online PowerShell pour identifier le In-Place qui est placé sur la boîte aux lettres. Utilisez le GUID de la In-Place d’attente que vous avez identifiée à l’étape 1.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name
```

Après avoir identifié la In-Place, vous pouvez utiliser le Centre d’administration Exchange (EAC) ou Exchange Online PowerShell pour supprimer la boîte aux lettres de la boîte aux lettres de la boîte aux lettres. Pour plus d'informations, voir [Créer ou supprimer une conservation inaltérable](/exchange/security-and-compliance/create-or-remove-in-place-holds).
  
### <a name="retention-policies-applied-to-specific-mailboxes"></a>Stratégies de rétention appliquées à des boîtes aux lettres spécifiques
  
Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/exchange-online-powershell) pour identifier la stratégie de rétention qui est appliquée à la boîte aux lettres. Cette commande retourne également toutes les stratégies Teams rétention de conversation appliquées à une boîte aux lettres. Utilisez le GUID (sans le préfixe ou le GUID) pour la stratégie de rétention que vous avez identifiée `mbx` `skp` à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Après avoir identifié la stratégie de rétention, go to the **Information governance**  >  **Retention** page in the Centre de conformité Microsoft 365, edit the retention policy that you identified in the previous step, and remove the mailbox from the list of recipients that are included in the retention policy.
  
### <a name="organization-wide-retention-policies"></a>Stratégies de rétention à l’échelle de l’organisation
  
Les stratégies de rétention à l’échelle Exchange, à l’échelle Teams et à l’échelle de l’organisation sont appliquées à chaque boîte aux lettres de l’organisation. Elles sont appliquées au niveau de l’organisation (et non au niveau de la boîte aux lettres) et sont renvoyées lorsque vous exécutez la cmdlet **Get-OrganizationConfig** à l’étape 1. Exécutez la commande suivante dans [le Centre de sécurité & conformité PowerShell](/powershell/exchange/exchange-online-powershell) pour identifier les stratégies de rétention à l’échelle de l’organisation. Utilisez le GUID (sans le préfixe) pour les stratégies de rétention à l’échelle de l’organisation que vous avez identifiées  `mbx` à l’étape 1.

```powershell
Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name
```

Après avoir identifié les stratégies de rétention à l’échelle de l’organisation, go to the **Information governance**  >  **Retention** page in the Centre de conformité Microsoft 365, edit each organization-wide retention policy that you identified in the previous step, and add the mailbox to the list of excluded recipients. Cela supprimera la boîte aux lettres de l’utilisateur de la stratégie de rétention. La réplication de la modification peut prendre jusqu’à 24 heures.

### <a name="retention-labels"></a>Étiquettes de rétention

Chaque fois qu’un utilisateur applique une étiquette configurée pour conserver du contenu ou conserver, puis supprimer le contenu d’un dossier ou d’un élément de sa boîte aux lettres, la propriété de boîte aux lettres *ComplianceTagHoldApplied* est définie sur **True**. Dans ce cas, la boîte aux lettres est considérée comme placée en conservation pour litige ou affectée à une stratégie de rétention.

Pour afficher la valeur de la *propriété ComplianceTagHoldApplied,* exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-Mailbox <username> |FL ComplianceTagHoldApplied
```

Une fois que vous avez identifié qu’une boîte aux lettres est en attente parce qu’une étiquette de rétention est appliquée à un dossier ou un élément, vous pouvez utiliser l’outil de recherche de contenu dans le centre de sécurité et conformité pour rechercher des éléments étiquetés à l’aide de la condition de recherche ComplianceTag. Pour plus d’informations, voir la section « Conditions de recherche » dans requêtes par mot clé et conditions de recherche [pour la recherche de contenu.](keyword-queries-and-search-conditions.md#conditions-for-common-properties)

Pour plus d’informations sur les étiquettes, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)

### <a name="ediscovery-holds"></a>Conservations eDiscovery
  
Exécutez les commandes suivantes dans le Centre de sécurité & conformité [PowerShell](/powershell/exchange/connect-to-scc-powershell) pour identifier la mise en attente associée à un cas eDiscovery (appelés « boîtes aux lettres *eDiscovery*» ) qui est appliqué à la boîte aux lettres. Utilisez le GUID (sans le préfixe) pour la période d’attente eDiscovery que vous avez identifiée  `UniH` à l’étape 1. La deuxième commande affiche le nom du cas eDiscovery à l’associé à la attente ; La troisième commande affiche le nom de l’attente.
  
```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold.Name
```

Une fois que vous avez identifié le nom du cas eDiscovery et la mise en attente, allez sur la page **eDiscovery eDiscovery** dans le centre de conformité, ouvrez le cas et supprimez la boîte aux lettres de la mise en \>  attente. Pour plus d’informations sur l’identification des mises en attente eDiscovery, voir la section « eDiscovery holds » dans [How to identify the type of hold placed on an Exchange Online mailbox](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds).
  
## <a name="step-4-remove-the-delay-hold-from-the-mailbox"></a>Étape 4 : Supprimer le délai d’attente de la boîte aux lettres

Une fois qu’un type de mise en attente est supprimé d’une boîte aux lettres, la valeur de la propriété de boîte aux lettres *DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True**. Cela se produit la prochaine fois que l’Assistant Dossier géré traite la boîte aux lettres et détecte qu’une attente a été supprimée. Cela s’appelle une attente différée et signifie que la suppression réelle de la boîte aux lettres est retardée de 30 jours pour empêcher la suppression définitive des données de la boîte aux lettres.  (L’objectif d’un report est de donner aux administrateurs la possibilité de rechercher ou de récupérer des éléments de boîte aux lettres qui seront purgés après la suppression d’une attente.)  Lorsqu’un délai d’attente est placé sur la boîte aux lettres, la boîte aux lettres est toujours considérée comme étant en attente pour une durée illimitée, comme si la boîte aux lettres était en attente pour litige. Au bout de 30 jours, le délai d’attente expire et Microsoft 365 tente automatiquement de supprimer le délai d’attente (en fixant la propriété *DelayHoldApplied* ou *DelayReleaseHoldApplied* sur **False)** afin que la mise en attente soit supprimée. Pour plus d’informations sur un délai d’attente, consultez la section « Gestion des boîtes aux lettres en attente » dans comment identifier le type de mise en attente placée sur une boîte aux lettres [Exchange Online de messagerie.](identify-a-hold-on-an-exchange-online-mailbox.md#managing-mailboxes-on-delay-hold)

Si la valeur de la *propriété DelayHoldApplied* ou *DelayReleaseHoldApplied* est définie sur **True,** exécutez l’une des commandes suivantes pour supprimer la mise en attente différée :

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Ou

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

Vous devez avoir le rôle de Exchange Online pour utiliser le paramètre *RemoveDelayHoldApplied* ou *RemoveDelayReleaseHoldApplied.*

## <a name="step-5-delete-items-in-the-recoverable-items-folder"></a>Étape 5 : Supprimer des éléments dans le dossier Éléments récupérables

Vous êtes maintenant prêt à supprimer des éléments dans le dossier Éléments récupérables à l’aide des cmdlets [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) et [New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) dans le Centre de sécurité & conformité PowerShell.

Pour rechercher des éléments situés dans le dossier Éléments récupérables, nous vous recommandons d’effectuer une *collection ciblée.* Cela signifie que vous limitez l’étendue de votre recherche uniquement aux éléments situés dans le dossier Éléments récupérables. Pour ce faire, exécutez le script dans l’article Utiliser la recherche de contenu [pour les collections ciblées.](use-content-search-for-targeted-collections.md) Ce script renvoie la valeur de la propriété d’ID de dossier pour tous les sous-dossiers du dossier Éléments récupérables cible. Ensuite, vous utilisez l’ID de dossier dans une requête de recherche pour renvoyer les éléments situés dans ce dossier.

Voici une vue d’ensemble du processus de recherche et de suppression d’éléments dans le dossier Éléments récupérables d’un utilisateur :

1. Exécutez le script de collecte ciblée qui renvoie les ID de dossier pour tous les dossiers de la boîte aux lettres de l’utilisateur cible. Le script se connecte à Exchange Online PowerShell et sécurité & conformité PowerShell dans la même session PowerShell. Pour plus d’informations, [voir Exécuter le script pour obtenir la liste des dossiers d’une boîte aux lettres.](use-content-search-for-targeted-collections.md#step-1-run-the-script-to-get-a-list-of-folders-for-a-mailbox-or-site)

2. Copiez les ID de dossier pour tous les sous-dossiers du dossier Éléments récupérables. Vous pouvez également rediriger la sortie du script vers un fichier texte.

   Voici une liste et une description des sous-dossiers du dossier Éléments récupérables à partir des éléments que vous pouvez rechercher et supprimer :

   - **Suppressions :** contient les éléments supprimés (supprimés( ou supprimés) dont la période de rétention des éléments supprimés n’a pas expiré. Les utilisateurs peuvent récupérer des éléments supprimés (récupérables) à partir de ce sous-Outlook.

   - **Purges :** contient les éléments supprimés définitivement dont la période de rétention des éléments supprimés a expiré. Les utilisateurs peuvent également supprimer définitivement des éléments en purgeant les éléments de leur dossier Éléments récupérables. Si la boîte aux lettres est en conservation, les éléments supprimés définitivement sont conservés. Ce sous-folder n’est pas visible pour les utilisateurs finaux.

   - **DiscoveryHolds**: contient les éléments supprimés définitivement qui ont été conservés par une conservation eDiscovery ou une stratégie de rétention. Ce sous-folder n’est pas visible pour les utilisateurs finaux.

   - **SubstrateHolds**: contient des éléments supprimés définitivement de Teams et d’autres applications basées sur le cloud qui ont été conservées par une stratégie de rétention ou tout autre type de conservation. Ce sous-folder n’est pas visible pour les utilisateurs finaux.

3. Utilisez la cmdlet **New-ComplianceSearch** (dans le Centre de sécurité & conformité PowerShell) ou utilisez l’outil de recherche de contenu dans le centre de conformité pour créer une recherche de contenu qui renvoie des éléments à partir du dossier Éléments récupérables de l’utilisateur cible. Pour ce faire, vous pouvez inclure folderId dans la requête de recherche pour tous les sous-dossiers que vous souhaitez rechercher. Par exemple, la requête suivante renvoie tous les messages dans les sous-folds Purges et eDiscoveryHolds :

   ```text
   folderid:<folder ID of Purges subfolder> OR folderid:<folder ID of DiscoveryHolds subfolder>
   ```

   Pour plus d’informations et des exemples sur l’exécution de recherches de contenu qui utilisent la propriété d’ID de dossier, voir Utiliser un ID de dossier ou pour [effectuer une collection ciblée.](use-content-search-for-targeted-collections.md#step-2-use-a-folder-id-or-documentlink-to-perform-a-targeted-collection)

   > [!NOTE]
   > Si vous utilisez la cmdlet **New-ComplianceSearch** pour effectuer une recherche dans le dossier Éléments récupérables, n’oubliez pas d’utiliser la cmdlet **Start-ComplianceSearch** pour exécuter la recherche.

4. Après avoir créé une recherche de contenu et validé qu’elle renvoie les éléments que vous souhaitez supprimer, utilisez la commande (dans le Centre de sécurité & conformité PowerShell) pour supprimer définitivement les éléments renvoyés par la recherche de contenu que vous avez créée à l’étape `New-ComplianceSearchAction -Purge -PurgeType HardDelete` précédente. Par exemple, vous pouvez exécuter une commande semblable à la commande suivante :

   ```powershell
   New-ComplianceSearchAction -SearchName "RecoverableItems" -Purge -PurgeType HardDelete
   ```

5. Un maximum de 10 éléments par boîte aux lettres sont supprimés lorsque vous exécutez la commande précédente. Cela signifie que vous de devez exécuter la commande plusieurs fois pour supprimer tous les éléments que vous souhaitez supprimer dans le dossier `New-ComplianceSearchAction -Purge` Éléments récupérables. Pour supprimer des éléments supplémentaires, vous devez d’abord supprimer l’action précédente de purge de la recherche de conformité. Pour ce faire, exécutez `Remove-ComplianceSearchAction` l’cmdlet. Par exemple, pour supprimer l’action de purge qui a été exécuté à l’étape précédente, exécutez la commande suivante :

   ```powershell
   Remove-ComplianceSearchAction "RecoverableItems_Purge"
   ```

   Après cela, vous pouvez créer une action de purge de la recherche de conformité pour supprimer d’autres éléments. Vous devez supprimer chaque action de purge avant d’en créer une nouvelle.

   Pour obtenir la liste des actions de recherche de conformité, vous pouvez exécuter la `Get-ComplianceSearchAction` cmdlet. Les actions de purge sont `_Purge` identifiées par l’application au nom de la recherche.

### <a name="verify-that-items-were-deleted"></a>Vérifier que les éléments ont été supprimés

Pour vérifier que vous avez correctement supprimé des éléments du dossier Éléments récupérables d’une boîte aux lettres, utilisez la cmdlet **Get-MailboxFolderStatistics** dans Exchange Online PowerShell pour vérifier la taille et le nombre d’éléments dans le dossier Éléments récupérables. Vous pouvez comparer ces statistiques à celles que vous avez collectées à l’étape 1.
  
Exécutez la commande suivante pour obtenir la taille actuelle et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables de la boîte aux lettres principale de l’utilisateur.
  
```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

Exécutez la commande suivante pour obtenir la taille et le nombre total d’éléments dans les dossiers et sous-dossiers du dossier Éléments récupérables de la boîte aux lettres d’archivage de l’utilisateur.

```powershell
Get-MailboxFolderStatistics <username> -FolderScope RecoverableItems -Archive | FL Name,FolderAndSubfolderSize,ItemsInFolderAndSubfolders
```

## <a name="step-6-revert-the-mailbox-to-its-previous-state"></a>Étape 6 : Revenir à l’état précédent de la boîte aux lettres

La dernière étape consiste à revenir à la configuration précédente de la boîte aux lettres. Cela implique de réinitialiser les propriétés que vous avez modifiées à l’étape 2 et de réappliquer les maintiens que vous avez supprimés à l’étape 3. Cela inclut les opérations suivantes :
  
- Modification de la période de rétention des éléments supprimés à sa valeur précédente. Vous pouvez également laisser cette valeur définie sur 30 jours, la valeur maximale en Exchange Online.

- Réactiver la récupération d’élément unique.

- Réactiver les méthodes d’accès client afin que le propriétaire puisse accéder à sa boîte aux lettres.

- Réappliquer les conservations et les stratégies de rétention que vous avez supprimées.

- Réactiver l’Assistant Dossier géré pour traiter la boîte aux lettres.

> [!IMPORTANT]
> Nous vous recommandons d’attendre 24 heures après avoir ré-appliqué une stratégie de conservation ou de rétention (et vérifié qu’elle est en place) avant de ré-activer l’Assistant Dossier géré pour traiter la boîte aux lettres.
  
Effectuez les étapes suivantes (dans la séquence spécifiée) dans Exchange Online PowerShell.
  
1. Exécutez la commande suivante pour revenir à la période de rétention des éléments supprimés à sa valeur d’origine. Cela suppose que le paramètre précédent est inférieur à 30 jours ; par exemple, 14 jours.

    ```powershell
    Set-Mailbox <username> -RetainDeletedItemsFor 14
    ```

2. Exécutez la commande suivante pour activer à nouveau la récupération d’élément unique.

    ```powershell
    Set-Mailbox <username> -SingleItemRecoveryEnabled $true
    ```

3. Exécutez la commande suivante pour ré-activer toutes les méthodes d’accès client à la boîte aux lettres.

    ```powershell
    Set-CASMailbox <username> -EwsEnabled $true -ActiveSyncEnabled $true -MAPIEnabled $true -OWAEnabled $true -ImapEnabled $true -PopEnabled $true
    ```

4. Réappliquez les holds que vous avez supprimés à l’étape 3. Selon le type d’attente, utilisez l’une des procédures suivantes.

    **Conservation pour litige**

    Exécutez la commande suivante pour activer à nouveau une boîte aux lettres en attente pour litige.

    ```powershell
    Set-Mailbox <username> -LitigationHoldEnabled $true
    ```

    **In-Place Hold**

    Utilisez le EAC (ou Exchange Online PowerShell) pour rajouter la boîte aux lettres au In-Place de la boîte aux lettres.

    **Stratégies de rétention appliquées à des boîtes aux lettres spécifiques**

    Utilisez le Centre de conformité Microsoft 365 pour rajouter la boîte aux lettres à la stratégie de rétention. Go to the **Information governance**  >  **Retention** page in the compliance center, edit the retention policy, and add the mailbox back to the list of recipients that the retention policy is applied to.

    **Stratégies de rétention à l’échelle de l’organisation**

    Si vous avez supprimé une stratégie de rétention à l’échelle de l’organisation ou de l’Exchange en l’excluant de la stratégie, utilisez le Centre de conformité Microsoft 365 pour supprimer la boîte aux lettres de la liste des utilisateurs exclus. Go to the **Information governance**  >  **Retention** page in the compliance center, edit the organization-wide retention policy, and remove the mailbox from the list of excluded recipients. Cela réapplique la stratégie de rétention à la boîte aux lettres de l’utilisateur.

    **Cas eDiscovery**

    Utilisez le Centre de conformité Microsoft 365 pour rajouter la boîte aux lettres à la boîte aux lettres associée à un cas eDiscovery. Go to the **eDiscovery**  >  **Core** page, open the case, and add the mailbox back to the hold. 

5. Exécutez la commande suivante pour autoriser l’Assistant Dossier géré à traiter à nouveau la boîte aux lettres. Comme indiqué précédemment, nous vous recommandons d’attendre 24 heures après la réappliquer une stratégie de conservation ou de rétention (et vérifier qu’elle est en place) avant de ré-activer l’Assistant Dossier géré.

    ```powershell
    Set-Mailbox <username> -ElcProcessingDisabled $false
    ```

6. Pour vérifier que la boîte aux lettres a été revenir à sa configuration précédente, vous pouvez exécuter les commandes suivantes, puis comparer les paramètres à ceux que vous avez collectés à l’étape 1.

    ```powershell
    Get-Mailbox <username> | FL ElcProcessingDisabled,InPlaceHolds,LitigationHoldEnabled,RetainDeletedItemsFor,SingleItemRecoveryEnabled
    ```

    ```powershell
    Get-CASMailbox <username> | FL EwsEnabled,ActiveSyncEnabled,MAPIEnabled,OWAEnabled,ImapEnabled,PopEnabled
    ```

## <a name="more-information"></a>Plus d’informations

Voici un tableau qui décrit comment identifier différents types de boîtes aux lettres en fonction des valeurs de la propriété *InPlaceHolds* lorsque vous exécutez les cmdlets **Get-Mailbox** ou **Get-OrganizationConfig.** Pour plus d’informations, voir Comment identifier le type de mise en attente placée sur [Exchange Online boîte aux lettres.](identify-a-hold-on-an-exchange-online-mailbox.md)

Comme indiqué précédemment, vous devez supprimer toutes les conservations et stratégies de rétention d’une boîte aux lettres avant de pouvoir supprimer des éléments dans le dossier Éléments récupérables.
  
| Type de conservation | Exemple de valeur | Comment identifier le hold |
|:-----|:-----|:-----|
|Conservation pour litige  <br/> | `True` <br/> |La propriété  *LitigationHoldEnabled*  est définie sur  `True`.  <br/> |
|Blocage local  <br/> | `c0ba3ce811b6432a8751430937152491` <br/> |La  *propriété InPlaceHolds*  contient le GUID de la In-Place qui est placée sur la boîte aux lettres. Vous pouvez savoir qu’il s’agit d’une In-Place car le GUID ne commence pas par un préfixe.  <br/> Vous pouvez utiliser la commande dans Exchange Online PowerShell pour obtenir des informations sur la In-Place `Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL` de la boîte aux lettres.  <br/> |
| Stratégies de rétention dans le Centre de conformité Microsoft 365 appliquées à des boîtes aux lettres spécifiques  <br/> | `mbxcdbbb86ce60342489bff371876e7f224` <br/> ou  <br/>  `skp127d7cf1076947929bf136b7a2a8c36f` <br/> |Lorsque vous exécutez la cmdlet **Get-Mailbox,** la  *propriété InPlaceHolds*  contient également les GUID des stratégies de rétention appliquées à la boîte aux lettres. Vous pouvez identifier les stratégies de rétention car le GUID commence par  `mbx` le préfixe. Si le GUID de la stratégie de rétention commence par le préfixe, cela indique que la stratégie de rétention est appliquée `skp` à Skype Entreprise conversations.  <br/> Pour identifier la stratégie de rétention appliquée à la boîte aux lettres, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell : <br/> <br/>`Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>N'oubliez pas de supprimer le préfixe  `mbx` ou  `skp` lorsque vous exécutez cette commande.  <br/> |
|Stratégies de rétention à l’échelle de l’Centre de conformité Microsoft 365  <br/> |Aucune valeur  <br/> ou  <br/>  `-mbxe9b52bf7ab3b46a286308ecb29624696` (indique que la boîte aux lettres est exclue d’une stratégie à l’échelle de l’organisation)  <br/> |Même si la propriété  *InPlaceHolds*  est vide lorsque vous exécutez la cmdlet **Get-Mailbox,** il se peut qu’une ou plusieurs stratégies de rétention à l’échelle de l’organisation soient appliquées à la boîte aux lettres.  <br/> Pour vérifier cela, vous pouvez exécuter la commande dans Exchange Online PowerShell pour obtenir la liste des GUID pour les stratégies de rétention à l’échelle de `Get-OrganizationConfig | FL InPlaceHolds` l’organisation. Le GUID des stratégies de rétention à l’échelle de l’organisation appliquées Exchange boîtes aux lettres commence par le `mbx` préfixe ; par exemple, `mbxa3056bb15562480fadb46ce523ff7b02` .  <br/> Pour identifier la stratégie de rétention à l’échelle de l’organisation qui est appliquée à la boîte aux lettres, exécutez la commande suivante dans le Centre de sécurité & conformité PowerShell : <br/><br/> `Get-RetentionCompliancePolicy <retention policy GUID without prefix> | FL Name`<br/><br/>Si une boîte aux lettres est exclue d’une stratégie de rétention à l’échelle de l’organisation, le GUID de la stratégie de rétention s’affiche dans la propriété  *InPlaceHolds*  de la boîte aux lettres de l’utilisateur lorsque vous exécutez la cmdlet **Get-Mailbox** . il est identifié par le préfixe  `-mbx` ; par exemple,  `-mbxe9b52bf7ab3b46a286308ecb29624696` <br/> |
|Cas eDiscovery dans la Centre de conformité Microsoft 365  <br/> | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d` <br/> |La *propriété InPlaceHolds* contient également le GUID de toute mise en attente associée à un cas eDiscovery dans le Centre de conformité Microsoft 365 qui peut être placé sur la boîte aux lettres. Vous pouvez déterminer qu'il s'agit d'une mise en conservation de cas eDiscovery, car le GUID commence par le préfixe  `UniH`.  <br/> Vous pouvez utiliser la cmdlet dans le Centre de sécurité & conformité PowerShell pour obtenir des informations sur le cas eDiscovery associé à la mise en attente sur la boîte aux  `Get-CaseHoldPolicy` lettres. Par exemple, vous pouvez exécuter la commande pour afficher le nom de la boîte aux lettres de la boîte  `Get-CaseHoldPolicy <hold GUID without prefix> | FL Name` aux lettres. Be sure to remove the  `UniH` lorsque vous exécutez cette commande.  <br/><br/> Pour identifier le cas eDiscovery associé à la boîte aux lettres, exécutez les commandes suivantes :<br/><br/>`$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>`<br/><br/>`Get-ComplianceCase $CaseHold.CaseId | FL Name`
