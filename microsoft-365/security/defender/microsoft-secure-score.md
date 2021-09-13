---
title: Degré de sécurisation Microsoft
description: Décrit le Niveau de sécurité Microsoft dans le portail Microsoft 365 Defender, comment améliorer votre posture de sécurité et ce à quoi les administrateurs de sécurité peuvent s’attendre.
keywords: score de sécurité Microsoft, score de sécurité, score de sécurité Office 365, score de sécurité Microsoft, Microsoft 365 Defender portail, actions d’amélioration
ms.prod: m365-security
ms.mktglfcycl: deploy
localization_priority: Normal
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.technology: m365d
ms.openlocfilehash: de8d0a0bc1609a3dfac9d177a51ef3903b477de4
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183095"
---
# <a name="microsoft-secure-score"></a>Niveau de sécurité Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Le Niveau de sécurité Microsoft est une mesure de la posture de sécurité d'une organisation, un chiffre plus élevé indiquant que davantage de mesures d'amélioration ont été prises. Il se trouve dans le https://security.microsoft.com/securescore portail [Microsoft 365 Defender.](overview-security-center.md)

En suivant les recommandations du Niveau de sécurité, vous pouvez protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le portail Microsoft 365 Defender, les organisations peuvent surveiller et travailler sur la sécurité de leurs identités, applications et appareils Microsoft 365 de sécurité.

Score sécurisé aide les organisations :  

* Rapport sur l'état actuel de la posture de sécurité de l'organisation.
* Améliorer leur posture de sécurité en leur offrant des possibilités de découverte, de visibilité, de guide et de contrôle.  
* Comparer avec des critères de référence et établir des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes des métriques et des tendances, à l’intégration à d’autres produits Microsoft, à la comparaison des scores avec des organisations similaires, et bien plus encore. Le score peut également refléter lorsque des solutions tierces ont traité les actions recommandées.

![Page d’accueil Du score sécurisé.](../../media/secure-score/secure-score-home-page.png)

## <a name="how-it-works"></a>Comment ça marche

Des points vous sont attribués pour les actions suivantes :

- Configuration des fonctionnalités de sécurité recommandées
- Effectuer des tâches liées à la sécurité
- Résolution de l’action d’amélioration à l’aide d’une application ou d’un logiciel tiers, ou d’une autre atténuation

Certaines actions d’amélioration ne donnent des points qu’une fois l’opération terminée. Certaines donnent des points partiels s’il elles sont terminées pour certains appareils ou utilisateurs. Si vous ne pouvez pas ou ne souhaitez pas effectuer l’une des actions d’amélioration, vous pouvez choisir d’accepter le risque ou le risque restant.

Si vous disposez d’une licence pour l’un des produits Microsoft pris en charge, vous verrez des recommandations pour ces produits. Nous vous présentons l’ensemble complet des améliorations possibles pour un produit, quelle que soit l’édition de licence, l’abonnement ou le plan. De cette façon, vous pouvez comprendre les meilleures pratiques de sécurité et améliorer votre score. Votre posture de sécurité absolue, représentée par le degré de sécurisation, reste la même, quelle que soit la licence dont votre organisation dispose pour un produit spécifique. N’oubliez pas que la sécurité et la convivialité doivent s’équilibrer, et certaines recommandations peuvent ne pas convenir à votre environnement.

Votre score est mis à jour en temps réel pour refléter les informations présentées dans les visualisations et les pages d’action d’amélioration. Le degré de sécurisation se synchronise également quotidiennement pour recevoir des données système sur les points que vous avez atteints pour chaque action.

### <a name="key-scenarios"></a>Scénarios clés

