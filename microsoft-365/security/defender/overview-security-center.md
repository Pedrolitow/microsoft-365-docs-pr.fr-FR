---
title: Vue d’ensemble du Centre de sécurité Microsoft 365
description: Avantages du Centre de sécurité Microsoft 365, en combinant Microsoft Defender pour Office 365 (MDO) et Microsoft Defender pour le point de terminaison (MDE), avec Microsoft Defender pour l’identité (MDI) et Microsoft Cloud App Security (MCAS). Cet article décrit les progrès réalisés par le Centre de sécurité Microsoft 365 pour les administrateurs.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, identités, données, appareils, applications
ms.prod: m365-security
ms.mktglfcycl: deploy
localization_priority: Normal
f1.keywords:
- NOCSH
ms.date: 02/02/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 142bc305950f9322c90e0d207f255c14abbc6b8c
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51197932"
---
# <a name="the-unified-microsoft-365-security-center-overview"></a>Vue d’ensemble du Centre de sécurité Microsoft 365 unifié

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

> Vous souhaitez découvrir Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou exécuter votre projet pilote en [production.](m365d-pilot.md?ocid=cx-evalpilot)

Le Centre de sécurité **Microsoft 365** amélioré combine la protection, la détection, l’examen et la réponse aux e-mails, à la collaboration, à l’identité et aux menaces d’appareils, dans un [https://security.microsoft.com](https://security.microsoft.com) portail central.    

Le Centre de sécurité Microsoft 365 regroupe les fonctionnalités des portails de sécurité Microsoft existants, tels que le Centre de sécurité Microsoft Defender et le Centre de sécurité & conformité Office 365. Le centre de sécurité met l’accent sur l’accès rapide aux informations, des dispositions plus simples et la mise en commun des informations associées pour faciliter leur utilisation. Ce centre inclut :

- **[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender pour Office 365 aide les organisations à sécuriser leur entreprise avec un ensemble de fonctionnalités de prévention, de détection, d’examen et de repérage pour protéger le courrier électronique et les ressources Office 365.
- **[Microsoft Defender pour le point de terminaison](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** offre une protection préventive, une détection post-violation, une enquête automatisée et une réponse pour les appareils de votre organisation.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** fait partie de la solution XDR *(Extended Detection and Response)* de Microsoft qui tire parti du portefeuille de sécurité Microsoft 365 pour analyser automatiquement les données de menace sur plusieurs domaines et créer une image d’une attaque sur un seul tableau de bord.

Si vous avez besoin d’informations sur les changements du Centre de sécurité & conformité Office 365 ou du Centre de sécurité Microsoft Defender, voir :

- [Defender pour Office 365 dans le Centre de sécurité Microsoft 365](microsoft-365-security-center-mdo.md)
- [Defender pour point de terminaison dans le Centre de sécurité Microsoft 365](microsoft-365-security-center-mde.md)

## <a name="what-to-expect"></a>À quoi s’attendre

Tout le contenu de sécurité que vous utilisez dans le Centre de sécurité et conformité Office 365 (protection.office.com) et le Centre de sécurité Microsoft Defender (securitycenter.microsoft.com) se trouve désormais dans le Centre de sécurité *Microsoft 365.*

Le Centre de sécurité Microsoft 365 permet aux équipes de sécurité d’examiner les attaques et de répondre à ces attaques en axant les signaux de différentes charges de travail dans une expérience unifiée unique :

- Incidents & alertes
- Repérage
- Centre de notifications
- Analyses de menaces

Le Centre de sécurité Microsoft  365 met l’accent sur l’unité, la clarté et les objectifs communs lors de la fusion de Microsoft Defender pour Office 365 et Microsoft Defender pour le point de terminaison. La fusion a été basée sur les priorités répertoriées ci-dessous et a été réalisée sans compromettre les fonctionnalités que chaque suite de sécurité a apportées à la combinaison :

- blocs de construction courants
- terminologie courante
- entités courantes
- parité des fonctionnalités avec d’autres charges de travail

## <a name="unified-investigations"></a>Examens unifiés

La simplification des centres de sécurité crée un volet unique pour examiner les incidents au sein d’une organisation Microsoft 365. Un exemple principal est le nœud **Incidents** dans le lancement rapide du Centre de sécurité Microsoft 365.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Page Incidents dans MDO.":::

Par exemple, un double-clic sur  un nom d’incident avec une gravité élevée vous amène à une page qui illustre l’avantage des centres convergants.

![Incident en plusieurs étapes impliquant une escalade des privilèges sur plusieurs points de terminaison, affichant 16 appareils touchés et 9 utilisateurs touchés.](../../media/converged-incident-info-3.png)

> [!TIP]
> L’onglet **Utilisateurs** convergés est un bon endroit pour commencer vos demandes. Cette page unique propose des informations pour les utilisateurs à partir de charges de travail convergées (Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité et MCAS, si vous l’exploitez) et une gamme de sources telles que Active Directory sur site, Azure Active Directory, les utilisateurs synchronisés, locaux et tiers. En savoir plus sur [la nouvelle expérience utilisateur.](investigate-users.md)

Les informations d’incident indiquent les spécificités utilisateur/identité et les appareils à risque, à côté des boîtes aux lettres concernées. Elle concerne également toutes les informations **d’investigation** et les preuves **recueillies.** Cela facilite la tâche des administrateurs et des équipes d’opérations de sécurité pour faire pivoter une alerte à haut risque vers les utilisateurs et les boîtes aux lettres concernés. Si vous regardez les onglets **Incident** en haut de cette page, d’autres tableaux croisés dynamiques de sécurité clés sont disponibles à partir de cet emplacement unique.

> [!IMPORTANT]
> En haut de n’importe quelle page pour un incident spécifique, vous verrez les onglets  **Résumé,** **Alertes, Périphériques,** Utilisateurs, Boîtes aux **lettres,** **Enquêtes** et Preuves. 

Selecting **Investigations** opens a page that features a graphic of the analysis taking place and lists a status (such as **pending approval**) for remediation. Prenez le temps de sélectionner des incidents spécifiques dans votre environnement, d’aller plus bas dans ces onglets et de créer un profil pour différents types de menaces. Les examens ultérieurs bénéficieront d’une connaissance familière.

## <a name="improved-processes"></a>Processus améliorés

Les contrôles courants et le contenu apparaissent au même endroit ou sont condensés dans un flux de données, ce qui facilite leur recherche. Par exemple, les paramètres unifiés.

### <a name="unified-settings"></a>Paramètres unifiés

![cliquez sur « Rôles » et ouvrez la page Paramètres, qui inclut les paramètres généraux, les autorisations, les API et les règles. Ouvrez Autorisations, puis Rôles. Affiche tous les rôles](../../media/converged-add-role-9.png)

### <a name="permissions--roles"></a>Autorisations & rôles

![Page Autorisations & rôles affichant les rôles endpoints & groupes, rôles et groupes d’appareils.](../../media/converged-roles-5.png)

 L’accès au Centre de sécurité Microsoft 365 est configuré avec des rôles globaux Azure Active Directory ou à l’aide de rôles personnalisés. For Defender for Endpoint, see [Assign user access to Microsoft Defender Security Center](/microsoft-365/security/defender-endpoint/assign-portal-access). Pour Defender pour Office 365, consultez Autorisations dans le Centre de conformité Microsoft 365 et le Centre de sécurité [Microsoft 365.](../office-365-security/permissions-microsoft-365-compliance-security.md)

- En savoir plus sur la gestion [de l’accès à Microsoft 365 Defender](m365d-permissions.md)
- En savoir plus sur la création [de rôles personnalisés](custom-roles.md) dans le Centre de sécurité Microsoft 365

> [!NOTE]
> Microsoft Defender pour le point de terminaison dans le Centre de sécurité Microsoft 365 prend en charge l’octroi de l’accès aux fournisseurs de services de sécurité [gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que l’accès est accordé dans le Centre de sécurité [Microsoft Defender.](./mssp-access.md)

### <a name="integrated-reports"></a>Rapports intégrés

Les rapports sont également unifiés dans le Centre de sécurité Microsoft 365. Les administrateurs peuvent commencer par un rapport de sécurité général et se brancher à des rapports spécifiques sur les points de terminaison, envoyer des & collaboration. Les liens ici sont générés dynamiquement en fonction de la configuration de la charge de travail.

### <a name="quickly-view-your-microsoft-365-environment"></a>Afficher rapidement votre environnement Microsoft 365

La page **d’accueil** affiche la plupart des cartes courantes dont les équipes de sécurité ont besoin. La composition des cartes et des données dépend du rôle d’utilisateur. Étant donné que le Centre de sécurité Microsoft 365 utilise le contrôle d’accès basé sur les rôles, différents rôles voient des cartes plus significatives pour leur travail quotidien.  

Ces informations rapides vous permettent de suivre les dernières activités de votre organisation. Le Centre de sécurité Microsoft 365 regroupe les signaux provenant de différentes sources pour présenter une vue globale de votre environnement Microsoft 365.

Les cartes sont dans les catégories suivantes :

- **Identités**: surveillez les identités de votre organisation et suivez les comportements suspects ou risqués. [En savoir plus sur la protection des identités.](/azure/active-directory/identity-protection/overview-identity-protection)
- **Données :** permettent de suivre l’activité des utilisateurs qui peut entraîner une divulgation non autorisée des données.
- **Appareils** : obtenez des informations à jour sur les alertes, l’activité de violation et d’autres menaces sur vos appareils.
- **Applications** : obtenir des informations sur la façon dont les applications cloud sont utilisées dans votre organisation. [En savoir plus sur les applications découvertes dans Cloud App Security.](/cloud-app-security/discovered-apps)

## <a name="threat-analytics-with-better-data-coverage"></a>Analyse des menaces avec une meilleure couverture de données
Suivez les menaces émergentes et répondez-y avec l’expérience intégrée d’analyse des menaces Microsoft 365 Defender suivante :

- Meilleure couverture des données entre Microsoft Defender pour le point de terminaison et Microsoft Defender pour Office 365, ce qui rend possible la gestion combinée des incidents, l’examen automatique, la correction et la recherche proactive ou réactive de menaces sur plusieurs domaines. 
- Détections et atténuations liées à la messagerie électronique de Microsoft Defender pour Office 365, en plus des données de point de terminaison déjà disponibles à partir de Microsoft Defender pour endpoint.
- Vue des incidents liés aux menaces qui regroupent les alertes en articles d’attaque de bout en bout dans Microsoft Defender pour le point de terminaison et Microsoft Defender pour Office 365 afin de réduire la file d’attente de travail, ainsi que de simplifier et d’accélérer votre enquête.
- Tentatives d’attaque détectées et bloquées par les solutions Microsoft 365 Defender. Il existe également des données que vous pouvez utiliser pour piloter des actions préventives qui atténuent les risques d’exposition supplémentaire et augmentent la résilience. 
- Conception améliorée qui place des informations exploitables à la une pour vous aider à identifier rapidement les données sur qui il est urgent de se concentrer, d’examiner et de tirer parti des rapports.

## <a name="a-centralized-learning-hub"></a>Hub d’apprentissage centralisé

Le Centre de sécurité Microsoft 365 inclut un hub d’apprentissage qui propose des conseils officiels à partir de ressources telles que le blog sur la sécurité Microsoft, la communauté de sécurité Microsoft sur YouTube et la documentation officielle sur docs.microsoft.com.

À l’intérieur du hub d’apprentissage, les conseils de collaboration de messagerie & (Microsoft Defender pour Office 365 ou MDO) sont côte à côte avec Endpoint (Microsoft Defender pour Endpoint ou MDE) et les ressources d’apprentissage de Microsoft 365 Defender.

Le hub d’apprentissage s’ouvre avec des parcours d’apprentissage organisés autour de rubriques telles que « Comment examiner l’utilisation de Microsoft 365 Defender ? » et « Meilleures pratiques de Microsoft Defender pour Office 365 ». Cette section est actuellement organisée par le groupe produit de sécurité au sein de Microsoft. Chaque parcours d’apprentissage reflète le temps projeté qu’il faut pour passer en travers des concepts. Par exemple, « Étapes à suivre lorsqu’un compte d’utilisateur Microsoft Defender pour Office 365 est compromis » est projeté pour prendre 8 minutes et constitue un apprentissage précieux à la volée.

Après avoir cliqué sur le contenu, il peut être utile de mettre en signet ce site et d’organiser les signets dans un dossier « Sécurité » ou « Critique ». Pour afficher tous les chemins d’accès d’apprentissage, cliquez sur le lien Afficher tout dans le panneau principal.

> [!NOTE]
> Il existe  des filtres utiles en haut du Centre de sécurité Microsoft 365 qui vous permettent de choisir entre les produits (actuellement Microsoft 365 Defender, Microsoft Defender pour Point de terminaison et Microsoft Defender pour Office 365). Notez que le nombre de ressources d’apprentissage pour chaque section est répertorié, ce qui peut aider les enseignants à suivre le nombre de ressources dont ils disposent pour la formation et l’apprentissage.
>
> Outre le filtre Produit, les rubriques actuelles, les types de ressources (des vidéos aux webinaires), les niveaux de familiarité ou d’expérience avec les domaines de sécurité, les rôles de sécurité et les fonctionnalités du produit sont répertoriés.

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires

Nous avons besoin de vos commentaires. Nous cherchons toujours à améliorer, donc s’il existe un message que vous souhaitez voir, envoyez-nous vos commentaires [sur Microsoft 365 Defender.](https://www.microsoft.com/videoplayer/embed/RE4K5Ci)

Vous pouvez également laisser des commentaires à partir de cet article. In the 'Feedback' section at the end under 'Submit and view feedback for', the options are *This product,* or *This page*.

Utilisez le **bouton Ce produit pour** les commentaires sur *le* produit :

1. Sélectionnez *ce produit* au bas de l’article.
    1. Cliquez avec le bouton droit sur le bouton et « Ouvrir dans un nouvel onglet » si vous souhaitez continuer à lire ces instructions.
2. Cela permet d’accéder au **forum UserVoice.**
3. Vous avez 2 options :
    1. Faites défiler vers le bas jusqu’à la zone de texte Comment pouvons-nous améliorer la conformité ou mieux protéger vos utilisateurs dans *Office 365 ?* et coller dans le Centre de sécurité *Microsoft 365*. Vous pouvez rechercher dans les résultats une idée comme la vôtre et la voter haut, ou utiliser le bouton pour **publier une nouvelle idée**.
    1. Si vous pensez que ce problème est déjà signalé et que vous souhaitez augmenter son profil avec un vote (ou des votes), utilisez la zone Donner des commentaires sur le côté droit de UserVoice.  Recherchez le Centre de sécurité *Microsoft 365,* recherchez le problème et utilisez le bouton **de vote** pour augmenter son état.

Utilisez *cette page pour* obtenir des commentaires sur l’article lui-même. Merci pour vos commentaires. Votre voix nous aide à améliorer les produits.

### <a name="explore-what-the-security-center-has-to-offer"></a>Explorer ce que le centre de sécurité a à offrir

Continuez à explorer les fonctionnalités du Centre de sécurité Microsoft 365 :

- [Gérer les incidents et les alertes](manage-incidents.md)
- [Suivre les menaces émergentes et y répondre avec l’analyse des menaces](threat-analytics.md)
- [Le centre des actions](m365d-action-center.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications, et les identités](./advanced-hunting-query-emails-devices.md)
- [Règles de détection personnalisée](./custom-detection-rules.md)
- [Alertes d’e-mail et collaboration](../../compliance/alert-policies.md#default-alert-policies)
- [Créer une simulation d’attaque par hameçonnage](../office-365-security/attack-simulation-training.md) et [créer une charge utile pour former vos équipes](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)
 
### <a name="related-information"></a>Informations connexes
- [Centre de sécurité Microsoft 365](overview-security-center.md)
- [Defender pour Office 365 dans le centre de sécurité Microsoft 365](microsoft-365-security-center-mdo.md)
- [Microsoft Defender pour le point de terminaison dans le Centre de sécurité Microsoft 365](microsoft-365-security-center-mde.md)
- [Redirection des comptes de Microsoft Defender pour le point de terminaison vers le Centre de sécurité Microsoft 365](microsoft-365-security-mde-redirection.md)