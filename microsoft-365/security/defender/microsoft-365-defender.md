---
title: Microsoft 365 Defender
description: Microsoft 365 Defender est une solution de protection coordonnée contre les menaces conçue pour protéger les appareils, les identités, les données et les applications
keywords: présentation de MMicrosoft 365 Defender, cybersécurité, menace persistante avancée, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, investigation et correction automatisées, repérage avancé
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
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
- m365solution-m365-defender
- m365solution-scenario
- m365solution-overview
ms.custom:
- admindeeplinkDEFENDER
- intro-overview
ms.topic: conceptual
ms.technology: m365d
adobe-target: true
ms.openlocfilehash: c5c9be7261394dad444cafe5bcb7ff1f8001f742
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940731"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender est une suite de défense d’entreprise pré-et post-violation unifiée qui coordonne en natif la détection, la prévention, les examens et la réponse sur les points de terminaison, les identités, les messages électroniques et les applications pour fournir une protection intégrée contre les attaques sophistiquées.

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace; comment il est entré dans l’environnement, ce qu’il est affecté et comment il impacte actuellement l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et guérir automatiquement les boîtes aux lettres affectées, les points de terminaison et les identités utilisateur.

<center><h2>Services Microsoft 365 Defender</center></h2>
<table><tr><td><center><b><a href="/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint"><b>Microsoft Defender pour point de terminaison</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management"><b>Gestion des vulnérabilités de Microsoft Defender</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/office-365-security/overview"><b>Microsoft Defender pour Office 365</b></center></a></td>
<td><center><b><a href="/defender-for-identity/"><b>Microsoft Defender pour Identity</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Defender pour Cloud Apps</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Guide interactif microsoft 365 Defender

Dans ce guide interactif, vous allez apprendre à protéger votre organisation avec Microsoft 365 Defender. Vous verrez comment Microsoft 365 Defender peut vous aider à détecter les risques de sécurité, à examiner les attaques à votre organisation et à prévenir automatiquement les activités dangereuses.

[Consulter le guide interactif](https://aka.ms/M365Defender-InteractiveGuide)

## <a name="microsoft-365-defender-protection"></a>Protection Microsoft 365 Defender

Les services Microsoft 365 Defender protègent :

- **Points de terminaison avec Defender pour point de terminaison** - Defender pour point de terminaison est une plateforme de point de terminaison unifiée pour la protection préventive, la détection post-violation, l’investigation automatisée et la réponse.
- **Ressources avec Gestion des vulnérabilités Defender** - Microsoft Defender Vulnerability Management offre une visibilité continue des ressources, des évaluations intelligentes basées sur les risques et des outils de correction intégrés pour aider vos équipes informatiques et de sécurité à hiérarchiser et à résoudre les vulnérabilités critiques et les erreurs de configuration au sein de votre organisation.
- **Courrier électronique et collaboration avec Defender pour Office 365** - Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les e-mails, les liens (URL) et les outils de collaboration.
- **Identités avec Defender pour Identity et Azure Active Directory (Azure AD) Identity Protection** - Defender pour Identity utilise vos signaux Active Directory Domain Services (AD DS) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. Azure AD Identity Protection automatise la détection et la correction des risques basés sur l’identité dans votre azure AD basé sur le cloud.
- **Applications avec Microsoft Defender pour Cloud Apps** - Microsoft Defender pour Cloud Apps est une solution multisaS complète qui offre une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces pour vos applications cloud.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww]

La couche unique entre produits de Microsoft 365 Defender augmente les composants de service individuels pour :

- Protégez-vous contre les attaques et coordonnez les réponses défensives dans les services par le biais du partage de signal et des actions automatisées.
- Racontez l’histoire complète de l’attaque entre les alertes de produit, les comportements et le contexte des équipes de sécurité en joignant des données sur des alertes, des événements suspects et des ressources impactées à des « incidents ».
- Automatiser la réponse à la compromission en déclenchant une auto-réparation pour les ressources impactées par le biais d’une correction automatisée.
- Permettre aux équipes de sécurité d’effectuer une chasse détaillée et efficace des menaces sur les points de terminaison et les données Office.

Voici un exemple de la façon dont le portail Microsoft 365 Defender met en corrélation toutes les alertes associées entre les produits en un seul incident.

:::image type="content" source="../../media/overview-incident.png" alt-text="Page vue d’ensemble de l’incident" lightbox="../../media/overview-incident.png":::

Voici un exemple de liste d’alertes associées pour un incident.

