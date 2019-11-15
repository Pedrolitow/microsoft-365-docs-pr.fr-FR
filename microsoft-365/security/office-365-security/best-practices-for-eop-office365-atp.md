---
title: Meilleures pratiques pour les paramètres de sécurité d’ATP et Office 365, recommandations, Sender Policy Framework, la création de rapports de messages basés sur un domaine, la conformité, la DomainKeys Identified identifiée, les étapes, son fonctionnement, etc.
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 10/23/2019
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
ms.openlocfilehash: 6f9d38f7f6200083983f42d74a54163566585a90
ms.sourcegitcommit: 2c2248b03f7753d64490f2f7e56ec644a235b65a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2019
ms.locfileid: "38640793"
---
# <a name="best-practices-for-eop-and-office-365-atp-security"></a>Meilleures pratiques pour la sécurité de l’ATP et d’Office 365

**Exchange Online Protection (EoP)** est le cœur de la sécurité des abonnements Office 365 et empêche les messages électroniques malveillants d’atteindre les boîtes de réception de vos employés. Toutefois, avec de nouvelles attaques plus sophistiquées émergentes tous les jours, des protections améliorées sont souvent requises. **Office 365 Advanced Threat Protection (ATP)** Le plan ATP 1 ou le plan ATP 2 contiennent des fonctionnalités supplémentaires qui donnent aux administrateurs plus de couches de sécurité, de contrôle et d’enquête. 

Bien que nous permettons aux administrateurs de sécurité de personnaliser leurs paramètres de sécurité, il existe deux niveaux de sécurité dans EOP et Office 365 ATP qui nous sont recommandés : **standard** et **strict**. L’environnement et les besoins de chaque client sont différents, mais nous pensons que ces niveaux de configurations de filtrage des messages empêchent le courrier indésirable d’atteindre la boîte de réception de vos employés dans la plupart des cas. 

Cette rubrique décrit ces paramètres recommandés par Microsoft pour vous aider à protéger vos utilisateurs Office 365.

## <a name="anti-spam-anti-malware-and-anti-phishing-protection-in-eop"></a>Blocage du courrier indésirable, des programmes malveillants et de la protection anti-hameçonnage dans EOP
Le blocage du courrier indésirable, anti-programme malveillant et anti-hameçonnage sont des fonctionnalités d’EOP qui peuvent être configurées par les administrateurs. Nous vous recommandons d’utiliser les configurations suivantes.

### <a name="anti-spam-policy"></a>Stratégie anti-courrier indésirable

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Action de détection du courrier indésirable|Déplacer le message dans le dossier Courrier indésirable|Mettre en quarantaine le message||
|Action de détection de courrier indésirable à fiabilité élevée|Mettre en quarantaine le message|Mettre en quarantaine le message||
|Action de détection de courrier d’hameçonnage|Mettre en quarantaine le message|Mettre en quarantaine le message||
|Action de détection de courrier hameçon à haute fiabilité|Mettre en quarantaine le message|Mettre en quarantaine le message||
|Action de détection de courrier en nombre|Déplacer le message dans le dossier Courrier indésirable|Mettre en quarantaine le message||
|Définir le seuil de courrier électronique en masse sur|6.x|4||
|Période de rétention de quarantaine|30 jours|30 jours||
|Conseils de sécurité|Activé|Activé||
|Expéditeurs autorisés|Aucune|Aucune||
|Domaines d’expéditeurs autorisés|Aucune|Aucune|L’ajout de domaines dont vous êtes propriétaire (également appelés _domaines acceptés_) à la liste des expéditeurs autorisés n’est pas obligatoire. En fait, il est considéré comme un risque élevé, car il permet aux acteurs incorrects de vous envoyer des messages qui seraient autrement filtrés. Utilisez l’Assistant d' [usurpation d’identité](learn-about-spoof-intelligence.md) dans le centre de sécurité & conformité de la page **paramètres anti-courrier indésirable** pour examiner tous les expéditeurs qui usurpent l’identité des domaines qui font partie de votre organisation ou qui usurpent des domaines externes.|
|Expéditeurs bloqués|Aucune|Aucune||
|Domaines des expéditeurs bloqués|Aucune|Aucune||
|Fréquence de notification de courrier indésirable de l’utilisateur final|Activé|Activé|3 jours|
|Purge automatique sans heure|Activé|Activé|Pour le courrier indésirable et les hameçons ZAP|
|MarkAsSpamBulkMail|Activé|Activé|Ce paramètre est disponible uniquement dans PowerShell|

