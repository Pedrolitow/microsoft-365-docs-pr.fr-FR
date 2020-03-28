---
title: Recommandations de Microsoft pour les paramètres de sécurité ATP et Office 365, recommandations, Sender Policy Framework, la création de rapports de messages basés sur un domaine, la conformité, la DomainKeys Identified identifiée, les étapes, son fonctionnement, les lignes de base de sécurité, les configurations de base pour EOP, planifications pour la protection avancée contre les menaces, configuration ATP, configuration EOP, configuration de l’ATP, configuration d’EOP, configuration de la sécurité
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 12/12/2019
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
ms.openlocfilehash: 9ddf704f767dfa5ff5c93888e51b91b2079a6c43
ms.sourcegitcommit: d00efe6010185559e742304b55fa2d07127268fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2020
ms.locfileid: "43032851"
---
# <a name="recommended-settings-for-eop-and-office-365-atp-security"></a>Paramètres recommandés pour la sécurité ATP d’Office 365

**Exchange Online Protection (EoP)** est le cœur de la sécurité des abonnements Office 365 et empêche les messages électroniques malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes tous les jours, des protections améliorées sont souvent requises. **Office 365 Advanced Threat Protection (ATP)** Le plan ATP 1 ou le plan ATP 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs plus de couches de sécurité, de contrôle et d’enquête.

Bien que nous permettons aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Office 365 ATP qui nous sont recommandés : **standard** et **strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de configurations de filtrage des messages empêchent le courrier indésirable d’atteindre la boîte de réception de vos employés dans la plupart des cas.

> [!IMPORTANT]
> La règle de courrier indésirable doit être activée sur une boîte aux lettres pour que le filtrage fonctionne correctement. Il est activé par défaut, mais vous devez le vérifier si le filtrage ne semble pas fonctionner. Pour plus d’informations, voir [Configurer les paramètres du courrier indésirable sur les boîtes aux lettres Exchange Online dans Office 365](configure-junk-email-settings-on-exo-mailboxes.md).

Cette rubrique décrit ces paramètres recommandés par Microsoft pour vous aider à protéger vos utilisateurs Office 365.

> [!TIP]
> Il existe un nouveau module PowerShell que vous pouvez télécharger appelé Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA) qui permet de déterminer certains de ces paramètres. Lorsqu’il est exécuté en tant qu’administrateur dans votre client, Get-ORCAReport permet de générer une évaluation du blocage du courrier indésirable, de l’anti-hameçonnage et d’autres paramètres d’hygiène des messages. Vous pouvez télécharger ce module à https://www.powershellgallery.com/packages/ORCA/l’adresse.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Blocage du courrier indésirable, des programmes malveillants et de la protection anti-hameçonnage dans EOP

Le blocage du courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités d’EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons d’utiliser les configurations suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de la stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies de blocage du courrier indésirable, consultez la rubrique [configure anti-spam Policies in Office 365](configure-your-spam-filter-policies.md).

