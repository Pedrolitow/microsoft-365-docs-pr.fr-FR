---
title: Degré de sécurisation Microsoft
description: Décrit le niveau de sécurité Microsoft dans le centre Microsoft 365 sécurité, comment améliorer votre posture de sécurité et ce à quoi les administrateurs de sécurité peuvent s’attendre.
keywords: score de sécurité Microsoft, score sécurisé, score de sécurité Office 365, score de sécurité Microsoft, centre de sécurité Microsoft 365, actions d’amélioration
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
ms.openlocfilehash: 1b03c2671939a3e8e3011b78b8f1484ef02979ea
ms.sourcegitcommit: 3d30ec03628870a22c54b6ec5d865cbe94f34245
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52930186"
---
# <a name="microsoft-secure-score"></a>Niveau de sécurité Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Le Niveau de sécurité Microsoft est une mesure de la posture de sécurité d'une organisation, un chiffre plus élevé indiquant que davantage de mesures d'amélioration ont été prises. Il se trouve dans le https://security.microsoft.com/securescore centre de [sécurité Microsoft 365.](overview-security-center.md)

En suivant les recommandations du Niveau de sécurité, vous pouvez protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le centre de sécurité Microsoft 365, les organisations peuvent surveiller et travailler sur la sécurité de leurs identités, applications et appareils Microsoft 365 leurs appareils.

Score sécurisé aide les organisations :  

* Rapport sur l'état actuel de la posture de sécurité de l'organisation.
* Améliorer leur posture de sécurité en leur offrant des possibilités de découverte, de visibilité, de guide et de contrôle.  
* Comparer avec des critères de référence et établir des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes de mesures et de tendances, à l’intégration avec d’autres produits Microsoft, à la comparaison des scores avec des organisations similaires, et bien plus encore. Le score peut également refléter le moment où des solutions tierces ont traité les actions recommandées.

![Page d’accueil du score de sécurisation](../../media/secure-score/secure-score-home-page.png)

## <a name="how-it-works"></a>Mode de fonctionnement

Vous avez des points pour les actions suivantes :

- Configuration des fonctionnalités de sécurité recommandées
- Effectuer des tâches liées à la sécurité
- Traitement de l’action d’amélioration avec une application ou un logiciel tiers, ou une autre atténuation

Certaines actions d’amélioration donnent uniquement des points lorsqu’elles sont entièrement terminées. Certains donnent des points partiels s’ils sont terminés pour certains appareils ou utilisateurs. Si vous ne pouvez pas ou ne souhaitez pas mettre en place l’une des actions d’amélioration, vous pouvez choisir d’accepter le risque ou le risque restant.

Si vous avez une licence pour l’un des produits Microsoft pris en charge, vous verrez des recommandations pour ces produits. Nous vous montrons l’ensemble complet des améliorations possibles pour un produit, indépendamment de l’édition de licence, de l’abonnement ou de l’offre. Ainsi, vous pouvez comprendre les meilleures pratiques en matière de sécurité et améliorer votre score. Votre posture de sécurité absolue, représentée par le niveau de sécurisation, reste la même quelle que soit la licence dont votre organisation est propriétaire pour un produit spécifique. N’oubliez pas que la sécurité et la convivialité doivent s’équilibrer, et certaines recommandations peuvent ne pas convenir à votre environnement.

Votre score est mis à jour en temps réel pour refléter les informations présentées dans les pages d’action d’amélioration et de visualisation. Secure Score se synchronise également quotidiennement pour recevoir des données système sur vos points obtenus pour chaque action.

### <a name="key-scenarios"></a>Scénarios clés