#### <a name="outbound-spam-filter-policy"></a>Stratégie de filtrage du courrier indésirable sortant

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Limites de destinataires de stratégie de courrier indésirable sortant-limite horaire externe|400|500||
|Limites de destinataires de stratégie de courrier indésirable sortant-limite horaire interne|800|1000||
|Limites de destinataires de stratégie de courrier indésirable sortant-limite journalière|800|1000||
|Action lorsqu’un utilisateur dépasse les limites|Empêcher l’utilisateur d’envoyer des messages|Empêcher l’utilisateur d’envoyer des messages||

### <a name="anti-malware-policy"></a>Stratégie anti-programme malveillant

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Réponse de détection de programmes malveillants|Non|Non|Si un programme malveillant est détecté dans une pièce jointe, le message est mis en quarantaine et ne peut être libéré que par un administrateur.|
|« Filtre de type de pièces jointes courantes » pour bloquer les types de fichiers suspects|Activé|Activé||
|Purge automatique contre les programmes malveillants à zéro heure|Activé|Activé||
|Informer les expéditeurs internes du message non remis|Désactivé|Désactivé||
|Informer les expéditeurs externes du message non remis|Désactivé|Désactivé||

### <a name="anti-phishing-policy"></a>Stratégie anti-hameçonnage

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Activer la protection contre l’usurpation d’identité|Activé|Activé||
|Activer l’expéditeur non authentifié (marquage)|Activé|Activé||
|Si un message électronique est envoyé par une personne qui n’est pas autorisé à usurper votre domaine|Déplacer le message vers les dossiers de courrier indésirable des destinataires|Mettre en quarantaine le message||

## <a name="office-365-advanced-threat-protection-atp-security"></a>Sécurité Office 365-protection avancée contre les menaces (ATP)
Des avantages supplémentaires en matière de sécurité sont inclus dans un abonnement Office 365 Advanced Threat Protection. Pour obtenir les dernières informations et informations, vous pouvez consulter les nouveautés [d’Office 365 ATP](whats-new-in-office-365-atp.md). 

La protection avancée contre les menaces Office 365 inclut les stratégies de pièces jointes fiables et de liens fiables pour empêcher la remise des messages contenant des pièces jointes potentiellement malveillantes et empêcher les utilisateurs de cliquer sur les URL potentiellement dangereuses.

> [!IMPORTANT]
> La protection avancée contre le hameçonnage est l’un des avantages d’un abonnement Office 365 ATP. Activé par défaut, l’anti-hameçonnage ***doit*** être configuré à l’aide de stratégies avant de lancer le filtrage du courrier. Oublier de configurer des stratégies anti-hameçonnage pourrait exposer les utilisateurs à des courriers électroniques risqués. Veillez à configurer vos stratégies anti-hameçonnage après avoir ajouté un abonnement Office 365 ATP.

Si vous avez ajouté un abonnement Office 365 ATP à votre EOP, définissez les configurations suivantes.

### <a name="office-atp-anti-phishing-policy"></a>Stratégie anti-hameçonnage Office ATP
Les clients EOP reçoivent une stratégie anti-hameçonnage de base, mais avec la protection avancée contre les menaces Office 365, les administrateurs obtiennent davantage de fonctionnalités et de contrôles pour vous aider à prévenir, détecter et remidi contre les attaques.

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
|EnableAuthenticationSafetyTip|True|True|Ce paramètre est disponible uniquement dans PowerShell|
|EnableAuthenticationSoftPassSafetyTip|False|Vrai|Ce paramètre est disponible uniquement dans PowerShell|
|EnableSuspiciousSafetyTip|False|Vrai|Ce paramètre est disponible uniquement dans PowerShell|
|TreatSoftPassAsAuthenticated|Vrai|False|Ce paramètre est disponible uniquement dans PowerShell|

