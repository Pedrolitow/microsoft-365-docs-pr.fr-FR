---
title: Étapes de configuration des fonctionnalités de protection contre les menaces dans Microsoft 365
description: Découvrez comment déployer les services et fonctionnalités de protection contre les menaces dans Microsoft 365 E5.
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
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
ms.openlocfilehash: 492db78c9aea881ae05dbc66f5e84ad98629b923
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49931985"
---
# <a name="configure-threat-protection-capabilities-across-microsoft-365"></a>Configurer les fonctionnalités de protection contre les menaces dans Microsoft 365

Suivez ces étapes pour configurer la protection contre les menaces dans Microsoft 365.


## <a name="step-1-set-up-multi-factor-authentication-and-conditional-access-policies"></a>Étape 1 : Configurer l’authentification multifacteur et les stratégies d’accès conditionnel

[L’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) oblige les utilisateurs à vérifier leur identité avec un appel téléphonique ou une application d’authentification. [Les stratégies d’accès](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) conditionnel définissent certaines exigences qui doivent être remplies pour que les utilisateurs accèdent aux applications et aux données dans Microsoft 365. L’mf et les stratégies d’accès conditionnel fonctionnent ensemble pour protéger votre organisation. Par exemple, si quelqu’un tente de se connecter à partir d’un appareil mobile à l’aide d’un compte qui n’est pas activé pour l' usage de l’mf et qu’une stratégie d’accès conditionnel exige l’application de l’mf, cet utilisateur ne pourra pas se connecter.  

Microsoft a testé et recommandé un ensemble spécifique d’accès conditionnel et de stratégies associées pour protéger l’accès à toutes vos applications SaaS, en particulier Microsoft 365. Les stratégies sont recommandées pour la protection de base, sensible et hautement réglementée. Commencez par implémenter les stratégies pour la protection de référence. 