|||||
|---|---|---|---|
|**Nom de la fonctionnalité de sécurité**|**Standard**|**Empêcher**|**Comment**|
|Action de détection du **courrier indésirable** <br/><br/> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier indésirable à fiabilité élevée** <br/><br/> _HighConfidenceSpamAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage** <br/><br/> _PhishSpamAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier d’hameçonnage à haut niveau de fiabilité** <br/><br/> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <br/><br/> `Quarantine`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Action de détection de **courrier en nombre** <br/><br/> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br/><br/> `MoveToJmf`|**Mettre en quarantaine le message** <br/><br/> `Quarantine`||
|Seuil de courrier électronique en masse <br/><br/> _BulkThreshold_|6 |4 |La valeur par défaut est actuellement 7, mais nous vous recommandons de la remplacer par 6. Pour plus d’informations, reportez-vous à [Bulk Complaint Level (BCL) in Office 365](bulk-complaint-level-values.md).|
|Période de rétention de quarantaine <br/><br/> _QuarantineRetentionPeriod_|30 jours|30 jours||
|**Conseils de sécurité** <br/><br/> _InlineSafetyTipsEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|Expéditeurs autorisés <br/><br/> _AllowedSenders_|Aucune|Aucune||
|Domaines d’expéditeur autorisés <br/><br/> _AllowedSenderDomains_|Aucune|Aucune|L’ajout de domaines dont vous êtes propriétaire (également appelés _domaines acceptés_) à la liste des expéditeurs autorisés n’est pas obligatoire. En fait, il est considéré comme un risque élevé, car il permet aux acteurs incorrects de vous envoyer des messages qui seraient autrement filtrés. Utilisez l’Assistant d' [usurpation d’identité](learn-about-spoof-intelligence.md) dans le centre de sécurité & conformité de la page **paramètres anti-courrier indésirable** pour examiner tous les expéditeurs qui usurpent l’identité des domaines qui font partie de votre organisation ou qui usurpent des domaines externes.|
|Expéditeurs bloqués <br/><br/> _BlockedSenders_|Aucune|Aucune||
|Domaines des expéditeurs bloqués <br/><br/> _BlockedSenderDomains_|Aucune|Aucune||
|**Activer les notifications de courrier indésirable à l’utilisateur final** <br/><br/> _EnableEndUserSpamNotifications_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Envoyer des notifications de courrier indésirable à l’utilisateur final tous les (jours)** <br/><br/> _EndUserSpamNotificationFrequency_|3 jours|3 jours||
|**Blocage du courrier indésirable** <br/><br/> _SpamZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Hameçon ZAP** <br/><br/> _PhishZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|_MarkAsSpamBulkMail_|Activé|Activé|Ce paramètre est disponible uniquement dans PowerShell.|
|

Il existe plusieurs autres paramètres de filtre de courrier indésirable (ASF) dans les stratégies de blocage du courrier indésirable qui sont en cours de désapprobation. Pour plus d’informations sur les chronologies de l’amortissement de ces fonctionnalités, reportez-vous à cette rubrique.

Nous vous **recommandons de désactiver ces paramètres ASF** pour les niveaux **standard** et **strict** . Pour plus d’informations sur les paramètres ASF, voir [paramètres de filtre de courrier indésirable avancés (ASF) dans Office 365](advanced-spam-filtering-asf-options.md).

|||
|----|---|
|**Nom de la fonctionnalité de sécurité**|**Comments**|
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

||||
|---|---|---|---|
|**Nom de la fonctionnalité de sécurité**|**Standard**|**Empêcher**|**Comment**|
|**Nombre maximal de destinataires par utilisateur : limite horaire externe** <br/><br/> _RecipientLimitExternalPerHour_|500|400||
|**Nombre maximal de destinataires par utilisateur : limite horaire interne** <br/><br/> _RecipientLimitInternalPerHour_|1000|800||
|**Nombre maximal de destinataires par utilisateur : limite quotidienne** <br/><br/> _RecipientLimitPerDay_|1000|800||
|**Action lorsqu’un utilisateur dépasse les limites** <br/><br/> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages** <br/><br/> `BlockUser`||
|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies de protection contre les programmes malveillants, consultez la rubrique [configure anti-malware Policies in Office 365](configure-anti-malware-policies.md).

|||||
|---|---|---|---|
|**Nom de la fonctionnalité de sécurité**|**Standard**|**Empêcher**|**Comment**|
|**Voulez-vous avertir les destinataires si leurs messages sont mis en quarantaine ?** <br/><br/> _Action_|Non <br/><br/> _DeleteMessage_|Non <br/><br/> _DeleteMessage_|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|**Filtre de types de pièces jointes courantes** <br/><br/> _EnableFileFilter_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes exécutables en fonction du type de fichier, quel que soit le contenu des pièces jointes.|
|**Purge automatique contre les programmes malveillants à zéro heure** <br/><br/> _ZapEnabled_|Activé <br/><br/> `$true`|Activé <br/><br/> `$true`||
|**Informer les expéditeurs internes** du message non remis <br/><br/> _EnableInternalSenderNotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|**Informer les expéditeurs externes** du message non remis <br/><br/> _Paramètre enableexternalsendernotifications_|Désactivé <br/><br/> `$false`|Désactivé <br/><br/> `$false`||
|

