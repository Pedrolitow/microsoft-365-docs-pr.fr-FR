---
title: Recommandations de Microsoft pour les paramètres de sécurité ATP et Office 365, recommandations, Sender Policy Framework, la création de rapports de messages basés sur un domaine, la conformité, la DomainKeys Identified identifiée, les étapes, son fonctionnement, les bases de sécurité, les configurations de base pour EOP, les configurations de base pour l’ATP, la configuration de la protection avancée contre les menaces, la configuration EOP
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: ''
manager: dansimp
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Advanced Threat Protection (ATP) ? Quelles sont les recommandations actuelles pour la protection standard ? Qu’est-ce qui doit être utilisé si vous voulez être plus strict ? Quels sont les autres éléments que vous obtenez si vous utilisez également la protection avancée contre les menaces ?
ms.openlocfilehash: f34c4e0aad2413fdeb082c37f980e6e4548db6b3
ms.sourcegitcommit: 583fd1ac1f385c58b93bda648907a1bd8e0a1950
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "45430374"
---
# <a name="recommended-settings-for-eop-and-office-365-atp-security"></a>Paramètres recommandés pour la sécurité ATP d’Office 365

**Exchange Online Protection (EoP)** est le cœur de la sécurité des abonnements Microsoft 365 et empêche les courriers électroniques malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes tous les jours, des protections améliorées sont souvent requises. **Office 365 Advanced Threat Protection (ATP)** Le plan ATP 1 ou le plan ATP 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs plus de couches de sécurité, de contrôle et d’enquête.

Bien que nous permettons aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Office 365 ATP qui nous sont recommandés : **standard** et **strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de configurations de filtrage des messages empêchent le courrier indésirable d’atteindre la boîte de réception de vos employés dans la plupart des cas.

Pour appliquer automatiquement les paramètres standard ou stricts aux utilisateurs, reportez-vous à la rubrique [stratégies de sécurité prédéfinies dans EOP et Office 365 ATP](preset-security-policies.md).

> [!IMPORTANT]
> La règle de courrier indésirable doit être activée sur une boîte aux lettres pour que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Cette rubrique décrit ces paramètres recommandés par Microsoft pour vous aider à protéger vos utilisateurs.

> [!TIP]
> Il existe un nouveau module PowerShell que vous pouvez télécharger appelé Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) qui permet de déterminer certains de ces paramètres. Lorsqu’il est exécuté en tant qu’administrateur dans votre client, Get-ORCAReport permet de générer une évaluation du blocage du courrier indésirable, de l’anti-hameçonnage et d’autres paramètres d’hygiène des messages. Vous pouvez télécharger ce module à l’adresse https://www.powershellgallery.com/packages/ORCA/ .

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Blocage du courrier indésirable, des programmes malveillants et de la protection anti-hameçonnage dans EOP

