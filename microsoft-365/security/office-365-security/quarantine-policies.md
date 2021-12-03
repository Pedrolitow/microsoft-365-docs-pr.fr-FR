---
title: Stratégies de mise en quarantaine
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
description: Les administrateurs peuvent apprendre à utiliser des stratégies de mise en quarantaine pour contrôler ce que les utilisateurs peuvent faire pour mettre en quarantaine les messages.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81bb257d809eeb16988118faaced2035b527c491
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2021
ms.locfileid: "61283721"
---
# <a name="quarantine-policies"></a>Stratégies de mise en quarantaine

Les stratégies de mise en quarantaine (auparavant appelées balises de mise en _quarantaine)_ dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 permettent aux administrateurs de contrôler ce que les utilisateurs peuvent faire pour mettre en quarantaine les messages en fonction de la raison pour laquelle le message a été mis en quarantaine.

Traditionnellement, les utilisateurs ont été autorisés ou refusés de niveaux d’interactivité pour les messages de mise en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine. Par exemple, les utilisateurs peuvent afficher et libérer les messages mis en quarantaine par le filtrage anti-courrier indésirable en tant que courrier indésirable ou en bloc, mais ils ne peuvent pas afficher ou libérer les messages mis en quarantaine en tant que hameçonnage ou programme malveillant à haut niveau de confiance.

