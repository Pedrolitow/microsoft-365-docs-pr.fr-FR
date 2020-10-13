---
title: Recommandations de Microsoft pour les paramètres de sécurité ATP et Office 365, recommandations, Sender Policy Framework, la création de rapports de messages basés sur un domaine, la conformité, la DomainKeys Identified identifiée, les étapes, son fonctionnement, les bases de sécurité, les configurations de base pour EOP, les configurations de base pour l’ATP, la configuration de la protection avancée contre les menaces, la configuration de l’ATP
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
- m365initiative-m365-defender
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Advanced Threat Protection (ATP) ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous voulez être plus strict ? Quels sont les autres éléments que vous obtenez si vous utilisez également la protection avancée contre les menaces ?
ms.openlocfilehash: fd2d680e093289aa5fc2dbcac127e35caf50098b
ms.sourcegitcommit: de600339b08951d6dd3933288a8da2327a4b6ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "48430656"
---
# <a name="recommended-settings-for-eop-and-office-365-atp-security"></a>Paramètres recommandés pour la sécurité ATP d’Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Exchange Online Protection (EoP)** est le cœur de la sécurité des abonnements Microsoft 365 et empêche les courriers électroniques malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes tous les jours, des protections améliorées sont souvent requises. **Office 365 Advanced Threat Protection (ATP)** Le plan ATP 1 ou le plan ATP 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs plus de couches de sécurité, de contrôle et d’enquête.

Bien que nous permettons aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Office 365 ATP qui nous sont recommandés : **standard** et **strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de filtrage contribueront à empêcher le courrier indésirable d’atteindre la boîte de réception de vos employés dans la plupart des situations.

Pour appliquer automatiquement les paramètres standard ou stricts aux utilisateurs, reportez-vous à la rubrique [stratégies de sécurité prédéfinies dans EOP et Office 365 ATP](preset-security-policies.md).

**Remarque**: la règle de courrier indésirable doit être activée sur les boîtes aux lettres afin que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Cet article décrit les paramètres par défaut, ainsi que les paramètres recommandés standard et stricts pour vous aider à protéger vos utilisateurs.

> [!TIP]
> Le module ORCA (Office 365 Advanced Threat Protection Recommended Configuration Analyzer) pour PowerShell peut vous aider à trouver les valeurs actuelles de ces paramètres. Plus précisément, la cmdlet **Get-ORCAReport** génère une évaluation du blocage du courrier indésirable, de l’anti-hameçonnage et d’autres paramètres d’hygiène des messages. Vous pouvez télécharger le module ORCA à l’adresse <https://www.powershellgallery.com/packages/ORCA/> .

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Blocage du courrier indésirable, des programmes malveillants et de la protection anti-hameçonnage dans EOP