Le blocage du courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités d’EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons d’utiliser les configurations suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de la stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies de blocage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in Office 365](configure-your-spam-filter-policies.md).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|Action de détection du **courrier indésirable** <br/><br/> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier indésirable à fiabilité élevée** <br/><br/> _HighConfidenceSpamAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage** <br/><br/> _PhishSpamAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage à haut niveau de fiabilité** <br/><br/> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier en nombre** <br/><br/> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Seuil de courrier électronique en masse <br/><br/> _BulkThreshold_|6 |4 |La valeur par défaut est actuellement 7, mais nous vous recommandons de la remplacer par 6. Pour plus d’informations, reportez-vous à [Bulk Complaint Level (BCL) in Office 365](bulk-complaint-level-values.md).|
|Période de rétention de quarantaine <br/><br/> _QuarantineRetentionPeriod_|30 jours|30 jours||
|**Conseils de sécurité** <br/><br/> _InlineSafetyTipsEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|Expéditeurs autorisés <br/><br/> _AllowedSenders_|Aucun|Aucun||
|Domaines d’expéditeur autorisés <br/><br/> _AllowedSenderDomains_|Aucun|Aucun|L’ajout de domaines dont vous êtes propriétaire (également appelés _domaines acceptés_) à la liste des expéditeurs autorisés n’est pas obligatoire. En fait, il est considéré comme un risque élevé, car il permet aux acteurs incorrects de vous envoyer des messages qui seraient autrement filtrés. Utilisez les fonctionnalités d' [usurpation d’identité](learn-about-spoof-intelligence.md) dans le centre de sécurité & conformité de la page **paramètres anti-courrier indésirable** pour examiner tous les expéditeurs qui usurpent l’identité des expéditeurs dans les domaines de messagerie de votre organisation ou usurper les adresses de messagerie de l’expéditeur dans les domaines externes.|
|Expéditeurs bloqués <br/><br/> _BlockedSenders_|Aucun|Aucun||
|Domaines des expéditeurs bloqués <br/><br/> _BlockedSenderDomains_|Aucun|Aucun||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <br/><br/> _EnableEndUserSpamNotifications_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <br/><br/> _EndUserSpamNotificationFrequency_|3 jours|3 jours||
|**Blocage du courrier indésirable** <br/><br/> _SpamZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Hameçon ZAP** <br/><br/> _PhishZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|_MarkAsSpamBulkMail_|Activé|Activé|Ce paramètre est disponible uniquement dans PowerShell.|
|

Il existe plusieurs autres paramètres de filtre de courrier indésirable (ASF) dans les stratégies de blocage du courrier indésirable qui sont en cours de désapprobation. Pour plus d’informations sur les chronologies de l’amortissement de ces fonctionnalités, reportez-vous à cette rubrique.

Nous vous **recommandons de désactiver ces paramètres ASF** pour les niveaux **standard** et **strict** . Pour plus d’informations sur les paramètres ASF, voir [paramètres de filtre de courrier indésirable avancés (ASF) dans Office 365](advanced-spam-filtering-asf-options.md).

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