:::image type="content" source="../../media/incident-list.png" alt-text="Liste des alertes pour un incident" lightbox="../../media/incident-list.png":::

Voici un exemple de chasse basée sur les requêtes sur les données brutes de l’e-mail et du point de terminaison.

:::image type="content" source="../../media/advanced-hunting.png" alt-text=" Page Repérage avancé avec les détails de la requête" lightbox="../../media/advanced-hunting.png":::

Les fonctionnalités multi-produits microsoft 365 Defender sont les suivantes :

- **Volet de verre unique entre produits dans le portail Microsoft 365 Defender** : vue centrale pour toutes les informations sur les détections, les ressources affectées, les actions automatisées effectuées et les preuves connexes dans une seule file d’attente et un seul volet dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. 
- **File d’attente d’incidents combinés** : pour aider les professionnels de la sécurité à se concentrer sur ce qui est essentiel en veillant à ce que l’étendue complète des attaques, les ressources affectées et les actions de correction automatisées soient regroupées et exposées en temps voulu. 
- **Réponse automatique aux menaces** : les informations sur les menaces critiques sont partagées en temps réel entre les produits Microsoft 365 Defender pour aider à arrêter la progression d’une attaque. 

   Par exemple, si un fichier malveillant est détecté sur un point de terminaison protégé par Defender pour point de terminaison, il indique à Defender pour Office 365 d’analyser et de supprimer le fichier de tous les messages électroniques. Le fichier sera bloqué à la vue par l’ensemble de la suite de sécurité Microsoft 365.

- **Réparation automatique pour les appareils compromis, les identités utilisateur et les boîtes aux lettres** : Microsoft 365 Defender utilise des actions automatiques et des playbooks basés sur l’IA pour corriger les ressources affectées à un état sécurisé. Microsoft 365 Defender tire parti des fonctionnalités de correction automatique des produits de suite pour s’assurer que toutes les ressources impactées liées à un incident sont automatiquement corrigées si possible.
- **Chasse aux menaces entre produits** : les équipes de sécurité peuvent tirer parti de leurs connaissances organisationnelles uniques pour rechercher des signes de compromission en créant leurs propres requêtes personnalisées sur les données brutes collectées par les différents produits de protection. Microsoft 365 Defender fournit un accès basé sur une requête à 30 jours de signaux bruts historiques et de données d’alerte sur le point de terminaison et les données Defender pour Office 365.

## <a name="get-started"></a>Prise en main

Les exigences de licence Microsoft 365 Defender doivent être remplies avant de pouvoir activer le service dans le portail Microsoft 365 Defender à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> Pour plus d’informations, consultez :