### <a name="eop-anti-phishing-policy-settings"></a>Paramètres de la stratégie anti-hameçonnage EOP

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Activer la protection contre l’usurpation d’identité|Activé|Activé||
|Activer l’expéditeur non authentifié (marquage)|Activé|Activé||
|Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine|Déplacer le message vers les dossiers de courrier indésirable des destinataires|Mettre en quarantaine le message||

## <a name="office-365-advanced-threat-protection-security"></a>Sécurité avancée contre les menaces Office 365

Des avantages supplémentaires en matière de sécurité sont inclus dans un abonnement Office 365 Advanced Threat Protection (ATP). Pour obtenir les dernières informations et informations, vous pouvez consulter les nouveautés [d’Office 365 ATP](whats-new-in-office-365-atp.md).

La protection avancée contre les menaces Office 365 inclut les stratégies de pièces jointes fiables et de liens fiables pour empêcher la remise des messages contenant des pièces jointes potentiellement malveillantes et empêcher les utilisateurs de cliquer sur les URL potentiellement dangereuses.

> [!IMPORTANT]
> La protection avancée contre le hameçonnage est l’un des avantages d’un abonnement Office 365 ATP. Bien qu’elle soit activée par défaut, vous ***devez*** configurer au moins une stratégie anti-hameçonnage avant de pouvoir commencer à filtrer les messages. Oublier de configurer des stratégies anti-hameçonnage pourrait exposer les utilisateurs à des courriers électroniques risqués. Veillez à configurer vos stratégies anti-hameçonnage après avoir ajouté un abonnement Office 365 ATP.

Si vous avez ajouté un abonnement Office 365 ATP à votre EOP, définissez les configurations suivantes.

### <a name="office-atp-anti-phishing-policy-settings"></a>Paramètres de la stratégie anti-hameçonnage Office ATP

Les clients EOP bénéficient d’une protection antiphishing de base comme décrit précédemment, mais Office 365 ATP inclut davantage de fonctionnalités et de contrôles pour vous aider à prévenir, détecter et corriger les attaques.

|Nom de la fonctionnalité de sécurité de l’emprunt d’identité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|(Modifier la stratégie d’emprunt d’identité) Ajouter des utilisateurs à protéger|Activé|Activé|Dépend de votre organisation, mais nous vous recommandons d’ajouter des utilisateurs dans les rôles clés. En interne, il peut s’agir de votre PDG, directeur financier et autres dirigeants. En externe, il peut s’agir des membres du Conseil ou de votre Conseil d’administration.|
|(Modifier la stratégie d’emprunt d’identité) Inclure automatiquement les domaines dont je suis propriétaire|Activé|Activé||
|(Modifier la stratégie d’emprunt d’identité) Inclure les domaines personnalisés|Activé|Activé|Dépend de votre organisation, mais nous vous recommandons d’ajouter des domaines que vous interagissez avec la plupart des personnes dont vous n’êtes pas propriétaire.|
|Si le courrier électronique est envoyé par un utilisateur représenté que vous avez spécifié|Mettre en quarantaine le message|Mettre en quarantaine le message||
|Si le courrier électronique est envoyé par un domaine emprunté que vous avez spécifié|Mettre en quarantaine le message|Mettre en quarantaine le message||
|Afficher le Conseil pour les utilisateurs empruntés|Activé|Activé||
|Afficher le Conseil pour les domaines empruntés|Activé|Activé||
|Afficher le Conseil pour les caractères inhabituels|Activé|Activé||
|Activer l’intelligence des boîtes aux lettres|Activé|Activé||
|Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres|Activé|Activé||
|Si le courrier électronique est envoyé par un utilisateur emprunté protégé par la boîte aux lettres|Déplacer le message vers les dossiers de courrier indésirable des destinataires|Mettre en quarantaine le message||
|(Modifier la stratégie d’emprunt d’identité) Ajouter des expéditeurs et des domaines approuvés|Aucune|Aucune|Dépend de votre organisation, mais nous vous recommandons d’ajouter des utilisateurs ou des domaines qui ne sont pas marqués correctement comme des hameçons en raison de l’emprunt d’identité uniquement et non d’autres filtres.|

