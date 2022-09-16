---
title: 12 tâches principales pour les équipes de sécurité afin de prendre en charge le travail à domicile
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.service: microsoft-365-security
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- remotework
ms.custom: admindeeplinkDEFENDER
description: Protégez vos e-mails et données professionnels contre les cybermenaces, y compris les ransomware, le hameçonnage et les pièces jointes malveillantes.
ms.openlocfilehash: dcf2d81828ff12ef857b10ec81595613d1e4f98a
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67741365"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>12 tâches principales pour les équipes de sécurité afin de prendre en charge le travail à domicile

Si vous êtes comme [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) et que vous vous retrouvez soudainement à prendre en charge une main-d’œuvre principalement basée à domicile, nous voulons vous aider à vous assurer que votre organisation fonctionne aussi en toute sécurité que possible. Cet article hiérarchise les tâches pour aider les équipes de sécurité à implémenter les fonctionnalités de sécurité les plus importantes le plus rapidement possible.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="Les principales tâches à effectuer pour prendre en charge le travail à domicile" lightbox="../media/security/security-support-remote-work.png":::


Si vous êtes une petite ou moyenne organisation utilisant l’un des plans d’entreprise de Microsoft, consultez plutôt les ressources suivantes :

- [Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 for Campaigns](../business-premium/index.md) (inclut une configuration de sécurité recommandée pour Microsoft 365 Business)

Pour les clients qui utilisent nos plans d’entreprise, Microsoft vous recommande d’effectuer les tâches répertoriées dans le tableau suivant qui s’appliquent à votre plan de service. Si, au lieu d’acheter un plan Microsoft 365 Entreprise, vous combinez des abonnements, notez les points suivants :

- Microsoft 365 E3 inclut Enterprise Mobility + Security (EMS) E3 et Azure AD P1
- Microsoft 365 E5 inclut EMS E5 et Azure AD P2

****

