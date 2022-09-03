---
title: Confiance nulle configurations d’identité et d’accès aux appareils - Microsoft 365 pour les entreprises
description: Décrit les recommandations microsoft et les concepts de base pour le déploiement de stratégies et de configurations de messagerie sécurisées, de documents et d’applications pour Confiance nulle.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.service: microsoft-365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-overview
- m365solution-zero-trust
- zerotrust-solution
- highpri
ms.subservice: mdo
ms.openlocfilehash: 8178c3bf98e5171fa5e7c6c257ce43e1b00f62e9
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67598338"
---
# <a name="zero-trust-identity-and-device-access-configurations"></a>Configurations des identités Zéro confiance et de l’accès aux appareils

Les architectures de sécurité qui s’appuient sur des pare-feu réseau et des réseaux privés virtuels (VPN) pour isoler et restreindre l’accès aux ressources et services technologiques d’une organisation ne sont plus suffisantes pour une main-d’œuvre qui requiert régulièrement l’accès à des applications et des ressources qui existent au-delà des limites traditionnelles du réseau d’entreprise.

Pour résoudre ce nouveau monde de l’informatique, Microsoft recommande vivement le modèle de sécurité Confiance nulle, qui est basé sur ces principes directeurs :

- Vérifiez explicitement.

  Toujours s’authentifier et autoriser en fonction de tous les points de données disponibles. C’est là que Confiance nulle stratégies d’identité et d’accès aux appareils sont cruciales pour la connexion et la validation continue.

- Utilisez des autorisations selon le principe des privilèges minimum.

  Limitez l’accès utilisateur avec des stratégies adaptatives juste-à-temps et juste-à-accès (JIT/JEA), des stratégies adaptatives basées sur les risques et la protection des données.

- Supposez une violation.

  Réduisez le rayon d’explosion et l’accès au segment. Vérifiez le chiffrement de bout en bout et utilisez l’analyse pour obtenir la visibilité, détecter les menaces et améliorer les défenses.

Voici l’architecture globale de Confiance nulle.

:::image type="content" source="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png" alt-text="Architecture microsoft Confiance nulle" lightbox="../../media/microsoft-365-policies-configurations/zero-trust-architecture.png":::

Confiance nulle stratégies d’identité et d’accès aux appareils répondent au principe de vérification de **guidage explicite** pour :

- Identités

  Lorsqu’une identité tente d’accéder à une ressource, vérifiez que l’identité avec une authentification forte et vérifiez que l’accès demandé est conforme et classique.

- Appareils (également appelés points de terminaison)

  Surveillez et appliquez les exigences d’intégrité et de conformité des appareils pour un accès sécurisé.

- Applications

  Appliquez des contrôles et des technologies pour découvrir l’informatique fantôme, garantir les autorisations appropriées dans l’application, contrôler l’accès en fonction de l’analytique en temps réel, surveiller le comportement anormal, contrôler les actions des utilisateurs et valider les options de configuration sécurisées.

Cette série d’articles décrit un ensemble de configurations requises pour l’accès aux identités et aux appareils, ainsi qu’un ensemble d’accès conditionnel Azure Active Directory (Azure AD), de Microsoft Intune et d’autres stratégies pour Confiance nulle accès à Microsoft 365 pour les applications et services cloud d’entreprise, d’autres services SaaS et des applications locales publiées avec Azure AD Proxy d'application.

Confiance nulle paramètres et stratégies d’accès aux identités et aux appareils sont recommandés dans trois niveaux : point de départ, entreprise et sécurité spécialisée pour les environnements avec des données hautement réglementées ou classifiées. Ces niveaux et leurs configurations correspondantes fournissent des niveaux cohérents de protection Confiance nulle sur vos données, identités et appareils.

Ces fonctionnalités et leurs recommandations :

- Sont pris en charge dans Microsoft 365 E3 et Microsoft 365 E5.
- Sont alignés avec [le score de sécurité Microsoft](../defender/microsoft-secure-score.md) ainsi que le [score d’identité dans Azure AD](/azure/active-directory/fundamentals/identity-secure-score), et augmenteront ces scores pour votre organisation.
- Vous aidera à implémenter ces [cinq étapes pour sécuriser votre infrastructure d’identité](/azure/security/azure-ad-secure-steps).