|Nom de la fonctionnalité de sécurité usurpée|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Activer la protection contre l’usurpation d’identité|Activé|Activé||
|Activer l’expéditeur non authentifié (marquage)|Activé|Activé||
|Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine|Déplacer le message vers les dossiers de courrier indésirable des destinataires|Mettre en quarantaine le message||
|EnableSuspiciousSafetyTip|False|True|Ce paramètre est disponible uniquement dans PowerShell|
|TreatSoftPassAsAuthenticated|Vrai|False|Ce paramètre est disponible uniquement dans PowerShell|


|Nom de la fonctionnalité de sécurité des paramètres avancés|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Seuils de hameçonnage avancés|2-agressif|3-plus agressif||

### <a name="safe-links-settings"></a>Paramètres de liens fiables

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Utiliser des liens fiables ATP dans les applications Office 365, Office pour iOS et Android|Activé|Activé|Cela relève des stratégies de liens fiables ATP qui s’appliquent à l’ensemble de l’Organisation|
Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables|Désactivé|Désactivé|Il s’agit des stratégies qui s’appliquent à l’ensemble de l’organisation et à toutes les stratégies qui s’appliquent à des destinataires spécifiques.|
|Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine|Activé|Activé|Il s’agit des stratégies qui s’appliquent à l’ensemble de l’organisation et des stratégies qui s’appliquent à des destinataires spécifiques.|
|Action pour les URL potentiellement malveillantes dans les messages|Activé|Activé||
|Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers|Activé|Activé||
|Attendre la fin de l’analyse des URL avant de remettre le message|Activé|Activé||
|Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation|Activé|Activé||

### <a name="safe-attachments"></a>Pièces jointes fiables

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Activer PACM pour SharePoint, OneDrive et Microsoft Teams.|Activé|Activé||
|Pièces jointes approuvées ATP réponse aux programmes malveillants inconnus|Bloc|Bloc||
|Redirection de la pièce jointe sur la détection|Activé|Activé|Rediriger vers l’adresse de messagerie d’un administrateur de sécurité qui sait comment déterminer si la pièce jointe est un programme malveillant ou non|
|Réponse aux pièces jointes approuvées ATP si l’analyse contre les pièces jointes expire ou si une erreur se produit|Activé|Activé||

## <a name="related-topics"></a>Sujets associés

- Vous recherchez les meilleures pratiques avec des **règles de transport Exchange mail Flow/Exchange**? Pour plus d’informations, consultez [cet article](https://docs.microsoft.com/microsoft-365/security/office-365-security/best-practices-for-configuring-eop) .

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (courriers électroniques marqués comme incorrects) et des faux négatifs (courrier incorrect autorisé) à Microsoft pour analyse. Pour plus d’informations, consultez la rubrique [signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour obtenir des informations sur **la configuration de votre** [service EOP](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-your-eop-service), ainsi que sur la **configuration** de la [Protection avancée contre les menaces d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp). (N’oubliez pas de consulter les instructions utiles dans «[protéger contre les menaces dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)».)

- Les **lignes de base de sécurité pour Windows** sont disponibles [ici](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) pour les options d’objet de stratégie de groupe/local et la sécurité basée sur Intune, [ici](https://docs.microsoft.com/intune/protect/security-baselines). Enfin, il est possible de trouver une comparaison entre Microsoft Defender Advanced Threat Protection (ATP) et les bases de sécurité Windows [Intune.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines)
