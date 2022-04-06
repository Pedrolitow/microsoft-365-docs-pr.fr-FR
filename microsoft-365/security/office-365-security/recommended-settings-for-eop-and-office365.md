---
title: Recommandations Microsoft pour EOP et les paramètres Defender pour Office 365 de sécurité
keywords: Office 365 recommandations en matière de sécurité, Sender Policy Framework, Domain-based Message Reporting and Conformance, DomainKeys Identified Mail, steps, how does it work, security baselines, baselines for EOP, baselines for Defender pour Office 365 , set up Defender pour Office 365 , set up EOP, configure Defender pour Office 365, configurer EOP, configuration de la sécurité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Quelles sont les meilleures pratiques pour Exchange Online Protection (EOP) et Defender pour Office 365 de sécurité ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous souhaitez être plus strict ? Quels sont les extras que vous obtenez si vous utilisez également Defender pour Office 365 ?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b4b6c9df3b8c458aaf548ff9c8cfe8cc51fa5824
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507169"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Paramètres recommandés pour EOP et pour la sécurité Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** est le cœur de la sécurité des abonnements Microsoft 365 et permet d’empêcher les e-mails malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes chaque jour, des protections améliorées sont souvent nécessaires. **Microsoft Defender pour Office 365** Plan 1 ou Plan 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs davantage de couches de sécurité, de contrôle et d’examen.

Bien que nous donnent la possibilité aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : **Standard** et **Strict**. Bien que les environnements et les besoins des clients soient différents, ces niveaux de filtrage permettent d’éviter que les messages indésirables n’atteignent la boîte de réception de vos employés dans la plupart des cas.

