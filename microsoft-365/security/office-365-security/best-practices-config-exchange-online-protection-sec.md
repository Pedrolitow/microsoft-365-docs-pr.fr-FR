---
title: Meilleures pratiques en matière de configuration pour EOP et Office 365 sécurité ATP, meilleures pratiques, paramètres, recommandations, Sender Policy Framework, rapports et conformité de message basés sur un domaine, DomainKeys Identified identifiés, étapes, fonctionnement,
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 10/18/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
description: Quelles sont les meilleures pratiques pour les paramètres de sécurité Exchange Online Protection (EOP) et Advanced Threat Protection (ATP) ? Qu’est-ce qui est recommandé ? Qu’est-ce qui doit être utilisé de manière agressive ? Quels sont les autres éléments que vous obtenez si vous utilisez également la protection avancée contre les menaces ?
ms.openlocfilehash: b40b4189ed996e1b2f671b77602630f2a98966a5
ms.sourcegitcommit: ffdf576fbc62c4c316f6d8061d2bd973e7df9f56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "37598298"
---
# <a name="best-practices-for-configuring-eop-and-office-365-atp-security"></a>Meilleures pratiques pour la configuration de la sécurité de l’ATP et d’Office 365

Exchange Online Protection (EOP) est le cœur de la sécurité pour les abonnements de E3 Office 365. Il est facultatif, et même encouragé, pour que les clients de E3 achètent un abonnement à Office 365 Advanced Threat Protection (ATP), par exemple. ATP plan 1 ou ATP plan 2, afin de tirer parti de la sécurité supplémentaire disponible dans les abonnements Office 365.

Nous aborderons deux niveaux de sécurité, appelés recommandé et agressif dans EOP, qui décrivent les commentaires sur l’utilisation des fonctionnalités aux deux niveaux de sécurité. Les sections commencent par la validation et l’authentification par courrier électronique, ce qui implique une partie de l’extérieur d’Office 365, dans DNS, et la sécurisation des messages sortants, ce qui permet aux clients de converser les ressources qu’ils doivent envoyer. Ces paramètres protègent au mieux votre abonnement.


## <a name="email-authentication"></a>Authentification de messagerie

SPF, DKIM et DMARC sont des acronymes pour Sender Policy Framework, DomainKeys Identified Identified Mail, ainsi qu’une authentification, un rapport et une conformité des messages basés sur un domaine (un Mouthful) et sont la base de l’authentification et de la validation de la messagerie.