Si votre organisation a des exigences ou des complexités d’environnement uniques, utilisez ces recommandations comme point de départ. Toutefois, la plupart des organisations peuvent implémenter ces recommandations comme prescrit.

Regardez cette vidéo pour obtenir une vue d’ensemble rapide des configurations d’identité et d’accès aux appareils pour Microsoft 365 pour les entreprises.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxEDQ]

> [!NOTE]
> Microsoft vend également des licences Enterprise Mobility + Security (EMS) pour les abonnements Office 365. Les fonctionnalités EMS E3 et EMS E5 sont équivalentes à celles de Microsoft 365 E3 et Microsoft 365 E5. Pour plus d’informations, consultez les [plans EMS](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/compare-plans-and-pricing) .

## <a name="intended-audience"></a>Public cible

Ces recommandations sont destinées aux architectes d’entreprise et aux professionnels de l’informatique qui sont familiarisés avec les services de sécurité et de productivité cloud Microsoft 365, notamment Azure AD (identité), Microsoft Intune (gestion des appareils) et Protection des données Microsoft Purview (protection des données).

### <a name="customer-environment"></a>Environnement client

Les stratégies recommandées s’appliquent aux organisations d’entreprise fonctionnant entièrement dans le cloud Microsoft et pour les clients disposant d’une infrastructure d’identité hybride, qui est une forêt Active Directory local Domain Services (AD DS) synchronisée avec un locataire Azure AD.

La plupart des recommandations fournies reposent sur des services disponibles uniquement avec Microsoft 365 E5, Microsoft 365 E3 avec le module complémentaire sécurité E5, EMS E5 ou des licences Azure AD Premium P2.

Pour les organisations qui n’ont pas ces licences, Microsoft vous recommande au moins d’implémenter [les paramètres de sécurité par défaut](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), qui sont inclus dans tous les plans Microsoft 365.

### <a name="caveats"></a>Avertissements

Votre organisation peut être soumise à des exigences réglementaires ou à d’autres exigences de conformité, notamment des recommandations spécifiques qui peuvent vous obliger à appliquer des stratégies qui diffèrent de ces configurations recommandées. Ces configurations recommandent des contrôles de l’utilisation qui n’étaient pas disponibles par le passé. Nous recommandons ces contrôles, car nous pensons qu’ils représentent un équilibre entre la sécurité et la productivité.

Nous avons fait de notre mieux pour prendre en compte un large éventail d’exigences de protection organisationnelle, mais nous ne pouvons pas tenir compte de toutes les exigences possibles ou de tous les aspects uniques de votre organisation.

## <a name="three-tiers-of-protection"></a>Trois niveaux de protection

La plupart des organisations ont des besoins spécifiques en matière de sécurité et de protection des données. Ces besoins varient selon leur secteur d’activité et selon les postes de travail en leur sein. Par exemple, votre service juridique et vos administrateurs peuvent avoir besoin de contrôles de sécurité et de protection des informations supplémentaires autour de leur correspondance électronique qui ne sont pas requis pour d’autres unités commerciales.

Chaque secteur d’activité possède aussi sa propre réglementation spécialisée. Plutôt que de fournir une liste de toutes les options de sécurité possibles ou une recommandation par segment d’industrie ou fonction de travail, des recommandations ont été fournies pour trois niveaux différents de sécurité et de protection qui peuvent être appliqués en fonction de la granularité de vos besoins.

- **Point de départ** : nous recommandons à tous les clients d’établir et d’utiliser une norme minimale pour protéger les données, ainsi que les identités et les appareils qui accèdent à vos données. Vous pouvez suivre ces recommandations pour fournir une protection par défaut renforcée comme point de départ pour toutes les organisations.
- **Entreprise** : Certains clients ont un sous-ensemble de données qui doivent être protégées à des niveaux supérieurs, ou ils peuvent exiger que toutes les données soient protégées à un niveau supérieur. Vous pouvez appliquer une protection accrue à tous les jeux de données ou à des jeux de données spécifiques dans votre environnement Microsoft 365. Nous vous recommandons de protéger les identités et les appareils qui accèdent à des données sensibles avec des niveaux de sécurité comparables.
- **Sécurité spécialisée** : si nécessaire, quelques clients disposent d’une petite quantité de données hautement classifiées, constituant des secrets commerciaux ou réglementées. Microsoft fournit des fonctionnalités pour aider ces clients à répondre à ces exigences, notamment une protection supplémentaire pour les identités et les appareils.

