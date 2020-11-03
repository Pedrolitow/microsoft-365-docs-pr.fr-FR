---
title: Préparation de votre environnement de laboratoire de test Microsoft 365 Defender
description: Préparer la signature des parties prenantes, les délais, les considérations environnementales et l’ordre d’adoption lors de la configuration de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender
keywords: Préparation de la version d’évaluation MTP, préparation du pilote MTP, préparation de l’exécution d’un projet pilote MTP, exécution d’un projet pilote MTP, déploiement, préparation, partie prenante, chronologie, environnement, point de terminaison, serveur, gestion, adoption
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.openlocfilehash: a255c74db030325ba22c2095fba732a93b8c269c
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48844847"
---
# <a name="prepare-your-microsoft-365-defender-trial-lab-or-pilot-environment"></a>Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

La création d’un laboratoire de test Microsoft 365 Defender ou d’un environnement pilote et son déploiement est un processus en trois phases :

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" bgcolor="#d5f5e3">
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval"> 
        <img src="../../media/prepare.png" alt="Prepare your Microsoft 365 Defender trial lab environment" title="Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft 365 Defender" />
      <br/>Phase 1 : préparer </a><br>
    </td>
     <td align="center"  >
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/setup-mtpeval">
        <img src="../../media/setup.png" alt="Set up your Microsoft 365 Defender trial lab environment" title="Configuration de votre laboratoire d’évaluation Microsoft 365 Defender ou de votre environnement pilote" />
      <br/>Phase 2 : configuration </a><br>
        </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/config-mtpeval">
        <img src="../../media/config-onboard.png" alt="Configure each Microsoft 365 Defender pillar" title="Configurer chaque pilier de Microsoft 365 Defender et intégrer vos points de terminaison" />
      <br/>Phase 3 : configurer & Onboard</a><br>
</td>
  </tr>
  <tr>
    <td style="width:25%; border:0;">
   
    </td>
    <td valign="top" style="width:25%; border:0;">
    
</td>
    <td valign="top" style="width:25%; border:0;">

</td>    
  </tr>
</table>

Vous êtes actuellement en phase de préparation.


La préparation est essentielle à tout déploiement réussi. Cette section vous guidera tout au long de ce que vous devez prendre en compte lors de la préparation de la création d’un laboratoire d’évaluation ou d’un environnement pilote pour votre déploiement de Microsoft 365 Defender.

