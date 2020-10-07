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
ms.openlocfilehash: 82dc26aea5c573b63bb66d087b332e3301e71409
ms.sourcegitcommit: 9841058fcc95f7c2fed6af92bc3c3686944829b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "48376972"
---
# <a name="microsoft-productivity-score-preview"></a>Score de productivité Microsoft (aperçu)

Le score de productivité aide les organisations à transformer le travail réalisé grâce à des informations sur la façon dont les utilisateurs utilisent Microsoft 365 et les expériences technologiques qui les prennent en charge. Le score reflète les performances de votre organisation par rapport aux actions des personnes et de la technologie et compare votre score avec les organisations comme les vôtres.

Le score inclut les éléments suivants :

- **Mesures** pour vous aider à découvrir comment les utilisateurs utilisent les produits Microsoft 365 pour collaborer, communiquer et travailler sur plusieurs plateformes.
- **Informations sur** les données pour vous aider à identifier les opportunités d’amélioration de la productivité et de la satisfaction des employés.
- **Actions recommandées** que vous pouvez prendre pour aider les personnes de votre organisation à utiliser efficacement les produits Microsoft 365 afin que tout le monde puisse le faire.

Nous fournissons des données, des informations et des recommandations dans deux domaines : 

- **Expériences des personnes :** Nous mesurons comment les utilisateurs collaborent sur le contenu, comment ils utilisent les produits Microsoft 365 pour communiquer et s’ils utilisent Microsoft 365 sur toutes les plateformes. 

    Ces informations sont fournies car, lorsque les personnes collaborent en ligne, elles font gagner du temps. En toute liberté de travail sur n’importe quel appareil, ils sont plus productifs et satisfaits. La communication de manière flexible rend les personnes plus efficaces, forment de meilleurs relations et votre organisation est plus unifiée. Pour obtenir des preuves, consultez la rubrique [Forrester Report](https://vc2prod.blob.core.windows.net/vc-resources/TEIStudies/TEI%20of%20Microsoft%20365%20E5%20-%20Oct%202018.pdf).

- **Expériences technologiques :** La productivité dépend de la technologie fiable et performante, ainsi que de l’utilisation efficace de Microsoft 365. Nous fournissons des [analyses de point de terminaison](https://aka.ms/endpointanalytics), ce qui vous permet de comprendre comment la productivité de vos utilisateurs peut être affectée par les problèmes de performances et d’intégrité liés à votre matériel et logiciels de point de terminaison. Nous fournissons également les actions recommandées pour les résoudre, ainsi que les analyses de connectivité réseau Microsoft 365 pour votre organisation.

Voir [qu’est-ce que le point de terminaison Analytics](https://docs.microsoft.com/mem/analytics/overview) pour une vue d’ensemble et les détails prérequis. Pour en savoir plus sur les informations sur la connectivité réseau Microsoft 365, consultez [la rubrique Network Connectivity Overview](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-networking-overview).
  

## <a name="how-the-score-is-calculated"></a>Mode de calcul du score

Votre score de productivité est basé sur les scores combinés de vos catégories de personnes et d’expériences technologiques. Chaque catégorie est pondérée équitablement, avec un total de 100 points par catégorie. Le nombre total de points possibles pour le score de productivité est de 500.

### <a name="score-categories"></a>Catégories de score 

- Collaboration sur le contenu (100 points)
- Communication (100 points)
- Mobilité (100 points)
- Analyse du point de terminaison (100 points)
- Connectivité réseau (100 points)
- **Total possible = 500 points**
 
 Dans chaque catégorie, nous identifions les modèles pour les activités clés qui sont des indicateurs de la façon dont les utilisateurs utilisent les produits Microsoft 365 pour collaborer, communiquer et travailler sur plusieurs plateformes. Nous fournissons des affichages de 28 jours et de 180 jours des activités clés. Nous fournissons également des mesures de prise en charge qui ne font pas partie du calcul de score, mais qui sont importantes pour vous aider à identifier les comportements et les paramètres sous-jacents sur lesquels vous pouvez agir pour effectuer des modifications.

### <a name="products-included-in-productivity-score"></a>Produits inclus dans le score de productivité 

Le score de productivité inclut des données à partir d’Exchange, SharePoint, OneDrive, teams, Word, Excel, PowerPoint, OneNote, Outlook, Yammer et Skype.

Votre score est mis à jour quotidiennement et reflète les actions de l’utilisateur effectuées au cours des 28 derniers (y compris le jour actuel).


## <a name="pre-requisites"></a>Conditions préalables 

Vous avez besoin d’un abonnement Microsoft 365 for Business ou Office 365 pour Enterprise pour obtenir des données sur les utilisateurs, et vous devez utiliser les services Cloud mutualisés. Pour obtenir des données analytiques de point de terminaison pour votre client, vous devez ajouter Microsoft Intune à votre abonnement. Intune vous permet de protéger les données de votre organisation en gérant les appareils et les applications.       Une fois que vous avez Intune, vous pouvez activer l’analyse du point de terminaison au sein de l’expérience Intune. En savoir plus sur Microsoft Intune. 

Pour afficher le score de productivité de votre organisation, vous devez disposer de l’un des rôles suivants : 

- Administrateur global 
- Administrateurs Exchange
- Administrateur SharePoint 
- Administrateur pour Skype Entreprise 
- Administrateur Teams 
- Lecteur général 
- Lecteur de rapports 

Vous pouvez accéder à l’expérience utilisateur à partir de la maison d’administration 365 sous **rapports**de  >  **productivité**.

## <a name="interpreting-productivity-score"></a>Interprétation de la note de productivité 

La page d’accueil des scores de productivité indique votre score total et l’historique des scores, ainsi que les principales perspectives pour chaque catégorie.

![Page d’accueil des scores de productivité](../../media/pslanding.png)

**Votre score** est affiché sous la forme d’une valeur de pourcentage ainsi qu’en points, ce qui vous permet de voir vos points (numérateur) et le nombre maximal de points possibles (dénominateur).

Les **tests d’évaluation d’homologue** vous permettent de comparer votre score avec des organisations comme les vôtres. Pour les catégories de personnes qui rencontrent des personnes, la mesure de test d’homologue est calculée comme la moyenne des mesures au sein d’un ensemble d’organisations similaires. L’ensemble est composé d’organisations de votre région avec un nombre similaire d’utilisateurs sous licence, de types de licences, de secteurs d’activité et de leur utilisation avec Microsoft 365. 

Le benchmark d’homologue Analytics de point de terminaison inclut des cibles pour les performances de démarrage des périphériques et une configuration logicielle recommandée basée sur des valeurs multilatérales agrégées sur tous les clients.

Pour la connectivité réseau, le banc d’essai recommandé est de 80 points.

La section **répartition du score** fournit une répartition de votre score de productivité avec des tests d’évaluation par les domaines des personnes et de l’expérience technique.

L’historique des scores indique comment le score dans chaque catégorie a été modifié au cours des 6 derniers mois.

Les domaines de l' **expérience utilisateur** et des expériences **technologiques** contiennent les informations principales pour les catégories de ces domaines. Vous pouvez cliquer sur chaque catégorie pour voir des informations plus approfondies.

## <a name="category-details-pages"></a>Pages de détails de catégorie

Chaque page de détails de catégorie présente les mesures principales de l’analyse et de la prise en charge, ainsi que les actions de recherche et les actions que vous pouvez effectuer pour effectuer des modifications dans votre organisation. Research prend en charge l’importance et la justification des connaissances principales pour chaque catégorie. Pour plus d’informations, [consultez le rapport Forrester](https://vc2prod.blob.core.windows.net/vc-resources/TEIStudies/TEI%20of%20Microsoft%20365%20E5%20-%20Oct%202018.pdf).

### <a name="content-collaboration-details"></a>Détails de la collaboration de contenu

Le principal aperçu de la collaboration de contenu est le nombre de personnes qui créent, lisent et collaborent (modifier et partager) en ligne. Ces mesures sont importantes car les recherches montrent que lorsque des personnes collaborent avec des fichiers en ligne, chaque personne enregistre une moyenne de 2 heures par semaine.

Nous définissons la collaboration de contenu comme une seule personne à la création et au partage d’un fichier Office, puis au moins une autre personne la lisant. 

**Lecteurs**: personnes qui accèdent ou téléchargent des fichiers en ligne dans OneDrive ou SharePoint.

**Créateurs :** Les personnes qui créent, modifient, chargent, synchronisent, archivent, copient ou déplacent des fichiers OneDrive ou SharePoint en ligne.

**Collaborateurs**: personnes qui collaborent avec des fichiers en ligne à l’aide de OneDrive ou de SharePoint. Deux personnes sont des collaborateurs, si l’une d’elles lit ou modifie une application Office en ligne ou un document Cloud PDF après que l’autre personne l’a créée ou modifiée, dans une fenêtre de 28 jours.

Les types de fichiers pris en compte pour la collaboration sont Word, Excel, PowerPoint, OneNote et PDF.

Nous fournissons des informations sur les heures de démarrage et la configuration des appareils dans votre organisation, ainsi que des informations sur la connectivité réseau pour la collaboration de contenu car la collaboration en ligne de fichiers nécessite des appareils fiables qui démarrent rapidement et disposent de logiciels à jour, ainsi que d’une bonne connectivité à Microsoft 365.

### <a name="communication-details"></a>Détails de communication

Le premier aperçu de la communication est la fréquence à laquelle les personnes de votre organisation utilisent la messagerie, la conversation et les publications communautaires pour communiquer. Lorsque les utilisateurs utilisent un grand nombre d’outils de communication en temps réel, ils peuvent choisir le mode de communication qui leur permet d’être le plus efficace, par exemple les conversations et les communautés qui les aident à développer des relations entre les différents emplacements Office.

### <a name="mobility-details"></a>Détails de la mobilité

Le principal aperçu de la mobilité est le nombre de personnes qui accèdent aux fichiers et utilisent la messagerie et la conversation sur plusieurs plateformes. La possibilité de travailler à partir de n’importe quel appareil qu’ils choisissent est importante pour les personnes ayant des rôles commerciaux, les cadres dirigeants, les consultants et les autres personnes qui ont besoin de travailler à distance du Bureau pour être productifs. Les améliorations apportées à ces travailleurs ont un impact important. 

Nous mesurons le pourcentage et le nombre absolu de personnes qui ont utilisé au moins une application de productivité Microsoft 365 sur deux ou plusieurs plateformes, y compris les ordinateurs de bureau, les appareils mobiles et les sites Web. Les applications de productivité que nous évaluons sont Outlook, teams, Word, Excel, PowerPoint, OneNote, Yammer et Skype. Les utilisateurs doivent disposer des applications Microsoft 365 pour les licences Enterprise, Exchange, Yammer, Skype ou Teams. 

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
