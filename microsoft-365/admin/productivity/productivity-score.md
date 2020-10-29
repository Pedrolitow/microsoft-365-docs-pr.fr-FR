---
title: Score de productivité Microsoft
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ROBOTS: NOINDEX, NOFOLLOW
description: Vue d’ensemble du score de productivité Microsoft.
ms.openlocfilehash: 3d014cd0eb3a3ceed3b3f3b48f126453e4ced193
ms.sourcegitcommit: fa26da0be667d4be0121c52b05488dc76c5d626c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "48794964"
---
# <a name="microsoft-productivity-score"></a>Score de productivité Microsoft 

Le score de productivité aide les organisations à transformer le travail réalisé grâce à des informations sur la façon dont les utilisateurs utilisent Microsoft 365 et les expériences technologiques qui les prennent en charge. Le score reflète les performances de votre organisation par rapport aux actions des personnes et de la technologie et compare votre score avec les organisations comme les vôtres.

Le score inclut les éléments suivants :

- **Mesures** pour vous aider à découvrir comment les utilisateurs utilisent les produits Microsoft 365 pour collaborer, communiquer et travailler sur plusieurs plateformes.
- **Informations sur** les données pour vous aider à identifier les opportunités d’amélioration de la productivité et de la satisfaction des employés.
- **Actions recommandées** que vous pouvez prendre pour aider les personnes de votre organisation à utiliser efficacement les produits Microsoft 365 afin que tout le monde puisse le faire.

Nous fournissons des données, des informations et des recommandations dans deux domaines : 