## <a name="prerequisites"></a>Conditions préalables
Découvrez la gestion des licences, la configuration matérielle et logicielle requise, ainsi que d’autres paramètres de configuration pour mettre en service et utiliser Microsoft 365 Defender. Reportez-vous à la configuration minimale requise pour [microsoft 365 Defender](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites), [Microsoft Defender pour les points de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements), [Microsoft Defender pour Office 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description), [Microsoft Defender for Identity](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites), [Microsoft Cloud App Security](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>Parties prenantes et déconnexion
Identifiez toutes les parties prenantes impliquées dans le projet et qui peuvent avoir besoin d’être déconnectées, vérifiées ou restez informées, qu’elles soient destinées à l’évaluation ou à l’exécution d’un projet pilote.

>[!NOTE]
>Toutes les organisations n’ont pas la maturité de l’organisation de sécurité pour avoir ces rôles. Dans ce cas, consultez votre équipe de direction sur la révision et l’approbation de responsabilités.

Ajoutez des parties prenantes dans le tableau ci-dessous selon les besoins de votre organisation.

-   SO = se déconnecter de ce projet

-   R = examiner ce projet et fournir des informations

-   I = informé de ce projet

| Nom                 | Role                                                                                                                                                                                                          | Action |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|
| Entrer le nom et l’adresse de messagerie | **Directeur de la sécurité des informations (CISO)** *un représentant exécutif qui sert de sponsor au sein de l’Organisation pour le déploiement de la nouvelle technologie.*                                                  | C'     |
| Entrer le nom et l’adresse de messagerie | **Directeur du centre d’opérations Cyber Defense (Cdoc)** *représentant de l’équipe Cdoc chargée de définir la manière dont cette modification est alignée sur les processus de l’équipe des opérations de sécurité des clients.*       | C'     |
| Entrer le nom et l’adresse de messagerie | **Architecte de la sécurité** *un représentant de l’équipe de sécurité chargé de définir le mode d’alignement de cette modification avec l’architecture de sécurité de base dans l’organisation.*                         | R      |
| Entrer le nom et l’adresse de messagerie | **Architecte de travail** *un représentant de l’équipe informatique chargée de définir la manière dont cette modification est alignée sur l’architecture de l’espace de travail de base dans l’organisation.*                             | R      |
| Entrer le nom et l’adresse de messagerie | **Analyste** *de la sécurité un représentant de l’équipe Cdoc qui peut fournir des commentaires sur les capacités de détection, l’expérience utilisateur et l’utilité globale de cette modification du point de vue des opérations de sécurité.* | I      |

## <a name="prepare-your-azure-active-directory"></a>Préparation de votre Azure Active Directory
Ignorez cette étape si vous avez déjà activé la synchronisation entre Active Directory et Azure Active Directory sur site. Consultez la documentation sur les meilleures pratiques existantes à partir d’Azure Active Directory. Les étapes suivantes sont optimisées pour évaluer ou exécuter un projet pilote Microsoft 365 Defender.

1. Accédez au portail [Azure Active Directory](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade) > **Azure ad Connect**. 
![Image de la page du portail Azure Active Directory](../../media/mtp-eval-1.png) <br> 

2. Cliquez sur **Télécharger** à partir de **Microsoft Azure Active Directory Connect** et transférez-le à votre contrôleur de domaine.
![Image de la page de téléchargement d’Azure active DIRECTORI Connect](../../media/mtp-eval-2.png) <br>

3. Sur le contrôleur de domaine, suivez l’Assistant Connexion Azure Active Directory. Lisez les termes du contrat de licence et la déclaration de confidentialité, puis cochez la case si vous acceptez. Cliquez sur **Continuer**.
![Image de la page d’accueil Azure AD Connect](../../media/mtp-eval-3.png) <br>

4. Accédez à **paramètres rapides**.
![Image de la page Paramètres Express](../../media/mtp-eval-4.png) <br>

5. Entrez vos informations d’identification d’administrateur général. Cliquez sur **Suivant**.
![Image de la page connexion à Azure AD où vous devez entrer vos informations d’identification d’administrateur général](../../media/mtp-eval-5.png) <br>

6. Entrez vos informations d’identification d’administrateur d’entreprise des services de domaine Active Directory. Cliquez sur **Suivant**.
![Image de la page connexion à AD DS où vous devez entrer vos informations d’identification](../../media/mtp-eval-6.png) <br>

7. Cliquez sur **installer** pour confirmer la configuration.
![Image de la page de confirmation de configuration](../../media/mtp-eval-7.png) <br>

8. Félicitations, vous avez réussi à configurer Azure Active Directory Connect.
![Image d’une page Azure Active Directory Connect correctement configurée](../../media/mtp-eval-8.png) <br>

Vous pouvez désormais [Ajouter des utilisateurs et des groupes à Active Directory](https://docs.microsoft.com/azure-advanced-threat-protection/atp-playbook-setup-lab#bkmk_hydrate) et [configurer une stratégie Sam-R](https://docs.microsoft.com/azure-advanced-threat-protection/atp-playbook-setup-lab#configure-sam-r-capabilities-from-contosodc).  


## <a name="configuration-order"></a>Ordre de configuration
Le tableau suivant indique l’ordre recommandé par Microsoft pour la configuration des composants Microsoft 365 Defender pour votre laboratoire d’évaluation ou votre déploiement d’environnement pilote.

| Composant                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Classement de la commande de configuration |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
|Microsoft Defender pour Office 365|Microsoft Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. <br> [Pour en savoir plus.](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)                                                                                                                                                                                                                                             | 0,1                   |
|Microsoft Defender pour l’identité|Microsoft Defender for Identity utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. <br> [En savoir plus](https://docs.microsoft.com/azure-advanced-threat-protection/).| n°2 |
|Microsoft Cloud App Security| La sécurité des applications Cloud Microsoft est un courtier en matière de sécurité d’accès au Cloud (CASB) qui fonctionne sur plusieurs nuages. Il offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre Cyber dans tous vos services Cloud. <br> [En savoir plus](https://docs.microsoft.com/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                   |
|Microsoft Defender pour point de terminaison | Microsoft Defender pour les fonctionnalités de détection et de réponse de point de terminaison de point de terminaison fournit des détections d’attaques avancées qui sont quasiment en temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces. <br> [Pour en savoir plus.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                    |                                                                                                                                                                                                                                    

## <a name="next-step"></a>Étape suivante
|![Phase 2 : configuration](../../media/setup.png) <br>[Phase 2 : configuration](setup-mtpeval.md) | Configuration de votre laboratoire d’évaluation Microsoft 365 Defender ou de votre environnement pilote
|:-------|:-----|

