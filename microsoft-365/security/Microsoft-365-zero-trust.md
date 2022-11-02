---
title: Confiance nulle plan de déploiement avec Microsoft 365
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Découvrez comment appliquer Confiance nulle principes de sécurité avec Microsoft 365 pour vous défendre contre les menaces et protéger les données sensibles.
ms.topic: tutorial
ms.service: microsoft-365-security
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- m365-security
- zerotrust-solution
- highpri
- tier1
ms.openlocfilehash: de227a1f4524770709e1a25345cfbdb697076c8d
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815592"
---
# <a name="zero-trust-deployment-plan-with-microsoft-365"></a>Confiance nulle plan de déploiement avec Microsoft 365

Cet article fournit un plan de déploiement pour créer **Confiance nulle** sécurité avec Microsoft 365. Confiance nulle est un nouveau modèle de sécurité qui suppose une violation et vérifie chaque requête comme si elle provenait d’un réseau non contrôlé. Quel que soit l’origine de la demande ou la ressource à laquelle elle accède, le modèle Confiance nulle nous apprend à « ne jamais faire confiance, toujours vérifier ».

Utilisez cet article avec cette affiche.

| Élément | Description |
|:-----|:-----|
|[![Illustration du plan de déploiement microsoft 365 Confiance nulle.](../media/solutions-architecture-center/m365-zero-trust-deployment-plan-thumb.png) ](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) <br/> [PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) \| [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx) <br/> Mise à jour de mars 2022 | **Guides de solution associés** <br/> <ul><li>[Déployer votre infrastructure d’identité pour Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview)</li><li>[Configurations d’identité et d’accès aux appareils recommandées](../security/office-365-security/microsoft-365-policies-configurations.md)</li><li>[Gérer des appareils avec Intune](../solutions/manage-devices-with-intune-overview.md)</li><li>[Évaluer et piloter Microsoft 365 Defender](../security/defender/eval-overview.md)</li><li>[Déployer une solution de protection des informations avec Microsoft Purview](../compliance/information-protection-solution.md)</li><li>[Déployer la protection des informations pour les réglementations en matière de confidentialité des données avec Microsoft 365](../solutions/information-protection-deploy.md)</li></ul>

## <a name="zero-trust-security-architecture"></a>architecture de sécurité Confiance nulle

Une approche Confiance nulle s’étend à l’ensemble du patrimoine numérique et sert de philosophie de sécurité intégrée et de stratégie de bout en bout.

Cette illustration fournit une représentation des éléments principaux qui contribuent à Confiance nulle.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Architecture de sécurité Confiance nulle" lightbox="../media/zero-trust/zero-trust-architecture.png":::

Dans cette illustration :

- L’application de la stratégie de sécurité est au centre d’une architecture Confiance nulle. Cela inclut l’authentification multifacteur avec accès conditionnel qui prend en compte le risque lié au compte d’utilisateur, l’état de l’appareil et d’autres critères et stratégies que vous définissez.
- Les identités, les appareils, les données, les applications, le réseau et d’autres composants d’infrastructure sont tous configurés avec une sécurité appropriée. Les stratégies configurées pour chacun de ces composants sont coordonnées avec votre stratégie de Confiance nulle globale. Par exemple, les stratégies d’appareil déterminent les critères pour les appareils sains et les stratégies d’accès conditionnel nécessitent des appareils intègres pour accéder à des applications et des données spécifiques.
- La protection contre les menaces et le renseignement surveillent l’environnement, exposent les risques actuels et prennent des mesures automatisées pour corriger les attaques.

Pour plus d’informations sur Confiance nulle, consultez [_**le Centre d’aide Confiance nulle**_](/security/zero-trust) de Microsoft.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](/security/zero-trust/zero-trust-ramp-overview).
-->

## <a name="deploying-zero-trust-for-microsoft-365"></a>Déploiement de Confiance nulle pour Microsoft 365