- **Expériences des personnes :** Mesure comment les utilisateurs collaborent sur le contenu, comment ils utilisent les produits Microsoft 365 pour communiquer et s’ils utilisent Microsoft 365 sur plusieurs plateformes. 

    Nous fournissons ces informations, car lorsque les personnes collaborent en ligne, elles font gagner du temps, et la liberté de travailler sur n’importe quel appareil devient plus productive et satisfaite. La possibilité de communiquer de manière flexible rend les personnes plus efficaces, ce qui permet de former de plus en plus de relations. Pour obtenir des preuves, consultez la rubrique [Forrester Report](https://vc2prod.blob.core.windows.net/vc-resources/TEIStudies/TEI%20of%20Microsoft%20365%20E5%20-%20Oct%202018.pdf).

- **Expériences technologiques :** La productivité dépend de la technologie fiable et efficace, ainsi que de l’utilisation efficace de Microsoft 365. Nous fournissons des [analyses de point de terminaison](https://aka.ms/endpointanalytics), ce qui vous permet de comprendre comment la productivité de vos utilisateurs peut être affectée par les problèmes de performances et d’intégrité liés à votre matériel et logiciels de point de terminaison. Nous fournissons également les actions recommandées pour les résoudre, ainsi que les analyses de connectivité réseau Microsoft 365 pour votre organisation.

Voir [qu’est-ce que le point de terminaison Analytics](https://docs.microsoft.com/mem/analytics/overview) pour une vue d’ensemble et les détails prérequis. Pour en savoir plus sur les informations sur la connectivité réseau Microsoft 365, consultez [la rubrique Network Connectivity Overview](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-networking-overview).
  

## <a name="how-the-score-is-calculated"></a>Mode de calcul du score

Votre score de productivité est basé sur les scores combinés de vos catégories de personnes et d’expériences technologiques. Chaque catégorie est pondérée équitablement, avec un total de 100 points. Le score de productivité le plus élevé possible est 500.

### <a name="score-categories"></a>Catégories de score 

- Collaboration sur le contenu (100 points)
- Communication (100 points)
- Mobilité (100 points)
- Analyse du point de terminaison (100 points)
- Connectivité réseau (100 points)
- **Total possible = 500 points**
 
 Dans chaque catégorie, nous identifions les modèles pour les activités clés qui sont des indicateurs de la façon dont les utilisateurs utilisent les produits Microsoft 365 pour collaborer, communiquer et travailler sur plusieurs plateformes. Nous fournissons des affichages de 28 jours et de 180 jours des activités clés. Nous fournissons également des mesures de prise en charge qui ne font pas partie du calcul de score, mais qui sont importantes pour vous aider à identifier les comportements et les paramètres sous-jacents sur lesquels vous pouvez agir.

### <a name="products-included-in-productivity-score"></a>Produits inclus dans le score de productivité 

Le score de productivité inclut des données à partir d’Exchange, SharePoint, OneDrive, teams, Word, Excel, PowerPoint, OneNote, Outlook, Yammer et Skype.

Votre score est mis à jour quotidiennement et reflète les actions de l’utilisateur effectuées au cours des 28 derniers (y compris le jour actuel).


## <a name="pre-requisites"></a>Conditions préalables 

Pour obtenir des données de personnes, vous avez besoin d’un abonnement Microsoft 365 for Business ou Office 365 pour Enterprise, et vous devez utiliser les services Cloud mutualisés. Pour obtenir des données analytiques de point de terminaison pour votre client, vous devez ajouter Microsoft Intune à votre abonnement. Intune vous permet de protéger les données de votre organisation en gérant les appareils et les applications.       Une fois que vous avez Intune, vous pouvez activer l’analyse du point de terminaison au sein de l’expérience Intune. En savoir plus sur Microsoft Intune. 

Pour afficher le score de productivité de votre organisation, vous devez disposer de l’un des rôles suivants : 

- Administrateur global 
- Administrateurs Exchange
- Administrateur SharePoint 
- Administrateur pour Skype Entreprise 
- Administrateur Teams 
- Lecteur général 
- Lecteur de rapports 

Vous pouvez accéder à l’expérience utilisateur à partir de la maison d’administration 365 sous **rapports** de  >  **productivité** .

## <a name="interpreting-productivity-score"></a>Interprétation de la note de productivité 

La page d’accueil des scores de productivité indique votre score total et l’historique des scores, ainsi que le principal aperçu de chaque catégorie.

![Page d’accueil des scores de productivité](../../media/pslanding.png)

**Votre score** est affiché sous la forme d’une valeur de pourcentage et en points. Vous pouvez voir vos points dans le numérateur et les points les plus maximaux possibles dans le dénominateur.

Les **tests d’évaluation d’homologue** vous permettent de comparer votre score avec des organisations comme les vôtres. Pour les catégories de personnes qui rencontrent des personnes, la mesure de test d’homologue est calculée comme la moyenne des mesures au sein d’un ensemble d’organisations similaires. L’ensemble est composé d’organisations de votre région avec un nombre similaire d’utilisateurs sous licence, de types de licences, de secteurs d’activité et de leur utilisation avec Microsoft 365. 

Le benchmark d’homologue Analytics de point de terminaison inclut des cibles pour les performances de démarrage des périphériques et une configuration logicielle recommandée basée sur des valeurs multilatérales agrégées sur tous les clients.

Pour la connectivité réseau, le banc d’essai recommandé est de 80 points.

La section **répartition du score** fournit une répartition de votre score de productivité avec des tests d’évaluation par les domaines des personnes et de l’expérience technique.

L’historique des scores indique comment le score dans chaque catégorie a été modifié au cours des 6 derniers mois.

Les domaines de l' **expérience utilisateur** et des expériences **technologiques** contiennent les informations principales pour les catégories de ces domaines. Vous pouvez cliquer sur chaque catégorie pour voir des informations plus approfondies.

## <a name="category-details-pages"></a>Pages de détails de catégorie

Chaque page de détails de catégorie présente les mesures principales de l’analyse et de la prise en charge, ainsi que les actions de recherche et les actions que vous pouvez effectuer pour effectuer des modifications dans votre organisation. Research prend en charge l’importance et la justification des connaissances principales pour chaque catégorie. Pour plus d’informations, [consultez le rapport Forrester](https://vc2prod.blob.core.windows.net/vc-resources/TEIStudies/TEI%20of%20Microsoft%20365%20E5%20-%20Oct%202018.pdf).

Les pages de détails sont les suivantes :
- [Collaboration de contenu : expériences de personnes](content-collaboration.md)
- [Communication – expériences de personnes](communication.md)
- [Réunions – expériences de personnes](meetings.md)
- [Mobilité – expériences de personnes](mobility.md)
- [Travail d’équipe – expériences de personnes](teamwork.md)
- [Intégrité des applications Microsoft 365 : expériences technologiques](apps-health.md)

## <a name="business-continuity-special-report"></a>Rapport spécial de continuité d’activité

Le rapport de continuité des opérations est un rapport d’intelligence de Workplace limité accessible à tous les clients de Microsoft 365 afin de les aider à orienter leur organisation pendant ce temps.  

Ce rapport aide les chefs d’entreprise à comprendre les éléments suivants : 

- Impact de la collaboration et de la communication sur le travail à distance. 

- Impact sur l’équilibre de la vie du travail au fur et à mesure que les personnes s’ajustent à la maison. 

- Si les réunions à distance prennent en charge une prise de décision efficace.

[En savoir plus sur le rapport de continuité d’activité](https://aka.ms/bcrps)

[En savoir plus sur Microsoft Graph](https://docs.microsoft.com/graph/)

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Partagez vos idées sur le score de productivité et vos idées sur la façon de l’améliorer. Utilisez les sections de **Commentaires** dans le produit et/ou joignez-vous à l’équipe de score de productivité sur ProductivityScorePreview@service.microsoft.com.
