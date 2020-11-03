---
title: Étapes à suivre pour configurer les fonctionnalités de protection contre les menaces dans Microsoft 365
description: Découvrez comment déployer les services et les fonctionnalités de protection contre les menaces à travers Microsoft 365 E5.
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365solution-threatprotection
- m365solution-scenario
ms.custom: ''
f1.keywords: NOCSH
ms.openlocfilehash: f3fa5c82efad0a51adf5e798bd89860e78256e15
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48845311"
---
# <a name="configure-threat-protection-capabilities-across-microsoft-365"></a>Configurer les fonctionnalités de protection contre les menaces dans Microsoft 365

Suivez les étapes ci-dessous pour configurer la protection contre les menaces sur Microsoft 365.


## <a name="step-1-set-up-multi-factor-authentication-and-conditional-access-policies"></a>Étape 1 : configurer l’authentification multifacteur et les stratégies d’accès conditionnel

[L’authentification multifacteur](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) (MFA) exige que les utilisateurs vérifient leur identité auprès d’un appel téléphonique ou d’une application d’authentificateur. Les [stratégies d’accès conditionnel](https://docs.microsoft.com/azure/active-directory/conditional-access/overview) définissent certaines exigences qui doivent être satisfaites pour permettre aux utilisateurs d’accéder aux applications et aux données dans Microsoft 365. Les stratégies MFA et d’accès conditionnel fonctionnent conjointement pour protéger votre organisation. Par exemple, si une personne tente de se connecter à partir d’un appareil mobile à l’aide d’un compte qui n’est pas activé pour l’authentification multifacteur et qu’une stratégie d’accès conditionnel exige l’application de l’authentification multifacteur, il ne pourra pas se connecter.  

Microsoft a testé et recommande un ensemble spécifique d’accès conditionnel et de stratégies associées pour protéger l’accès à toutes les applications SaaS, en particulier Microsoft 365. Les stratégies sont recommandées pour la protection des données de référence, sensibles et hautement réglementées. Commencez par implémenter les stratégies pour la protection de base. 


[ ![ Stratégies courantes de configuration de l’identité et de l’accès aux appareils](../media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png) 
 [voir une version plus grande de cette image](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/microsoft-365-policies-configurations/Identity_device_access_policies_byplan.png)

### <a name="to-implement-baseline-protection-for-microsoft-365"></a>Pour implémenter la protection de base pour Microsoft 365

![Processus de déploiement de la protection de base](../media/solutions-architecture-center/deploy-threat-protection-identity-access-steps.png) 

1. [Configurez les composants requis, y compris Azure Identity Protection](../security/office-365-security/identity-access-prerequisites.md).
2. [Configurez les stratégies courantes d’identité et d’accès aux appareils](../security/office-365-security/identity-access-policies.md) pour la protection de base.
3. Configurez [les stratégies pour les utilisateurs invités](../security/office-365-security/identity-access-policies-guest-access.md), [Microsoft teams](../security/office-365-security/teams-access-policies.md), [Exchange Online](../security/office-365-security/secure-email-recommended-policies.md)et [OneDrive](../security/office-365-security/sharepoint-file-access-policies.md).

### <a name="more-information-about-protecting-identities"></a>Plus d’informations sur la protection des identités

- [Configurations des identités et de l’accès aux appareils](../security/office-365-security/microsoft-365-policies-configurations.md)
- [Conseils de sécurité pour Azure MFA](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication-security-best-practices)

## <a name="step-2-configure-microsoft-defender-for-identity"></a>Étape 2 : configurer Microsoft Defender pour l’identité

[Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) est une solution de sécurité basée sur le Cloud qui fonctionne avec vos signaux [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-whatis) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation.

Microsoft Defender for Identity permet aux analystes et aux professionnels de la sécurité des opérations de sécurité (SECOPS) de détecter les attaques avancées dans les environnements hybrides :
- Surveiller les utilisateurs, le comportement de l’entité et les activités à l’aide d’une analyse basée sur l’apprentissage.
- Protéger les identités des utilisateurs et informations d’identification stockées dans Active Directory.
- Identifier et examiner les activités suspectes des utilisateurs et les attaques avancées tout au long de la chaîne de terminaison.
- Fournir des informations claires sur les incidents reposant sur une chronologie simple pour un triage rapide.

### <a name="to-set-up-microsoft-defender-for-identity"></a>Pour configurer Microsoft Defender pour l’identité

![Processus de déploiement de Microsoft Defender pour l’identité](../media/solutions-architecture-center/deploy-azure-atp-steps.png) 

1. [Configurez Microsoft Defender pour l’identité](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1) afin de protéger vos environnements principaux.
2. Protégez tous vos [contrôleurs de domaine](https://docs.microsoft.com/azure-advanced-threat-protection/atp-sensor-monitoring) et [forêts](https://docs.microsoft.com/azure-advanced-threat-protection/atp-multi-forest).
3. Intégrez [Microsoft Defender pour les alertes d’identité](https://docs.microsoft.com/azure-advanced-threat-protection/suspicious-activity-guide?tabs=external) dans votre flux de travail des opérations de sécurité (SECOPS).

### <a name="more-information-about-microsoft-defender-for-identity"></a>Plus d’informations sur Microsoft Defender pour l’identité

- [Qu’est-ce que Microsoft Defender pour l’identité ?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)
- [Vidéo : introduction à Microsoft Defender pour l’identité](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- [Microsoft Defender pour le déploiement d’identité](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="step-3-turn-on-microsoft-365-defender"></a>Étape 3 : activer Microsoft 365 Defender

[Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) combine les fonctionnalités dans une solution unique. Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent associer les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace ; la manière dont il entre dans l’environnement, ce qu’il est affecté et la façon dont il influe actuellement sur l’organisation. Microsoft 365 Defender effectue une action automatique pour empêcher ou bloquer les boîtes aux lettres affectées, les points de terminaison et les identités des utilisateurs concernés.

Microsoft 365 Defender unifie les alertes, les incidents, l’analyse et la réponse automatiques, ainsi que la recherche avancée sur les charges de travail (Microsoft Defender for Identity, Microsoft Defender for Office 365, Microsoft Defender for Endpoint et Microsoft Cloud App Security) dans un seul volet d’expérience. Une fois que vous avez configuré un ou plusieurs de vos services Defender pour Office 365, activez Microsoft 365 Defender. De nouvelles fonctionnalités sont ajoutées en permanence à Microsoft 365 Defender ; envisagez d’opter pour recevoir des fonctionnalités d’aperçu.

### <a name="to-set-up-microsoft-365-defender"></a>Pour configurer Microsoft 365 Defender

![Processus de déploiement de Microsoft 365 Defender](../media/solutions-architecture-center/deploy-mtp-steps.png) 

1. [Passez en revue les conditions préalables](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites).
2. [Activez Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable).
3. [Abonnez-vous aux fonctionnalités d’aperçu](https://docs.microsoft.com/microsoft-365/security/mtp/preview).

### <a name="more-information-about-microsoft-365-defender"></a>Plus d’informations sur Microsoft 365 Defender

- [Qu’est-ce que Microsoft 365 Defender ?](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection)
- [Nouveautés de Microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/whats-new)

## <a name="step-4-configure-microsoft-defender-for-office-365"></a>Étape 4 : configurer Microsoft Defender pour Office 365

[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) protège votre organisation contre les menaces malveillantes dans les messages électroniques (pièces jointes et URL), les documents Office et les outils de collaboration. Le tableau suivant répertorie les fonctionnalités et les fonctionnalités de Microsoft Defender pour Office 365 incluses dans Microsoft 365 E5 :

|Fonctionnalités de configuration, de protection et de détection|Fonctionnalités d’automatisation, d’enquête, de correction et d’éducation|
|---|---|
|[Pièces jointes fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-attachments)<br/>[Liens fiables](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-safe-links)<br/>[Documents sécurisés](https://docs.microsoft.com/microsoft-365/security/office-365-security/safe-docs)<br/>[ATP pour SharePoint, OneDrive et Microsoft Teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/atp-for-spo-odb-and-teams)<br/>[Anti-hameçonnage dans Defender pour la protection d’Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/set-up-anti-phishing-policies#exclusive-settings-in-atp-anti-phishing-policies)|[Suivi des menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-trackers)<br/>[Threat Explorer](https://docs.microsoft.com/microsoft-365/security/office-365-security/threat-explorer)<br/>[Examen et réponse automatisés](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air)<br/>[Simulateur d’attaques](https://docs.microsoft.com/microsoft-365/security/office-365-security/attack-simulator)|
|

Avec Microsoft Defender pour Office 365, les personnes de votre organisation peuvent communiquer et collaborer de manière plus sécurisée, grâce à la protection contre les menaces pour leur contenu de messagerie et leurs documents Office.

### <a name="to-set-up-microsoft-defender-for-office-365"></a>Pour configurer Microsoft Defender pour Office 365

![Processus de déploiement de Microsoft Defender pour Office 365](../media/solutions-architecture-center/deploy-office365-atp-steps.png) 

1. [Installez et configurez vos stratégies Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats).
2. [Affichez et utilisez votre Microsoft Defender pour les rapports Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/view-reports-for-atp).
3. [Utiliser les fonctionnalités d’enquête et de réponse aux menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-ti).

### <a name="more-information-about-microsoft-defender-for-office-365"></a>Plus d’informations sur Microsoft Defender pour Office 365

- [Vue d’ensemble de Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)
- [Nouveautés de Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/whats-new-in-office-365-atp)

## <a name="step-5-configure-microsoft-defender-for-endpoint"></a>Étape 5 : configurer Microsoft Defender pour le point de terminaison

[Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection) protège les appareils de votre organisation (également appelés points de terminaison) de cyber, les attaques avancées et les violations de données. Les équipes de sécurité peuvent être plus efficaces pour gérer la sécurité de leurs points de terminaison. Des outils puissants aident les organisations à suivre les systèmes dépourvus de correctifs à l’aide de la détection de vulnérabilité avec la [gestion des menaces et des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt). Les fonctionnalités de détection et de correction automatisées, telles que la réduction de la [surface d’attaque](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction), la [protection nouvelle génération](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10), la [détection et la réponse du point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response), ainsi que l’analyse et la [Correction automatisées](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations) vous aident à protéger vos appareils contre les programmes malveillants. En plus de ces fonctionnalités, les clients peuvent obtenir des notifications proactives et consulter les experts Microsoft Threat à la demande, dans le cadre du service de chasse à la responsabilité gérée. 


### <a name="set-up-microsoft-defender-for-endpoint"></a>Configurer Microsoft Defender pour le point de terminaison

![Processus de déploiement de Microsoft Defender pour le point de terminaison](../media/solutions-architecture-center/deploy-mdatp-steps.png) 

1. [Préparez votre déploiement de Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/deployment-phases).
2. [Configurer votre Microsoft Defender pour le déploiement du point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/micros.oft-defender-atp/production-deployment)
3. [Intégré à Microsoft Defender pour le service de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/onboarding).
4. [Effectuez les principales tâches d’administration de la sécurité](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation).

### <a name="more-information-about-microsoft-defender-for-endpoint"></a>Plus d’informations sur Microsoft Defender pour le point de terminaison

- [En savoir plus sur Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection).
- [Essayez l’atelier d’évaluation de Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/evaluation-lab).

## <a name="step-6-configure-microsoft-cloud-app-security"></a>Étape 6 : configurer la sécurité des applications Cloud Microsoft

[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security) est un courtier de sécurité d’accès au Cloud qui prend en charge la collecte de journaux, les connecteurs d’API et le proxy inverse. Microsoft Cloud App Security offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre Cyber dans tous vos services Cloud. Avec Microsoft Cloud App Security, vos opérations de sécurité peuvent protéger les informations sensibles de votre organisation, se protéger contre les cyber et les anomalies, découvrir et surveiller les applications qui accèdent aux données de votre organisation, et vous assurer que les applications Cloud de votre organisation répondent aux exigences de conformité.

### <a name="set-up-microsoft-cloud-app-security"></a>Configuration de la sécurité des applications Cloud Microsoft

![Processus de déploiement de la sécurité des applications Cloud Microsoft](../media/solutions-architecture-center/deploy-mcas-steps.png) 

1. [Configurez le portail et d’autres exigences de base](https://docs.microsoft.com/cloud-app-security/general-setup).
2. [Configurez la détection](https://docs.microsoft.com/cloud-app-security/set-up-cloud-discovery) sur le Cloud et les [applications de connexion](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).
3. [Déployer le contrôle d’application d’accès conditionnel pour les applications proposées](https://docs.microsoft.com/cloud-app-security/proxy-deployment-aad).
4. [Utiliser les outils d’enquête et les tableaux de bord](https://docs.microsoft.com/cloud-app-security/investigate).

### <a name="more-information-about-microsoft-cloud-app-security"></a>Rubrique relative aux informations supplémentaires concernant Microsoft Cloud App Security

- [Passez en revue les nouvelles fonctionnalités et](https://docs.microsoft.com/cloud-app-security/release-notes)fonctionnalités.
- [En savoir plus sur la sécurité des applications Cloud de Microsoft](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security).

## <a name="step-7-monitor-status-and-take-actions"></a>Étape 7 : surveiller l’État et prendre des mesures

Une fois que vous avez configuré et déployé vos services et fonctionnalités de protection contre les menaces, l’étape suivante consiste à surveiller les détections de menaces et à prendre les mesures appropriées. Le meilleur point de départ est le centre de sécurité Microsoft 365 ( [https://security.microsoft.com](https://security.microsoft.com) ), où vous pouvez surveiller et gérer la sécurité dans vos identités, données, périphériques, applications et infrastructure Microsoft. 

![Centre de sécurité Microsoft 365](../media/solutions-architecture-center/m365-security-center.png)

Le centre de sécurité Microsoft 365 est spécifiquement destiné aux équipes de sécurité et aux administrateurs de sécurité. Dans le centre de sécurité Microsoft 365, vous pouvez :
- Afficher l’état de sécurité global de votre organisation avec le [score sécurisé](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score).
- [Surveillez et affichez des rapports](https://docs.microsoft.com/microsoft-365/security/mtp/monitoring-and-reporting) sur l’état de vos identités, données, périphériques, applications et infrastructure.
- Reliez les points sur les alertes par le biais d' [incidents](https://docs.microsoft.com/microsoft-365/security/mtp/incident-queue).
- Utilisez l’analyse [et la correction automatisées](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-autoir) pour résoudre les menaces.
- [Recherche proactive de menaces](https://docs.microsoft.com/microsoft-365/security/mtp/advanced-hunting-overview), telles que des tentatives d’intrusion ou une activité de violation affectant votre courrier électronique, vos données, vos périphériques et vos identités.
- [Comprenez les dernières campagnes](https://docs.microsoft.com/microsoft-365/security/mtp/latest-attack-campaigns) et techniques d’attaque avec l’analyse des menaces.
- ... et bien plus encore !

### <a name="more-information-about-the-microsoft-365-security-center"></a>Plus d’informations sur le centre de sécurité Microsoft 365

- [Prise en main du centre de sécurité Microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/overview-security-center).
- [Surveiller et afficher les rapports](https://docs.microsoft.com/microsoft-365/security/mtp/monitoring-and-reporting).
- [Consultez les portails de sécurité dans Microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/portals).

## <a name="step-8-train-users"></a>Étape 8 : former les utilisateurs

Les utilisateurs de la formation peuvent enregistrer les utilisateurs et les opérations de sécurité de votre équipe de manière plus longue et plus frustrante. Les utilisateurs chevronnés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites Web suspects. 

Le manuel de la [campagne](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) Harvard Kennedy School Cybersecurity fournit des conseils excellents sur l’établissement d’une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage. 

Microsoft 365 fournit les ressources suivantes pour aider les utilisateurs au sein de votre organisation :

|Notion  |Ressources  |
|---------|---------|
|Microsoft 365     |[Voies de formation personnalisables](https://docs.microsoft.com/office365/customlearning/) <p>Ces ressources peuvent vous aider à réunir des formations pour les utilisateurs finaux de votre organisation.        |
|Sécurité Microsoft 365 |[Module d’apprentissage : sécurisez votre organisation à l’aide de la sécurité intégrée et intelligente de Microsoft 365](https://docs.microsoft.com/learn/modules/security-with-microsoft-365) <p>Ce module vous permet de décrire les fonctionnalités de sécurité de Microsoft 365 et d’expliquer les avantages de ces fonctionnalités de sécurité. |
|Authentification multifacteur     | [Vérification en deux étapes : qu’est-ce que la page de vérification supplémentaire ?](https://docs.microsoft.com/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Cet article permet aux utilisateurs finaux de comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au sein de votre organisation.    |

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’effectuer les actions décrites dans cet article : [protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Ces actions incluent :
- Utilisation de mots de passe forts
- Protection des appareils 
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non gérés)
    
Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en effectuant les actions recommandées dans les articles suivants :
- [Protéger votre compte de messagerie Outlook.com](https://support.microsoft.com/office/help-protect-your-outlook-com-email-account-a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)
- [Protégez votre compte Gmail à l’aide de la vérification en deux étapes](https://go.microsoft.com/fwlink/?linkid=2015688&amp;clcid=0x409)
