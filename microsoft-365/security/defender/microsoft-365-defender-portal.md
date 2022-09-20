---
title: Portail Microsoft 365 Defender
description: Le portail Microsoft 365 Defender combine la protection, la détection, l’investigation et la réponse aux menaces de messagerie, de collaboration, d’identité, d’appareil et d’application, dans un emplacement central.
keywords: présentation de MMicrosoft 365 Defender, cybersécurité, menace persistante avancée, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, investigation et correction automatisées, repérage avancé
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- admindeeplinkDEFENDER
- intro-overview
ms.topic: conceptual
adobe-target: true
ms.openlocfilehash: 70a262cd53bed114bd8d4a8e737c796b13bd831a
ms.sourcegitcommit: 078149c9645ce220911ccd6ce54f984a4c92ce53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2022
ms.locfileid: "67809418"
---
# <a name="microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Le [portail Microsoft 365 Defender](https://sip.security.microsoft.com/homepage) combine la protection, la détection, l’investigation et la réponse aux menaces de messagerie, de collaboration, d’identité, d’appareil et d’application cloud, dans un emplacement central. Le portail Microsoft 365 Defender met l’accent sur l’accès rapide aux informations, les dispositions plus simples et le regroupement d’informations connexes pour faciliter leur utilisation. Elle comprend :