|Étape|Tâche|Tous les plans Office 365 Entreprise|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Activer l’authentification multifacteur (MFA) Azure AD](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Se protéger contre les menaces](#2-protect-against-threats)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Configurer Microsoft Defender pour Office 365](#3-configure-microsoft-defender-for-office-365)|||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Configurer Microsoft Defender pour Identity](#4-configure-microsoft-defender-for-identity)|||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Activer Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Configurer la protection des applications mobiles Intune pour les téléphones et tablettes](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7 |[Configurer l’authentification multifacteur et l’accès conditionnel pour les invités, y compris la protection des applications Intune](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8 |[Inscrire des PC dans la gestion des appareils et exiger des PC conformes](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9 |[Optimiser votre réseau pour la connectivité cloud](#9-optimize-your-network-for-cloud-connectivity)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Former les utilisateurs](#10-train-users)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Démarrer avec Microsoft Defender pour les applications cloud](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12 |[Surveiller les menaces et prendre des mesures](#12-monitor-for-threats-and-take-action)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inclus.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

Avant de commencer, vérifiez votre [degré de sécurisation Microsoft 365](./defender/microsoft-secure-score.md) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. À partir d’un tableau de bord centralisé, vous pouvez surveiller et améliorer la sécurité de vos identités, données, applications, appareils et infrastructure Microsoft 365. Des points vous sont attribués pour configurer les fonctionnalités de sécurité recommandées, effectuer des tâches liées à la sécurité (telles que l’affichage de rapports) ou répondre aux recommandations avec une application ou un logiciel tiers. Les tâches recommandées dans cet article augmenteront votre score.

:::image type="content" source="../media/secure-score.png" alt-text="Écran Microsoft Secure Score dans le portail Microsoft 365 Defender" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1 : Activer l’authentification multifacteur (MFA) Azure AD

La meilleure chose à faire pour améliorer la sécurité des employés travaillant à domicile consiste à activer l’authentification multifacteur. Si vous n’avez pas encore de processus en place, traitez-le comme un pilote d’urgence et assurez-vous que vous avez des gens de soutien prêts à aider les employés qui sont bloqués. Comme vous ne pouvez probablement pas distribuer des appareils de sécurité matériels, utilisez Windows Hello biométrie et des applications d’authentification pour smartphone comme Microsoft Authenticator.

Normalement, Microsoft vous recommande de donner aux utilisateurs 14 jours pour inscrire leur appareil à Multi-Factor Authentication avant d’exiger l’authentification multifacteur. Toutefois, si votre personnel travaille soudainement de la maison, continuez et exigez l’authentification multifacteur comme priorité de sécurité et soyez prêt à aider les utilisateurs qui en ont besoin.

L’application de ces stratégies ne prendra que quelques minutes, mais soyez prêt à prendre en charge vos utilisateurs au cours des prochains jours.

****

|Planification|Recommandation|
|---|---|
|Plans Microsoft 365 (sans Azure AD P1 ou P2)|[Activer les paramètres de sécurité par défaut dans Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). La sécurité par défaut d’Azure AD inclut l’authentification multifacteur pour les utilisateurs et les administrateurs.|
|Microsoft 365 E3 (avec Azure AD P1)|Utilisez les [Stratégies d’accès conditionnel courantes](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) pour configurer les stratégies suivantes : <br/>- [Exiger l’authentification multifacteur pour les administrateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Exiger l’authentification multifacteur pour tous les utilisateurs](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Bloquer l’authentification héritée](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (avec Azure AD P2)|En tirant parti d’Azure AD Identity Protection, commencez à implémenter [l’ensemble recommandé par Microsoft d’accès conditionnel et de stratégies associées](./office-365-security/identity-access-policies.md) en créant les stratégies suivantes :<br/> - [Exiger l’authentification multifacteur lorsque le risque de connexion est moyen ou élevé](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Bloquer les clients ne prenant pas en charge l’authentification moderne](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Les utilisateurs à risque élevé doivent modifier leur mot de passe](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2 : Protéger contre les menaces

Tous les plans Microsoft 365 incluent diverses fonctionnalités de protection contre les menaces. Le renforcement de la protection pour ces fonctionnalités ne prend que quelques minutes.

- Protection anti-programme malveillant
- Protection contre les URL et fichiers malveillants
- Protection anti-hameçonnage
- Protection anti-courrier indésirable

Consultez [Protéger contre les menaces dans Office 365](office-365-security/protect-against-threats.md) pour obtenir des conseils que vous pouvez utiliser comme point de départ.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3 : Configurer Microsoft Defender pour Office 365

Microsoft Defender pour Office 365, inclus avec Microsoft 365 E5 et Office 365 E5, protège votre organisation contre les menaces malveillantes posées par les e-mails, les liens (URL) et les outils de collaboration. La configuration peut prendre plusieurs heures.

Microsoft Defender pour Office 365 :

- Protège votre organisation contre les menaces de messagerie inconnues en temps réel à l’aide de systèmes intelligents qui inspectent les pièces jointes et les liens à la recherche de contenu malveillant. Ces systèmes automatisés incluent une plateforme de détonation robuste, des modèles heuristiques et des modèles Machine Learning.
- Protège votre organisation lorsque les utilisateurs collaborent et partagent des fichiers, en identifiant et en bloquant les fichiers malveillants dans les sites d’équipe et les bibliothèques de documents.
- Applique des modèles Machine Learning et des algorithmes avancés de détection d’emprunt d’identité pour éviter les attaques par hameçonnage.

Pour obtenir une vue d’ensemble, y compris un résumé des plans, consultez [Defender pour Office 365](./office-365-security/defender-for-office-365.md).

Votre administrateur général peut configurer ces protections :

- [Configuration des stratégies de liens fiables](office-365-security/set-up-safe-links-policies.md)
- [Configurer les paramètres globaux pour les liens fiables](office-365-security/configure-global-settings-for-safe-links.md)
- [Définir des stratégies de pièces jointes fiables](office-365-security/set-up-safe-attachments-policies.md)

Vous devez travailler avec votre administrateur Exchange Online et l’administrateur SharePoint Online pour configurer Defender pour Office 365 pour ces charges de travail :

- [Pertahanan Microsoft untuk Titik Akhir pour SharePoint, OneDrive et Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4 : Configurer Microsoft Defender pour Identity

[Microsoft Defender pour Identity](/azure-advanced-threat-protection/what-is-atp) est une solution de sécurité basée sur le cloud qui exploite vos signaux Active Directory sur site pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions des utilisateurs malveillants ciblant votre organisation. Concentrez-vous sur cette étape, car elle protège votre infrastructure locale et votre infrastructure cloud, n’a pas de dépendances ou de prérequis et peut offrir un avantage immédiat.

- Consultez les [guides de démarrage rapide de Microsoft Defender pour Identity](/azure-advanced-threat-protection/install-atp-step1) pour obtenir une configuration rapide
- Regarder [la vidéo : Présentation de Microsoft Defender pour Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Passer en revue les [trois phases du déploiement de Microsoft Defender pour Identity](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5 : Activer Microsoft 365 Defender

Maintenant que Microsoft Defender pour Office 365 et Microsoft Defender pour Identity sont configurés, vous pouvez afficher les signaux combinés de ces fonctionnalités dans un tableau de bord. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) regroupe les alertes, les incidents, l’investigation et la réponse automatisées, ainsi que la recherche avancée entre les charges de travail (Microsoft Defender pour Identity, Defender pour Office 365, Microsoft Defender pour point de terminaison et Microsoft Defender for Cloud Apps) dans un seul volet dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"> portail Microsoft 365 Defender</a>.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="Tableau de bord Microsoft 365 Defender" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

Une fois que vous avez configuré un ou plusieurs de vos services Defender pour Office 365, activez MTP. De nouvelles fonctionnalités sont ajoutées en permanence à MTP ; envisagez d’accepter de recevoir des fonctionnalités en préversion.

- [Mer informasjon sur MTP](./defender/microsoft-365-defender.md)
- [Activer MTP](./defender/m365d-enable.md)
- [Optez pour les fonctionnalités en préversion](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6 : Configurer la protection des applications mobiles Intune pour les téléphones et tablettes

Microsoft Intune Mobile Application Management (MAM) vous permet de gérer et de protéger les données de votre organisation sur les téléphones et tablettes sans gérer ces appareils. Voici le principe de fonctionnement :

- Vous créez une stratégie de protection des applications (APP) qui détermine quelles applications sur un appareil sont gérées et quels comportements sont autorisés (par exemple, empêcher la copie des données d’une application managée vers une application non managée). Vous créez une stratégie pour chaque plateforme (iOS, Android).
- Après avoir créé les stratégies de protection des applications, vous les appliquez en créant une règle d’accès conditionnel dans Azure AD pour exiger des applications approuvées et une protection des données d’application.

Les stratégies de protection des applications incluent de nombreux paramètres. Heureusement, vous n’avez pas besoin d’en savoir plus sur chaque paramètre et de peser les options. Microsoft facilite l’application d’une configuration de paramètres en recommandant des points de départ. [L’infrastructure de protection des données à l’aide de stratégies de protection des applications](/mem/intune/apps/app-protection-framework) comprend trois niveaux parmi lesquels vous pouvez choisir.

Mieux encore, Microsoft coordonne cette infrastructure de protection des applications avec un ensemble d’accès conditionnel et de stratégies associées que nous recommandons à toutes les organisations d’utiliser comme point de départ. Si vous avez implémenté l’authentification multifacteur à l’aide des conseils de cet article, vous êtes à mi-chemin !

Pour configurer la protection des applications mobiles, suivez les instructions fournies dans [les stratégies d’accès aux identités et aux appareils courantes](./office-365-security/identity-access-policies.md) :

 1. Utilisez les conseils [appliquer des stratégies de protection des données APP](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) pour créer des stratégies pour iOS et Android. Le niveau 2 (protection améliorée des données) est recommandé pour la protection de référence.
 2. Créez une règle d’accès conditionnel pour [exiger des applications approuvées et une protection d’application](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7 : Configurer l’authentification multifacteur et l’accès conditionnel pour les invités, y compris la protection des applications mobiles Intune

Ensuite, nous allons nous assurer que vous pouvez continuer à collaborer et à travailler avec des invités. Si vous utilisez le plan Microsoft 365 E3 et que vous avez implémenté l’authentification multifacteur pour tous les utilisateurs, vous êtes défini.

Si vous utilisez le plan Microsoft 365 E5 et que vous tirez parti d’Azure Identity Protection pour l’authentification multifacteur basée sur les risques, vous devez effectuer quelques ajustements (car Azure AD Identity Protection ne s’étend pas aux invités) :

- Créez une règle d’accès conditionnel pour exiger l’authentification multifacteur pour les invités et les utilisateurs externes.
- Mettez à jour la règle d’accès conditionnel MFA basée sur les risques pour exclure les invités et les utilisateurs externes.

Utilisez les conseils de [mise à jour des stratégies courantes pour autoriser et protéger l’accès invité et externe](./office-365-security/identity-access-policies-guest-access.md) afin de comprendre le fonctionnement de l’accès invité avec Azure AD et de mettre à jour les stratégies affectées.

Les stratégies de protection des applications mobiles Intune que vous avez créées, ainsi que la règle d’accès conditionnel pour exiger des applications approuvées et une protection d’application, s’appliquent aux comptes invités et contribuent à protéger les données de votre organisation.

> [!NOTE]
> Si vous avez déjà inscrit des PC dans la gestion des appareils pour exiger des PC conformes, vous devez également exclure les comptes invités de la règle d’accès conditionnel qui applique la conformité des appareils.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8 : Inscrire des PC dans la gestion des appareils et exiger des PC conformes

Il existe plusieurs méthodes pour inscrire les appareils de vos employés. Chaque méthode dépend de la propriété de l’appareil (personnel ou entreprise), du type d’appareil (iOS, Windows, Android) et de la configuration requise (réinitialisations, affinité, verrouillage). Le tri peut prendre un peu de temps. Voir : [Inscrire des appareils dans Microsoft Intune](/mem/intune/enrollment/).

La méthode la plus rapide consiste à [configurer l’inscription automatique pour Windows 10 appareils](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Vous pouvez également tirer parti de ces didacticiels :

- [Utiliser Autopilot pour inscrire des appareils Windows dans Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Utiliser les fonctionnalités d’inscription des appareils d’entreprise d’Apple dans Apple Business Manager (ABM) pour inscrire des appareils iOS/iPadOS dans Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Après avoir inscrit des appareils, suivez les instructions des stratégies [d’accès aux identités et aux appareils courantes](./office-365-security/identity-access-policies.md) pour créer les stratégies suivantes :

- [Définir des stratégies de conformité des appareils](./office-365-security/identity-access-policies.md#define-device-compliance-policies) : les paramètres recommandés pour Windows 10 incluent la nécessité d’une protection antivirus. Si vous avez Microsoft 365 E5, utilisez Pertahanan Microsoft untuk Titik Akhir pour surveiller l’intégrité des appareils des employés. Assurez-vous que les stratégies de conformité pour d’autres systèmes d’exploitation incluent la protection antivirus et les logiciels de protection des points de terminaison.
- [Exiger des PC conformes](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) : il s’agit de la règle d’accès conditionnel dans Azure AD qui applique les stratégies de conformité des appareils.

Une seule organisation peut gérer un appareil. Veillez donc à exclure les comptes invités de la règle d’accès conditionnel dans Azure AD. Si vous n’excluez pas les utilisateurs invités et externes des stratégies qui nécessitent la conformité des appareils, ces stratégies bloquent ces utilisateurs. Pour plus d’informations, consultez [Mise à jour des stratégies courantes pour autoriser et protéger l’accès invité et externe](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9 : Optimiser votre réseau pour la connectivité cloud

Si vous autorisez rapidement la plupart de vos employés à travailler à domicile, ce changement soudain de modèles de connectivité peut avoir un impact significatif sur l’infrastructure réseau de l’entreprise. De nombreux réseaux ont été mis à l’échelle et conçus avant l’adoption des services cloud. Dans de nombreux cas, les réseaux sont tolérants aux travailleurs distants, mais n’ont pas été conçus pour être utilisés à distance par tous les utilisateurs simultanément.

Les éléments réseau tels que les concentrateurs VPN, l’équipement de sortie du réseau central (tels que les proxies et les dispositifs de protection contre la perte de données), la bande passante Internet centrale, les circuits MPLS en panne, la fonctionnalité NAT, etc., sont soudainement soumis à une énorme contrainte en raison de la charge de l’ensemble de l’entreprise qui les utilise. Le résultat final est une baisse des performances et de la productivité, associée à une mauvaise expérience utilisateur pour les utilisateurs qui s’adaptent au travail à domicile.

Certaines des protections qui ont traditionnellement été fournies par le routage du trafic via un réseau d’entreprise sont fournies par les applications cloud auxquelles vos utilisateurs accèdent. Si vous avez atteint cette étape dans cet article, vous avez implémenté un ensemble de contrôles de sécurité cloud sophistiqués pour les services et les données Microsoft 365. Une fois ces contrôles en place, vous pouvez être prêt à acheminer le trafic des utilisateurs distants directement vers Office 365. Si vous avez toujours besoin d’un lien VPN pour accéder à d’autres applications, vous pouvez améliorer considérablement vos performances et votre expérience utilisateur en implémentant le tunneling fractionné. Une fois que vous avez obtenu un accord au sein de votre organisation, cela peut être effectué en une journée par une équipe réseau bien coordonnée.

Pour plus d’informations, consultez ces ressources sur Docs :

- [Vue d’ensemble : Optimiser la connectivité pour les utilisateurs distants à l’aide du tunneling fractionné VPN](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implémentation d'un tunnel VPN partagé pour Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Articles de blog récents sur cette rubrique :

- [Comment optimiser rapidement le trafic pour le personnel à distance & réduire la charge sur votre infrastructure](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Autres moyens pour les professionnels de la sécurité et l’informatique d’obtenir des contrôles de sécurité modernes dans les scénarios de travail à distance uniques d’aujourd’hui](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10 : Former des utilisateurs

La formation des utilisateurs peut faire gagner beaucoup de temps et de frustration à vos utilisateurs et à votre équipe chargée des opérations de sécurité. Les utilisateurs avertis sont moins susceptibles d’ouvrir des pièces jointes ou de cliquer sur des liens dans des messages électroniques douteux, et ils sont plus susceptibles d’éviter les sites web suspects.

Le [Manuel de la campagne de cybersécurité](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) de l’École Harvard Kennedy fournit d’excellents conseils sur l’établissement d’une culture forte de la sensibilisation à la sécurité au sein de votre organisation, y compris la formation des utilisateurs pour identifier les attaques par hameçonnage.

Microsoft 365 fournit les ressources suivantes pour aider à informer les utilisateurs de votre organisation :

****

|Concept|Ressources|
|---|---|
|Microsoft 365|[Parcours d’apprentissage personnalisables](/office365/customlearning/) <p>Ces ressources peuvent vous aider à mettre en place une formation pour les utilisateurs finaux de votre organisation.|
|Sécurité Microsoft 365|[Module d’apprentissage : Sécuriser votre organisation avec une sécurité intégrée et intelligente à partir de Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Ce module vous permet de décrire comment les fonctionnalités de sécurité Microsoft 365 fonctionnent ensemble et d’articuler les avantages de ces fonctionnalités de sécurité.|
|Authentification multifacteur|[Vérification en deux étapes : quelle est la page de vérification supplémentaire ?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Cet article aide les utilisateurs finaux à comprendre ce qu’est l’authentification multifacteur et pourquoi elle est utilisée auprès de votre organisation.|

En plus de ces conseils, Microsoft recommande à vos utilisateurs d’effectuer les actions décrites dans cet article : [Protéger votre compte et vos appareils contre les pirates et les programmes malveillants](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Ces actions incluent :

- Utilisation de mots de passe forts
- Protection des appareils
- Activation des fonctionnalités de sécurité sur les PC Windows 10 et Mac (pour les appareils non gérés)

Microsoft recommande également aux utilisateurs de protéger leurs comptes de messagerie personnels en effectuant les actions recommandées dans les articles suivants :

- [Protéger votre compte de messagerie Outlook.com](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Protéger votre compte Gmail avec la vérification en 2 étapes](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11 : Bien démarrer avec Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](/cloud-app-security) offre une visibilité enrichie, un contrôle sur le déplacement des données et des analyses sophistiquées pour identifier et combattre les cybermenaces dans tous vos services cloud. Une fois que vous avez commencé à utiliser Defender pour Cloud Apps, les stratégies de détection d’anomalies sont automatiquement activées, mais Defender pour Cloud Apps a une période d’apprentissage initiale de sept jours pendant laquelle toutes les alertes de détection d’anomalies ne sont pas déclenchées.

Commencez maintenant à utiliser Defender pour Cloud Apps. Vous pourrez ensuite configurer des contrôles et une surveillance plus sophistiqués.

- [Démarrage rapide : Bien démarrer avec Defender pour Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Obtenir une analyse comportementale instantanée et la détection des anomalies](/cloud-app-security/anomaly-detection-policy)
- [Mer informasjon sur Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Passer en revue les nouvelles fonctionnalités](/cloud-app-security/release-notes)
- [Consultez les instructions d’installation de base](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12 : Surveiller les menaces et prendre des mesures

Microsoft 365 inclut plusieurs façons de surveiller l’état et de prendre les mesures appropriées. Votre meilleur point de départ est le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, où vous pouvez afficher le [score de sécurité Microsoft](./defender/microsoft-secure-score.md) de votre organisation, ainsi que toutes les alertes ou entités qui nécessitent votre attention.

- [Prise en main du portail Microsoft 365 Defender](./defender/microsoft-365-defender-portal.md)
- [Voir les portails de sécurité dans Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez rapidement implémenté certaines des protections de sécurité les plus importantes et votre organisation est beaucoup plus sécurisée. Vous êtes maintenant prêt à aller encore plus loin avec les fonctionnalités de protection contre les menaces (y compris les Pertahanan Microsoft untuk Titik Akhir), les fonctionnalités de classification et de protection des données et la sécurisation des comptes d’administration. Pour obtenir un ensemble plus approfondi et méthodique de recommandations de sécurité pour Microsoft 365, consultez [Les décideurs en matière de sécurité pour les entreprises (BDM) de Microsoft 365](Microsoft-365-security-for-bdm.md).

Visitez également la nouvelle documentation de Microsoft sur Defender pour le cloud en [matière de sécurité](/security).