[ ![ Stratégies courantes pour la configuration de l’identité et de l’accès aux](../media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)appareils 
 [Voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)

### <a name="to-implement-baseline-protection-for-microsoft-365"></a>Pour implémenter la protection de référence pour Microsoft 365

![Processus de déploiement de la protection de référence](../media/solutions-architecture-center/deploy-threat-protection-identity-access-steps.png) 

1. [Configurez les conditions préalables, y compris Azure Identity Protection.](../security/office-365-security/identity-access-prerequisites.md)
2. [Configurez des stratégies communes d’accès aux identités](../security/office-365-security/identity-access-policies.md) et aux appareils pour la protection de référence.
3. Configurez des stratégies pour [les utilisateurs invités,](../security/office-365-security/identity-access-policies-guest-access.md) [Microsoft Teams,](../security/office-365-security/teams-access-policies.md) [Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)et [SharePoint Online et OneDrive.](../security/office-365-security/sharepoint-file-access-policies.md)

### <a name="more-information-about-protecting-identities"></a>Plus d’informations sur la protection des identités

- [Configurations des identités et de l’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md)
- [Conseils de sécurité pour Azure MFA](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices)

## <a name="step-2-configure-microsoft-defender-for-identity"></a>Étape 2 : Configurer Microsoft Defender pour l’identité

[Microsoft Defender pour](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) l’identité est une solution de sécurité basée sur le cloud qui fonctionne avec vos signaux [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.

Microsoft Defender pour l’identité permet aux analystes et aux professionnels de la sécurité des opérations de sécurité (SecOps) de détecter les attaques avancées dans les environnements hybrides pour :
- Surveillez les utilisateurs, le comportement des entités et les activités avec des analyses basées sur l’apprentissage.
- Protéger les identités des utilisateurs et informations d’identification stockées dans Active Directory.
- Identifier et examiner les activités suspectes des utilisateurs et les attaques avancées tout au long de la chaîne de terminaison.
- Fournir des informations claires sur les incidents reposant sur une chronologie simple pour un triage rapide.

### <a name="to-set-up-microsoft-defender-for-identity"></a>Pour configurer Microsoft Defender pour l’identité

![Processus de déploiement de Microsoft Defender pour l’identité](../media/solutions-architecture-center/deploy-azure-atp-steps.png) 

1. [Configurer Microsoft Defender pour l’identité pour](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1) protéger vos environnements principaux.
2. Protégez tous vos [contrôleurs de domaine](https://docs.microsoft.com/azure-advanced-threat-protection/atp-sensor-monitoring) et [forêts.](https://docs.microsoft.com/azure-advanced-threat-protection/atp-multi-forest)
3. Intégrez [les alertes Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide?tabs=external) à votre flux de travail d’opérations de sécurité (SecOps).

### <a name="more-information-about-microsoft-defender-for-identity"></a>Plus d’informations sur Microsoft Defender pour l’identité

- [Qu’est-ce que Microsoft Defender pour Identity ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Vidéo : Présentation de Microsoft Defender pour l’identité](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- [Déploiement de Microsoft Defender pour l’identité](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="step-3-turn-on-microsoft-365-defender"></a>Étape 3 : Activer Microsoft 365 Defender

[Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) combine les signaux et orchestre les fonctionnalités en une seule solution. Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace . comment il est entré dans l’environnement, ce qu’il a affecté et comment il a actuellement un impact sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés.

Microsoft 365 Defender unifie les alertes, les incidents, les enquêtes et réponses automatisées, ainsi que la recherche avancée sur les charges de travail (Microsoft Defender pour l’identité, Microsoft Defender pour Office 365, Microsoft Defender pour endpoint et Microsoft Cloud App Security) dans un seul volet de l’expérience de verre. Une fois que vous avez configuré un ou plusieurs de vos services Defender pour Office 365, allumez Microsoft 365 Defender. De nouvelles fonctionnalités sont continuellement ajoutées à Microsoft 365 Defender . envisagez d’opter pour la réception des fonctionnalités d’aperçu.

### <a name="to-set-up-microsoft-365-defender"></a>Pour configurer Microsoft 365 Defender

![Processus de déploiement de Microsoft 365 Defender](../media/solutions-architecture-center/deploy-mtp-steps.png) 

1. [Examinez les conditions préalables.](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites)
2. [Activer Microsoft 365 Defender.](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable)
3. [Optez pour les fonctionnalités d’aperçu.](https://docs.microsoft.com/microsoft-365/security/mtp/preview)

### <a name="more-information-about-microsoft-365-defender"></a>Plus d’informations sur Microsoft 365 Defender

- [Présentation de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection)
- [Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)

## <a name="step-4-configure-microsoft-defender-for-office-365"></a>Étape 4 : Configurer Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) protège votre organisation contre les menaces malveillantes dans les messages électroniques (pièces jointes et URL), les documents Office et les outils de collaboration. Le tableau suivant répertorie les fonctionnalités et fonctionnalités de Microsoft Defender pour Office 365 incluses dans Microsoft 365 E5 :

|Fonctionnalités de configuration, de protection et de détection|Fonctionnalités d’automatisation, d’examen, de correction et d’éducation|
|---|---|
|[Pièces jointes fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-attachments)<br/>[Liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links)<br/>[Documents sécurisés](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-docs)<br/>[ATP pour SharePoint, OneDrive et Microsoft Teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams)<br/>[Anti-hameçonnage dans la protection de Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies#exclusive-settings-in-atp-anti-phishing-policies)|[Suivi des menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-trackers)<br/>[Threat Explorer](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer)<br/>[Examen et réponse automatisés](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)<br/>[Simulateur d’attaques](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator)|
|

Avec Microsoft Defender pour Office 365, les membres de votre organisation peuvent communiquer et collaborer plus en toute sécurité, avec une protection contre les menaces pour leur contenu de courrier électronique et leurs documents Office.

### <a name="to-set-up-microsoft-defender-for-office-365"></a>Pour configurer Microsoft Defender pour Office 365

![Processus de déploiement de Microsoft Defender pour Office 365](../media/solutions-architecture-center/deploy-office365-atp-steps.png) 

1. [Configurez et configurez vos stratégies Microsoft Defender pour Office 365.](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)
2. [Affichez et utilisez vos rapports Microsoft Defender pour Office 365.](https://docs.microsoft.com/microsoft-365/security/office-365-security/view-reports-for-atp)
3. [Utiliser les fonctionnalités d’examen et de réponse aux menaces.](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-ti)

### <a name="more-information-about-microsoft-defender-for-office-365"></a>Plus d’informations sur Microsoft Defender pour Office 365

- [Présentation de Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)
- [Nouveautés de Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/whats-new-in-office-365-atp)

## <a name="step-5-configure-microsoft-defender-for-endpoint"></a>Étape 5 : Configurer Microsoft Defender pour le point de terminaison

[Microsoft Defender pour le point](https://docs.microsoft.com/windows/security/threat-protection) de terminaison protège les appareils de votre organisation (également appelés points de terminaison) contre les cybermenaces, les attaques avancées et les violations de données. Les équipes de sécurité peuvent être plus efficaces dans la gestion de la sécurité de leurs points de terminaison. Des outils robustes aident les organisations à suivre les systèmes non mis en place à l’aide de la détection des vulnérabilités avec la gestion [des menaces et des vulnérabilités.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) Les fonctionnalités automatisées de détection et de correction, telles que la [](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) réduction de la [surface](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction)d’attaque, la [protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10)nouvelle [génération,](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response)la détection et la réponse des points de terminaison, ainsi que les examens et corrections automatisés contribuent à protéger vos appareils contre les programmes malveillants. En plus de ces fonctionnalités, les clients peuvent recevoir des notifications proactives et consulter les experts microsoft en matière de menaces à la demande, dans le cadre du service de recherche géré par l’utilisateur. 


### <a name="set-up-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour le point de terminaison

![Processus de déploiement de Microsoft Defender pour le point de terminaison](../media/solutions-architecture-center/deploy-mdatp-steps.png) 

1. [Préparez votre Microsoft Defender pour le déploiement de point de terminaison.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/deployment-phases)
2. [Configurer votre déploiement de Microsoft Defender pour les points de terminaison](https://docs.microsoft.com/windows/security/threat-protection/micros.oft-defender-atp/production-deployment)
3. [Intégration au service Microsoft Defender for Endpoint.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/onboarding)
4. [Effectuer vos tâches administratives de sécurité les plus importantes.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation)

### <a name="more-information-about-microsoft-defender-for-endpoint"></a>Plus d’informations sur Microsoft Defender pour le point de terminaison

- [En savoir plus sur Microsoft Defender pour point de terminaison.](https://docs.microsoft.com/windows/security/threat-protection)
- [Essayez le laboratoire d’évaluation de Microsoft Defender for Endpoint.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/evaluation-lab)

## <a name="step-6-configure-microsoft-cloud-app-security"></a>Étape 6 : Configurer Microsoft Cloud App Security

[Microsoft Cloud App Security est](https://docs.microsoft.com/cloud-app-security) un courtier de sécurité Cloud Access qui prend en charge la collecte de journaux, les connecteurs d’API et le proxy inverse. Microsoft Cloud App Security offre une visibilité enrichie, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et lutter contre les cybermenaces dans tous vos services cloud. Avec Microsoft Cloud App Security, vos opérations de sécurité peuvent protéger les informations sensibles de votre organisation, se protéger contre les cybermenaces et les anomalies, découvrir et surveiller les applications qui accèdent aux données de votre organisation et s’assurer que les applications cloud de votre organisation répondent aux exigences de conformité.

### <a name="set-up-microsoft-cloud-app-security"></a>Configurer Microsoft Cloud App Security

![Processus de déploiement de Microsoft Cloud App Security](../media/solutions-architecture-center/deploy-mcas-steps.png) 

1. [Configurer le portail et d’autres exigences de base.](https://docs.microsoft.com/cloud-app-security/general-setup)
2. [Configurer la découverte cloud et](https://docs.microsoft.com/cloud-app-security/set-up-cloud-discovery) connecter des [applications.](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps)
3. [Déployer le contrôle d’application d’accès conditionnel pour les applications disponibles.](https://docs.microsoft.com/cloud-app-security/proxy-deployment-aad)
4. [Utilisez les outils d’examen et les tableaux de bord.](https://docs.microsoft.com/cloud-app-security/investigate)

### <a name="more-information-about-microsoft-cloud-app-security"></a>Rubrique relative aux informations supplémentaires concernant Microsoft Cloud App Security

- [Passer en revue les nouvelles fonctionnalités.](https://docs.microsoft.com/cloud-app-security/release-notes)
- [En savoir plus sur Microsoft Cloud App Security.](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)

## <a name="step-7-monitor-status-and-take-actions"></a>Étape 7 : Surveiller l’état et prendre des mesures

Une fois que vous avez installé et déployé vos services et fonctionnalités de protection contre les menaces, l’étape suivante consiste à surveiller les détections de menaces et à prendre les mesures appropriées. Votre meilleur point de départ est le Centre de sécurité Microsoft 365 ( ), où vous pouvez surveiller et gérer la sécurité au sein de vos [https://security.microsoft.com](https://security.microsoft.com) identités, données, appareils, applications et infrastructure Microsoft. 

![Centre de sécurité Microsoft 365](../media/solutions-architecture-center/m365-security-center.png)

Le Centre de sécurité Microsoft 365 est spécifiquement destiné aux administrateurs de sécurité et aux équipes en matière d’opérations de sécurité. Dans le Centre de sécurité Microsoft 365, vous pouvez :
- Affichez l’état de sécurité global de votre organisation avec [le niveau de sécurisation.](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score)
- [Surveillez et affichez des rapports](https://docs.microsoft.com/microsoft-365/security/mtp/monitoring-and-reporting) sur l’état de vos identités, données, appareils, applications et infrastructure.
- Connectez les points sur les alertes par le biais [d’incidents.](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue)
- Utiliser [l’examen et la correction automatisés pour](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir) traiter les menaces.
- [Recherchez de manière proactive les menaces,](https://docs.microsoft.com/microsoft-365/security/mtp/advanced-hunting-overview)telles que les tentatives d’intrusion ou l’activité de violation affectant vos e-mails, données, appareils et identités.
- [Comprendre les dernières campagnes d’attaque](https://docs.microsoft.com/microsoft-365/security/mtp/latest-attack-campaigns) et techniques avec l’analyse des menaces.
- ... et bien plus encore !

### <a name="more-information-about-the-microsoft-365-security-center"></a>Plus d’informations sur le Centre de sécurité Microsoft 365

- [Mise en place du Centre de sécurité Microsoft 365.](https://docs.microsoft.com/microsoft-365/security/mtp/overview-security-center)
- [Surveiller et afficher les rapports.](https://docs.microsoft.com/microsoft-365/security/mtp/monitoring-and-reporting)
- [Consultez les portails de sécurité dans Microsoft 365.](https://docs.microsoft.com/microsoft-365/security/mtp/portals)

## <a name="step-8-train-users"></a>Étape 8 : Former les utilisateurs

La formation des utilisateurs peut faire gagner beaucoup de temps et de frustration à vos utilisateurs et à votre équipe en matière d’opérations de sécurité. Les utilisateurs expérimentés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites web suspects. 

Le manuel de campagne de [cyber-sécurité](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) de l’établissement d’un établissement scolaire de contrôle de la sécurité fournit d’excellents conseils sur l’établissement d’une culture forte de sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage. 

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

|Concept  |Ressources  |
|---------|---------|
|Microsoft 365     |[Parcours d’apprentissage personnalisables](https://docs.microsoft.com/office365/customlearning/) <p>Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs finaux de votre organisation.        |
|Sécurité Microsoft 365 |[Module d’apprentissage : sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](https://docs.microsoft.com/learn/modules/security-with-microsoft-365) <p>Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité. |
|Authentification multifacteur     | [Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](https://docs.microsoft.com/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au niveau de votre organisation.    |

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’prendre les mesures décrites dans cet article : Protéger votre compte et vos appareils contre les pirates [informatiques et les programmes malveillants.](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx) Ces actions incluent :
- Utilisation de mots de passe forts
- Protection des appareils 
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non utilisés)
    
Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en prenant les mesures recommandées dans les articles suivants :
- [Protéger votre compte de Outlook.com de messagerie](https://support.microsoft.com/office/help-protect-your-outlook-com-email-account-a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)
- [Protéger votre compte Gmail avec la vérification en deux étapes](https://go.microsoft.com/fwlink/?linkid=2015688&amp;clcid=0x409)
