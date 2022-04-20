---
title: Plan de déploiement zéro trust Microsoft 365
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Découvrez comment déployer Microsoft 365 Confiance nulle sécurité dans votre environnement pour vous défendre contre les menaces et protéger les données sensibles.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: 3b943569485ffaa96b33208c1c4bf0a491c23a95
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939474"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Plan de déploiement zéro trust Microsoft 365

Cet article fournit un plan de déploiement pour la création **de Confiance nulle** la sécurité avec Microsoft 365. Confiance nulle est un nouveau modèle de sécurité qui suppose une violation et vérifie chaque demande comme s’il provenait d’un réseau non contrôlé. Quel que soit l’endroit d’origine de la requête ou la ressource à laquelle elle accède, le modèle Confiance nulle nous apprend à « ne jamais faire confiance, toujours vérifier ».

## <a name="zero-trust-security-architecture"></a>architecture de sécurité Confiance nulle

Une approche Confiance nulle s’étend à l’ensemble du patrimoine numérique et sert de philosophie de sécurité intégrée et de stratégie de bout en bout.

Cette illustration fournit une représentation des éléments principaux qui contribuent à Confiance nulle.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Architecture de sécurité Confiance nulle" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Dans cette illustration :

- L’application de la stratégie de sécurité est au centre d’une architecture Confiance nulle. Cela inclut l’authentification multifacteur avec accès conditionnel qui prend en compte le risque de compte d’utilisateur, l’état de l’appareil et d’autres critères et stratégies que vous définissez.
- Les identités, appareils, données, applications, réseau et autres composants d’infrastructure sont tous configurés avec une sécurité appropriée. Les stratégies configurées pour chacun de ces composants sont coordonnées avec votre stratégie de Confiance nulle globale. Par exemple, les stratégies d’appareil déterminent les critères pour les appareils sains et les stratégies d’accès conditionnel nécessitent des appareils sains pour l’accès à des applications et des données spécifiques.
- La protection contre les menaces et le renseignement surveillent l’environnement, exposent les risques actuels et prennent des mesures automatisées pour corriger les attaques.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype).
-->

Pour plus d’informations sur Confiance nulle, consultez le [_**Centre d’aide Confiance nulle**_](/security/zero-trust) microsoft.

## <a name="deploying-zero-trust-for-microsoft-365"></a>Déploiement de Confiance nulle pour Microsoft 365

Microsoft 365 est conçu intentionnellement avec de nombreuses fonctionnalités de sécurité et de protection des informations pour vous aider à créer des Confiance nulle dans votre environnement. La plupart des fonctionnalités peuvent être étendues pour protéger l’accès aux autres applications SaaS utilisées par votre organisation et aux données de ces applications.

Cette illustration représente le travail de déploiement de fonctionnalités Confiance nulle. Ce travail est divisé en unités de travail qui peuvent être configurées ensemble, en commençant par le bas et en travaillant jusqu’en haut pour vous assurer que le travail requis est terminé.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Pile de déploiement Microsoft 365 Confiance nulle" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Dans cette illustration :

- Confiance nulle commence par une base de protection des identités et des appareils.
- Les fonctionnalités de protection contre les menaces reposent sur cette base pour fournir une surveillance et une correction en temps réel des menaces de sécurité.
- La protection et la gouvernance des informations fournissent des contrôles sophistiqués ciblant des types spécifiques de données afin de protéger vos informations les plus précieuses et de vous aider à vous conformer aux normes de conformité, notamment la protection des informations personnelles.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Étape 1. Configurer Confiance nulle protection de l’identité et de l’accès aux appareils : stratégies de point de départ

La première étape consiste à créer votre base Confiance nulle en configurant la protection des identités et de l’accès aux appareils.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Processus de configuration de Confiance nulle protection de l’identité et de l’accès aux appareils" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

Accédez à [**_Confiance nulle protection de l’identité et de l’accès aux appareils_**](office-365-security/microsoft-365-policies-configurations.md) pour obtenir des conseils normatifs pour ce faire. Cette série d’articles décrit un ensemble de configurations requises pour l’identité et l’accès aux appareils, ainsi qu’un ensemble de Azure Active Directory (Azure AD) l’accès conditionnel, Microsoft Intune et d’autres stratégies pour sécuriser l’accès à Microsoft 365  pour les applications et services cloud d’entreprise, les autres services SaaS et les applications locales publiés avec Azure AD Proxy d'application.

