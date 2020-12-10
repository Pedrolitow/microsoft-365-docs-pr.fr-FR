---
title: Recommandations de Microsoft pour les paramètres de sécurité EOP et Defender pour Office 365 recommandations, Sender Policy Framework, rapport de message basé sur un domaine, Conformance, DomainKeys Identified de la messagerie identifiée, étapes, fonctionnement, bases de sécurité, configurations de base pour EOP, configurations de base pour Defender pour Office 365, set up Defender for Office 365, set up EOP, configure Defender for Office 365, configure EOP, Security Configuration
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
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Defender pour Office 365 ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous voulez être plus strict ? Quels sont les autres éléments que vous obtenez si vous utilisez également Defender pour Office 365 ?
ms.openlocfilehash: 192e37a1a9a373f7b6712600bc3c81189f7c51ad
ms.sourcegitcommit: ee39faf3507d0edc9497117b3b2854955c959c6c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "49615959"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Exchange Online Protection (EoP)** est le cœur de la sécurité des abonnements Microsoft 365 et empêche les courriers électroniques malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes tous les jours, des protections améliorées sont souvent requises. **Microsoft Defender pour Office 365** Plan 1 ou plan 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs plus de couches de sécurité, de contrôle et d’enquête.

Bien que nous permettons aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : **standard** et **strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de filtrage contribueront à empêcher le courrier indésirable d’atteindre la boîte de réception de vos employés dans la plupart des situations.

