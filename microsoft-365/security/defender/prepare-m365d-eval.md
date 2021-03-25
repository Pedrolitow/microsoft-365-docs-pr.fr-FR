---
title: Préparer votre environnement de laboratoire d’essai Microsoft 365 Defender
description: Préparer la signature des parties prenantes, les chronologies, les considérations sur l’environnement et l’ordre d’adoption lors de la configuration de votre laboratoire d’essai ou de votre environnement pilote Microsoft 365 Defender
keywords: Version d’évaluation MTP, préparation du pilote MTP, préparation pour l’exécution d’un projet pilote MTP, exécuter un projet pilote MTP, déployer, préparer, parties prenantes, chronologie, environnement, point de terminaison, serveur, gestion, adoption
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: f0e0bf29068bea0f213f8b00403213969f5b9106
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51066750"
---
# <a name="prepare-your-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Préparer votre laboratoire d’essai ou votre environnement pilote Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La création d’un laboratoire d’évaluation ou d’un environnement pilote Microsoft 365 Defender et son déploiement sont un processus en trois phases :

|![Phase 1 : Préparer](../../media/phase-diagrams/prepare.png)<br/>Phase 1 : Préparer |[![Phase 2 : Configurer](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Phase 2 : Configurer](setup-m365deval.md) |[![Phase 3 : Intégration](../../media/phase-diagrams/onboard.png)](config-m365d-eval.md)<br/>[Phase 3 : Intégration](config-m365d-eval.md) | [![Retour au pilote](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Retour au manuel pilote](m365d-pilot.md) |
|--|--|--|--|
|*Vous êtes là !* | || |

Vous êtes actuellement en phase de préparation.


La préparation est essentielle pour tout déploiement réussi. Cette section vous guide à travers ce que vous devez prendre en compte lorsque vous vous préparez à créer un laboratoire d’essai ou un environnement pilote pour votre déploiement de Microsoft 365 Defender.

## <a name="prerequisites"></a>Prerequisites
Découvrez les licences, la configuration matérielle et logicielle requise et d’autres paramètres de configuration pour mettre en service et utiliser Microsoft 365 Defender. Consultez les conditions minimales requises pour [Microsoft 365 Defender,](https://docs.microsoft.com/microsoft-365/security/defender/prerequisites) [Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements)pour le point de terminaison, Microsoft Defender pour Office [365,](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) [Microsoft Defender pour](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites)l’identité, Microsoft Cloud App [Security](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>Parties prenantes et sign-off
Identifiez toutes les parties prenantes impliquées dans le projet et celles qui peuvent avoir besoin de se signer, de réviser ou de rester informées, que ce soit pour l’évaluation ou l’exécution d’un projet pilote.

>[!NOTE]
>Toutes les organisations ne peuvent pas avoir la maturité de l’organisation de sécurité pour avoir ces rôles. Dans ce cas, consultez votre équipe de direction sur les responsabilités de révision et d’approbation.

Ajoutez des parties prenantes au tableau ci-dessous, le cas échéant, pour votre organisation.

-   SO = Sign-off on this project

-   R = Examiner ce projet et fournir une entrée

-   I = Informé de ce projet

| Nom                 | Role                                                                                                                                                                                                          | Action |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| Entrer un nom et un e-mail | Responsable de la sécurité des informations **(CISO)** Représentant exécutif qui sert de sponsor au sein de l’organisation *pour le déploiement de nouvelles technologies.*                                                  | SO     |
| Entrer un nom et un e-mail | Responsable du Centre des opérations de cybersécurité **(CDOC)** Représentant de l’équipe CDOC responsable de la définition de la façon dont cette modification est alignée sur les processus de l’équipe des opérations de sécurité des *clients.*       | SO     |
| Entrer un nom et un e-mail | **Architecte de sécurité** Un représentant de l’équipe de sécurité responsable de la définition de la façon dont cette modification est alignée sur l’architecture de sécurité principale *de l’organisation.*                         | R      |
| Entrer un nom et un e-mail | **Architecte de l’espace** de travail Un représentant de l’équipe en charge de la définition de la façon dont cette modification est alignée sur l’architecture de l’espace de travail *principal de l’organisation.*                             | R      |
| Entrer un nom et un e-mail | **Analyste de sécurité** Représentant de l’équipe CDOC qui peut fournir des commentaires sur les fonctionnalités de détection, l’expérience utilisateur et l’utilité globale de ce changement du point de vue des *opérations de sécurité.* | I      |

## <a name="prepare-your-azure-active-directory"></a>Préparer votre Azure Active Directory
Ignorez cette étape si vous avez déjà activé la synchronisation entre Active Directory et Azure Active Directory en local. Consulter la documentation des meilleures pratiques existante à partir d’Azure Active Directory. Les étapes suivantes sont optimisées pour évaluer ou exécuter un projet Pilote Microsoft 365 Defender.

1. Go to the [Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade) portal > **Azure AD Connect**. 
![Image de la page du portail Azure Active Directory](../../media/mtp-eval-1.png) <br> 

2. Cliquez **sur Télécharger** à partir de Microsoft Azure Active **Directory Connect et** transférez-le à votre contrôleur de domaine.
![Image de la page de téléchargement Azure Active Directoru Connect](../../media/mtp-eval-2.png) <br>

3. Sur le contrôleur de domaine, suivez l’Assistant Azure Active Directory Connect. Lisez les termes du contrat de licence et la notification de confidentialité, puis cochez la case si vous acceptez. Cliquez sur **Continuer**.
![Image de la page d’accueil d’Azure AD Connect](../../media/mtp-eval-3.png) <br>

4. Accédez à **Paramètres Express.**
![Image de la page Paramètres express](../../media/mtp-eval-4.png) <br>

5. Entrez vos informations d’identification d’administrateur général. Cliquez sur **Suivant**.
![Image de la page Connexion à Azure AD dans laquelle vous devez entrer vos informations d’identification d’administrateur général](../../media/mtp-eval-5.png) <br>

6. Entrez vos informations d’identification d’administrateur d’entreprise des services de domaine Active Directory. Cliquez sur **Suivant**.
![Image de la page Se connecter à AD DS où vous devez entrer vos informations d’identification](../../media/mtp-eval-6.png) <br>

7. Cliquez **sur Installer** pour confirmer la configuration.
![Image de la page de confirmation de configuration](../../media/mtp-eval-7.png) <br>

8. Félicitations, vous avez correctement configuré Azure Active Directory Connect.
![Image d’une page Azure Active Directory Connect correctement configurée](../../media/mtp-eval-8.png) <br>

Vous pouvez désormais [ajouter des utilisateurs et des groupes à Active Directory](/azure-advanced-threat-protection/atp-playbook-setup-lab#bkmk_hydrate) et [configurer une stratégie SAM-R.](/azure-advanced-threat-protection/atp-playbook-setup-lab#configure-sam-r-capabilities-from-contosodc)  


## <a name="configuration-order"></a>Ordre de configuration
Le tableau suivant indique l’ordre recommandé par Microsoft pour configurer les composants Microsoft 365 Defender pour le déploiement de votre laboratoire d’essai ou de votre environnement pilote.

| Composant                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Classement de l’ordre de configuration |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
|Microsoft Defender pour Office 365|Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. <br> [Pour en savoir plus.](/microsoft-365/security/defender-365-security/defender-for-office-365)                                                                                                                                                                                                                                             | 1                   |
|Microsoft Defender pour Identity|Microsoft Defender pour l’identité utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. <br> [En savoir plus](/azure-advanced-threat-protection/).| 2 |
|Microsoft Cloud App Security| Microsoft Cloud App Security est un courtier de sécurité d’accès au cloud (CASB) qui opère sur plusieurs clouds. Il offre une visibilité enrichie, un contrôle sur les déplacements de données et des analyses sophistiquées pour identifier et lutter contre les cybermenaces dans tous vos services cloud. <br> [En savoir plus](/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                   |
|Microsoft Defender pour point de terminaison | Les fonctionnalités de détection et de réponse de Microsoft Defender pour point de terminaison assurent des détections avancées des attaques en quasi temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces. <br> [Pour en savoir plus.](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                    |                                                                                                                                                                                                                                    

## <a name="next-step"></a>Étape suivante
|![Phase 2 : Installation](../../media/setup.png) <br>[Phase 2 : Installation](setup-m365deval.md) | Configurer votre laboratoire d’essai ou votre environnement pilote Microsoft 365 Defender
|:-------|:-----|