|Comprend|Conditions préalables|N’inclut pas|
|---------|---------|---------|
|Stratégies d’identité et d’accès aux appareils recommandées pour trois niveaux de protection : <ul><li>Point de départ</li><li>Enterprise (recommandé)</li><li>Spécialisé</li></ul> <br> Recommandations supplémentaires pour : <ul><li>Utilisateurs externes (invités)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Microsoft Defender for Cloud Apps</lu></ul>|Microsoft E3 ou E5 <br><br> Azure Active Directory dans l’un des modes suivants : <ul><li>Cloud uniquement</li><li>Authentification hybride avec synchronisation de hachage de mot de passe (PHS)</li><li>Hybride avec authentification directe (PTA)</li><li>Fédérés</li></ul>|Inscription d’appareils pour les stratégies qui nécessitent des appareils gérés. Voir [l’étape 2. Gérer les points de terminaison avec Intune](#step-2-manage-endpoints-with-intune) pour inscrire des appareils|

Commencez par implémenter le niveau de point de départ. Ces stratégies ne nécessitent pas l’inscription d’appareils dans la gestion.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Les Confiance nulle stratégies d’identité et d’accès aux appareils — niveau de point de départ" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>Étape 2. Gérer les points de terminaison avec Intune

Ensuite, inscrivez vos appareils dans la gestion et commencez à les protéger avec des contrôles plus sophistiqués.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Gérer les points de terminaison avec l’élément Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

Accédez à [**_Gérer les appareils avec Intune_**](../solutions/manage-devices-with-intune-overview.md) pour obtenir des conseils normatifs pour ce faire.

|Comprend|Conditions préalables|N’inclut pas|
|---------|---------|---------|
|Inscrire des appareils avec Intune : <ul><li>Appareils appartenant à l’entreprise</li><li>Autopilot/automatisé</li><li>Inscription</li></ul> <br> Configurer des stratégies : <ul><li>Stratégies de protection des applications</li><li>Stratégies de conformité</li><li>Stratégies de profil d’appareil</li></ul>|Inscrire des points de terminaison avec Azure AD|Configuration des fonctionnalités de protection des informations, notamment : <ul><li>Types d’informations sensibles</li><li>Étiquettes</li><li>Stratégies de protection contre la perte de données</li></ul> <br> Pour ces fonctionnalités, consultez [l’étape 5. Protéger et régir les données sensibles](#step-5-protect-and-govern-sensitive-data) (plus loin dans cet article).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Étape 3. Ajouter Confiance nulle protection de l’identité et de l’accès aux appareils — stratégies Enterprise

Avec les appareils inscrits dans la gestion, vous pouvez désormais implémenter l’ensemble complet des stratégies d’identité et d’accès aux appareils Confiance nulle recommandées, nécessitant des appareils conformes.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Les Confiance nulle les stratégies d’identité et d’accès avec la gestion des appareils" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Revenez aux [**_stratégies d’accès aux identités et aux appareils courantes_**](office-365-security/identity-access-policies.md) et ajoutez-les au niveau Enterprise.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Les stratégies d’identité et d’accès Confiance nulle — niveau Enterprise (recommandé)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Étape 4. Évaluer, piloter et déployer Microsoft 365 Defender

Microsoft 365 Defender est une solution de détection et de réponse étendue (XDR) qui collecte, met en corrélation et analyse automatiquement les données de signal, de menace et d’alerte à partir de votre environnement Microsoft 365, notamment le point de terminaison, l’e-mail, les applications et les identités.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Processus d’ajout de Microsoft 365 Defender à l’architecture Confiance nulle" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Accédez à [**_Évaluer et pilotez Microsoft 365 Defender_**](defender/eval-overview.md) pour obtenir un guide méthodical sur le pilote et le déploiement de composants Microsoft 365 Defender.

|Comprend|Conditions préalables|N’inclut pas|
|---------|---------|---------|
|Configurez l’environnement d’évaluation et de pilote pour tous les composants : <ul><li>Defender pour l’identité</li><li>Defender pour Office 365</li><li>Defender pour point de terminaison</li><li>Microsoft Defender for Cloud Apps</li></ul> <br> Protéger contre les menaces <br><br> Examiner les menaces et y répondre|Consultez les conseils pour en savoir plus sur les exigences d’architecture pour chaque composant de Microsoft 365 Defender.| Azure AD Identity Protection n’est pas inclus dans ce guide de solution. Il est inclus à [l’étape 1. Configurez Confiance nulle protection d’identité et d’accès aux appareils](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>Étape 5. Protéger et régir les données sensibles

Implémentez Microsoft Purview Information Protection pour vous aider à découvrir, classer et protéger des informations sensibles où qu’elles résident ou voyagent.

Microsoft Purview Information Protection fonctionnalités sont incluses dans Microsoft Purview et vous donnent les outils nécessaires pour connaître vos données, protéger vos données et éviter la perte de données.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Fonctionnalités de protection des informations protégeant les données par le biais de l’application des stratégies" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Bien que ce travail soit représenté en haut de la pile de déploiement illustrée plus haut dans cet article, vous pouvez commencer ce travail à tout moment.

Microsoft Purview Information Protection fournit un framework, un processus et des fonctionnalités que vous pouvez utiliser pour atteindre vos objectifs métier spécifiques.

![Microsoft Purview Information Protection](../media/zero-trust/mip-solution-overview.png)

Pour plus d’informations sur la planification et le déploiement de la protection des informations, consultez [**_Déployer une solution Information Protection Microsoft Purview_**](../compliance/information-protection-solution.md). 

Si vous déployez la protection des informations pour les réglementations de confidentialité des données, ce guide de solution fournit une infrastructure recommandée pour l’ensemble du processus : [**_déployer la protection des informations pour les réglementations de confidentialité des données avec Microsoft 365_**](../solutions/information-protection-deploy.md).
