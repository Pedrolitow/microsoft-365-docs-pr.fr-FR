---
title: Degré de sécurisation Microsoft
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, comment améliorer votre position de sécurité et ce que les administrateurs de sécurité peuvent vous attendre.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 212cefebfa3b4954f30d114419f82a5862e98a4f
ms.sourcegitcommit: 09a500a44d8723f8f2be87d9ad4ce7e453c5192b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "45094797"
---
# <a name="microsoft-secure-score"></a>Degré de sécurisation Microsoft

Microsoft Secure score est une mesure de la position de sécurité d’une organisation, avec un nombre supérieur indiquant d’autres actions d’amélioration. Vous pouvez https://security.microsoft.com/securescore le trouver dans le [Centre de sécurité Microsoft 365](overview-security-center.md).

Le suivi des recommandations de score de sécurité peut protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le centre de sécurité Microsoft 365, les organisations peuvent surveiller et gérer la sécurité des identités, des données, des applications, des périphériques et de l’infrastructure de Microsoft 365.

Le score de sécurité aide les organisations :  

* Rapport sur l’état actuel de l’état de sécurité de l’organisation.
* Améliorez la position de la sécurité en fournissant des possibilités de détectabilité, de visibilité, de conseils et de contrôle.  
* Comparez avec des benchmarks et établissez des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes de mesures et tendances, à une intégration à d’autres produits Microsoft, à une comparaison de scores avec des organisations similaires, et bien plus encore. Le score peut également indiquer quand les solutions tierces ont résolu les actions recommandées.

![Page d’accueil du score sécurisé](../../media/secure-score/secure-score-homepage-new.png)

## <a name="how-it-works"></a>Mode de fonctionnement

Vous disposez de points pour la configuration des fonctionnalités de sécurité recommandées, l’exécution de tâches liées à la sécurité ou la gestion de l’action d’amélioration avec une application ou un logiciel tiers, ou une autre limitation. Certaines actions d’amélioration donnent uniquement des points lorsqu’ils sont complètement terminés, et d’autres les déposent si elles sont terminées pour certains périphériques ou utilisateurs. Si vous ne pouvez pas ou ne souhaitez pas arrêter une des actions d’amélioration, vous pouvez choisir d’accepter le risque ou le risque restant.

Nous vous montrons l’ensemble complet des améliorations possibles, quelle que soit la licence, afin que vous puissiez comprendre les meilleures pratiques en matière de sécurité et améliorer votre score. Votre posture de sécurité absolue est représentée par la fonction de chiffrement sécurisé, qui reste la même quelle que soit la licence de produit que possède votre organisation. N’oubliez pas que la sécurité doit être équilibrée avec la convivialité et que toutes les recommandations ne peuvent pas fonctionner pour votre environnement.

Votre score est mis à jour en temps réel afin de refléter les informations présentées dans les pages de l’action visualisations et amélioration. Le score sécurisé est également synchronisé quotidiennement pour recevoir les données système relatives aux points obtenus pour chaque action.

### <a name="key-scenarios"></a>Scénarios clés

- [Vérifier votre score actuel](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Comparez votre score aux organisations comme la vôtre](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Afficher les actions d’amélioration et décider d’un plan d’action](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Initier des flux de travail pour enquêter ou implémenter](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)
    - [Centre de sécurité Microsoft 365 et intégration ServiceNow](tickets-security-center.md)

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont évaluées

Chaque action d’amélioration vaut 10 points maximum. La plupart sont évaluées de manière binaire : Si vous implémentez l’action d’amélioration, par exemple créer une nouvelle stratégie ou activer un paramètre spécifique, vous obtenez 100% des points. Pour les autres actions d’amélioration, les points sont fournis sous la forme d’un pourcentage de la configuration totale. Par exemple, si l’action d’amélioration indique 10 points en protégeant tous vos utilisateurs à l’aide de l’authentification multifacteur et que vous n’avez que 50 de 100 Total utilisateurs protégés, vous recevrez un score partiel de 5 points (50 protégé/100 total * 10 pts max = 5 pts le score partiel).

### <a name="products-included-in-secure-score"></a>Produits inclus dans le score de sécurité

Il existe actuellement des recommandations pour Microsoft 365 (y compris Exchange Online), Azure AD, Microsoft Defender ATP, Azure ATP et la sécurité des applications Cloud. Des recommandations pour d’autres produits de sécurité seront bientôt disponibles. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais il s’agit d’une base de référence correcte. Vous pouvez également marquer les actions d’amélioration telles qu’elles sont couvertes par une atténuation tierce ou alternative.

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Microsoft Secure score a mis à jour les actions d’amélioration afin de prendre en charge les paramètres de [sécurité par défaut dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), ce qui facilite la protection de votre organisation avec des paramètres de sécurité préconfigurés pour les attaques courantes.

Si vous activez les paramètres de sécurité par défaut, vous recevrez des points complets pour les actions d’amélioration suivantes :

- Assurez-vous que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé (9 points).
- Exiger MFA pour les rôles d’administration (10 points)
- Activer la stratégie pour bloquer l’authentification héritée (7 points)

>[!IMPORTANT]
>Les paramètres de sécurité par défaut incluent des fonctionnalités de sécurité qui fournissent une sécurité similaire aux actions d’amélioration « stratégie de risque de connexion » et « stratégie de risque utilisateur ». Au lieu de configurer ces stratégies en plus des paramètres de sécurité par défaut, nous vous recommandons de mettre à jour leurs statuts sur « résolu par une autre atténuation ».

