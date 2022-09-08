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
ms.custom: ''
description: Les administrateurs peuvent apprendre à utiliser des stratégies de quarantaine pour contrôler ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: be6661d4a40632a66a6a183d16e3bbfa0a85552f
ms.sourcegitcommit: 02a9c7f915d3a795a373b62dbdee2925966703f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2022
ms.locfileid: "67623755"
---
# <a name="quarantine-policies"></a>Stratégies de mise en quarantaine

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les stratégies de quarantaine (anciennement appelées _balises de quarantaine_) dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 permettent aux administrateurs de contrôler ce que les utilisateurs sont en mesure de faire pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine. Cette fonctionnalité est disponible dans toutes les organisations Microsoft 365 avec Exchange Online boîtes aux lettres.

Traditionnellement, les utilisateurs ont été autorisés ou refusés des niveaux d’interactivité pour les messages de quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine. Par exemple, les utilisateurs peuvent afficher et publier des messages qui ont été mis en quarantaine par filtrage anti-courrier indésirable en tant que courrier indésirable ou en bloc, mais ils ne peuvent pas afficher ou libérer des messages qui ont été mis en quarantaine comme hameçonnage ou programmes malveillants à haut niveau de confiance.

Pour les [fonctionnalités de protection prises en charge](#step-2-assign-a-quarantine-policy-to-supported-features), les stratégies de quarantaine spécifient ce que les utilisateurs sont autorisés à faire à leurs propres messages (messages où ils sont destinataires) en quarantaine et dans _les notifications de quarantaine_. [Les notifications de quarantaine](use-spam-notifications-to-release-and-report-quarantined-messages.md) remplacent les notifications de courrier indésirable de l’utilisateur final. Ces notifications sont désormais contrôlées par des stratégies de quarantaine et contiennent des informations sur les messages mis en quarantaine pour toutes les fonctionnalités de protection prises en charge (pas seulement les verdicts de stratégie anti-courrier indésirable et de stratégie anti-hameçonnage).

Les stratégies de quarantaine par défaut qui appliquent les fonctionnalités utilisateur historiques sont automatiquement affectées aux actions dans les fonctionnalités de protection prises en charge qui mettent en quarantaine les messages. Vous pouvez également créer des stratégies de quarantaine personnalisées et les affecter aux fonctionnalités de protection prises en charge pour autoriser ou empêcher les utilisateurs d’effectuer des actions spécifiques sur ces types de messages mis en quarantaine.

Les autorisations de stratégie de quarantaine individuelles sont combinées dans les groupes d’autorisations prédéfinies suivants :

- Pas d’accès
- Accès limité
- Accès complet

Les autorisations de stratégie de quarantaine individuelles contenues dans les groupes d’autorisations prédéfinies sont décrites dans le tableau suivant :

|Autorisation|Pas d’accès|Accès limité|Accès complet|
|---|:---:|:---:|:---:|
|**Bloquer l’expéditeur** (_PermissionToBlockSender_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Delete** (_PermissionToDelete_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Préversion** (_PermissionToPreview_)||![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|**Autoriser les destinataires à libérer un message de la quarantaine** (_PermissionToRelease_)<sup>\*</sup>|||![Marque de vérification.](../../media/checkmark.png)|
|**Autoriser les destinataires à demander la mise en quarantaine d’un message** (_PermissionToRequestRelease_)||![Coche](../../media/checkmark.png)||

<sup>\*</sup>**L’autorisation autoriser les destinataires à publier un message à partir de l’autorisation de mise en quarantaine** n’est pas respectée dans les stratégies anti-programme malveillant ou pour le verdict de hameçonnage à haut niveau de confiance dans les stratégies anti-courrier indésirable. Les utilisateurs ne peuvent pas libérer leurs propres programmes malveillants ou messages de hameçonnage à haut niveau de confiance à partir de la quarantaine. Au mieux, vous pouvez utiliser l’option **Autoriser les destinataires pour demander la libération d’un message à partir de l’autorisation de mise en quarantaine** .

Les stratégies de quarantaine par défaut, leurs groupes d’autorisations associés et si les notifications de quarantaine sont activées sont décrites dans le tableau suivant :

|Stratégie de quarantaine par défaut|Groupe d’autorisations utilisé|Notifications de quarantaine activées ?|
|---|:---:|:---:|
|AdminOnlyAccessPolicy|Pas d’accès|Non|
|DefaultFullAccessPolicy|Accès complet|Non|
|NotificationEnabledPolicy<sup>\*</sup>|Accès complet|Oui|

Si vous n’aimez pas les autorisations par défaut dans les groupes d’autorisations prédéfinies ou si vous souhaitez activer les notifications de quarantaine, créez et utilisez des stratégies de quarantaine personnalisées. Pour plus d’informations sur le rôle de chaque autorisation, consultez la section [Détails des autorisations](#quarantine-policy-permission-details) de stratégie de quarantaine plus loin dans cet article.

Vous créez et affectez des stratégies de quarantaine dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online ; powerShell EOP autonome dans les organisations EOP sans boîtes aux lettres Exchange Online).

> [!NOTE]
> La durée pendant laquelle les messages mis en quarantaine sont maintenus en quarantaine avant leur expiration est contrôlée par le **courrier indésirable conservé en quarantaine pendant ce nombre de jours** (_QuarantineRetentionPeriod_) dans les stratégies anti-courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).
>
> Si vous modifiez la stratégie de quarantaine affectée à une fonctionnalité de protection prise en charge, la modification affecte les messages mis en quarantaine _après_ la modification. Les messages précédemment mis en quarantaine par cette fonctionnalité de protection ne sont pas affectés par les paramètres de la nouvelle affectation de stratégie de quarantaine.

## <a name="full-access-permissions-and-quarantine-notifications"></a>Autorisations d’accès complet et notifications de mise en quarantaine

<sup>\*</sup> La stratégie de quarantaine nommée NotificationEnabledPolicy n’est pas présente dans tous les environnements. Vous disposerez de la stratégie de quarantaine NotificationEnabledPolicy si votre organisation répond aux deux exigences suivantes :

- Votre organisation existait avant que la fonctionnalité de stratégie de quarantaine ne soit activée (fin juillet/début août 2021).
- Vous aviez une ou plusieurs stratégies [anti-courrier indésirable](configure-your-spam-filter-policies.md) (stratégie anti-courrier indésirable par défaut ou stratégies anti-courrier indésirable personnalisées) où le paramètre **Activer les notifications de courrier indésirable de l’utilisateur final** était activé.

Comme décrit précédemment, les notifications de quarantaine dans les stratégies de quarantaine remplacent les notifications de courrier indésirable de l’utilisateur final que vous avez utilisées pour activer ou désactiver les stratégies anti-courrier indésirable. La stratégie de quarantaine intégrée nommée DefaultFullAccessPolicy duplique les _autorisations historiques pour les_ messages mis en quarantaine, mais _les notifications de quarantaine_ ne sont pas activées dans la stratégie de quarantaine. Et, comme vous ne pouvez pas modifier la stratégie intégrée, vous ne pouvez pas activer les notifications de quarantaine dans DefaultFullAccessPolicy.

Pour fournir les autorisations de DefaultFullAccessPolicy, mais avec les notifications de quarantaine activées, nous avons créé la stratégie nommée NotificationEnabledPolicy à utiliser à la place de DefaultFullAccessPolicy pour les organisations qui en avaient besoin (les organisations où les notifications de courrier indésirable de l’utilisateur final ont été activées).

Pour les nouvelles organisations ou les organisations plus anciennes qui n’ont jamais eu de notifications de courrier indésirable pour les utilisateurs finaux activées dans les stratégies anti-courrier indésirable, vous n’aurez pas la stratégie de quarantaine nommée NotificationEnabledPolicy. Pour activer les notifications de quarantaine, vous pouvez créer et utiliser des stratégies de quarantaine personnalisées dans lesquelles les notifications de quarantaine sont activées.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour afficher, créer, modifier ou supprimer des stratégies de quarantaine, vous devez être membre des rôles **Gestion de l’organisation**, **Administrateur de la sécurité ou Administrateur** de la **quarantaine** dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

## <a name="step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Étape 1 : Créer des stratégies de quarantaine dans le portail Microsoft 365 Defender

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à Email & stratégies de **collaboration** \> **& stratégies** de **menace de** \> règles \> **en quarantaine** dans la section **Règles**. Ou, pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

   :::image type="content" source="../../media/mdo-quarantine-policy-page.png" alt-text="Page stratégie de mise en quarantaine dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-quarantine-policy-page.png":::

2. Dans la page **Stratégies de quarantaine** , cliquez sur ![l’icône Ajouter une stratégie personnalisée.](../../media/m365-cc-sc-create-icon.png) **Ajouter une stratégie personnalisée**.

3. **L’Assistant Nouvelle stratégie** s’ouvre. Dans la page **Nom de** la stratégie, entrez un nom court mais unique dans la zone **Nom** de la stratégie. Vous devez identifier et sélectionner la stratégie de quarantaine par nom dans les étapes à venir. Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **d’accès aux messages du destinataire** , sélectionnez l’une des valeurs suivantes :
   - **Accès limité** : les autorisations individuelles incluses dans ce groupe d’autorisations sont décrites plus haut dans cet article.
   - **Définir un accès spécifique (Avancé)** : utilisez cette valeur pour spécifier des autorisations personnalisées. Configurez les paramètres suivants qui s’affichent :
     - **Sélectionner la préférence d’action de mise en production** : Sélectionnez l’une des valeurs suivantes :
       - Vide : il s’agit de la valeur par défaut.
       - **Autoriser les destinataires à libérer un message de la quarantaine**
       - **Autoriser les destinataires à demander la libération d’un message de quarantaine**
     - **Sélectionnez des actions supplémentaires que les destinataires peuvent effectuer sur les messages mis en quarantaine** : sélectionnez certaines valeurs, toutes ou aucune des valeurs suivantes :
       - **Supprimer**
       - **Aperçu**
       - **Bloquer l’expéditeur**

   Ces autorisations et leur effet sur les messages mis en quarantaine et dans les notifications de mise en quarantaine sont décrits dans la section [détails des autorisations](#quarantine-policy-permission-details) de stratégie de quarantaine plus loin dans cet article.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page de **notification de courrier indésirable de l’utilisateur final** , **sélectionnez Activer** l’activation des notifications de mise en quarantaine (anciennement notifications de courrier indésirable de l’utilisateur final). Lorsque vous avez terminé, cliquez sur **Suivant**.

   > [!NOTE]
   > Comme expliqué précédemment, les stratégies intégrées (AdminOnlyAccessPolicy ou DefaultFullAccessPolicy) n’ont pas de notifications en quarantaine activées, et vous ne pouvez pas modifier les stratégies.

6. Dans la page **Vérifier** la stratégie, passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

7. Dans la page de confirmation qui s’affiche, cliquez sur **Terminé**.

Vous êtes maintenant prêt à affecter la stratégie de quarantaine à une fonctionnalité de quarantaine, comme décrit dans la section [Étape 2](#step-2-assign-a-quarantine-policy-to-supported-features) .

### <a name="create-quarantine-policies-in-powershell"></a>Créer des stratégies de quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour créer des stratégies de quarantaine, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez l’applet de commande **New-QuarantinePolicy**.

> [!NOTE]
> Si vous n’utilisez pas le paramètre _ESNEnabled_ et la valeur `$true`, les notifications de quarantaine sont désactivées.

#### <a name="use-the-enduserquarantinepermissionsvalue-parameter"></a>Utiliser le paramètre EndUserQuarantinePermissionsValue

Pour créer une stratégie de quarantaine à l’aide du paramètre _EndUserQuarantinePermissionsValue_ , utilisez la syntaxe suivante :

```powershell
New-QuarantinePolicy -Name "<UniqueName>" -EndUserQuarantinePermissionsValue <0 to 236> [-EsnEnabled $true]
```

Le paramètre _EndUserQuarantinePermissionsValue_ utilise une valeur décimale convertie à partir d’une valeur binaire. La valeur binaire correspond aux autorisations de mise en quarantaine de l’utilisateur final disponibles dans un ordre spécifique. Pour chaque autorisation, la valeur 1 est égale à True et la valeur 0 est False.

L’ordre et les valeurs requis pour chaque autorisation individuelle sont décrits dans le tableau suivant :

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

<sup>\*</sup> La valeur 0 ne masque pas le bouton **Afficher l’en-tête du message** dans les détails du message mis en quarantaine (le bouton est toujours disponible).

<sup>\*\*</sup> Ce paramètre n’est pas utilisé (la valeur 0 ou 1 ne fait rien).

<sup>\*\*\*</sup> Ne définissez pas ces deux valeurs sur 1. Définissez l’un sur 1 et l’autre sur 0, ou les deux sur 0.

Pour les autorisations d’accès limitées, les valeurs requises sont les suivantes :

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

Cet exemple crée une stratégie de quarantaine nommée LimitedAccess avec des notifications de quarantaine activées qui attribuent les autorisations d’accès limité, comme décrit dans le tableau précédent.

```powershell
New-QuarantinePolicy -Name LimitedAccess -EndUserQuarantinePermissionsValue 27 -EsnEnabled $true
```

Pour les autorisations personnalisées, utilisez le tableau précédent pour obtenir la valeur binaire qui correspond aux autorisations souhaitées. Convertissez la valeur binaire en valeur décimale et utilisez la valeur décimale pour le paramètre _EndUserQuarantinePermissionsValue_ . N’utilisez pas la valeur binaire pour la valeur du paramètre.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-QuarantinePolicy](/powershell/module/exchange/new-quarantinepolicy).

## <a name="step-2-assign-a-quarantine-policy-to-supported-features"></a>Étape 2 : Affecter une stratégie de quarantaine aux fonctionnalités prises en charge

Dans les fonctionnalités _de protection prises en charge_ qui met en quarantaine les messages électroniques, vous pouvez affecter une stratégie de quarantaine aux actions de quarantaine disponibles. Les fonctionnalités qui mettent en quarantaine les messages et la disponibilité des stratégies de quarantaine sont décrites dans le tableau suivant :

|Fonctionnalité|Stratégies de quarantaine prises en charge ?|Stratégies de quarantaine par défaut utilisées|
|---|:---:|---|
|[Stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md) : <ul><li>**Courrier indésirable** (_SpamAction_)</li><li>**Courrier indésirable à haut niveau de confiance** (_HighConfidenceSpamAction_)</li><li>**Hameçonnage** (_PhishSpamAction_)</li><li>**Hameçonnage à haut niveau de confiance** (_HighConfidencePhishAction_)</li><li>**Bulk** (_BulkSpamAction_)</li></ul>|Oui|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>AdminOnlyAccessPolicy (aucun accès)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li></ul>|
|Stratégies anti-hameçonnage: <ul><li>[Protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) (_AuthenticationFailAction_)</li><li>[Protection de l’emprunt d’identité dans Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) :<ul><li>**Si le message est détecté en tant qu’utilisateur emprunt d’identité** (_TargetedUserProtectionAction_)</li><li>**Si le message est détecté comme un domaine usurpé d’identité** (_TargetedDomainProtectionAction_)</li><li>**Si l’intelligence de boîte aux lettres détecte et emprunte l’identité de l’utilisateur** (_MailboxIntelligenceProtectionAction_)</li></ul></li></ul>|Oui|<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>Protection de l’emprunt d’identité :<ul><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li><li>DefaultFullAccessPolicy<sup>\*</sup> (accès complet)</li></ul></li></ul>|
|[Stratégies anti-programme malveillant](configure-anti-malware-policies.md) : tous les messages détectés sont toujours mis en quarantaine.|Oui|AdminOnlyAccessPolicy (aucun accès)|
|[Protection des pièces jointes sécurisées](safe-attachments.md) : <ul><li>Email messages avec des pièces jointes mises en quarantaine comme programmes malveillants par des stratégies de pièces jointes sécurisées (_Activer_ et _action_)</li><li>Fichiers mis en quarantaine en tant que programmes [malveillants par des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li></ul>|<ul><li>Oui</li><li>Non</li></ul>|<ul><li>AdminOnlyAccessPolicy (aucun accès)</li><li>s/o</li></ul>|
|[Règles de flux de messagerie](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (également appelées règles de transport) avec l’action : **Remettre le message à la quarantaine hébergée** (_quarantaine_).|Non|s/o|

<sup>\*</sup> Comme [décrit précédemment dans cet article](#full-access-permissions-and-quarantine-notifications), votre organisation peut utiliser NotificationEnabledPolicy au lieu de DefaultFullAccessPolicy. La seule différence entre ces deux stratégies de quarantaine est que les notifications de quarantaine sont activées dans NotificationEnabledPolicy et désactivées dans DefaultFullAccessPolicy.

Les stratégies de quarantaine par défaut, les groupes d’autorisations prédéfinis et les autorisations sont décrits au [début de cet article](#quarantine-policies) et [plus loin dans cet article](#preset-permissions-groups).

> [!NOTE]
> Si vous êtes satisfait des autorisations par défaut de l’utilisateur final et des notifications de quarantaine fournies (ou non) par les stratégies de quarantaine par défaut, vous n’avez rien à faire. Si vous souhaitez ajouter ou supprimer des fonctionnalités de l’utilisateur final (les boutons disponibles) pour les messages mis en quarantaine par l’utilisateur, ou activer des notifications de quarantaine et ajouter ou supprimer les mêmes fonctionnalités dans les notifications de quarantaine, vous pouvez affecter une stratégie de quarantaine différente à l’action de quarantaine.

## <a name="assign-quarantine-policies-in-supported-policies-in-the-microsoft-365-defender-portal"></a>Affecter des stratégies de quarantaine dans les stratégies prises en charge dans le portail Microsoft 365 Defender

> [!NOTE]
> Les utilisateurs ne peuvent pas publier leurs propres messages qui ont été mis en quarantaine en tant que programmes malveillants (stratégies anti-programmes malveillants) ou hameçonnage à haut niveau de confiance (stratégies anti-courrier indésirable), quelle que soit la façon dont la stratégie de mise en quarantaine est configurée. Au mieux, les administrateurs peuvent configurer la stratégie de quarantaine afin que les utilisateurs puissent demander la publication de leurs programmes malveillants mis en quarantaine ou des messages de hameçonnage à haut niveau de confiance.

### <a name="anti-spam-policies"></a>Stratégies anti-courrier indésirable

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à Email & stratégies de **collaboration** \> **& règles** \> **anti-courrier**  \> indésirable dans la section **Stratégies**.

   Ou, pour accéder directement à la page **Ant-spam policies** , utilisez <https://security.microsoft.com/antispam>.

2. Dans la page **Stratégies anti-courrier indésirable** , effectuez l’une des étapes suivantes :
   - Recherchez et sélectionnez une stratégie anti-courrier indésirable **entrante** existante.
   - Créez une stratégie anti-courrier indésirable **entrante** .

3. Effectuez l’une des étapes suivantes :
   - **Modifier l’existant** : sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le menu volant détails de la stratégie, accédez à la section **Actions** , puis cliquez sur **Modifier les actions**.
   - **Créer nouveau** : dans l’Assistant Nouvelle stratégie, accédez à la page **Actions** .

4. Dans la page **Actions** , chaque verdict qui contient l’action Message de **mise en quarantaine** aura également la zone **Sélectionner la stratégie de quarantaine** pour vous permettre de sélectionner une stratégie de quarantaine correspondante.

   Remarque : lorsque vous **créez** une stratégie, une valeur **de stratégie de quarantaine Select** vide indique que la stratégie de quarantaine par défaut pour ce verdict est utilisée. Lorsque vous modifiez ultérieurement la stratégie, les valeurs vides sont remplacées par les noms de stratégie de quarantaine par défaut réels, comme décrit dans le tableau précédent.

   :::image type="content" source="../../media/quarantine-tags-in-anti-spam-policies.png" alt-text="Sélections de la stratégie de quarantaine dans une stratégie anti-courrier indésirable" lightbox="../../media/quarantine-tags-in-anti-spam-policies.png":::

Des instructions complètes sur la création et la modification des stratégies anti-courrier indésirable sont décrites dans Configurer les stratégies [anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

#### <a name="anti-spam-policies-in-powershell"></a>Stratégies anti-courrier indésirable dans PowerShell

Si vous préférez utiliser PowerShell pour attribuer des stratégies de quarantaine dans des stratégies anti-courrier indésirable, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-HostedContentFilterPolicy -Name "<Unique name>" | Set-HostedContentFilterPolicy -Identity "<Policy name>"> [-SpamAction Quarantine] [-SpamQuarantineTag <QuarantineTagName>] [-HighConfidenceSpamAction Quarantine] [-HighConfidenceSpamQuarantineTag <QuarantineTagName>] [-PhishSpamAction Quarantine] [-PhishQuarantineTag <QuarantineTagName>] [-HighConfidencePhishQuarantineTag <QuarantineTagName>] [-BulkSpamAction Quarantine] [-BulkQuarantineTag <QuarantineTagName>] ...
```

**Remarques** :

- La valeur par défaut des paramètres _PhishSpamAction_ et _HighConfidencePhishAction_ est Quarantine. Vous n’avez donc pas besoin d’utiliser ces paramètres lorsque vous créez de nouvelles stratégies de filtre de courrier indésirable dans PowerShell. Pour les paramètres _SpamAction_, _HighConfidenceSpamAction_ et _BulkSpamAction_ dans les stratégies anti-courrier indésirable nouvelles ou existantes, la stratégie de quarantaine n’est effective que si la valeur est Quarantaine.

  Pour afficher les valeurs de paramètre importantes dans les stratégies anti-courrier indésirable existantes, exécutez la commande suivante :

  ```powershell
  Get-HostedContentFilterPolicy | Format-List Name,*SpamAction,HighConfidencePhishAction,*QuarantineTag
  ```

  Pour plus d’informations sur les valeurs d’action par défaut et les valeurs d’action recommandées pour Standard et Strict, consultez [les paramètres de stratégie anti-courrier indésirable EOP](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

- Lorsque vous créez de nouvelles stratégies anti-courrier indésirable, un verdict de filtrage du courrier indésirable sans paramètre de stratégie de quarantaine correspondant signifie que la [stratégie de quarantaine par défaut](#step-2-assign-a-quarantine-policy-to-supported-features) pour ce verdict est utilisée.

  Vous devez remplacer une stratégie de quarantaine par défaut par une stratégie de quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine pour ce verdict de filtrage du courrier indésirable particulier.

- Une nouvelle stratégie anti-courrier indésirable dans PowerShell nécessite une stratégie de filtrage du courrier indésirable (paramètres) à l’aide de l’applet de commande **New-HostedContentFilterPolicy** et une règle de filtre de courrier indésirable exclusive (filtres de destinataires) à l’aide de l’applet de commande **New-HostedContentFilterRule** . Pour obtenir des instructions, consultez [Utiliser PowerShell pour créer des stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md#use-powershell-to-create-anti-spam-policies).

Cet exemple crée une stratégie de filtrage du courrier indésirable nommée Research Department avec les paramètres suivants :

- L’action pour tous les verdicts de filtrage du courrier indésirable est définie sur Quarantaine.
- La stratégie de quarantaine personnalisée nommée NoAccess qui affecte **aucune autorisation d’accès** remplace toutes les stratégies de quarantaine par défaut qui n’affectent pas encore **d’autorisations d’accès** par défaut.

```powershell
New-HostedContentFilterPolicy -Name "Research Department" -SpamAction Quarantine -SpamQuarantineTag NoAccess -HighConfidenceSpamAction Quarantine -HighConfidenceSpamQuarantineTag NoAction -PhishSpamAction Quarantine -PhishQuarantineTag NoAction -BulkSpamAction Quarantine -BulkQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-HostedContentFilterPolicy](/powershell/module/exchange/new-hostedcontentfilterpolicy).

Cet exemple modifie la stratégie de filtrage du courrier indésirable existante nommée Ressources humaines. L’action pour le verdict de mise en quarantaine du courrier indésirable est définie sur Quarantaine, et la stratégie de quarantaine personnalisée nommée NoAccess est affectée.

```powershell
Set-HostedContentFilterPolicy -Identity "Human Resources" -SpamAction Quarantine -SpamQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-HostedContentFilterPolicy](/powershell/module/exchange/set-hostedcontentfilterpolicy).

### <a name="anti-phishing-policies"></a>Politiques anti-hameçonnage

L’intelligence par usurpation d’identité est disponible dans EOP et Defender pour Office 365. La protection de l’emprunt d’identité de l’utilisateur, la protection de l’emprunt d’identité de domaine et l’intelligence de boîte aux lettres sont disponibles uniquement dans Defender pour Office 365. Si vous souhaitez en savoir plus, consultez l’article [Stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md).

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à Email &  stratégies de **collaboration** \> **& règles** \>  \> de protection contre le hameçonnage dans la section **Stratégies**.

   Ou, pour accéder directement à la page **Ant-spam policies** , utilisez <https://security.microsoft.com/antiphishing>.

2. Dans la page **Anti-hameçonnage** , effectuez l’une des étapes suivantes :
   - Recherchez et sélectionnez une stratégie anti-hameçonnage existante.
   - Créez une stratégie anti-hameçonnage.

3. Effectuez l’une des étapes suivantes :
   - **Modifier l’existant** : sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le menu volant des détails de la stratégie, accédez à la section **Paramètres de protection** , puis cliquez sur **Modifier les paramètres de protection**.
   - **Créer nouveau** : dans l’Assistant Nouvelle stratégie, accédez à la page **Actions** .

4. Dans la page **Paramètres de protection** , vérifiez que les paramètres suivants sont activés et configurés selon les besoins :
   - **Utilisateurs activés pour la protection** : spécifiez les utilisateurs.
   - **Domaines activés pour la protection** : sélectionnez **Inclure les domaines que je possède** et/ou **Inclure des domaines personnalisés** et spécifiez les domaines.
   - **Activer la veille des boîtes aux lettres**
   - **Activer l’intelligence pour la protection de l’emprunt d’identité**
   - **Activer l’intelligence par usurpation d’identité**

5. Effectuez l’une des étapes suivantes :
   - **Modifier l’existant** : dans le menu volant détails de la stratégie, accédez à la section **Actions** , puis cliquez sur **Modifier les actions**.
   - **Créer nouveau** : dans l’Assistant Nouvelle stratégie, accédez à la page **Actions** .

6. Dans la page **Actions** , chaque verdict qui contient **la mise en quarantaine de l’action de message** aura également la zone **Appliquer la stratégie de quarantaine** pour vous permettre de sélectionner une stratégie de quarantaine correspondante.

   Remarque : lorsque vous **créez** une stratégie, une valeur de stratégie **Appliquer la mise en quarantaine** vide indique que la stratégie de quarantaine par défaut pour cette action est utilisée. Lorsque vous modifiez ultérieurement la stratégie, les valeurs vides sont remplacées par les noms de stratégie de quarantaine par défaut réels, comme décrit dans le tableau précédent.

   :::image type="content" source="../../media/quarantine-tags-in-anti-phishing-policies.png" alt-text="Sélections de la stratégie de quarantaine dans une stratégie anti-hameçonnage" lightbox="../../media/quarantine-tags-in-anti-phishing-policies.png":::

Des instructions complètes sur la création et la modification des stratégies anti-hameçonnage sont disponibles dans les rubriques suivantes :

- [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md)
- [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md)

#### <a name="anti-phishing-policies-in-powershell"></a>Stratégies anti-hameçonnage dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de quarantaine dans des stratégies anti-hameçonnage, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-AntiPhishPolicy -Name "<Unique name>" | Set-AntiPhishPolicy -Identity "<Policy name>"> [-EnableSpoofIntelligence $true] [-AuthenticationFailAction Quarantine] [-SpoofQuarantineTag <QuarantineTagName>] [-EnableMailboxIntelligence $true] [-EnableMailboxIntelligenceProtection $true] [-MailboxIntelligenceProtectionAction Quarantine] [-MailboxIntelligenceQuarantineTag <QuarantineTagName>] [-EnableOrganizationDomainsProtection $true] [-EnableTargetedDomainsProtection $true] [-TargetedDomainProtectionAction Quarantine] [-TargetedDomainQuarantineTag <QuarantineTagName>] [-EnableTargetedUserProtection $true] [-TargetedUserProtectionAction Quarantine] [-TargetedUserQuarantineTag <QuarantineTagName>] ...
```

**Remarques** :

- Les paramètres _Enable\*_ sont nécessaires pour activer les fonctionnalités de protection spécifiques. La valeur par défaut des paramètres _EnableMailboxIntelligence_ et _EnableSpoofIntelligence_ est $true. Vous n’avez donc pas besoin d’utiliser ces paramètres lorsque vous créez de nouvelles stratégies anti-hameçonnage dans PowerShell. Tous les autres paramètres _Enable\*_ doivent avoir la valeur $true afin que vous puissiez définir la valeur Quarantaine dans les paramètres Action correspondants _\*_ pour affecter ensuite une stratégie de quarantaine. Aucun des paramètres _*\Action_ n’a la valeur par défaut Quarantaine.

  Pour afficher les valeurs de paramètre importantes dans les stratégies anti-hameçonnage existantes, exécutez la commande suivante :

  ```powershell
  Get-AntiPhishPolicy | Format-List Name,Enable*Intelligence,Enable*Protection,*Action,*QuarantineTag
  ```

  Pour plus d’informations sur les valeurs d’action par défaut et les valeurs d’action recommandées pour Standard et Strict, consultez [les paramètres de stratégie anti-hameçonnage EOP et les](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) paramètres d’emprunt [d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](recommended-settings-for-eop-and-office365.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

- Lorsque vous créez des stratégies anti-hameçonnage, une action anti-hameçonnage sans paramètre de stratégie de quarantaine correspondant signifie que la [stratégie de quarantaine par défaut](#step-2-assign-a-quarantine-policy-to-supported-features) pour ce verdict est utilisée.

  Vous devez remplacer une stratégie de quarantaine par défaut par une stratégie de quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine pour ce verdict particulier.

- Une nouvelle stratégie anti-hameçonnage dans PowerShell nécessite une stratégie anti-hameçonnage (paramètres) à l’aide de l’applet de commande **New-AntiPhishPolicy** et une règle anti-hameçonnage exclusive (filtres de destinataires) à l’aide de l’applet de commande **New-AntiPhishRule** . Pour obtenir des instructions, consultez les rubriques suivantes :
  - [Utiliser PowerShell pour configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)
  - [Utiliser Exchange Online PowerShell pour configurer des stratégies anti-hameçonnage](configure-mdo-anti-phishing-policies.md#use-exchange-online-powershell-to-configure-anti-phishing-policies)

Cet exemple crée une stratégie anti-hameçonnage nommée Research Department avec les paramètres suivants :

- L’action pour tous les verdicts de filtrage du courrier indésirable est définie sur Quarantaine.
- La stratégie de quarantaine personnalisée nommée NoAccess qui affecte **aucune autorisation d’accès** remplace toutes les stratégies de quarantaine par défaut qui n’affectent pas encore **d’autorisations d’accès** par défaut.

```powershell
New-AntiPhishPolicy -Name "Research Department" -AuthenticationFailAction Quarantine -SpoofQuarantineTag NoAccess -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -MailboxIntelligenceQuarantineTag NoAccess -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-AntiPhishPolicy](/powershell/module/exchange/new-antiphishpolicy).

Cet exemple modifie la stratégie anti-hameçonnage existante nommée Ressources humaines. L’action pour les messages détectés par l’emprunt d’identité de l’utilisateur et l’emprunt d’identité de domaine est définie sur Quarantaine, et la stratégie de quarantaine personnalisée nommée NoAccess est affectée.

```powershell
Set-AntiPhishPolicy -Identity "Human Resources" -EnableTargetedDomainsProtection $true -TargetedDomainProtectionAction Quarantine -TargetedDomainQuarantineTag NoAccess -EnableTargetedUserProtection $true -TargetedUserProtectionAction Quarantine -TargetedUserQuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AntiPhishPolicy](/powershell/module/exchange/set-antiphishpolicy).

### <a name="anti-malware-policies"></a>Stratégies anti-programme malveillant

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à Email & stratégies de **collaboration** \> **& règles** \> **de** \> protection **contre les programmes malveillants** dans la section **Stratégies**.

   Ou, pour accéder directement à la page **Anti-programme malveillant** , utilisez <https://security.microsoft.com/antimalwarev2>.

2. Dans la page **Anti-programme malveillant** , effectuez l’une des étapes suivantes :
   - Recherchez et sélectionnez une stratégie anti-programme malveillant existante.
   - Créez une stratégie anti-programme malveillant.

3. Effectuez l’une des étapes suivantes :
   - **Modifier l’existant** : sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le menu volant des détails de la stratégie, accédez à la section **Paramètres de protection** , puis cliquez sur **Modifier les paramètres de protection**.
   - **Créer nouveau** : dans l’Assistant Nouvelle stratégie, accédez à la page **Actions** .

4. Dans la page **Paramètres de protection** , sélectionnez une stratégie de quarantaine dans la zone **stratégie de quarantaine** .

   Remarque : lorsque vous **créez** une stratégie, une valeur de stratégie **de quarantaine** vide indique la stratégie de quarantaine par défaut utilisée. Lorsque vous modifiez ultérieurement la stratégie, la valeur vide est remplacée par le nom de stratégie de quarantaine par défaut réel, comme décrit dans le tableau précédent.

#### <a name="anti-malware-policies-in-powershell"></a>Stratégies anti-programme malveillant dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de quarantaine dans des stratégies anti-programme malveillant, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-AntiMalwarePolicy -Name "<Unique name>" | Set-AntiMalwarePolicy -Identity "<Policy name>"> [-QuarantineTag <QuarantineTagName>]
```

**Remarques** :

- Lorsque vous créez des stratégies anti-programme malveillant sans utiliser le paramètre QuarantineTag lorsque vous créez une stratégie anti-programme malveillant, la stratégie de quarantaine par défaut pour les détections de programmes malveillants est utilisée (AdminOnlyAccessPolicy).

  Vous devez remplacer la stratégie de quarantaine par défaut par une stratégie de quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages mis en quarantaine en tant que programmes malveillants.

  Pour afficher les valeurs de paramètre importantes dans les stratégies anti-hameçonnage existantes, exécutez la commande suivante :

  ```powershell
  Get-MalwareFilterPolicy | Format-Table Name,QuarantineTag
  ```

- Une nouvelle stratégie anti-programme malveillant dans PowerShell nécessite une stratégie de filtrage des programmes malveillants (paramètres) à l’aide de l’applet de commande **New-MalwareFilterPolicy** et une règle de filtre de programmes malveillants exclusive (filtres de destinataires) à l’aide de l’applet de commande **New-MalwareFilterRule** . Pour obtenir des instructions, consultez [Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies anti-programme malveillant](configure-anti-malware-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-anti-malware-policies).

Cet exemple crée une stratégie de filtre de programmes malveillants nommée Research Department qui utilise la stratégie de quarantaine personnalisée nommée NoAccess qui n’affecte **aucune autorisation d’accès** aux messages mis en quarantaine.

```powershell
New-MalwareFilterPolicy -Name "Research Department" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Cet exemple modifie la stratégie de filtre de programmes malveillants existante nommée Ressources humaines en affectant la stratégie de quarantaine personnalisée nommée NoAccess qui n’affecte **aucune autorisation d’accès** aux messages mis en quarantaine.

```powershell
New-MalwareFilterPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

### <a name="safe-attachments-policies-in-defender-for-office-365"></a>Stratégies de pièces jointes sécurisées dans Defender pour Office 365

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à Email & stratégies de **collaboration** \> **& règles** - **Pièces jointes sécurisées des** **stratégies** \> \> de menace dans la section **Stratégies**.

   Ou, pour accéder directement à la page **Pièces jointes sécurisées** , utilisez <https://security.microsoft.com/safeattachmentv2>.

2. Dans la page **Pièces jointes sécurisées** , effectuez l’une des étapes suivantes :
   - Recherchez et sélectionnez une stratégie de pièces jointes sécurisées existante.
   - Créez une stratégie de pièces jointes sécurisées.

3. Effectuez l’une des étapes suivantes :
   - **Modifier l’existant** : sélectionnez la stratégie en cliquant sur le nom de la stratégie. Dans le menu volant des détails de la stratégie, accédez à la section **Paramètres** , puis cliquez sur **Modifier les paramètres**.
   - **Créer :** dans l’Assistant Nouvelle stratégie, accédez à la page **Paramètres** .

4. Dans la page **Paramètres** , procédez comme suit :
   1. **Réponse de programmes malveillants inconnus des pièces jointes fiables** : Sélectionnez **Bloquer**, **Remplacer** ou **Livraison dynamique**.
   2. Sélectionnez une stratégie de quarantaine dans la zone **stratégie de quarantaine** .

   Remarque : lorsque vous **créez** une stratégie, une valeur de stratégie **de quarantaine** vide indique que la stratégie de quarantaine par défaut est utilisée. Lorsque vous modifiez ultérieurement la stratégie, la valeur vide est remplacée par le nom de stratégie de quarantaine par défaut réel, comme décrit dans le tableau précédent.

Des instructions complètes sur la création et la modification de stratégies de pièces jointes sécurisées sont décrites dans [Configurer des stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md).

#### <a name="safe-attachments-policies-in-powershell"></a>Stratégies de pièces jointes sécurisées dans PowerShell

Si vous préférez utiliser PowerShell pour affecter des stratégies de quarantaine dans les stratégies pièces jointes sécurisées, connectez-vous à Exchange Online PowerShell ou Exchange Online Protection PowerShell et utilisez la syntaxe suivante :

```powershell
<New-SafeAttachmentPolicy -Name "<Unique name>" | Set-SafeAttachmentPolicy -Identity "<Policy name>"> -Enable $true -Action <Block | Replace | DynamicDelivery> [-QuarantineTag <QuarantineTagName>]
```

**Remarques** :

- Les valeurs de paramètre _Action_ Block, Replace ou DynamicDelivery peuvent entraîner la mise en quarantaine des messages (la valeur Allow ne met pas en quarantaine les messages). La valeur du paramètre _Action_ est significative uniquement lorsque la valeur du paramètre _Enable_ est `$true`.

- Lorsque vous créez des stratégies de pièces jointes sécurisées sans utiliser le paramètre QuarantineTag, la stratégie de quarantaine par défaut pour les détections de pièces jointes sécurisées dans le courrier électronique est utilisée (AdminOnlyAccessPolicy).

  Vous devez remplacer la stratégie de quarantaine par défaut par une stratégie de quarantaine personnalisée uniquement si vous souhaitez modifier les fonctionnalités par défaut de l’utilisateur final sur les messages électroniques mis en quarantaine par les stratégies pièces jointes sécurisées.

  Pour afficher les valeurs de paramètre importantes, exécutez la commande suivante :

  ```powershell
  Get-SafeAttachmentPolicy | Format-List Name,Enable,Action,QuarantineTag
  ```

- Une nouvelle stratégie de pièces jointes sécurisées dans PowerShell nécessite une stratégie de pièce jointe sécurisée (paramètres) à l’aide de l’applet de commande **New-SafeAttachmentPolicy** et une règle de pièce jointe sécurisée exclusive (filtres de destinataires) à l’aide de l’applet **de commande New-SafeAttachmentRule** . Pour obtenir des instructions, consultez [Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour configurer des stratégies de pièces jointes sécurisées](set-up-safe-attachments-policies.md#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies).

Cet exemple crée une stratégie de pièce jointe sécurisée nommée Research Department qui bloque les messages détectés et utilise la stratégie de quarantaine personnalisée nommée NoAccess qui affecte **aucune autorisation d’accès** aux messages mis en quarantaine.

```powershell
New-SafeAttachmentPolicy -Name "Research Department" -Enable $true -Action Block -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-MalwareFilterPolicy](/powershell/module/exchange/new-malwarefilterpolicy).

Cet exemple modifie la stratégie de pièce jointe sécurisée existante nommée Ressources humaines en affectant la stratégie de quarantaine personnalisée nommée NoAccess qui n’affecte **aucune autorisation d’accès** .

```powershell
Set-SafeAttachmentPolicy -Identity "Human Resources" -QuarantineTag NoAccess
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-MalwareFilterPolicy](/powershell/module/exchange/set-malwarefilterpolicy).

## <a name="configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal"></a>Configurer les paramètres de notification de quarantaine globale dans le portail Microsoft 365 Defender

Les paramètres globaux des stratégies de quarantaine vous permettent de personnaliser les notifications de quarantaine envoyées aux destinataires de messages mis en quarantaine si les notifications de quarantaine sont activées dans la stratégie de quarantaine. Pour plus d’informations sur ces notifications, consultez [Notifications de quarantaine](use-spam-notifications-to-release-and-report-quarantined-messages.md).

1. Dans le portail Microsoft 365 Defender, accédez à Email & stratégies de **collaboration** \> **& règles** \> **Stratégies de menace** \> **Stratégies de quarantaine** dans la section **Règles**. Ou, pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

2. Dans la page **Stratégies de quarantaine** , sélectionnez **Paramètres globaux**.

3. Dans le menu volant **des paramètres de notification de quarantaine** qui s’ouvre, configurez les paramètres suivants :

   - Personnalisez les notifications de quarantaine en fonction de la langue du destinataire :

     - **Nom d’affichage** de l’expéditeur utilisé dans les notifications de quarantaine, comme illustré dans la capture d’écran suivante.

       :::image type="content" source="../../media/quarantine-tags-esn-customization-display-name.png" alt-text="Nom d’affichage de l’expéditeur personnalisé dans une notification de mise en quarantaine." lightbox="../../media/quarantine-tags-esn-customization-display-name.png":::

     - Texte **d’exclusion de responsabilité** ajouté au bas des notifications de mise en quarantaine. Le texte localisé, **une exclusion de responsabilité de votre organisation,** est toujours inclus en premier, suivi du texte que vous spécifiez comme indiqué dans la capture d’écran suivante :

       :::image type="content" source="../../media/quarantine-tags-esn-customization-disclaimer.png" alt-text="Exclusion de responsabilité personnalisée au bas d’une notification de mise en quarantaine." lightbox="../../media/quarantine-tags-esn-customization-disclaimer.png":::

     - Identificateur de langue pour le **nom d’affichage** et les valeurs **d’exclusion de responsabilité** . Les notifications de quarantaine sont déjà localisées en fonction des paramètres de langue du destinataire. Les valeurs **Nom d’affichage** et **Exclusion de responsabilité** sont utilisées dans les notifications de mise en quarantaine qui s’appliquent à la langue du destinataire.

       Sélectionnez la langue dans la zone **Choisir la langue** _avant_ d’entrer des valeurs dans les zones **Nom d’affichage** et **Exclusion de responsabilité** . Lorsque vous **modifiez** la valeur dans la zone Choisir la langue, les valeurs des zones **Nom d’affichage** et **Exclusion de responsabilité** sont vidées.

     Procédez comme suit pour personnaliser les notifications de quarantaine en fonction de la langue du destinataire :

     1. Sélectionnez la langue dans la zone **Choisir la langue** . La valeur par défaut est **Default**, ce qui signifie la langue par défaut de l’organisation Microsoft 365. Pour plus d’informations, consultez [Comment définir les paramètres de langue et de région pour Microsoft 365](/office365/troubleshoot/access-management/set-language-and-region).
     2. Entrez les valeurs du **nom d’affichage** et **de la clause d’exclusion de responsabilité**. Les valeurs doivent être uniques pour chaque langue. Si vous essayez de réutiliser un **nom d’affichage** ou une valeur **d’exclusion** de responsabilité pour plusieurs langues, une erreur s’affiche lorsque vous cliquez sur **Enregistrer**.
     3. Cliquez sur le bouton **Ajouter**.
     4. Répétez les étapes précédentes pour créer un maximum de trois notifications de quarantaine personnalisées en fonction de la langue du destinataire. Une zone sans étiquette affiche les langues que vous avez configurées :

        :::image type="content" source="../../media/quarantine-tags-esn-customization-selected-languages.png" alt-text="Langues sélectionnées dans les paramètres de notification de quarantaine globaux des stratégies de quarantaine." lightbox="../../media/quarantine-tags-esn-customization-selected-languages.png":::

   - **Utiliser le logo de mon entreprise** : sélectionnez cette option pour remplacer le logo Microsoft par défaut utilisé en haut des notifications de quarantaine. Avant de procéder à cette étape, vous devez suivre les instructions fournies dans [Personnaliser le thème Microsoft 365 pour que votre organisation](../../admin/setup/customize-your-organization-theme.md) charge votre logo personnalisé. Cette option n’est pas prise en charge si votre organisation dispose d’un logo personnalisé pointant vers une URL au lieu d’un fichier de logo personnalisé chargé. 

     La capture d’écran suivante montre un logo personnalisé dans une notification de quarantaine :

     :::image type="content" source="../../media/quarantine-tags-esn-customization-logo.png" alt-text="Logo personnalisé dans une notification de quarantaine" lightbox="../../media/quarantine-tags-esn-customization-logo.png":::

   - **Envoyer une notification de courrier indésirable à l’utilisateur final tous les (jours)** : sélectionnez la fréquence des notifications de quarantaine. La valeur par défaut est 3 jours, mais vous pouvez sélectionner 1 à 15 jours.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   :::image type="content" source="../../media/mdo-quarantine-policy-quarantine-notification-settings.png" alt-text="Menu volant des paramètres de notification de mise en quarantaine dans le portail Microsoft 365 Defender." lightbox="../../media/mdo-quarantine-policy-quarantine-notification-settings.png":::

## <a name="view-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Afficher les stratégies de quarantaine dans le portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender, accédez à Email & stratégies de **collaboration** \> **& règles** \> **Stratégies de menace** \> **Stratégies de quarantaine** dans la section **Règles**. Ou, pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

2. La page **Stratégies de quarantaine** affiche la liste des stratégies par **nom** et date de **dernière mise à jour** .

3. Pour afficher les paramètres des stratégies de quarantaine intégrées ou personnalisées, sélectionnez la stratégie de quarantaine dans la liste en cliquant sur le nom.

4. Pour afficher les paramètres globaux, cliquez sur **Paramètres globaux**

### <a name="view-quarantine-policies-in-powershell"></a>Afficher les stratégies de quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour afficher les stratégies de quarantaine, effectuez l’une des étapes suivantes :

- Pour afficher une liste récapitulative de toutes les stratégies intégrées ou personnalisées, exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy | Format-Table Name
  ```

- Pour afficher les paramètres des stratégies de quarantaine intégrées ou personnalisées, remplacez \<QuarantinePolicyName\> par le nom de la stratégie de quarantaine et exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy -Identity "<QuarantinePolicyName>"
  ```

- Pour afficher les paramètres globaux des notifications de quarantaine, exécutez la commande suivante :

  ```powershell
  Get-QuarantinePolicy -QuarantinePolicyType GlobalQuarantinePolicy
  ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-HostedContentFilterPolicy](/powershell/module/exchange/get-hostedcontentfilterpolicy).

## <a name="modify-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Modifier les stratégies de quarantaine dans le portail Microsoft 365 Defender

Vous ne pouvez pas modifier les stratégies de quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Vous pouvez modifier la stratégie intégrée nommée NotificationEnabledPolicy ([si vous l’avez](#full-access-permissions-and-quarantine-notifications)) et les stratégies de quarantaine personnalisées.

1. Dans le portail Microsoft 365 Defender, accédez à Email & stratégies de **collaboration** \> **& règles** \> **Stratégies de menace** \> **Stratégies de quarantaine** dans la section **Règles**. Ou, pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

2. Dans la page **Stratégies de quarantaine** , sélectionnez la stratégie en cliquant sur le nom.

3. Après avoir sélectionné la stratégie, cliquez sur l’icône Modifier la ![stratégie.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier la stratégie** qui s’affiche.

4. L’Assistant **Modification de** stratégie qui s’ouvre est pratiquement identique à l’Assistant **Nouvelle** stratégie, comme décrit dans la section [Créer des stratégies de quarantaine dans la section Microsoft 365 Defender portail](#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) plus haut dans cet article.

   La principale différence est que vous ne pouvez pas renommer une stratégie existante.

5. Lorsque vous avez terminé de modifier la stratégie, accédez à la page **Résumé** , puis cliquez sur **Envoyer**.

### <a name="modify-quarantine-policies-in-powershell"></a>Modifier les stratégies de quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour modifier une stratégie de quarantaine personnalisée, remplacez-la \<QuarantinePolicyName\> par le nom de la stratégie de quarantaine et utilisez la syntaxe suivante :

```powershell
Set-QuarantinePolicy -Identity "<QuarantinePolicyName>" [Settings]
```

Les paramètres disponibles sont les mêmes que ceux décrits pour la création de stratégies de quarantaine plus haut dans cet article.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-QuarantinePolicy](/powershell/module/exchange/set-quarantinepolicy).

## <a name="remove-quarantine-policies-in-the-microsoft-365-defender-portal"></a>Supprimer les stratégies de quarantaine dans le portail Microsoft 365 Defender

**Remarques** :

- Vous ne pouvez pas supprimer les stratégies de quarantaine intégrées nommées AdminOnlyAccessPolicy ou DefaultFullAccessPolicy. Vous pouvez supprimer la stratégie intégrée nommée NotificationEnabledPolicy ([si vous l’avez](#full-access-permissions-and-quarantine-notifications)) et les stratégies de quarantaine personnalisées.
- Avant de supprimer une stratégie de quarantaine, vérifiez qu’elle n’est pas utilisée. Par exemple, exécutez la commande suivante dans PowerShell :

  ```powershell
  Write-Output -InputObject "Anti-spam policies","----------------------";Get-HostedContentFilterPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-phishing policies","----------------------";Get-AntiPhishPolicy | Format-List Name,*QuarantineTag; Write-Output -InputObject "Anti-malware policies","----------------------";Get-MalwareFilterPolicy | Format-List Name,QuarantineTag; Write-Output -InputObject "Safe Attachments policies","---------------------------";Get-SafeAttachmentPolicy | Format-List Name,QuarantineTag
  ```

  Si la stratégie de quarantaine est utilisée, [remplacez la stratégie de quarantaine affectée](#step-2-assign-a-quarantine-policy-to-supported-features) avant de la supprimer.

1. Dans le portail Microsoft 365 Defender, accédez à Email & stratégies de **collaboration** \> **& règles** \> **Stratégies de menace** \> **Stratégies de quarantaine** dans la section **Règles**. Ou, pour accéder directement à la page **Stratégies de quarantaine** , utilisez <https://security.microsoft.com/quarantinePolicies>.

2. Dans la page **Stratégies de quarantaine** , sélectionnez la stratégie de quarantaine personnalisée à supprimer en cliquant sur le nom.

3. Après avoir sélectionné la stratégie, cliquez sur l’icône Supprimer la ![stratégie.](../../media/m365-cc-sc-delete-icon.png) **Icône supprimer une** stratégie qui s’affiche.

4. Cliquez sur **Supprimer la stratégie** dans la boîte de dialogue de confirmation qui s’affiche.

### <a name="remove-quarantine-policies-in-powershell"></a>Supprimer les stratégies de quarantaine dans PowerShell

Si vous préférez utiliser PowerShell pour supprimer une stratégie de quarantaine personnalisée, remplacez-la \<QuarantinePolicyName\> par le nom de la stratégie de quarantaine et exécutez la commande suivante :

```powershell
Remove-QuarantinePolicy -Identity "<QuarantinePolicyName>"
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-QuarantinePolicy](/powershell/module/exchange/remove-quarantinepolicy).

## <a name="system-alerts-for-quarantine-release-requests"></a>Alertes système pour les demandes de mise en quarantaine

Par défaut, la stratégie d’alerte par défaut nommée **Utilisateur demandé pour libérer un message mis en quarantaine** génère automatiquement une alerte d’information et envoie une notification à La Gestion de l’organisation (administrateur général) chaque fois qu’un utilisateur demande la publication d’un message mis en quarantaine :

Les administrateurs peuvent personnaliser les destinataires des notifications par e-mail ou créer une stratégie d’alerte personnalisée pour plus d’options.

Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

## <a name="quarantine-policy-permission-details"></a>Détails de l’autorisation de stratégie de quarantaine

Les sections suivantes décrivent les effets des groupes d’autorisations prédéfinies et des autorisations individuelles dans les détails des messages mis en quarantaine et dans les notifications de mise en quarantaine.

### <a name="preset-permissions-groups"></a>Groupes d’autorisations prédéfinies

Les autorisations individuelles incluses dans les groupes d’autorisations prédéfinis sont répertoriées dans le tableau au début de cet article.

#### <a name="no-access"></a>Pas d’accès

Si la stratégie de quarantaine attribue les autorisations **d’accès non** accessible (accès administrateur uniquement), les utilisateurs ne peuvent pas voir les messages mis en quarantaine :

- **Détails des messages mis en quarantaine** : aucun message ne s’affiche dans la vue de l’utilisateur final.
- **Notifications de quarantaine** : aucune notification ne sera envoyée pour ces messages.

#### <a name="limited-access"></a>Accès limité

Si la stratégie de quarantaine affecte les autorisations **d’accès limité** , les utilisateurs obtiennent les fonctionnalités suivantes :

- **Détails du message mis en quarantaine : les boutons** suivants sont disponibles :
  - **Demande de mise en production**
  - **Afficher les en-têtes de messages**
  - **Afficher une prévisualisation du message**
  - **Supprimer de la quarantaine**
  - **Bloquer l’expéditeur**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-limited-access.png" alt-text="Les boutons disponibles dans le message mis en quarantaine sont détaillés si la stratégie de quarantaine accorde à l’utilisateur des autorisations d’accès limitées" lightbox="../../media/quarantine-tags-quarantined-message-details-limited-access.png":::

- **Notifications de quarantaine : les boutons** suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Demande de mise en production**
  - **Révision**

  :::image type="content" source="../../media/quarantine-tags-esn-limited-access.png" alt-text="Boutons disponibles dans la notification de quarantaine si la stratégie de quarantaine accorde à l’utilisateur des autorisations d’accès limitées" lightbox="../../media/quarantine-tags-esn-limited-access.png":::

#### <a name="full-access"></a>Accès complet

Si la stratégie de quarantaine affecte les autorisations **d’accès complet** (toutes les autorisations disponibles), les utilisateurs obtiennent les fonctionnalités suivantes :

- **Détails du message mis en quarantaine : les boutons** suivants sont disponibles :
  - **Message de publication**
  - **Afficher les en-têtes de messages**
  - **Afficher une prévisualisation du message**
  - **Supprimer de la quarantaine**
  - **Bloquer l’expéditeur**

  :::image type="content" source="../../media/quarantine-tags-quarantined-message-details-full-access.png" alt-text="Les boutons disponibles dans le message mis en quarantaine sont détaillés si la stratégie de quarantaine donne à l’utilisateur des autorisations d’accès complet" lightbox="../../media/quarantine-tags-quarantined-message-details-full-access.png":::

- **Notifications de quarantaine : les boutons** suivants sont disponibles :
  - **Bloquer l’expéditeur**
  - **Débloquer**
  - **Révision**

  :::image type="content" source="../../media/quarantine-tags-esn-full-access.png" alt-text="Boutons disponibles dans la notification de quarantaine si la stratégie de quarantaine donne à l’utilisateur des autorisations d’accès complet" lightbox="../../media/quarantine-tags-esn-full-access.png":::

> [!NOTE]
> Comme expliqué précédemment, les notifications de quarantaine sont désactivées dans la stratégie de quarantaine par défaut nommée DefaultFullAccessPolicy, même si le groupe **d’autorisations d’accès complet** est affecté à cette stratégie de quarantaine. Les notifications de quarantaine sont disponibles uniquement dans les stratégies de quarantaine personnalisées que vous créez ou dans la stratégie d’accès en quarantaine par défaut nommée NotificationEnabledPolicy ([si cette stratégie est disponible dans votre organisation](#full-access-permissions-and-quarantine-notifications)).

### <a name="individual-permissions"></a>Autorisations individuelles

#### <a name="block-sender-permission"></a>Bloquer l’autorisation de l’expéditeur

L’autorisation **d’expéditeur de** bloc (_PermissionToBlockSender_) contrôle l’accès au bouton qui permet aux utilisateurs d’ajouter facilement l’expéditeur de messages mis en quarantaine à leur liste d’expéditeurs bloqués.

- **Détails du message mis en quarantaine** :
  - **Bloquer** l’autorisation de l’expéditeur activé : le bouton **Bloquer l’expéditeur** est disponible.
  - **Bloquer** l’autorisation de l’expéditeur désactivée : le bouton **Bloquer l’expéditeur** n’est pas disponible.

- **Notifications de quarantaine :**
  - **Bloquer** l’autorisation de l’expéditeur activé : le bouton **Bloquer l’expéditeur** est disponible.
  - **Bloquer** l’autorisation de l’expéditeur désactivée : le bouton **Bloquer l’expéditeur** n’est pas disponible.

Pour plus d’informations sur la liste des expéditeurs bloqués, consultez [Bloquer les messages d’une personne](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077#__toc304379667) et [Utiliser Exchange Online PowerShell pour configurer la collection de listes sécurisées sur une boîte aux lettres](configure-junk-email-settings-on-exo-mailboxes.md#use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox).

#### <a name="delete-permission"></a>Autorisations de suppression

L’autorisation **Delete** (_PermissionToDelete_) contrôle la possibilité pour les utilisateurs de supprimer leurs messages (messages dont l’utilisateur est un destinataire) de la mise en quarantaine.

- **Détails du message mis en quarantaine** :
  - **Autorisation de suppression** activée : le bouton **Supprimer de la quarantaine** est disponible.
  - **Autorisation de suppression** désactivée : le bouton **Supprimer de la quarantaine** n’est pas disponible.

- **Notifications de quarantaine** : aucun effet.

#### <a name="preview-permission"></a>Autorisation d’aperçu

L’autorisation **d’aperçu** (_PermissionToPreview_) contrôle la possibilité pour les utilisateurs d’afficher un aperçu de leurs messages en quarantaine.

- **Détails du message mis en quarantaine** :
  - **Autorisation d’aperçu** activée : le bouton **Aperçu du message** est disponible.
  - **Autorisation d’aperçu** désactivée : le bouton **Aperçu du message** n’est pas disponible.

- **Notifications de quarantaine** : aucun effet.

#### <a name="allow-recipients-to-release-a-message-from-quarantine-permission"></a>Autoriser les destinataires à libérer un message de l’autorisation de mise en quarantaine

> [!NOTE]
> Cette autorisation n’est pas respectée dans les stratégies anti-programmes malveillants ou pour le verdict de hameçonnage à haut niveau de confiance dans les stratégies anti-courrier indésirable. Les utilisateurs ne peuvent pas libérer leurs propres programmes malveillants ou messages de hameçonnage à haut niveau de confiance à partir de la quarantaine. Au mieux, vous pouvez utiliser l’option [Autoriser les destinataires pour demander la libération d’un message à partir de l’autorisation d’autorisation de mise en quarantaine](#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission) .

Autoriser **les destinataires à libérer un message à partir de** l’autorisation de mise en quarantaine (_PermissionToRelease_) contrôle la capacité des utilisateurs à libérer leurs messages mis en quarantaine directement et sans l’approbation d’un administrateur.

- **Détails du message mis en quarantaine** :
  - Autorisation activée : le bouton **Publier le message** est disponible.
  - Autorisation désactivée : le bouton **Publier le message** n’est pas disponible.

- **Notifications de quarantaine :**
  - Autorisation activée : le bouton **Libérer** est disponible.
  - Autorisation désactivée : le bouton **Libérer** n’est pas disponible.

#### <a name="allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission"></a>Autoriser les destinataires à demander la libération d’un message à partir de l’autorisation de mise en quarantaine

**L’autorisation des destinataires de demander la libération d’un message à partir de** l’autorisation de quarantaine (_PermissionToRequestRelease_) contrôle la capacité des utilisateurs à _demander_ la publication de leurs messages mis en quarantaine. Le message n’est publié qu’une fois qu’un administrateur a approuvé la demande.

- **Détails du message mis en quarantaine** :
  - Autorisation activée : le bouton **Demander la mise en production** est disponible.
  - Autorisation désactivée : le bouton **Demander la mise en production** n’est pas disponible.

- **Notifications de quarantaine :**
  - Autorisation activée : le bouton **Demander la mise en production** est disponible.
  - Autorisation désactivée : le bouton **Demander la mise en production** n’est pas disponible.