- [Conditions de licence](prerequisites.md#licensing-requirements)
- [Activer Microsoft 365 Defender](m365d-enable.md)

## <a name="the-microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> combine la protection, la détection, l’investigation et la réponse aux *menaces de messagerie*, de *collaboration*, *d’identité*, *d’appareil* et *d’application* , dans un emplacement central.

Ce volet unique regroupe les fonctionnalités des portails de sécurité Microsoft existants, comme le portail Microsoft 365 Defender et le Centre de sécurité & conformité Office 365. Le portail Microsoft 365 Defender met l’accent sur l’accès rapide aux informations, les dispositions plus simples et le regroupement d’informations connexes pour faciliter l’utilisation. Elle comprend :

- **[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender pour Office 365 aide les organisations à sécuriser leur entreprise avec un ensemble de fonctionnalités de prévention, de détection, d’investigation et de repérage pour protéger les e-mails et les ressources Office 365.
- **[Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** offre une protection préventive, une détection post-violation, une investigation automatisée et une réponse pour les appareils de votre organisation.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** fait partie de la solution XDR ( *Extended Detection and Response* ) de Microsoft qui tire parti du portefeuille de sécurité Microsoft 365 pour analyser automatiquement les données de menace entre les domaines et créer une image d’une attaque sur un tableau de bord unique.
- **[Microsoft Defender pour Cloud Apps](/cloud-app-security/)** est une solution multisaS et PaaS complète qui offre une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces pour vos applications cloud.

Si vous avez besoin d’informations sur ce qui a changé à partir du Centre de sécurité & conformité Office 365 ou du portail Microsoft 365 Defender, consultez :

- [Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender pour Point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Le portail Microsoft 365 Defender utilise et applique l’accès en fonction des rôles existants, et déplace chaque modèle de sécurité dans le portail unifié. Chaque charge de travail convergée a son propre accès en fonction des rôles. Les rôles déjà présents dans les produits seront convergés automatiquement vers le portail Microsoft 365 Defender. Toutefois, Microsoft Defender pour Cloud Apps gère toujours ses propres rôles et autorisations.

Regardez cette courte vidéo pour en savoir plus sur le nouveau portail unifié dans Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

### <a name="what-to-expect"></a>À quoi s’attendre

Tout le contenu de sécurité que vous utilisez dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Centre de sécurité & conformité Office 365</a> et le Centre de sécurité Microsoft 365 se trouve désormais dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

Le portail Microsoft 365 Defender permet aux équipes de sécurité d’examiner et de répondre aux attaques en intégrant des signaux provenant de différentes charges de travail dans un ensemble d’expériences unifiées pour :

- Incidents et alertes
- Repérage
- Centre de notifications
- Analyses de menaces

Microsoft 365 Defender met l’accent sur *l’unité, la clarté et les objectifs communs* lorsqu’il fusionne Microsoft Defender pour Office 365 et Microsoft Defender pour point de terminaison. La fusion a été basée sur les priorités répertoriées ci-dessous et effectuée sans sacrifier les fonctionnalités que chaque suite de sécurité a apportées à la combinaison de :

- Blocs de construction courants
- Terminologie courante
- Entités courantes
- Parité des fonctionnalités avec d’autres charges de travail

> [!NOTE]
> Le portail Microsoft 365 Defender est accessible sans qu’il soit nécessaire pour les clients d’effectuer des étapes de migration ou d’acheter une nouvelle licence. Par exemple, ce nouveau portail est accessible aux administrateurs disposant d’un abonnement E3, tout comme à ceux qui ont Microsoft Defender pour Office 365 Plan 1 et Plan 2 ; Toutefois, les clients Exchange Online Protection ou Defender pour Office 365 Plan 1 voient uniquement les fonctionnalités de sécurité prises en charge par leur licence d’abonnement. L’objectif du portail est de centraliser la sécurité.

### <a name="unified-investigations"></a>Examens unifiés

La centralisation des informations de sécurité crée un emplacement unique pour l’examen des incidents de sécurité dans Microsoft 365. Un exemple principal est **incidents** sous **Incidents & alertes** sur le lancement rapide de Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender" lightbox="../../media/converged-incidents-2.png.png":::

La sélection d’un nom d’incident affiche une page qui illustre la valeur de la centralisation des informations de sécurité.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Page Résumé d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/converged-incident-info-3.png":::

En haut d’une page d’incident, vous verrez les **onglets** **Résumé**, Alertes, **Appareils**, **Utilisateurs**, **Boîtes aux lettres**, **Investigations**, **Preuve et réponse**, ainsi que les onglets **Graph**. Sélectionnez ces onglets pour plus d’informations. Par exemple, l’onglet **Utilisateurs** affiche des informations pour les utilisateurs à partir de charges de travail convergées (Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity et Microsoft Defender pour Cloud Apps) et une gamme de sources telles que les services de domaine Active Directory locaux (AD DS), Azure AD et les fournisseurs d’identité tiers. Pour plus d’informations, consultez [examiner les utilisateurs](investigate-users.md).

Prenez le temps d’examiner les incidents dans votre environnement, d’explorer ces onglets et de vous entraîner à comprendre comment accéder aux informations fournies pour les incidents pour différents types de menaces.

Pour plus d’informations, consultez [incidents dans Microsoft 365 Defender](incidents-overview.md).

### <a name="improved-processes"></a>Processus améliorés

Les contrôles et le contenu courants apparaissent au même endroit ou sont condensés dans un flux de données, ce qui facilite leur recherche. Par exemple, les paramètres unifiés.

#### <a name="unified-settings"></a>Paramètres unifiés

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Page Paramètres dans le portail Microsoft 365 Defender" lightbox="../../media/converged-add-role-9.png":::

#### <a name="permissions--roles"></a>Autorisations & rôles

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Les rôles de points de terminaison & groupes affichés sur la page Autorisations & rôles" lightbox="../../media/converged-roles-5.png":::

L’accès à Microsoft 365 Defender est configuré avec des rôles globaux Azure AD ou à l’aide de rôles personnalisés. Pour Defender pour point de terminaison, consultez [Affecter l’accès utilisateur au portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/assign-portal-access). Pour Defender pour Office 365, consultez [Autorisations dans le portail de conformité Microsoft Purview et Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- En savoir plus sur la [gestion de l’accès à Microsoft 365 Defender](m365d-permissions.md)
- En savoir plus sur la [création de rôles personnalisés](custom-roles.md) dans Microsoft 365 Defender

> [!NOTE]
> Microsoft Defender pour point de terminaison dans Microsoft 365 Defender prend en charge [l’octroi de l’accès aux fournisseurs de services de sécurité gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que l’accès est [accordé dans le portail Microsoft 365 Defender](./mssp-access.md).

#### <a name="integrated-reports"></a>Rapports intégrés

Les rapports sont également unifiés dans Microsoft 365 Defender. Les administrateurs peuvent commencer par un rapport de sécurité général et créer des rapports spécifiques sur les points de terminaison, l’e-mail & la collaboration. Les liens ici sont générés dynamiquement en fonction de la configuration de la charge de travail.

#### <a name="quickly-view-your-microsoft-365-environment"></a>Afficher rapidement votre environnement Microsoft 365

La page **d’accueil** affiche de nombreuses cartes courantes dont les équipes de sécurité ont besoin. La composition des cartes et des données dépend du rôle d’utilisateur. Étant donné que le portail Microsoft 365 Defender utilise le contrôle d’accès en fonction du rôle, différents rôles voient des cartes plus significatives pour leurs tâches quotidiennes.

Ces informations en un clin d’œil vous aident à suivre les dernières activités de votre organisation. Microsoft 365 Defender rassemble les signaux de différentes sources pour présenter une vue holistique de votre environnement Microsoft 365.

Les cartes appartiennent aux catégories suivantes :

- **Identités** : surveillez les identités de votre organisation et suivez les comportements suspects ou à risque. [En savoir plus sur la protection des identités](/azure/active-directory/identity-protection/overview-identity-protection).
- **Données** : suivez l’activité des utilisateurs susceptible d’entraîner une divulgation de données non autorisée.
- **Appareils** : obtenez des informations à jour sur les alertes, l’activité de violation et d’autres menaces sur vos appareils.
- **Applications** : découvrez comment les applications cloud sont utilisées dans votre organisation. [En savoir plus sur les applications découvertes dans Defender pour Cloud Apps](/cloud-app-security/discovered-apps).


#### <a name="search-across-entities-preview"></a>Rechercher entre les entités (préversion)

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.
La barre de recherche se trouve en haut de la page. Lorsque vous tapez, des suggestions sont fournies afin qu’il soit plus facile de trouver des entités. La page des résultats de recherche améliorés centralise les résultats de toutes les entités.

Vous pouvez rechercher parmi les entités suivantes dans Defender pour point de terminaison et Defender pour Identity : 

- **Appareils** pris en charge pour Defender pour point de terminaison et Defender pour Identity. Prend en charge l’utilisation d’opérateurs de recherche. 
- **Utilisateurs** : pris en charge pour Defender pour point de terminaison, Defender pour Identity et Defender pour les applications cloud. 
- **Fichiers, adresses IP et URL** - mêmes fonctionnalités que dans Defender pour point de terminaison.

    >[!NOTE]
    >Les recherches d’adresses IP et d’URL correspondent exactement et n’apparaissent pas dans la page des résultats de la recherche . Elles mènent directement à la page d’entité. 

- **TVM** : mêmes fonctionnalités que dans Defender pour point de terminaison (vulnérabilités, logiciels et recommandations). 

 





### <a name="threat-analytics-with-better-data-coverage"></a>Analyse des menaces avec une meilleure couverture des données

Suivez et répondez aux menaces émergentes avec l’expérience intégrée d’analyse des menaces Microsoft 365 Defender suivante :

- Meilleure couverture des données entre Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365, ce qui rend possible la gestion combinée des incidents, l’investigation automatique, la correction et la chasse proactive ou réactive des menaces entre domaines.
- Détections et atténuations liées aux e-mails de Microsoft Defender pour Office 365, en plus des données de point de terminaison déjà disponibles à partir de Microsoft Defender pour point de terminaison.
- Vue des incidents liés aux menaces qui regroupent les alertes en récits d’attaque de bout en bout dans Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365 afin de réduire la file d’attente de travail, ainsi que de simplifier et d’accélérer votre investigation.
- Tentatives d’attaque détectées et bloquées par les solutions Microsoft 365 Defender. Il existe également des données que vous pouvez utiliser pour mener des actions préventives qui atténuent le risque d’exposition supplémentaire et augmentent la résilience.
- Conception améliorée qui met les informations exploitables à l’honneur pour vous aider à identifier rapidement les données sur lesquelles vous pouvez vous concentrer, examiner et tirer parti des rapports de toute urgence.

### <a name="a-centralized-learning-hub"></a>Un hub d’apprentissage centralisé

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> inclut un hub d’apprentissage qui fournit des conseils officiels à partir de ressources telles que le blog de sécurité Microsoft, la communauté de sécurité Microsoft sur YouTube et la documentation officielle de docs.microsoft.com.

À l’intérieur du hub d’apprentissage, les conseils relatifs à la collaboration par e-mail & (Microsoft Defender pour Office 365) sont côte à côte avec le point de terminaison (Microsoft Defender pour point de terminaison) et les ressources d’apprentissage Microsoft 365 Defender.

Le hub d’apprentissage s’ouvre avec des parcours d’apprentissage organisés autour de rubriques telles que « Comment examiner l’utilisation de Microsoft 365 Defender ? » et « Meilleures pratiques de Microsoft Defender pour Office 365 ». Cette section est actuellement organisée par le groupe de produits de sécurité au sein de Microsoft. Chaque parcours d’apprentissage reflète le temps qu’il faut pour passer à travers les concepts. Par exemple, « Les étapes à suivre lorsqu’un compte d’utilisateur Microsoft Defender pour Office 365 est compromis » sont prévues pour prendre 8 minutes et constituent un apprentissage utile à la volée.

Après avoir cliqué sur le contenu, il peut être utile de marquer ce site et d’organiser les signets dans un dossier « Sécurité » ou « Critique ». Pour afficher tous les parcours d’apprentissage, cliquez sur le lien Afficher tout dans le volet principal.

> [!NOTE]
> Il existe **des filtres utiles** en haut du hub d’apprentissage Microsoft 365 Defender qui vous permettent de choisir entre les produits (actuellement Microsoft 365 Defender, Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365). Notez que le nombre de ressources d’apprentissage pour chaque section est répertorié, ce qui peut aider les apprenants à suivre le nombre de ressources dont ils disposent pour la formation et l’apprentissage.
>
> Outre le filtre Produit, les rubriques actuelles, les types de ressources (des vidéos aux webinaires), les niveaux de connaissance ou d’expérience des zones de sécurité, les rôles de sécurité et les fonctionnalités de produit sont répertoriés.

> [!TIP]
> Il existe de nombreuses autres opportunités d’apprentissage dans [Microsoft Learn](/learn/). Vous trouverez une formation de certification telle que [le cours MS-500T02-A : Implémentation de la protection microsoft 365 contre les menaces](/learn/certifications/courses/ms-500t02).

### <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires

Nous avons besoin de vos commentaires. Nous cherchons toujours à nous améliorer. Par conséquent, si vous souhaitez voir quelque chose, [regardez cette vidéo pour savoir comment nous faire confiance pour lire vos commentaires](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Vous pouvez également laisser vos commentaires dans cet article. Dans la section « Commentaires » à la fin sous « Envoyer et afficher les commentaires pour », les options sont *Ce produit* ou *cette page*.

Utilisez le bouton **Ce produit** pour obtenir des commentaires sur *le produit* :

1. Sélectionnez *ce produit* en bas de l’article.
    1. Cliquez avec le bouton droit sur le bouton et ouvrez-le dans un nouvel onglet si vous souhaitez continuer à lire ces instructions.
2. Vous accédez alors au **forum UserVoice**.
3. Vous disposez de 2 options :
    1. Faites défiler jusqu’à la zone de texte *Comment pouvons-nous améliorer la conformité ou mieux protéger vos utilisateurs dans Office 365 ?* et coller dans *Microsoft 365 Defender*. Vous pouvez rechercher dans les résultats une idée comme la vôtre et la voter, ou utiliser le bouton **Publier une nouvelle idée**.
    1. Si vous êtes certain que ce problème est déjà signalé et que vous souhaitez augmenter son profil avec un vote (ou des votes), utilisez la zone *Donner des commentaires* sur le côté droit de UserVoice. Recherchez *Microsoft 365 Defender*, **recherchez le problème et utilisez le bouton Vote** pour augmenter son statut.

Utilisez *cette page* pour obtenir des commentaires sur l’article lui-même. Merci pour vos commentaires. Votre voix nous aide à améliorer les produits.

### <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Découvrir ce que le portail Microsoft 365 Defender a à offrir

Continuez à explorer les fonctionnalités et fonctionnalités de Microsoft 365 Defender :

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
> [Démarrer >](/learn/paths/defender-detect-respond/)


## <a name="see-also"></a>Voir aussi

- [Nouveautés de Microsoft 365 Defender](whats-new.md)
- [Microsoft Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
