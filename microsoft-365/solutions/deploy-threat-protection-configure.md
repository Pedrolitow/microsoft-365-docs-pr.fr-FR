---
title: Étapes de configuration des fonctionnalités de protection contre les menaces dans Microsoft 365
description: Utilisez cet article comme guide pour implémenter votre solution de protection contre les menaces. Déployez les services et fonctionnalités de protection contre les menaces Microsoft 365 E5.
keywords: solution de sécurité, configuration, configuration, Microsoft 365 E5, protection avancée contre les menaces, defender
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.technology: m365d
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-threatprotection
- m365solution-scenario
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: 32ee06e77b9c3f32e4bb9b07458925a254756d2d
ms.sourcegitcommit: 4740e69326eb7f8302eec7bab5bd516d498e4492
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2021
ms.locfileid: "59401889"
---
# <a name="configure-threat-protection-capabilities-across-microsoft-365"></a>Configurer les fonctionnalités de protection contre les menaces dans Microsoft 365

Suivez ces étapes pour configurer la protection contre les menaces dans Microsoft 365.

## <a name="step-1-set-up-multi-factor-authentication-and-conditional-access-policies"></a>Étape 1 : Configurer l’authentification multifacteur et les stratégies d’accès conditionnel

[L’authentification multifacteur](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) exige que les utilisateurs vérifient leur identité avec un appel téléphonique ou une application d’authentification. [Les stratégies d’accès](/azure/active-directory/conditional-access/overview) conditionnel définissent certaines exigences qui doivent être remplies pour que les utilisateurs accèdent aux applications et aux données dans Microsoft 365. Les stratégies mfa et d’accès conditionnel fonctionnent ensemble pour protéger votre organisation. Par exemple, si quelqu’un tente de se connecte à partir d’un appareil mobile à l’aide d’un compte qui n’est pas activé pour l' usage de l’mf et qu’une stratégie d’accès conditionnel exige que l' usage de l’mf soit en vigueur, l’utilisateur ne peut pas se connecter.  

Microsoft a testé et recommandé un ensemble spécifique d’accès conditionnel et de stratégies associées pour protéger l’accès à toutes vos applications SaaS, en particulier Microsoft 365. Les stratégies sont recommandées pour la protection de référence, sensible et hautement réglementée. Commencez par implémenter les stratégies de protection de référence.

