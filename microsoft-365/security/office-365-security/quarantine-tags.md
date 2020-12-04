---
title: Balises de mise en quarantaine
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Les administrateurs peuvent apprendre à utiliser les balises de mise en quarantaine pour contrôler ce que les utilisateurs peuvent faire à leurs messages mis en quarantaine.
ms.openlocfilehash: 68f28e2dff3bdeada2685ef6806489f5e57f5daf
ms.sourcegitcommit: d81c7cea85af6ad5fef81d3c930514a51464368c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "49572668"
---
# <a name="quarantine-tags"></a>Balises de mise en quarantaine

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont actuellement en version préliminaire, ne sont pas disponibles pour tous les utilisateurs et peuvent faire l’objet de modifications.

Les balises de mise en quarantaine dans Exchange Online Protection (EOP) permettent aux administrateurs de contrôler ce que les utilisateurs peuvent faire de leurs messages mis en quarantaine en fonction de la mise en quarantaine du message.

EOP a traditionnellement autorisé ou empêché certains niveaux d’interactivité pour les messages en [quarantaine](find-and-release-quarantined-messages-as-a-user.md) et dans les [notifications de courrier indésirable pour l’utilisateur final](use-spam-notifications-to-release-and-report-quarantined-messages.md). Par exemple, les utilisateurs finaux peuvent afficher et libérer les messages qui ont été mis en quarantaine par le filtrage du courrier indésirable en tant que courrier indésirable ou en bloc, mais ils ne peuvent pas afficher ou libérer les messages mis en quarantaine en tant que phishing à haut niveau de fiabilité.