Microsoft 365 est conçu intentionnellement avec de nombreuses fonctionnalités de sécurité et de protection des informations pour vous aider à créer des Confiance nulle dans votre environnement. La plupart des fonctionnalités peuvent être étendues pour protéger l’accès à d’autres applications SaaS utilisées par votre organisation et aux données au sein de ces applications.

Cette illustration représente le travail de déploiement de fonctionnalités Confiance nulle. Ce travail est divisé en unités de travail qui peuvent être configurées ensemble, en commençant par le bas et en haut pour vous assurer que le travail requis est terminé.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Pile de déploiement Microsoft 365 Confiance nulle" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

Dans cette illustration :

- Confiance nulle commence par une base de protection des identités et des appareils.
- Les fonctionnalités de protection contre les menaces reposent sur cette base pour fournir une surveillance et une correction en temps réel des menaces de sécurité.
- La protection et la gouvernance des informations fournissent des contrôles sophistiqués ciblant des types spécifiques de données pour protéger vos informations les plus précieuses et vous aider à vous conformer aux normes de conformité, y compris la protection des informations personnelles.


Cet article part du principe que vous avez déjà configuré l’identité cloud. Si vous avez besoin d’aide pour cet objectif, consultez [**Déployer votre infrastructure d’identité pour Microsoft 365**](/microsoft-365/enterprise/deploy-identity-solution-overview).

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Étape 1. Configurer Confiance nulle protection de l’identité et de l’accès aux appareils : stratégies de point de départ

La première étape consiste à créer votre base de Confiance nulle en configurant la protection des identités et de l’accès aux appareils.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Processus de configuration de Confiance nulle protection de l’identité et de l’accès aux appareils" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

Accédez à [**_Confiance nulle protection de l’identité et de l’accès aux appareils_**](office-365-security/microsoft-365-policies-configurations.md) pour obtenir des instructions normatives à cette fin. Cette série d’articles décrit un ensemble de configurations préalables d’accès aux identités et aux appareils, ainsi qu’un ensemble de stratégies d’accès conditionnel Azure Active Directory (Azure AD), de Microsoft Intune et d’autres stratégies pour sécuriser l’accès à Microsoft 365 pour les services et applications cloud d’entreprise, les autres services SaaS et les applications locales publiées avec Azure AD Proxy d'application.

