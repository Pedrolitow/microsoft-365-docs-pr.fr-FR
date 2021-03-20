---
title: Étapes de configuration des fonctionnalités de protection contre les menaces dans Microsoft 365
description: Découvrez comment déployer les services et fonctionnalités de protection contre les menaces dans Microsoft 365 E5.
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: m365d
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-threatprotection
- m365solution-scenario
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: f767b44b66fbc69f28a6514acc3936eb3074e70b
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50918477"
---
# <a name="configure-threat-protection-capabilities-across-microsoft-365"></a>Configurer les fonctionnalités de protection contre les menaces dans Microsoft 365

Suivez ces étapes pour configurer la protection contre les menaces dans Microsoft 365.


## <a name="step-1-set-up-multi-factor-authentication-and-conditional-access-policies"></a>Étape 1 : Configurer l’authentification multifacteur et les stratégies d’accès conditionnel

[L’authentification multifacteur](/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) oblige les utilisateurs à vérifier leur identité avec un appel téléphonique ou une application d’authentification. [Les stratégies d’accès](/azure/active-directory/conditional-access/overview) conditionnel définissent certaines exigences qui doivent être remplies pour que les utilisateurs accèdent aux applications et aux données dans Microsoft 365. Les stratégies mfa et d’accès conditionnel fonctionnent ensemble pour protéger votre organisation. Par exemple, si quelqu’un tente de se connecte à partir d’un appareil mobile à l’aide d’un compte qui n’est pas activé pour l' usage de l’ateur de base de données et qu’une stratégie d’accès conditionnel exige que l' usage de l' usage de l’mf soit en vigueur, l’utilisateur ne pourra pas se connecter.  

Microsoft a testé et recommandé un ensemble spécifique d’accès conditionnel et de stratégies associées pour protéger l’accès à toutes vos applications SaaS, en particulier Microsoft 365. Les stratégies sont recommandées pour la protection de référence, sensible et hautement réglementée. Commencez par implémenter les stratégies de protection de référence. 