Pour appliquer automatiquement les paramètres standard ou stricts aux utilisateurs, reportez-vous à la rubrique [stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

> [!NOTE]
> La règle de courrier indésirable doit être activée sur les boîtes aux lettres afin que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

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
|Action de détection du **courrier indésirable** <p> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Action de détection de **courrier indésirable à fiabilité élevée** <p> _HighConfidenceSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Action de détection de **courrier d’hameçonnage** <p> _PhishSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Action de détection de **courrier d’hameçonnage à haut niveau de fiabilité** <p> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Action de détection de **courrier en nombre** <p> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Seuil de courrier électronique en masse <p> _BulkThreshold_|7 |6 |4 |Pour plus d’informations, reportez-vous à [Bulk Complaint Level (BCL) in Office 365](bulk-complaint-level-values.md).|
|Période de rétention de quarantaine <p> _QuarantineRetentionPeriod_|15 jours|30 jours|30 jours||
|**Conseils de sécurité** <p> _InlineSafetyTipsEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|Expéditeurs autorisés <p> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur autorisés <p> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines à la liste des expéditeurs autorisés est une mauvaise idée. Les agresseurs seraient en mesure de vous envoyer des courriers électroniques qui seraient autrement filtrés. <p> Utilisez les fonctionnalités d' [usurpation d’identité](learn-about-spoof-intelligence.md) dans le centre de sécurité & conformité de la page **paramètres anti-courrier indésirable** pour examiner tous les expéditeurs qui usurpent l’identité des expéditeurs dans les domaines de messagerie de votre organisation ou usurper les adresses de messagerie de l’expéditeur dans les domaines externes.|
|Expéditeurs bloqués <p> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines des expéditeurs bloqués <p> _BlockedSenderDomains_|Aucun|Aucun|Aucun||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <p> _EnableEndUserSpamNotifications_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <p> _EndUserSpamNotificationFrequency_|3 jours|3 jours|3 jours||
|**Blocage du courrier indésirable** <p> _SpamZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Hameçon ZAP** <p> _PhishZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
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
|**Nombre maximal de destinataires par utilisateur : limite horaire externe** <p> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite horaire interne** <p> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Nombre maximal de destinataires par utilisateur : limite quotidienne** <p> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Action lorsqu’un utilisateur dépasse les limites** <p> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages jusqu’à la date suivante** <p> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages** <p> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages** <p> `BlockUser`||
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies de protection contre les programmes malveillants, consultez la rubrique [configure anti-malware Policies in Office 365](configure-anti-malware-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Voulez-vous avertir les destinataires si leurs messages sont mis en quarantaine ?** <p> _Action_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Non <p> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Filtre de types de pièces jointes courantes** <p> _EnableFileFilter_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu des pièces jointes.|
|**Purge automatique contre les programmes malveillants à zéro heure** <p> _ZapEnabled_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Informer les expéditeurs internes** du message non remis <p> _EnableInternalSenderNotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|**Informer les expéditeurs externes** du message non remis <p> _Paramètre enableexternalsendernotifications_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`||
|

### <a name="eop-default-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage par défaut EOP

Pour plus d’informations sur ces paramètres, reportez-vous à la rubrique [usurpation Settings](set-up-anti-phishing-policies.md#spoof-settings). Pour configurer ces paramètres, consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection contre l’usurpation d’identité** <p> _EnableAntispoofEnforcement_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’expéditeur non authentifié** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

## <a name="microsoft-defender-for-office-365-security"></a>Sécurité Microsoft Defender pour Office 365

Des avantages supplémentaires en matière de sécurité sont offerts avec un abonnement Microsoft Defender pour Office 365. Pour obtenir les dernières nouvelles et informations, voir [what’s New in Defender for Office 365](whats-new-in-office-365-atp.md).

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 fournit une [protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) et une intelligence de boîte aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités de [protection contre l’emprunt d’identité](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) disponibles et les [Paramètres avancés](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ne sont pas configurés ni activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.
>
> - Aucune stratégie de liens fiables ou stratégies de pièces jointes fiables par défaut ne protège automatiquement tous les destinataires de l’organisation. Pour obtenir les protections, vous devez créer au moins une stratégie de liens fiables et une stratégie de pièces jointes fiables.
>
> - La protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md) protection et protection des [documents sécurisés](safe-docs.md) n’a aucune dépendance vis-à-vis des stratégies de liens fiables.

Si votre abonnement inclut Microsoft Defender pour Office 365 ou si vous avez acheté Defender pour Office 365 en tant que module complémentaire, définissez les configurations standard ou rigoureuses suivantes.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour Office 365

Les clients EOP reçoivent un antiphishing de base comme décrit précédemment, mais Microsoft Defender pour Office 365 inclut davantage de fonctionnalités et de contrôles pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, consultez la rubrique [configure anti-phishing Policies in Defender for Office 365](configure-atp-anti-phishing-policies.md).

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ces paramètres, reportez-vous à la rubrique [emprunt d’identité des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ces paramètres, consultez la rubrique [configure anti-phishing Policies in Defender for Office 365](configure-atp-anti-phishing-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|Utilisateurs protégés : **Ajouter des utilisateurs à protéger** <p> _EnableTargetedUserProtection_ <p> _TargetedUsersToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of users\>|Activé <p> `$true` <p> \<list of users\>|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans les rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, votre directeur financier et d’autres dirigeants. De manière externe, les expéditeurs protégés peuvent inclure les membres du Conseil ou votre Conseil d’administration.|
|Domaines protégés : **inclure automatiquement les domaines dont je suis propriétaire** <p> _EnableOrganizationDomainsProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|Domaines protégés : **inclure des domaines personnalisés** <p> _EnableTargetedDomainsProtection_ <p> _TargetedDomainsToProtect_|Désactivé <p> `$false` <p> aucune|Activé <p> `$true` <p> \<list of domains\>|Activé <p> `$true` <p> \<list of domains\>|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines (domaines d’expéditeurs) dont vous n’êtes pas propriétaire, mais avec lesquels vous interagissez fréquemment.|
|Utilisateurs protégés : **si un message électronique est envoyé par un utilisateur représenté** <p> _TargetedUserProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|Domaines protégés : **si un message électronique est envoyé par un domaine emprunté** <p> _TargetedDomainProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Mettre en quarantaine le message** <p> `Quarantine`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Afficher le Conseil pour les utilisateurs empruntés** <p> _EnableSimilarUsersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher le Conseil pour les domaines empruntés** <p> _EnableSimilarDomainsSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Afficher le Conseil pour les caractères inhabituels** <p> _EnableUnusualCharactersSafetyTips_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’intelligence des boîtes aux lettres ?** <p> _EnableMailboxIntelligence_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres ?** <p> _EnableMailboxIntelligenceProtection_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Si le courrier électronique est envoyé par un utilisateur emprunté protégé par la boîte aux lettres** <p> _MailboxIntelligenceProtectionAction_|**Ne pas appliquer d’action** <p> `NoAction`|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`||
|**Expéditeurs approuvés** <p> _ExcludedSenders_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des utilisateurs qui sont identifiés de manière incorrecte comme hameçonnage en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|**Domaines approuvés** <p> _ExcludedDomains_|Aucun|Aucun|Aucun|En fonction de votre organisation, nous vous recommandons d’ajouter des domaines qui ne sont pas marqués correctement comme hameçonnage en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|

#### <a name="spoof-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’usurpation dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Notez qu’il s’agit des mêmes paramètres que ceux disponibles dans les [paramètres de stratégie anti-courrier indésirable dans EOP](#eop-anti-spam-policy-settings).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|---|---|---|---|
|**Activer la protection contre l’usurpation d’identité** <p> _EnableAntispoofEnforcement_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|**Activer l’expéditeur non authentifié** <p> _EnableUnauthenticatedSender_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <p> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <p> `MoveToJmf`|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <p> `MoveToJmf`|**Mettre en quarantaine le message** <p> `Quarantine`|Ce paramètre s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres avancés des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ce paramètre, voir [Advanced phishing Thresholds in anti-phishing Policies in Microsoft Defender for Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ce paramètre, consultez la rubrique [configure anti-phishing Policies in Defender for Office 365](configure-atp-anti-phishing-policies.md).

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuils de hameçonnage avancés** <p> _PhishThresholdLevel_|**1-standard** <p> `1`|**2-agressif** <p> `2`|**3-plus agressif** <p> `3`||
|

### <a name="safe-links-settings"></a>Paramètres de liens fiables

Les liens fiables dans Defender pour Office 365 incluent des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans les stratégies de liens fiables actifs, ainsi que les paramètres spécifiques à chaque stratégie de liens fiables. Pour plus d’informations, consultez la rubrique [liens approuvés dans Defender pour Office 365](atp-safe-links.md).

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux pour les liens fiables

Pour configurer ces paramètres, voir [configure Global Settings for Safe Links in Defender for Office 365](configure-global-settings-for-safe-links.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Utiliser les liens fiables dans : applications Office 365** <p> _EnableSafeLinksForO365Clients_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`|Utiliser les liens fiables dans les applications Office 365 Desktop et mobile (iOS et Android) prises en charge. Pour plus d’informations, consultez la rubrique [paramètres de liens approuvés pour les applications Office 365](atp-safe-links.md#safe-links-settings-for-office-365-apps).|
|**Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables** <p> _TrackClicks_|Activé <p> `$false`|Désactivé <p> `$true`|Désactivé <p> `$true`|La désactivation de ce paramètre (paramètre _TrackClicks_ à `$true` ) effectue le suivi des clics des utilisateurs dans les applications Office 365 prises en charge.|
|**Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine** <p> _AllowClickThrough_|Activé <p> `$false`|Activé <p> `$false`|Activé <p> `$false`|L’activation de ce paramètre (  paramètre AllowClickThrough `$false` ) empêche le clic sur l’URL d’origine dans les applications Office 365 prises en charge.|
|

#### <a name="safe-links-policy-settings"></a>Paramètres de stratégie de liens fiables

Pour configurer ces paramètres, reportez-vous à la rubrique [configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-atp-safe-links-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safelinkspolicy) et [Set-safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de liens approuvés par défaut. Les valeurs de la colonne par défaut sont les valeurs par défaut dans les nouvelles stratégies de liens approuvés que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Sélectionner l’action pour les URL potentiellement malveillantes dans les messages** <p> _IsEnabled_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams** <p> _EnableSafeLinksForTeams_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** <p> _ScanUrls_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Attendre la fin de l’analyse des URL avant de remettre le message** <p> _DeliverMessageAfterScan_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation** <p> _EnableForInternalSenders_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`||
|**Ne pas suivre les clics des utilisateurs** <p> _DoNotTrackUserClicks_|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactivé <p> `$false`|Désactiver ce paramètre (paramètre _DoNotTrackUserClicks_ à `$false` ) effectue le suivi des clics des utilisateurs.|
|**Ne pas autoriser les utilisateurs à cliquer vers l’URL d’origine** <p> _DoNotAllowClickThrough_|Désactivé <p> `$false`|Activé <p> `$true`|Activé <p> `$true`|Activer ce paramètre (paramètre _DoNotAllowClickThrough_ `$true` ) empêche le clic sur l’URL d’origine.|
|

### <a name="safe-attachments-settings"></a>Paramètres de pièces jointes fiables

Les pièces jointes fiables dans Microsoft Defender pour Office 365 incluent des paramètres globaux qui n’ont aucune relation avec les stratégies de pièces jointes fiables et des paramètres spécifiques à chaque stratégie de liens fiables. Pour plus d’informations, consultez la rubrique [pièces jointes fiables dans Defender pour Office 365](atp-safe-attachments.md).

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux pour les pièces jointes fiables

Pour configurer ces paramètres, reportez-vous à la rubrique activer la protection avancée contre [les menaces pour SharePoint, OneDrive et Microsoft teams](turn-on-atp-for-spo-odb-and-teams.md) et [documents approuvés dans Microsoft 365 E5](safe-docs.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams** <p> _EnableATPForSPOTeamsODB_|Activé <p> `$true`|Activé <p> `$true`||
|**Activer des documents approuvés pour les clients Office** <p> _EnableSafeDocs_|Activé <p> `$true`|Activé <p> `$true`|Ce paramètre est disponible uniquement avec les licences de sécurité Microsoft 365 E5 ou Microsoft 365 E5. Pour plus d’informations, reportez-vous à la rubrique [documents approuvés dans Microsoft Defender pour Office 365](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer en mode protégé même si les documents fiables identifient le fichier comme étant malveillant** <p> _AllowSafeDocsOpen_|Désactivé <p> `$false`|Désactivé <p> `$false`|Ce paramètre est lié aux documents approuvés.|
|

#### <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes fiables

Pour configurer ces paramètres, reportez-vous à la rubrique [configurer des stratégies de pièces jointes fiables dans Defender pour Office 365](set-up-atp-safe-attachments-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy) et [Set-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’y a pas de stratégie de pièces jointes approuvées par défaut. Les valeurs de la colonne par défaut sont les valeurs par défaut dans les nouvelles stratégies de pièces jointes approuvées que vous créez.

****

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Empêcher|Commentaire|
|---|:---:|:---:|:---:|---|
|**Pièces jointes fiables réponse aux programmes malveillants inconnus** <p> _Action_|Bloquer <p> `Block`|Bloquer <p> `Block`|Bloquer <p> `Block`||
|**Redirection de la pièce jointe sur la détection** : **activer la redirection** <p> _Redirect_ <p> _RedirectAddress_|OFF et aucune adresse de messagerie n’est spécifiée. <p> `$true` <p> aucune|Et spécifiez une adresse de messagerie. <p> `$true` <p> une adresse de messagerie|Et spécifiez une adresse de messagerie. <p> `$true` <p> une adresse de messagerie|Rediriger les messages vers un administrateur de sécurité pour révision.|
|**Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit.** <p> _ActionOnError_|Activé <p> `$true`|Activé <p> `$true`|Activé <p> `$true`||
|

## <a name="related-articles"></a>Articles connexes

- Vous recherchez les meilleures pratiques pour les **règles de flux de messagerie Exchange (également appelées règles de transport**) ? Consultez la rubrique [Best Practices for Configuring mail Flow Rules in Exchange Online](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (courriers électroniques marqués comme incorrects) et des faux négatifs (courrier incorrect autorisé) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour obtenir des informations sur la façon de **configurer** votre [service EOP](set-up-your-eop-service.md)et **configurer** [Microsoft Defender pour Office 365](office-365-atp.md). N’oubliez pas les instructions utiles dans «[protéger contre les menaces dans Office 365](protect-against-threats.md)».

- Les **bases de sécurité pour Windows** sont disponibles ici : [où puis-je obtenir les bases de sécurité ?](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options d’objets de stratégie de groupe/de site et les [bases de sécurité pour configurer les appareils Windows 10 dans Intune](https://docs.microsoft.com/intune/protect/security-baselines) pour la sécurité basée sur Intune. Enfin, une comparaison entre Microsoft Defender pour le point de terminaison et les bases de sécurité Microsoft Intune est disponible dans [comparaison des lignes de base de sécurité Microsoft Defender pour les points de terminaison et Windows Intune](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