:::image type="content" source="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png" alt-text="Cône Sécurité" lightbox="../../media/microsoft-365-policies-configurations/M365-idquality-threetiers.png":::

Ces conseils vous montrent comment implémenter Confiance nulle protection pour les identités et les appareils pour chacun de ces niveaux de protection. Utilisez ces conseils comme un minimum pour votre organisation et ajustez les stratégies pour répondre aux exigences spécifiques de votre organisation.

Il est important d’utiliser des niveaux de protection cohérents sur vos identités, appareils et données. Par exemple, la protection pour les utilisateurs disposant de comptes&mdash;prioritaires tels que les cadres, les dirigeants, les responsables et d’autres&mdash;personnes doit inclure le même niveau de protection pour leurs identités, leurs appareils et les données auxquels ils accèdent. 
<!--

The **Zero Trust identity and device protection for Microsoft 365** architecture model shows you which capabilities are comparable.

[![Thumb image for Zero Trust Identity and device protection for Microsoft 365 poster.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-thumbnail.png)](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) <br> [View as a PDF](../../downloads/MSFT_cloud_architecture_identity&device_protection.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.pdf)  \| [Download as a Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT_cloud_architecture_identity&device_protection.vsdx)

--> 

En outre, consultez la solution [déployer la protection des informations pour la réglementation de confidentialité des données](../../solutions/information-protection-deploy.md) afin de protéger les informations stockées dans Microsoft 365.

## <a name="security-and-productivity-trade-offs"></a>Compromis entre sécurité et productivité

L’implémentation d’une stratégie de sécurité nécessite des compromis entre la sécurité et la productivité. Il est utile d’évaluer la façon dont chaque décision affecte l’équilibre entre la sécurité, les fonctionnalités et la facilité d’utilisation.

:::image type="content" source="../../media/microsoft-365-policies-configurations/security-triad.png" alt-text="Triade de sécurité équilibrant la sécurité, les fonctionnalités et la facilité d’utilisation" lightbox="../../media/microsoft-365-policies-configurations/security-triad.png":::

Les recommandations fournies sont basées sur les principes suivants :

- Connaissez vos utilisateurs et soyez flexibles à leurs exigences de sécurité et fonctionnelles.
- Appliquez une stratégie de sécurité juste-à-temps et assurez-vous qu’elle est significative.

## <a name="services-and-concepts-for-zero-trust-identity-and-device-access-protection"></a>Services et concepts pour Confiance nulle protection de l’identité et de l’accès aux appareils

Microsoft 365 pour entreprise est conçu pour permettre aux grandes organisations d’être créatifs et de collaborer en toute sécurité.

Cette section fournit une vue d’ensemble des services et fonctionnalités Microsoft 365 qui sont importants pour Confiance nulle l’identité et l’accès aux appareils.

### <a name="azure-ad"></a>Azure AD

Azure AD fournit une suite complète de fonctionnalités de gestion des identités. Nous vous recommandons d’utiliser ces fonctionnalités pour sécuriser l’accès.