|Comprend|Configuration requise|N’inclut pas|
|---------|---------|---------|
|Stratégies d’identité et d’accès aux appareils recommandées pour trois niveaux de protection : <ul><li>Point de départ</li><li>Entreprise (recommandé)</li><li>Spécialisé</li></ul> <br> Recommandations supplémentaires pour : <ul><li>Utilisateurs externes (invités)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Microsoft Defender for Cloud Apps</lu></ul>|Microsoft E3 ou E5 <br><br> Azure Active Directory dans l’un des modes suivants : <ul><li>Cloud uniquement</li><li>Hybride avec authentification de synchronisation de hachage de mot de passe (PHS)</li><li>Hybride avec authentification directe (PTA)</li><li>Fédérés</li></ul>|Inscription des appareils pour les stratégies qui nécessitent des appareils gérés. Consultez [l’étape 2. Gérer les points de terminaison avec Intune](#step-2-manage-endpoints-with-intune) pour inscrire des appareils|

Commencez par implémenter le niveau de point de départ. Ces stratégies ne nécessitent pas l’inscription d’appareils dans la gestion.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Le Confiance nulle les stratégies d’identité et d’accès aux appareils : niveau de point de départ" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>Étape 2. Gérer les points de terminaison avec Intune

Ensuite, inscrivez vos appareils dans la gestion et commencez à les protéger avec des contrôles plus sophistiqués.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="L’élément Gérer les points de terminaison avec Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

Accédez à [**_Gérer les appareils avec Intune_**](../solutions/manage-devices-with-intune-overview.md) pour obtenir des instructions normatives à cette fin.

|Comprend|Configuration requise|N’inclut pas|
|---------|---------|---------|
|Inscrire des appareils avec Intune : <ul><li>Appareils d’entreprise</li><li>Autopilot/automatisé</li><li>Inscription</li></ul> <br> Configurer des stratégies : <ul><li>Stratégies de protection des applications</li><li>Stratégies de conformité</li><li>Stratégies de profil d’appareil</li></ul>|Inscrire des points de terminaison auprès d’Azure AD|Configuration des fonctionnalités de protection des informations, notamment : <ul><li>Types d’informations sensibles</li><li>Étiquettes</li><li>Stratégies de protection contre la perte de données</li></ul> <br> Pour ces fonctionnalités, consultez [Étape 5. Protéger et régir les données sensibles](#step-5-protect-and-govern-sensitive-data) (plus loin dans cet article).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Étape 3. Ajouter Confiance nulle protection de l’identité et de l’accès aux appareils — Stratégies d’entreprise

Avec les appareils inscrits dans la gestion, vous pouvez désormais implémenter l’ensemble complet des stratégies d’identité et d’accès aux appareils Confiance nulle recommandées, nécessitant des appareils conformes.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Le Confiance nulle les stratégies d’identité et d’accès avec la gestion des appareils" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Revenez à [**_Stratégies communes d’identité et d’accès aux appareils_**](office-365-security/identity-access-policies.md) et ajoutez les stratégies au niveau Entreprise.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Stratégies d’identité et d’accès Confiance nulle - Niveau Entreprise (recommandé)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Étape 4. Évaluer, piloter et déployer des Microsoft 365 Defender

Microsoft 365 Defender est une solution de détection et de réponse étendue (XDR) qui collecte, met en corrélation et analyse automatiquement les données de signal, de menace et d’alerte de votre environnement Microsoft 365, y compris les points de terminaison, les e-mails, les applications et les identités.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Processus d’ajout de Microsoft 365 Defender à l’architecture Confiance nulle" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Accédez à [**_Évaluer et pilote Microsoft 365 Defender_**](defender/eval-overview.md) pour obtenir un guide méthodique sur le pilotage et le déploiement de composants Microsoft 365 Defender.

|Comprend|Configuration requise|N’inclut pas|
|---------|---------|---------|
|Configurez l’environnement d’évaluation et pilote pour tous les composants : <ul><li>Defender pour l’identité</li><li>Defender pour Office 365</li><li>Defender pour point de terminaison</li><li>Microsoft Defender for Cloud Apps</li></ul> <br> Protéger contre les menaces <br><br> Examiner les menaces et y répondre|Consultez les instructions pour en savoir plus sur les exigences d’architecture pour chaque composant de Microsoft 365 Defender.| Azure AD Identity Protection n’est pas inclus dans ce guide de solution. Il est inclus à [l’étape 1. Configurez Confiance nulle protection des identités et de l’accès aux appareils](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>Étape 5. Protéger et régir les données sensibles

Implémentez Protection des données Microsoft Purview pour vous aider à découvrir, classifier et protéger les informations sensibles où qu’elles se trouvent ou voyagent.

Protection des données Microsoft Purview fonctionnalités sont incluses dans Microsoft Purview et vous donnent les outils nécessaires pour connaître vos données, protéger vos données et éviter toute perte de données.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Fonctionnalités de protection des informations protégeant les données par le biais de l’application de la stratégie" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Bien que ce travail soit représenté en haut de la pile de déploiement illustrée plus haut dans cet article, vous pouvez commencer ce travail à tout moment.

Protection des données Microsoft Purview fournit une infrastructure, un processus et des fonctionnalités que vous pouvez utiliser pour atteindre vos objectifs métier spécifiques.

![Protection de l'information Microsoft Purview](../media/zero-trust/mip-solution-overview.png)

Pour plus d’informations sur la planification et le déploiement de la protection des informations, consultez [**_Déployer une solution Protection des données Microsoft Purview_**](../compliance/information-protection-solution.md). 

Si vous déployez des réglementations en matière de protection des informations pour la confidentialité des données, ce guide de solution fournit une infrastructure recommandée pour l’ensemble du processus : [**_Déployer la protection des informations pour les réglementations en matière de confidentialité des données avec Microsoft 365_**](../solutions/information-protection-deploy.md).
