---
title: Recommandations Microsoft pour les paramètres de sécurité EOP et Defender pour Office 365
keywords: Office 365 recommandations de sécurité, Infrastructure de stratégie d’expéditeur, rapports et conformité des messages basés sur le domaine, courrier identifié DomainKeys, étapes, fonctionnement, bases de référence de sécurité, lignes de base pour EOP, lignes de base pour Defender pour Office 365, configuration Defender pour Office 365, configuration d’EOP, configuration Defender pour Office 365, configurer EOP, configuration de la sécurité
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
- m365-security
- m365initiative-defender-office365
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Defender pour Office 365 ? Quelles sont les recommandations actuelles en matière de protection standard ? Que faut-il utiliser si vous voulez être plus strict ? Et quels extras obtenez-vous si vous utilisez également Defender pour Office 365?
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: ed580495feda8f913afa2541563d60e029b7c2c9
ms.sourcegitcommit: 04e517c7e00323b5c33d8ea937115725cf2cfd4d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2022
ms.locfileid: "68565799"
---
# <a name="recommended-settings-for-eop-and-microsoft-defender-for-office-365-security"></a>Paramètres recommandés pour EOP et pour la sécurité Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Exchange Online Protection (EOP)** est le cœur de la sécurité pour les abonnements Microsoft 365 et permet d’empêcher les e-mails malveillants d’atteindre les boîtes de réception de vos employés. Mais avec de nouvelles attaques plus sophistiquées qui apparaissent chaque jour, des protections améliorées sont souvent nécessaires. **Microsoft Defender pour Office 365** Plan 1 ou Plan 2 contiennent des fonctionnalités supplémentaires qui offrent aux administrateurs plus de couches de sécurité, de contrôle et d’investigation.

Bien que nous donnions aux administrateurs de sécurité la possibilité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Microsoft Defender pour Office 365 que nous recommandons : **Standard** et **Strict**. Bien que les environnements et les besoins des clients soient différents, ces niveaux de filtrage permettent d’empêcher les messages indésirables d’atteindre la boîte de réception de vos employés dans la plupart des situations.

