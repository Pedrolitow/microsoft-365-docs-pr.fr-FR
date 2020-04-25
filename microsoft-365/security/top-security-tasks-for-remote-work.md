---
title: 12 premières tâches pour les équipes de sécurité qui prennent en charge le travail à domicile
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.service: o365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- remotework
description: Protégez votre courrier électronique et vos données professionnelles contre les menaces informatiques, notamment les ransomware, le hameçonnage et les pièces jointes malveillantes.
ms.openlocfilehash: f2d76fd92ac6d439fd6400a0478028c99ae935eb
ms.sourcegitcommit: 481fb95d8b80cf2102a9c73b21e7effa79e594e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "43808847"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>12 premières tâches pour les équipes de sécurité qui prennent en charge le travail à domicile

Si vous êtes comme [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) et que vous avez soudainement besoin de prendre en charge un personnel basé principalement sur la maison, nous souhaitons vous aider à garantir le bon fonctionnement de votre organisation. Cet article donne la priorité aux tâches pour aider les équipes de sécurité à implémenter les fonctionnalités de sécurité les plus importantes aussi rapidement que possible. 

Si vous êtes une petite ou moyenne organisation à l’aide de l’un des plans d’entreprise de Microsoft, consultez plutôt ces ressources :
- [10 façons de sécuriser Office 365 et Microsoft 365 pour les offres professionnelles](../admin/security-and-compliance/secure-your-business-data.md) 
- [Microsoft 365 pour les campagnes](https://docs.microsoft.com/microsoft-365/campaigns/?view=o365-worldwide) (inclut une configuration de sécurité recommandée pour Microsoft 365 Business)

  
Pour les clients qui utilisent nos plans d’entreprise, Microsoft vous recommande d’effectuer les tâches indiquées dans le tableau suivant qui s’appliquent à votre plan de service. Si, au lieu d’acheter un plan d’entreprise Microsoft 365, vous associez des abonnements, notez ce qui suit :
- Microsoft 365 E3 inclut Enterprise Mobility + Security (EMS) E3 et Azure AD P1
- Microsoft 365 E5 inclut EMS E5 et Azure AD P2
  
||**Task**| Tous les plans Office 365 Enterprise|**Microsoft 365 E3** |**Microsoft 365 E5**|
|:-----|:-----|:-----|:-----|:-----|
|0,1      |[Activer l’authentification multifacteur Azure](#1-enable-azure-multi-factor-authentication-mfa)   |   ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)  |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)   | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      | 
|n°2     | [Se protéger contre les menaces](#2-protect-against-threats) |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png) |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)       | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)       | 
|3      |  [Configurer la protection avancée contre les menaces Office 365](#3-configure-office-365-advanced-threat-protection)  |   |      |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)     | 
|4       | [Configurer Azure Advanced Threat Protection (ATP)](#4-configure-azure-advanced-threat-protection)   |   |      |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)     | 
|5      |   [Activer la protection avancée contre les menaces Microsoft](#5-turn-on-microsoft-advanced-threat-protection)  |  |      | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      | 
|6       | [Configurer la protection des applications mobiles Intune pour les téléphones et les tablettes](#6-configure-intune-mobile-app-protection-for-phones-and-tablets) |    |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)       |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)       | 
|7      | [Configurer l’authentification MFA et l’accès conditionnel pour les invités, y compris la protection des applications Intune](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)  |    |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)     | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      | 
|8       |  [Inscrire des PC dans la gestion des appareils et exiger des PC conformes](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)   |  | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)        | ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)        | 
|9       | [Optimiser votre réseau pour la connectivité Cloud](#9-optimize-your-network-for-cloud-connectivity)  |  ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png) |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)        | 
|10    | [Former les utilisateurs](#10-train-users) |    ![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png) |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)      | 
|11  |[Pris en main de Microsoft Cloud App Security](#11-get-started-with-microsoft-cloud-app-security) |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)   |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)   |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)   |
|12  |[Surveiller les menaces et prendre des mesures](#12-monitor-for-threats-and-take-action) |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)   |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)  |![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)  |
| | | |


   
Avant de commencer, vérifiez votre [score de sécurité microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score) dans le centre de sécurité Microsoft 365. À partir d’un tableau de bord centralisé, vous pouvez surveiller et améliorer la sécurité de vos identités, données, applications, périphériques et infrastructure Microsoft 365. Vous disposez de points pour la configuration des fonctionnalités de sécurité recommandées, l’exécution de tâches liées à la sécurité (telles que l’affichage de rapports) ou l’adressage de recommandations avec une application ou un logiciel tiers. Les tâches recommandées dans cet article généreront votre score.
  
![Capture d’écran du score de sécurité Microsoft](../media/secure-score.png)
  
## <a name="1-enable-azure-multi-factor-authentication-mfa"></a>1 : activer Azure Multi-Factor Authentication (MFA)
La meilleure chose que vous pouvez faire pour améliorer la sécurité pour les employés travaillant à domicile consiste à activer l’authentification multifacteur. Si vous n’avez pas encore de processus en place, traitez-le comme un pilote d’urgence et assurez-vous que les personnes du support technique sont prêtes à aider les employés qui se bloquent. Comme vous ne pouvez pas distribuer de périphériques de sécurité matérielle, utilisez les applications d’authentification Windows Hello biométrie et Smartphone telles que Microsoft Authenticator.

Normalement, Microsoft vous recommande de donner aux utilisateurs 14 jours pour enregistrer leur appareil pour l’authentification multifacteur avant d’exiger l’authentification multifacteur. Toutefois, si votre personnel travaille soudainement à partir de chez vous, continuez et exigez la sécurité MFA comme priorité de sécurité et préparez-vous à aider les utilisateurs qui en ont besoin. 

L’application de ces stratégies ne prend que quelques minutes, mais il est prêt à prendre en charge vos utilisateurs au cours des prochains jours.  


|Offre  |Recommandation  |
|---------|---------|
|Plans Microsoft 365 (sans Azure AD P1 ou P2)     |[Activer les paramètres de sécurité par défaut dans Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Les paramètres de sécurité par défaut dans Azure AD incluent MFA pour les utilisateurs et les administrateurs.   |
|Microsoft 365 E3 (avec Azure AD P1)     | Utilisez des [stratégies d’accès conditionnel courantes](https://docs.microsoft.com/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes : <br>- [Exiger l’authentification multifacteur pour les administrateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Exiger l’authentification multifacteur pour tous les utilisateurs](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloquer l’authentification héritée](https://docs.microsoft.com/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (avec Azure AD P2)     | En tirant parti de Azure AD Identity Protection, commencez à implémenter l' [ensemble recommandé par Microsoft de l’accès conditionnel et des stratégies associées](../enterprise/identity-access-policies.md) en créant ces deux stratégies :<br> - [Exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](../enterprise/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [Bloquer les clients qui ne prennent pas en charge l’authentification moderne](../enterprise/identity-access-policies.md#block-clients-that-dont-support-modern-authentication)<br>- [Les utilisateurs à haut risque doivent changer leur mot de passe](../enterprise/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |


  
## <a name="2-protect-against-threats"></a>2 : se protéger contre les menaces

Tous les plans Microsoft 365 incluent diverses fonctionnalités de protection contre les menaces. La protection contre ces fonctionnalités ne prend que quelques minutes.
- Protection anti-programme malveillant
- Protection contre les URL et les fichiers malveillants
- Protection anti-hameçonnage
- Protection anti-courrier indésirable

Consultez la rubrique [Protégez-vous contre les menaces dans Office 365](office-365-security/protect-against-threats.md) pour obtenir des instructions que vous pouvez utiliser comme point de départ.
    

## <a name="3-configure-office-365-advanced-threat-protection"></a>3 : configurer Office 365 Advanced Threat Protection

Office 365 Advanced Threat Protection (ATP), inclus dans Microsoft 365 E5 et Office 365 E5, protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. La configuration peut prendre plusieurs heures.

Office 365 ATP :
- Protège votre organisation contre les menaces de messagerie inconnues en temps réel à l’aide de systèmes intelligents qui inspectent les pièces jointes et les liens de contenu malveillant. Ces systèmes automatisés incluent une plateforme de détonation robuste, des méthodes heuristiques et des modèles d’apprentissage automatique. 
- Protège votre organisation lorsque les utilisateurs collaborent et partagent des fichiers en identifiant et en bloquant les fichiers malveillants dans les sites d’équipe et les bibliothèques de documents. 
- Applique les modèles d’apprentissage automatique et les algorithmes de détection d’usurpation d’identité avancés aux attaques de hameçonnage AVERT. 

Pour obtenir une vue d’ensemble, y compris un récapitulatif des plans, voir [Office 365 Advanced Threat Protection](office-365-security/office-365-atp.md).

Votre administrateur général peut configurer les protections suivantes :
- [Configurer des liens fiables ATP](office-365-security/set-up-atp-safe-links-policies.md)
- [Définir des stratégies de pièces jointes fiables de PACM](office-365-security/set-up-atp-safe-attachments-policies.md)
- [Configurer une liste d’URL personnalisée « ne pas réécrire »](office-365-security/set-up-a-custom-do-not-rewrite-urls-list-with-atp.md)
- [Configurer une liste d’URL bloquée personnalisée](office-365-security/set-up-a-custom-blocked-urls-list-wtih-atp.md)

Vous devrez collaborer avec votre administrateur Exchange Online et votre administrateur SharePoint Online pour configurer la protection avancée contre les menaces pour ces charges de travail :
- [Activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams](office-365-security/turn-on-atp-for-spo-odb-and-teams.md)

## <a name="4-configure-azure-advanced-threat-protection"></a>4 : configurer Azure protection avancée contre les menaces

[Azure Advanced Threat Protection](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) (Azure ATP) est une solution de sécurité basée sur le Cloud qui tire parti de vos signaux Active Directory locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. Concentrez-vous sur cette étape, car elle protège votre infrastructure local et votre infrastructure cloud, ne dispose d’aucune dépendance ou prérequis et peut fournir des avantages immédiats.


- Voir les [QuickStarts Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/install-atp-step1) pour obtenir le programme d’installation rapidement 
- Regarder la [vidéo : présentation de](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE) la protection avancée contre les menaces
- Passer en revue les [trois phases du déploiement Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-advanced-threat-protection"></a>5 : activer Microsoft Advanced Threat Protection

À présent que vous disposez d’Office 365 ATP et d’Azure ATP configurés, vous pouvez afficher les signaux combinés à partir de ces fonctionnalités dans un tableau de bord. [Microsoft Threat Protection](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection) (MTP) rassemble des alertes, des incidents, une enquête et une réponse automatiques, ainsi qu’une recherche avancée sur les charges de travail (Azure ATP, Office 365 ATP, Microsoft Defender ATP et Microsoft Cloud App Security) dans un seul volet sur [Security.Microsoft.com](https://security.microsoft.com). 
<br>

![Illustration de tableau de bord MTP](../media/top-ten-security-remote-work-mtp-dashboard.png)
<br><br>
Une fois que vous avez configuré un ou plusieurs services de protection avancée contre les menaces, activez le service MTP. De nouvelles fonctionnalités sont ajoutées en continu à la fonction MTP ; envisagez d’opter pour recevoir des fonctionnalités d’aperçu.

- [En savoir plus sur le MTP](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-threat-protection?view=o365-worldwide)
- [Activer le MTP](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable?view=o365-worldwide)
- [S’abonner aux fonctionnalités d’aperçu](https://docs.microsoft.com/microsoft-365/security/mtp/preview?view=o365-worldwide)


## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6 : configurer la protection des applications mobiles Intune pour les téléphones et les tablettes

Microsoft Intune Mobile Application Management (MAM) vous permet de gérer et de protéger les données de votre organisation sur les téléphones et les tablettes sans gérer ces appareils. Voici le principe de fonctionnement :
- Vous créez une stratégie de protection des applications (APP) qui détermine les applications sur un appareil qui sont gérées et les comportements autorisés (par exemple, empêcher que les données d’une application gérée soient copiées dans une application non gérée). Vous créez une stratégie pour chaque Platorm (iOS, Android).
- Après avoir créé les stratégies de protection des applications, vous les appliquez en créant une règle d’accès conditionnel dans Azure AD pour exiger des applications approuvées et la protection des données d’application.

Les stratégies de protection des applications incluent de nombreux paramètres. Heureusement, vous n’avez pas besoin d’en savoir plus sur chaque paramètre et de peser les options. Microsoft facilite l’application d’une configuration de paramètres en recommandant les points de départ. L' [infrastructure de protection des données utilisant des stratégies de protection des applications](https://docs.microsoft.com/mem/intune/apps/app-protection-framework) comprend trois niveaux parmi lesquels vous pouvez choisir. 

Encore mieux, Microsoft coordonne cette infrastructure de protection des applications avec un ensemble d’accès conditionnel et de stratégies associées nous recommandons que toutes les organisations utilisent comme point de départ. Si vous avez implémenté MFA en utilisant les instructions de cet article, vous êtes à la moitié.

Pour configurer la protection des applications mobiles, utilisez les instructions des [stratégies courantes d’identité et d’accès aux appareils](../enterprise/identity-access-policies.md):
 1. Utilisez le guide [appliquer les stratégies de protection des données d’application](../enterprise/identity-access-policies.md#apply-app-data-protection-policies) pour créer des stratégies pour iOS et Android. Le niveau 2 (protection améliorée des données) est recommandé pour la protection de base. 
 2. Créer une règle d’accès conditionnel pour [exiger les applications approuvées et la protection des](../enterprise/identity-access-policies.md#require-approved-apps-and-app-protection)applications. 

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7 : configurer l’authentification MFA et l’accès conditionnel pour les invités, y compris la protection des applications mobiles Intune

Nous allons maintenant vous assurer que vous pouvez continuer à collaborer et collaborer avec vos invités. Si vous utilisez le plan Microsoft 365 E3 et que vous avez implémenté l’authentification multifacteur pour tous les utilisateurs, vous êtes défini. 

Si vous utilisez la planification Microsoft 365 E5 et que vous tirez parti d’Azure Identity Protection pour l’authentification multifacteur basée sur les risques, vous devez effectuer quelques ajustements (car la protection des identités Azure AD ne s’étend pas aux invités) :
- Créez une nouvelle règle d’accès conditionnel pour exiger la MFA toujours pour les invités et les utilisateurs externes.
- Mettre à jour la règle d’accès conditionnel MFA basée sur un risque pour exclure les invités et les utilisateurs externes.

Utilisez les instructions de [mise à jour des stratégies communes pour autoriser et protéger les accès invités et externes](../enterprise/identity-access-policies-guest-access.md) afin de comprendre le fonctionnement de l’accès invité avec Azure ad et mettre à jour les stratégies affectées. 

Les stratégies de protection d’application mobile Intune que vous avez créées, ainsi que la règle d’accès conditionnel pour exiger les applications approuvées et la protection d’application, s’appliquent aux comptes invités et vous aideront à protéger les données de votre organisation. 

**Remarque**: Si vous avez déjà déployé des PC dans la gestion des appareils pour exiger des PC conformes, vous devrez également exclure les comptes invités de la règle d’accès conditionnel qui applique la conformité de l’appareil. 


## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8 : inscrire des PC dans la gestion des appareils et exiger des PC conformes

Il existe plusieurs méthodes pour inscrire les appareils de votre personnel. Chaque méthode dépend de la propriété de l’appareil (personnel ou entreprise), du type d’appareil (iOS, Windows, Android) et de la configuration requise (réinitialisations, affinité, verrouillage). Le tri peut prendre un peu de temps. Voir : [inscrire des appareils dans Microsoft Intune](https://docs.microsoft.com/mem/intune/enrollment/). 

Pour commencer, il est recommandé de configurer l' [inscription automatique pour les appareils Windows 10](https://docs.microsoft.com/mem/intune/enrollment/quickstart-setup-auto-enrollment). 

Vous pouvez également tirer parti de ces didacticiels :
- [Utiliser AutoPilot pour inscrire des appareils Windows dans Intune](https://docs.microsoft.com/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Utiliser les fonctionnalités d’inscription d’appareil entreprise d’Apple dans le gestionnaire d’entreprise (ABM) pour inscrire des appareils iOS/iPad dans Intune](https://docs.microsoft.com/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Une fois les périphériques déployés, utilisez les instructions des [stratégies courantes d’identité et d’accès](../enterprise/identity-access-policies.md) aux appareils pour créer ces stratégies :
- [Définir les stratégies de conformité des appareils](../enterprise/identity-access-policies.md#define-device-compliance-policies) : les paramètres recommandés pour Windows 10 incluent la protection antivirus. Si vous disposez de Microsoft 365 E5, utilisez Microsoft Defender protection avancée contre les menaces pour surveiller l’état des appareils des employés. Assurez-vous que les stratégies de conformité pour d’autres systèmes d’exploitation incluent la protection antivirus et le logiciel de protection du point de terminaison. 
- [Exiger des PC conformes](../enterprise/identity-access-policies.md#require-compliant-pcs-but-not-compliant-phones-and-tablets) : il s’agit de la règle d’accès conditionnel dans Azure ad qui applique les stratégies de conformité des appareils.

Une seule organisation peut gérer un appareil ; Veillez donc à exclure les comptes invités de la règle d’accès conditionnel dans Azure AD. Si vous n’excluez pas les utilisateurs invités et externes des stratégies qui nécessitent une conformité de l’appareil, ces stratégies bloqueront ces utilisateurs. Pour plus d’informations, reportez-vous à [la rubrique mise à jour des stratégies communes pour autoriser et protéger les invités et l’accès externe](../enterprise/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9 : optimiser votre réseau pour la connectivité Cloud

Si vous activez rapidement la plupart de vos employés à partir de la maison, ce changement soudain de modèle de connectivité peut avoir un impact significatif sur l’infrastructure réseau d’entreprise. De nombreux réseaux ont été redimensionnés et conçus avant l’adoption des services Cloud. Dans de nombreux cas, les réseaux sont tolérants aux travailleurs distants, mais ils n’ont pas été conçus pour être utilisés simultanément par tous les utilisateurs.

Les éléments réseau, tels que les concentrateurs VPN, les équipements de sortie réseau centraux (tels que les proxies et les appareils de protection contre la perte de données), la bande passante Internet centrale, les circuits MPLS, les fonctionnalités NAT, etc., sont soudainement soumis à une déformation considérable en raison de la charge de l’ensemble de l’entreprise. Le résultat final est une baisse des performances et de la productivité couplée à une expérience utilisateur médiocre pour les utilisateurs qui s’adaptent au travail à partir de la maison.

Certaines des protections traditionnellement fournies par le routage du trafic via un réseau d’entreprise sont fournies par les applications Cloud auxquelles les utilisateurs accèdent. Si vous avez atteint cette étape dans cet article, vous avez implémenté un ensemble de contrôles de sécurité Cloud sophistiqués pour les données et les services Microsoft 365. Une fois ces contrôles en place, vous pouvez router le trafic des utilisateurs distants directement vers Office 365. Si vous avez toujours besoin d’un lien VPN pour accéder à d’autres applications, vous pouvez grandement améliorer les performances et l’expérience utilisateur en implémentant le tunneling fractionné. Une fois que vous avez obtenu un accord dans votre Oganization, vous pouvez le faire dans une journée par une équipe de réseau bien coordonnée.


Pour plus d’informations, reportez-vous à ces ressources sur docs :
- [Vue d’ensemble : optimiser la connectivité pour les utilisateurs distants à l’aide du tunneling VPN Split](https://docs.microsoft.com/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implémentation de la segmentation du tunnel par VPN pour Office 365](https://docs.microsoft.com/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Articles de blog récents sur cette rubrique :
- [Comment optimiser rapidement le trafic pour le personnel à distance & réduire la charge sur votre infrastructure](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Autres méthodes pour les professionnels de la sécurité et pour obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance d’aujourd’hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)


## <a name="10-train-users"></a>10 : former les utilisateurs

Les utilisateurs de la formation peuvent économiser de l’équipe et de la sécurité de vos utilisateurs et de votre activité. Les utilisateurs chevronnés sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites Web suspects. 

Le manuel de la [campagne](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) Harvard Kennedy School Cybersecurity fournit des conseils excellents sur l’établissement d’une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage. 

Microsoft 365 fournit les ressources suivantes pour aider les utilisateurs au sein de votre organisation :

|Concept  |Ressources  |
|---------|---------|
|Microsoft 365     |[Voies de formation personnalisables](https://docs.microsoft.com/office365/customlearning/) <p>Ces ressources peuvent vous aider à réunir des formations pour les utilisateurs finaux de votre organisation.        |
|Sécurité Microsoft 365 |[Module d’apprentissage : sécurisez votre organisation à l’aide de la sécurité intégrée et intelligente de Microsoft 365](https://docs.microsoft.com/learn/modules/security-with-microsoft-365) <p>Ce module vous permet de décrire les fonctionnalités de sécurité de Microsoft 365 et d’expliquer les avantages de ces fonctionnalités de sécurité. |
|Authentification multifacteur     | [Vérification en deux étapes : qu’est-ce que la page de vérification supplémentaire ?](https://docs.microsoft.com/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Cet article permet aux utilisateurs finaux de comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée au sein de votre organisation.    |
| | |

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’effectuer les actions décrites dans cet article : [protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Ces actions incluent :
  
- Utilisation de mots de passe forts
    
- Protection des appareils 
    
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non gérés)
    
Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en effectuant les actions recommandées dans les articles suivants :
  
- [Protéger votre compte de messagerie Outlook.com](https://support.office.com/article/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba.aspx)
    
- [Protégez votre compte Gmail à l’aide de la vérification en deux étapes](https://go.microsoft.com/fwlink/?linkid=2015688&amp;clcid=0x409)


## <a name="11-get-started-with-microsoft-cloud-app-security"></a>11 : prise en main de la sécurité des applications Cloud Microsoft

[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security) offre une visibilité riche, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre Cyber dans tous vos services Cloud. Une fois que vous avez commencé à utiliser la sécurité de l’application Cloud, les stratégies de détection des anomalies sont automatiquement activées, mais la sécurité des applications Cloud dispose d’une période d’apprentissage initiale de sept jours pendant laquelle toutes les alertes de détection d’anomalies ne sont pas générées.

Prise en main de la sécurité des applications Cloud maintenant. Par la suite, vous pouvez configurer une surveillance et des contrôles plus sophistiqués.

- [QuickStart : prise en main de la sécurité des applications Cloud](https://docs.microsoft.com/cloud-app-security/getting-started-with-cloud-app-security)
- [Obtenir des analyses comportementales instantanées et des détections d’anomalies](https://docs.microsoft.com/cloud-app-security/anomaly-detection-policy)
- [En savoir plus sur la sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security)
- [Passer en revue les nouvelles fonctionnalités](https://docs.microsoft.com/cloud-app-security/release-notes)
- [Voir les instructions de configuration de base](https://docs.microsoft.com/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12 : surveiller les menaces et prendre des mesures

Microsoft 365 propose plusieurs méthodes pour surveiller l’État et prendre les mesures appropriées. Le meilleur point de départ est le centre de sécurité Microsoft[https://security.microsoft.com](https://security.microsoft.com)365 (), où vous pouvez afficher le [score](https://docs.microsoft.com/microsoft-365/security/mtp/microsoft-secure-score?view=o365-worldwide)de sécurité Microsoft de votre organisation, ainsi que les alertes ou les entités nécessitant votre attention.

- [Prise en main du centre de sécurité Microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/overview-security-center?view=o365-worldwide)
- [Surveiller et afficher les rapports](https://docs.microsoft.com/microsoft-365/security/mtp/monitoring-and-reporting?view=o365-worldwide)
- [Consultez les portails de sécurité dans Microsoft 365](https://docs.microsoft.com/microsoft-365/security/mtp/portals)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez rapidement implémenté certaines des protections de sécurité les plus importantes et votre organisation est plus sécurisée. Vous êtes maintenant prêt à continuer à utiliser les fonctionnalités de protection contre les menaces (notamment Microsoft Defender Advanced Threat Protection), les fonctionnalités de protection et de classification des données, et à sécuriser les comptes administratifs. Pour un ensemble plus approfondi de recommandations de sécurité pour Microsoft 365, consultez [la rubrique microsoft 365 Security for Business Decisions (BDM)](Microsoft-365-security-for-bdm.md). 

Visitez également le nouveau centre de sécurité de Microsoft sur [docs.Microsoft.com/Security](https://docs.microsoft.com/security). 