- [Vérifier votre score actuel](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Comparer votre score à des organisations telles que les vôtres](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Afficher les actions d’amélioration et décider d’un plan d’action](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Lancer des flux de travail pour examiner ou implémenter](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont note es

Chaque action d’amélioration vaut 10 points ou moins, et la plupart d’entre eux sont marqués de manière binaire. Si vous implémentez l’action d’amélioration, comme créer une stratégie ou activer un paramètre spécifique, vous obtenez 100 % des points. Pour les autres actions d’amélioration, les points sont donnés sous forme de pourcentage de la configuration totale.

Par exemple, une action d’amélioration indique que vous obtenez 10 points en protégeant tous vos utilisateurs avec l’authentification multifacteur. Vous n’avez que 50 utilisateurs sur 100 au total protégés. Vous obtenez donc un score partiel de 5 points (50 protégé / 100 au total * 10 pts max = 5 pts).

### <a name="products-included-in-secure-score"></a>Produits inclus dans secure score

Il existe actuellement des recommandations pour les produits suivants :

- Microsoft 365 (y compris Exchange Online)
- Azure Active Directory
- Microsoft Defender pour point de terminaison
- Microsoft Defender pour l’identité
- Cloud App Security
- Microsoft Teams

Recommandations d’autres produits de sécurité seront bientôt disponible. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais elles sont une bonne base de référence. Vous pouvez également marquer les actions d’amélioration comme couvertes par une solution tierce ou autre.

### <a name="security-defaults"></a>Paramètres de sécurité par défaut

Microsoft Secure Score a mis à jour les actions d’amélioration pour prendre en charge les paramètres de sécurité par défaut dans Azure Active Directory, ce qui facilite la protection de votre organisation avec des paramètres de sécurité pré-configurés pour les [attaques](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)courantes.

Si vous allumez les paramètres de sécurité par défaut, des points complets vous seront attribués pour les actions d’amélioration suivantes :

- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé (9 points)
- Exiger l’mf pour les rôles d’administration (10 points)
- Activer la stratégie pour bloquer l’authentification héritée (7 points)

>[!IMPORTANT]
>Les valeurs par défaut de sécurité incluent des fonctionnalités de sécurité qui fournissent une sécurité similaire à la « stratégie de risque de la signature » et aux actions d’amélioration de la « stratégie de risque utilisateur ». Au lieu de définir ces stratégies en plus des paramètres de sécurité par défaut, nous vous recommandons de mettre à jour leurs statuts sur « Résolu via une autre atténuation ».

## <a name="required-permissions"></a>Autorisations requises

Pour avoir l’autorisation d’accéder au Score de sécurité Microsoft, vous devez avoir l’un des rôles suivants dans Azure Active Directory.

### <a name="read-and-write-roles"></a>Lire et écrire des rôles

Avec l’accès en lecture et en écriture, vous pouvez apporter des modifications et interagir directement avec le score de sécurité. Vous pouvez également attribuer un accès en lecture seule à d’autres utilisateurs.

* Administrateur général
* Administrateur de sécurité
* Administrateur Exchange
* Administrateur SharePoint

### <a name="read-only-roles"></a>Rôles en lecture seule

Avec l’accès en lecture seule, vous ne pouvez pas modifier l’état ou les notes d’une action d’amélioration, modifier des zones de score ou modifier des comparaisons personnalisées.

* Administrateur du support technique
* Administrateur d’utilisateurs
* Administrateur du support technique
* Lecteur Sécurité
* Opérateur de sécurité
* Lecteur général

## <a name="risk-awareness"></a>Sensibilisation aux risques

Le Score de sécurité Microsoft est un résumé numérique de votre posture de sécurité en fonction des configurations système, du comportement de l’utilisateur et d’autres mesures liées à la sécurité. Il ne s’agit pas d’une mesure absolue du risque de violation de votre système ou de vos données. Au lieu de cela, il représente la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft, ce qui peut vous aider à réduire le risque de violation. Aucun service en ligne n’est contre les violations de sécurité et le score de sécurité ne doit pas être interprété comme une garantie contre les violations de sécurité.

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous avez des problèmes, faites-le nous savoir en publiant dans la communauté sécurité, confidentialité [& conformité.](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) Nous surveillons la communauté et fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluer votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivre votre historique du Score de sécurisation Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
