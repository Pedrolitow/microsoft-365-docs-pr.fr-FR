---
title: Recommandations Microsoft pour les paramètres de sécurité EOP et Defender pour Office 365
keywords: Recommandations en matière de sécurité Office 365, sender policy framework, domain-based Message Reporting and Conformance, DomainKeys Identified Mail, steps, how does it work, security baselines, baselines for EOP, baselines for Defender for Office 365 , set up Defender for Office 365 , set up EOP, configure Defender for Office 365, configure EOP, security configuration
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Defender pour Office 365 ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous voulez être plus strict ? Quels sont les extras que vous obtenez si vous utilisez également Defender pour Office 365 ?
ms.openlocfilehash: c93475f1215477281604abe72d70a60a75c41b3f
ms.sourcegitcommit: 9833f95ab6ab95aea20d68a277246dca2223f93d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2021
ms.locfileid: "49794459"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Paramètres recommandés pour la sécurité d’EOP et de Microsoft Defender pour Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Exchange Online Protection (EOP)** est le cœur de la sécurité pour les abonnements Microsoft 365 et permet d’empêcher les e-mails malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes chaque jour, des protections améliorées sont souvent nécessaires. **Microsoft Defender pour Office 365** Les plans 1 ou Plan 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs davantage de niveaux de sécurité, de contrôle et d’examen.

Bien que nous donnent la possibilité aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : **Standard** et **Strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de filtrage contribueront à empêcher les messages indésirables d’atteindre la boîte de réception de vos employés dans la plupart des situations.

Pour appliquer automatiquement les paramètres Standard ou Strict aux utilisateurs, voir Stratégies de sécurité prédéfini dans EOP et [Microsoft Defender pour Office 365.](preset-security-policies.md)

> [!NOTE]
> La règle de courrier indésirable doit être activée sur les boîtes aux lettres pour que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Cet article décrit les paramètres par défaut, ainsi que les paramètres standard et strict recommandés pour protéger vos utilisateurs.

> [!TIP]
> Le module ORCA (Advanced Threat Protection Recommended Configuration Analyzer) Office 365 pour PowerShell peut vous aider (administrateurs) à trouver les valeurs actuelles de ces paramètres. Plus précisément, la cmdlet **Get-ORCAReport** génère une évaluation des paramètres de protection anti-courrier indésirable, anti-hameçonnage et autres paramètres d’hygiène des messages. Vous pouvez télécharger le module ORCA sur <https://www.powershellgallery.com/packages/ORCA/> .

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Protection anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage dans EOP

Les fonctionnalités anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons les configurations Standard ou Strict suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies anti-courrier indésirable, voir Configurer des stratégies [anti-courrier indésirable dans Office 365.](configure-your-spam-filter-policies.md)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Action de** détection du courrier indésirable <p> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection du courrier indésirable** à niveau de confiance élevé <p> _HighConfidenceSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection de courrier d’hameçonnage** <p> _PhishSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection de courrier de hameçonnage** à haut niveau de confiance <p> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Action de détection de courrier en** bloc <p> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Seuil des courriers électroniques en bloc <p> _BulkThreshold_|7 |6 |4 |Pour plus d’informations, voir [Niveau de réclamation en bloc (BCL) dans Office 365.](bulk-complaint-level-values.md)|
|Période de rétention de mise en quarantaine <p> _QuarantineRetentionPeriod_|15 jours|30 jours|30 jours||
|**Conseils de sécurité** <p> _InlineSafetyTipsEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|Expéditeurs autorisés <p> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs autorisés <p> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines à la liste des expéditeurs autorisés est une idée très mauvaise. Les attaquants pourraient vous envoyer des messages électroniques qui seraient autrement filtrés. <p> Utilisez [](learn-about-spoof-intelligence.md) la veille contre l’usurpation d’adresse dans le Centre de sécurité & conformité sur la page des **paramètres anti-courrier** indésirable pour passer en revue tous les expéditeurs qui usurpent des adresses e-mail d’expéditeur dans les domaines de messagerie de votre organisation ou usurpent des adresses de messagerie d’expéditeur dans des domaines externes.|
|Expéditeurs bloqués <p> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs bloqués <p> _BlockedSenderDomains_|Aucun|Aucun|Aucun||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <p> _EnableEndUserSpamNotifications_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <p> _EndUserSpamNotificationFrequency_|3 jours|3 jours|3 jours||
|**ZAP de courrier indésirable** <p> _SpamZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Phish ZAP** <p> _PhishZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|_MarkAsSpamBulkMail_|Activé|Activé|Activé|Ce paramètre est uniquement disponible dans PowerShell.|
|

