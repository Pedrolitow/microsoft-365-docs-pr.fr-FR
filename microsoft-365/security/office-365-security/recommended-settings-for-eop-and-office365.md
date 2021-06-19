---
title: Recommandations Microsoft pour EOP et Defender pour les paramètres Office 365 de sécurité
keywords: recommandations en matière de sécurité Office 365, sender policy framework, domain-based Message Reporting and Conformance, DomainKeys Identified Mail, steps, how does it work, security baselines, baselines for EOP, baselines for Defender for Office 365 , set up Defender for Office 365 , set up EOP, configure Defender for Office 365, configure EOP, security configuration
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Quelles sont les meilleures pratiques pour Exchange Online Protection (EOP) et Defender pour Office 365 de sécurité ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous voulez être plus strict ? Quels sont les extras que vous obtenez si vous utilisez également Defender pour Office 365 ?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 031dd6ffe05c700b65fb56da90a49ed194c17321
ms.sourcegitcommit: c70067b4ef9c6f8f04aca68c35bb5141857c4e4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "53029512"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** est le cœur de la sécurité des abonnements Microsoft 365 et permet d’empêcher les e-mails malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes chaque jour, des protections améliorées sont souvent nécessaires. **Microsoft Defender pour Office 365** Les plans 1 ou Plan 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs davantage de niveaux de sécurité, de contrôle et d’examen.

Bien que nous donnent la possibilité aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : **Standard** et **Strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de filtrage contribueront à empêcher les messages indésirables d’atteindre la boîte de réception de vos employés dans la plupart des situations.

Pour appliquer automatiquement les paramètres Standard ou Strict aux utilisateurs, consultez Stratégies de sécurité prédéfini dans [EOP](preset-security-policies.md)et Microsoft Defender pour Office 365 .

> [!NOTE]
> La règle de courrier indésirable doit être activée sur les boîtes aux lettres pour que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md).

Cet article décrit les paramètres par défaut, ainsi que les paramètres standard et strict recommandés pour protéger vos utilisateurs. Les tableaux contiennent les paramètres dans le portail Microsoft 365 Defender et PowerShell (Exchange Online PowerShell ou Exchange Online Protection PowerShell autonome pour les organisations Exchange Online boîtes aux lettres).

> [!TIP]
> Le Office 365 module ORCA (Advanced Threat Protection Recommended Configuration Analyzer) pour PowerShell peut vous aider (administrateurs) à trouver les valeurs actuelles de ces paramètres. Plus précisément, la cmdlet **Get-ORCAReport** génère une évaluation des paramètres d’hygiène des messages anti-courrier indésirable, anti-hameçonnage et autres. Vous pouvez télécharger le module ORCA sur <https://www.powershellgallery.com/packages/ORCA/> .

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Protection anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage dans EOP

Les fonctionnalités anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons les configurations Standard ou Strict suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies anti-courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Action de** détection du courrier indésirable <p> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection du courrier indésirable** à niveau de confiance élevé <p> _HighConfidenceSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection du** hameçonnage <p> _PhishSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection du hameçonnage à haut** niveau de confiance <p> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de** détection en bloc <p> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Seuil des courriers électroniques en bloc** <p> _BulkThreshold_|7 |6 |4 |Pour plus d’informations, voir [Niveau de réclamation en bloc (BCL) dans EOP.](bulk-complaint-level-values.md)|
|_MarkAsSpamBulkMail_|Activé|Activé|Activé|Ce paramètre est uniquement disponible dans PowerShell.|
|**Conserver le courrier indésirable en quarantaine pendant ce nombre de jours** <p> _QuarantineRetentionPeriod_|15 jours|30 jours|30 jours||
|**Activer les conseils de sécurité contre le courrier indésirable** <p> _InlineSafetyTipsEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|Expéditeurs autorisés <p> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur autorisés <p> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines à la liste des expéditeurs autorisés est une idée très mauvaise. Les attaquants pourraient vous envoyer des messages électroniques qui seraient autrement filtrés. <p> Utilisez [](learn-about-spoof-intelligence.md) la veille contre l’usurpation d’adresses et la liste d’adresses ip/bloqués du client pour passer en revue tous les expéditeurs usurpant des adresses de messagerie d’expéditeur dans les domaines de messagerie de votre organisation ou usurpant des adresses de messagerie d’expéditeur dans des domaines externes. [](tenant-allow-block-list.md)|
|Expéditeurs bloqués <p> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs bloqués <p> _BlockedSenderDomains_|Aucun|Aucun|Aucun||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <p> _EnableEndUserSpamNotifications_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <p> _EndUserSpamNotificationFrequency_|3 jours|3 jours|3 jours||
|Activer la purge automatique d’heure zéro (ZAP) pour les messages de hameçonnage <p> _PhishZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|Activer ZAP pour le courrier indésirable <p> _SpamZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|