Ces méthodes gèrent les messages sortants à partir d’Office 365 et aident les systèmes de destination à approuver que les messages électroniques provenant de votre domaine sont valides. Il s’agit des seules meilleures pratiques que nous allons aborder, qui impliquent des configurations qui doivent être effectuées en *dehors* d’Office 365, dans votre système DNS. Pour connaître les étapes de configuration spécifiques, reportez-vous à la section [authentification et validation](https://docs.microsoft.com/office365/securitycompliance/how-office-365-uses-spf-to-prevent-spoofing) de la messagerie dans la table des matières sécurité et conformité.


|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|[Créer des enregistrements SPF](https://docs.microsoft.com/office365/securitycompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)    | Oui        |    Oui     |   -      |
|[Configuration de la signature DKIM pour les domaines](https://docs.microsoft.com/office365/securitycompliance/use-dkim-to-validate-outbound-email)     |  Oui       |    Oui     |  -       |
|[Implémenter DMARC avec l’action de rejet ou de mise en quarantaine](https://docs.microsoft.com/office365/securitycompliance/use-dmarc-to-validate-email)     |   Oui      |     Oui    |   Utilisez action = None pour recommandé et action = Reject pour agressif.     |

> [!IMPORTANT]
> Pour travailler avec les rôles de sécurité et les autorisations, assurez-vous que vous disposez du ou des rôles corrects dans Office 365 ou le centre de sécurité et conformité. Si vous êtes un *administrateur de sécurité* dans Azure Active Directory, un *administrateur Global* dans Office 365 ou un *Gestionnaire d’organisation Exchange Online* dans Exchange Online/Exchange Online PowerShell, vous êtes prêt à aller plus en plus.

## <a name="anti-spam-anti-malware-and-anti-phishing"></a>Blocage du courrier indésirable, anti-programme malveillant et anti-hameçonnage

La protection contre le courrier indésirable et les programmes malveillants sont des fonctionnalités d’EOP. Le filtrage du courrier indésirable, activé par défaut dans Office 365, analyse tous les messages et affecte une valeur de seuil de probabilité de courrier indésirable à chaque message. Pour clarifier, son objectif est d’énumérer la manière dont le filtre est sûr que le message est (ou non) du courrier indésirable. Les valeurs faibles, comme-1 sont des courriers non indésirables provenant d’expéditeurs approuvés et de terres dans une boîte aux lettres d’utilisateur. Les scores élevés, tels que 7, 8 ou 9, sont soit très suspects, soit des expéditeurs de courrier indésirable connus et des responsables du courrier indésirable d’un utilisateur ou de la mise en quarantaine accessible par l’administrateur.

Le filtrage des programmes malveillants est également activé par défaut dans Office 365. Comme le filtrage du courrier indésirable, les filtres anti-programmes malveillants fonctionnent sur les messages entrants et sortants. Dans les deux cas, cette protection peut être configurée pour un meilleur ajustement par les administrateurs.

Les filtres phising sont activés par défaut dans Office 365, mais doivent être configurés pour une meilleure adéquation. Voici ce que nous recommandons pour la protection anti-hameçonnage dans EOP.

### <a name="anti-spam"></a>Blocage du courrier indésirable

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Période de rétention de quarantaine    |   Oui      |     Oui    |   30 jours   |
|Fréquence de notification de courrier indésirable de l’utilisateur final   |   Oui      |     Oui    |   3 jours   |
|Zéro heure la purge automatique doit être activée.   |   Oui      |     Oui    |   True  |
|L’action de détection du courrier indésirable doit être envoyée à | JMF | Quarantaine | - |
|L’action de détection de courrier indésirable à fiabilité élevée doit être envoyée à | Quarantaine | Quarantaine| - |
|L’action de détection en bloc doit être définie sur | JMF | Quarantaine | - |
|Définir le seuil de courrier électronique en masse sur | 6.x | 4 | - |
|Les conseils de sécurité doivent être activés.| True | True | - |
|Activer la notification de courrier indésirable de l’utilisateur final| Vrai | False | - |
|Expéditeurs autorisés | Aucune | Aucune | - |
|Domaines d’expéditeurs autorisés | Aucune | Aucune | - |
|Expéditeurs bloqués | Aucune | Aucune | - |
|Domaines des expéditeurs bloqués | Aucune | Aucune | - |
|Stratégie de courrier indésirable sortant RRL | 500 | 500 | - |

Recommandé pour **les** deux niveaux recommandés et agressifs :

|Nom de la fonctionnalité de sécurité  |
|---------|
|IncreaseScoreWithImageLinks|
|IncreaseScoreWithNumericIps|
|IncreaseScoreWithRedirectToOtherPort|
|IncreaseScoreWithBizOrInfoUrls|
|MarkAsSpamEmptyMessages|
|MarkAsSpamJavaScriptInHtml|
|MarkAsSpamFramesInHtml|
|MarkAsSpamObjectTagsInHtml|
|MarkAsSpamEmbedTagsInHtml|
|MarkAsSpamFormTagsInHtml|
|MarkAsSpamWebBugsInHtml|
|MarkAsSpamSensitiveWordList|
|MarkAsSpamFromAddressAuthFail|
|MarkAsSpamNdrBackscatter|

Recommandé pour **les niveaux de niveau** recommandé et agressif :

|Nom de la fonctionnalité de sécurité  |
|---------|
|MarkAsSpamSpfRecordHardFail|
|MarkAsSpamBulkMail|

### <a name="anti-malware"></a>Anti-programme malveillant

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Configurer les notifications de programmes malveillants pour les sources internes |Oui |Oui |- |
|Désactiver la notification des expéditeurs externes de détection de programmes malveillants |Oui |Oui |- |
|Utiliser le « filtre de type de pièces jointes courantes » pour bloquer les types de fichiers suspects | Oui |Oui |- |
|Programme malveillant ZAP |True |True |- |
|Action de programmes malveillants |Bloc |Bloc |- |

### <a name="anti-phishing"></a>Anti-hameçonnage

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Zéro heure la purge automatique doit être activée-hameçonnage| True | True | - | 
|L’action de détection d’hameçon doit être définie sur | Mise en quarantaine-demande | Mise en quarantaine-administrateur | - |
|L’action de détection de hameçonnage à niveau de confiance élevé doit être définie sur | Mise en quarantaine-administrateur | Mise en quarantaine-administrateur | - |
|EnableMailboxIntelligence | True | True | - |
|EnableSimilarUsersSafetyTips | True | True | - |
|EnableSimilarDomainsSafetyTips | True | True | - |
|EnableUnusualCharactersSafetyTips | True | True | - |
|TargetedUserProtectionAction |NoAction |Bloc | - |
|MailboxIntelligenceProtectionAction |NoAction |Bloc | - |
|TargetedDomainProtectionAction |NoAction |Bloc | - |
|AuthenticationFailAction |MoveToJmf |Quarantaine | - |
|AntiSpoofEnforcementType |Importante |Importante | - |
|EnableAuthenticationSafetyTip |False |Vrai | - |
|EnableAntiSpoofEnforcement |True |True | - |
|EnableUnauthenticatedSender |True |True | - |
|EnableAuthenticationSoftPassSafetyTip |False |Vrai | - |
|TreatSoftPassAsAuthenticated |Vrai |False | - |
|EnableSuspiciousSafetyTip |True |True | - |

## <a name="office-365-advanced-threat-protection-atp-security"></a>Sécurité Office 365-protection avancée contre les menaces (ATP)

Précédemment, j’ai dit qu’il a été encouragé pour les abonnements de E3 afin d’ajouter un plan de service Office 365 DAV (plan 1) ou le plan de disponibilité 2 le plus complet. La protection avancée contre le hameçonnage est une raison pour laquelle. Activé par défaut, l’anti-hameçonnage ***doit*** être configuré avec des stratégies pour fonctionner. En oubliant de configurer les stratégies anti-hameçonnage exposent les utilisateurs à des risques, assurez-vous que l’étape 2 est ajoutée après avoir ajouté un abonnement ATP.

> [!IMPORTANT]
>  Si vous disposez d’un abonnement E5, vous avez actuellement un [plan ATP 2](https://products.office.com/exchange/advance-threat-protection). Consultez ce lien pour découvrir [les nouveautés de la](https://review.docs.microsoft.com/microsoft-365/security/office-365-security/whats-new-in-office-365-atp?branch=oatp-newstuff)protection avancée contre les menaces.

### <a name="advanced-anti-phishing"></a>Protection avancée contre le hameçonnage

Le hameçonnage est une tentative de dissembler comme une société ou une personne digne de rôle pour voler des informations personnelles telles que des numéros de carte de crédit ou des codes confidentiels ou des mots de passe d’ordinateur ou d’appareil. Le hameçonnage peut impliquer :

- L' **usurpation**, où les usurpateurs tentent d’envoyer des messages pour le compte d’une cible spécifique dans un domaine (par exemple, ellar@2020contoso.com tentant d’envoyer des courriers électroniques pour ellar@2020litware.com (un scénario de méthodes d’authentification de messagerie électronique peuvent aider à contrecarrer). 

- **Emprunt d’identité**, où le courrier électronique reçu dont l’expéditeur est similaire (ou semblable) à un domaine cible ou un nom d’utilisateur. L’acteur incorrect ici, imite un nom d’utilisateur spécifique ou envoie des messages à partir d’un domaine cible. Voici un domaine Pretense : ellar @ 2020 | itware. com et voici un utilisateur Pretense : ellαr @ 2020litware. com (examinez attentivement les noms de domaine et d’utilisateur dans ces exemples pour intercepter l’emprunt d’identité de domaine et d’utilisateur).

Si vous avez ajouté un abonnement Office 365 ATP à votre EOP, veillez à définir les configurations suivantes.

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Définir le seuil d’hameçonnage avancé sur | n°2 | 4 | - |
|Activer la protection contre l’usurpation d’identité | Oui | Oui | - |
|Activer l’intelligence des boîtes aux lettres dans les stratégies d’emprunt d’identité | Oui | Oui | - |
|Activer la protection contre l’usurpation d’identité basée sur les boîtes aux lettres | Oui | Oui | - |
|L’action d’emprunt d’identité de domaine doit être | JMF | Quarantaine | - |
|L’action d’emprunt d’identité de l’utilisateur doit être | JMF | Qurantine | - |
|L’action de protection contre l’usurpation d’identité basée sur les boîtes aux lettres doit être |TETE  |JMF | - |

### <a name="safe-links-and-safe-attachments"></a>Liens fiables et pièces jointes fiables

 La protection avancée contre les menaces inclut les stratégies de pièces jointes fiables et de liens fiables pour empêcher la remise des messages contenant des pièces jointes potentiellement malveillantes et empêcher les utilisateurs de cliquer sur des URL potentiellement dangereuses.

#### <a name="safe-links"></a>Liens fiables

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Les liens fiables ATP doivent suivre les clics des utilisateurs à des fins de réponse. |Oui |Oui |- |
|Les liens fiables ATP doivent être activés pour les applications Office |Oui |Oui |- |
|Les liens fiables ATP doivent être activés pour le domaine interne |Oui |Oui |- |
|Les liens fiables ATP doivent appliquer l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers. |Oui |Oui |- |
|Les liens fiables ATP doivent attendre la fin de l’analyse des URL avant de remettre le message. |Oui |Oui |- |
<!--
|URLs to block | | | |
|URLs not to wrap | | | |-->

#### <a name="safe-attachments"></a>Pièces jointes fiables

|Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|L’action de stratégie de pièces jointes sécurisée ATP doit être |Quarantaine |Quarantaine |- |
|La protection ATP doit être activée pour OneDrive, SharePoint et Teams |Oui |Oui |- |
<!--
|Allowed file hashes | | | |
|Blocked file hashes | | | |
-->

## <a name="miscellaneous-settings"></a>Paramètres divers

Ces paramètres couvrent un éventail de fonctionnalités qui ne rentrent pas nécessairement dans des catégories spécifiques ci-dessus. Il se peut également que vous trouviez des paramètres de 1 OFF.

Nom de la fonctionnalité de sécurité  |Recommandé |Façon  |Commentaire  |
|---------|---------|---------|---------|
|Créer des enregistrements SPF |Oui |Oui |- |
|Configuration de la signature DKIM pour les domaines |Oui |Oui |- |
|Implémenter le rapport de message basé sur un domaine et la conformité (DMARC) avec l’action de rejet ou de mise en quarantaine |action = None |action = refuser | |
|Déployer le complément de rapport de message pour améliorer la création de rapports d’utilisateur final sur les E-mails suspects |Oui |Oui |- |
|Planifier les programmes malveillants et le courrier indésirable |Oui |Oui |- |
|L’auto-fowarding vers les domaines externes doit être interdite ou surveillée |- |Oui |- |
|L’audit unifié doit être activé |Oui |Oui |- |
|IMAP doit être désactivé là où il n’est pas nécessaire |- |activation |- |
|Le POP doit être désactivé lorsque ce n’est pas obligatoire |- |activation |- |
|L’envoi authentifié SMTP doit être désactivé lorsqu’il n’est pas requis par les applications |- |activation |- |
|EWS doit être désactivé |- |activation |- |
|PowerShell |- |activation |- |
|Configuration de l’environnement de stratégie des expéditeurs pour une panne forcée |-all |-all |- |
|Utiliser l’intelligence d’usurpation d’identité pour les expéditeurs de liste d’autorisation dès que possible |Oui |Oui |- |
|Blocage du périmètre basé sur l’annuaire (DBEB) |Activé |Activé |Type de domaine = faisant autorité |