Pour les [fonctionnalités de protection prises en charge](#step-2-assign-a-quarantine-tag-to-supported-features), les balises de mise en quarantaine spécifient ce que les utilisateurs sont autorisés à faire dans les messages de notification de courrier indésirable de l’utilisateur final et dans les messages mis en quarantaine (messages dans lesquels l’utilisateur est un destinataire). Les balises de mise en quarantaine par défaut sont automatiquement attribuées pour appliquer les fonctionnalités d’historique pour les utilisateurs finaux sur les messages mis en quarantaine. Vous pouvez créer et affecter des balises de mise en quarantaine personnalisées pour autoriser ou empêcher les utilisateurs finals d’effectuer des actions spécifiques sur les messages mis en quarantaine.

Les autorisations individuelles sont combinées dans les groupes d’autorisations prédéfinis suivants :

- Pas d’accès
- Accès limité
- Accès total

Les autorisations individuelles disponibles et ce qui est inclus ou non dans les groupes d’autorisations prédéfinis sont décrits dans le tableau suivant :

|Autorisation|Pas d’accès|Accès limité|Accès total|
|---|:---:|:---:|:---:|
|**Autoriser l’expéditeur** (_PermissionToAllowSender_)|||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**Bloquer l’expéditeur** (_PermissionToBlockSender_)||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**Supprimer** (_PermissionToDelete_)||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**Aperçu** (_PermissionToPreview_)||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**Autoriser les destinataires à libérer un message en quarantaine** (_PermissionToRelease_)|||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
|**Autoriser les destinataires à demander la libération d’un message en quarantaine** (_PermissionToRequestRelease_)||![Coche](../../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
|

Si vous n’aimez pas les autorisations par défaut dans les groupes d’autorisations prédéfinis, vous pouvez utiliser des autorisations personnalisées lors de la création ou de la modification de balises de mise en quarantaine personnalisées. Pour plus d’informations sur ce que fait chaque autorisation, voir la section Détails de l' [autorisation de mise en quarantaine](#quarantine-tag-permission-details) plus loin dans cet article.

Vous créez et attribuez des balises de mise en quarantaine dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online ; environnement EOP autonome dans les organisations EOP sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **balises de quarantaine** , ouvrez <https://protection.office.com/quarantineTags> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour afficher, créer, modifier ou supprimer des balises de mise en quarantaine, vous devez être membre des rôles de gestion de l' **organisation** ou d' **administrateur de sécurité** dans le centre de [sécurité & conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="step-1-create-quarantine-tags-in-the-security--compliance-center"></a>Étape 1 : créer des balises de mise en quarantaine dans le centre de sécurité & conformité

1. Dans le centre de sécurité & conformité, accédez à stratégie de **gestion des menaces** , \> **Policy** puis sélectionnez **balises de mise en quarantaine**.

2. Sur la page **balises de quarantaine** , sélectionnez **Ajouter une balise personnalisée**.

3. L’Assistant **nouvelle balise** s’ouvre. Dans la page nom de la **balise** , entrez un bref nom unique dans le champ nom de la **balise** . Vous devrez identifier et sélectionner la balise par nom dans les étapes à venir. Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Sur la page **accès aux messages des destinataires** , sélectionnez l’une des valeurs suivantes :
   - **Aucun accès**
   - **Accès limité**
   - **Accès total**

   Les autorisations individuelles qui sont incluses dans ces groupes d’autorisations sont décrites plus haut dans cet article.

   Pour spécifier des autorisations personnalisées, sélectionnez **définir un accès spécifique (avancé)** et configurez les paramètres suivants :

     - **Sélectionnez la préférence** de l’action de publication : sélectionnez l’une des valeurs suivantes :
       - **Aucune action de libération**: il s’agit de la valeur par défaut.
       - **Autoriser les destinataires à diffuser un message en quarantaine**
       - **Autoriser les destinataires à demander la libération d’un message en quarantaine**

     - **Sélectionnez les actions supplémentaires que les destinataires peuvent effectuer sur les messages mis en quarantaine**: sélectionnez certaines, toutes ou aucune des valeurs suivantes :
       - **Supprimer**
       - **Aperçu**
       - **Autoriser l’expéditeur**
       - **Bloquer l’expéditeur**

   Ces autorisations et leur effet sur les messages mis en quarantaine et les notifications de courrier indésirable de l’utilisateur final sont décrits dans la section Détails des autorisations de la [balise de mise en quarantaine](#quarantine-tag-permission-details) plus loin dans cet article.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur la page **récapitulative** qui s’affiche, vérifiez vos paramètres. Vous pouvez cliquer sur **modifier** sur chaque paramètre pour le modifier.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

6. Cliquez sur **OK** dans la page de confirmation qui s’affiche.

Vous êtes maintenant prêt à affecter la balise de mise en quarantaine à une fonctionnalité de mise en quarantaine, comme décrit dans la section [étape 2](#step-2-assign-a-quarantine-tag-to-supported-features) .

### <a name="create-quarantine-tags-in-powershell"></a>Créer des balises de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour créer des balises de mise en quarantaine, connectez-vous à Exchange Online PowerShell ou à Exchange Online Protection PowerShell et utilisez la cmdlet **New-QuarantineTag** . Vous avez le choix entre deux méthodes :

- Utilisez le paramètre _EndUserQuarantinePermissionsValue_ .
- Utilisez le paramètre _EndUserQuarantinePermissions_ .

Ces méthodes sont décrites dans les sections suivantes.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Utiliser le paramètre EndUserQuarantinePermissionsValue

Pour créer une balise de mise en quarantaine à l’aide du paramètre _EndUserQuarantinePermissionsValue_ , utilisez la syntaxe suivante :

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236>
```

Le paramètre _EndUserQuarantinePermissionsValue_ utilise une valeur décimale qui est convertie à partir d’une valeur binaire. La valeur binaire correspond aux autorisations de mise en quarantaine de l’utilisateur final disponibles dans un ordre spécifique. Pour chaque autorisation, la valeur 1 est égale à true et la valeur 0 équivaut à false.

L’ordre et les valeurs requis pour chaque autorisation individuelle dans des groupes d’autorisations prédéfinis sont décrits dans le tableau suivant :

****

|Autorisation|Pas d’accès|Accès limité|Accès total|
|---|:---:|:---:|:---:|
|PermissionToAllowSender|0|0|1 |
|PermissionToBlockSender|0|1 |1 |
|PermissionToDelete|0|1 |1 |
|PermissionToDownload<sup>\*</sup>|0|0|0|
|PermissionToPreview|0|1 |1 |
|PermissionToRelease<sup>\*\*</sup>|0|0|1 |
|PermissionToRequestRelease<sup>\*\*</sup>|0|1 |0|
|PermissionToViewHeader<sup>\*</sup>|0|0|0|
|Valeur binaire|00000000|01101010|11101100|
|Valeur décimale à utiliser|0|106|236|

<sup>\*</sup> Actuellement, cette valeur est toujours 0. Pour PermissionToViewHeader, la valeur 0 ne masque pas le bouton d' **en-tête afficher le message** dans les détails du message en quarantaine (le bouton est toujours disponible).

<sup>\*\*</sup> Ne définissez pas ces deux valeurs sur 1. Définissez un sur 1 et l’autre sur 0, ou définissez-les deux sur 0.

Cet exemple montre comment créer un nom de balise de mise en quarantaine NoAccess qui affecte les autorisations sans accès comme décrit dans le tableau précédent.

```powershell
New-QuarantineTag -Name NoAccess -EndUserQuarantinePermissionsValue 0
```

Pour les autorisations d’accès limité, utilisez la valeur 106. Pour les autorisations d’accès total, utilisez la valeur 236.

Pour les autorisations personnalisées, utilisez le tableau précédent pour obtenir la valeur binaire correspondant aux autorisations de votre choix. Convertissez la valeur binaire en une valeur décimale et utilisez la valeur décimale pour le paramètre _EndUserQuarantinePermissionsValue_ .

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-QuarantineTag](https://docs.microsoft.com/powershell/module/exchange/new-quarantinetag).

#### <a name="use-the-enduserquarantinepermissions-parameter"></a>Utiliser le paramètre EndUserQuarantinePermissions

Pour créer une balise de mise en quarantaine à l’aide du paramètre _EndUserQuarantinePermissionsValue_ , procédez comme suit :

A. Stockez un objet d’autorisations de mise en quarantaine dans une variable à l’aide de la cmdlet **New-QuarantinePermissions** .
<br/>
B. Utilisez la variable comme valeur _EndUserQuarantinePermissions_ dans la commande **New-QuarantineTag** .

##### <a name="step-a-store-a-quarantine-permissions-object-in-a-variable"></a>Étape A : stocker un objet d’autorisations de mise en quarantaine dans une variable

Utilisez la syntaxe suivante :

```powershell
$<VariableName> = New-QuarantinePermissions [-PermissionToAllowSender <$true | $False>] [-PermissionToBlockSender <$true | $False>] [-PermissionToDelete <$true | $False>] [-PermissionToPreview <$true | $False>] [-PermissionToRelease <$true | $False>] [-PermissionToRequestRelease <$true | $False>]
```

La valeur par défaut des paramètres inutilisés est `$false` , de sorte que vous devez uniquement utiliser les paramètres pour lesquels vous souhaitez définir la valeur `$true` .

Les exemples suivants montrent comment créer des objets permission qui correspondent aux groupes d’autorisations prédéfinis :

- **Aucun accès**:

  ```powershell
  $NoAccess = New-QuarantinePermissions
  ```

- **Accès limité**:

  ```powershell
  $LimitedAccess = New-QuarantinePermissions -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRequestRelease $true
  ```

- **Accès total**:

  ```powershell
  $FullAccess = New-QuarantinePermissions -PermissionToAllowSender $true -PermissionToBlockSender $true -PermissionToDelete $true -PermissionToPreview $true -PermissionToRelease $true
  ```

Pour afficher les valeurs que vous avez définies, exécutez le nom de la variable en tant que commande (par exemple, exécutez la commande `$NoAccess` ).

Pour les autorisations personnalisées, ne définissez pas les paramètres _PermissionToRelease_ et _PermissionToRequestRelease_ sur `$true` . Définissez un comme `$true` et laissez le reste `$false` , ou laissez les deux en tant que `$false` .

Vous pouvez également modifier une variable d’objet d’autorisations existante après avoir créé mais avant de l’utiliser à l’aide de la cmdlet **Set-QuarantinePermissions** .

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-QuarantinePermissions](https://docs.microsoft.com/powershell/module/exchange/new-quarantinepermissions) et [Set-QuarantinePermissions](https://docs.microsoft.com/powershell/module/exchange/set-quarantinepermissions).

##### <a name="step-b-use-the-variable-in-the-new-quarantinetag-command"></a>Étape B : utiliser la variable dans la commande New-QuarantineTag

Une fois que vous avez créé et stocké l’objet permissions dans une variable, utilisez la variable pour la valeur du paramètre _EndUserQuarantinePermission_ dans la commande **New-QuarantineTag** suivante :

```powershell
New-QuarantineTag -Name "<UniqueName>" -EndUserQuarantinePermissions $<VariableName>
```

Cet exemple crée une nouvelle balise de mise en quarantaine nommée LimitedAccess à l’aide de l' `$LimitedAccess` objet permissions qui a été décrit et créé à l’étape précédente.

```powershell
New-QuarantineTag -Name LimitedAccess -EndUserQuarantinePermissions $LimitedAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-QuarantineTag](https://docs.microsoft.com/powershell/module/exchange/new-quarantinetag).

## <a name="step-2-assign-a-quarantine-tag-to-supported-features"></a>Étape 2 : affecter une balise de mise en quarantaine aux fonctionnalités prises en charge

Dans les fonctionnalités de protection _prises en charge_ qui met en quarantaine les messages ou les fichiers (automatiquement ou en tant qu’une action configurable), vous pouvez affecter une balise de mise en quarantaine aux actions de mise en quarantaine disponibles. Les fonctionnalités de mise en quarantaine des messages et la disponibilité des balises de mise en quarantaine sont décrites dans le tableau suivant :

****

|Fonctionnalité|Balises de mise en quarantaine prises en charge ?|Balises de mise en quarantaine par défaut utilisées|
|---|:---:|---|
|[Stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md): <ul><li>**Courrier indésirable** (_SpamAction_)</li><li>**Courrier indésirable à niveau de confiance élevé** (_HighConfidenceSpamAction_)</li><li>**Courrier électronique de hameçonnage** (_PhishSpamAction_)</li><li>**Courrier électronique de hameçonnage à haute fiabilité** (_HighConfidencePhishAction_)</li><li>**Courrier en masse** (_BulkSpamAction_)</li></ul>|Oui|<ul><li>DefaultSpamTag (accès total)</li><li>DefaultHighConfSpamTag (accès total)</li><li>DefaultPhishTag (accès total)</li><li>DefaultHighConfPhishTag (pas d’accès)</li><li>DefaultBulkTag (accès total)</li></ul>
|Stratégies anti-hameçonnage : <ul><li>[Protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<sup>\*</sup> <ul><li>**Si le courrier électronique est envoyé par un utilisateur emprunté** (_TargetedUserProtectionAction_)</li><li>**Si le courrier électronique est envoyé par un domaine emprunté** (_TargetedDomainProtectionAction_)</li><li>Intelligence des boîtes **aux lettres** \> **Si le courrier électronique est envoyé par un utilisateur emprunté** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul></ul>|Non|s/o|
|[Stratégies de protection contre les programmes malveillants](configure-anti-malware-policies.md): tous les messages détectés sont toujours mis en quarantaine.|Non|s/o|
|[ATP pour SharePoint, OneDrive et Microsoft Teams](atp-for-spo-odb-and-teams.md)|Non|s/o|
|Les [règles de flux de messagerie](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) avec l’action : **remet le message à la quarantaine hébergée** (_mise en quarantaine_).|Non|s/o|
|

<sup>\*</sup> Les paramètres de protection contre l’emprunt d’identité sont disponibles uniquement dans les stratégies anti-hameçonnage de Microsoft Defender pour Office 365.

Si vous êtes satisfait des autorisations de l’utilisateur final fournies par les balises de mise en quarantaine par défaut, aucune action n’est nécessaire. Si vous souhaitez personnaliser les fonctionnalités de l’utilisateur final (boutons disponibles) dans les notifications de courrier indésirable de l’utilisateur final ou les détails du message en quarantaine, vous pouvez affecter une balise de mise en quarantaine personnalisée.

### <a name="assign-quarantine-tags-in-anti-spam-policies-in-the-security--compliance-center"></a>Attribuer des balises de mise en quarantaine dans les stratégies de blocage du courrier indésirable dans le centre de sécurité & conformité

Pour plus d’informations sur la création et la modification de stratégies de blocage du courrier indésirable, voir [configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

1. Dans le centre de sécurité & conformité, accédez à stratégie de **gestion des menaces** , \> **Policy** \> puis sélectionnez **blocage du courrier indésirable**. Ou ouvrez <https://protection.office.com/antispam> .

2. Recherchez et sélectionnez une stratégie de blocage du courrier indésirable existante à modifier, ou créez une nouvelle stratégie de blocage du courrier indésirable.

3. Dans la fenêtre mobile détails de la stratégie, développez la section **actions de courrier indésirable et en bloc** .
  
4. Si vous avez sélectionné **message mis en quarantaine** pour l’action d’une option de filtrage du courrier indésirable disponible, la zone **appliquer la balise de stratégie de mise en quarantaine** est disponible pour vous permettant de sélectionner la balise de mise en quarantaine pour ce verdict.

   **Remarque**: lorsque vous créez une stratégie, une valeur de balise de mise en quarantaine vide pour un filtrage du courrier indésirable en verdict indique que la balise de mise en quarantaine par défaut pour ce verdict est utilisée. Lorsque vous modifiez ultérieurement la stratégie, les valeurs non renseignées sont remplacées par les noms de balise de mise en quarantaine par défaut réels, comme décrit dans le tableau précédent.
  
   ![Sélections de la balise de quarantaine dans une stratégie de blocage du courrier indésirable](../../media/quarantine-tags-in-anti-spam-policies.png)

5. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

#### <a name="assign-quarantine-tags-in-anti-spam-policies-in-powershell"></a>Attribuer des balises de mise en quarantaine dans les stratégies de blocage du courrier indésirable dans PowerShell

Si vous préférez utiliser PowerShell pour attribuer des balises de mise en quarantaine dans des stratégies de blocage du courrier indésirable, connectez-vous à Exchange Online PowerShell ou à Exchange Online Protection PowerShell, puis utilisez la syntaxe suivante :

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>">  [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Remarques**:

- La valeur par défaut du paramètre _HighConfidencePhishAction_ est mise en quarantaine, vous n’avez donc pas besoin de définir l’action de mise en quarantaine pour les détections de hameçonnage à haute fiabilité dans les nouvelles stratégies de blocage du courrier indésirable. Pour tous les autres filtrages de courrier indésirable en fonction des stratégies anti-courrier indésirable nouvelles ou existantes, la balise de mise en quarantaine n’est effective que si la valeur de l’action est mise en quarantaine. Pour afficher les valeurs d’action dans les stratégies anti-courrier indésirable existantes, exécutez la commande suivante :

  ```powershell
  Get-HostedContentFilterPolicy | Format-Table Name,*SpamAction,HighConfidencePhishAction
  ```

  Pour plus d’informations sur les valeurs d’action par défaut et sur les valeurs d’action recommandées pour standard et strict, voir [EOP anti-spam Policy Settings](recommended-settings-for-eop-and-office365-atp.md#eop-anti-spam-policy-settings).

- Le filtrage du courrier indésirable correspondant à un paramètre de balise de mise en quarantaine correspondant signifie que la [balise de mise en quarantaine par défaut](#step-2-assign-a-quarantine-tag-to-supported-features) pour ce verdict est utilisée.

  Vous ne devez remplacer une balise de mise en quarantaine par défaut par une balise de mise en quarantaine personnalisée que si vous souhaitez modifier les fonctionnalités de l’utilisateur final par défaut sur les messages mis en quarantaine.

- Une nouvelle stratégie de blocage du courrier indésirable dans PowerShell nécessite une stratégie de filtrage du courrier indésirable (paramètres) à l’aide de la cmdlet **New-HostedContentFilterPolicy** et une nouvelle règle de filtrage du courrier indésirable (filtres de destinataires) à l’aide de la cmdlet **New-hostedcontentfilterrule permet** . Pour obtenir des instructions, consultez la rubrique [Utiliser PowerShell pour créer des stratégies de blocage du courrier indésirable](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Cet exemple crée une nouvelle stratégie de filtrage du courrier indésirable nommée Research Department avec les paramètres suivants :

- L’action pour l’ensemble du filtrage du courrier indésirable est définie sur quarantaine.
- La balise de mise en quarantaine personnalisée nommée NoAccess qui n’affecte pas d’autorisations d' **accès** remplace les balises de mise en quarantaine par défaut qui n’assignent pas encore d’autorisations d' **accès** par défaut.

```powershell
New-HostedContentFilterPolicy -Name Research Department -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedContentFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/new-hostedcontentfilterpolicy).

Cet exemple modifie la stratégie de filtrage du courrier indésirable nommée Human Resources. L’action pour le verdict de mise en quarantaine du courrier indésirable est définie sur quarantaine et la balise de mise en quarantaine personnalisée nommée NoAccess est attribuée.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedContentFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/set-hostedcontentfilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-security--compliance-center"></a>Configurer les paramètres de notification de mise en quarantaine globale dans le centre de sécurité & conformité

Les paramètres globaux pour les balises de mise en quarantaine vous permettent de personnaliser les notifications de courrier indésirable de l’utilisateur final qui sont envoyées aux destinataires des messages mis en quarantaine. Pour plus d’informations sur ces notifications, consultez la rubrique [notifications de courrier indésirable de l’utilisateur final](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Dans le centre de sécurité & conformité, accédez à stratégie de **gestion des menaces** , \> **Policy** puis sélectionnez **balises de mise en quarantaine**.

2. Sur la page **balises de quarantaine** , sélectionnez **paramètres globaux**.

3. Dans la fenêtre mobile **paramètres de notification de mise en quarantaine** qui s’ouvre, configurez une partie ou l’ensemble des paramètres suivants :

   - **Utiliser mon logo de société**: sélectionnez cette option pour remplacer le logo Microsoft par défaut qui est utilisé en haut des notifications de courrier indésirable de l’utilisateur final. Avant cela, vous devez suivre les instructions de la procédure [personnaliser le thème Microsoft 365 de votre organisation](https://docs.microsoft.com/microsoft-365/admin/setup/customize-your-organization-theme) pour télécharger votre logo personnalisé.

     La capture d’écran suivante montre un logo personnalisé dans une notification de courrier indésirable pour l’utilisateur final :

     ![Un logo personnalisé dans une notification de courrier indésirable pour l’utilisateur final](../../media/quarantine-tags-esn-customization-logo.png)

   - **Choisir la langue**: les notifications de courrier indésirable de l’utilisateur final sont déjà localisées en fonction des paramètres de langue du destinataire. Vous pouvez spécifier un texte personnalisé dans différentes langues pour le **nom d’affichage** et les valeurs de clause d’exclusion de **responsabilité** .

     Sélectionnez au moins une langue dans la première langue, puis cliquez sur **Ajouter**. Vous pouvez sélectionner plusieurs langues en cliquant sur **Ajouter** après chacune d’elles. Une case langue de section affiche toutes les langues que vous avez sélectionnées :

     ![Langues sélectionnées dans la deuxième langue de la zone dans les paramètres de notification de mise en quarantaine globale des balises de mise en quarantaine](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **Nom d’affichage**: Personnalisez le nom d’affichage de l’expéditeur utilisé dans les notifications de courrier indésirable de l’utilisateur final.

     Pour chaque langue que vous avez ajoutée, sélectionnez la langue dans la seconde langue (ne cliquez pas sur le X) et entrez la valeur de texte souhaitée dans la zone **nom complet** .

     La capture d’écran suivante montre le nom d’affichage personnalisé dans une notification de courrier indésirable de l’utilisateur final :

     ![Nom d’affichage personnalisé de l’expéditeur dans une notification de courrier indésirable pour l’utilisateur final](../../media/quarantine-tags-esn-customization-display-name.png)

   - **Clause d’exclusion** de responsabilité : ajoutez une clause d’exclusion de responsabilité personnalisée au bas des notifications de courrier indésirable de l’utilisateur final. Le texte localisé, **une clause d’exclusion de responsabilité de votre organisation :** est toujours inclus en premier, suivi du texte que vous spécifiez.

     Pour chaque langue que vous avez ajoutée, sélectionnez la langue dans la deuxième langue (ne cliquez pas sur X) et entrez la valeur de texte souhaitée dans la zone **exclusion de responsabilité** .

     La capture d’écran suivante montre la clause d’exclusion de responsabilité personnalisée dans une notification de courrier indésirable de l’utilisateur final :

     ![Une clause d’exclusion de responsabilité personnalisée au bas d’une notification de courrier indésirable de l’utilisateur final](../../media/quarantine-tags-esn-customization-disclaimer.png)

## <a name="view-quarantine-tags-in-the-security--compliance-center"></a>Afficher les balises de mise en quarantaine dans le centre de sécurité & conformité

1. Dans le centre de sécurité & conformité, accédez à stratégie de **gestion des menaces** , \> **Policy** puis sélectionnez **balises de mise en quarantaine**.

- Pour afficher les paramètres des balises de mise en quarantaine prédéfinies ou personnalisées, sélectionnez la balise de mise en quarantaine dans la liste (n’activez pas la case à cocher).

- Pour afficher les paramètres globaux, sélectionnez **paramètres globaux** .

### <a name="view-quarantine-tags-in-powershell"></a>Afficher les balises de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour afficher les balises de mise en quarantaine, effectuez l’une des opérations suivantes :

- Pour afficher la liste récapitulative de toutes les balises prédéfinies ou personnalisées, exécutez la commande suivante :

  ```powershell
  Get-QuarantineTag | Format-Table Name
  ```

- Pour afficher les paramètres des balises de mise en quarantaine prédéfinies ou personnalisées, remplacez \<TagName\> par le nom de la balise de mise en quarantaine, puis exécutez la commande suivante :

  ```powershell
  Get-QuarantineTag -Identity "<TagName>"
  ```

- Pour afficher les paramètres globaux, exécutez la commande suivante :

  ```powershell
  Get-QuarantineTag -QuarantineTagType GlobalQuarantineTag
  ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedContentFilterPolicy](https://docs.microsoft.com/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="remove-quarantine-tags-in-the-security--compliance-center"></a>Supprimer les balises de mise en quarantaine dans le centre de sécurité & conformité

**Remarques**:

- Vous ne pouvez pas supprimer les balises de quarantaine prédéfinies.

- Avant de supprimer une balise de mise en quarantaine personnalisée, vérifiez qu’elle n’est pas utilisée. Par exemple, exécutez la commande suivante dans PowerShell :

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag
  ```

  Si la balise de mise en quarantaine est utilisée, [Remplacez la balise de mise en quarantaine affectée avant de la](#step-2-assign-a-quarantine-tag-to-supported-features) supprimer.

1. Dans le centre de sécurité & conformité, accédez à stratégie de **gestion des menaces** , \> **Policy** puis sélectionnez **balises de mise en quarantaine**.

2. Sur la page **balises de quarantaine** , sélectionnez la balise de mise en quarantaine personnalisée que vous souhaitez supprimer, puis cliquez sur **Supprimer la balise**.

3. Cliquez sur **Supprimer la balise** dans la boîte de dialogue de confirmation qui s’affiche.

### <a name="remove-quarantine-tags-in-powershell"></a>Supprimer les balises de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour supprimer une balise de mise en quarantaine personnalisée, remplacez \<TagName\> par le nom de la balise de mise en quarantaine, puis exécutez la commande suivante :

```powershell
Remove-QuarantineTag -Identity "<TagName>"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Remove-QuarantineTag](https://docs.microsoft.com/powershell/module/exchange/remove-quarantinetag).

## <a name="quarantine-tag-permission-details"></a>Détails des autorisations de la balise de mise en quarantaine

Les sections suivantes décrivent les effets des groupes d’autorisations prédéfinis et des autorisations individuelles dans les détails des messages mis en quarantaine et dans les notifications de courrier indésirable de l’utilisateur final.

### <a name="preset-permissions-groups"></a>Groupes d’autorisations prédéfinis

Les autorisations individuelles qui sont incluses dans des groupes d’autorisations prédéfinis sont répertoriées dans le tableau au début de cet article.

#### <a name="no-access"></a>Pas d’accès

Si la balise de mise en quarantaine affecte les autorisations **aucune** autorisation (aucune autorisation), les utilisateurs reçoivent toujours des fonctionnalités de ligne de base :

- **Détails du message en quarantaine**: le bouton d' **en-tête afficher le message** est toujours disponible.

  ![Boutons disponibles dans les détails du message en quarantaine si la balise de mise en quarantaine donne à l’utilisateur aucune autorisation d’accès](../../media/quarantine-tags-quarantined-message-details-no-access.png)

- **Notifications de courrier indésirable de l’utilisateur final**: le bouton **Review** qui dirige l’utilisateur vers le message en quarantaine est toujours disponible.

  ![Boutons disponibles dans la notification de courrier indésirable de l’utilisateur final si la balise de mise en quarantaine donne à l’utilisateur aucune autorisation d’accès](../../media/quarantine-tags-esn-no-access.png)

#### <a name="limited-access"></a>Accès limité

Si la balise de mise en quarantaine affecte les autorisations d' **accès limitées** , les utilisateurs obtiennent les fonctionnalités suivantes :

- **Détails du message en quarantaine**: les boutons suivants sont disponibles :
  - **Version de la demande**
  - **Afficher l’en-tête du message**
  - **Aperçu du message**
  - **Bloquer l’expéditeur**
  - **Supprimer de la quarantaine**

  ![Boutons disponibles dans les détails du message en quarantaine si la balise de mise en quarantaine accorde aux utilisateurs des autorisations d’accès limitées](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **Notifications de courrier indésirable de l’utilisateur final**: les boutons suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Révision**

  ![Boutons disponibles dans la notification de courrier indésirable de l’utilisateur final si la balise de mise en quarantaine accorde aux utilisateurs des autorisations d’accès limitées](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>Accès total

Si la balise de mise en quarantaine affecte les autorisations d' **accès total** (toutes les autorisations disponibles), les utilisateurs bénéficient des fonctionnalités suivantes :

- **Détails du message en quarantaine**: les boutons suivants sont disponibles :
  - **Message de publication**
  - **Afficher l’en-tête du message**
  - **Aperçu du message**
  - **Bloquer l’expéditeur**
  - **Autoriser l’expéditeur**
  - **Supprimer de la quarantaine**

  ![Boutons disponibles dans les détails du message en quarantaine si la balise de mise en quarantaine accorde à l’utilisateur les autorisations d’accès total](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **Notifications de courrier indésirable de l’utilisateur final**: les boutons suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Version**
  - **Révision**

  ![Boutons disponibles dans la notification de courrier indésirable de l’utilisateur final si la balise de mise en quarantaine accorde à l’utilisateur les autorisations d’accès total](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>Autorisations individuelles

> [!NOTE]
> N’oubliez pas que les utilisateurs reçoivent toujours les boutons décrits dans la section [pas d’accès](#no-access) . Ces boutons ne sont pas inclus dans les descriptions d’autorisation individuelles.

#### <a name="allow-sender-permission"></a>Autorisation de l’expéditeur

L’autorisation **autoriser l’expéditeur** (_PermissionToAllowSender_) contrôle l’accès au bouton qui permet aux utilisateurs d’ajouter facilement l’expéditeur du message en quarantaine à leur liste des expéditeurs approuvés.

- **Détails du message en quarantaine**:
  - **Autoriser** l’autorisation de l’expéditeur activé : le bouton **autoriser l’expéditeur** est disponible.
  - **Autoriser l’expéditeur** désactivé : le bouton **autoriser l’expéditeur** n’est pas disponible.

- **Notifications de courrier indésirable de l’utilisateur final**: aucun effet.

Pour plus d’informations sur la liste des expéditeurs approuvés, voir [empêcher le blocage des expéditeurs approuvés](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379666) et [utiliser Exchange Online PowerShell pour configurer la collection de listes fiables sur une boîte aux lettres](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="block-sender-permission"></a>Autorisation bloquer l’expéditeur

L’autorisation **proscrire l’expéditeur** (_PermissionToBlockSender_) contrôle l’accès au bouton qui permet aux utilisateurs d’ajouter facilement l’expéditeur du message en quarantaine à la liste des expéditeurs bloqués.

- **Détails du message en quarantaine**:
  - Autorisation de blocage de l' **expéditeur** activée : le bouton **bloquer l’expéditeur** est disponible.
  - Autorisation de blocage de l' **expéditeur** désactivée : le bouton **bloquer l’expéditeur** n’est pas disponible.

- **Notifications de courrier indésirable de l’utilisateur final**:
  - Autorisation de blocage de l' **expéditeur** désactivée : le bouton **bloquer l’expéditeur** n’est pas disponible.
  - Autorisation de blocage de l' **expéditeur** activée : le bouton **bloquer l’expéditeur** est disponible.

Pour plus d’informations sur la liste des expéditeurs bloqués, voir [bloquer les messages de quelqu’un](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) et [utiliser Exchange Online PowerShell pour configurer la collection de listes fiables sur une boîte aux lettres](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Supprimer une autorisation

L’autorisation de **suppression** (_PermissionToDelete_) contrôle la possibilité pour les utilisateurs de supprimer leurs messages (messages dans lesquels l’utilisateur est un destinataire) de la mise en quarantaine.

- **Détails du message en quarantaine**:
  - Autorisation de **suppression** activée : le bouton **supprimer de la quarantaine** est disponible.
  - Autorisation de **suppression** désactivée : le bouton **supprimer du contrôle** n’est pas disponible.

- **Notifications de courrier indésirable de l’utilisateur final**: aucun effet.

#### <a name="preview-permission"></a>Autorisation d’aperçu

L’autorisation **preview** (_PermissionToPreview_) contrôle la possibilité pour les utilisateurs de prévisualiser leurs messages en quarantaine.

- **Détails du message en quarantaine**:
  - Autorisation d' **Aperçu** activée : le bouton **Aperçu du message** est disponible.
  - Autorisation d' **Aperçu** désactivée : le bouton **Aperçu du message** n’est pas disponible.

- **Notifications de courrier indésirable de l’utilisateur final**: aucun effet.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Autoriser les destinataires à libérer un message à partir de l’autorisation de mise en quarantaine

L’autorisation **autoriser les destinataires à libérer un message à partir de la quarantaine** (_PermissionToRelease_) contrôle la capacité des utilisateurs à libérer leurs messages mis en quarantaine directement et sans l’approbation d’un administrateur.

- **Détails du message en quarantaine**:
  - Autorisation activée : le bouton **diffuser le message** est disponible.
  - Autorisation désactivée : le bouton **diffuser le message** n’est pas disponible.
  
- **Notifications de courrier indésirable de l’utilisateur final**:
  - Autorisation activée : le bouton de **publication** est disponible.
  - Autorisation désactivée : le bouton de **publication** n’est pas disponible.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Autoriser les destinataires à demander la libération d’un message à partir de l’autorisation de mise en quarantaine

L’option **autoriser les destinataires à demander la libération d’un message à partir de l’autorisation de mise en quarantaine** (_PermissionToRequestRelease_) contrôle la capacité des utilisateurs à _demander_ la libération de leurs messages mis en quarantaine. Le message n’est publié qu’après qu’un administrateur a approuvé la demande.

- **Détails du message en quarantaine**:
  - Autorisation activée : le bouton de lancement de la **demande** est disponible.
  - Autorisation désactivée : le bouton de libération de la **demande** n’est pas disponible.

- **Notifications de courrier indésirable de l’utilisateur final**: le bouton de **publication** n’est pas disponible.