## <a name="required-permissions"></a>Autorisations requises

Pour avoir l’autorisation d’accéder à la note de sécurité Microsoft, vous devez disposer de l’un des rôles suivants dans Azure Active Directory.

### <a name="read-and-write-roles"></a>Rôles de lecture et d’écriture

Avec l’accès en lecture et en écriture, vous pouvez effectuer des modifications et interagir directement avec le score de sécurité. Vous pouvez également attribuer un accès en lecture seule aux autres utilisateurs.

* Administrateur général
* Administrateur de sécurité
* Administrateur Exchange
* Administrateur SharePoint
* Administrateur de compte

### <a name="read-only-roles"></a>Rôles en lecture seule

Avec un accès en lecture seule, vous n’êtes pas en mesure de modifier l’État ou les notes pour une action d’amélioration, de modifier des zones de score ou de modifier des comparaisons personnalisées.

* Administrateur du support technique
* Administrateur d’utilisateurs
* Administrateur de service
* Lecteur Sécurité
* Opérateur de sécurité
* Lecteur général

## <a name="risk-awareness"></a>Sensibilisation aux risques

Microsoft Secure score est un résumé numérique de votre position de sécurité basée sur les configurations système, le comportement de l’utilisateur et d’autres mesures liées à la sécurité ; il ne s’agit pas d’une mesure absolue de la probabilité de violation de votre système ou de vos données. Il représente plutôt la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft, ce qui peut vous aider à compenser le risque d’être compromis. Aucun service en ligne n’est totalement immunisé contre les violations de sécurité et le score sécurisé ne doit pas être interprété comme une garantie d’une violation de sécurité.

## <a name="whats-new"></a>Quelles sont les nouveautés ? 

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité, nous avons apporté des modifications. Pour en savoir plus sur les modifications planifiées, consultez [la rubrique what’s from Microsoft Secure score ?](microsoft-secure-score-whats-coming.md).

### <a name="incompatibility-with-identity-secure-score-and-graph-api"></a>Incompatibilité avec le score de sécurité d’identité et l’API Graph

Dans la version récente de Microsoft Secure score, un modèle de notation amélioré a été publié. Ces modifications permettent d’obtenir une vue plus flexible et précise de votre position de sécurité. Toutefois, ces mises à jour ont rendu le score de sécurité Microsoft incompatible temporairement avec le score de sécurité d’identité et l’API Graph.

Dans le temps, le score de sécurité d’identité et l’API Graph adopteront le nouveau modèle de notation. Jusqu’à ce moment, les clients verront les différences entre les scores communiqués par Microsoft Secure score, Identity Secure score et l’API Graph. Nous nous excusons des désagréments que cela peut entraîner et nous travaillons pour garantir que ces expériences sont plus compatibles à l’avenir.

### <a name="updated-improvement-actions"></a>Actions d’amélioration mises à jour

- Ajout d’actions d’amélioration Azure Active Directory
- Ajout d’actions d’amélioration de la protection avancée contre les menaces
- Prise en charge des recommandations de sécurité de la [& de gestion des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) de Microsoft Defender ATP
    - Toutes les recommandations de sécurité fournies par TVM sont désormais disponibles

### <a name="updated-interface-and-functionality"></a>Interface et fonctionnalité mises à jour

* Toutes les nouvelles mesures et tendances pour les CISO et les discussions au niveau des prospects
* Nouvelles façons de suivre et d’évaluer votre score
* Meilleure approche et compréhension pour les régressions de score
* Filtrage, balisage, recherche et regroupement de vos actions d’amélioration
* Gérer vos objectifs à venir à l’aide de projections de score et des actions planifiées
* Et bien plus encore !

### <a name="june-2020"></a>Juin 2020

#### <a name="removed-improvement-action-for-microsoft-defender-advanced-threat-protection"></a>Suppression de l’action d’amélioration pour la protection avancée contre les menaces Microsoft Defender

* Activer les règles de réduction de la surface d’attaque

#### <a name="added-improvement-actions-for-microsoft-defender-advanced-threat-protection"></a>Ajout d’actions d’amélioration pour la protection avancée contre les menaces Microsoft Defender

* Empêcher Adobe Reader de créer des processus enfants
* Utiliser la protection avancée contre les ransomware
* Empêcher toutes les applications Office de créer des processus enfants
* Empêcher les applications Office de créer du contenu exécutable
* Bloquer JavaScript ou VBScript pour lancer le téléchargement de contenu exécutable
* Bloquer l’exécution des scripts potentiellement brouillés
* Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie Web
* Bloquer l’application de communication Office de la création de processus enfants
* Bloquer les processus non approuvés et non signés qui s’exécutent à partir de ports USB
* Blocage de la persistance via l’abonnement aux événements WMI
* Bloquer l’injection de code dans d’autres processus par les applications Office
* Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à un critère de récurrence, d’âge ou de liste approuvée
* Création de processus de bloc provenant de commandes PSExec et WMI
* Bloquer le vol d’informations d’identification à partir du sous-système Windows local Security Authority (lsass.exe)
* Bloquer les appels d’API Win32 à partir de macros Office

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Si vous rencontrez des problèmes, indiquez-nous en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Obtenir une visibilité sur la position de la sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