|Nom de la fonctionnalité de sécurité des paramètres avancés|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Seuils de hameçonnage avancés|2-agressif|3-plus agressif||

### <a name="safe-links-settings"></a>Paramètres de liens fiables

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Utiliser des liens fiables ATP dans les applications Office 365, Office pour iOS et Android|Activé|Activé|Cela relève des stratégies de liens fiables ATP qui s’appliquent à l’ensemble de l’Organisation|
Ne pas suivre lorsque les utilisateurs cliquent sur les liens fiables|Désactivé|Désactivé|Cela relève des stratégies de liens fiables ATP qui s’appliquent à l’ensemble de l’Organisation|
|Ne pas autoriser les utilisateurs à cliquer sur les liens fiables vers l’URL d’origine|Activé|Activé|Cela relève des stratégies de liens fiables ATP qui s’appliquent à l’ensemble de l’Organisation|
|Action pour les URL potentiellement malveillantes dans les messages|Activé|Activé||
|Application de l’analyse des URL en temps réel pour les liens suspects et les liens pointant vers des fichiers|Activé|Activé||
|Attendre la fin de l’analyse des URL avant de remettre le message|Activé|Activé||
|Appliquer des liens fiables aux messages électroniques envoyés au sein de l’Organisation|Activé|Activé||

### <a name="safe-attachments"></a>Pièces jointes fiables

|Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams.|Activé|Activé||
|Pièces jointes approuvées ATP réponse aux programmes malveillants inconnus|Bloc|Bloc||
|Redirection de la pièce jointe sur la détection|Activé|Activé|Rediriger vers l’adresse de messagerie d’un administrateur de sécurité qui sait comment déterminer si la pièce jointe est un programme malveillant ou non|
|Réponse aux pièces jointes approuvées ATP si l’analyse contre les pièces jointes expire ou si une erreur se produit|Activé|Activé||

## <a name="miscellaneous-settings-for-eop-or-office-365-atp"></a>Paramètres divers pour EOP ou Office 365 ATP

Ces paramètres couvrent un éventail de fonctionnalités qui ne rentrent pas nécessairement dans des catégories spécifiques ci-dessus. Certains de ces paramètres sont externes au centre de sécurité & conformité.

Nom de la fonctionnalité de sécurité|Standard|Empêcher|Commentaire|
|---------|---------|---------|---------|
|[Configurer SPF dans Office 365 pour empêcher l’usurpation](set-up-spf-in-office-365-to-help-prevent-spoofing.md)|Oui|Oui||
|[Utilisation de DKIM pour valider les messages sortants envoyés à partir de votre domaine personnalisé dans Office 365](use-dkim-to-validate-outbound-email.md)|Oui|Oui||
|[Utiliser DMARC pour valider les e-mails dans Office 365](use-dmarc-to-validate-email.md)|Oui|Oui|Utilisez action = Quarantine for standard et action = Reject pour strict.|
|Déployer le complément de rapport de message pour améliorer la création de rapports d’utilisateur final sur les E-mails suspects|Oui|Oui||
|Planifier les programmes malveillants et le courrier indésirable|Oui|Oui||
|Le transfert automatique vers les domaines externes ne doit pas être autorisé ni surveillé|Oui|Oui||
|L’audit unifié doit être activé|Oui|Oui||
|Connectivité IMAP à la boîte aux lettres|Désactivé|Désactivé||
|Connectivité POP à la boîte aux lettres|Désactivé|Désactivé||
|Envoi authentifié SMTP vers la boîte aux lettres|Désactivé|Désactivé||
|Connectivité EWS à la boîte aux lettres|Désactivé|Désactivé||
|Connectivité PowerShell|Désactivé|Désactivé||
|Utiliser l’intelligence d’usurpation d’identité pour les expéditeurs de liste d’autorisation dès que possible|Oui|Oui||
|Blocage du périmètre basé sur l’annuaire (DBEB)|Activé|Activé|Type de domaine = faisant autorité|
|[Configurer l’authentification multifacteur pour tous les comptes d’administrateur](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)|Activé|Activé||