[ ![ Stratégies courantes pour la configuration de l’accès aux identités et aux appareils.](../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png) 
 [Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png)

### <a name="to-implement-baseline-protection-for-microsoft-365"></a>Pour implémenter la protection de référence pour Microsoft 365

![Processus de déploiement de la protection de référence.](../media/deploy-threat-protection/deploy-threat-protection-identity-access-steps.png) 

1. [Configurez les conditions préalables, y compris Azure AD Identity Protection.](../security/office-365-security/identity-access-prerequisites.md)
2. [Configurez des stratégies communes d’accès aux identités](../security/office-365-security/identity-access-policies.md) et appareils pour la protection de référence.
3. Configurez des [stratégies](../security/office-365-security/identity-access-policies-guest-access.md)pour les utilisateurs invités, [Microsoft Teams,](../security/office-365-security/teams-access-policies.md) [Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)et [SharePoint Online et OneDrive](../security/office-365-security/sharepoint-file-access-policies.md).

### <a name="more-information-about-protecting-identities"></a>Plus d’informations sur la protection des identités

- [Configurations des identités et de l’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md)
- [Conseils de sécurité pour Azure MFA](/azure/active-directory/authentication/multi-factor-authentication-security-best-practices)

## <a name="step-2-configure-microsoft-defender-for-identity"></a>Étape 2 : Configurer Microsoft Defender pour l’identité

[Microsoft Defender pour](/defender-for-identity/what-is) l’identité est une solution de sécurité basée sur le cloud qui fonctionne avec vos signaux AD DS (Active Directory Domain Services) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.

Microsoft Defender pour l’identité permet aux analystes et aux professionnels de la sécurité des opérations de sécurité (SecOps) de détecter les attaques avancées dans les environnements hybrides pour :

- Surveillez les utilisateurs, le comportement des entités et les activités avec des analyses basées sur l’apprentissage.
- Protéger les identités des utilisateurs et informations d’identification stockées dans Active Directory.
- Identifier et examiner les activités suspectes des utilisateurs et les attaques avancées tout au long de la chaîne de terminaison.
- Fournir des informations claires sur les incidents reposant sur une chronologie simple pour un triage rapide.

### <a name="to-set-up-microsoft-defender-for-identity"></a>Pour configurer Microsoft Defender pour l’identité

![Processus de déploiement de Microsoft Defender pour l’identité.](../media/deploy-threat-protection/deploy-azure-atp-steps.png) 

1. [Configurer Microsoft Defender pour l’identité pour](/azure-advanced-threat-protection/install-atp-step1) protéger vos environnements principaux.
2. Protégez tous vos [contrôleurs de domaine](/azure-advanced-threat-protection/atp-sensor-monitoring) et [forêts.](/azure-advanced-threat-protection/atp-multi-forest)
3. Intégrez [les alertes Microsoft Defender for Identity](/azure-advanced-threat-protection/suspicious-activity-guide?tabs=external) à votre flux de travail d’opérations de sécurité (SecOps).

### <a name="more-information-about-microsoft-defender-for-identity"></a>Plus d’informations sur Microsoft Defender pour l’identité

- [Qu’est-ce que Microsoft Defender pour Identity ?](/azure-advanced-threat-protection/what-is-atp)
- [Vidéo : Présentation de Microsoft Defender pour l’identité](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- [Déploiement de Microsoft Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="step-3-turn-on-microsoft-365-defender"></a>Étape 3 : Activer Microsoft 365 Defender

[Microsoft 365 Defender](../security/defender/microsoft-365-defender.md) combine les signaux et orchestre les fonctionnalités dans une solution unique. Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace . comment il est entré dans l’environnement, ce qu’il a affecté et comment il a actuellement un impact sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés.

Microsoft 365 Defender unifie les alertes, les incidents, l’examen et la réponse automatisés, ainsi que la recherche avancée sur les charges de travail (Microsoft Defender pour l’identité, Microsoft Defender pour Office 365, Microsoft Defender pour le point de terminaison et Microsoft Cloud App Security) dans un seul volet de l’expérience en verre. De nouvelles fonctionnalités sont continuellement ajoutées aux Microsoft 365 Defender ; envisagez d’opter pour la réception des fonctionnalités d’aperçu.

### <a name="to-set-up-microsoft-365-defender"></a>Pour configurer Microsoft 365 Defender

![Processus de déploiement des Microsoft 365 Defender.](../media/deploy-threat-protection/deploy-mtp-steps.png) 

1. [Examinez les conditions préalables.](../security/defender/prerequisites.md)
2. [Activer Microsoft 365 Defender](../security/defender/m365d-enable.md).
3. [Optez pour les fonctionnalités d’aperçu.](../security/defender/preview.md)

### <a name="more-information-about-microsoft-365-defender"></a>Plus d’informations sur Microsoft 365 Defender

- [Qu’est-ce que Microsoft 365 Defender ?](../security/defender/microsoft-365-defender.md)
- [Nouveautés de Microsoft 365 Defender](../security/defender/whats-new.md)

## <a name="step-4-configure-microsoft-defender-for-office-365"></a>Étape 4 : Configurer Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](../security/office-365-security/defender-for-office-365.md) protège votre organisation contre les menaces malveillantes dans les messages électroniques (pièces jointes et URL), les Office documents et les outils de collaboration. Le tableau suivant répertorie les fonctionnalités et fonctionnalités de Microsoft Defender Office 365 incluses dans Microsoft 365 E5 :

<br/><br/>

|Fonctionnalités de configuration, de protection et de détection|Fonctionnalités d’automatisation, d’examen, de correction et d’éducation|
|---|---|
|[Pièces jointes fiables](../security/office-365-security/safe-attachments.md) <p> [Liens fiables](../security/office-365-security/safe-links.md) <p> [Documents sécurisés](../security/office-365-security/safe-docs.md) <p> [Pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md) <p> [Protection anti-hameçonnage dans Microsoft 365](../security/office-365-security/anti-phishing-protection.md)|[Suivi des menaces](../security/office-365-security/threat-trackers.md) <p> [Threat Explorer](../security/office-365-security/threat-explorer.md) <p> [Examen et réponse automatisés](../security/office-365-security/office-365-air.md) <p> [Formation à la simulation d'attaque](../security/office-365-security/attack-simulation-training.md)|

Avec Microsoft Defender pour Office 365, les membres de votre organisation peuvent communiquer et collaborer plus en toute sécurité, avec une protection contre les menaces pour leur contenu de messagerie et leurs documents Office documents.

### <a name="to-set-up-microsoft-defender-for-office-365"></a>Pour configurer Microsoft Defender pour Office 365

![Processus de déploiement de Microsoft Defender pour Office 365.](../media/deploy-threat-protection/deploy-office365-atp-steps.png) 

1. [Configurez et configurez votre Microsoft Defender pour Office 365 stratégies.](../security/office-365-security/protect-against-threats.md)
2. [Affichez et utilisez votre Microsoft Defender pour Office 365 rapports.](../security/office-365-security/view-reports-for-mdo.md)
3. [Utiliser les fonctionnalités d’examen et de réponse aux menaces.](../security/office-365-security/office-365-ti.md)

### <a name="more-information-about-microsoft-defender-for-office-365"></a>Plus d’informations sur Microsoft Defender pour Office 365

- [Vue d’ensemble Office 365 Microsoft Defender for Office 365](../security/office-365-security/defender-for-office-365.md)
- [Nouveautés de Microsoft Defender pour Office 365](../security/office-365-security/whats-new-in-defender-for-office-365.md)

## <a name="step-5-configure-microsoft-defender-for-endpoint"></a>Étape 5 : Configurer Microsoft Defender pour le point de terminaison

[Microsoft Defender pour le point](/windows/security/threat-protection) de terminaison protège les appareils de votre organisation (également appelés points de terminaison) contre les cybermenaces, les attaques avancées et les violations de données. Les équipes de sécurité peuvent être plus efficaces dans la gestion de la sécurité de leurs points de terminaison. Des outils robustes aident les organisations à suivre les systèmes non mis en place à l’aide de la détection des vulnérabilités avec la gestion [des menaces et des vulnérabilités.](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) Les fonctionnalités automatisées de détection et de correction, telles que [](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) la réduction de la [surface](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction)d’attaque, la [protection](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10)nouvelle [génération, protection évolutive des points de terminaison](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)et les examens et corrections automatisés contribuent à protéger vos appareils contre les programmes malveillants. En plus de ces fonctionnalités, les clients peuvent recevoir des notifications proactives et consulter les Spécialistes des menaces Microsoft à la demande, dans le cadre du service de recherche géré par l’utilisateur.

### <a name="set-up-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour point de terminaison

![Processus de déploiement de Microsoft Defender pour le point de terminaison.](../media/deploy-threat-protection/deploy-mdatp-steps.png) 

1. [Préparez votre environnement pour Microsoft Defender pour le point de terminaison.](../security/defender-endpoint/deployment-phases.md)
2. [Déployez Microsoft Defender pour le point de terminaison.](../security/defender-endpoint/production-deployment.md)
3. [Intégration au service Microsoft Defender for Endpoint.](../security/defender-endpoint/onboarding.md)
4. [Effectuer vos tâches administratives de sécurité les plus importantes.](../security/defender-endpoint/tvm-security-recommendation.md)

### <a name="more-information-about-microsoft-defender-for-endpoint"></a>Plus d’informations sur Microsoft Defender pour le point de terminaison

- [En savoir plus sur Microsoft Defender pour point de terminaison.](../security/defender-endpoint/microsoft-defender-endpoint.md)
- [Essayez le laboratoire d’évaluation de Microsoft Defender for Endpoint](../security/defender-endpoint/evaluation-lab.md).

## <a name="step-6-configure-microsoft-cloud-app-security"></a>Étape 6 : Configurer Microsoft Cloud App Security

[Microsoft Cloud App Security](/cloud-app-security) est un courtier de sécurité d’accès cloud qui prend en charge la collecte de journaux, les connecteurs d’API et le proxy inverse. Microsoft Cloud App Security offre une visibilité enrichie, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et lutter contre les cybermenaces dans tous vos services cloud. Grâce à Microsoft Cloud App Security, vos opérations de sécurité peuvent protéger les informations sensibles de votre organisation, se protéger contre les cybermenaces et les anomalies, découvrir et surveiller les applications qui accèdent aux données de votre organisation et s’assurer que les applications cloud de votre organisation répondent aux exigences de conformité.

### <a name="set-up-microsoft-cloud-app-security"></a>Configurer Microsoft Cloud App Security

![Processus de déploiement des Microsoft Cloud App Security.](../media/deploy-threat-protection/deploy-mcas-steps.png) 

1. [Configurer le portail et d’autres conditions de base.](/cloud-app-security/general-setup)
2. [Configurer la découverte cloud et](/cloud-app-security/set-up-cloud-discovery) connecter des [applications.](/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
3. [Déployer le contrôle d’application d’accès conditionnel pour les applications disponibles.](/cloud-app-security/proxy-deployment-aad)
4. [Utilisez les outils d’examen et les tableaux de bord.](/cloud-app-security/investigate)

### <a name="more-information-about-microsoft-cloud-app-security"></a>Rubrique relative aux informations supplémentaires concernant Microsoft Cloud App Security

- [Passer en revue les nouvelles fonctionnalités et fonctionnalités.](/cloud-app-security/release-notes)
- [En savoir plus sur Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security).

## <a name="step-7-monitor-status-and-take-actions"></a>Étape 7 : Surveiller l’état et prendre des mesures

Une fois que vous avez installé et déployé vos services et fonctionnalités de protection contre les menaces, l’étape suivante consiste à surveiller les détections de menaces et à prendre les mesures appropriées. Votre meilleur point de départ est le centre de sécurité Microsoft 365 ( ), où vous pouvez surveiller et gérer la sécurité au sein de vos [https://security.microsoft.com](https://security.microsoft.com) identités, données, appareils, applications et infrastructure Microsoft.

![Microsoft 365 de sécurité.](../media/solutions-architecture-center/m365-security-center.png)

Le centre Microsoft 365 sécurité est destiné aux administrateurs de sécurité et aux équipes en matière d’opérations de sécurité. Dans le Microsoft 365 de sécurité, vous pouvez :

- Affichez l’état de sécurité global de votre organisation avec [le niveau de sécurisation.](/microsoft-365/security/defender/microsoft-secure-score)
- [Surveillez et affichez des rapports](../security/defender-endpoint/threat-protection-reports.md) sur l’état de vos identités, données, appareils, applications et infrastructure.
- Connecter points sur les alertes par le biais [d’incidents.](/microsoft-365/security/defender/incident-queue)
- Utiliser [l’examen et la correction automatisés pour](../security/defender/m365d-autoir.md) traiter les menaces.
- [Recherchez de manière proactive les menaces,](/microsoft-365/security/defender/advanced-hunting-overview)telles que les tentatives d’intrusion ou l’activité de violation affectant vos e-mails, données, appareils et identités.
- [Comprendre les dernières campagnes d’attaque](/microsoft-365/security/defender/latest-attack-campaigns) et techniques avec l’analyse des menaces.
- ... et bien plus encore !

### <a name="more-information-about-the-microsoft-365-security-center"></a>Plus d’informations sur le centre Microsoft 365 de sécurité

- [Mise en place du centre de Microsoft 365 de sécurité.](../security/defender/overview-security-center.md)
- [Surveiller et afficher les rapports.](../security/defender/overview-security-center.md)
- [Consultez les portails de sécurité dans Microsoft 365](../security/defender/portals.md).

## <a name="step-8-train-users"></a>Étape 8 : Former les utilisateurs

La formation des utilisateurs peut faire gagner beaucoup de temps et de frustration à vos utilisateurs et à votre équipe en matière d’opérations de sécurité. Les utilisateurs expérimentés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et sont plus susceptibles d’éviter les sites web suspects. 

Le manuel de campagne de [cyber-sécurité](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) de l’établissement de Contrôles School fournit d’excellents conseils sur l’établissement d’une culture forte de sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage. 

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

<br/><br/>

|Concept|Ressources|
|---|---|
|Microsoft 365|[Parcours d’apprentissage personnalisables](/office365/customlearning/) <p> Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs finaux de votre organisation.|
|Sécurité Microsoft 365|[Learning module : sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](/learn/modules/security-with-microsoft-365) <p> Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité.|
|Authentification multifacteur|[Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p> Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au niveau de votre organisation.|

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’prendre les mesures décrites dans cet article : Protéger votre compte et vos appareils contre les pirates [informatiques et les programmes malveillants.](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx) Ces actions incluent :

- Utilisation de mots de passe forts
- Protection des appareils
- Activation des fonctionnalités de sécurité sur Windows 10 mac et pc (pour les appareils non utilisés)

Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en prenant les mesures recommandées dans les articles suivants :

- [Protéger votre compte Outlook.com](https://support.microsoft.com/office/help-protect-your-outlook-com-email-account-a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)
- [Protéger votre compte Gmail avec la vérification en deux étapes](https://go.microsoft.com/fwlink/?linkid=2015688&amp;clcid=0x409)