[ ![ Stratégies courantes pour la configuration de l’identité et de l’accès aux appareils](../media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)Voir une version plus grande de cette 
 [image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)

### <a name="to-implement-baseline-protection-for-microsoft-365"></a>Pour implémenter la protection de référence pour Microsoft 365

![Processus de déploiement de la protection de référence](../media/deploy-threat-protection/deploy-threat-protection-identity-access-steps.png) 

1. [Configurez les conditions préalables, y compris Azure AD Identity Protection.](../security/office-365-security/identity-access-prerequisites.md)
2. [Configurez des stratégies communes d’accès aux identités](../security/office-365-security/identity-access-policies.md) et aux appareils pour la protection de référence.
3. Configurez des stratégies pour [les utilisateurs invités,](../security/office-365-security/identity-access-policies-guest-access.md) [Microsoft Teams,](../security/office-365-security/teams-access-policies.md) [Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)et [SharePoint Online et OneDrive.](../security/office-365-security/sharepoint-file-access-policies.md)

### <a name="more-information-about-protecting-identities"></a>Plus d’informations sur la protection des identités

- [Configurations des identités et de l’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md)
- [Conseils de sécurité pour Azure MFA](/azure/active-directory/authentication/multi-factor-authentication-security-best-practices)

## <a name="step-2-configure-microsoft-defender-for-identity"></a>Étape 2 : Configurer Microsoft Defender pour l’identité

[Microsoft Defender pour](/azure-advanced-threat-protection/what-is-atp) l’identité est une solution de sécurité basée sur le cloud qui fonctionne avec vos signaux AD DS (Active Directory Domain Services) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.

Microsoft Defender pour l’identité permet aux analystes et aux professionnels de la sécurité des opérations de sécurité (SecOps) de détecter les attaques avancées dans les environnements hybrides pour :
- Surveillez les utilisateurs, le comportement des entités et les activités avec des analyses basées sur l’apprentissage.
- Protéger les identités des utilisateurs et informations d’identification stockées dans Active Directory.
- Identifier et examiner les activités suspectes des utilisateurs et les attaques avancées tout au long de la chaîne de terminaison.
- Fournir des informations claires sur les incidents reposant sur une chronologie simple pour un triage rapide.

### <a name="to-set-up-microsoft-defender-for-identity"></a>Pour configurer Microsoft Defender pour l’identité

![Processus de déploiement de Microsoft Defender pour l’identité](../media/deploy-threat-protection/deploy-azure-atp-steps.png) 

1. [Configurer Microsoft Defender pour l’identité pour](/azure-advanced-threat-protection/install-atp-step1) protéger vos environnements principaux.
2. Protégez tous vos [contrôleurs de domaine](/azure-advanced-threat-protection/atp-sensor-monitoring) et [forêts.](/azure-advanced-threat-protection/atp-multi-forest)
3. Intégrez [les alertes Microsoft Defender for Identity](/azure-advanced-threat-protection/suspicious-activity-guide?tabs=external) à votre flux de travail d’opérations de sécurité (SecOps).

### <a name="more-information-about-microsoft-defender-for-identity"></a>Plus d’informations sur Microsoft Defender pour l’identité

- [Qu’est-ce que Microsoft Defender pour Identity ?](/azure-advanced-threat-protection/what-is-atp)
- [Vidéo : Présentation de Microsoft Defender pour l’identité](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- [Déploiement de Microsoft Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="step-3-turn-on-microsoft-365-defender"></a>Étape 3 : Activer Microsoft 365 Defender

[Microsoft 365 Defender](../security/mtp/microsoft-threat-protection.md) combine les signaux et orchestre les fonctionnalités en une seule solution. Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace . comment il est entré dans l’environnement, ce qu’il a affecté et comment il a actuellement un impact sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés.

Microsoft 365 Defender unifie les alertes, les incidents, les enquêtes et réponses automatisées, ainsi que la recherche avancée sur les charges de travail (Microsoft Defender pour l’identité, Microsoft Defender pour Office 365, Microsoft Defender pour endpoint et Microsoft Cloud App Security) dans un seul volet de l’expérience de verre. Une fois que vous avez configuré un ou plusieurs de vos services Defender pour Office 365, allumez Microsoft 365 Defender. De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft 365 Defender . envisagez d’opter pour la réception des fonctionnalités d’aperçu.

### <a name="to-set-up-microsoft-365-defender"></a>Pour configurer Microsoft 365 Defender

![Processus de déploiement de Microsoft 365 Defender](../media/deploy-threat-protection/deploy-mtp-steps.png) 

1. [Examinez les conditions préalables.](../security/mtp/prerequisites.md)
2. [Activer Microsoft 365 Defender.](../security/mtp/mtp-enable.md)
3. [Optez pour les fonctionnalités d’aperçu.](../security/mtp/preview.md)

### <a name="more-information-about-microsoft-365-defender"></a>Plus d’informations sur Microsoft 365 Defender

- [Présentation de Microsoft 365 Defender](../security/mtp/microsoft-threat-protection.md)
- [Nouveautés de Microsoft 365 Defender](../security/mtp/whats-new.md)

## <a name="step-4-configure-microsoft-defender-for-office-365"></a>Étape 4 : Configurer Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](../security/office-365-security/office-365-atp.md) protège votre organisation contre les menaces malveillantes dans les messages électroniques (pièces jointes et URL), les documents Office et les outils de collaboration. Le tableau suivant répertorie les fonctionnalités et fonctionnalités de Microsoft Defender pour Office 365 incluses dans Microsoft 365 E5 :

|Fonctionnalités de configuration, de protection et de détection|Fonctionnalités d’automatisation, d’examen, de correction et d’éducation|
|---|---|
|[Pièces jointes fiables](../security/office-365-security/atp-safe-attachments.md)<br/>[Liens fiables](../security/office-365-security/atp-safe-links.md)<br/>[Documents sécurisés](../security/office-365-security/safe-docs.md)<br/>[ATP pour SharePoint, OneDrive et Microsoft Teams](../security/office-365-security/atp-for-spo-odb-and-teams.md)<br/>[Anti-hameçonnage dans la protection de Defender pour Office 365](../security/office-365-security/set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)|[Suivi des menaces](../security/office-365-security/threat-trackers.md)<br/>[Threat Explorer](../security/office-365-security/threat-explorer.md)<br/>[Examen et réponse automatisés](../security/office-365-security/office-365-air.md)<br/>[Simulateur d’attaques](../security/office-365-security/attack-simulator.md)|
|

Avec Microsoft Defender pour Office 365, les membres de votre organisation peuvent communiquer et collaborer plus en toute sécurité, avec une protection contre les menaces pour leur contenu de courrier électronique et leurs documents Office.

### <a name="to-set-up-microsoft-defender-for-office-365"></a>Pour configurer Microsoft Defender pour Office 365

![Processus de déploiement de Microsoft Defender pour Office 365](../media/deploy-threat-protection/deploy-office365-atp-steps.png) 

1. [Configurez et configurez vos stratégies Microsoft Defender pour Office 365.](../security/office-365-security/protect-against-threats.md)
2. [Affichez et utilisez vos rapports Microsoft Defender pour Office 365.](../security/office-365-security/view-reports-for-atp.md)
3. [Utiliser les fonctionnalités d’examen et de réponse aux menaces.](../security/office-365-security/office-365-ti.md)

### <a name="more-information-about-microsoft-defender-for-office-365"></a>Plus d’informations sur Microsoft Defender pour Office 365

- [Présentation de Microsoft Defender pour Office 365](../security/office-365-security/office-365-atp.md)
- [Nouveautés de Microsoft Defender pour Office 365](../security/office-365-security/whats-new-in-office-365-atp.md)

## <a name="step-5-configure-microsoft-defender-for-endpoint"></a>Étape 5 : Configurer Microsoft Defender pour le point de terminaison

[Microsoft Defender pour le point](/windows/security/threat-protection) de terminaison protège les appareils de votre organisation (également appelés points de terminaison) contre les cybermenaces, les attaques avancées et les violations de données. Les équipes de sécurité peuvent être plus efficaces dans la gestion de la sécurité de leurs points de terminaison. Des outils robustes aident les organisations à suivre les systèmes non mis en place à l’aide de la détection des vulnérabilités avec la gestion [des menaces et des vulnérabilités.](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) Les fonctionnalités automatisées de détection et de correction, telles que la [](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) réduction de la [surface](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction)d’attaque, la [protection](/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10)nouvelle [génération,](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)la détection et la réponse des points de terminaison, ainsi que les examens et corrections automatisés contribuent à protéger vos appareils contre les programmes malveillants. En plus de ces fonctionnalités, les clients peuvent recevoir des notifications proactives et consulter les experts microsoft en matière de menaces à la demande, dans le cadre du service de recherche géré par l’utilisateur. 


### <a name="set-up-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour le point de terminaison

![Processus de déploiement de Microsoft Defender pour le point de terminaison](../media/deploy-threat-protection/deploy-mdatp-steps.png) 

1. [Préparez votre environnement pour microsoft Defender pour le déploiement de point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/deployment-phases)
2. [Configurer votre déploiement microsoft Defender pour le point de terminaison.](/windows/security/threat-protection/micros.oft-defender-atp/production-deployment)
3. [Intégration au service Microsoft Defender for Endpoint.](/windows/security/threat-protection/microsoft-defender-atp/onboarding)
4. [Effectuer vos tâches administratives de sécurité les plus importantes.](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation)

### <a name="more-information-about-microsoft-defender-for-endpoint"></a>Plus d’informations sur Microsoft Defender pour le point de terminaison

- [En savoir plus sur Microsoft Defender pour point de terminaison.](/windows/security/threat-protection)
- [Essayez le laboratoire d’évaluation de Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/evaluation-lab).

## <a name="step-6-configure-microsoft-cloud-app-security"></a>Étape 6 : Configurer Microsoft Cloud App Security

[Microsoft Cloud App Security est](/cloud-app-security) un courtier de sécurité Cloud Access qui prend en charge la collecte de journaux, les connecteurs d’API et le proxy inverse. Microsoft Cloud App Security offre une visibilité enrichie, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et lutter contre les cybermenaces dans tous vos services cloud. Avec Microsoft Cloud App Security, vos opérations de sécurité peuvent protéger les informations sensibles de votre organisation, se protéger contre les cybermenaces et les anomalies, découvrir et surveiller les applications qui accèdent aux données de votre organisation et s’assurer que les applications cloud de votre organisation répondent aux exigences de conformité.

### <a name="set-up-microsoft-cloud-app-security"></a>Configurer Microsoft Cloud App Security

![Processus de déploiement de Microsoft Cloud App Security](../media/deploy-threat-protection/deploy-mcas-steps.png) 

1. [Configurer le portail et d’autres conditions de base.](/cloud-app-security/general-setup)
2. [Configurer la découverte cloud et](/cloud-app-security/set-up-cloud-discovery) connecter des [applications.](/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
3. [Déployer le contrôle d’application d’accès conditionnel pour les applications disponibles.](/cloud-app-security/proxy-deployment-aad)
4. [Utilisez les outils d’examen et les tableaux de bord.](/cloud-app-security/investigate)

### <a name="more-information-about-microsoft-cloud-app-security"></a>Rubrique relative aux informations supplémentaires concernant Microsoft Cloud App Security

- [Passer en revue les nouvelles fonctionnalités et fonctionnalités.](/cloud-app-security/release-notes)
- [En savoir plus sur Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security).

## <a name="step-7-monitor-status-and-take-actions"></a>Étape 7 : Surveiller l’état et prendre des mesures

Une fois que vous avez installé et déployé vos services et fonctionnalités de protection contre les menaces, l’étape suivante consiste à surveiller les détections de menaces et à prendre les mesures appropriées. Votre meilleur point de départ est le Centre de sécurité Microsoft 365 ( ), où vous pouvez surveiller et gérer la sécurité au sein de vos [https://security.microsoft.com](https://security.microsoft.com) identités, données, appareils, applications et infrastructure Microsoft. 

![Centre de sécurité Microsoft 365](../media/solutions-architecture-center/m365-security-center.png)

Le Centre de sécurité Microsoft 365 est spécifiquement destiné aux administrateurs de sécurité et aux équipes des opérations de sécurité. Dans le Centre de sécurité Microsoft 365, vous pouvez :
- Affichez l’état de sécurité global de votre organisation avec [le niveau de sécurisation.](../security/mtp/microsoft-secure-score.md)
- [Surveillez et affichez des rapports](../security/mtp/overview-security-center.md) sur l’état de vos identités, données, appareils, applications et infrastructure.
- Connectez les points sur les alertes par le biais [d’incidents.](../security/mtp/incident-queue.md)
- Utiliser [l’examen et la correction automatisés pour](../security/mtp/mtp-autoir.md) traiter les menaces.
- [Recherchez de manière proactive les menaces,](../security/mtp/advanced-hunting-overview.md)telles que les tentatives d’intrusion ou l’activité de violation affectant vos e-mails, données, appareils et identités.
- [Comprendre les dernières campagnes d’attaque](../security/mtp/latest-attack-campaigns.md) et techniques avec l’analyse des menaces.
- ... et bien plus encore !

### <a name="more-information-about-the-microsoft-365-security-center"></a>Plus d’informations sur le Centre de sécurité Microsoft 365

- [Mise en place du Centre de sécurité Microsoft 365.](../security/mtp/overview-security-center.md)
- [Surveiller et afficher les rapports.](../security/mtp/overview-security-center.md)
- [Consultez les portails de sécurité dans Microsoft 365.](../security/mtp/portals.md)

## <a name="step-8-train-users"></a>Étape 8 : Former les utilisateurs

La formation des utilisateurs peut faire gagner beaucoup de temps et de frustration à vos utilisateurs et à votre équipe en matière d’opérations de sécurité. Les utilisateurs expérimentés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites web suspects. 

Le manuel de campagne de [cyber-sécurité](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) de l’établissement de Contrôles School fournit d’excellents conseils sur l’établissement d’une culture forte de sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage. 

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

|Concept  |Ressources  |
|---------|---------|
|Microsoft 365     |[Parcours d’apprentissage personnalisables](/office365/customlearning/) <p>Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs finaux de votre organisation.        |
|Sécurité Microsoft 365 |[Module d’apprentissage : sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité. |
|Authentification multifacteur     | [Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au niveau de votre organisation.    |

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’prendre les mesures décrites dans cet article : Protéger votre compte et vos appareils contre les pirates [informatiques et les programmes malveillants.](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx) Ces actions incluent :
- Utilisation de mots de passe forts
- Protection des appareils 
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non utilisés)
    
Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en prenant les mesures recommandées dans les articles suivants :
- [Protéger votre compte de Outlook.com de messagerie](https://support.microsoft.com/office/help-protect-your-outlook-com-email-account-a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)
- [Protéger votre compte Gmail avec la vérification en deux étapes](https://go.microsoft.com/fwlink/?linkid=2015688&amp;clcid=0x409)