|Fonctionnalité|Description|Licence|
|---|---|---|
|[Authentification multifacteur (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|L’authentification multifacteur exige que les utilisateurs fournissent deux formes de vérification, telles qu’un mot de passe d’utilisateur et une notification de l’application Microsoft Authenticator ou un appel téléphonique. L’authentification multifacteur réduit considérablement le risque que les informations d’identification volées puissent être utilisées pour accéder à votre environnement. Microsoft 365 utilise le service Azure AD Multi-Factor Authentication pour les connexions MFA.|Microsoft 365 E3 ou E5|
|[Accès conditionnel](/azure/active-directory/conditional-access/overview)|Azure AD évalue les conditions de connexion de l’utilisateur et utilise des stratégies d’accès conditionnel pour déterminer l’accès autorisé. Par exemple, dans ce guide, nous vous montrons comment créer une stratégie d’accès conditionnel pour exiger la conformité des appareils pour l’accès aux données sensibles. Cela réduit considérablement le risque qu’un pirate informatique disposant de son propre appareil et d’informations d’identification volées puisse accéder à vos données sensibles. Il protège également les données sensibles sur les appareils, car ils doivent répondre à des exigences spécifiques en matière d’intégrité et de sécurité.|Microsoft 365 E3 ou E5|
|[Groupes Azure AD](/azure/active-directory/fundamentals/active-directory-manage-groups)|Les stratégies d’accès conditionnel, la gestion des appareils avec Intune et même les autorisations sur les fichiers et les sites de votre organisation s’appuient sur l’affectation à des comptes d’utilisateurs ou à des groupes Azure AD. Nous vous recommandons de créer des groupes Azure AD qui correspondent aux niveaux de protection que vous implémentez. Par exemple, vos cadres supérieurs sont probablement des cibles de plus grande valeur pour les pirates informatiques. Par conséquent, il est judicieux d’ajouter les comptes d’utilisateur de ces employés à un groupe Azure AD et d’affecter ce groupe à des stratégies d’accès conditionnel et à d’autres stratégies qui appliquent un niveau de protection plus élevé pour l’accès.|Microsoft 365 E3 ou E5|
|[Inscription de l’appareil](/azure/active-directory/devices/overview)|Vous inscrivez un appareil dans Azure AD pour créer une identité pour l’appareil. Cette identité est utilisée pour authentifier l’appareil lorsqu’un utilisateur se connecte et pour appliquer des stratégies d’accès conditionnel qui nécessitent des PC joints à un domaine ou conformes. Pour ce guide, nous utilisons l’inscription des appareils pour inscrire automatiquement des ordinateurs Windows joints à un domaine. L’inscription d’appareils est un prérequis pour la gestion des appareils avec Intune.|Microsoft 365 E3 ou E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Vous permet de détecter les vulnérabilités potentielles qui affectent les identités de votre organisation et de configurer la stratégie de correction automatisée en cas de risque de connexion faible, moyenne et élevée et à risque utilisateur. Cette aide s’appuie sur cette évaluation des risques pour appliquer des stratégies d’accès conditionnel pour l’authentification multifacteur. Ces conseils incluent également une stratégie d’accès conditionnel qui oblige les utilisateurs à modifier leur mot de passe si une activité à haut risque est détectée pour leur compte.|Microsoft 365 E5, Microsoft 365 E3 avec le module complémentaire sécurité E5, EMS E5 ou les licences Azure AD Premium P2|
|[Réinitialisation de mot de passe en libre-service (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Permettre à vos utilisateurs de réinitialiser leurs mots de passe en toute sécurité et sans intervention du support technique, en fournissant la vérification de plusieurs méthodes d’authentification que l’administrateur peut contrôler.|Microsoft 365 E3 ou E5|
|[Protection par mot de passe Azure AD](/azure/active-directory/authentication/concept-password-ban-bad)|Détectez et bloquez les mots de passe faibles connus et leurs variantes, ainsi que les termes faibles supplémentaires spécifiques à votre organisation. Les listes générales par défaut de mots de passe interdits sont automatiquement appliquées à tous les utilisateurs d’un client Azure AD. Vous pouvez définir d’autres entrées dans une liste personnalisée de mots de passe interdits. Lorsque les utilisateurs modifient ou réinitialisent leurs mots de passe, ces listes sont vérifiées de façon à garantir l’utilisation de mots de passe forts.|Microsoft 365 E3 ou E5|

Voici les composants de Confiance nulle’identité et de l’accès aux appareils, y compris les objets Intune et Azure AD, les paramètres et les sous-services.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-components.png" alt-text="Composants de l’identité Confiance nulle et de l’accès aux appareils" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-components.png":::

### <a name="microsoft-intune"></a>Microsoft Intune

[Intune](/intune/introduction-intune) est le service de gestion des appareils mobiles basé sur le cloud de Microsoft. Ce guide recommande la gestion des appareils des PC Windows avec Intune et recommande les configurations de stratégie de conformité des appareils. Intune détermine si les appareils sont conformes et envoie ces données à Azure AD à utiliser lors de l’application de stratégies d’accès conditionnel.

#### <a name="intune-app-protection"></a>protection des applications Intune

[Intune](/intune/app-protection-policy) stratégies de protection des applications peuvent être utilisées pour protéger les données de votre organisation dans les applications mobiles, avec ou sans inscrire des appareils dans la gestion. Intune permet de protéger les informations, de s’assurer que vos employés peuvent toujours être productifs et d’éviter la perte de données. En implémentant des stratégies au niveau de l’application, vous pouvez restreindre l’accès aux ressources de l’entreprise et conserver les données sous le contrôle de votre service informatique.

Ces conseils vous montrent comment créer des stratégies recommandées pour appliquer l’utilisation d’applications approuvées et déterminer comment ces applications peuvent être utilisées avec vos données métier.

### <a name="microsoft-365"></a>Microsoft 365

Ces conseils vous montrent comment implémenter un ensemble de stratégies pour protéger l’accès aux services cloud Microsoft 365, notamment Microsoft Teams, Exchange, SharePoint et OneDrive. En plus d’implémenter ces stratégies, nous vous recommandons d’augmenter le niveau de protection de votre locataire à l’aide des ressources suivantes :

- [Configurer votre client pour une sécurité accrue](tenant-wide-setup-for-increased-security.md)

  Recommandations qui s’appliquent à la sécurité des points de départ pour votre locataire.

- [Feuille de route de sécurité : Principales priorités pour les 30 premiers jours, 90 jours et au-delà](security-roadmap.md)

  Recommandations qui incluent la journalisation, la gouvernance des données, l’accès administrateur et la protection contre les menaces.

### <a name="windows-11-or-windows-10-with-microsoft-365-apps-for-enterprise"></a>Windows 11 ou Windows 10 avec Applications Microsoft 365 pour les grandes entreprises

Windows 11 ou Windows 10 avec Applications Microsoft 365 pour les grandes entreprises est l’environnement client recommandé pour les PC. Nous vous recommandons Windows 11 ou Windows 10, car Azure est conçu pour offrir l’expérience la plus fluide possible pour Azure AD et en local. Windows 11 ou Windows 10 inclut également des fonctionnalités de sécurité avancées qui peuvent être gérées via Intune. Applications Microsoft 365 pour les grandes entreprises inclut les dernières versions des applications Office. Ceux-ci utilisent l’authentification moderne, qui est plus sécurisée et une exigence pour l’accès conditionnel. Ces applications incluent également des outils de conformité et de sécurité améliorés.

## <a name="applying-these-capabilities-across-the-three-tiers-of-protection"></a>Application de ces fonctionnalités sur les trois niveaux de protection

Le tableau suivant récapitule nos recommandations relatives à l’utilisation de ces fonctionnalités sur les trois niveaux de protection.

|Mécanisme de protection|Point de départ|Entreprise|Sécurité spécialisée|
|---|---|---|---|
|**Appliquer une authentification multifacteur**|En cas de risque de connexion moyen ou supérieur|En cas de risque de connexion faible ou supérieur|Pour toutes les nouvelles sessions|
|**Appliquer la modification du mot de passe**|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|Pour les utilisateurs à haut risque|
|**Appliquer Intune protection des applications**|Oui|Oui|Oui|
|**Appliquer l’inscription Intune pour l’appareil appartenant à l’organisation**|Exiger un PC conforme ou joint à un domaine, mais autoriser les téléphones et tablettes BYOD (Apportez votre propre appareil)|Exiger un appareil conforme ou joint à un domaine|Exiger un appareil conforme ou joint à un domaine|

## <a name="device-ownership"></a>Propriété des appareils

Le tableau ci-dessus reflète la tendance pour de nombreuses organisations à prendre en charge une combinaison d’appareils appartenant à l’organisation, ainsi que des appareils personnels ou BYOD pour permettre la productivité mobile au sein de la main-d’œuvre. Intune stratégies de protection des applications garantissent que le courrier électronique est protégé contre l’exfiltration de l’application mobile Outlook et d’autres applications mobiles Office, sur les appareils appartenant à l’organisation et les BYOD.

Nous recommandons que les appareils appartenant à l’organisation soient gérés par Intune ou joints à un domaine pour appliquer des protections et un contrôle supplémentaires. Selon la sensibilité des données, votre organisation peut choisir de ne pas autoriser les BYOD pour des populations d’utilisateurs spécifiques ou des applications spécifiques.

## <a name="deployment-and-your-apps"></a>Déploiement et vos applications

Avant de configurer et de déployer Confiance nulle configuration de l’identité et de l’accès aux appareils pour vos applications intégrées à Azure AD, vous devez :

- Déterminez les applications utilisées dans votre organisation que vous souhaitez protéger.
- Analysez cette liste d’applications pour déterminer les ensembles de stratégies qui fournissent des niveaux de protection appropriés.

  Vous ne devez pas créer des ensembles distincts de stratégies pour chaque application, car leur gestion peut devenir fastidieuse. Microsoft vous recommande de regrouper vos applications qui ont les mêmes exigences de protection pour les mêmes utilisateurs.

  Par exemple, vous pouvez avoir un ensemble de stratégies qui incluent toutes les applications Microsoft 365 pour tous vos utilisateurs pour la protection des points de départ et un deuxième ensemble de stratégies pour toutes les applications sensibles, telles que celles utilisées par les ressources humaines ou les services financiers, et les appliquer à ces groupes.

Une fois que vous avez déterminé l’ensemble des stratégies pour les applications que vous souhaitez sécuriser, déployez les stratégies à vos utilisateurs de façon incrémentielle, en traitant les problèmes en cours de route.

Par exemple, configurez les stratégies qui seront utilisées pour toutes vos applications Microsoft 365 pour Exchange uniquement avec les modifications supplémentaires pour Exchange. Déployer ces stratégies pour vos utilisateurs et résoudre les problèmes éventuels. Ensuite, ajoutez Teams avec ses modifications supplémentaires et déployez-la à vos utilisateurs. Ensuite, ajoutez SharePoint avec ses modifications supplémentaires. Continuez à ajouter le reste de vos applications jusqu’à ce que vous puissiez configurer en toute confiance ces stratégies de point de départ pour inclure toutes les applications Microsoft 365.

De même, pour vos applications sensibles, créez l’ensemble de stratégies et ajoutez une application à la fois et parcourez tous les problèmes jusqu’à ce qu’ils soient tous inclus dans l’ensemble de stratégies d’application sensible.

Microsoft recommande de ne pas créer d’ensembles de stratégies qui s’appliquent à toutes les applications, car cela peut entraîner des configurations inattendues. Par exemple, les stratégies qui bloquent toutes les applications peuvent verrouiller vos administrateurs hors du Portail Azure et les exclusions ne peuvent pas être configurées pour des points de terminaison importants tels que Microsoft Graph.

## <a name="steps-to-configure-zero-trust-identity-and-device-access"></a>Étapes de configuration de l’identité Confiance nulle et de l’accès aux appareils

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png" alt-text="Étapes de configuration de l’identité Confiance nulle et de l’accès aux appareils" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps.png":::

1. Configurez les fonctionnalités d’identité requise et leurs paramètres.
2. Configurez les stratégies courantes d’identité et d’accès conditionnel.
3. Configurez des stratégies d’accès conditionnel pour les utilisateurs invités et externes.
4. Configurez des stratégies d’accès conditionnel pour les applications&mdash;cloud Microsoft 365 telles que Microsoft Teams, Exchange et SharePoint&mdash;et les stratégies de Microsoft Defender for Cloud Apps.

Une fois que vous avez configuré Confiance nulle’identité et l’accès aux appareils, consultez le [guide de déploiement des fonctionnalités Azure AD](/azure/active-directory/fundamentals/active-directory-deployment-checklist-p2) pour obtenir une liste de vérification par phases des fonctionnalités supplémentaires à prendre en compte et [la gouvernance des identités Azure AD](/azure/active-directory/governance/) pour protéger, surveiller et auditer l’accès.

## <a name="next-step"></a>Étape suivante

[Travail requis pour implémenter Confiance nulle stratégies d’identité et d’accès aux appareils](identity-access-prerequisites.md)