Pour appliquer automatiquement les paramètres Standard ou Strict aux utilisateurs, consultez [stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

Cet article décrit les paramètres par défaut, ainsi que les paramètres Standard et Strict recommandés pour protéger vos utilisateurs. Les tables contiennent les paramètres dans le portail Microsoft 365 Defender et PowerShell (Exchange Online PowerShell ou autonome Exchange Online Protection PowerShell pour les organisations sans boîtes aux lettres Exchange Online).

> [!NOTE]
> Le Office 365 module ORCA (Advanced Threat Protection Recommended Configuration Analyzer) pour PowerShell peut vous aider (administrateurs) à trouver les valeurs actuelles de ces paramètres. Plus précisément, l’applet de commande **Get-ORCAReport** génère une évaluation des paramètres anti-courrier indésirable, anti-hameçonnage et autres paramètres d’hygiène des messages. Vous pouvez télécharger le module ORCA à l’adresse <https://www.powershellgallery.com/packages/ORCA/>.
>
> Dans les organisations Microsoft 365, nous vous recommandons de laisser le filtre Junk Email dans Outlook défini sur **Aucun filtrage automatique** pour éviter les conflits inutiles (positifs et négatifs) avec les verdicts de filtrage du courrier indésirable d’EOP. Si vous souhaitez en savoir plus, consultez les articles suivants :
>
> - [Configurer les paramètres du courrier indésirable dans les boîtes aux lettres Exchange Online](configure-junk-email-settings-on-exo-mailboxes.md)
> - [À propos des paramètres de courrier indésirable dans Outlook](configure-junk-email-settings-on-exo-mailboxes.md#about-junk-email-settings-in-outlook)
> - [Modifier le niveau de protection dans le filtre de Email indésirable](https://support.microsoft.com/en-us/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b)
> - [Créer des listes d’expéditeurs fiables dans EOP](create-safe-sender-lists-in-office-365.md)
> - [Créer des listes d’expéditeurs bloqués dans EOP](create-block-sender-lists-in-office-365.md)

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Protection anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage dans EOP

Les fonctionnalités anti-courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons les configurations Standard ou Strict suivantes.

### <a name="eop-anti-spam-policy-settings"></a>Paramètres de stratégie anti-courrier indésirable EOP

Pour créer et configurer des stratégies anti-courrier indésirable, consultez Configurer les stratégies [anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil d’e-mail en bloc & propriétés de courrier indésirable**|||||
|**Seuil d’e-mail en bloc** <br><br> _BulkThreshold_|7 |6|5|Pour plus d’informations, consultez le [niveau de réclamation en bloc (BCL) dans EOP](bulk-complaint-level-values.md).|
|_MarkAsSpamBulkMail_|`On`|`On`|`On`|Ce paramètre est disponible uniquement dans PowerShell.|
|**Augmenter les paramètres de score de courrier indésirable**|Désactivé|Désactivé|Désactivé|Tous ces paramètres font partie de l’Advanced Spam Filter (ASF). Pour plus d’informations, consultez les [paramètres ASF dans la section stratégies anti-courrier indésirable](#asf-settings-in-anti-spam-policies) de cet article.|
|**Marquer comme paramètres de courrier indésirable**|Désactivé|Désactivé|Désactivé|La plupart de ces paramètres font partie d’ASF. Pour plus d’informations, consultez les [paramètres ASF dans la section stratégies anti-courrier indésirable](#asf-settings-in-anti-spam-policies) de cet article.|
|**Contient des langues spécifiques** <br><br> _EnableLanguageBlockList_ <br><br> _LanguageBlockList_|**Désactivé** <br><br> `$false` <br><br> Vide|**Désactivé** <br><br> `$false` <br><br> Vide|**Désactivé** <br><br> `$false` <br><br> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. Vous pouvez bloquer les messages dans des langues spécifiques en fonction des besoins de votre entreprise.|
|**De ces pays** <br><br> _EnableRegionBlockList_ <br><br> _RegionBlockList_|**Désactivé** <br><br> `$false` <br><br> Vide|**Désactivé** <br><br> `$false` <br><br> Vide|**Désactivé** <br><br> `$false` <br><br> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. Vous pouvez bloquer les messages de pays spécifiques en fonction des besoins de votre entreprise.|
|**Mode test** (_TestModeAction_)|**Aucune**|**Aucune**|**Aucune**|Ce paramètre fait partie d’ASF. Pour plus d’informations, consultez les [paramètres ASF dans la section stratégies anti-courrier indésirable](#asf-settings-in-anti-spam-policies) de cet article.|
|**Actions**||||Partout où vous sélectionnez **Le message de mise en quarantaine**, une zone **de stratégie de mise en quarantaine Sélection** est disponible. Les stratégies de quarantaine définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. <br><br> Les stratégies de sécurité prédéfinies Standard et Strict utilisent les stratégies de quarantaine par défaut (AdminOnlyAccessPolicy ou DefaultFullAccessPolicy sans notifications de quarantaine) comme décrit dans le tableau [ci-après](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br><br> Lorsque vous créez une stratégie anti-courrier indésirable, une valeur vide signifie que la stratégie de quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages qui ont été mis en quarantaine par ce verdict particulier (AdminOnlyAccessPolicy sans notification de mise en quarantaine pour le **hameçonnage à haut niveau de confiance**; DefaultFullAccessPolicy sans notifications de mise en quarantaine pour tout le reste). <br><br> Les administrateurs peuvent créer et sélectionner des stratégies de quarantaine personnalisées qui définissent des fonctionnalités plus restrictives ou moins restrictives pour les utilisateurs dans les stratégies anti-courrier indésirable par défaut ou personnalisées. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|Action de détection **du courrier indésirable** <br><br> _SpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br><br> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|**Action de détection du courrier indésirable à haut niveau de confiance** <br><br> _HighConfidenceSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|Action de détection **d’hameçonnage** <br><br> _PhishSpamAction_|**Déplacer le message vers le dossier Junk Email**<sup>\*</sup> <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`|<sup>\*</sup>La valeur par défaut est **Déplacer le message vers le dossier Junk Email** dans la stratégie anti-courrier indésirable par défaut et dans les nouvelles stratégies anti-courrier indésirable que vous créez dans PowerShell. La valeur par défaut est **le message de mise en quarantaine** dans les nouvelles stratégies anti-courrier indésirable que vous créez dans le portail Microsoft 365 Defender.|
|**Action de détection de hameçonnage à haut niveau de confiance** <br><br> _HighConfidencePhishAction_|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|Action de détection **en bloc** <br><br> _BulkSpamAction_|**Déplacer le message dans le dossier Courrier indésirable** <br><br> `MoveToJmf`|**Déplacer le message dans le dossier Courrier indésirable** <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|**Conserver le courrier indésirable en quarantaine pendant ce nombre de jours** <br><br> _QuarantineRetentionPeriod_|15 jours|30 jours|30 jours|  <br><br> Cette valeur affecte également les messages mis en quarantaine par des stratégies anti-hameçonnage. Pour plus d’informations, consultez [messages électroniques mis en quarantaine dans EOP](quarantine-email-messages.md).|
|**Activer les conseils de sécurité relatifs au courrier indésirable** <br><br> _InlineSafetyTipsEnabled_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|Activer le vidage automatique de zéro heure (ZAP) pour les messages de hameçonnage <br><br> _PhishZapEnabled_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|Activer ZAP pour les messages indésirables <br><br> _SpamZapEnabled_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Autoriser & liste de blocs**|||||
|Expéditeurs autorisés <br><br> _AllowedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur autorisés <br><br> _AllowedSenderDomains_|Aucun|Aucun|Aucun|L’ajout de domaines à la liste des expéditeurs autorisés est une très mauvaise idée. Les attaquants seraient en mesure de vous envoyer des e-mails qui seraient autrement filtrés. <br><br> Utilisez [l’insight sur l’usurpation d’identité](learn-about-spoof-intelligence.md) et la [liste d’autorisation/de blocage du locataire](manage-tenant-allow-block-list.md) pour examiner tous les expéditeurs qui usurpent les adresses e-mail de l’expéditeur dans les domaines de messagerie de votre organisation ou usurpent les adresses e-mail de l’expéditeur dans des domaines externes.|
|Expéditeurs bloqués <br><br> _BlockedSenders_|Aucun|Aucun|Aucun||
|Domaines d’expéditeur bloqués <br><br> _BlockedSenderDomains_|Aucun|Aucun|Aucun||

#### <a name="asf-settings-in-anti-spam-policies"></a>Paramètres ASF dans les stratégies anti-courrier indésirable

Pour plus d’informations sur les paramètres du filtre anti-courrier indésirable avancé (ASF) dans les stratégies anti-courrier indésirable, consultez [les paramètres du filtre anti-courrier indésirable avancé (ASF) dans EOP](advanced-spam-filtering-asf-options.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Recommandé<br/>Standard|Recommandé<br/>Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Liens d'image vers des sites distants** <br><br> _IncreaseScoreWithImageLinks_|Désactivé|Désactivé|Désactivé||
|**Adresse IP numérique dans l'URL** <br><br> _IncreaseScoreWithNumericIps_|Désactivé|Désactivé|Désactivé||
|**Redirection de l'URL vers un autre port** <br><br> _IncreaseScoreWithRedirectToOtherPort_|Désactivé|Désactivé|Désactivé||
|**Liens vers des sites web .biz ou .info** <br><br> _IncreaseScoreWithBizOrInfoUrls_|Désactivé|Désactivé|Désactivé||
|**Messages vides** <br><br> _MarkAsSpamEmptyMessages_|Désactivé|Désactivé|Désactivé||
|**Balises Embed dans le code HTML** <br><br> _MarkAsSpamEmbedTagsInHtml_|Désactivé|Désactivé|Désactivé||
|**JavaScript ou VBScript dans le code HTML** <br><br> _MarkAsSpamJavaScriptInHtml_|Désactivé|Désactivé|Désactivé||
|**Balises Form dans le code HTML** <br><br> _MarkAsSpamFormTagsInHtml_|Désactivé|Désactivé|Désactivé||
|**Balises frame ou iframe en HTML** <br><br> _MarkAsSpamFramesInHtml_|Désactivé|Désactivé|Désactivé||
|**Bogues web dans le code HTML** <br><br> _MarkAsSpamWebBugsInHtml_|Désactivé|Désactivé|Désactivé||
|**Balises Object dans le code HTML** <br><br> _MarkAsSpamObjectTagsInHtml_|Désactivé|Désactivé|Désactivé||
|**Mots sensibles** <br><br> _MarkAsSpamSensitiveWordList_|Désactivé|Désactivé|Désactivé||
|**Enregistrement SPF : échec sévère** <br><br> _MarkAsSpamSpfRecordHardFail_|Désactivé|Désactivé|Désactivé||
|**Échec du filtrage de l’ID de l’expéditeur** <br><br> _MarkAsSpamFromAddressAuthFail_|Désactivé|Désactivé|Désactivé||
|**Rétrodiffusion** <br><br> _MarkAsSpamNdrBackscatter_|Désactivé|Désactivé|Désactivé||
|**Mode test** <br><br> _TestModeAction_)|Aucun|Aucun|Aucun|Pour les paramètres ASF qui prennent en charge **test** en tant qu’action, vous pouvez configurer l’action en mode test sur **None**, **Ajouter le texte par défaut de l’en-tête X** ou **Envoyer un message CCI** (`None`, `AddXHeader`ou `BccMessage`). Pour plus d’informations, consultez [Activer, désactiver ou tester les paramètres ASF](advanced-spam-filtering-asf-options.md#enable-disable-or-test-asf-settings).|

#### <a name="eop-outbound-spam-policy-settings"></a>Paramètres de stratégie de courrier indésirable sortant EOP

Pour créer et configurer des stratégies de courrier indésirable sortant, consultez [Configurer le filtrage du courrier indésirable sortant dans EOP](configure-the-outbound-spam-policy.md).

Pour plus d’informations sur les limites d’envoi par défaut dans le service, consultez [Limites d’envoi](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-1).

> [!NOTE]
> Les stratégies de courrier indésirable sortant ne font pas partie des stratégies de sécurité prédéfinies Standard ou Strict. Les valeurs **Standard** et **Strict** indiquent nos valeurs **recommandées** dans la stratégie de courrier indésirable sortant par défaut ou dans les stratégies de courrier indésirable sortant personnalisées que vous créez.

|Nom de la fonctionnalité de sécurité|Par défaut|Recommandé<br/>Standard|Recommandé<br/>Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Définir une limite de messages externes** <br><br> _RecipientLimitExternalPerHour_|0|500|400|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite de messages internes** <br><br> _RecipientLimitInternalPerHour_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Définir une limite quotidienne de messages** <br><br> _RecipientLimitPerDay_|0|1000|800|La valeur par défaut 0 signifie utiliser les valeurs par défaut du service.|
|**Restriction imposée aux utilisateurs qui atteignent la limite de messages** <br><br> _ActionWhenThresholdReached_|**Empêcher l’utilisateur d’envoyer des messages électroniques jusqu’au lendemain** <br><br> `BlockUserForToday`|**Empêcher l’utilisateur d’envoyer des messages** <br><br> `BlockUser`|**Empêcher l’utilisateur d’envoyer des messages** <br><br> `BlockUser`||
|**Règles de transfert automatique** <br><br> _AutoForwardingMode_|**Automatique - Contrôlé par le système** <br><br> `Automatic`|**Automatique - Contrôlé par le système** <br><br> `Automatic`|**Automatique - Contrôlé par le système** <br><br> `Automatic`|
|**Envoyer une copie des messages sortants qui dépassent ces limites à ces utilisateurs et groupes** <br><br> _BccSuspiciousOutboundMail_ <br><br> _BccSuspiciousOutboundAdditionalRecipients_|Non sélectionnée <br><br> `$false` <br><br> Vide|Non sélectionnée <br><br> `$false` <br><br> Vide|Non sélectionnée <br><br> `$false` <br><br> Vide|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br><br> Ce paramètre fonctionne uniquement dans la stratégie de courrier indésirable sortant par défaut. Cela ne fonctionne pas dans les stratégies de courrier indésirable sortant personnalisées que vous créez.|
|**Notifier ces utilisateurs et groupes si un expéditeur est bloqué en raison de l’envoi de courrier indésirable sortant** <br><br> _NotifyOutboundSpam_ <br><br> _NotifyOutboundSpamRecipients_|Non sélectionnée <br><br> `$false` <br><br> Vide|Non sélectionnée <br><br> `$false` <br><br> Vide|Non sélectionnée <br><br> `$false` <br><br> Vide|La [stratégie d’alerte](../../compliance/alert-policies.md) par défaut nommée **Utilisateur limité à l’envoi d’e-mails** envoie déjà des notifications par e-mail aux membres du groupe **TenantAdmins** (**administrateurs généraux**) lorsque les utilisateurs sont bloqués en raison du dépassement des limites de la stratégie. **Nous vous recommandons vivement d’utiliser la stratégie d’alerte plutôt que ce paramètre dans la stratégie de courrier indésirable sortant pour informer les administrateurs et d’autres utilisateurs**. Pour obtenir des instructions, consultez [Vérifier les paramètres d’alerte pour les utilisateurs restreints](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users).|

### <a name="eop-anti-malware-policy-settings"></a>Paramètres de stratégie anti-programme malveillant EOP

Pour créer et configurer des stratégies anti-programme malveillant, consultez Configurer des stratégies [anti-programme malveillant dans EOP](configure-anti-malware-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Paramètres de protection**|||||
|**Activer le filtre des pièces jointes courantes** <br><br> _EnableFileFilter_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Ce paramètre met en quarantaine les messages qui contiennent des pièces jointes en fonction du type de fichier, quel que soit le contenu de la pièce jointe. Pour obtenir la liste des types de fichiers, consultez [stratégies anti-programme malveillant](anti-malware-protection.md#anti-malware-policies).|
|Notifications de filtre de pièces jointes courantes (**lorsque ces types de fichiers sont trouvés**) <br><br> _FileTypeAction_|**Rejeter les messages avec un reçu de non-remise (NDR)** <br><br> `Reject`|**Rejeter les messages avec un reçu de non-remise (NDR)** <br><br> `Reject`|**Rejeter les messages avec un reçu de non-remise (NDR)** <br><br> `Reject`||
|**Activer le vidage automatique de zéro heure pour les programmes malveillants** <br><br> _ZapEnabled_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Stratégie de quarantaine**|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|Lorsque vous créez une stratégie anti-programme malveillant, une valeur vide signifie que la stratégie de quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages qui ont été mis en quarantaine en tant que programmes malveillants (AdminOnlyAccessPolicy sans notifications de quarantaine). <br><br> Les stratégies de sécurité prédéfinies Standard et Strict utilisent la stratégie de quarantaine par défaut (AdminOnlyAccessPolicy sans notifications de quarantaine) comme décrit dans le tableau [ci-après](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br><br> Les administrateurs peuvent créer et sélectionner des stratégies de quarantaine personnalisées qui définissent davantage de fonctionnalités pour les utilisateurs dans les stratégies anti-programmes malveillants par défaut ou personnalisées. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**notifications Administration**|||||
|**Informer un administrateur des messages non remis provenant d’expéditeurs internes** <br><br> _EnableInternalSenderAdminNotifications_ <br><br> _InternalSenderAdminAddress_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre.|
|**Informer un administrateur des messages non remis provenant d’expéditeurs externes** <br><br> _EnableExternalSenderAdminNotifications_ <br><br> _ExternalSenderAdminAddress_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre.|
|**Personnaliser les notifications**||||Nous n’avons aucune recommandation spécifique pour ces paramètres.|
|**Utiliser un texte de notification personnalisé** <br><br> _CustomNotifications_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`||
|**À partir du nom** <br><br> _CustomFromName_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||
|**Adresse de provenance** <br><br> _CustomFromAddress_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||
|**Personnaliser les notifications pour les messages des expéditeurs internes**||||Ces paramètres sont utilisés uniquement si **l’option Informer un administrateur des messages non remis provenant d’expéditeurs internes** est sélectionnée.|
|**Sujet** <br><br> _CustomInternalSubject_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||
|**Message** <br><br> _CustomInternalBody_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||
|**Personnaliser les notifications pour les messages des expéditeurs externes**||||Ces paramètres sont utilisés uniquement si **l’option Informer un administrateur des messages non remis provenant d’expéditeurs externes** est sélectionnée.|
|**Sujet** <br><br> _CustomExternalSubject_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||
|**Message** <br><br> _CustomExternalBody_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`||

### <a name="eop-anti-phishing-policy-settings"></a>Paramètres de stratégie anti-hameçonnage EOP

Pour plus d’informations sur ces paramètres, consultez [Paramètres d’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings). Pour configurer ces paramètres, consultez Configurer des stratégies [anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

Les paramètres d’usurpation d’identité sont interdépendants, mais le paramètre **Afficher le premier conseil de sécurité du contact** n’a aucune dépendance vis-à-vis des paramètres d’usurpation d’identité.

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil d’hameçonnage & protection**|||||
|**Activer l’intelligence par usurpation d’identité** <br><br> _EnableSpoofIntelligence_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Actions**|||||
|**Si le message est détecté comme usurpation d’identité** <br><br> _AuthenticationFailAction_|**Déplacer le message vers les dossiers de Email indésirables des destinataires** <br><br> `MoveToJmf`|**Déplacer le message vers les dossiers de Email indésirables des destinataires** <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`|Ce paramètre s’applique aux expéditeurs usurpés qui ont été automatiquement bloqués, comme indiqué dans [l’insight d’intelligence de l’usurpation](learn-about-spoof-intelligence.md) d’identité, ou bloqués manuellement dans la [liste d’autorisation/de blocage du locataire](manage-tenant-allow-block-list.md). <br><br> Si vous sélectionnez **Mettre en quarantaine le message**, une zone **Appliquer la stratégie de mise en quarantaine** est disponible pour sélectionner la stratégie de quarantaine qui définit ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine en tant qu’usurpation d’identité. Lorsque vous créez une stratégie anti-hameçonnage, une valeur vide signifie que la stratégie de quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages qui ont été mis en quarantaine en tant qu’usurpation d’identité (DefaultFullAccessPolicy sans notifications de quarantaine). <br><br> Les stratégies de sécurité prédéfinies Standard et Strict utilisent la stratégie de quarantaine par défaut (DefaultFullAccessPolicy sans notifications de quarantaine) comme décrit dans le tableau [ci-après](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br><br> Les administrateurs peuvent créer et sélectionner des stratégies de quarantaine personnalisées qui définissent des fonctionnalités plus restrictives ou moins restrictives pour les utilisateurs dans les stratégies anti-hameçonnage par défaut ou personnalisées. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Afficher le premier conseil de sécurité du contact** <br><br> _EnableFirstContactSafetyTips_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Pour plus d’informations, consultez [Premier conseil de sécurité de contact](set-up-anti-phishing-policies.md#first-contact-safety-tip).|
|**Afficher (?) pour les expéditeurs non authentifiés pour l’usurpation d’identité** <br><br> _EnableUnauthenticatedSender_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Ajoute un point d’interrogation (?) à la photo de l’expéditeur dans Outlook pour les expéditeurs usurpés non identifiés. Pour plus d’informations, consultez [les indicateurs d’expéditeur non authentifiés](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|
|**Afficher la balise « via »** <br><br> _EnableViaTag_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Ajoute une balise via (chris@contoso.com via fabrikam.com) à l’adresse From si elle est différente du domaine dans la signature DKIM ou l’adresse **MAIL FROM** . <br><br> Pour plus d’informations, consultez [les indicateurs d’expéditeur non authentifiés](set-up-anti-phishing-policies.md#unauthenticated-sender-indicators).|

## <a name="microsoft-defender-for-office-365-security"></a>sécurité Microsoft Defender pour Office 365

Des avantages supplémentaires en matière de sécurité sont fournis avec un abonnement Microsoft Defender pour Office 365. Pour obtenir les dernières actualités et informations, vous pouvez voir [les nouveautés de Defender pour Office 365](whats-new-in-defender-for-office-365.md).

> [!IMPORTANT]
>
> - La stratégie anti-hameçonnage par défaut dans Microsoft Defender pour Office 365 fournit une [protection contre l’usurpation d’identité](set-up-anti-phishing-policies.md#spoof-settings) et une intelligence de boîte aux lettres pour tous les destinataires. Toutefois, les autres fonctionnalités de [protection d’emprunt d’identité](#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) [disponibles et les paramètres avancés](#advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ne sont pas configurés ou activés dans la stratégie par défaut. Pour activer toutes les fonctionnalités de protection, modifiez la stratégie anti-hameçonnage par défaut ou créez des stratégies anti-hameçonnage supplémentaires.
>
> - Bien qu’il n’existe pas de stratégie de pièces jointes sécurisées ou de stratégie de liens sécurisés par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** offre une protection des pièces jointes sécurisées et une protection des liens sécurisés à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de sécurité prédéfinies Standard ou Strict, ou dans des stratégies de pièces jointes sécurisées personnalisées ou des stratégies de liens sécurisés). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).
>
> - [Les pièces jointes sécurisées pour la protection SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md) et la protection [des documents sécurisés](safe-docs.md) n’ont aucune dépendance vis-à-vis des stratégies liens fiables.

Si votre abonnement inclut Microsoft Defender pour Office 365 ou si vous avez acheté Defender pour Office 365 en tant que module complémentaire, définissez les configurations Standard ou Strict suivantes.

### <a name="anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage dans Microsoft Defender pour Office 365

Les clients EOP bénéficient d’un anti-hameçonnage de base comme décrit précédemment, mais Defender pour Office 365 inclut plus de fonctionnalités et de contrôle pour aider à prévenir, détecter et corriger les attaques. Pour créer et configurer ces stratégies, consultez Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

#### <a name="advanced-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ce paramètre, consultez [Seuils de hameçonnage avancés dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ce paramètre, consultez Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil d’e-mail d’hameçonnage** <br><br> _PhishThresholdLevel_|**1 - Standard** <br><br> `1`|**3 - Plus agressif** <br><br> `3`|**4 - Plus agressif** <br><br> `4`||

#### <a name="impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365

Pour plus d’informations sur ces paramètres, consultez [Les paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Pour configurer ces paramètres, consultez Configurer des stratégies [anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

|Nom de la fonctionnalité de sécurité|Par défaut|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|---|
|**Seuil d’hameçonnage & protection**|||||
|**Permettre aux utilisateurs de protéger** (protection des utilisateurs empruntés) <br><br> _EnableTargetedUserProtection_ <br><br> _TargetedUsersToProtect_|Non sélectionnée <br><br> `$false` <br><br> none|Sélectionné <br><br> `$true` <br><br> \<list of users\>|Sélectionné <br><br> `$true` <br><br> \<list of users\>|Nous vous recommandons d’ajouter des utilisateurs (expéditeurs de messages) dans des rôles clés. En interne, les expéditeurs protégés peuvent être votre PDG, le directeur financier et d’autres hauts dirigeants. En externe, les expéditeurs protégés peuvent inclure des membres du conseil ou votre conseil d’administration.|
|**Activer la protection des domaines** (protection de domaine empruntée)|Non sélectionnée|Sélectionné|Sélectionné||
|**Inclure les domaines que je possède** <br><br> _EnableOrganizationDomainsProtection_|Désactivé <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Inclure des domaines personnalisés** <br><br> _EnableTargetedDomainsProtection_ <br><br> _TargetedDomainsToProtect_|Désactivé <br><br> `$false` <br><br> none|Sélectionné <br><br> `$true` <br><br> \<list of domains\>|Sélectionné <br><br> `$true` <br><br> \<list of domains\>|Nous vous recommandons d’ajouter des domaines (domaines d’expéditeur) que vous ne possédez pas, mais avec lesquels vous interagissez fréquemment.|
|**Ajouter des expéditeurs et des domaines de confiance** <br><br> _ExcludedSenders_ <br><br> _ExcludedDomains_|Aucun|Aucun|Aucun|Selon votre organisation, nous vous recommandons d’ajouter des expéditeurs ou des domaines qui sont incorrectement identifiés comme tentatives d’emprunt d’identité.|
|**Activer la veille des boîtes aux lettres** <br><br> _EnableMailboxIntelligence_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Activer l’intelligence pour la protection de l’emprunt d’identité** <br><br> _EnableMailboxIntelligenceProtection_|Désactivé <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Ce paramètre autorise l’action spécifiée pour les détections d’emprunt d’identité par intelligence de boîte aux lettres.|
|**Actions**||||Partout où vous sélectionnez **Mettre en quarantaine le message**, une zone **de stratégie de mise en quarantaine Sélection** est disponible. Les stratégies de quarantaine définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine. <br><br> Les stratégies de sécurité prédéfinies Standard et Strict utilisent la stratégie de quarantaine par défaut (DefaultFullAccessPolicy sans notifications de quarantaine) comme décrit dans le tableau [ci-après](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br><br> Lorsque vous créez une stratégie anti-hameçonnage, une valeur vide signifie que la stratégie de quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages qui ont été mis en quarantaine par ce verdict (DefaultFullAccessPolicy pour tous les types de détection d’emprunt d’identité). <br><br> Les administrateurs peuvent créer et sélectionner des stratégies de quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs dans les stratégies anti-hameçonnage par défaut ou personnalisées. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Si le message est détecté en tant qu’utilisateur emprunt d’identité** <br><br> _TargetedUserProtectionAction_|**N’appliquez aucune action** <br><br> `NoAction`|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|**Si le message est détecté comme un domaine emprunté** <br><br> _TargetedDomainProtectionAction_|**N’appliquez aucune action** <br><br> `NoAction`|**Mettre en quarantaine le message** <br><br> `Quarantine`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|**Si l’intelligence de boîte aux lettres détecte un utilisateur emprunt d’identité** <br><br> _MailboxIntelligenceProtectionAction_|**N’appliquez aucune action** <br><br> `NoAction`|**Déplacer le message vers les dossiers de Email indésirables des destinataires** <br><br> `MoveToJmf`|**Mettre en quarantaine le message** <br><br> `Quarantine`||
|**Afficher l’info-bulle de sécurité de l’emprunt d’identité de l’utilisateur** <br><br> _EnableSimilarUsersSafetyTips_|Désactivé <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Afficher l’info-bulle de sécurité d’emprunt d’identité de domaine** <br><br> _EnableSimilarDomainsSafetyTips_|Désactivé <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Afficher le conseil de sécurité des caractères inhabituels d’emprunt d’identité de l’utilisateur** <br><br> _EnableUnusualCharactersSafetyTips_|Désactivé <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||

#### <a name="eop-anti-phishing-policy-settings-in-microsoft-defender-for-office-365"></a>Paramètres de stratégie anti-hameçonnage EOP dans Microsoft Defender pour Office 365

Il s’agit des mêmes paramètres que ceux disponibles dans [les paramètres de stratégie anti-courrier indésirable dans EOP](#eop-anti-spam-policy-settings).

### <a name="safe-attachments-settings"></a>Paramètres des pièces jointes sécurisées

Les pièces jointes sécurisées dans Microsoft Defender pour Office 365 incluent des paramètres globaux qui n’ont aucune relation avec les stratégies de pièces jointes sécurisées et des paramètres spécifiques à chaque stratégie liens sécurisés. Pour plus d’informations, consultez [Pièces jointes sécurisées dans Defender pour Office 365](safe-attachments.md).

Bien qu’il n’existe aucune stratégie de pièces jointes sécurisées par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des pièces jointes sécurisées à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de sécurité prédéfinies Standard ou Strict ou dans les stratégies de pièces jointes sécurisées personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-attachments"></a>Paramètres globaux pour les pièces jointes sécurisées

> [!NOTE]
> Les paramètres globaux des pièces jointes sécurisées sont définis par la stratégie de sécurité prédéfinies de **protection intégrée** , mais pas par les stratégies de sécurité prédéfinies **Standard** ou **Strict** . Dans les deux cas, les administrateurs peuvent modifier ces paramètres de pièces jointes sécurisées globales à tout moment.
>
> La colonne **Par défaut** affiche les valeurs avant l’existence de la stratégie de sécurité prédéfinies de **protection intégrée** . La colonne **de protection intégrée** affiche les valeurs définies par la stratégie de sécurité prédéfinies de **protection intégrée** , qui sont également nos valeurs recommandées.

Pour configurer ces paramètres, consultez [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) et [documents sécurisés dans Microsoft 365 E5](safe-docs.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Par défaut|Protection intégrée|Commentaire|
|---|:---:|:---:|---|
|**Activer Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams** <br><br> _EnableATPForSPOTeamsODB_|Désactivé <br><br> `$false`|Activé <br><br> `$true`|Pour empêcher les utilisateurs de télécharger des fichiers malveillants, consultez [Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).|
|**Activer les documents sécurisés pour les clients Office** <br><br> _EnableSafeDocs_|Désactivé <br><br> `$false`|Activé <br><br> `$true`|Cette fonctionnalité est disponible et significative uniquement avec des licences qui ne sont pas incluses dans Defender pour Office 365 (par exemple, Microsoft 365 A5 ou Microsoft 365 E5 Sécurité). Pour plus d’informations, consultez [Documents sécurisés dans Microsoft 365 A5 ou E5 Sécurité](safe-docs.md).|
|**Autoriser les utilisateurs à cliquer via la vue protégée même si des documents sécurisés ont identifié le fichier comme malveillant** <br><br> _AllowSafeDocsOpen_|Désactivé <br><br> `$false`|Désactivé <br><br> `$false`|Ce paramètre est lié aux documents sécurisés.|

#### <a name="safe-attachments-policy-settings"></a>Paramètres de stratégie pièces jointes fiables

Pour configurer ces paramètres, consultez [Configurer des stratégies de pièces jointes sécurisées dans Defender pour Office 365](set-up-safe-attachments-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy) et [Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de pièces jointes sécurisées par défaut, mais la protection des pièces jointes sécurisées est affectée à tous les destinataires par la [stratégie de sécurité prédéfinie de **protection intégrée**](preset-security-policies.md) (les utilisateurs qui ne sont pas définis dans les stratégies pièces jointes sécurisées).
>
> La valeur **par défaut dans** la colonne personnalisée fait référence aux valeurs par défaut dans les nouvelles stratégies de pièces jointes sécurisées que vous créez. Les colonnes restantes indiquent (sauf indication contraire) les valeurs configurées dans les stratégies de sécurité prédéfinies correspondantes.

|Nom de la fonctionnalité de sécurité|Valeur par défaut dans custom|Protection intégrée|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|:---:|---|
|**Réponse de programmes malveillants inconnus pièces jointes fiables** <br><br> _Activer_ et _action_|**Désactivé** <br><br> `-Enable $false` et `-Action Block`|**Bloquer** <br><br> `-Enable $true` et `-Action Block`|**Bloquer** <br><br> `-Enable $true` et `-Action Block`|**Bloquer** <br><br> `-Enable $true` et `-Action Block`|Lorsque le paramètre _Enable_ est $false, la valeur du paramètre _Action_ n’a pas d’importance.|
|**Stratégie de quarantaine** (_QuarantineTag_)|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy|AdminOnlyAccessPolicy| <br><br> Les stratégies de sécurité prédéfinies Standard et Strict utilisent la stratégie de quarantaine par défaut (AdminOnlyAccessPolicy sans notifications de quarantaine) comme décrit dans le tableau [ci-après](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). <br><br> Lorsque vous créez une stratégie de pièces jointes sécurisées, une valeur vide signifie que la stratégie de quarantaine par défaut est utilisée pour définir les fonctionnalités historiques des messages qui ont été mis en quarantaine par des pièces jointes sécurisées (AdminOnlyAccessPolicy sans notifications de mise en quarantaine). <br><br> Les administrateurs peuvent créer et sélectionner des stratégies de quarantaine personnalisées qui définissent davantage de fonctionnalités pour les utilisateurs. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).|
|**Redirection d’une pièce jointe avec des pièces jointes détectées** : **activer la redirection** <br><br> _Redirect_ <br><br> _RedirectAddress_|Non sélectionné et aucune adresse e-mail spécifiée. <br><br> `-Redirect $false` <br><br> _RedirectAddress_ est vide (`$null`)|Non sélectionné et aucune adresse e-mail spécifiée. <br><br> `-Redirect $false` <br><br> _RedirectAddress_ est vide (`$null`)|Sélectionné et spécifiez une adresse e-mail. <br><br> `$true` <br><br> une adresse e-mail|Sélectionné et spécifiez une adresse e-mail. <br><br> `$true` <br><br> une adresse e-mail|Rediriger les messages vers un administrateur de sécurité pour révision. <br><br> **Remarque** : ce paramètre n’est pas configuré dans les stratégies de sécurité prédéfinies de protection **standard**, **stricte** ou **intégrée** . Les valeurs **Standard** et **Strict** indiquent nos valeurs **recommandées** dans les nouvelles stratégies de pièces jointes sécurisées que vous créez.|
|**Appliquer la réponse de détection des pièces jointes sécurisées si l’analyse ne peut pas se terminer (délai d’expiration ou erreurs)** <br><br> _ActionOnError_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||

### <a name="safe-links-settings"></a>Paramètres liens sécurisés

Les liens sécurisés dans Defender pour Office 365 incluent des paramètres globaux qui s’appliquent à tous les utilisateurs inclus dans des stratégies de liens fiables actives et des paramètres spécifiques à chaque stratégie liens fiables. Pour plus d’informations, consultez [Liens fiables dans Defender pour Office 365](safe-links.md).

Bien qu’il n’existe aucune stratégie de liaisons sécurisées par défaut, la stratégie de sécurité prédéfinie de **protection intégrée** fournit une protection des liens sécurisés à tous les destinataires (utilisateurs qui ne sont pas définis dans les stratégies de sécurité prédéfinies standard ou strictes ou dans les stratégies de liens sécurisés personnalisées). Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

#### <a name="global-settings-for-safe-links"></a>Paramètres globaux pour les liens fiables

> [!NOTE]
> Les paramètres globaux des liens sécurisés sont définis par la stratégie de sécurité prédéfinies de **protection intégrée** , mais pas par les stratégies de sécurité prédéfinies **Standard** ou **Strict** . Dans les deux cas, les administrateurs peuvent modifier ces paramètres de liens fiables globaux à tout moment.
>
> La colonne **Par défaut** affiche les valeurs avant l’existence de la stratégie de sécurité prédéfinies de **protection intégrée** . La colonne **de protection intégrée** affiche les valeurs définies par la stratégie de sécurité prédéfinies de **protection intégrée** , qui sont également nos valeurs recommandées.

Pour configurer ces paramètres, consultez [Configurer les paramètres globaux pour les liens sécurisés dans Defender pour Office 365](configure-global-settings-for-safe-links.md).

Dans PowerShell, vous utilisez l’applet de commande [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365) pour ces paramètres.

|Nom de la fonctionnalité de sécurité|Par défaut|Protection intégrée|Commentaire|
|---|:---:|:---:|---|
|**Bloquer les URL suivantes** <br><br> _ExcludedUrls_|Vide <br><br> `$null`|Vide <br><br> `$null`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br><br> Pour plus d’informations, consultez [la liste « Bloquer les URL suivantes » pour les liens sécurisés](safe-links.md#block-the-following-urls-list-for-safe-links). <br><br> **Remarque** : vous pouvez désormais gérer les entrées d’URL de bloc dans la [liste d’autorisation/de blocage du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-block-entries-for-urls-in-the-tenant-allowblock-list). La liste « Bloquer les URL suivantes » est en cours de dépréciation. Nous allons essayer de migrer des entrées existantes de la liste « Bloquer les URL suivantes » pour bloquer les entrées d’URL dans la liste d’autorisations/de blocs du locataire. Les messages contenant l’URL bloquée seront mis en quarantaine.|

#### <a name="safe-links-policy-settings"></a>Coffre de stratégie liens

Pour configurer ces paramètres, consultez Configurer des stratégies [de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

Dans PowerShell, vous utilisez les applets de commande [New-SafeLinksPolicy](/powershell/module/exchange/new-safelinkspolicy) et [Set-SafeLinksPolicy](/powershell/module/exchange/set-safelinkspolicy) pour ces paramètres.

> [!NOTE]
> Comme décrit précédemment, il n’existe aucune stratégie de liens sécurisés par défaut, mais la protection des liens sécurisés est affectée à tous les destinataires par la [stratégie de sécurité prédéfinies de **protection intégrée**](preset-security-policies.md) (les utilisateurs qui, autrement, ne sont pas inclus dans les stratégies liens fiables).
>
> La colonne **Par défaut dans la colonne personnalisée** fait référence aux valeurs par défaut dans les nouvelles stratégies liens sécurisés que vous créez. Les colonnes restantes indiquent (sauf indication contraire) les valeurs configurées dans les stratégies de sécurité prédéfinies correspondantes.

|Nom de la fonctionnalité de sécurité|Valeur par défaut dans custom|Protection intégrée|Standard|Strict|Commentaire|
|---|:---:|:---:|:---:|:---:|---|
|**URL & cliquez sur les paramètres de protection**||||||
|**Action sur les URL potentiellement malveillantes dans les e-mails**||||||
|**Activé : les liens fiables vérifient une liste de liens malveillants connus lorsque des utilisateurs cliquent sur des liens dans un e-mail** <br><br> _EnableSafeLinksForEmail_|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Appliquer des liens fiables aux courriers envoyés au sein de l’organisation** <br><br> _EnableForInternalSenders_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Appliquer l’analyse d’URL en temps réel pour les liens suspects et les liens qui pointent vers des fichiers** <br><br> _ScanUrls_|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Attendre la fin de l’analyse de l’URL avant de remettre le message** <br><br> _DeliverMessageAfterScan_|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Ne pas réécrire d’URL, effectuer des vérifications via l’API liens fiables uniquement** <br><br> _DisableURLRewrite_|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`||
|**Ne pas réécrire les URL suivantes dans un e-mail** <br><br> _DoNotRewriteUrls_|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`|Vide <br><br> `$null`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br><br> **Remarque** : les entrées de la liste « Ne pas réécrire les URL suivantes » ne sont pas analysées ou encapsulées par des liens fiables pendant le flux de courrier. Utilisez [les entrées d’URL d’autorisation dans la liste d’autorisations/blocages du locataire](allow-block-urls.md#use-the-microsoft-365-defender-portal-to-create-allow-entries-for-urls-in-the-submissions-portal) afin que les URL ne soient pas analysées ou encapsulées par des liens sécurisés pendant le flux de messagerie _et_ au moment du clic.|
|**Action pour les URL potentiellement malveillantes dans Microsoft Teams**||||||
|**Activé : Liens fiables vérifie une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans Microsoft Teams** <br><br> _EnableSafeLinksForTeams_|Non sélectionnée <br><br> `$false`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Action pour les URL potentiellement malveillantes dans les applications Microsoft Office**||||||
|**Activé : les liens fiables vérifient une liste de liens malveillants connus lorsque les utilisateurs cliquent sur des liens dans des applications Microsoft Office** <br><br> _EnableSafeLinksForOffice_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Utilisez des liens sécurisés dans les applications de bureau et mobiles (iOS et Android) prises en charge Office 365. Pour plus d’informations, consultez [les paramètres Liens sécurisés pour les applications Office](safe-links.md#safe-links-settings-for-office-apps).|
|**Paramètres de protection au moment du clic**||||||
|**Suivre les clics de l’utilisateur** <br><br> _TrackUserClicks_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`||
|**Autoriser les utilisateurs à cliquer sur l’URL d’origine** <br><br> _AllowClickThrough_|Sélectionné <br><br> `$true`|Sélectionné <br><br> `$true`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|La désactivation de ce paramètre (en définissant _AllowClickThrough_ sur `$false`) empêche le clic sur l’URL d’origine.|
|**Afficher la personnalisation de l’organisation sur les pages de notification et d’avertissement** <br><br> _EnableOrganizationBranding_|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Non sélectionnée <br><br> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br><br> Avant d’activer ce paramètre, vous devez suivre les instructions fournies dans [Personnaliser le thème Microsoft 365 pour que votre organisation](../../admin/setup/customize-your-organization-theme.md) charge le logo de votre entreprise.|
|**Notification**||||||
|**Comment voulez-vous informer vos utilisateurs ?** <br><br> _CustomNotificationText_ <br><br> _UseTranslatedNotificationText_|**Utiliser le texte de notification par défaut** <br><br> Vide (`$null`) <br><br> `$false`|**Utiliser le texte de notification par défaut** <br><br> Vide (`$null`) <br><br> `$false`|**Utiliser le texte de notification par défaut** <br><br> Vide (`$null`) <br><br> `$false`|**Utiliser le texte de notification par défaut** <br><br> Vide (`$null`) <br><br> `$false`|Nous n’avons aucune recommandation spécifique pour ce paramètre. <br><br> Vous pouvez sélectionner **Utiliser le texte de notification personnalisé** (`-CustomNotificationText "<Custom text>"`) pour entrer et utiliser du texte de notification personnalisé. Si vous spécifiez du texte personnalisé, vous pouvez également sélectionner **Utiliser Microsoft Translator pour la localisation automatique** (`-UseTranslatedNotificationText $true`) pour traduire automatiquement le texte dans la langue de l’utilisateur.|

## <a name="related-articles"></a>Articles connexes

- Recherchez-vous les meilleures pratiques pour **les règles de flux de messagerie Exchange (également appelées règles de transport**) ? Consultez [les meilleures pratiques pour configurer les règles de flux de messagerie dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/configuration-best-practices).

- Les administrateurs et les utilisateurs peuvent envoyer des faux positifs (bon e-mail marqué comme mauvais) et des faux négatifs (e-mail incorrect autorisé) à Microsoft à des fins d’analyse. Pour plus d’informations, voir [Signaler des messages et des fichiers à Microsoft](report-junk-email-messages-to-microsoft.md).

- Utilisez ces liens pour plus d’informations sur la **configuration** de votre [service EOP](/exchange/standalone-eop/set-up-your-eop-service) et **la configuration** [de Microsoft Defender pour Office 365](defender-for-office-365.md). N’oubliez pas les instructions utiles dans « [Protéger contre les menaces dans Office 365](protect-against-threats.md) ».

- Les **bases de référence de sécurité pour Windows sont disponibles** ici : [où puis-je obtenir les lignes de base de sécurité ? pour les](/windows/security/threat-protection/windows-security-baselines#where-can-i-get-the-security-baselines) options DG/locales, et [utiliser des bases de référence de sécurité pour configurer des appareils Windows dans Intune](/intune/protect/security-baselines) pour Intune sécurité basée sur. Enfin, une comparaison entre les bases de référence de sécurité Microsoft Defender pour point de terminaison et Microsoft Intune est disponible dans [Comparer les Microsoft Defender pour point de terminaison et Windows Intune lignes de base de sécurité](/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline#compare-the-microsoft-defender-atp-and-the-windows-intune-security-baselines).