Pour les fonctionnalités de [protection](#step-2-assign-a-quarantine-policy-to-supported-features)prise en charge, les stratégies de mise en quarantaine spécifient ce que les utilisateurs sont autorisés à faire à leurs propres messages (messages dont ils sont _destinataires)_ en quarantaine et dans les notifications de mise en quarantaine. Les notifications de mise en quarantaine remplacent les notifications de courrier indésirable pour l’utilisateur final. Ces notifications sont désormais contrôlées par des stratégies de mise en quarantaine et contiennent des informations sur les messages mis en quarantaine pour toutes les fonctionnalités de protection prise en charge (pas seulement les verdicts de stratégie anti-courrier indésirable et anti-hameçonnage).

Les stratégies de mise en quarantaine par défaut qui appliquent les fonctionnalités utilisateur historiques sont automatiquement affectées aux actions des fonctionnalités de protection prises en charge qui met en quarantaine les messages. Vous pouvez également créer des stratégies de mise en quarantaine personnalisées et les affecter aux fonctionnalités de protection prises en charge pour autoriser ou empêcher les utilisateurs d’effectuer des actions spécifiques sur ces types de messages mis en quarantaine.

Les autorisations de stratégie de mise en quarantaine individuelles sont combinées dans les groupes d’autorisations prédéfins suivants :

- Pas d’accès
- Accès limité
- Accès total

Les autorisations de stratégie de mise en quarantaine individuelles contenues dans les groupes d’autorisations prédéfinits sont décrites dans le tableau suivant :

<br>

****

|Autorisation|Pas d’accès|Accès limité|Accès total|
|---|:---:|:---:|:---:|
|**Bloquer l’expéditeur** (_PermissionToBlockSender_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Preview** (_PermissionToPreview_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Autoriser les destinataires à libérer un message de la quarantaine** (_PermissionToRelease_)|||![Coche.](../../media/checkmark.png)|
|**Autoriser les destinataires à demander qu’un message soit libéré** de la quarantaine (_PermissionToRequestRelease_)||![Coche](../../media/checkmark.png)||
|

Les stratégies de mise en quarantaine par défaut, les groupes d’autorisations associés et l’option d’activer les notifications de mise en quarantaine sont décrites dans le tableau suivant :

<br>

|Stratégie de mise en quarantaine par défaut|Groupe d’autorisations utilisé|Notifications de mise en quarantaine activées ?|
|---|---|---|
|AdminOnlyAccessPolicy|Pas d’accès|Non|
|DefaultFullAccessPolicy|Accès total|Non|
|NotificationEnabledPolicy<sup>\*</sup>|Accès total|Oui|

Si vous n’aimez pas les autorisations par défaut dans les groupes d’autorisations prédéfinefois, ou si vous souhaitez activer les notifications de mise en quarantaine, créez et utilisez des stratégies de mise en quarantaine personnalisées. Pour plus d’informations sur l’objet de chaque autorisation, consultez la section Détails des [autorisations](#quarantine-policy-permission-details) de stratégie de mise en quarantaine plus loin dans cet article.

Vous créez et affectez des stratégies de mise en quarantaine dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 ayant des boîtes aux lettres Exchange Online ; EOP PowerShell autonome dans les organisations EOP sans Exchange Online boîtes aux lettres).

> [!NOTE]
> La durée de mise en quarantaine des messages mis  en quarantaine avant leur expiration est contrôlée par la stratégie de rétention du courrier indésirable en quarantaine pendant ce nombre de jours _(QuarantineRetentionPeriod_) dans les stratégies anti-courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).
>
> Si vous modifiez la stratégie de mise en quarantaine affectée à une  fonctionnalité de protection prise en charge, la modification affecte les messages mis en quarantaine après la modification. Les messages précédemment mis en quarantaine par cette fonctionnalité de protection ne sont pas affectés par les paramètres de la nouvelle attribution de stratégie de mise en quarantaine.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Autorisations d’accès total et notifications de mise en quarantaine

<sup>\*</sup> La stratégie de mise en quarantaine nommée NotificationEnabledPolicy n’est pas présente dans tous les environnements. Vous aurez la stratégie de mise en quarantaine NotificationEnabledPolicy si votre organisation répond aux deux exigences suivantes :

- Votre organisation existait avant que la fonctionnalité de stratégie de mise en quarantaine ne soit désactivée (fin juillet/début août 2021).
- Vous aviez une ou plusieurs stratégies [anti-courrier](configure-your-spam-filter-policies.md) indésirable (stratégie anti-courrier indésirable par défaut ou stratégies anti-courrier indésirable personnalisées) dans laquelle le paramètre Activer les **notifications** de courrier indésirable de l’utilisateur final était activé.

Comme décrit précédemment, les notifications de mise en quarantaine dans les stratégies de mise en quarantaine remplacent les notifications de courrier indésirable de l’utilisateur final que vous avez utilisées pour activer ou désactiver les stratégies anti-courrier indésirable. La stratégie de mise en quarantaine intégrée nommée DefaultFullAccessPolicy duplique les _autorisations historiques_ pour les messages mis en quarantaine, mais les _notifications_ de mise en quarantaine ne sont pas désactivées dans la stratégie de mise en quarantaine. De plus, étant donné que vous ne pouvez pas modifier la stratégie intégrée, vous ne pouvez pas activer les notifications de mise en quarantaine dans DefaultFullAccessPolicy.

Pour fournir les autorisations de DefaultFullAccessPolicy, mais avec les notifications de mise en quarantaine désactivées, nous avons créé la stratégie nommée NotificationEnabledPolicy à utiliser à la place de DefaultFullAccessPolicy pour les organisations qui en avaient besoin (organisations où les notifications de courrier indésirable à l’utilisateur final étaient allumées).

Pour les nouvelles organisations ou les organisations plus anciennes qui n’ont jamais activé les notifications de courrier indésirable pour l’utilisateur final dans les stratégies anti-courrier indésirable, vous n’avez pas la stratégie de mise en quarantaine nommée NotificationEnabledPolicy. Pour activer les notifications de mise en quarantaine, vous pouvez créer et utiliser des stratégies de mise en quarantaine personnalisées lorsque les notifications de mise en quarantaine sont allumées.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le portail Microsoft 365 Defender sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> . Ou pour aller directement à la page Des stratégies **de** mise en quarantaine, ouvrez <https://security.microsoft.com/quarantinePolicies> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour afficher, créer, modifier ou supprimer des stratégies de mise en quarantaine,  vous devez être membre des rôles Gestion de l’organisation, Administrateur de la sécurité ou Administrateur de la mise en quarantaine dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Étape 1 : Créer des stratégies de mise en quarantaine dans le portail Microsoft 365 Defender de mise en quarantaine

1. Dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a>sélectionnez **e-mail & stratégies** de collaboration contre les menaces Section Stratégies de mise en \>  \>  \>  quarantaine, puis sélectionnez **Stratégies de mise en quarantaine.**

2. Dans la page **Stratégie de** mise en quarantaine, cliquez sur Ajouter une icône de ![ stratégie personnalisée.](../../media/m365-cc-sc-create-icon.png) **Ajouter une stratégie personnalisée**.

3. **L’Assistant Nouvelle** stratégie s’ouvre. Dans la page **Nom de la** stratégie, entrez un nom court mais unique dans la zone Nom de **la** stratégie. Vous devez identifier et sélectionner la stratégie de mise en quarantaine par nom dans les étapes à venir. Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **d’accès aux messages du** destinataire, sélectionnez l’une des valeurs suivantes :
   - **Accès limité**: les autorisations individuelles incluses dans ce groupe d’autorisations sont décrites plus tôt dans cet article.
   - **Définir un accès spécifique (avancé)**: utilisez cette valeur pour spécifier des autorisations personnalisées. Configurez les paramètres suivants qui s’affichent :
     - **Sélectionnez la préférence d’action de** publication : sélectionnez l’une des valeurs suivantes :
       - Vide : il s’agit de la valeur par défaut.
       - **Autoriser les destinataires à libérer un message de la quarantaine**
       - **Autoriser les destinataires à demander qu’un message soit libéré de la quarantaine**
     - **Sélectionnez des actions supplémentaires que les destinataires peuvent prendre** sur les messages mis en quarantaine : sélectionnez une partie, l’ensemble ou aucune des valeurs suivantes :
       - **Delete**
       - **Aperçu**
       - **Bloquer l’expéditeur**

   Ces autorisations et leur effet sur les messages mis en quarantaine et les notifications de mise en quarantaine sont décrits dans la section détails des [autorisations](#quarantine-policy-permission-details) de stratégie de mise en quarantaine plus loin dans cet article.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **De notification** de courrier indésirable à l’utilisateur final, sélectionnez **Activer** pour activer les notifications de mise en quarantaine (anciennement appelées notifications de courrier indésirable pour l’utilisateur final). Lorsque vous avez terminé, cliquez sur **Suivant**.

   > [!NOTE]
   > Comme expliqué précédemment, les stratégies intégrées (AdminOnlyAccessPolicy ou DefaultFullAccessPolicy) ne sont pas mises en quarantaine et vous ne pouvez pas modifier les stratégies.

6. Dans la page **Examiner la stratégie,** examinez vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

7. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

Vous êtes maintenant prêt à affecter la stratégie de mise en quarantaine à une fonctionnalité de mise en quarantaine, comme décrit dans la section [Étape 2.](#step-2-assign-a-quarantine-policy-to-supported-features)

### <a name="create-quarantine-policies-in-powershell"></a>Créer des stratégies de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour créer des stratégies de mise en quarantaine, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la cmdlet **New-QuarantinePolicy.**

> [!NOTE]
> Si vous n’utilisez pas le _paramètre ESNEnabled_ et la valeur, les notifications de mise en quarantaine `$true` sont désactivées.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Utiliser le paramètre EndUserQuarantinePermissionsValue

Pour créer une stratégie de mise en quarantaine à l’aide du paramètre _EndUserQuarantinePermissionsValue,_ utilisez la syntaxe suivante :

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

Le _paramètre EndUserQuarantinePermissionsValue_ utilise une valeur décimale convertie à partir d’une valeur binaire. La valeur binaire correspond aux autorisations de mise en quarantaine de l’utilisateur final disponibles dans un ordre spécifique. Pour chaque autorisation, la valeur 1 est égale à True et la valeur 0 à False.

L’ordre et les valeurs requis pour chaque autorisation individuelle sont décrits dans le tableau suivant :

<br>

****

|Autorisation|Valeur décimale|Valeur binaire|
|---|:---:|:---:|
|PermissionToViewHeader<sup>\*</sup>|128|10000000|
|PermissionToDownload<sup>\*\*</sup>|64|01000000|
|PermissionToAllowSender<sup>\*\*</sup>|32|00100000|
|PermissionToBlockSender|16|00010000|
|PermissionToRequestRelease<sup>\*\*\*</sup>|8 |00001000|
|PermissionToRelease<sup>\*\*\*</sup>|4|00000100|
|PermissionToPreview|2|00000010|
|PermissionToDelete|1|00000001|
|

<sup>\*</sup> La valeur 0 ne masque pas le bouton Afficher l’en-tête du **message** dans les détails du message mis en quarantaine (le bouton est toujours disponible).

<sup>\*\*</sup> Ce paramètre n’est pas utilisé (la valeur 0 ou 1 ne fait rien).

<sup>\*\*\*</sup> Ne définissez pas ces deux valeurs sur 1. Définissez l’un sur 1 et l’autre sur 0, ou définissez les deux sur 0.

Pour les autorisations d’accès limité, les valeurs requises sont :

<br>

****

|Autorisation|Accès limité|
|---|:--:|
|PermissionToViewHeader|0|
|PermissionToDownload|0|
|PermissionToAllowSender|0|
|PermissionToBlockSender|1|
|PermissionToRequestRelease|1|
|PermissionToRelease|0|
|PermissionToPreview|1|
|PermissionToDelete|1|
|Valeur binaire|00011011|
|Valeur décimale à utiliser|27|
|

Cet exemple crée une stratégie de mise en quarantaine nommée LimitedAccess avec des notifications de mise en quarantaine qui sont mises en quarantaine et qui attribue les autorisations d’accès limité comme décrit dans le tableau précédent.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

Pour les autorisations personnalisées, utilisez le tableau précédent pour obtenir la valeur binaire qui correspond aux autorisations de votre choix. Convertissez la valeur binaire en valeur décimale et utilisez la valeur décimale pour le paramètre _EndUserQuarantinePermissionsValue._

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Étape 2 : Attribuer une stratégie de mise en quarantaine aux fonctionnalités prise en charge

Dans les _fonctionnalités_ de protection prises en charge qui met en quarantaine les messages électroniques, vous pouvez affecter une stratégie de mise en quarantaine aux actions de mise en quarantaine disponibles. Les fonctionnalités de mise en quarantaine des messages et la disponibilité des stratégies de mise en quarantaine sont décrites dans le tableau suivant :

<br>

****

|Fonctionnalité|Stratégies de mise en quarantaine pris en charge ?|Stratégies de mise en quarantaine par défaut utilisées|
|---|:---:|---|
|[Stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md): <ul><li>**Courrier** indésirable (_SpamAction_)</li><li>**Courrier indésirable à niveau** de confiance élevé (_HighConfidenceSpamAction_)</li><li>**Hameçonnage** (_PhishSpamAction_)</li><li>**Hameçonnage à haut niveau de** confiance (_HighConfidencePhishAction_)</li><li>**Bulk** (_BulkSpamAction_)</li></ul>|Oui|<ul><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>AdminOnlyAccessPolicy (aucun accès)</li><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li></ul>|
|Stratégies anti-hameçonnage: <ul><li>[Protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Protection contre l’emprunt d’identité dans Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365):<ul><li>**Si le message est détecté comme un utilisateur dont** l’identité est usurpée (_TargetedUserProtectionAction_)</li><li>**Si le message est détecté comme un** domaine dont l’identité a été usurpée (_TargetedDomainProtectionAction_)</li><li>**Si l’intelligence de boîte aux lettres détecte et usurpe l’identité de** l’utilisateur (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Oui|<ul><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>Protection contre l’emprunt d’identité :<ul><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy <sup>\*</sup> (accès complet)</li></ul></li></ul>|
|[Stratégies anti-programme](configure-anti-malware-policies.md)malveillant : tous les messages détectés sont toujours mis en quarantaine.|Oui|AdminOnlyAccessPolicy (aucun accès)|
|[Coffre protection des pièces jointes](safe-attachments.md): <ul><li>Messages électroniques avec pièces jointes mis en quarantaine en tant que programmes malveillants par Coffre stratégies de pièces jointes (_Activer_ et _action_)</li><li>Fichiers mis en quarantaine comme programmes [malveillants par Coffre pièces jointes](mdo-for-spo-odb-and-teams.md) pour SharePoint, OneDrive et Microsoft Teams</li></ul>|<ul><li>Oui</li><li>Non</li></ul>|<ul><li>AdminOnlyAccessPolicy (aucun accès)</li><li>s/o</li></ul>|
|[Règles de flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) avec l’action : Remettre le **message** en quarantaine hébergé (mise en _quarantaine)._|Non|s/o|
|

<sup>\*</sup> Comme [décrit précédemment dans cet article,](#full-access-permissions-and-quarantine-notifications)votre organisation peut utiliser NotificationEnabledPolicy au lieu de DefaultFullAccessPolicy. La seule différence entre ces deux stratégies de mise en quarantaine est que les notifications de mise en quarantaine sont allumées dans NotificationEnabledPolicy et désactivées dans DefaultFullAccessPolicy.

Les stratégies de mise en quarantaine par défaut, les groupes d’autorisations prédéfinits et les autorisations sont décrits au début de cet [article](#quarantine-policies) et plus [loin dans cet article.](#preset-permissions-groups)

> [!NOTE]
> Si vous êtes satisfait des autorisations par défaut de l’utilisateur final et des notifications de mise en quarantaine fournies (ou non) par les stratégies de mise en quarantaine par défaut, vous n’avez rien à faire. Si vous souhaitez ajouter ou supprimer des fonctionnalités de l’utilisateur final (boutons disponibles) pour les messages mis en quarantaine, ou activer les notifications de mise en quarantaine et ajouter ou supprimer les mêmes fonctionnalités dans les notifications de mise en quarantaine, vous pouvez affecter une stratégie de mise en quarantaine différente à l’action de mise en quarantaine.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Affecter des stratégies de mise en quarantaine dans les stratégies prise en charge dans le portail Microsoft 365 Defender

### <a name="anti-spam-policies"></a>Stratégies anti-courrier indésirable

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>dans la section Règles, & stratégies de **collaboration** & stratégies contre les \>  \>  \>  menaces. 

   Ou, pour aller directement à la page des stratégies **Ant-spam,** utilisez <https://security.microsoft.com/antispam> .

2. Dans la page **Stratégies anti-courrier** indésirable, faites l’une des opérations suivantes :
   - Recherchez et sélectionnez **une** stratégie anti-courrier indésirable entrant existante.
   - Créez une stratégie **de** courrier indésirable entrant.

3. Effectuez l’une des étapes suivantes :
   - **Modifier une stratégie existante**: sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le volant des détails de la stratégie, allez dans la section **Actions,** puis cliquez **sur Modifier les actions.**
   - **Créer :** dans l’Assistant Nouvelle stratégie, accès à la page **Actions.**

4. Dans la page **Actions,** chaque verdict qui a  l’action de **message** de mise en quarantaine aura également la zone Sélectionner la stratégie de mise en quarantaine pour que vous sélectionniez une stratégie de mise en quarantaine correspondante.

   **Remarque**: lorsque vous créez  une stratégie, une valeur de stratégie de mise en quarantaine Select vide indique que la stratégie de mise en quarantaine par défaut pour ce verdict est utilisée. Lorsque vous modifiez ultérieurement la stratégie, les valeurs vides sont remplacées par les noms de stratégie de mise en quarantaine par défaut réels, comme décrit dans le tableau précédent.

   ![Sélections de stratégie de mise en quarantaine dans une stratégie anti-courrier indésirable.](../../media/quarantine-tags-in-anti-spam-policies.png)

Des instructions complètes pour la création et la modification des stratégies anti-courrier indésirable sont décrites dans Configurer des stratégies [anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

#### <a name="anti-spam-policies-in-powershell"></a>Stratégies anti-courrier indésirable dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de mise en quarantaine dans les stratégies anti-courrier indésirable, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Remarques** :

- La valeur par défaut des paramètres _PhishSpamAction_ et _HighConfidencePhishAction_ est Mise en quarantaine. Vous n’avez donc pas besoin d’utiliser ces paramètres lorsque vous créez de nouvelles stratégies de filtrage du courrier indésirable dans PowerShell. Pour les paramètres _SpamAction,_ _HighConfidenceSpamAction_ et _BulkSpamAction_ dans les stratégies anti-courrier indésirable nouvelles ou existantes, la stratégie de mise en quarantaine n’est effective que si la valeur est Mise en quarantaine.

  Pour voir les valeurs de paramètre importantes dans les stratégies anti-courrier indésirable existantes, exécutez la commande suivante :

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Pour plus d’informations sur les valeurs d’action par défaut et les valeurs d’action recommandées pour Standard et Strict, voir paramètres de stratégie [anti-courrier indésirable EOP.](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

- Lorsque vous créez de nouvelles stratégies anti-courrier indésirable, un [](#step-2-assign-a-quarantine-policy-to-supported-features) verdict de filtrage du courrier indésirable sans paramètre de stratégie de mise en quarantaine correspondant signifie que la stratégie de mise en quarantaine par défaut pour ce verdict est utilisée.

  Vous devez remplacer une stratégie de mise en quarantaine par défaut par une stratégie de mise en quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine pour ce verdict particulier de filtrage du courrier indésirable.

- Une nouvelle stratégie anti-courrier indésirable dans PowerShell nécessite une stratégie de filtrage du courrier indésirable (paramètres) à l’aide de la cmdlet **New-HostedContentFilterPolicy** et une règle de filtrage de courrier indésirable exclusive (filtres de destinataires) à l’aide de la cmdlet **New-HostedContentFilterRule.** Pour obtenir des instructions, [voir Utiliser PowerShell pour créer des stratégies anti-courrier indésirable.](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies)

Cet exemple crée une stratégie de filtrage du courrier indésirable nommée Research Department avec les paramètres suivants :

- L’action pour tous les verdicts de filtrage du courrier indésirable est définie sur Quarantaine.
- La stratégie de mise en quarantaine  personnalisée nommée NoAccess qui attribue aucune autorisation  d’accès remplace toutes les stratégies de mise en quarantaine par défaut qui n’attribuent pas déjà aucune autorisation d’accès par défaut.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Cet exemple modifie la stratégie de filtrage de courrier indésirable existante nommée Human Resources. L’action pour le verdict de mise en quarantaine du courrier indésirable est définie sur Mise en quarantaine et la stratégie de mise en quarantaine personnalisée nommée NoAccess est affectée.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Politiques anti-hameçonnage

La veille contre l’usurpation d’adresse est disponible dans EOP et Defender Office 365. La protection contre l’emprunt d’identité d’utilisateur, la protection contre l’usurpation d’identité de domaine et l’intelligence des boîtes aux lettres sont disponibles uniquement dans Defender Office 365. Si vous souhaitez en savoir plus, consultez l’article [Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md).

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>dans la section Règles, & stratégies de **collaboration** & stratégies de menace \>  \>  \> **anti-hameçonnage.** 

   Ou, pour aller directement à la page des stratégies **Ant-spam,** utilisez <https://security.microsoft.com/antiphishing> .

2. Dans la page **Anti-hameçonnage,** faites l’une des opérations suivantes :
   - Recherchez et sélectionnez une stratégie anti-hameçonnage existante.
   - Créez une stratégie anti-hameçonnage.

3. Effectuez l’une des étapes suivantes :
   - **Modifier une stratégie existante**: sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le volant des détails de la stratégie, allez dans la section **Paramètres** de protection, puis cliquez sur Modifier les **paramètres de protection.**
   - **Créer :** dans l’Assistant Nouvelle stratégie, accès à la page **Actions.**

4. Dans la page **Paramètres de protection,** vérifiez que les paramètres suivants sont allumés et configurés selon les besoins :
   - **Utilisateurs activés pour la protection :** spécifier les utilisateurs.
   - **Domaines activés à protéger**: **sélectionnez** Inclure les domaines que je possède et/ou Incluez des domaines **personnalisés** et spécifiez les domaines.
   - **Activer l’intelligence des boîtes aux lettres**
   - **Activer la veille pour la protection contre l’emprunt d’identité**
   - **Activer la veille contre l’usurpation d’informations**

5. Effectuez l’une des étapes suivantes :
   - **Modifier existant :** dans le volet d’informations de stratégie, allez dans la section **Actions,** puis cliquez sur **Modifier les actions.**
   - **Créer :** dans l’Assistant Nouvelle stratégie, accès à la page **Actions.**

6. Dans la page **Actions,** chaque verdict qui a mis  en quarantaine l’action de **message** aura également la zone Appliquer la stratégie de mise en quarantaine pour que vous sélectionniez une stratégie de mise en quarantaine correspondante.

   **Remarque**: lorsque vous créez  une stratégie, une valeur vide de stratégie Appliquer la quarantaine indique que la stratégie de mise en quarantaine par défaut de cette action est utilisée. Lorsque vous modifiez ultérieurement la stratégie, les valeurs vides sont remplacées par les noms de stratégie de mise en quarantaine par défaut réels, comme décrit dans le tableau précédent.

   ![Sélections de stratégie de mise en quarantaine dans une stratégie anti-hameçonnage.](../../media/quarantine-tags-in-anti-phishing-policies.png)

Des instructions complètes pour la création et la modification des stratégies anti-hameçonnage sont disponibles dans les rubriques suivantes :

- [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>Stratégies anti-hameçonnage dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de mise en quarantaine dans les stratégies anti-hameçonnage, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Remarques** :

- Les _\* paramètres Enable_ sont requis pour activer les fonctionnalités de protection spécifiques. La valeur par défaut des paramètres _EnableMailboxIntelligence_ et _EnableSpoofIntelligence_ est $true, vous n’avez donc pas besoin d’utiliser ces paramètres lorsque vous créez des stratégies anti-hameçonnage dans PowerShell. Tous les _autres paramètres Enable \*_ doivent avoir la valeur $true afin que vous pouvez définir la valeur Mise en quarantaine dans les paramètres _\* d’action_ correspondants pour affecter ensuite une stratégie de mise en quarantaine. Aucun des paramètres _*\Action_ n’a la valeur par défaut Quarantaine.

  Pour voir les valeurs de paramètre importantes dans les stratégies anti-hameçonnage existantes, exécutez la commande suivante :

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Pour plus d’informations sur les valeurs d’action par défaut et les valeurs d’action recommandées pour Standard et Strict, voir paramètres de stratégie [anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) et paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 .

- Lorsque vous créez des stratégies anti-hameçonnage, une action anti-hameçonnage sans paramètre de stratégie de mise en quarantaine correspondant signifie que la stratégie de mise en quarantaine par défaut pour ce verdict est utilisée. [](#step-2-assign-a-quarantine-policy-to-supported-features)

  Vous devez remplacer une stratégie de mise en quarantaine par défaut par une stratégie de mise en quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine pour ce verdict particulier.

- Une nouvelle stratégie anti-hameçonnage dans PowerShell nécessite une stratégie anti-hameçonnage (paramètres) à l’aide de la cmdlet **New-AntiPhishPolicy** et une règle anti-hameçonnage exclusive (filtres de destinataires) à l’aide de la cmdlet **New-AntiPhishRule.** Pour obtenir des instructions, consultez les rubriques suivantes :
  - [Utiliser PowerShell pour configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

Cet exemple crée une stratégie anti-hameçonnage nommée Research Department avec les paramètres suivants :

- L’action pour tous les verdicts de filtrage du courrier indésirable est définie sur Quarantaine.
- La stratégie de mise en quarantaine  personnalisée nommée NoAccess qui attribue aucune autorisation  d’accès remplace toutes les stratégies de mise en quarantaine par défaut qui n’attribuent pas déjà aucune autorisation d’accès par défaut.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

Cet exemple modifie la stratégie anti-hameçonnage existante nommée Human Resources. L’action pour les messages détectés par l’emprunt d’identité d’utilisateur et l’emprunt d’identité de domaine est définie sur Mise en quarantaine et la stratégie de mise en quarantaine personnalisée nommée NoAccess est affectée.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Stratégies anti-programme malveillant

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>dans la section Règles, & stratégies de **collaboration** & stratégies contre les \>  \>  \>  menaces. 

   Ou, pour aller directement à la page **Anti-programme** malveillant, utilisez <https://security.microsoft.com/antimalwarev2> .

2. Dans la page **Anti-programme** malveillant, faites l’une des opérations suivantes :
   - Recherchez et sélectionnez une stratégie anti-programme malveillant existante.
   - Créez une stratégie anti-programme malveillant.

3. Effectuez l’une des étapes suivantes :
   - **Modifier une stratégie existante**: sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le volant des détails de la stratégie, allez dans la section **Paramètres** de protection, puis cliquez sur Modifier les **paramètres de protection.**
   - **Créer :** dans l’Assistant Nouvelle stratégie, accès à la page **Actions.**

4. Dans la **page Paramètres de protection,** sélectionnez une stratégie de mise en quarantaine dans la zone **de stratégie de mise en** quarantaine.

   **Remarque**: lorsque vous créez  une stratégie, une valeur de stratégie de quarantaine vide indique la stratégie de mise en quarantaine par défaut utilisée. Lorsque vous modifiez ultérieurement la stratégie, la valeur vide est remplacée par le nom réel de la stratégie de mise en quarantaine par défaut, comme décrit dans le tableau précédent.

#### <a name="anti-malware-policies-in-powershell"></a>Stratégies anti-programme malveillant dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de mise en quarantaine dans les stratégies anti-programme malveillant, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Remarques** :

- Lorsque vous créez des stratégies anti-programme malveillant sans utiliser le paramètre QuarantineTag lorsque vous créez une stratégie anti-programme malveillant, la stratégie de mise en quarantaine par défaut pour les détections de programmes malveillants est utilisée (AdminOnlyAccessPolicy).

  Vous devez remplacer la stratégie de mise en quarantaine par défaut par une stratégie de mise en quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine en tant que programmes malveillants.

  Pour voir les valeurs de paramètre importantes dans les stratégies anti-hameçonnage existantes, exécutez la commande suivante :

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- Une nouvelle stratégie anti-programme malveillant dans PowerShell nécessite une stratégie de filtrage des programmes malveillants (paramètres) à l’aide de la cmdlet **New-MalwareFilterPolicy** et une règle de filtrage des programmes malveillants exclusive (filtres de destinataires) à l’aide de la cmdlet **New-MalwareFilterRule.** Pour obtenir des instructions, voir Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies [anti-programme malveillant.](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies)

Cet exemple crée une stratégie de filtrage des programmes malveillants nommée Research Department qui utilise la stratégie de mise en quarantaine personnalisée noAccess qui attribue des **autorisations** d’accès illimité aux messages mis en quarantaine.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Cet exemple modifie la stratégie de filtrage des programmes malveillants existante nommée Human Resources  en attribuant la stratégie de mise en quarantaine personnalisée noAccess qui n’attribue aucune autorisation d’accès aux messages mis en quarantaine.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Coffre de pièces jointes dans Defender pour Office 365

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>go to **Email & collaboration** Policies & \> **rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies.**

   Ou, pour aller directement à la page **Coffre pièces jointes,** utilisez <https://security.microsoft.com/safeattachmentv2> .

2. Dans la page **Coffre pièces jointes,** faites l’une des étapes suivantes :
   - Recherchez et sélectionnez une stratégie Coffre pièces jointes existante.
   - Créez une stratégie Coffre pièces jointes.

3. Effectuez l’une des étapes suivantes :
   - **Modifier une stratégie existante**: sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le volant des détails de la stratégie, allez à la section **Paramètres,** puis cliquez sur **Modifier les paramètres.**
   - **Créer :** dans l’Assistant Nouvelle stratégie, vous pouvez Paramètres **page.**

4. Sur la **Paramètres** page, faites les étapes suivantes :
   1. **Coffre les pièces jointes d’une réponse anti-programme** malveillant inconnue : **sélectionnez Bloquer,** **Remplacer** ou **Remise dynamique.**
   2. Sélectionnez une stratégie de mise en quarantaine dans la **zone de stratégie de mise en** quarantaine.

   **Remarque**: lorsque vous créez  une stratégie, une valeur de stratégie de quarantaine vide indique que la stratégie de mise en quarantaine par défaut est utilisée. Lorsque vous modifiez ultérieurement la stratégie, la valeur vide est remplacée par le nom réel de la stratégie de mise en quarantaine par défaut, comme décrit dans le tableau précédent.

Les instructions complètes pour la création et la modification Coffre des stratégies de pièces jointes sont décrites dans La Coffre stratégies de pièces [jointes dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>Coffre pièces jointes dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de mise en quarantaine dans les stratégies de pièces jointes Coffre, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Remarques** :

- Les _valeurs_ du paramètre Action Block, Replace ou DynamicDelivery peuvent entraîner la mise en quarantaine des messages (la valeur Autoriser ne met pas les messages en quarantaine). La valeur du paramètre _Action_ n’est significative que lorsque la valeur du _paramètre Enable_ est `$true` .

- Lorsque vous créez des stratégies de pièces jointes Coffre sans utiliser le paramètre QuarantineTag, la stratégie de mise en quarantaine par défaut pour les détections de pièces jointes Coffre dans le courrier électronique est utilisée (AdminOnlyAccessPolicy).

  Vous devez remplacer la stratégie de mise en quarantaine par défaut par une stratégie de mise en quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages électroniques mis en quarantaine par les stratégies Coffre pièces jointes.

  Pour voir les valeurs de paramètre importantes, exécutez la commande suivante :

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- Une nouvelle stratégie de pièces jointes Coffre dans PowerShell nécessite une stratégie de pièces jointes sécurisées (paramètres) à l’aide de la cmdlet **New-SafeAttachmentPolicy** et une règle de pièce jointe sécurisée exclusive (filtres de destinataires) à l’aide de l’cmdlet **New-SafeAttachmentRule.** Pour obtenir des instructions, voir Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des [stratégies Coffre pièces jointes.](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies)

Cet exemple crée une stratégie de pièce jointe sécurisée nommée Research Department qui bloque les  messages détectés et utilise la stratégie de mise en quarantaine personnalisée noAccess qui n’attribue aucune autorisation d’accès aux messages en quarantaine.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Cet exemple modifie la stratégie de pièces jointes sécurisées existante nommée Human Resources  en attribuant la stratégie de mise en quarantaine personnalisée noAccess qui n’accorde aucune autorisation d’accès.

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Configurer les paramètres globaux de notification de mise en quarantaine dans le portail Microsoft 365 Defender

Les paramètres globaux des stratégies de mise en quarantaine vous permettent de personnaliser les notifications de mise en quarantaine qui sont envoyées aux destinataires des messages mis en quarantaine si les notifications de mise en quarantaine sont mises en quarantaine dans la stratégie de mise en quarantaine. Pour plus d’informations sur ces notifications, voir [notifications de mise en quarantaine.](use-spam-notifications-to-release-and-report-quarantined-messages.md)

1. Dans le portail Microsoft 365 Defender, sélectionnez Stratégies de mise en quarantaine & stratégies de **collaboration** sur les menaces, puis \>  \>  \>  sélectionnez **Stratégies de mise en quarantaine.**

2. Dans la page **Stratégie de** mise en quarantaine, sélectionnez **Paramètres globaux.**

3. Dans le volant **des paramètres de notification de** mise en quarantaine qui s’ouvre, configurez tout ou partie des paramètres suivants :

   - **Nom d’affichage**: personnaliser le nom complet de l’expéditeur utilisé dans les notifications de mise en quarantaine.

     Pour chaque langue que vous avez ajoutée, sélectionnez la langue dans la deuxième langue (ne cliquez pas  sur le X) et entrez la valeur de texte de votre choix dans la zone Nom complet.

     La capture d’écran suivante montre le nom complet personnalisé dans une notification de mise en quarantaine :

     ![Nom complet de l’expéditeur personnalisé dans une notification de mise en quarantaine.](../../media/quarantine-tags-esn-customization-display-name.png)

   - **Clause d’exclusion de** responsabilité : ajoutez une clause d’exclusion de responsabilité personnalisée au bas des notifications de mise en quarantaine. Le texte localisé, **une clause d’exclusion** de responsabilité de votre organisation, est toujours inclus en premier, suivi du texte que vous spécifiez.

     Pour chaque langue que vous avez ajoutée, sélectionnez la langue dans la deuxième langue (ne cliquez pas sur le X) et entrez la valeur de texte de votre choix dans la zone Exclusion de **responsabilité.**

     La capture d’écran suivante montre la clause d’exclusion de responsabilité personnalisée dans une notification de mise en quarantaine :

     ![Une clause d’exclusion de responsabilité personnalisée au bas d’une notification de mise en quarantaine.](../../media/quarantine-tags-esn-customization-disclaimer.png)

   - **Choisir la langue**: les notifications de mise en quarantaine sont déjà localisées en fonction des paramètres de langue du destinataire. Vous pouvez spécifier du texte personnalisé dans différentes langues pour le nom **d’affichage** et les valeurs **de clause d’exclusion** de responsabilité.

     Sélectionnez au moins une langue dans la première langue, puis cliquez sur **Ajouter.** Vous pouvez sélectionner plusieurs langues en cliquant sur **Ajouter** après chacune d’elles. Une zone de langue de section affiche toutes les langues que vous avez sélectionnées :

     ![Langues sélectionnées dans la deuxième langue dans les paramètres globaux de notification de mise en quarantaine des stratégies de mise en quarantaine.](../../media/quarantine-tags-esn-customization-selected-languages.png)

   - **Utilisez le logo de mon entreprise**: sélectionnez cette option pour remplacer le logo Microsoft par défaut qui est utilisé en haut des notifications de mise en quarantaine. Avant de faire cela, vous devez suivre les instructions dans Personnaliser le thème [Microsoft 365](../../admin/setup/customize-your-organization-theme.md) pour que votre organisation télécharge votre logo personnalisé.

     La capture d’écran suivante montre un logo personnalisé dans une notification de mise en quarantaine :

     ![Logo personnalisé dans une notification de mise en quarantaine.](../../media/quarantine-tags-esn-customization-logo.png)

   - Envoyer une notification de courrier indésirable à **l’utilisateur final tous les (jours)**: sélectionnez la fréquence des notifications de mise en quarantaine.

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Afficher les stratégies de mise en quarantaine dans le Microsoft 365 Defender web

1. Dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a>sélectionnez **e-mail & stratégies** de collaboration contre les menaces Section Stratégies de mise en \>  \>  \>  quarantaine, puis sélectionnez **Stratégies de mise en quarantaine.**

2. La page **Stratégie de** mise en quarantaine affiche la liste des stratégies par **nom** et date de dernière mise **à** jour.

3. Pour afficher les paramètres des stratégies de mise en quarantaine intégrées ou personnalisées, sélectionnez la stratégie de mise en quarantaine dans la liste en cliquant sur le nom.

4. Pour afficher les paramètres globaux, cliquez **sur Paramètres globaux**

### <a name="view-quarantine-policies-in-powershell"></a>Afficher les stratégies de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour afficher les stratégies de mise en quarantaine, faites l’une des étapes suivantes :

- Pour afficher une liste récapitulatif de toutes les stratégies intégrées ou personnalisées, exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Pour afficher les paramètres des stratégies de mise en quarantaine intégrées ou personnalisées, remplacez-les par le nom de la stratégie de mise en quarantaine \<QuarantinePolicyName\> et exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Pour afficher les paramètres globaux des notifications de mise en quarantaine, exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Modifier les stratégies de mise en quarantaine dans le portail Microsoft 365 Defender de mise en quarantaine

Vous ne pouvez pas modifier les stratégies de mise en quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Vous pouvez modifier la stratégie intégrée nommée NotificationEnabledPolicy[(si](#full-access-permissions-and-quarantine-notifications)vous l’avez) et les stratégies de mise en quarantaine personnalisées.

1. Dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a>sélectionnez **e-mail & stratégies** de collaboration contre les menaces Section Stratégies de mise en \>  \>  \>  quarantaine, puis sélectionnez **Stratégies de mise en quarantaine.**

2. Dans la page **Stratégies de** mise en quarantaine, sélectionnez la stratégie en cliquant sur le nom.

3. Après avoir sélectionné la stratégie, cliquez sur ![ l’icône Modifier la stratégie.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier la** stratégie qui s’affiche.

4. **L’Assistant** Modifier la stratégie qui s’ouvre est pratiquement identique à l’Assistant Nouvelle stratégie, comme décrit dans la section Créer des stratégies de mise en quarantaine dans la section du portail [Microsoft 365 Defender](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) plus tôt dans cet article. 

   La principale différence est que vous ne pouvez pas renommer une stratégie existante.

5. Lorsque vous avez terminé de modifier la stratégie, allez sur la **page** Résumé et cliquez sur **Envoyer.**

### <a name="modify-quarantine-policies-in-powershell"></a>Modifier les stratégies de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour modifier une stratégie de mise en quarantaine personnalisée, remplacez-la par le nom de la stratégie de mise en quarantaine et utilisez \<QuarantinePolicyName\> la syntaxe suivante :

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

Les paramètres disponibles sont les mêmes que ceux décrits pour la création de stratégies de mise en quarantaine plus tôt dans cet article.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Supprimer les stratégies de mise en quarantaine dans le portail Microsoft 365 Defender de mise en quarantaine

**Remarques** :

- Vous ne pouvez pas supprimer les stratégies de mise en quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Vous pouvez supprimer la stratégie intégrée nommée NotificationEnabledPolicy[(si](#full-access-permissions-and-quarantine-notifications)vous l’avez) et les stratégies de mise en quarantaine personnalisées.
- Avant de supprimer une stratégie de mise en quarantaine, vérifiez qu’elle n’est pas utilisée. Par exemple, exécutez la commande suivante dans PowerShell :

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Si la stratégie de mise en quarantaine est utilisée, [remplacez la stratégie](#step-2-assign-a-quarantine-policy-to-supported-features) de mise en quarantaine attribuée avant de la supprimer.

1. Dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a>sélectionnez **e-mail & stratégies** de collaboration contre les menaces Section Stratégies de mise en \>  \>  \>  quarantaine, puis sélectionnez **Stratégies de mise en quarantaine.**

2. Dans la page **Stratégie de** mise en quarantaine, sélectionnez la stratégie de mise en quarantaine personnalisée à supprimer en cliquant sur le nom.

3. Après avoir sélectionné la stratégie, cliquez sur ![ l’icône Supprimer la stratégie.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer la stratégie** qui s’affiche.

4. Cliquez **sur Supprimer la stratégie** dans la boîte de dialogue de confirmation qui s’affiche.

### <a name="remove-quarantine-policies-in-powershell"></a>Supprimer les stratégies de mise en quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour supprimer une stratégie de mise en quarantaine personnalisée, remplacez-la par le nom de la stratégie de mise en quarantaine \<QuarantinePolicyName\> et exécutez la commande suivante :

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Alertes système pour les demandes de mise en quarantaine

Par défaut, la stratégie d’alerte par défaut nommée User a demandé à libérer un **message** mis en quarantaine génère automatiquement une alerte de gravité moyenne et envoie des messages de notification aux membres des groupes de rôles suivants chaque fois qu’un utilisateur demande la libération d’un message mis en quarantaine :

- Administrateur de mise en quarantaine
- Administrateur de sécurité
- Gestion de l’organisation (administrateur général)

Les administrateurs peuvent personnaliser les destinataires de notification par courrier électronique ou créer une stratégie d’alerte personnalisée pour plus d’options.

Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Détails des autorisations de stratégie de mise en quarantaine

Les sections suivantes décrivent les effets des groupes d’autorisations prédéfinés et des autorisations individuelles dans les détails des messages mis en quarantaine et dans les notifications de mise en quarantaine.

### <a name="preset-permissions-groups"></a>Groupes d’autorisations prédéfins

Les autorisations individuelles incluses dans les groupes d’autorisations prédéfinés sont répertoriées dans le tableau au début de cet article.

#### <a name="no-access"></a>Pas d’accès

Si la stratégie de  mise en quarantaine attribue les autorisations Aucun accès (accès administrateur uniquement), les utilisateurs ne pourront pas voir les messages mis en quarantaine :

- **Détails des messages mis en quarantaine**: aucun message ne s’affiche dans l’affichage de l’utilisateur final.
- **Notifications de mise en** quarantaine : aucune notification n’est envoyée pour ces messages.

#### <a name="limited-access"></a>Accès limité

Si la stratégie de mise en quarantaine attribue les **autorisations** d’accès limité, les utilisateurs obtiennent les fonctionnalités suivantes :

- **Détails du message mis en quarantaine**: les boutons suivants sont disponibles :
  - **Publication de la demande**
  - **Afficher les en-têtes de messages**
  - **Afficher une prévisualisation du message**
  - **Supprimer de la quarantaine**
  - **Bloquer l’expéditeur**

  ![Boutons disponibles dans les détails du message mis en quarantaine si la stratégie de mise en quarantaine accorde à l’utilisateur des autorisations d’accès limité.](../../media/quarantine-tags-quarantined-message-details-limited-access.png)

- **Notifications de mise en** quarantaine : les boutons suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Publication de la demande**
  - **Révision**

  ![Boutons disponibles dans la notification de mise en quarantaine si la stratégie de mise en quarantaine accorde à l’utilisateur des autorisations d’accès limité.](../../media/quarantine-tags-esn-limited-access.png)

#### <a name="full-access"></a>Accès total

Si la stratégie de mise en quarantaine attribue les **autorisations** d’accès total (toutes les autorisations disponibles), les utilisateurs disposent des fonctionnalités suivantes :

- **Détails du message mis en quarantaine**: les boutons suivants sont disponibles :
  - **Message de libération**
  - **Afficher les en-têtes de messages**
  - **Afficher une prévisualisation du message**
  - **Supprimer de la quarantaine**
  - **Bloquer l’expéditeur**

  ![Boutons disponibles dans les détails du message mis en quarantaine si la stratégie de mise en quarantaine accorde à l’utilisateur des autorisations d’accès total.](../../media/quarantine-tags-quarantined-message-details-full-access.png)

- **Notifications de mise en** quarantaine : les boutons suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Version**
  - **Révision**

  ![Boutons disponibles dans la notification de mise en quarantaine si la stratégie de mise en quarantaine accorde à l’utilisateur des autorisations d’accès total.](../../media/quarantine-tags-esn-full-access.png)

### <a name="individual-permissions"></a>Autorisations individuelles

#### <a name="block-sender-permission"></a>Bloquer l’autorisation de l’expéditeur

**L’autorisation** Bloquer l’expéditeur (_PermissionToBlockSender_) contrôle l’accès au bouton qui permet aux utilisateurs d’ajouter facilement l’expéditeur du message mis en quarantaine à leur liste des expéditeurs bloqués.

- **Détails du message mis en quarantaine**:
  - **Autorisation bloquer l’expéditeur** activée : le **bouton Bloquer l’expéditeur** est disponible.
  - **Bloquer l’autorisation** de l’expéditeur désactivée : le bouton **Bloquer l’expéditeur** n’est pas disponible.

- **Notifications de mise en quarantaine**:
  - **Autorisation bloquer l’expéditeur** activée : le **bouton Bloquer l’expéditeur** est disponible.
  - **Bloquer l’autorisation** de l’expéditeur désactivée : le bouton **Bloquer l’expéditeur** n’est pas disponible.

Pour plus d’informations sur la liste des expéditeurs bloqués, voir Bloquer les [messages](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) d’une personne et utiliser Exchange Online PowerShell pour configurer la collection de listes sécurisées sur [une boîte aux lettres.](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox)

#### <a name="delete-permission"></a>Autorisations de suppression

**L’autorisation** Supprimer (_PermissionToDelete_) contrôle la possibilité pour les utilisateurs de supprimer leurs messages (messages dont l’utilisateur est un destinataire) de la quarantaine.

- **Détails du message mis en quarantaine**:
  - **Autorisation de** suppression activée : le bouton **Supprimer de** la quarantaine est disponible.
  - **Autorisation de** suppression désactivée : le bouton **Supprimer de la quarantaine** n’est pas disponible.

- **Notifications de mise en quarantaine**: aucun effet.

#### <a name="preview-permission"></a>Autorisation d’aperçu

**L’autorisation** Aperçu (_PermissionToPreview_) contrôle la possibilité pour les utilisateurs d’afficher un aperçu de leurs messages en quarantaine.

- **Détails du message mis en quarantaine**:
  - **Autorisation d’aperçu** activée : le bouton **Aperçu du message** est disponible.
  - **Autorisation d’aperçu** désactivée : le bouton **Aperçu du message** n’est pas disponible.

- **Notifications de mise en quarantaine**: aucun effet.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Autoriser les destinataires à libérer un message de l’autorisation de mise en quarantaine

L’autorisation autoriser les destinataires à libérer un message de l’autorisation de mise en quarantaine (_PermissionToRelease_) contrôle la capacité des **utilisateurs** à libérer leurs messages mis en quarantaine directement et sans l’approbation d’un administrateur.

- **Détails du message mis en quarantaine**:
  - Autorisation activée : le bouton **Libérer le message** est disponible.
  - Autorisation désactivée : le bouton **Libérer le message** n’est pas disponible.

- **Notifications de mise en quarantaine**:
  - Autorisation activée : le bouton **Libérer** est disponible.
  - Autorisation désactivée : **le** bouton Libérer n’est pas disponible.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Autoriser les destinataires à demander la libération d’un message de l’autorisation de mise en quarantaine

L’autorisation autoriser les destinataires à demander la libération d’un message de l’autorisation  de mise en quarantaine (_PermissionToRequestRelease_) contrôle la capacité des **utilisateurs** à demander la libération de leurs messages mis en quarantaine. Le message n’est publié qu’une fois qu’un administrateur a approuvé la demande.

- **Détails du message mis en quarantaine**:
  - Autorisation activée : le bouton **De publication** de la demande est disponible.
  - Autorisation désactivée : le **bouton De publication** de la demande n’est pas disponible.

- **Notifications de mise en quarantaine**:
  - Autorisation activée : le bouton **De publication** de la demande est disponible.
  - Autorisation désactivée : le **bouton De publication** de la demande n’est pas disponible.