- [Vérifier votre score actuel](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Comparer votre score à des organisations comme la vôtre](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Afficher les actions d’amélioration et décider d’un plan d’action](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Lancer des flux de travail pour examiner ou implémenter](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont notées

Chaque action d’amélioration vaut 10 points ou moins, et la plupart sont notées de manière binaire. Si vous implémentez l’action d’amélioration, comme créer une stratégie ou activer un paramètre spécifique, vous obtenez 100 % des points. Pour les autres actions d’amélioration, les points sont indiqués sous forme de pourcentage de la configuration totale.

Par exemple, une action d’amélioration indique que vous obtenez 10 points en protégeant tous vos utilisateurs avec l’authentification multifacteur. Vous avez seulement 50 utilisateurs sur 100 protégés au total. Vous obtenez donc un score partiel de 5 points (50 protégés / 100 au total * 10 points maximum = 5 pts).

### <a name="products-included-in-secure-score"></a>Produits inclus dans le degré de sécurisation

Il existe actuellement des recommandations pour les produits suivants :

- Microsoft 365 (y compris Exchange Online)
- Azure Active Directory
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité
- Cloud App Security
- Microsoft Teams

Des recommandations pour d’autres produits de sécurité seront bientôt disponibles. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais elles constituent une bonne base de référence. Vous pouvez également marquer les actions d’amélioration comme couvertes par un tiers ou une autre atténuation.

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Microsoft Secure Score a mis à jour les actions d’amélioration pour prendre en charge les[paramètres de sécurité par défaut dans Azure Active Directory](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), ce qui facilite la protection de votre organisation avec des paramètres de sécurité préconfigurés pour les attaques courantes.

Si vous activez les paramètres de sécurité par défaut, vous recevrez des points complets pour les actions d’amélioration suivantes :

- Vérifier que tous les utilisateurs peuvent effectuer une authentification multifacteur pour un accès sécurisé (9 points)
- Exiger l’authentification multifacteur pour les rôles d’administration (10 points)
- Activer la stratégie pour bloquer l’authentification héritée (7 points)

>[!IMPORTANT]
>Les paramètres de sécurité par défaut incluent des fonctionnalités de sécurité qui assurent une sécurité similaire aux actions d’amélioration de la « stratégie de risque de connexion » et de la « stratégie de risque utilisateur ». Au lieu de configurer ces stratégies en plus des paramètres de sécurité par défaut, nous vous recommandons de mettre à jour leurs états sur « Résolu via une autre atténuation ».

## <a name="required-permissions"></a>Autorisations requises

Pour avoir l’autorisation d’accéder à Microsoft Secure Score, vous devez disposer de l’un des rôles suivants dans Azure Active Directory.

### <a name="read-and-write-roles"></a>Rôles de lecture et d’écriture

Avec l’accès en lecture et en écriture, vous pouvez apporter des modifications et interagir directement avec le degré de sécurisation. Vous pouvez également attribuer un accès en lecture seule à d’autres utilisateurs.

* Administrateur général
* Administrateur de sécurité
* Administrateur Exchange
* Administrateur SharePoint

### <a name="read-only-roles"></a>Rôles en lecture seule

Avec l’accès en lecture seule, vous ne pouvez pas modifier l’état ou les notes d’une action d’amélioration, modifier des zones de score ou modifier des comparaisons personnalisées.

* Administrateur du support technique
* Administrateur d’utilisateurs
* Administrateur de support de service
* Lecteur Sécurité
* Opérateur de sécurité
* Lecteur général

## <a name="risk-awareness"></a>Sensibilisation aux risques

Le niveau de sécurité Microsoft est un résumé numérique de votre posture de sécurité en fonction des configurations système, du comportement de l’utilisateur et d’autres mesures de sécurité. Il ne s’agit pas d’une mesure absolue de la probabilité de violation de votre système ou de vos données. Au lieu de cela, il représente la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft qui peuvent aider à contrebalancer le risque de violation. Aucun service en ligne n’est protégé contre les violations de sécurité et le degré de sécurisation ne doit pas être interprété comme une garantie contre les violations de sécurité d’aucune manière.

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous rencontrez des problèmes, faites-le nous savoir en publiant dans la communauté [Sécurité, confidentialité et conformité](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous supervisons la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluer votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivez votre historique de score de sécurité Microsoft et répondez aux objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Ce qui est à venir](microsoft-secure-score-whats-coming.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