Plusieurs autres paramètres de filtrage avancé du courrier indésirable (ASF) dans les stratégies anti-courrier indésirable sont en train d’être supprimés. Plus d’informations sur la chronologie de l’amortissement de ces fonctionnalités seront communiquées en dehors de cet article.

Nous vous recommandons de désactiver ces **paramètres** ASF pour les niveaux **Standard** **et Strict.** Pour plus d’informations sur les paramètres ASF, voir les paramètres de filtrage avancé du courrier indésirable [(ASF) dans Office 365.](advanced-spam-filtering-asf-options.md)

****

|Nom de la fonctionnalité de sécurité|Commentaire|
|---|---|
|**Liens d’image vers des sites distants** (_IncreaseScoreWithImageLinks_)||
|**Adresse IP numérique dans l’URL** (_IncreaseScoreWithNumericIps_)||
|**Redirection UL vers un autre port** (_IncreaseScoreWithRedirectToOtherPort_)||
|**URL des sites web .biz ou .info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Messages vides** (_MarkAsSpamEmptyMessages_)||
|**JavaScript ou VBScript en HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Balises Frame ou IFrame en HTML** (_MarkAsSpamFramesInHtml_)||
|**Balises d’objet en HTML** (_MarkAsSpamObjectTagsInHtml_)||
|**Incorporer des balises au format HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**Balises de formulaire en HTML** (_MarkAsSpamFormTagsInHtml_)||
|**Bogues web au format HTML** (_MarkAsSpamWebBugsInHtml_)||
|**Appliquer une liste de mots sensibles** (_MarkAsSpamSensitiveWordList_)||
|**Enregistrement SPF : échec en dur** (_MarkAsSpamSpfRecordHardFail_)||
|**Filtrage conditionnel de l’ID de** l’expéditeur : échec en dur (_MarkAsSpamFromAddressAuthFail_)||
|**NDR backscatter** (_MarkAsSpamNdrBackscatter_)||
|

#### <a name="eop-outbound-spam-policy-settings"></a>Paramètres de stratégie de courrier indésirable sortant EOP

Pour créer et configurer des stratégies de courrier indésirable sortant, voir Configurer le filtrage du courrier indésirable sortant [dans Office 365.](configure-the-outbound-spam-policy.md)

