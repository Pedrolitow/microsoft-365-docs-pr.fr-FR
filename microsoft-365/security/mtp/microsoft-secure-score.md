---
title: Degré de sécurisation Microsoft
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, comment améliorer votre position de sécurité et ce que les administrateurs de sécurité peuvent vous attendre.
keywords: score de sécurité Microsoft, score de sécurisation, score de sécurité Office 365, score de sécurité Microsoft, centre de sécurité Microsoft 365, actions d’amélioration
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
ms.openlocfilehash: 7fe5be065ee45700a1f08a39c8050757c3843f7b
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682570"
---
# <a name="microsoft-secure-score"></a>Degré de sécurisation Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Secure score est une mesure de la position de sécurité d’une organisation, avec un nombre supérieur indiquant d’autres actions d’amélioration. Vous pouvez https://security.microsoft.com/securescore le trouver dans le [Centre de sécurité Microsoft 365](overview-security-center.md).

Le suivi des recommandations de score de sécurité peut protéger votre organisation contre les menaces. À partir d’un tableau de bord centralisé dans le centre de sécurité Microsoft 365, les organisations peuvent surveiller et gérer la sécurité des identités, des applications et des appareils Microsoft 365.

Le score de sécurité aide les organisations :  

* Rapport sur l’état actuel de l’état de sécurité de l’organisation.
* Améliorez la position de la sécurité en fournissant des possibilités de détectabilité, de visibilité, de conseils et de contrôle.  
* Comparez avec des benchmarks et établissez des indicateurs de performance clés (KPI).

Les organisations ont accès à des visualisations robustes de mesures et tendances, à une intégration à d’autres produits Microsoft, à une comparaison de scores avec des organisations similaires, et bien plus encore. Le score peut également indiquer quand les solutions tierces ont résolu les actions recommandées.

![Page d’accueil du score sécurisé](../../media/secure-score/secure-score-homepage-new.png)

## <a name="how-it-works"></a>Mode de fonctionnement

Vous disposez de points pour les actions suivantes :

- Configuration des fonctionnalités de sécurité recommandées
- Exécution de tâches liées à la sécurité
- Gestion de l’action d’amélioration avec une application ou un logiciel tiers, ou une autre limitation

Certaines actions d’amélioration ne donnent de points qu’une fois complètement terminé. Certains fournissent des points partiels s’ils sont terminés pour certains appareils ou utilisateurs. Si vous ne pouvez pas ou ne souhaitez pas arrêter une des actions d’amélioration, vous pouvez choisir d’accepter le risque ou le risque restant.

Si vous disposez d’une licence pour l’un des produits Microsoft pris en charge, vous verrez des recommandations pour ces produits. Nous vous montrons l’ensemble des améliorations possibles pour un produit, indépendamment de la licence Edition, abonnement ou plan. De cette manière, vous pouvez comprendre les meilleures pratiques en matière de sécurité et améliorer votre score. Votre position absolue de sécurité, représentée par la fonction de chiffrement sécurisé, reste la même quelle que soit la licence de votre organisation pour un produit spécifique. N’oubliez pas que la sécurité doit être équilibrée avec la convivialité et que toutes les recommandations ne peuvent pas fonctionner pour votre environnement.

Votre score est mis à jour en temps réel afin de refléter les informations présentées dans les pages de l’action visualisations et amélioration. Le score sécurisé est également synchronisé quotidiennement pour recevoir les données système relatives aux points obtenus pour chaque action.

### <a name="key-scenarios"></a>Scénarios clés

- [Vérifier votre score actuel](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Comparez votre score aux organisations comme la vôtre](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Afficher les actions d’amélioration et décider d’un plan d’action](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Initier des flux de travail pour enquêter ou implémenter](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)
    - [Centre de sécurité Microsoft 365 et intégration ServiceNow](tickets-security-center.md)

### <a name="how-improvement-actions-are-scored"></a>Comment les actions d’amélioration sont évaluées

Chaque action d’amélioration vaut 10 points maximum, et la plupart d’entre elles sont évaluées de manière binaire. Si vous implémentez l’action d’amélioration, par exemple créer une nouvelle stratégie ou activer un paramètre spécifique, vous obtenez 100% des points. Pour les autres actions d’amélioration, les points sont fournis sous la forme d’un pourcentage de la configuration totale.

Par exemple, une action d’amélioration vous indique 10 points en protégeant tous vos utilisateurs à l’aide de l’authentification multifacteur. Vous ne disposez que de 50 de 100 total d’utilisateurs protégés, vous obtiendrez un score partiel de 5 points (50 protégé/100 au total * 10 pts max = 5 pts).

### <a name="products-included-in-secure-score"></a>Produits inclus dans le score de sécurité

Il existe actuellement des recommandations pour Microsoft 365 (y compris Exchange Online), Azure Active Directory, Microsoft Defender for Endpoint, Microsoft Defender for Identity et Cloud App Security. Des recommandations pour d’autres produits de sécurité seront bientôt disponibles. Les recommandations ne couvrent pas toutes les surfaces d’attaque associées à chaque produit, mais elles sont de bonnes bases. Vous pouvez également marquer les actions d’amélioration telles qu’elles sont couvertes par une atténuation tierce ou alternative.

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

Avec un accès en lecture seule, vous ne pouvez pas modifier le statut ou les notes pour une action d’amélioration, modifier des zones de score ou modifier des comparaisons personnalisées.

* Administrateur du support technique
* Administrateur d’utilisateurs
* Administrateur de service
* Lecteur de sécurité
* Opérateur de sécurité
* Lecteur général

## <a name="risk-awareness"></a>Sensibilisation aux risques

Microsoft Secure score est un résumé numérique de votre position de sécurité basée sur les configurations système, le comportement de l’utilisateur et d’autres mesures liées à la sécurité. Il ne s’agit pas d’une mesure absolue de la probabilité de violation de votre système ou de vos données. Il représente plutôt la mesure dans laquelle vous avez adopté des contrôles de sécurité dans votre environnement Microsoft afin de compenser le risque d’être compromis. Aucun service en ligne n’est totalement immunisé contre les violations de sécurité et le score sécurisé ne doit pas être interprété comme une garantie d’une violation de sécurité.

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous rencontrez des problèmes, informez-le en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluez votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