Pour appliquer automatiquement les paramètres Standard ou Strict aux utilisateurs, voir Stratégies de sécurité prédéfini [dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Cet article décrit les paramètres par défaut, ainsi que les paramètres standard et strict recommandés pour protéger vos utilisateurs. Les tableaux contiennent les paramètres dans le portail Microsoft 365 Defender et PowerShell (Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome pour les organisations Exchange Online boîtes aux lettres).

> [!TIP]
> Vous ne pouvez pas modifier les paramètres standard et strict recommandés dans le portail Microsoft 365 Defender web. Pour modifier les valeurs recommandées telles que **Activer la** protection des utilisateurs, vous devez utiliser [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
>
> Le Office 365 module ORCA (Advanced Threat Protection Recommended Configuration Analyzer) pour PowerShell peut vous aider (administrateurs) à trouver les valeurs actuelles de ces paramètres. Plus précisément, la cmdlet **Get-ORCAReport** génère une évaluation des paramètres d’hygiène des messages anti-courrier indésirable, anti-hameçonnage et autres. Vous pouvez télécharger le module ORCA sur <https://www.powershellgallery.com/packages/ORCA/>.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Protection anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage dans EOP

Les fonctionnalités anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons les configurations standard ou stricte suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies anti-courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de courrier électronique en & propriétés de courrier indésirable**|||||
|**Seuil des courriers électroniques en bloc** <br/><br/> _BulkThreshold_|7 |6 |4|Pour plus d’informations, voir [Niveau de réclamation en bloc (BCL) dans EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Ce paramètre est uniquement disponible dans PowerShell.|
|**Augmenter les paramètres du score** de courrier indésirable|Désactivé|Désactivé|Désactivé|Tous ces paramètres font partie du filtre de courrier indésirable avancé (ASF). Pour plus d’informations, consultez la section [paramètres ASF dans la section des stratégies anti-courrier](#asf-settings-in-anti-spam-policies) indésirable de cet article.|
|**Marquer comme paramètres de** courrier indésirable|Désactivé|Désactivé|Désactivé|La plupart de ces paramètres font partie d’ASF. Pour plus d’informations, consultez la section [paramètres ASF dans la section des stratégies anti-courrier](#asf-settings-in-anti-spam-policies) indésirable de cet article.|
|**Contient des langues spécifiques** <br/><br/> _EnableLanguageBlockList_ <br/><br/> _LanguageBlockList_|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. Vous pouvez bloquer les messages dans des langues spécifiques en fonction des besoins de votre entreprise.|
|**À partir de ces pays** <br/><br/> _EnableRegionBlockList_ <br/><br/> _RegionBlockList_|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|**Désactivé** <br/><br/> `$false` <br/><br/> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. Vous pouvez bloquer les messages provenant de pays spécifiques en fonction des besoins de votre entreprise.|
|**Mode test** (_TestModeAction_)|**Aucune**|**Aucune**|**Aucune**|Ce paramètre fait partie d’ASF. Pour plus d’informations, consultez la section [paramètres ASF dans la section des stratégies anti-courrier](#asf-settings-in-anti-spam-policies) indésirable de cet article.|
|**Actions**||||Où que vous sélectionniez le **message de mise** en quarantaine, une **zone sélectionner** une stratégie de mise en quarantaine est disponible. Les stratégies de mise en quarantaine définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. <br/><br/> Lorsque vous créez une stratégie anti-courrier indésirable, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages mis en quarantaine par ce verdict particulier (AdminOnlyAccessPolicy pour le hameçonnage à haut niveau de **confiance ;** DefaultFullAccessPolicy pour tout le reste). <br/><br/> Les administrateurs peuvent créer et sélectionner des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités plus restrictives ou moins restrictives pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Action de** détection du courrier indésirable <br/><br/> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Action de détection du courrier indésirable** à niveau de confiance élevé <br/><br/> _HighConfidenceSpamAction_|**Mettre en quarantaine le message** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Action de détection du** hameçonnage <br/><br/> _PhishSpamAction_|**Mettre en quarantaine le message** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Action de détection du hameçonnage à haut** niveau de confiance <br/><br/> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Action de** détection en bloc <br/><br/> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Conserver le courrier indésirable en quarantaine pendant ce nombre de jours** <br/><br/> _QuarantineRetentionPeriod_|15 jours<sup>\*</sup>|30 jours|30 jours|<sup>\*</sup> La valeur par défaut est 15 jours dans la stratégie anti-courrier indésirable par défaut et dans les nouvelles stratégies anti-courrier indésirable que vous créez dans PowerShell. La valeur par défaut est 30 jours dans les nouvelles stratégies anti-courrier indésirable que vous créez dans le portail Microsoft 365 Defender courrier indésirable. <br/><br/> Cette valeur affecte également les messages mis en quarantaine par les stratégies anti-hameçonnage. Pour plus d’informations, voir [Messages électroniques mis en quarantaine dans EOP](quarantine-email-messages.md).|
|**Activer les conseils de sécurité contre le courrier indésirable** <br/><br/> _InlineSafetyTipsEnabled_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|Activer la purge automatique d’heure zéro (ZAP) pour les messages de hameçonnage <br/><br/> _PhishZapEnabled_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|Activer ZAP pour les messages indésirables <br/><br/> _SpamZapEnabled_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Autoriser les & liste d’attente**|||||
|Expéditeurs autorisés <br/><br/> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur autorisés <br/><br/> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines à la liste des expéditeurs autorisés est une idée très mauvaise. Les attaquants pourraient vous envoyer des messages électroniques qui seraient autrement filtrés. <br/><br/> Utilisez la [](learn-about-spoof-intelligence.md) veille contre l’usurpation d’adresses et la liste d’adresses de blocage[/](tenant-allow-block-list.md)d’usurpation d’adresses client pour passer en revue tous les expéditeurs usurpant des adresses de messagerie d’expéditeur dans les domaines de messagerie de votre organisation ou usurpant des adresses de messagerie d’expéditeur dans des domaines externes.|
|Expéditeurs bloqués <br/><br/> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs bloqués <br/><br/> _BlockedSenderDomains_|Aucun|Aucun|Aucun||

#### <a name="asf-settings-in-anti-spam-policies"></a>Paramètres ASF dans les stratégies anti-courrier indésirable

Le tableau de cette section décrit les paramètres de filtrage avancé du courrier indésirable (ASF) disponibles dans les stratégies anti-courrier indésirable. Tous ces paramètres **sont éteints** pour les **niveaux Standard** **et Strict** . Pour plus d’informations sur les paramètres ASF, consultez les [paramètres de filtre de courrier indésirable avancé (ASF) dans EOP](advanced-spam-filtering-asf-options.md).

|Nom de la fonctionnalité de sécurité|Commentaire|
|---|---|
|**Liens d’image vers des sites distants** (_IncreaseScoreWithImageLinks_)||
|**Adresse IP numérique dans l’URL** (_IncreaseScoreWithNumericIps_)||
|**Redirection d’URL vers** un autre port (_IncreaseScoreWithRedirectToOtherPort_)||
|**Liens vers des sites web .biz ou .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Messages vides** (_MarkAsSpamEmptyMessages_)||
|**Incorporer des balises au format HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**JavaScript ou VBScript en HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Balises de formulaire en HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Balises frame ou iframe en HTML** (_MarkAsSpamFramesInHtml_)||
|**Bogues web au format HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Balises d’objet en HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Mots sensibles** (_MarkAsSpamSensitiveWordList_)||
|**Enregistrement SPF : échec en dur** (_MarkAsSpamSpfRecordHardFail_)||
|**Échec de filtrage de l’ID de** l’expéditeur (_MarkAsSpamFromAddressAuthFail_)||
|**Backscatter** (_MarkAsSpamNdrBackscatter_)||
|**Mode test** (_TestModeAction_)|Pour les paramètres ASF qui supportent **Test** en tant qu’action, vous pouvez configurer l’action du mode test sur **Aucun, Ajouter** du texte d’en-tête **X** par défaut ou envoyer un **message Bcc** (`None`ou `AddXHeader``BccMessage`). Pour plus d’informations, [voir Activer, désactiver ou tester les paramètres ASF](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Paramètres de stratégie de courrier indésirable sortant EOP

Pour créer et configurer des stratégies de courrier indésirable sortant, voir Configurer le filtrage du courrier indésirable sortant [dans EOP](configure-the-outbound-spam-policy.md).

Pour plus d’informations sur les limites d’envoi par défaut dans le service, voir [Limites d’envoi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Les stratégies de courrier indésirable sortant ne font pas partie des stratégies de sécurité standard ou stricte. Les **valeurs Standard** et **Strict** indiquent nos valeurs recommandées dans la stratégie de courrier indésirable sortant par défaut ou les stratégies personnalisées que vous créez.

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Définir une limite de messages externes** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite de message interne** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite quotidienne des messages** <br/><br/> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Restriction imposée aux utilisateurs qui atteignent la limite de message** <br/><br/> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages jusqu’au jour suivant** <br/><br/> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <br/><br/> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <br/><br/> `BlockUser`||
|**Règles de transmission automatique** <br/><br/> _AutoForwardingMode_|**Automatique - Contrôlé par le système** <br/><br/> `Automatic`|**Automatique - Contrôlé par le système** <br/><br/> `Automatic`|**Automatique - Contrôlé par le système** <br/><br/> `Automatic`|
|**Envoyer une copie des messages sortants qui dépassent ces limites à ces utilisateurs et groupes** <br/><br/> _BccSuspiciousOutboundMail_ <br/><br/> _BccSuspiciousOutboundAdditionalRecipients_|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br/><br/> Ce paramètre fonctionne uniquement dans la stratégie de courrier indésirable sortant par défaut. Elle ne fonctionne pas dans les stratégies de courrier indésirable sortant personnalisées que vous créez.|
|**Avertir ces utilisateurs et groupes si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant** <br/><br/> _NotifyOutboundSpam_ <br/><br/> _NotifyOutboundSpamRecipients_|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|Non sélectionnée <br/><br/> `$false` <br/><br/> Vide|La stratégie [](../../compliance/alert-policies.md) d’alerte par défaut nommée User **restricted from sending email** already sends email notifications to members of the **TenantAdmins (Global admins**) group when users are blocked due to exceeding the limits in policy. **Nous vous recommandons vivement d’utiliser** la stratégie d’alerte plutôt que ce paramètre dans la stratégie de courrier indésirable sortant pour avertir les administrateurs et les autres utilisateurs. Pour obtenir des instructions, [voir Vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies anti-programme malveillant, voir Configurer des stratégies [anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Paramètres de protection**|||||
|**Activer le filtre des pièces jointes courantes** <br/><br/> _EnableFileFilter_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu de la pièce jointe.|
|**Activer la purge automatique sans heure pour les programmes malveillants** <br/><br/> _ZapEnabled_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Stratégie de mise en quarantaine**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Lorsque vous créez une stratégie anti-programme malveillant, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages mis en quarantaine en tant que programmes malveillants (AdminOnlyAccessPolicy). <br/><br/> Les administrateurs peuvent créer et sélectionner des stratégies de mise en quarantaine personnalisées qui définissent davantage de fonctionnalités pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Notifications des destinataires**|||||
|**Avertir les destinataires lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <br/><br/> _Action_|Non sélectionnée <br/><br/> _DeleteMessage_|Non sélectionnée <br/><br/> _DeleteMessage_|Non sélectionnée <br/><br/> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Notifications de l’expéditeur**|||||
|**Avertir les expéditeurs internes lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <br/><br/> _EnableInternalSenderNotifications_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`||
|**Avertir les expéditeurs externes lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <br/><br/> _EnableExternalSenderNotifications_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`||
|**Notifications de l’administrateur**|||||
|**Informer un administrateur des messages non reçus d’expéditeurs internes** <br/><br/> _EnableInternalSenderAdminNotifications_ <br/><br/> _InternalSenderAdminAddress_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre.|
|**Informer un administrateur des messages non reçus d’expéditeurs externes** <br/><br/> _EnableExternalSenderAdminNotifications_ <br/><br/> _ExternalSenderAdminAddress_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre.|
|**Personnaliser les notifications**||||Nous n’avons aucune recommandation spécifique pour ces paramètres.|
|**Utiliser un texte de notification personnalisé** <br/><br/> _CustomNotifications_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`||
|**De nom** <br/><br/> _CustomFromName_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||
|**Adresse de provenance** <br/><br/> _CustomFromAddress_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||
|**Personnaliser les notifications pour les messages provenant d’expéditeurs internes**||||Ces paramètres sont utilisés uniquement si les expéditeurs internes sont avertis lorsque des **messages** sont mis  en quarantaine en tant que programmes malveillants ou si les messages non envoyés provenant d’expéditeurs internes sont sélectionnés.|
|**Subject** <br/><br/> _CustomInternalSubject_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||
|**Message** <br/><br/> _CustomInternalBody_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||
|**Personnaliser les notifications pour les messages provenant d’expéditeurs externes**||||Ces paramètres sont utilisés uniquement si les expéditeurs externes sont avertis lorsque des **messages** sont mis en quarantaine en tant que programmes malveillants ou si les **messages** non envoyés provenant d’expéditeurs externes sont sélectionnés.|
|**Subject** <br/><br/> _CustomExternalSubject_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||
|**Message** <br/><br/> _CustomExternalBody_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage EOP

Pour plus d’informations sur ces paramètres, voir [Paramètres d’usurpation d’informations](set-up-anti-phishing-policies.md#spoof-settings). Pour configurer ces paramètres, voir [Configurer des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de hameçonnage & protection**|||||
|**Activer la veille contre l’usurpation d’informations** <br/><br/> _EnableSpoofIntelligence_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Actions**|||||
|**Si le message est détecté comme usurpant une usurpation** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|Ce paramètre s’applique aux expéditeurs usurpés qui ont été automatiquement bloqués, comme indiqué [](learn-about-spoof-intelligence.md) dans la veille contre l’usurpation d’informations ou bloqués manuellement dans la liste d’adresses client autoriser[/bloquer](tenant-allow-block-list.md). <br/><br/> Si vous sélectionnez Mettre le **message** en  quarantaine, une zone de stratégie Appliquer la mise en quarantaine est disponible pour sélectionner la stratégie de mise en quarantaine qui définit ce que les utilisateurs sont autorisés à faire aux messages mis en quarantaine en tant qu’usurpation. Lorsque vous créez une stratégie anti-hameçonnage, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages mis en quarantaine en tant qu’usurpation (DefaultFullAccessPolicy). <br/><br/> Les administrateurs peuvent créer et sélectionner des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités plus restrictives ou moins restrictives pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Afficher le premier contact conseil de sécurité** <br/><br/> _EnableFirstContactSafetyTips_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Pour plus d’informations, [voir First contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’adresse** <br/><br/> _EnableUnauthenticatedSender_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook des expéditeurs usurpés non identifiés. Pour plus d’informations, voir [Expéditeur non authentifié](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Afficher la balise « via »** <br/><br/> _EnableViaTag_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse De si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . <br/><br/> Pour plus d’informations, voir [Expéditeur non authentifié](set-up-anti-phishing-policies.md#unauthenticated-sender).|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender pour Office 365 sécurité

Des avantages supplémentaires en matière de sécurité sont Microsoft Defender pour Office 365 abonnement. Pour obtenir les dernières actualités et informations, vous pouvez consulter les [nouveautés de Defender pour Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 protection contre [l’usurpation](set-up-anti-phishing-policies.md#spoof-settings) d’adresses et l’intelligence des boîtes aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités de [protection](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contre l’emprunt d’identité disponibles et les paramètres avancés ne sont pas [configurés](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.
>
> - Bien qu’il n’existe pas de stratégie de pièces jointes Coffre ou de stratégie de liens Coffre par défaut, la stratégie de sécurité prédéfinit de **protection** intégrée offre une protection Coffre des pièces jointes et une protection de liens Coffre à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de pièces jointes Coffre personnalisées ou les stratégies de liens Coffre). Pour plus d’informations, voir [Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).
>
> - [Coffre pièces jointes pour SharePoint, OneDrive](mdo-for-spo-odb-and-teams.md) et la protection Microsoft Teams et [la protection Coffre Documents](safe-docs.md) ne sont pas dépendantes des stratégies Coffre liens.

Si votre abonnement inclut Microsoft Defender pour Office 365 ou si vous avez acheté Defender pour Office 365 en tant que modules, définissez les configurations Standard ou Strict suivantes.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour Office 365

Les clients EOP obtiennent un anti-hameçonnage de base, comme décrit précédemment, mais Defender pour Office 365 inclut plus de fonctionnalités et de contrôle pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, voir Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres avancés dans les stratégies anti-hameçonnage Microsoft Defender pour Office 365

Pour plus d’informations sur ce paramètre, voir Seuils d’hameçonnage avancés dans les [stratégies anti-hameçonnage Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ce paramètre, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de courrier d’hameçonnage** <br/><br/> _PhishThresholdLevel_|**1 - Standard** <br/><br/> `1`|**2 - Agressif** <br/><br/> `2`|**3 - Plus agressif** <br/><br/> `3`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage Microsoft Defender pour Office 365

Pour plus d’informations sur ces paramètres, voir paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ces paramètres, voir Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de hameçonnage & protection**|||||
|**Permettre aux utilisateurs de se protéger** (protection des utilisateurs dont l’identité est usurpée) <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Non sélectionnée <br/><br/> `$false` <br/><br/> none|Sélectionné <br/><br/> `$true` <br/><br/> \<list of users\>|Sélectionné <br/><br/> `$true` <br/><br/> \<list of users\>|Nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans les rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, votre directeur financier et d’autres cadres supérieurs. En externe, les expéditeurs protégés peuvent inclure des membres du conseil ou votre conseil d’administration. <br/><br/> Dans les stratégies de sécurité prédéfines, vous ne pouvez pas spécifier les utilisateurs à protéger. Vous devez désactiver les stratégies de sécurité prédéfinie et utiliser des stratégies anti-hameçonnage personnalisées pour ajouter des utilisateurs dans des rôles clés, comme suggéré.|
|**Activer les domaines à protéger** (protection de domaine dont l’identité est usurpée)|Non sélectionnée|Sélectionné|Sélectionné||
|**Inclure les domaines que je possède** <br/><br/> _EnableOrganizationDomainsProtection_|Désactivé <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Inclure des domaines personnalisés** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Désactivé <br/><br/> `$false` <br/><br/> none|Sélectionné <br/><br/> `$true` <br/><br/> \<list of domains\>|Sélectionné <br/><br/> `$true` <br/><br/> \<list of domains\>|Nous vous recommandons d’ajouter des domaines (domaines d’expéditeur) que vous ne possédez pas, mais avec qui vous interagissez fréquemment. <br/><br/> Dans les stratégies de sécurité prédéfines, vous ne pouvez pas spécifier les domaines custm à protéger. Vous devez désactiver les stratégies de sécurité prédéfinie et utiliser des stratégies anti-hameçonnage personnalisées pour ajouter des domaines personnalisés à protéger comme suggéré.|
|**Ajouter des expéditeurs et des domaines de confiance** <br/><br/> _ExcludedSenders_ <br/><br/> _ExcludedDomains_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des expéditeurs ou des domaines qui sont identifiés à tort comme des tentatives d’emprunt d’identité.|
|**Activer l’intelligence des boîtes aux lettres** <br/><br/> _EnableMailboxIntelligence_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Activer la veille pour la protection contre l’emprunt d’identité** <br/><br/> _EnableMailboxIntelligenceProtection_|Désactivé <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ce paramètre autorise l’action spécifiée pour les détections d’emprunt d’identité par l’intelligence des boîtes aux lettres.|
|**Actions**||||Où que vous sélectionniez la **mise en quarantaine du message**, une **zone sélectionner** la stratégie de mise en quarantaine est disponible. Les stratégies de mise en quarantaine définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. <br/><br/> Lorsque vous créez une stratégie anti-hameçonnage, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages mis en quarantaine par ce verdict (DefaultFullAccessPolicy pour tous les types de détection d’emprunt d’identité). <br/><br/> Les administrateurs peuvent créer et sélectionner des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Si le message est détecté comme un utilisateur dont l’identité est usurpée** <br/><br/> _TargetedUserProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|N’oubliez pas que les stratégies de sécurité prédéfines ne vous permettent pas de spécifier les utilisateurs à protéger, de sorte que ce paramètre ne fait rien dans les stratégies de sécurité prédéfines.|
|**Si le message est détecté comme un domaine dont l’identité est usurpée** <br/><br/> _TargetedDomainProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|N’oubliez pas que les stratégies de sécurité prédéfines ne vous permettent pas de spécifier les domaines personnalisés à protéger, de sorte que ce paramètre affecte uniquement les domaines que vous possédez, et non les domaines personnalisés.|
|**Si l’intelligence de boîte aux lettres détecte et usurpe l’identité de l’utilisateur** <br/><br/> _MailboxIntelligenceProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`||
|**Afficher l’emprunt d’identité conseil de sécurité** <br/><br/> _EnableSimilarUsersSafetyTips_|Désactivé <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Afficher les conseil de sécurité** <br/><br/> _EnableSimilarDomainsSafetyTips_|Désactivé <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Afficher les caractères inhabituels d’emprunt d’identité conseil de sécurité** <br/><br/> _EnableUnusualCharactersSafetyTips_|Désactivé <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage EOP dans Microsoft Defender pour Office 365

Ce sont les mêmes paramètres que ceux disponibles dans les [paramètres de stratégie anti-courrier indésirable dans EOP](#eop-anti-spam-policy-settings).

Les paramètres d’usurpation sont liés, mais le paramètre Afficher le premier **contact conseil de sécurité** ne dépend pas des paramètres d’usurpation.

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de hameçonnage & protection**|||||
|**Activer la veille contre l’usurpation d’informations** <br/><br/> _EnableSpoofIntelligence_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Actions**|||||
|**Si le message est détecté comme usurpant une usurpation** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre le message en quarantaine** <br/><br/> `Quarantine`|Ce paramètre s’applique aux expéditeurs usurpés qui ont été automatiquement bloqués, comme indiqué [](learn-about-spoof-intelligence.md) dans la veille contre l’usurpation d’informations ou bloqués manuellement dans la liste d’adresses client autoriser[/bloquer](tenant-allow-block-list.md). <br/><br/> Si vous sélectionnez **Mettre le message** en  quarantaine, une zone de stratégie Appliquer la mise en quarantaine est disponible pour sélectionner la stratégie de mise en quarantaine qui définit ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. Lorsque vous créez une stratégie anti-hameçonnage, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques pour l’usurpation des messages mis en quarantaine (DefaultFullAccessPolicy). <br/><br/> Les administrateurs peuvent créer et sélectionner une stratégie de mise en quarantaine personnalisée qui définit ce que les destinataires sont autorisés à faire pour ces messages en quarantaine. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Afficher le premier contact conseil de sécurité** <br/><br/> _EnableFirstContactSafetyTips_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Pour plus d’informations, [voir First contact conseil de sécurité](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’adresse** <br/><br/> _EnableUnauthenticatedSender_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook des expéditeurs usurpés non identifiés. Pour plus d’informations, voir [Expéditeur non authentifié](set-up-anti-phishing-policies.md#unauthenticated-sender).|
|**Afficher la balise « via »** <br/><br/> _EnableViaTag_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse De si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . <br/><br/> Pour plus d’informations, voir [Expéditeur non authentifié](set-up-anti-phishing-policies.md#unauthenticated-sender).|

### <a name="safe-attachments-settings"></a>Coffre de pièces jointes

Coffre pièces jointes dans Microsoft Defender pour Office 365 comprend les paramètres globaux qui n’ont pas de relation avec les stratégies de pièces jointes Coffre et les paramètres spécifiques à chaque stratégie de liens Coffre données. Pour plus d’informations, [voir Coffre pièces jointes dans Defender pour Office 365](safe-attachments.md).

Bien qu’il n’existe aucune stratégie de pièces jointes Coffre par défaut, la stratégie de sécurité prédéfinit de **protection** intégrée fournit une protection de pièces jointes Coffre à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de pièces jointes Coffre personnalisées). Pour plus d’informations, voir [Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux pour Coffre pièces jointes

> [!NOTE]
> Les paramètres globaux pour Coffre pièces jointes sont définies par la stratégie de sécurité prédéfinit de **protection** intégrée, mais pas par les stratégies de sécurité prédéfinëes **Standard** ou **Strict**. Dans les deux cas, les administrateurs peuvent modifier ces paramètres globaux Coffre pièces jointes à tout moment.
>
> La **colonne Par** défaut affiche les valeurs avant l’existence de la stratégie de sécurité prédéfinit de **protection** intégrée. La **colonne de protection** intégrée affiche les valeurs définies par la stratégie de sécurité prédéfinit de **protection** intégrée, qui sont également nos valeurs recommandées.

Pour configurer ces paramètres, voir Activer les pièces [jointes Coffre pour les documents SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) et [Coffre dans Microsoft 365 E5](safe-docs.md).

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Par défaut|Protection intégrée|Commentaire|
|---|:---:|:---:|---|
|**Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Pour empêcher les utilisateurs de télécharger des fichiers malveillants, voir Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de [télécharger des fichiers malveillants](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Activer les Coffre documents pour Office clients** <br/><br/> _EnableSafeDocs_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Cette fonctionnalité est disponible et significative uniquement avec les licences qui ne sont pas incluses dans Defender pour Office 365 (par exemple, Microsoft 365 E5 ou Microsoft 365 E5 Sécurité). Pour plus d’informations, [voir Coffre Documents dans Microsoft 365 E5](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer dans le affichage protégé même si Coffre documents ont identifié le fichier comme malveillant** <br/><br/> _AllowSafeDocsOpen_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Ce paramètre est lié à Coffre Documents.|

#### <a name="safe-attachments-policy-settings"></a>Coffre de stratégie pièces jointes

Pour configurer ces paramètres, voir [Configurer les stratégies Coffre pièces jointes dans Defender pour Office 365](set-up-safe-attachments-policies.md).

Dans PowerShell, vous utilisez les cmdlets [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) et [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de pièces jointes Coffre par défaut, mais la protection des pièces jointes Coffre est attribuée à tous les destinataires par la stratégie de sécurité prédéfinit de [**protection**](preset-security-policies.md) intégrée.
>
> La **valeur par défaut dans la** colonne personnalisée fait référence aux valeurs par défaut dans les nouvelles Coffre pièces jointes que vous créez. Les colonnes restantes indiquent (sauf indication contraire) les valeurs configurées dans les stratégies de sécurité prédéfinées correspondantes.

|Nom de la fonctionnalité de sécurité|Valeur par défaut dans custom|Protection intégrée|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|:---:|---|
|**Coffre de programmes malveillants inconnus des pièces jointes** <br/><br/> _Activer_ et _action_|**Désactivé** <br/><br/> `-Enable $false` et `-Action Block`|**Bloquer** <br/><br/> `-Enable $true` et `-Action Block`|**Bloquer** <br/><br/> `-Enable $true` et `-Action Block`|**Bloquer** <br/><br/> `-Enable $true` et `-Action Block`|Lorsque le _paramètre Enable_ est $false, la valeur du paramètre _Action_ n’a pas d’importance.|
|**Stratégie de mise en quarantaine** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Lorsque vous créez une stratégie de pièces jointes Coffre, une valeur vide signifie que la stratégie de mise en quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages mis en quarantaine par Coffre Attachments (AdminOnlyAccessPolicy). <br/><br/> Les administrateurs peuvent créer et sélectionner des stratégies de mise en quarantaine personnalisées qui définissent davantage de fonctionnalités pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Rediriger la pièce jointe avec les pièces jointes détectées** : **activer la redirection** <br/><br/> _Redirect_ <br/><br/> _RedirectAddress_|Non sélectionné et aucune adresse de messagerie spécifiée. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ est vide (`$null`)|Non sélectionné et aucune adresse de messagerie spécifiée. <br/><br/> `-Redirect $false` <br/><br/> _RedirectAddress_ est vide (`$null`)|Sélectionné et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse e-mail|Sélectionné et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse e-mail|Rediriger les messages vers un administrateur de sécurité pour révision. <br/><br/> **Remarque** : ce paramètre n’est pas configuré dans les stratégies de sécurité prédéfinées **Standard**, **Strict** ou **Built-in Protection** . Les **valeurs Standard** et **Strict** indiquent nos **valeurs** recommandées dans les Coffre pièces jointes que vous créez.|
|**Appliquer la réponse Coffre détection des pièces jointes si l’analyse ne peut pas se terminer (délai d’Coffre erreurs)** <br/><br/> _ActionOnError_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||

### <a name="safe-links-settings"></a>Coffre de liens

Coffre liens dans Defender pour Office 365 inclut des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies de liens Coffre actives, ainsi que des paramètres spécifiques à chaque stratégie de liens Coffre. Pour plus d’informations, [voir Coffre liens dans Defender pour Office 365](safe-links.md).

Bien qu’il n’existe aucune stratégie de liens Coffre par défaut, la stratégie de sécurité prédéfinit de **protection** intégrée fournit une protection de liens Coffre à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de liens Coffre personnalisées). Pour plus d’informations, voir [Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux pour Coffre liens

> [!NOTE]
> Les paramètres globaux des liens Coffre sont définies par la stratégie de sécurité prédéfinit de **protection** intégrée, mais pas par les stratégies de sécurité prédéfinëes **Standard** ou **Strict**. Dans les deux cas, les administrateurs peuvent modifier ces paramètres globaux Coffre liens à tout moment.
>
> La **colonne Par** défaut affiche les valeurs avant l’existence de la stratégie de sécurité prédéfinit de **protection** intégrée. La **colonne de protection** intégrée affiche les valeurs définies par la stratégie de sécurité prédéfinit de **protection** intégrée, qui sont également nos valeurs recommandées.

Pour configurer ces paramètres, voir [Configure global settings for Coffre Links in Defender pour Office 365](configure-global-settings-for-safe-links.md).

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Par défaut|Protection intégrée|Commentaire|
|---|:---:|:---:|---|
|**Bloquer les URL suivantes** <br/><br/> _ExcludedUrls_|Vide <br/><br/> `$null`|Vide <br/><br/> `$null`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br/><br/> Pour plus d’informations, [consultez la liste « Bloquer les URL suivantes » Coffre liens](safe-links.md#block-the-following-urls-list-for-safe-links).
|**Utiliser des Coffre de ligne de Office 365 applications** <br/><br/> _EnableSafeLinksForO365Clients_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Utilisez Coffre dans les applications de bureau et mobiles (iOS et Android) Office 365 pris en charge. Pour plus d’informations, [Coffre paramètres de liens pour Office 365 applications.](safe-links.md#safe-links-settings-for-office-365-apps)|
|**Ne pas suivre le moment où les utilisateurs cliquent sur les liens protégés dans Office 365 applications** <br/><br/> _TrackClicks_|Activé <br/><br/> `$false`|Désactivé <br/><br/> `$true`|La définition de ce paramètre (définition de _TrackClicks_ `$true`sur ) suit les clics de l’utilisateur dans les applications Office 365 pris en charge.|
|**Ne pas laisser les utilisateurs accéder à l’URL d’origine dans Office 365 applications** <br/><br/> _AllowClickThrough_|Activé <br/><br/> `$false`|Activé <br/><br/> `$false`|L’turning on this setting (setting _AllowClickThrough_ to `$false`) prevents click through to the original URL in supported Office 365 apps.|

#### <a name="safe-links-policy-settings"></a>Coffre de stratégie liens

Pour configurer ces paramètres, voir Configurer les stratégies [Coffre liens dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

Dans PowerShell, vous utilisez les cmdlets [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) et [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de liens Coffre par défaut, mais la protection Coffre Links est attribuée à tous les destinataires par la stratégie de sécurité prédéfinit de [**protection** intégrée](preset-security-policies.md).
>
> La **valeur par défaut dans la** colonne personnalisée fait référence aux valeurs par défaut dans les nouvelles stratégies Coffre liens que vous créez. Les colonnes restantes indiquent (sauf indication contraire) les valeurs configurées dans les stratégies de sécurité prédéfinées correspondantes.

|Nom de la fonctionnalité de sécurité|Valeur par défaut dans custom|Protection intégrée|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|:---:|---|
|**Url & paramètres de protection de clic**||||||
|**Action sur les URL potentiellement malveillantes dans les e-mails**||||||
|**On: Coffre links checks a list of known, malicious links when users click links in email** <br/><br/> _EnableSafeLinksForEmail_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Appliquer Coffre liens vers les messages électroniques envoyés au sein de l’organisation** <br/><br/> _EnableForInternalSenders_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** <br/><br/> _ScanUrls_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Attendre la fin de l’analyse de l’URL avant de remettre le message** <br/><br/> _DeliverMessageAfterScan_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Ne réécrivez pas les URL, effectuez des vérifications via Coffre API Links uniquement** <br/><br/> _DisableURLRewrite_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`||
|**Ne pas réécrire les URL suivantes dans le courrier électronique** <br/><br/> _DoNotRewriteUrls_|Non sélectionnée <br/><br/> blank|Non sélectionnée <br/><br/> blank|Non sélectionnée <br/><br/> blank|Non sélectionnée <br/><br/> blank|Nous n’avons aucune recommandation spécifique pour ce paramètre. Pour plus d’informations, voir [« Ne pas réécrire les URL suivantes » dans Coffre de liens](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).|
|**Action pour les URL potentiellement malveillantes dans Microsoft Teams**||||||
|**On: Coffre Links checks a list of known, malicious links when users click links in Microsoft Teams** <br/><br/> _EnableSafeLinksForTeams_|Non sélectionnée <br/><br/> `$false`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Cliquer sur paramètres de protection**||||||
|**Suivre les clics de l’utilisateur** <br/><br/> _TrackUserClicks_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`||
|**Laisser les utilisateurs cliquer jusqu’à l’URL d’origine** <br/><br/> _AllowClickThrough_|Sélectionné <br/><br/> `$true`|Sélectionné <br/><br/> `$true`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|La définition de ce paramètre (paramètre _AllowClickThrough_ `$false`sur ) empêche de cliquer sur l’URL d’origine.|
|**Afficher la marque de l’organisation sur les pages de notification et d’avertissement** <br/><br/> _EnableOrganizationBranding_|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Non sélectionnée <br/><br/> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br/><br/> Avant d’activer ce paramètre, vous devez suivre les instructions dans Personnaliser le thème [Microsoft 365](../../admin/setup/customize-your-organization-theme.md) pour que votre organisation télécharge le logo de votre entreprise.|
|**Notification**||||||
|**Comment souhaitez-vous en informer vos utilisateurs ?**|**Utiliser le texte de notification par défaut**|**Utiliser le texte de notification par défaut**|**Utiliser le texte de notification par défaut**|**Utiliser le texte de notification par défaut**|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br/><br/> Vous pouvez sélectionner **Utiliser un texte de notification personnalisé** (_CustomNotificationText_) pour entrer le texte de notification personnalisé à utiliser. Vous pouvez également sélectionner **Utiliser Traducteur Microsoft** pour la localisation automatique (_UseTranslatedNotificationText_) pour traduire le texte de notification personnalisé dans la langue de l’utilisateur.

## <a name="related-articles"></a>Articles connexes

- Vous recherchez les meilleures pratiques pour Exchange **de flux de messagerie (également appelées règles de transport**) ? Voir [Meilleures pratiques pour la configuration des règles de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Les administrateurs et les utilisateurs peuvent soumettre des faux positifs (courrier électronique de qualité marqué comme faux) et des faux négatifs (courriers électroniques erronés autorisés) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour obtenir des informations **sur la configuration** de votre [service EOP](/exchange/standalone-eop/set-up-your-eop-service) et la **configuration** [de Microsoft Defender pour Office 365](defender-for-office-365.md). N’oubliez pas les instructions utiles dans « Protéger contre les menaces [Office 365](protect-against-threats.md) ».

- Les lignes de base de sécurité pour **Windows** sont disponibles ici : Où puis-je obtenir les lignes de base de sécurité [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options GPO/sur site, et utiliser les lignes de base de sécurité pour configurer les appareils [Windows dans Intune](/intune/protect/security-baselines) pour la sécurité basée sur Intune. Enfin, une comparaison entre les Microsoft Defender pour point de terminaison et Microsoft Intune de sécurité est disponible dans Comparer les Microsoft Defender pour point de terminaison [ Windows Intune de sécurité.](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines)
