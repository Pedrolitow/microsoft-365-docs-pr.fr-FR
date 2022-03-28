---
title: Microsoft 365 Defender
description: Microsoft 365 Defender est une solution de protection contre les menaces coordonnée conçue pour protéger les appareils, l’identité, les données et les applications
keywords: introduction à MMicrosoft 365 Defender, cybersécurité, menace persistante avancée, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
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
ms.openlocfilehash: 28f50cbd362104ba910ed5560e184036fc7f8703
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754638"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Voulez-vous faire l'expérience de Microsoft 365 Defender? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Microsoft 365 Defender est une suite de défense d’entreprise pré-et post-violation unifiée qui coordonne en natif la détection, la prévention, les examens et la réponse sur les points de terminaison, les identités, les messages électroniques et les applications pour fournir une protection intégrée contre les attaques sophistiquées.

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminent l’étendue et l’impact complets de la menace, la façon dont elle est entrée dans l’environnement, ce qu’elle a affecté et son impact actuel sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés.

<center><h2>Services Microsoft 365 Defender</center></h2>
<table><tr><td><center><b><a href="/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint"><b>Microsoft Defender pour point de terminaison</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/office-365-security/overview"><b>Microsoft Defender pour Office 365</b></center></a></td>
<td><center><b><a href="/defender-for-identity/"><b>Microsoft Defender pour l’identité</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Defender pour les applications cloud</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Microsoft 365 Defender interactif

Dans ce guide interactif, vous allez découvrir comment protéger votre organisation à l’Microsoft 365 Defender. Vous verrez comment les Microsoft 365 Defender peuvent vous aider à détecter les risques de sécurité, à examiner les attaques de votre organisation et à prévenir automatiquement les activités dangereuses.

[Consulter le guide interactif](https://aka.ms/M365Defender-InteractiveGuide)

## <a name="microsoft-365-defender-protection"></a>Microsoft 365 Defender protection

Microsoft 365 Defender protection des services :

- **Points de terminaison avec Defender pour point** de terminaison - Defender pour point de terminaison est une plateforme de point de terminaison unifiée pour la protection préventive, la détection post-violation, l’examen automatisé et la réponse.
- **E-mail et collaboration avec Defender pour Office 365** : Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration.
- Identités avec **Defender for Identity and Azure Active Directory (Azure AD) Identity Protection** : Defender for Identity utilise vos signaux AD DS (Active Directory Domain Services) locaux pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. Azure AD Identity Protection automatise la détection et la correction des risques basés sur l’identité dans vos Azure AD.
- **Applications avec Microsoft Defender pour** les applications cloud : Microsoft Defender pour les applications cloud est une solution saaS complète qui apporte une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces à vos applications cloud.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww]

Microsoft 365 Defender’une couche unique entre produits augmente les composants de service individuels pour :

- Protégez-vous contre les attaques et coordonnez les réponses coordonnées au sein des services par le biais du partage de signal et des actions automatisées.
- Narratez l’intégralité de l’attaque sur les alertes, les comportements et le contexte des produits pour les équipes de sécurité en joignant les données sur les alertes, les événements suspects et les ressources impactées aux « incidents ».
- Automatisez la réponse à la compromission en déclenchant une réparation automatique des biens touchés par le biais de corrections automatisées.
- Permettre aux équipes de sécurité d’effectuer une recherche détaillée et efficace des menaces sur les points de terminaison et Office données.

Voici un exemple de la façon dont le portail Microsoft 365 Defender met en corrélation toutes les alertes associées entre les produits en un seul incident.

:::image type="content" source="../../media/overview-incident.png" alt-text="Exemple de page de vue d’ensemble d’un incident" lightbox="../../media/overview-incident.png":::

Voici un exemple de la liste des alertes associées à un incident.

:::image type="content" source="../../media/incident-list.png" alt-text="Exemple de liste d’alertes pour un incident" lightbox="../../media/incident-list.png":::