Pour plus d’informations sur les limites d’envoi par défaut dans le service, voir [Limites d’envoi.](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Nombre maximal de destinataires par utilisateur : limite horaire externe** <p> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite horaire interne** <p> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite quotidienne** <p> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Action lorsqu’un utilisateur dépasse les limites** <p> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages jusqu’au jour suivant** <p> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <p> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages électroniques** <p> `BlockUser`||
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies anti-programme malveillant, voir Configurer des stratégies [anti-programme malveillant dans Office 365.](configure-anti-malware-policies.md)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Voulez-vous avertir les destinataires si leurs messages sont mis en quarantaine ?** <p> _Action_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Filtre types de pièces jointes courants** <p> _EnableFileFilter_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu de la pièce jointe.|
|**Purge automatique des programmes malveillants sans heure** <p> _ZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Avertir les expéditeurs internes** du message non reçu <p> _EnableInternalSenderNotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|**Avertir les expéditeurs externes** du message non envoyé <p> _EnableExternalSenderNotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|

### <a name="eop-default-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage par défaut EOP

Pour plus d’informations sur ces paramètres, voir [Paramètres d’usurpation d’informations.](set-up-anti-phishing-policies.md#spoof-settings) Pour configurer ces paramètres, voir [Configurer des stratégies anti-hameçonnage dans EOP.](configure-anti-phishing-policies-eop.md)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection contre l’usurpation d’usurpation** <p> _EnableSpoofIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’expéditeur non authentifié** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, [voir Paramètres d’usurpation d’informations dans les stratégies anti-hameçonnage.](set-up-anti-phishing-policies.md)|
|**Si un e-mail est envoyé par une personne qui n’est pas autorisée à usurper votre domaine** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans la [veille contre l’usurpation d’adresse.](learn-about-spoof-intelligence.md)|
|

## <a name="microsoft-defender-for-office-365-security"></a>Sécurité Microsoft Defender pour Office 365

Des avantages supplémentaires en matière de sécurité sont ajoutés avec un abonnement Microsoft Defender pour Office 365. Pour obtenir les dernières actualités et informations, vous pouvez voir les nouveautés de [Defender pour Office 365.](whats-new-in-office-365-atp.md)

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 fournit une [protection](set-up-anti-phishing-policies.md#spoof-settings) contre l’usurpation d’adresse et une intelligence des boîtes aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités disponibles de [protection](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) contre l’emprunt d’identité et les paramètres avancés ne sont pas [configurés](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.
>
> - Il n’existe aucune stratégie de liens sécurisés ou de pièces jointes sécurisées par défaut qui protège automatiquement tous les destinataires de l’organisation. Pour obtenir les protections, vous devez créer au moins une stratégie de liens sécurisés et une stratégie de pièces jointes sécurisées.
>
> - [AtP pour SharePoint, OneDrive et](atp-for-spo-odb-and-teams.md) la protection Microsoft Teams et la protection des [documents](safe-docs.md) sécurisés n’ont pas de dépendances sur les stratégies de liens sécurisés.

Si votre abonnement inclut Microsoft Defender pour Office 365 ou si vous avez acheté Defender pour Office 365 en tant que module, définissez les configurations Standard ou Strict suivantes.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour Office 365

Les clients EOP obtiennent un anti-hameçonnage de base comme décrit précédemment, mais Microsoft Defender pour Office 365 inclut davantage de fonctionnalités et de contrôle pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, voir Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365.](configure-atp-anti-phishing-policies.md)

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ces paramètres, voir paramètres d’emprunt d’identité dans les [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) Pour configurer ces paramètres, voir Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365.](configure-atp-anti-phishing-policies.md)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|Utilisateurs protégés : ajouter **des utilisateurs à protéger** <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of users\>|Activé <p> `$true` <p> \<list of users\>|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans les rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, votre directeur financier et d’autres cadres supérieurs. En externe, les expéditeurs protégés peuvent inclure des membres du conseil ou votre conseil d’administration.|
|Domaines protégés : inclure automatiquement **les domaines dont je suis propriétaire** <p> _EnableOrganizationDomainsProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|Domaines protégés : inclure **des domaines personnalisés** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of domains\>|Activé <p> `$true` <p> \<list of domains\>|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines (domaines d’expéditeur) que vous ne possédez pas, mais avec qui vous interagissez fréquemment.|
|Utilisateurs protégés : **si le courrier électronique est envoyé par un utilisateur dont l’identité est usurpée** <p> _TargetedUserProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre le message en quarantaine** <p> `Quarantine`|**Mettre le message en quarantaine** <p> `Quarantine`||
|Domaines protégés : si le courrier électronique est envoyé par un domaine **dont l’identité est usurpée** <p> _TargetedDomainProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre le message en quarantaine** <p> `Quarantine`|**Mettre le message en quarantaine** <p> `Quarantine`||
|**Afficher les conseils pour les utilisateurs dont l’identité est usurpée** <p> _EnableSimilarUsersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher le conseil pour les domaines dont l’identité est usurpée** <p> _EnableSimilarDomainsSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher les conseils pour les caractères inhabituels** <p> _EnableUnusualCharactersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’intelligence des boîtes aux lettres ?** <p> _EnableMailboxIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer la protection contre l’usurpation d’identité basée sur l’intelligence des boîtes aux lettres** <p> _EnableMailboxIntelligenceProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Si le courrier électronique est envoyé par un utilisateur dont l’identité est protégée par l’intelligence des boîtes aux lettres** <p> _MailboxIntelligenceProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`||
|**Expéditeurs approuvés** <p> _ExcludedSenders_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs marqués à tort comme hameçonnages en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|**Domaines approuvés** <p> _ExcludedDomains_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines qui sont marqués de manière incorrecte comme hameçonnage en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|

#### <a name="spoof-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’usurpation dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Notez que ces paramètres sont les mêmes que ceux disponibles dans les paramètres de stratégie [anti-courrier indésirable dans EOP.](#eop-anti-spam-policy-settings)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|---|---|---|---|
|**Activer la protection contre l’usurpation d’usurpation** <p> _EnableSpoofIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’expéditeur non authentifié** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, [voir Paramètres d’usurpation d’informations dans les stratégies anti-hameçonnage.](set-up-anti-phishing-policies.md)|
|**Si un e-mail est envoyé par une personne qui n’est pas autorisée à usurper votre domaine** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers Courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre le message en quarantaine** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans la [veille contre l’usurpation d’adresse.](learn-about-spoof-intelligence.md)|
|

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ce paramètre, voir Seuils de hameçonnage avancés dans les [stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365) Pour configurer ce paramètre, voir Configurer des [stratégies anti-hameçonnage dans Defender pour Office 365.](configure-atp-anti-phishing-policies.md)

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuils de hameçonnage avancés** <p> _PhishThresholdLevel_|**1 - Standard** <p> `1`|**2 - Agressif** <p> `2`|**3 - Plus agressif** <p> `3`||
|

### <a name="safe-links-settings"></a>Paramètres de liens sécurisés

La stratégie De liens sécurisés dans Defender pour Office 365 inclut des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies de liens sécurisés actifs, ainsi que des paramètres spécifiques à chaque stratégie de liens sécurisés. Pour plus d’informations, [voir Liens sécurisés dans Defender pour Office 365.](atp-safe-links.md)

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux des liens sécurisés

Pour configurer ces paramètres, voir Configurer les paramètres globaux des liens [sécurisés dans Defender pour Office 365.](configure-global-settings-for-safe-links.md)

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Utiliser des liens sécurisés dans : applications Office 365** <p> _EnableSafeLinksForO365Clients_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Utilisez la fonction Liens sécurisés dans les applications office 365 de bureau et mobiles (iOS et Android) pris en charge. Pour plus d’informations, voir Paramètres de liens [sécurisés pour les applications Office 365.](atp-safe-links.md#safe-links-settings-for-office-365-apps)|
|**Ne pas suivre le moment où les utilisateurs cliquent sur Liens sécurisés** <p> _TrackClicks_|Activé <p> `$false`|Désactivé <p> `$true`|Désactivé <p> `$true`|La définition de ce paramètre (définition de _TrackClicks_ sur ) suit les clics des utilisateurs dans les applications `$true` Office 365 pris en charge.|
|**Ne pas laisser les utilisateurs cliquer sur liens sécurisés vers l’URL d’origine** <p> _AllowClickThrough_|Activé <p> `$false`|Activé <p> `$false`|Activé <p> `$false`|L’turning on this setting (setting _AllowClickThrough_ to `$false` ) prevents click through to the original URL in supported Office 365 apps.|
|

#### <a name="safe-links-policy-settings"></a>Paramètres de stratégie de liens sécurisés

Pour configurer ces paramètres, voir Configurer les stratégies de liens sécurisés [dans Microsoft Defender pour Office 365.](set-up-atp-safe-links-policies.md)

Dans PowerShell, vous utilisez les cmdlets [New-SafeLinksPolicy](https://docs.microsoft.com/powershell/module/exchange/new-safelinkspolicy) et [Set-SafeLinksPolicy](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de liens sécurisés par défaut. Les valeurs de la colonne Par défaut sont les valeurs par défaut des nouvelles stratégies de liens sécurisés que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans les messages** <p> _IsEnabled_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft Teams** <p> _EnableSafeLinksForTeams_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** <p> _ScanUrls_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Attendre la fin de l’analyse de l’URL avant de remettre le message** <p> _DeliverMessageAfterScan_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Appliquer des liens sûrs aux messages électroniques envoyés au sein de l’organisation** <p> _EnableForInternalSenders_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Ne pas suivre les clics de l’utilisateur** <p> _DoNotTrackUserClicks_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`|La dés off off this setting (setting _DoNotTrackUserClicks_ to `$false` ) suit les clics des utilisateurs.|
|**Ne pas autoriser les utilisateurs à accéder à l’URL d’origine** <p> _DoNotAllowClickThrough_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|L’turning on this setting (setting _DoNotAllowClickThrough_ to `$true` ) prevents click through to the original URL.|
|

### <a name="safe-attachments-settings"></a>Paramètres des pièces jointes sécurisées

Les pièces jointes sécurisées dans Microsoft Defender pour Office 365 incluent les paramètres globaux qui n’ont aucune relation avec les stratégies de pièces jointes sécurisées et les paramètres spécifiques à chaque stratégie de liens sécurisés. Pour plus d’informations, [voir Pièces jointes sécurisées dans Defender pour Office 365.](atp-safe-attachments.md)

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux des pièces jointes sécurisées

Pour configurer ces paramètres, voir Activer LAP pour [SharePoint, OneDrive et Microsoft Teams](turn-on-atp-for-spo-odb-and-teams.md) et documents sécurisés dans Microsoft [365 E5.](safe-docs.md)

Dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Activé <p> `$true`|Activé <p> `$true`||
|**Activer les documents sécurisés pour les clients Office** <p> _EnableSafeDocs_|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre est disponible uniquement avec les licences de sécurité Microsoft 365 E5 ou Microsoft 365 E5. Pour plus d’informations, [voir Documents sécurisés dans Microsoft Defender pour Office 365.](safe-docs.md)|
|**Autoriser les utilisateurs à cliquer dans le affichage protégé même si les documents sécurisés ont identifié le fichier comme malveillant** <p> _AllowSafeDocsOpen_|Désactivé <p> `$false`|Désactivé <p> `$false`|Ce paramètre est lié aux documents sécurisés.|
|

#### <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes sécurisées

Pour configurer ces paramètres, voir Configurer les stratégies de pièces [jointes sécurisées dans Defender pour Office 365.](set-up-atp-safe-attachments-policies.md)

Dans PowerShell, vous utilisez les cmdlets [New-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy) et [Set-SafeAttachmentPolicy](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de pièces jointes sécurisées par défaut. Les valeurs de la colonne Par défaut sont les valeurs par défaut des nouvelles stratégies de pièces jointes sécurisées que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Réponse aux programmes malveillants inconnus pour les pièces jointes sécurisées** <p> _Action_|Bloquer <p> `Block`|Bloquer <p> `Block`|Bloquer <p> `Block`||
|**Rediriger la pièce jointe lors de la détection** : activer la **redirection** <p> _Redirect_ <p> _RedirectAddress_|Hors service et aucune adresse de messagerie n’est spécifiée. <p> `$true` <p> aucune|On, and specify an email address. <p> `$true` <p> une adresse e-mail|On, and specify an email address. <p> `$true` <p> une adresse e-mail|Rediriger les messages vers un administrateur de sécurité pour révision.|
|**Appliquez la sélection ci-dessus si l’analyse des programmes malveillants pour les pièces jointes arrive à son moment ou si une erreur se produit.** <p> _ActionOnError_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|

## <a name="related-articles"></a>Articles connexes

- Vous recherchez les meilleures pratiques pour les règles de flux de **messagerie Exchange (également appelées règles de transport)**? Consultez [les meilleures pratiques pour configurer les règles de flux de messagerie dans Exchange Online.](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices)

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (e-mail de qualité marqué comme faux) et des faux négatifs (courriers électroniques erronés autorisés) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour  obtenir des informations sur la configuration de votre [service EOP](set-up-your-eop-service.md)et la **configuration** de Microsoft Defender pour [Office 365.](office-365-atp.md) N’oubliez pas les instructions utiles dans « Protéger contre[les menaces dans Office 365](protect-against-threats.md)».

- Les lignes de base de sécurité pour **Windows** sont disponibles ici : Où puis-je obtenir les lignes de base de sécurité [?](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options GPO/sur site, et utiliser les lignes de base de sécurité pour configurer les appareils [Windows 10 dans Intune](https://docs.microsoft.com/intune/protect/security-baselines) pour la sécurité basée sur Intune. Enfin, une comparaison entre les lignes de base de sécurité microsoft Defender pour point de terminaison et Microsoft Intune est disponible dans Comparer microsoft Defender pour le point de terminaison et les lignes de base de sécurité [Windows Intune.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines)