Pour plus d’informations sur les limites d’envoi par défaut dans le service, consultez la rubrique [limites d’envoi](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1)

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Nombre maximal de destinataires par utilisateur : limite horaire externe** <br/><br/> _RecipientLimitExternalPerHour_|500|400||
|**Nombre maximal de destinataires par utilisateur : limite horaire interne** <br/><br/> _RecipientLimitInternalPerHour_|1000|800||
|**Nombre maximal de destinataires par utilisateur : limite quotidienne** <br/><br/> _RecipientLimitPerDay_|1000|800||
|**Action lorsqu’un utilisateur dépasse les limites** <br/><br/> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`||
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies de protection contre les programmes malveillants, consultez la rubrique [configure anti-malware Policies in Office 365](configure-anti-malware-policies.md).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Voulez-vous avertir les destinataires si leurs messages sont mis en quarantaine ?** <br/><br/> _Action_|Non <br/><br/> _DeleteMessage_|Non <br/><br/> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Filtre de types de pièces jointes courantes** <br/><br/> _EnableFileFilter_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu des pièces jointes.|
|**Purge automatique contre les programmes malveillants à zéro heure** <br/><br/> _ZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Informer les expéditeurs internes** du message non remis <br/><br/> _EnableInternalSenderNotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|**Informer les expéditeurs externes** du message non remis <br/><br/> _Paramètre enableexternalsendernotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|

### <a name="eop-default-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage par défaut EOP

Pour plus d’informations sur ces paramètres, reportez-vous à la rubrique [usurpation Settings](set-up-anti-phishing-policies.md#spoof-settings). Pour configurer ces paramètres, consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Activer la protection contre l’usurpation d’identité** <br/><br/> _EnableAntispoofEnforcement_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’expéditeur non authentifié** <br/><br/> _EnableUnauthenticatedSender_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|Cela s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

## <a name="office-365-advanced-threat-protection-security"></a>Sécurité avancée contre les menaces Office 365

Des avantages supplémentaires en matière de sécurité sont inclus dans un abonnement Office 365 Advanced Threat Protection (ATP). Pour obtenir les dernières informations et informations, vous pouvez consulter les nouveautés [d’Office 365 ATP](whats-new-in-office-365-atp.md).

La protection avancée contre les menaces Office 365 inclut les stratégies de pièces jointes fiables et de liens fiables pour empêcher la remise des messages contenant des pièces jointes potentiellement malveillantes et empêcher les utilisateurs de cliquer sur les URL potentiellement dangereuses.

> [!IMPORTANT]
> La protection avancée contre le hameçonnage est l’un des avantages d’un abonnement Office 365 ATP. Bien qu’elle soit activée par défaut, vous ***devez*** configurer au moins une stratégie anti-hameçonnage avant de pouvoir commencer à filtrer les messages. Oublier de configurer des stratégies anti-hameçonnage pourrait exposer les utilisateurs à des courriers électroniques risqués. Veillez à configurer vos stratégies anti-hameçonnage après avoir ajouté un abonnement Office 365 ATP.

Si vous avez ajouté un abonnement Office 365 ATP à votre EOP, définissez les configurations suivantes.

### <a name="office-atp-anti-phishing-policy-settings"></a>Paramètres de la stratégie anti-hameçonnage Office ATP

Les clients EOP bénéficient d’une protection antiphishing de base comme décrit précédemment, mais Office 365 ATP inclut davantage de fonctionnalités et de contrôles pour vous aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, consultez la rubrique [configure ATP anti-phishing Policies in Office 365](configure-atp-anti-phishing-policies.md).

#### <a name="impersonation-settings-in-atp-anti-phishing-policies"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage ATP

Pour plus d’informations sur ces paramètres, consultez la rubrique [emprunt d’identité dans les stratégies anti-hameçonnage ATP](set-up-anti-phishing-policies.md#impersonation-settings-in-atp-anti-phishing-policies). Pour configurer ces paramètres, consultez la rubrique [configure ATP anti-phishing Policies](configure-atp-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|Utilisateurs protégés : **Ajouter des utilisateurs à protéger** <br/><br/> _EnableTargetedUserProtection_ <br/><br/> _TargetedUsersToProtect_|Activé <br/><br/> `$true` <br/><br/> \<list of users\>|Activé <br/><br/> `$true` <br/><br/> \<list of users\>|Dépend de votre organisation, mais nous vous recommandons d’ajouter des utilisateurs dans les rôles clés. En interne, il peut s’agir de votre PDG, directeur financier et autres dirigeants. En externe, il peut s’agir des membres du Conseil ou de votre Conseil d’administration.|
|Domaines protégés : **inclure automatiquement les domaines dont je suis propriétaire** <br/><br/> _EnableOrganizationDomainsProtection_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|Domaines protégés : **inclure des domaines personnalisés** <br/><br/> _EnableTargetedDomainsProtection_ <br/><br/> _TargetedDomainsToProtect_|Activé <br/><br/> `$true` <br/><br/> \<list of domains\>|Activé <br/><br/> `$true` <br/><br/> \<list of domains\>|Dépend de votre organisation, mais nous vous recommandons d’ajouter des domaines avec lesquels vous interagissez fréquemment.|
|Utilisateurs protégés : **si un message électronique est envoyé par un utilisateur représenté** <br/><br/> _TargetedUserProtectionAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Domaines protégés : **si un message électronique est envoyé par un domaine emprunté** <br/><br/> _TargetedDomainProtectionAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Afficher le Conseil pour les utilisateurs empruntés** <br/><br/> _EnableSimilarUsersSafetyTips_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Afficher le Conseil pour les domaines empruntés** <br/><br/> _EnableSimilarDomainsSafetyTips_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Afficher le Conseil pour les caractères inhabituels** <br/><br/> _EnableUnusualCharactersSafetyTips_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’intelligence des boîtes aux lettres ?** <br/><br/> _EnableMailboxIntelligence_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres ?** <br/><br/> _EnableMailboxIntelligenceProtection_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Si le courrier électronique est envoyé par un utilisateur emprunté protégé par la boîte aux lettres** <br/><br/> _MailboxIntelligenceProtectionAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|**Expéditeurs approuvés** <br/><br/> _ExcludedSenders_|Aucun|Aucun|Dépend de votre organisation, mais nous vous recommandons d’ajouter des utilisateurs qui sont identifiés de manière incorrecte comme des hameçons en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|**Domaines approuvés** <br/><br/> _ExcludedDomains_|Aucun|Aucun|Dépend de votre organisation, mais nous vous recommandons d’ajouter des domaines qui sont identifiés de manière incorrecte comme des hameçons en raison de l’emprunt d’identité uniquement et non d’autres filtres.|
|

#### <a name="spoof-settings-in-atp-anti-phishing-policies"></a>Paramètres d’usurpation dans les stratégies anti-hameçonnage ATP

Notez qu’il s’agit des mêmes paramètres que ceux disponibles dans les [paramètres de stratégie anti-courrier indésirable dans EOP](#eop-anti-spam-policy-settings).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Activer la protection contre l’usurpation d’identité** <br/><br/> _EnableAntispoofEnforcement_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer l’expéditeur non authentifié** <br/><br/> _EnableUnauthenticatedSender_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ajoute un point d’interrogation ( ?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, reportez-vous à la rubrique [usurpation des paramètres dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md).|
|**Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine** <br/><br/> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de courrier indésirable des destinataires** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|Cela s’applique aux expéditeurs bloqués dans l' [intelligence d’usurpation d’identité](learn-about-spoof-intelligence.md).|
|

#### <a name="advanced-settings-in-atp-anti-phishing-policies"></a>Paramètres avancés dans les stratégies anti-hameçonnage ATP

Pour plus d’informations sur ce paramètre, consultez la rubrique [seuils d’hameçonnage avancés dans les stratégies anti-hameçonnage ATP](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-atp-anti-phishing-policies). Pour configurer ce paramètre, consultez la rubrique [configure ATP anti-phishing Policies](configure-atp-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Seuils de hameçonnage avancés** <br/><br/> _PhishThresholdLevel_|**2-agressif** <br/><br/> `2`|**3-plus agressif** <br/><br/> `3`||

### <a name="atp-safe-links-policy-settings"></a>Paramètres de stratégie de liens fiables ATP

Pour configurer ces paramètres, reportez-vous à la rubrique [set up Office 365 ATP Safe Links Policies](set-up-atp-safe-links-policies.md).

#### <a name="safe-links-policy-settings-in-the-default-policy-for-all-users"></a>Paramètres de stratégie de liens fiables dans la stratégie par défaut pour tous les utilisateurs

**Remarque**: dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Utiliser les liens fiables dans : applications Office 365** <br/><br/> _EnableSafeLinksForO365Clients_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Utilisez des liens fiables ATP dans les clients Office 365 Desktop et mobile (iOS et Android).|
|**Utiliser les liens fiables dans : compagnons Office Web Access** <br/><br/> _EnableSafeLinksForWebAccessCompanion_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Utiliser les liens fiables ATP dans Office Web Apps.|
|**Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables** <br/><br/> _TrackClicks_|Désactivé <br/><br/> `$true`|Désactivé <br/><br/> `$true`||
|**Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine** <br/><br/> _AllowClickThrough_|Activé <br/><br/> `$false`|Activé <br/><br/> `$false`||
|

#### <a name="safe-links-policy-settings-in-custom-policies-for-specific-users"></a>Paramètres de stratégie de liens fiables dans les stratégies personnalisées pour des utilisateurs spécifiques

**Remarque**: dans PowerShell, vous utilisez les applets de commande [New-Safelinkspolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safelinkspolicy) et [Set-safelinkspolicy permet] ( https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy ] pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Sélectionner l’action pour les URL potentiellement malveillantes dans les messages** <br/><br/> _IsEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Sélectionnez l’action pour les URL inconnues ou potentiellement malveillantes dans Microsoft teams** <br/><br/> _EnableSafeLinksForTeams_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers** <br/><br/> _ScanUrls_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Attendre la fin de l’analyse des URL avant de remettre le message** <br/><br/> _DeliverMessageAfterScan_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation** <br/><br/> _EnableForInternalSenders_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables** <br/><br/> _DoNotTrackUserClicks_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`|
|**Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine** <br/><br/> _DoNotAllowClickThrough_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|