Voici un exemple de recherche basée sur une requête sur les données brutes des e-mails et des points de terminaison.

:::image type="content" source="../../media/advanced-hunting.png" alt-text="Exemple de recherche avancée et de requête" lightbox="../../media/advanced-hunting.png":::

Microsoft 365 Defender fonctionnalités entre produits sont les suivantes :

- Volet unique entre produits dans le portail **Microsoft 365 Defender** : un affichage central pour toutes les informations sur les détections, les biens touchés, les actions automatisées prises et les preuves associées dans une seule file d’attente et un seul volet dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>. 
- File **d’attente d’incidents combinés** : pour aider les professionnels de la sécurité à se concentrer sur ce qui est critique en garantissant l’étendue complète des attaques, les ressources impactées et les actions de correction automatisées sont regroupées et mises en avant en temps voulu. 
- **Réponse automatique aux menaces** : les informations sur les menaces critiques sont partagées en temps réel entre les produits Microsoft 365 Defender pour aider à arrêter la progression d’une attaque. 

   Par exemple, si un fichier malveillant est détecté sur un point de terminaison protégé par Defender for Endpoint, il demande à Defender de Office 365 d’analyser et de supprimer le fichier de tous les messages électroniques. Le fichier sera bloqué à la vue par l’ensemble Microsoft 365 suite de sécurité.

- **Auto-réparation pour les appareils compromis, les identités des utilisateurs** et les boîtes aux lettres : Microsoft 365 Defender utilise des actions automatiques et des playbooks optimisés par l’IA pour corriger les biens touchés à un état sécurisé. Microsoft 365 Defender utilise les fonctionnalités de correction automatique des produits de la suite pour s’assurer que tous les biens touchés liés à un incident sont automatiquement corrigés lorsque cela est possible.
- **Recherche de** menaces entre produits : les équipes de sécurité peuvent tirer parti de leurs connaissances organisationnelles uniques pour chercher des signes de compromission en créant leurs propres requêtes personnalisées sur les données brutes collectées par les différents produits de protection. Microsoft 365 Defender fournit un accès basé sur une requête à 30 jours de signaux bruts historiques et de données d’alerte sur le point de terminaison et Defender pour Office 365 données.

## <a name="get-started"></a>Prise en main

Microsoft 365 Defender licences doivent être satisfaites avant de pouvoir activer le service dans le portail Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> à l’Microsoft 365 Defender pour plus d’informations, voir :