De nombreux paramètres de filtrage avancé du courrier indésirable (ASF) dans les stratégies anti-courrier indésirable sont en train d’être supprimés. Plus d’informations sur la chronologie de l’amortissement de ces fonctionnalités seront communiquées en dehors de cet article.

Nous vous recommandons de ne pas définir les **paramètres** ASF suivants pour les **niveaux Standard** et **Strict.** Pour plus d’informations sur les paramètres ASF, voir les paramètres de filtre de courrier indésirable avancé [(ASF) dans EOP.](advanced-spam-filtering-asf-options.md)

<br>

****

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
|

#### <a name="eop-outbound-spam-policy-settings"></a>Paramètres de stratégie de courrier indésirable sortant EOP

Pour créer et configurer des stratégies de courrier indésirable sortant, voir Configurer le filtrage du courrier indésirable sortant [dans EOP.](configure-the-outbound-spam-policy.md)

Pour plus d’informations sur les limites d’envoi par défaut dans le service, voir [Limites d’envoi.](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1)

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Définir une limite de messages externes** <p> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite de message interne** <p> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite quotidienne des messages** <p> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Restriction imposée aux utilisateurs qui atteignent la limite de message** <p> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages jusqu’au jour suivant** <p> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <p> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <p> `BlockUser`||
|**Règles de transmission automatique** <p> _AutoForwardingMode_|**Automatique - Contrôlé par le système** <p> `Automatic`|**Automatique - Contrôlé par le système** <p> `Automatic`|**Automatique - Contrôlé par le système** <p> `Automatic`|
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies anti-programme malveillant, voir Configurer des [stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Avertir les destinataires lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <p> _Action_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Activer le filtre des pièces jointes courantes** <p> _EnableFileFilter_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu de la pièce jointe.|
|**Activer la purge automatique zéro heure pour les programmes malveillants** <p> _ZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Avertir les expéditeurs internes lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <p> _EnableInternalSenderNotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|**Avertir les expéditeurs externes lorsque les messages sont mis en quarantaine en tant que programmes malveillants** <p> _EnableExternalSenderNotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|

### <a name="eop-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage EOP

Pour plus d’informations sur ces paramètres, voir [Paramètres d’usurpation d’informations.](set-up-anti-phishing-policies.md#spoof-settings) Pour configurer ces paramètres, voir [Configurer des stratégies anti-hameçonnage dans EOP.](configure-anti-phishing-policies-eop.md)

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la veille contre l’usurpation d’informations** <p> _EnableSpoofIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Si le courrier électronique est détecté comme usurpant une adresse** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs usurpés qui ont [](learn-about-spoof-intelligence.md) été automatiquement bloqués comme indiqué dans l’aperçu de l’usurpation d’intelligence ou qui ont été bloqués manuellement dans la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)|
|**Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’adresse** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook des expéditeurs usurpés non identifiés. Si vous souhaitez en savoir plus, consultez l’article [Paramètres d’usurpation dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Afficher la balise « via »** <p> _EnableViaTag_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse De si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM.** <p> Si ce paramètre n’est pas disponible, le point d’interrogation et la balise via sont tous deux contrôlés par la balise **Show (?)** pour les expéditeurs non authentifiés pour le paramètre d’usurpation d’adresse dans votre organisation. |
|

## <a name="microsoft-defender-for-office-365-security"></a>Microsoft Defender pour la Office 365 sécurité

Des avantages supplémentaires en matière de sécurité s’offrent à vous avec un abonnement Microsoft Defender Office 365 abonnement. Pour obtenir les dernières actualités et informations, vous pouvez voir les [nouveautés](whats-new-in-defender-for-office-365.md)de Defender pour Office 365 .

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut dans Microsoft [](set-up-anti-phishing-policies.md#spoof-settings) Defender pour Office 365 protection contre l’usurpation d’adresses et l’intelligence des boîtes aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités disponibles de [protection](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contre l’emprunt d’identité et les paramètres avancés ne sont pas [configurés](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.
>
> - Il n’existe aucune stratégie Safe liens ou Safe pièces jointes par défaut qui protègent automatiquement tous les destinataires de l’organisation. Pour obtenir les protections, vous devez créer au moins une stratégie Safe liens et Safe pièces jointes.
>
> - Safe pièces jointes pour [SharePoint, OneDrive](mdo-for-spo-odb-and-teams.md) et la protection Microsoft Teams et [la](safe-docs.md) protection Safe Documents ne sont pas dépendantes des stratégies Safe liens.

Si votre abonnement inclut Microsoft Defender pour Office 365 ou si vous avez acheté Defender pour Office 365 en tant que modules, définissez les configurations Standard ou Strict suivantes.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour les Office 365

Les clients EOP obtiennent un anti-hameçonnage de base comme décrit précédemment, mais Microsoft Defender pour Office 365 inclut davantage de fonctionnalités et de contrôle pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, voir Configurer des stratégies [anti-hameçonnage](configure-mdo-anti-phishing-policies.md)dans Defender pour Office 365 .

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ces paramètres, voir paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 . Pour configurer ces paramètres, voir Configurer des stratégies [anti-hameçonnage](configure-mdo-anti-phishing-policies.md)dans Defender pour Office 365 .

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|Utilisateurs protégés (expéditeurs) : **activer la protection des utilisateurs** <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of users\>|Activé <p> `$true` <p> \<list of users\>|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans les rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, votre directeur financier et d’autres cadres supérieurs. En externe, les expéditeurs protégés peuvent inclure des membres du conseil ou votre conseil d’administration.|
|Utilisateurs protégés : si le message est détecté comme un utilisateur dont **l’identité est usurpée** <p> _TargetedUserProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre le message en quarantaine** <p> `Quarantine`|**Mettre le message en quarantaine** <p> `Quarantine`||
|Domaines protégés : inclure **les domaines dont je suis propriétaire** <p> _EnableOrganizationDomainsProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|Domaines protégés : inclure **des domaines personnalisés** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of domains\>|Activé <p> `$true` <p> \<list of domains\>|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines (domaines d’expéditeur) que vous ne possédez pas, mais avec qui vous interagissez fréquemment.|
|Domaines protégés : si le message est détecté comme un domaine **dont l’identité a été usurpée** <p> _TargetedDomainProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre le message en quarantaine** <p> `Quarantine`|**Mettre le message en quarantaine** <p> `Quarantine`||
|**Ajouter des expéditeurs et des domaines de confiance** <p> _ExcludedSenders_ <p> _ExcludedDomains_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des expéditeurs ou des domaines qui sont identifiés à tort comme des tentatives d’emprunt d’identité.|
|**Activer l’intelligence des boîtes aux lettres** <p> _EnableMailboxIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer la veille pour la protection contre l’emprunt d’identité** <p> _EnableMailboxIntelligenceProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre autorise l’action spécifiée pour les détections d’emprunt d’identité par l’intelligence des boîtes aux lettres.|
|**Si l’intelligence de boîte aux lettres détecte et usurpe l’identité d’un utilisateur** <p> _MailboxIntelligenceProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`||
|**Afficher l’emprunt d’identité conseil de sécurité** <p> _EnableSimilarUsersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher les conseil de sécurité** <p> _EnableSimilarDomainsSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher les caractères inhabituels d’emprunt d’identité conseil de sécurité** <p> _EnableUnusualCharactersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|

#### <a name="spoof-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’usurpation d’une stratégie anti-hameçonnage dans Microsoft Defender pour Office 365

Notez que ces paramètres sont les mêmes que ceux disponibles dans les paramètres de stratégie [anti-courrier indésirable dans EOP.](#eop-anti-spam-policy-settings)

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la veille contre l’usurpation d’informations** <p> _EnableSpoofIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Si le courrier électronique est détecté comme usurpant une adresse** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs usurpés qui ont [](learn-about-spoof-intelligence.md) été automatiquement bloqués comme indiqué dans l’aperçu de l’usurpation d’intelligence ou qui ont été bloqués manuellement dans la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)|
|**Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’adresse** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook des expéditeurs usurpés non identifiés. Si vous souhaitez en savoir plus, consultez l’article [Paramètres d’usurpation dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Afficher la balise « via »** <p> _EnableViaTag_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse De si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM.** <p> Si ce paramètre n’est pas disponible, le point d’interrogation et la balise via sont tous deux contrôlés par la balise **Show (?)** pour les expéditeurs non authentifiés pour le paramètre d’usurpation d’adresse dans votre organisation. |
|

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ce paramètre, voir Seuils d’hameçonnage avancés dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)dans Microsoft Defender pour Office 365 . Pour configurer ce paramètre, voir Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil de courrier d’hameçonnage** <p> _PhishThresholdLevel_|**1 - Standard** <p> `1`|**2 - Agressif** <p> `2`|**3 - Plus agressif** <p> `3`||
|

### <a name="safe-links-settings"></a>Safe Paramètres des liens

Safe Les liens dans Defender pour Office 365 incluent des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies actives de liens Safe, ainsi que des paramètres spécifiques à chaque stratégie de liens Safe. Pour plus d’informations, [voir Safe liens dans Defender pour Office 365](safe-links.md).

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux des liens Safe web

Pour configurer ces paramètres, voir Configurer les [paramètres](configure-global-settings-for-safe-links.md)globaux pour les Safe dans Defender pour Office 365 .

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Utiliser Safe liens vers : Office 365 applications** <p> _EnableSafeLinksForO365Clients_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Utilisez Safe dans les applications de bureau et mobiles (iOS et Android) Office 365 pris en charge. Pour plus d’informations, [voir Safe liens pour les Office 365 applications.](safe-links.md#safe-links-settings-for-office-365-apps)|
|**Ne pas suivre le moment où les utilisateurs cliquent sur les liens protégés Office 365 applications** <p> _TrackClicks_|Activé <p> `$false`|Désactivé <p> `$true`|Désactivé <p> `$true`|La définition de ce paramètre (paramètre _TrackClicks_ sur ) suit les clics de l’utilisateur `$true` dans les applications Office 365 pris en charge.|
|**Ne pas laisser les utilisateurs accéder à l’URL d’origine dans Office 365 applications** <p> _AllowClickThrough_|Activé <p> `$false`|Activé <p> `$false`|Activé <p> `$false`|L’turning on this setting (setting _AllowClickThrough_ to `$false` ) prevents click through to the original URL in supported Office 365 apps.|
|

#### <a name="safe-links-policy-settings"></a>Safe Paramètres de stratégie de liens

Pour configurer ces paramètres, voir Configurer les stratégies Safe [liens dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

Dans PowerShell, vous utilisez les cmdlets [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) et [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de liens Safe par défaut. Les valeurs de la colonne Par défaut sont les valeurs par défaut des nouvelles stratégies Safe liens que vous créez.

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages** <p> _IsEnabled_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft Teams** <p> _EnableSafeLinksForTeams_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** <p> _ScanUrls_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Attendre la fin de l’analyse de l’URL avant de remettre le message** <p> _DeliverMessageAfterScan_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Appliquer Safe liens vers les messages électroniques envoyés au sein de l’organisation** <p> _EnableForInternalSenders_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Ne pas suivre les clics de l’utilisateur** <p> _DoNotTrackUserClicks_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`|La dés off off this setting (setting _DoNotTrackUserClicks_ to `$false` ) suit les clics des utilisateurs.|
|**Ne pas autoriser les utilisateurs à accéder à l’URL d’origine** <p> _DoNotAllowClickThrough_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|L’turning on this setting (setting _DoNotAllowClickThrough_ to `$true` ) prevents click through to the original URL.|
|

### <a name="safe-attachments-settings"></a>Safe Paramètres des pièces jointes

Safe Les pièces jointes dans Microsoft Defender pour Office 365 comprennent les paramètres globaux qui n’ont aucune relation avec les stratégies de pièces jointes Safe et les paramètres spécifiques à chaque stratégie de liens Safe. Pour plus d’informations, [voir Safe pièces jointes dans Defender pour Office 365](safe-attachments.md).

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux pour Safe pièces jointes

Pour configurer ces paramètres, voir Activer les pièces [jointes Safe](turn-on-mdo-for-spo-odb-and-teams.md) pour les documents SharePoint, OneDrive et Microsoft Teams et [Safe dans Microsoft 365 E5](safe-docs.md).

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Activé <p> `$true`|Activé <p> `$true`||
|**Activer les Safe documents pour Office clients** <p> _EnableSafeDocs_|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre n’est disponible qu’avec Microsoft 365 E5 ou Microsoft 365 E5 Sécurité licences. Pour plus d’informations, [Safe documents dans Microsoft Defender pour Office 365](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer dans le affichage protégé même si Safe documents ont identifié le fichier comme malveillant** <p> _AllowSafeDocsOpen_|Désactivé <p> `$false`|Désactivé <p> `$false`|Ce paramètre est lié à Safe Documents.|
|

#### <a name="safe-attachments-policy-settings"></a>Safe Paramètres de stratégie de pièces jointes

Pour configurer ces paramètres, voir Configurer les [stratégies Safe pièces jointes dans Defender pour Office 365](set-up-safe-attachments-policies.md).

Dans PowerShell, vous utilisez les cmdlets [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) et [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie Safe pièces jointes par défaut. Les valeurs de la colonne Par défaut sont les valeurs par défaut des nouvelles stratégies Safe pièces jointes que vous créez.

<br>

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Safe Réponse aux programmes malveillants inconnus pour les pièces jointes** <p> _Action_|Bloquer <p> `Block`|Bloquer <p> `Block`|Bloquer <p> `Block`||
|**Rediriger la pièce jointe lors de la détection** : activer la **redirection** <p> _Redirect_ <p> _RedirectAddress_|Hors service et aucune adresse de messagerie n’est spécifiée. <p> `$true` <p> aucune|On, and specify an email address. <p> `$true` <p> une adresse e-mail|On, and specify an email address. <p> `$true` <p> une adresse e-mail|Rediriger les messages vers un administrateur de sécurité pour révision.|
|**Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes arrive à son moment ou si une erreur se produit.** <p> _ActionOnError_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|

## <a name="related-articles"></a>Articles connexes

- Vous recherchez les meilleures pratiques pour Exchange règles de flux de **messagerie (également appelées règles de transport)**? Consultez [les meilleures pratiques pour configurer les règles de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (e-mail de qualité marqué comme faux) et des faux négatifs (courriers électroniques erronés autorisés) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour  plus d’informations sur la configuration de votre [service EOP](/exchange/standalone-eop/set-up-your-eop-service)et la **configuration** de Microsoft Defender [pour Office 365](defender-for-office-365.md). N’oubliez pas les instructions utiles dans « Protéger contre les menaces[Office 365](protect-against-threats.md)».

- Les lignes de base de sécurité pour **Windows** sont disponibles ici : Où puis-je obtenir les lignes de base de sécurité [?](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options GPO/sur site, et utiliser les lignes de base de sécurité pour configurer des appareils Windows 10 dans [Intune](/intune/protect/security-baselines) pour la sécurité basée sur Intune. Enfin, une comparaison entre les lignes de base de sécurité microsoft Defender pour point de terminaison et Microsoft Intune est disponible dans Comparez Microsoft Defender pour point de terminaison et les lignes de base de sécurité [Windows Intune.](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines)