### <a name="atp-safe-attachments-policy-settings"></a>Paramètres de stratégie de pièces jointes approuvées ATP

Pour configurer ces paramètres, reportez-vous à la rubrique [set up Office 365 ATP Safe Attachments Policies](set-up-atp-safe-attachments-policies.md).

#### <a name="safe-attachments-policy-settings-in-the-default-policy-for-all-users"></a>Paramètres de stratégie de pièces jointes fiables dans la stratégie par défaut pour tous les utilisateurs

**Remarque**: dans PowerShell, vous utilisez la cmdlet [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams** <br/><br/> _EnableATPForSPOTeamsODB_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Activer des documents approuvés pour les clients Office**<bt/><br/> _EnableSafeDocs_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||Ce paramètre est disponible uniquement avec les licences de sécurité Microsoft 365 E5 ou Microsoft 365 E5. Pour plus d’informations, consultez la rubrique [documents approuvés dans Office 365 protection avancée contre les menaces](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer en mode protégé même si les documents fiables identifient le fichier comme étant malveillant**<bt/><br/> _AllowSafeDocsOpen_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|

#### <a name="safe-attachments-policy-settings-in-custom-policies-for-specific-users"></a>Paramètres de stratégie de pièces jointes fiables dans les stratégies personnalisées pour des utilisateurs spécifiques

**Remarque**: dans PowerShell, vous utilisez les applets de commande [New-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/new-safeattachmentpolicy) et [Set-safeattachmentpolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---|---|---|---|
|**Pièces jointes fiables réponse aux programmes malveillants inconnus** <br/><br/> _Action_|Bloc <br/><br/> `Block`|Bloc <br/><br/> `Block`||
|**Redirection de la pièce jointe sur la détection** : **activer la redirection** <br/><br/> _Redirect_ <br/><br/> _RedirectAddress_|Sur et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse de messagerie|Sur et spécifiez une adresse de messagerie. <br/><br/> `$true` <br/><br/> une adresse de messagerie|Rediriger les messages vers un administrateur de sécurité pour révision.|
|**Appliquer la sélection ci-dessus si l’analyse anti-programme malveillant pour les pièces jointes expire ou si une erreur se produit.** <br/><br/> _ActionOnError_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|

## <a name="related-topics"></a>Voir aussi

- Vous recherchez les meilleures pratiques avec des **règles de transport Exchange mail Flow/Exchange**? Pour plus d’informations, consultez [cet article](https://docs.microsoft.com/microsoft-365/security/office-365-security/best-practices-for-configuring-eop) .

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (courriers électroniques marqués comme incorrects) et des faux négatifs (courrier incorrect autorisé) à Microsoft pour analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour obtenir des informations sur **la configuration de votre** [service EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-your-eop-service), ainsi que sur la **configuration** de la [Protection avancée contre les menaces d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp). (N’oubliez pas de consulter les instructions utiles dans «[protéger contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)».)

- Les **lignes de base de sécurité pour Windows** sont disponibles [ici](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options d’objet de stratégie de groupe/local et la sécurité basée sur Intune, [ici](https://docs.microsoft.com/intune/protect/security-baselines). Enfin, il est possible de trouver une comparaison entre Microsoft Defender Advanced Threat Protection (ATP) et les bases de sécurité Windows [Intune.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines)