- [Conditions de licence](prerequisites.md#licensing-requirements)
- [Activer Microsoft 365 Defender](m365d-enable.md)

## <a name="the-microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender combine</a> la protection, la détection, l’examen et la réponse aux e-mails *,* *à la collaboration**, à* l’identité *, aux* appareils et aux menaces d’application, à un endroit central.

Ce volet unique regroupe les fonctionnalités des portails de sécurité Microsoft existants, tels que le portail Microsoft 365 Defender et le Centre de sécurité & conformité Office 365. Le portail Microsoft 365 Defender met l’accent sur l’accès rapide aux informations, des dispositions plus simples et la mise en réseau des informations associées pour faciliter leur utilisation. Elle comprend :

- **[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender pour Office 365 aide les organisations à sécuriser leur entreprise avec un ensemble de fonctionnalités de prévention, de détection, d’examen et de repérage pour protéger les e-mails et Office 365 ressources.
- **[Microsoft Defender pour le point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** offre une protection préventive, une détection post-violation, une enquête automatisée et une réponse pour les appareils de votre organisation.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** fait partie de la solution XDR (*Extended Detection and Response*) de Microsoft qui tire parti du portefeuille de sécurité Microsoft 365 pour analyser automatiquement les données de menace sur plusieurs domaines et créer une image d’une attaque sur un tableau de bord unique.
- **[Microsoft Defender pour les applications cloud](/cloud-app-security/)** est une solution complète entre SaaS et PaaS qui offre une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces pour vos applications cloud.

Si vous avez besoin d’informations sur les changements du Centre de sécurité & conformité Office 365 ou du portail Microsoft 365 Defender, voir :

- [Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender pour Point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Le Microsoft 365 Defender utilise et applique l’accès basé sur les rôles existant et déplace chaque modèle de sécurité vers le portail unifié. Chaque charge de travail convergée dispose de son propre accès basé sur les rôles. Les rôles déjà dans les produits seront convergés automatiquement vers Microsoft 365 Defender’entreprise. Toutefois, Microsoft Defender pour les applications cloud gèrera toujours ses propres rôles et autorisations.

### <a name="what-to-expect"></a>À quoi s’attendre

Tout le contenu de sécurité que vous utilisez dans le Centre de sécurité <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">et conformité Office 365</a> & et le Centre de sécurité Microsoft 365 se trouve désormais dans le portail <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a>

Le portail Microsoft 365 Defender permet aux équipes de sécurité d’examiner et de répondre aux attaques en apportant des signaux provenant de différentes charges de travail dans un ensemble d’expériences unifiées pour :

- Incidents et alertes
- Repérage
- Centre de notifications
- Analyses de menaces

Microsoft 365 Defender met l’accent sur *l’unité,* la clarté et les objectifs communs lors de la fusion de Microsoft Defender pour Office 365 et Microsoft Defender pour le point de terminaison. La fusion a été basée sur les priorités répertoriées ci-dessous et a été réalisée sans compromettre les fonctionnalités que chaque suite de sécurité a apportées à la combinaison de :

- Blocs de construction courants
- Terminologie courante
- Entités courantes
- Parité des fonctionnalités avec d’autres charges de travail

> [!NOTE]
> Le portail Microsoft 365 Defender est accessible sans que les clients n’ont besoin de suivre les étapes de migration ou d’acheter une nouvelle licence. Par exemple, ce nouveau portail est accessible aux administrateurs  titulaires d’un abonnement E3, tout comme les utilisateurs de Microsoft Defender pour Office 365 Plan 1 et Plan 2 ; toutefois, les clients Exchange Online Protection ou Defender pour Office 365 Plan 1 voient uniquement les fonctionnalités de sécurité que leur licence d’abonnement prend en charge. L’objectif du portail est de centraliser la sécurité.

### <a name="unified-investigations"></a>Examens unifiés

La centralisation des informations de sécurité crée un endroit unique pour examiner les incidents de sécurité Microsoft 365. Un exemple principal est **incidents** sous **Incidents & alertes** sur le lancement rapide de Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Exemple de page Incidents dans Microsoft 365 Defender" lightbox="../../media/converged-incidents-2.png.png":::

La sélection d’un nom d’incident affiche une page qui illustre la valeur de la centralisation des informations de sécurité.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Exemple de page Résumé d’un incident dans Microsoft 365 Defender" lightbox="../../media/converged-incident-info-3.png":::

En haut d’une page d’incident, vous verrez les **onglets** **Résumé,** Alertes **, Appareils****,** Utilisateurs, **Boîtes** aux lettres, **Enquêtes****, Preuves** et réponse, et **Graph données.** Sélectionnez ces onglets pour obtenir des informations plus détaillées. Par exemple, l’onglet Utilisateurs affiche des informations pour les utilisateurs à partir de charges de travail convergées (Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité et Microsoft Defender pour les applications cloud) et une gamme de sources telles que les services de domaine Active Directory (AD DS) locaux, les Azure AD et les fournisseurs d’identité tiers. Pour plus d’informations, voir [examiner les utilisateurs](investigate-users.md).

Prenez le temps de passer en revue les incidents dans votre environnement, d’examiner ces onglets et de vous exercer à comprendre comment accéder aux informations fournies pour les incidents pour différents types de menaces.

Pour plus d’informations, [consultez les incidents dans Microsoft 365 Defender](incidents-overview.md).

### <a name="improved-processes"></a>Processus améliorés

Les contrôles courants et le contenu apparaissent au même endroit ou sont condensés dans un flux de données, ce qui facilite leur recherche. Par exemple, les paramètres unifiés.

#### <a name="unified-settings"></a>Paramètres unifiés

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Page Paramètres du portail Microsoft 365 Defender web" lightbox="../../media/converged-add-role-9.png":::

#### <a name="permissions--roles"></a>Autorisations & rôles

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Page Autorisations & rôles affichant les rôles endpoints & groupes, rôles et groupes d’appareils" lightbox="../../media/converged-roles-5.png":::

L’accès Microsoft 365 Defender est configuré avec Azure AD rôles globaux ou à l’aide de rôles personnalisés. Pour Defender pour le point de terminaison, voir Attribuer un accès utilisateur [au portail Microsoft 365 Defender web](/microsoft-365/security/defender-endpoint/assign-portal-access). Pour Defender for Office 365, voir [Autorisations dans les Centre de conformité Microsoft 365 et Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- En savoir plus sur la gestion [de l’accès aux Microsoft 365 Defender](m365d-permissions.md)
- En savoir plus sur la création [de rôles personnalisés](custom-roles.md) dans Microsoft 365 Defender

> [!NOTE]
> Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender prend en charge l’octroi de l’accès aux fournisseurs de services de sécurité [gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que l’accès est accordé dans le portail [Microsoft 365 Defender](./mssp-access.md).

#### <a name="integrated-reports"></a>Rapports intégrés

Les rapports sont également unifiés dans Microsoft 365 Defender. Les administrateurs peuvent commencer par un rapport de sécurité général et se brancher à des rapports spécifiques sur les points de terminaison, les e-mails & collaboration. Les liens ici sont générés dynamiquement en fonction de la configuration de la charge de travail.

#### <a name="quickly-view-your-microsoft-365-environment"></a>Afficher rapidement votre environnement de Microsoft 365 de travail

La page **d’accueil** affiche la plupart des cartes courantes dont les équipes de sécurité ont besoin. La composition des cartes et des données dépend du rôle d’utilisateur. Étant donné Microsoft 365 Defender portail utilise le contrôle d’accès basé sur les rôles, différents rôles voient des cartes plus significatives pour leur travail quotidien.

Ces informations rapides vous permettent de suivre les dernières activités de votre organisation. Microsoft 365 Defender rassemble les signaux provenant de différentes sources pour présenter une vue globale de Microsoft 365 environnement.

Les cartes sont dans les catégories suivantes :

- **Identités** : surveillez les identités de votre organisation et suivez les comportements suspects ou risqués. [En savoir plus sur la protection des identités](/azure/active-directory/identity-protection/overview-identity-protection).
- **Données :** permettent de suivre l’activité des utilisateurs qui peut entraîner une divulgation non autorisée des données.
- **Appareils** : obtenez des informations à jour sur les alertes, l’activité de violation et d’autres menaces sur vos appareils.
- **Applications** : obtenir des informations sur la façon dont les applications cloud sont utilisées dans votre organisation. [En savoir plus sur les applications découvertes dans Defender pour les applications cloud](/cloud-app-security/discovered-apps).


#### <a name="search-across-entities-preview"></a>Rechercher entre entités (prévisualisation)

>[!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.
La barre de recherche se trouve en haut de la page. Lorsque vous tapez, des suggestions sont fournies afin de faciliter la recherche d’entités. La page des résultats de recherche améliorés centralise les résultats de toutes les entités.

Vous pouvez effectuer des recherches dans les entités suivantes dans Defender for Endpoint et Defender for Identity : 

- **Appareils** - pris en charge à la fois pour Defender pour endpoint et Defender pour l’identité. Prend en charge l’utilisation des opérateurs de recherche. 
- **Utilisateurs** - pris en charge pour Defender pour le point de terminaison, Defender pour l’identité et Defender pour les applications cloud. 
- **Fichiers, adresses IPS et URL : mêmes fonctionnalités** que dans Defender pour le point de terminaison.

    >[!NOTE]
    >Les recherches d’ADRESSES IP et d’URL correspondent exactement et n’apparaissent pas dans la page des résultats de la recherche : elles mènent directement à la page d’entité. 

- **TVM** - mêmes fonctionnalités que dans Defender pour point de terminaison (vulnérabilités, logiciels et recommandations). 

 





### <a name="threat-analytics-with-better-data-coverage"></a>Analyse des menaces avec une meilleure couverture de données

Suivez les menaces émergentes et répondez-y à l’Microsoft 365 Defender l’expérience intégrée de l’analyse des menaces :

- Meilleure couverture des données entre Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365, ce qui rend possible la gestion combinée des incidents, l’examen automatique, la correction et la recherche proactive ou réactive de menaces sur plusieurs domaines.
- Détections et atténuations liées à la messagerie électronique de Microsoft Defender pour Office 365, en plus des données de point de terminaison déjà disponibles à partir de Microsoft Defender for Endpoint.
- Une vue des incidents liés aux menaces qui regroupent les alertes dans des articles d’attaque de bout en bout dans Microsoft Defender pour Point de terminaison et Microsoft Defender pour Office 365 afin de réduire la file d’attente de travail, ainsi que simplifier et accélérer votre enquête.
- Les tentatives d’attaque détectées et bloquées par Microsoft 365 Defender solutions. Il existe également des données que vous pouvez utiliser pour piloter des actions préventives qui atténuent les risques d’exposition supplémentaire et augmentent la résilience.
- Conception améliorée qui place des informations exploitables à la une pour vous aider à identifier rapidement les données sur qui il est urgent de se concentrer, d’examiner et de tirer parti des rapports.

### <a name="a-centralized-learning-hub"></a>Un hub Learning centralisé

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail</a> inclut un hub d’apprentissage qui publie des conseils officiels à partir de ressources telles que le blog sur la sécurité Microsoft, la communauté de sécurité Microsoft sur YouTube et la documentation officielle sur docs.microsoft.com.

À l’intérieur du hub d’apprentissage, les conseils de collaboration de & de messagerie (Microsoft Defender pour Office 365) sont côte à côte avec Endpoint (Microsoft Defender pour Endpoint) et Microsoft 365 Defender ressources d’apprentissage.

Le hub d’apprentissage s’ouvre Learning des chemins d’accès organisés autour de rubriques telles que « Comment examiner l’utilisation Microsoft 365 Defender ? » et « Microsoft Defender pour Office 365 meilleures pratiques ». Cette section est actuellement organisée par le groupe produit de sécurité au sein de Microsoft. Chaque Learning chemin d’accès reflète le temps projeté qu’il faut pour passer à travers les concepts. Par exemple, « Étapes à suivre lorsqu’un compte d’utilisateur Microsoft Defender pour Office 365 est compromis » est projeté pour prendre 8 minutes et constitue un apprentissage précieux à la volée.

Après avoir cliqué sur le contenu, il peut être utile de mettre en signet ce site et d’organiser les signets dans un dossier « Sécurité » ou « Critique ». Pour afficher tous les Learning chemins d’accès, cliquez sur le lien Afficher tout dans le panneau principal.

> [!NOTE]
> Il existe des  filtres utiles en haut du hub d’apprentissage Microsoft 365 Defender qui vous permettent de choisir entre les produits (actuellement Microsoft 365 Defender, Microsoft Defender pour point de terminaison et Microsoft Defender pour Office 365). Notez que le nombre de ressources d’apprentissage pour chaque section est répertorié, ce qui peut aider les enseignants à suivre le nombre de ressources dont ils disposent pour la formation et l’apprentissage.
>
> Outre le filtre Produit, les rubriques actuelles, les types de ressources (des vidéos aux webinaires), les niveaux de familiarité ou d’expérience avec les domaines de sécurité, les rôles de sécurité et les fonctionnalités du produit sont répertoriés.

> [!TIP]
> Il existe de nombreuses autres possibilités d’apprentissage [dans Microsoft Learn](/learn/). Vous trouverez des formations de certification telles que le cours [MS-500T02-A : mise en œuvre Microsoft 365 protection contre les menaces](/learn/certifications/courses/ms-500t02).

### <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires

Nous avons besoin de vos commentaires. Nous cherchons toujours à nous améliorer. Ainsi, si vous souhaitez voir quelque chose, regardez cette vidéo pour savoir comment nous faire confiance pour lire [vos commentaires](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Vous pouvez également laisser des commentaires à partir de cet article. Dans la section « Commentaires » à la fin sous « Envoyer et afficher les commentaires pour » , les options sont ce *produit ou* *cette page*.

Utilisez le **bouton Ce produit pour** les commentaires *sur le* produit :

1. *Sélectionnez ce produit* au bas de l’article.
    1. Cliquez avec le bouton droit sur le bouton et « Ouvrir dans un nouvel onglet » si vous souhaitez continuer à lire ces instructions.
2. Cela permet d’accéder au **forum UserVoice**.
3. Vous avez 2 options :
    1. Faites défiler vers le bas jusqu’à la zone de texte Comment pouvons-nous améliorer la conformité ou mieux protéger vos utilisateurs *dans Office 365 ?* et coller dans *Microsoft 365 Defender*. Vous pouvez rechercher dans les résultats une idée comme la vôtre et la voter haut, ou utiliser le bouton publier **une nouvelle idée**.
    1. Si vous pensez que ce problème est déjà signalé et que vous souhaitez augmenter son profil avec un vote (ou des votes),  utilisez la zone Donner des commentaires sur le côté droit de UserVoice. Recherchez *Microsoft 365 Defender*, **recherchez le problème et** utilisez le bouton de vote pour augmenter son état.

Utilisez *cette page pour* obtenir des commentaires sur l’article lui-même. Merci pour vos commentaires. Votre voix nous aide à améliorer les produits.

### <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Découvrez ce que Microsoft 365 Defender portail de recherche a à offrir

Continuez à explorer les fonctionnalités et fonctionnalités dans Microsoft 365 Defender :

- [Gérer les incidents et les alertes](manage-incidents.md)
- [Suivre et répondre aux menaces émergentes avec l’analytique des menaces](threat-analytics.md)
- [Le centre des actions](m365d-action-center.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications, et les identités](./advanced-hunting-query-emails-devices.md)
- [Règles de détection personnalisée](./custom-detection-rules.md)
- [Alertes d’e-mail et collaboration](../../compliance/alert-policies.md#default-alert-policies)
- [Créer une simulation d’attaque par hameçonnage](../office-365-security/attack-simulation-training.md) et [créer une charge utile pour former vos équipes](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)

## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Grâce à ce parcours d’apprentissage de Microsoft Learn, vous pouvez comprendre Microsoft 365 Defender et comment il peut vous aider à identifier, contrôler et corriger les menaces de sécurité.

|Formation :|Détecter les cyberattaques et y répondre avec Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender de formation.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Microsoft 365 Defender unifie les signaux de menace sur les points de terminaison, les identités, le courrier électronique et les applications afin de fournir une protection intégrée contre les cyberattaques sophistiquées. Microsoft 365 Defender est l’expérience centrale pour examiner et répondre aux incidents et rechercher de manière proactive les activités de cybersécurité malveillantes en cours.<p> 1 h 38 min - Learning chemin d’accès - 5 modules|

> [!div class="nextstepaction"]
> [Démarrer >](/learn/paths/defender-detect-respond/)


## <a name="see-also"></a>Voir aussi

- [Nouveautés de Microsoft 365 Defender](whats-new.md)
- [Microsoft Defender pour Office 365 dans Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