- **[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender pour Office 365 aide les organisations à sécuriser leur entreprise avec un ensemble de fonctionnalités de prévention, de détection, d’investigation et de chasse pour protéger les e-mails et les ressources Office 365.
- **[Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** offre une protection préventive, une détection post-violation, une investigation automatisée et une réponse pour les appareils de votre organisation.
- **[Microsoft Defender pour Identity](/defender-for-identity/what-is)** est une solution de sécurité basée sur le cloud qui tire parti de vos signaux Active Directory local pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation.
- **[Microsoft Defender for Cloud Apps](/cloud-app-security/)** est une solution multisaS et PaaS complète qui offre une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces pour vos applications cloud.

Regardez cette courte vidéo pour en savoir plus sur le portail Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

## <a name="what-to-expect"></a>À quoi s'attendre

Le portail Microsoft 365 Defender permet aux équipes de sécurité d’examiner et de répondre aux attaques en intégrant des signaux provenant de différentes charges de travail dans un ensemble d’expériences unifiées pour :

- Incidents et alertes
- Repérage
- Actions & soumissions
- Analyses de menaces
- Niveau de sécurité
- Hub d’apprentissage
- Essais

Microsoft 365 Defender met l’accent sur *l’unité, la clarté et les objectifs communs*. 

> [!NOTE]
> Le portail Microsoft 365 Defender est accessible sans qu’il soit nécessaire pour les clients d’effectuer des étapes de migration ou d’acheter une nouvelle licence. Par exemple, ce nouveau portail est accessible aux administrateurs disposant d’un abonnement E3, tout comme à ceux qui ont Microsoft Defender pour Office 365 Plan 1 et Plan 2 ; toutefois, Exchange Online Protection ou Defender pour Office 365  Les clients plan 1 voient uniquement les fonctionnalités de sécurité prises en charge par leur licence d’abonnement. L’objectif du portail est de centraliser la sécurité.

## <a name="incident-and-alert-investigations"></a>Enquêtes sur les incidents et les alertes

La centralisation des informations de sécurité crée un emplacement unique pour l’examen des incidents de sécurité dans Microsoft 365. Un exemple principal est **incidents** sous **Incidents & alertes**.

:::image type="content" source="../../media/converged-incidents-2.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender" lightbox="../../media/converged-incidents-2.png":::

La sélection d’un nom d’incident affiche une page qui illustre la valeur de la centralisation des informations de sécurité, car vous aurez de meilleurs insights sur l’étendue complète d’une menace, de l’e-mail à l’identité, en passant par les points de terminaison.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Page Résumé d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/converged-incident-info-3.png":::

Prenez le temps d’examiner les incidents dans votre environnement, d’explorer chaque alerte et de vous entraîner à comprendre comment accéder aux informations et déterminer les étapes suivantes de votre analyse.

Pour plus d’informations, consultez [les incidents dans Microsoft 365 Defender](incidents-overview.md).

## <a name="hunting"></a>Repérage
Vous pouvez créer des règles de détection personnalisées et rechercher des menaces spécifiques dans votre environnement. **La chasse** utilise un outil de chasse aux menaces basé sur une requête qui vous permet d’inspecter de manière proactive les événements de votre organisation pour localiser les indicateurs de menace et les entités. Ces règles s’exécutent automatiquement pour rechercher, puis répondre aux suspicions d’activité de violation, aux machines mal configurées et à d’autres résultats.

Pour plus d’informations, consultez [La chasse proactive contre les menaces avec la chasse avancée dans Microsoft 365 Defender](advanced-hunting-overview.md).

## <a name="improved-processes"></a>Processus améliorés

Les contrôles et le contenu courants apparaissent au même endroit ou sont condensés dans un flux de données, ce qui facilite leur recherche. Par exemple, les paramètres unifiés.

### <a name="unified-settings"></a>Paramètres unifiés

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Page Paramètres dans le portail Microsoft 365 Defender" lightbox="../../media/converged-add-role-9.png":::

### <a name="permissions--roles"></a>Autorisations & rôles

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Les rôles de points de terminaison & groupes affichés sur la page Autorisations & rôles" lightbox="../../media/converged-roles-5.png":::

L’accès à Microsoft 365 Defender est configuré avec des rôles globaux Azure AD ou à l’aide de rôles personnalisés.

- En savoir plus sur la [gestion de l’accès à Microsoft 365 Defender](m365d-permissions.md)
- En savoir plus sur la [création de rôles personnalisés](custom-roles.md) dans Microsoft 365 Defender


### <a name="integrated-reports"></a>Rapports intégrés

Les rapports sont également unifiés dans Microsoft 365 Defender. Les administrateurs peuvent commencer par un rapport de sécurité général et créer des rapports spécifiques sur les points de terminaison, l’e-mail & la collaboration. Les liens ici sont générés dynamiquement en fonction de la configuration de la charge de travail.

### <a name="quickly-view-your-microsoft-365-environment"></a>Afficher rapidement votre environnement Microsoft 365

La page **d’accueil** affiche de nombreuses cartes courantes dont les équipes de sécurité ont besoin. La composition des cartes et des données dépend du rôle d’utilisateur. Étant donné que Microsoft 365 Defender portail utilise le contrôle d’accès en fonction du rôle, différents rôles voient des cartes plus significatives pour leurs tâches quotidiennes.

Ces informations en un clin d’œil vous aident à suivre les dernières activités de votre organisation. Microsoft 365 Defender rassemble les signaux de différentes sources pour présenter une vue holistique de votre environnement Microsoft 365.

Vous pouvez ajouter et supprimer différentes cartes en fonction de vos besoins.

### <a name="search-across-entities-preview"></a>Rechercher entre les entités (préversion)

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.
La barre de recherche se trouve en haut de la page. Lorsque vous tapez, des suggestions sont fournies afin qu’il soit plus facile de trouver des entités. La page des résultats de recherche améliorés centralise les résultats de toutes les entités.

Vous pouvez rechercher parmi les entités suivantes dans Defender pour point de terminaison et Defender pour Identity : 

- **Appareils** pris en charge pour Defender pour point de terminaison et Defender pour Identity. Prend en charge l’utilisation d’opérateurs de recherche. 
- **Utilisateurs** : pris en charge pour Defender pour point de terminaison, Defender pour Identity et Defender pour les applications cloud. 
- **Fichiers, adresses IP et URL** - mêmes fonctionnalités que dans Defender pour point de terminaison.

    >[!NOTE]
    >Les recherches d’adresses IP et d’URL correspondent exactement et n’apparaissent pas dans la page des résultats de la recherche . Elles mènent directement à la page d’entité. 

- **MDVM** : mêmes fonctionnalités que dans Defender pour point de terminaison (vulnérabilités, logiciels et recommandations). 

## <a name="threat-analytics"></a>Analyses de menaces

Suivez et répondez aux menaces émergentes avec l’analyse des menaces Microsoft 365 Defender suivante : l’analytique des menaces est la solution de renseignement sur les menaces Microsoft 365 Defender par des experts en sécurité Microsoft. Il est conçu pour aider les équipes de sécurité à être aussi efficaces que possible face aux menaces émergentes, telles que :

- Acteurs de menaces actifs et leurs campagnes
- Techniques d’attaque populaires et nouvelles
- Vulnérabilités critiques
- Surface d'attaque courantes
- Programmes malveillants répandus

## <a name="learning-hub"></a>Hub d’apprentissage

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> comprend un hub d’apprentissage qui fournit des conseils à partir de ressources telles que le blog de sécurité Microsoft, la communauté de sécurité Microsoft sur YouTube et la documentation officielle.

> [!NOTE]
> Il existe **des filtres utiles** en haut de Microsoft 365 Defender hub d’apprentissage qui vous permettent de choisir entre les produits (actuellement Microsoft 365 Defender, Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365). Notez que le nombre de ressources d’apprentissage pour chaque section est répertorié, ce qui peut aider les apprenants à suivre le nombre de ressources dont ils disposent pour la formation et l’apprentissage.
>
> Outre le filtre Produit, les rubriques actuelles, les types de ressources (des vidéos aux webinaires), les niveaux de connaissance ou d’expérience des zones de sécurité, les rôles de sécurité et les fonctionnalités de produit sont répertoriés.

> [!TIP]
> Il existe de nombreuses autres opportunités d’apprentissage dans [Microsoft Learn](/training/). Vous trouverez une formation de certification telle que [le cours MS-500T02-A : Implémentation de la protection microsoft 365 contre les menaces](/training/certifications/courses/ms-500t02).

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires

Nous avons besoin de vos commentaires. Nous cherchons toujours à nous améliorer. Par conséquent, si vous souhaitez voir quelque chose, [regardez cette vidéo pour savoir comment nous faire confiance pour lire vos commentaires](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

## <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Découvrir ce que le portail Microsoft 365 Defender a à offrir

Continuez à explorer les fonctionnalités et les fonctionnalités dans Microsoft 365 Defender :

- [Gérer les incidents et les alertes](manage-incidents.md)
- [Suivre et répondre aux menaces émergentes avec l’analytique des menaces](threat-analytics.md)
- [Le centre des actions](m365d-action-center.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications, et les identités](./advanced-hunting-query-emails-devices.md)
- [Règles de détection personnalisée](./custom-detection-rules.md)
- [Alertes d’e-mail et collaboration](../../compliance/alert-policies.md#default-alert-policies)
- [Créer une simulation d’attaque par hameçonnage](../office-365-security/attack-simulation-training.md) et [créer une charge utile pour entraîner vos équipes](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)

## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Avec ce parcours d’apprentissage de Microsoft Learn, vous pouvez comprendre Microsoft 365 Defender et comment il peut aider à identifier, contrôler et corriger les menaces de sécurité.

|Formation :|Détecter les cyberattaques et y répondre avec Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender de formation.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Microsoft 365 Defender unifie les signaux de menace sur les points de terminaison, les identités, le courrier électronique et les applications afin de fournir une protection intégrée contre les cyberattaques sophistiquées. Microsoft 365 Defender est l’expérience centrale pour examiner et répondre aux incidents et rechercher de manière proactive les activités de cybersécurité malveillantes en cours.<p> 1 h 38 min - Parcours d’apprentissage - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/training/paths/defender-detect-respond/)


## <a name="see-also"></a>Voir aussi

- [Nouveautés de Microsoft 365 Defender](whats-new.md)
- [Microsoft Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