Les fonctionnalités de blocage du courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons d’utiliser les configurations standard ou rigoureuses suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de la stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies de blocage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in Office 365](configure-your-spam-filter-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|Action de détection du **courrier indésirable** <br/><br/> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier indésirable à fiabilité élevée** <br/><br/> _HighConfidenceSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage** <br/><br/> _PhishSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage à haut niveau de fiabilité** <br/><br/> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier en nombre** <br/><br/> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Seuil de courrier électronique en masse <br/><br/> _BulkThreshold_|7 |6 |4 |Pour plus d’informations, reportez-vous à [Bulk Complaint Level (BCL) in Office 365](bulk-complaint-level-values.md).|
|Période de rétention de quarantaine <br/><br/> _QuarantineRetentionPeriod_|15 jours|30 jours|30 jours||
|**Conseils de sécurité** <br/><br/> _InlineSafetyTipsEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|Expéditeurs autorisés <br/><br/> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur autorisés <br/><br/> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines que vous possédez (_domaines acceptés_) à la liste des expéditeurs autorisés est une mauvaise idée. Les agresseurs seraient en mesure de vous envoyer des courriers électroniques qui seraient autrement filtrés. <br/><br/> Utilisez les fonctionnalités d' [usurpation d’identité](learn-about-spoof-intelligence.md) dans le centre de sécurité & conformité de la page **paramètres anti-courrier indésirable** pour examiner tous les expéditeurs qui usurpent l’identité des expéditeurs dans les domaines de messagerie de votre organisation ou usurper les adresses de messagerie de l’expéditeur dans les domaines externes.|
|Expéditeurs bloqués <br/><br/> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs bloqués <br/><br/> _BlockedSenderDomains_|Aucun|Aucun|Aucun||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <br/><br/> _EnableEndUserSpamNotifications_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <br/><br/> _EndUserSpamNotificationFrequency_|3 jours|3 jours|3 jours||
|**Blocage du courrier indésirable** <br/><br/> _SpamZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Hameçon ZAP** <br/><br/> _PhishZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|_MarkAsSpamBulkMail_|Activé|Activé|Activé|Ce paramètre est disponible uniquement dans PowerShell.|
|

Il existe plusieurs autres paramètres de filtre de courrier indésirable (ASF) dans les stratégies de blocage du courrier indésirable qui sont en cours de désapprobation. Pour plus d’informations sur les chronologies de l’amortissement de ces fonctionnalités, reportez-vous à cet article.

Nous vous **recommandons de désactiver ces paramètres ASF** pour les niveaux **standard** et **strict** . Pour plus d’informations sur les paramètres ASF, voir [paramètres de filtre de courrier indésirable avancés (ASF) dans Office 365](advanced-spam-filtering-asf-options.md).

****

|Nom de la fonctionnalité de sécurité|Commentaire|
|---|---|
|**Liens d’image vers des sites distants** (_IncreaseScoreWithImageLinks_)||
|**Adresse IP numérique dans l’URL** (_IncreaseScoreWithNumericIps_)||
|**Redirection UL vers un autre port** (_IncreaseScoreWithRedirectToOtherPort_)||
|**URL vers les sites Web. biz ou. info** (_IncreaseScoreWithBizOrInfoUrls_)||
|**Messages vides** (_MarkAsSpamEmptyMessages_)||
|**JavaScript ou VBScript en HTML** (_MarkAsSpamJavaScriptInHtml_)||
|**Balises Frame ou IFRAME en HTML** (_MarkAsSpamFramesInHtml_)||
|**Balises d’objet dans le code html** (_MarkAsSpamObjectTagsInHtml_)||
|**Balises embed en HTML** (_MarkAsSpamEmbedTagsInHtml_)||
|**Balises de formulaire dans le code html** (_MarkAsSpamFormTagsInHtml_)||
|**Bogues Web dans le code html** (_MarkAsSpamWebBugsInHtml_)||
|**Appliquer la liste de mots sensibles** (_MarkAsSpamSensitiveWordList_)||
|**Enregistrement SPF : échec matériel** (_MarkAsSpamSpfRecordHardFail_)||
|**Filtrage des ID de l’expéditeur conditionnel : échec matériel** (_MarkAsSpamFromAddressAuthFail_)||
|Notification de **non-remise rétrodiffusion** (_MarkAsSpamNdrBackscatter_)||
|

#### <a name="eop-outbound-spam-policy-settings"></a>Paramètres de stratégie de courrier indésirable sortant EOP

Pour créer et configurer des stratégies de courrier indésirable sortant, consultez la rubrique [configuration du filtrage du courrier indésirable sortant dans Office 365](configure-the-outbound-spam-policy.md).

Pour plus d’informations sur les limites d’envoi par défaut dans le service, consultez la rubrique [limites d’envoi](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Nombre maximal de destinataires par utilisateur : limite horaire externe** <br/><br/> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite horaire interne** <br/><br/> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite quotidienne** <br/><br/> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Action lorsqu’un utilisateur dépasse les limites** <br/><br/> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages jusqu’à la date suivante** <br/><br/> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`||
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies de protection contre les programmes malveillants, consultez la rubrique [configure anti-malware Policies in Office 365](configure-anti-malware-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Voulez-vous avertir les destinataires si leurs messages sont mis en quarantaine ?** <br/><br/> _Action_|Non <br/><br/> _DeleteMessage_|Non <br/><br/> _DeleteMessage_|Non <br/><br/> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Filtre de types de pièces jointes courantes** <br/><br/> _EnableFileFilter_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu des pièces jointes.|
|**Purge automatique contre les programmes malveillants à zéro heure** <br/><br/> _ZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Informer les expéditeurs internes** du message non remis <br/><br/> _EnableInternalSenderNotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|**Informer les expéditeurs externes** du message non remis <br/><br/> _Paramètre enableexternalsendernotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|

### <a name="eop-default-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage par défaut EOP

Pour plus d’informations sur ces paramètres, reportez-vous à la rubrique [usurpation Settings](set-up-anti-phishing-policies.md#spoof-settings). Pour configurer ces paramètres, consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection contre l’usurpation d’identité** <br/><br/> _EnableAntispoofEnforcement_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’expéditeur non authentifié** <br/><br/> _EnableUnauthenticatedSender_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

## <a name="office-365-advanced-threat-protection-security"></a>Sécurité avancée contre les menaces Office 365

Des avantages supplémentaires en matière de sécurité sont inclus dans un abonnement Office 365 Advanced Threat Protection (ATP). Pour obtenir les dernières informations et informations, vous pouvez consulter les nouveautés [d’Office 365 ATP](whats-new-in-office-365-atp.md).

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut ATP fournit une [protection contre les falsifications](set-up-anti-phishing-policies.md#spoof-settings) pour tous les destinataires. Toutefois, les paramètres de [protection contre l’emprunt d’identité](#impersonation-settings-in-atp-anti-phishing-policies) disponibles pour des expéditeurs ou des domaines d’expéditeur spécifiques ne sont pas configurés ou activés dans la stratégie par défaut. Pour activer la protection contre l’emprunt d’identité, configurez la stratégie par défaut ou créez des stratégies anti-hameçonnage supplémentaires ATP.
>
> - Aucune stratégie de liens fiables ou stratégies de pièces jointes fiables par défaut ne protège automatiquement tous les destinataires de l’organisation. Pour obtenir les protections, vous devez créer au moins une stratégie de liens fiables et une stratégie de pièces jointes fiables.
>
> - La protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md) protection et protection des [documents sécurisés](safe-docs.md) n’a aucune dépendance vis-à-vis des stratégies de liens fiables.

Si votre abonnement inclut Office 365 ATP ou si vous avez acheté Office 365 ATP en tant que module complémentaire, définissez les configurations standard ou rigoureuses suivantes.

### <a name="atp-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage ATP

Les clients EOP bénéficient d’une protection antiphishing de base comme décrit précédemment, mais Office 365 ATP inclut davantage de fonctionnalités et de contrôles pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, consultez la rubrique [configure ATP anti-phishing Policies in Office 365](configure-atp-anti-phishing-policies.md).

#### <a name="impersonation-settings-in-atp-anti-phishing-policies"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage ATP

Pour plus d’informations sur ces paramètres, consultez la rubrique [emprunt d’identité dans les stratégies anti-hameçonnage ATP](set-up-anti-phishing-policies.md#impersonation-settings-in-atp-anti-phishing-policies). Pour configurer ces paramètres, consultez la rubrique [configure ATP anti-phishing Policies](configure-atp-anti-phishing-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|Utilisateurs protégés : **Ajouter des utilisateurs à protéger** <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Désactivé <br/><br/> `$false` <br/><br/> aucune|Activé <br/><br/> `$true` <br/><br/> \<list of users\>|Activé <br/><br/> `$true` <br/><br/> \<list of users\>|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans les rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, votre directeur financier et d’autres dirigeants. De manière externe, les expéditeurs protégés peuvent inclure les membres du Conseil ou votre Conseil d’administration.|
|Domaines protégés : **inclure automatiquement les domaines dont je suis propriétaire** <br/><br/> _EnableOrganizationDomainsProtection_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|Domaines protégés : **inclure des domaines personnalisés** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Désactivé <br/><br/> `$false` <br/><br/> aucune|Activé <br/><br/> `$true` <br/><br/> \<list of domains\>|Activé <br/><br/> `$true` <br/><br/> \<list of domains\>|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines (domaines d’expéditeurs) dont vous n’êtes pas propriétaire, mais avec lesquels vous interagissez fréquemment.|
|Utilisateurs protégés : **si un message électronique est envoyé par un utilisateur représenté** <br/><br/> _TargetedUserProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Domaines protégés : **si un message électronique est envoyé par un domaine emprunté** <br/><br/> _TargetedDomainProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Afficher le Conseil pour les utilisateurs empruntés** <br/><br/> _EnableSimilarUsersSafetyTips_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Afficher le Conseil pour les domaines empruntés** <br/><br/> _EnableSimilarDomainsSafetyTips_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Afficher le Conseil pour les caractères inhabituels** <br/><br/> _EnableUnusualCharactersSafetyTips_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’intelligence des boîtes aux lettres ?** <br/><br/> _EnableMailboxIntelligence_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres ?** <br/><br/> _EnableMailboxIntelligenceProtection_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Si le courrier électronique est envoyé par un utilisateur emprunté protégé par la boîte aux lettres** <br/><br/> _MailboxIntelligenceProtectionAction_|**Ne pas appliquer d’action** <br/><br/> `NoAction`|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Expéditeurs approuvés** <br/><br/> _ExcludedSenders_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs qui sont identifiés de manière incorrecte comme hameçonnage en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|**Domaines approuvés** <br/><br/> _ExcludedDomains_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines qui ne sont pas marqués correctement comme hameçonnage en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|

#### <a name="spoof-settings-in-atp-anti-phishing-policies"></a>Paramètres d’usurpation dans les stratégies anti-hameçonnage ATP

Notez qu’il s’agit des mêmes paramètres que ceux disponibles dans les [paramètres de stratégie anti-courrier indésirable dans EOP](#eop-anti-spam-policy-settings).

****

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Activer la protection contre l’usurpation d’identité** <br/><br/> _EnableAntispoofEnforcement_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’expéditeur non authentifié** <br/><br/> _EnableUnauthenticatedSender_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

#### <a name="advanced-settings-in-atp-anti-phishing-policies"></a>Paramètres avancés dans les stratégies anti-hameçonnage ATP

Pour plus d’informations sur ce paramètre, consultez la rubrique [seuils d’hameçonnage avancés dans les stratégies anti-hameçonnage ATP](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-atp-anti-phishing-policies). Pour configurer ce paramètre, consultez la rubrique [configure ATP anti-phishing Policies](configure-atp-anti-phishing-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuils de hameçonnage avancés** <br/><br/> _PhishThresholdLevel_|**1-standard** <br/><br/> `1`|**2-agressif** <br/><br/> `2`|**3-plus agressif** <br/><br/> `3`||
|

### <a name="safe-links-settings"></a>Paramètres de liens fiables

Les liens fiables dans Office 365 ATP incluent des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies de liens fiables actifs, ainsi que les paramètres spécifiques à chaque stratégie de liens fiables. Pour plus d’informations, consultez la rubrique [liens approuvés dans Office 365 ATP](atp-safe-links.md).

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux pour les liens fiables

Pour configurer ces paramètres, voir [configure Global Settings for Safe Links in Office 365 ATP](configure-global-settings-for-safe-links.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Utiliser les liens fiables dans : applications Office 365** <br/><br/> _EnableSafeLinksForO365Clients_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Utiliser des liens fiables ATP dans les applications Office 365 Desktop et mobile (iOS et Android) prises en charge. Pour plus d’informations, consultez la rubrique [paramètres de liens approuvés pour les applications Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps).|
|**Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables** <br/><br/> _TrackClicks_|Activé <br/><br/> `$false`|Désactivé <br/><br/> `$true`|Désactivé <br/><br/> `$true`|La désactivation de ce paramètre (paramètre _TrackClicks_ à `$true` ) effectue le suivi des clics des utilisateurs dans les applications Office 365 prises en charge.|
|**Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine** <br/><br/> _AllowClickThrough_|Activé <br/><br/> `$false`|Activé <br/><br/> `$false`|Activé <br/><br/> `$false`|L’activation de ce paramètre ( _AllowClickThrough_ paramètre AllowClickThrough `$false` ) empêche le clic sur l’URL d’origine dans les applications Office 365 prises en charge.|
|

#### <a name="safe-links-policy-settings"></a>Paramètres de stratégie de liens fiables

Pour configurer ces paramètres, reportez-vous à la rubrique [configurer des stratégies de liens fiables dans Office 365 ATP](set-up-atp-safe-links-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safelinkspolicy) et [Set-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

**Remarque**: comme décrit précédemment, il n’existe aucune stratégie de liens approuvés par défaut. Les valeurs de la colonne par défaut sont les valeurs par défaut dans les nouvelles stratégies de liens approuvés que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Sélectionner l’action pour les URL potentiellement malveillantes dans les messages** <br/><br/> _IsEnabled_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams** <br/><br/> _EnableSafeLinksForTeams_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** <br/><br/> _ScanUrls_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Attendre la fin de l’analyse des URL avant de remettre le message** <br/><br/> _DeliverMessageAfterScan_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation** <br/><br/> _EnableForInternalSenders_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Ne pas suivre les clics des utilisateurs** <br/><br/> _DoNotTrackUserClicks_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Désactiver ce paramètre (paramètre _DoNotTrackUserClicks_ à `$false` ) effectue le suivi des clics des utilisateurs.|
|**Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine** <br/><br/> _DoNotAllowClickThrough_|Désactivé <br/><br/> `$false`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activer ce paramètre (paramètre _DoNotAllowClickThrough_ `$true` ) empêche le clic sur l’URL d’origine.|
|

### <a name="safe-attachments-settings"></a>Paramètres de pièces jointes fiables

Les pièces jointes fiables dans Office 365 ATP incluent des paramètres globaux qui n’ont aucune relation avec les stratégies de pièces jointes fiables et des paramètres spécifiques à chaque stratégie de liens fiables. Pour plus d’informations, consultez la rubrique [pièces jointes fiables dans Office 365 DAV](atp-safe-attachments.md).

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux pour les pièces jointes fiables

Pour configurer ces paramètres, reportez-vous à la rubrique activer la protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md) et [documents approuvés dans Microsoft 365 E5](safe-docs.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer des documents approuvés pour les clients Office**<bt/><br/> _EnableSafeDocs_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ce paramètre est disponible uniquement avec les licences de sécurité Microsoft 365 E5 ou Microsoft 365 E5. Pour plus d’informations, consultez la rubrique [documents approuvés dans Office 365 protection avancée contre les menaces](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer en mode protégé même si les documents fiables identifient le fichier comme étant malveillant**<bt/><br/> _AllowSafeDocsOpen_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|Ce paramètre est lié aux documents approuvés.|
|

#### <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes fiables

Pour configurer ces paramètres, voir [configurer des stratégies de pièces jointes fiables dans Office 365 ATP](set-up-atp-safe-attachments-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy) et [Set-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

**Remarque**: comme décrit précédemment, il n’y a pas de stratégie de pièces jointes approuvées par défaut. Les valeurs de la colonne par défaut sont les valeurs par défaut dans les nouvelles stratégies de pièces jointes approuvées que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Pièces jointes fiables réponse aux programmes malveillants inconnus** <br/><br/> _Action_|Bloquer <br/><br/> `Block`|Bloquer <br/><br/> `Block`|Bloquer <br/><br/> `Block`||
|**Redirection de la pièce jointe sur la détection** : **activer la redirection** <br/><br/> _Redirect_ <br/><br/> _RedirectAddress_|OFF et aucune adresse de messagerie n’est spécifiée. <br/><br/> `$true` <br/><br/> aucune|Et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse de messagerie|Et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse de messagerie|Rediriger les messages vers un administrateur de sécurité pour révision.|
|**Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit.** <br/><br/> _ActionOnError_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|

## <a name="related-articles"></a>Articles connexes

- Vous recherchez les meilleures pratiques pour les **règles de flux de messagerie Exchange (également appelées règles de transport**) ? Consultez la rubrique [Best Practices for Configuring mail Flow Rules in Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (courriers électroniques marqués comme incorrects) et des faux négatifs (courrier incorrect autorisé) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour obtenir des informations sur **la configuration de votre** [service EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-your-eop-service), ainsi que sur la **configuration** de la [Protection avancée contre les menaces d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp). N’oubliez pas les instructions utiles dans «[protéger contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)».

- Les **bases de sécurité pour Windows** sont disponibles [ici](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) [pour les options](https://docs.microsoft.com/intune/protect/security-baselines) d’objet de stratégie de groupe/local et pour la sécurité basée sur Intune. Enfin, une comparaison entre Microsoft Defender Advanced Threat Protection (ATP) et les bases de sécurité Microsoft Intune est disponible [ici](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
