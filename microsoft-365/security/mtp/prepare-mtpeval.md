---
title: Préparer votre environnement de laboratoire d’évaluation de la protection contre les menaces Microsoft
description: Préparation de la signature des parties prenantes, des délais, des considérations environnementales et de l’ordre d’adoption lors de la configuration de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection
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
- m365solution-evalutatemtp
ms.topic: article
ms.openlocfilehash: ac60415f38644c4630a181b1c8d696acced57ded
ms.sourcegitcommit: 9d8d071659e662c266b101377e24549963e43fef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "48368000"
---
# <a name="prepare-your-microsoft-threat-protection-trial-lab-or-pilot-environment"></a>Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Protection Microsoft contre les menaces

La création d’un laboratoire de test Microsoft Threat Protection ou d’un environnement pilote et son déploiement est un processus en trois phases :

<br>
<table border="0" width="100%" align="center">
  <tr style="text-align:center;">
    <td align="center" style="width:25%; border:0;" bgcolor="#d5f5e3">
      <a href= "https://docs.microsoft.com/microsoft-365/security/mtp/prepare-mtpeval"> 
        <img src="../../media/prepare.png" alt="Prepare your Microsoft Threat Protection trial lab environment" title="Préparation de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection" />
      <br/>Phase 1 : préparer </a><br>
    </td>
     <td align="center"  >
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/setup-mtpeval">
        <img src="../../media/setup.png" alt="Set up your Microsoft Threat Protection trial lab environment" title="Configuration de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection" />
      <br/>Phase 2 : configuration </a><br>
        </td>
    <td align="center">
      <a href="https://docs.microsoft.com/microsoft-365/security/mtp/config-mtpeval">
        <img src="../../media/config-onboard.png" alt="Configure each Microsoft Threat Protection pillar" title="Configurer chaque pilier de protection contre les menaces Microsoft et intégrer vos points de terminaison" />
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


La préparation est essentielle à tout déploiement réussi. Cette section vous guidera tout au long de ce que vous devez prendre en compte lors de la préparation de la création d’un laboratoire d’évaluation ou d’un environnement pilote pour votre déploiement de la protection contre les menaces Microsoft.

## <a name="prerequisites"></a>Conditions préalables
Découvrez la gestion des licences, la configuration matérielle et logicielle requise, ainsi que d’autres paramètres de configuration pour mettre en service et utiliser la protection contre les menaces Microsoft. Voir la configuration minimale requise pour la [protection contre les menaces Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites), [Microsoft Defender atp](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements), [Office 365 ATP](https://docs.microsoft.com/office365/servicedescriptions/office-365-advanced-threat-protection-service-description), [Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites), [sécurité des applications Cloud Microsoft](https://docs.microsoft.com/azure-advanced-threat-protection/atp-prerequisites).

## <a name="stakeholders-and-sign-off"></a>Parties prenantes et déconnexion
La section suivante permet d’identifier toutes les parties prenantes impliquées dans le projet et qui peuvent avoir besoin de se déconnecter, de consulter ou de rester informées, qu’elles soient destinées à l’évaluation ou à l’exécution d’un projet pilote.

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
| Entrer le nom et l’adresse de messagerie | **Analyste** *de la sécurité un représentant de l’équipe Cdoc qui peut fournir des informations sur les fonctionnalités de détection, l’expérience utilisateur et l’utilité globale de cette modification du point de vue des opérations de sécurité.* | I      |

## <a name="prepare-your-azure-active-directory"></a>Préparation de votre Azure Active Directory
Ignorez cette étape si vous avez déjà activé la synchronisation entre Active Directory et Azure Active Directory sur site. Consultez la documentation sur les meilleures pratiques existantes à partir d’Azure Active Directory. Les étapes suivantes sont optimisées pour évaluer ou exécuter un projet pilote de protection Microsoft contre les menaces.

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
Le tableau ci-dessous indique l’ordre dans lequel Microsoft recommande de configurer les composants de protection contre les menaces Microsoft pour votre déploiement d’essai ou d’environnement pilote.

| Composant                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Classement de la commande de configuration |
|-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| Office 365 – Protection avancée contre les menaces| Office 365 ATP protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. <br> [Pour en savoir plus.](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp)                                                                                                                                                                                                                                             | 1                    |
|Azure Advanced Threat Protection|Azure ATP utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. <br> [En savoir plus](https://docs.microsoft.com/azure-advanced-threat-protection/).| 2  |
|Microsoft Cloud App Security| La sécurité des applications Cloud Microsoft est un courtier en matière de sécurité d’accès au Cloud (CASB) qui fonctionne sur plusieurs nuages. Il offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre Cyber dans tous vos services Cloud. <br> [En savoir plus](https://docs.microsoft.com/cloud-app-security/).                                                                                                                                                                                                                                                                                                                                                                       |3                    |
|Microsoft Defender – Protection avancée contre les menaces | Les fonctionnalités de détection et de réponse des points de terminaison de Microsoft Defender – Protection avancée contre les menaces assurent des détections avancées des attaques en quasi temps réel et exploitables. Les analystes de la sécurité peuvent hiérarchiser efficacement les alertes, avoir une meilleure visibilité de l’ampleur d’une faille et prendre des mesures correctives pour remédier aux menaces. <br> [Pour en savoir plus.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)                                     |4                    |                                                                                                                                                                                                                                    

## <a name="next-step"></a>Étape suivante
|![Phase 2 : configuration](../../media/setup.png) <br>[Phase 2 : configuration](setup-mtpeval.md) | Configuration de votre laboratoire d’évaluation ou de votre environnement pilote Microsoft Threat Protection
|:-------|:-----|

