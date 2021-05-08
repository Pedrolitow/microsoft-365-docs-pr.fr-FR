---
title: Vue d’ensemble des rubriques de Microsoft Viva
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: cjtan
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-viva-topics
localization_priority: None
description: Présentation de Rubriques Viva.
ms.openlocfilehash: 1d66751d55c0144149fa8325e89be404e3df19ed
ms.sourcegitcommit: 8e4c107e4da3a00be0511b05bc655a98fe871a54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52281028"
---
# <a name="microsoft-viva-topics-overview"></a>Vue d’ensemble des rubriques de Microsoft Viva 

Cette rubrique utilise la technologie Microsoft AI, les Microsoft 365, Microsoft Graph, la recherche et d’autres composants et services pour apporter des connaissances à vos utilisateurs dans les applications Microsoft 365 qu’ils utilisent quotidiennement, en commençant par les pages modernes SharePoint, Recherche Microsoft et Recherche dans Word et PowerPoint.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LhZP]  

</br>

Rubriques Viva aide à résoudre un problème d’entreprise majeur dans de nombreuses entreprises, en fournissant les informations aux utilisateurs lorsqu’ils en ont besoin. Par exemple, les nouveaux employés doivent apprendre rapidement un grand nombre de nouvelles informations et rencontrer des conditions dont ils ne connaissent rien lorsqu’ils lisent les informations de l’entreprise. Pour en savoir plus, l’utilisateur devra peut-être s’éloigner de ce qu’il fait et consacrer un temps précieux à la recherche de détails, tels que des informations sur ce terme, les membres de l’organisation comme experts dans le domaine, et les sites et documents liés au terme.

Rubriques Viva utilise l’IA pour rechercher et identifier automatiquement **rubriques** dans votre organisation. Il compile les informations les concernant, telles qu’une brève description, les personnes travaillant sur le sujet, ainsi que les sites, fichiers et pages qui y sont associés. Un responsable des connaissances ou un collaborateur peut choisir de mettre à jour les informations de la rubrique selon vos besoins. Les rubriques sont accessibles à vos utilisateurs. Par conséquent, pour chaque occurrence de la rubrique qui apparaît sur un site SharePoint moderne dans les actualités et pages, le texte est mis en évidence. Les utilisateurs peuvent choisir de sélectionner la rubrique pour en savoir plus à son sujet via les détails de cette rubrique. Vous pouvez également trouver des rubriques dans la Recherche SharePoint.


## <a name="how-topics-are-displayed-to-users"></a>Affichage des rubriques pour les utilisateurs

Lorsqu’une rubrique est mentionnée dans du contenu sur des actualités et pages SharePoint, elle est mise en évidence. Vous pouvez ouvrir le résumé du sujet à partir de la mise en évidence. Ouvrez les détails du sujet à partir du titre du résumé. La rubrique mentionnée peut être identifiée automatiquement ou a été ajoutée à la page avec une référence directe à la rubrique par l’auteur de la page. 

   ![Points forts de la rubrique](../media/knowledge-management/saturn.png) 

Lorsque vous utilisez la recherche dans Word ou PowerPoint, soit par  le biais de la zone de recherche, soit en sélectionnant Rechercher dans le menu contextatif, les résultats affichés peuvent également afficher le résumé de la rubrique.

   ![Capture d’écran montrant la recherche dans Word via la zone de recherche.](../media/knowledge-management/word-search-2.png)

   ![Capture d’écran montrant la recherche dans Word par le biais du menu context de recherche.](../media/knowledge-management/word-search-1.png)

## <a name="knowledge-indexing"></a>Indexation des informations

Rubriques Viva utilise la technologie Microsoft IA pour identifier les **rubriques** dans votre environnement Microsoft 365.

Une rubrique est une expression ou un terme qui est significatif ou important du point de vue organisationnel. Il a une signification spécifique pour l’organisation et comprend des ressources liées qui peuvent aider les personnes à comprendre sa signification et à trouver des informations supplémentaires à son sujet. Il existe différents types de rubriques qui seront importants pour votre organisation. Dans un premier temps, la technologie d'IA de Microsoft se concentre sur les types suivants :
- Project
- Événement
- Organisation
- Emplacement
- Produit
- Travail créatif
- Champ d’étude


Lorsqu'une rubrique est identifiée et que l'IA détermine qu'elle contient suffisamment d'informations pour être une rubrique suggérée, une **page de rubrique** affiche les informations qui ont été recueillies par l'indexation de la rubrique, par exemple :

- Autres noms et acronymes.
- Une brève description de la rubrique.
- Contacts qui sont peut-être bien informés sur la rubrique.
- Fichiers, pages et sites associés à la rubrique.

Vos administrateurs d’informations peuvent choisir d’analyser tous les sites SharePoint dans votre client pour les sujets ou simplement en sélectionner certains.

Consultez [Découverte et traitement de rubrique](./topic-experiences-discovery-curation.md)

## <a name="roles"></a>Rôles

Lorsque vous utilisez Rubriques Viva dans votre environnement Microsoft 365, vos utilisateurs ont les rôles suivants :

- Visionneurs de rubriques : les utilisateurs qui peuvent voir les points forts des rubriques sur les sites modernes SharePoint auxquels ils ont au moins un accès *en lecture*, et dans la Recherche Microsoft. Ils peuvent sélectionner les points forts des rubriques pour en afficher les détails dans les pages des rubriques. Les visionneurs de rubriques peuvent fournir des commentaires sur l’utilité d’une rubrique pour eux.

- Contributeurs : utilisateurs ayant le droit de modifier des rubriques existantes ou d’en créer de nouveaux. Les administrateurs d’informations attribuent des autorisations de collaborateur aux utilisateurs via les paramètres Rubriques Viva du Centre d’administration Microsoft 365. Notez que vous pouvez également choisir de donner à tous les visionneurs de rubriques l'autorisation de modifier et de créer des rubriques afin que chacun puisse contribuer aux rubriques qu'il voit.

- Gestionnaires d’informations : utilisateurs qui guident les rubriques tout au long du cycle de vie des rubriques. Les responsables d’informations utilisent la page **Gérer les rubriques** du centre thématique pour confirmer les rubriques suggérées par l’IA, supprimer des rubriques qui ne sont plus pertinentes, modifier des rubriques existantes ou en créer de nouveaux, et sont les seuls utilisateurs à y accéder. Les administrateurs d’informations attribuent des autorisations de gestionnaire d’informations aux utilisateurs via les paramètres administrateur de Rubriques Viva du Centre d’administration Microsoft 365. 

- Administrateurs d’informations : les administrateurs d’informations configurera Rubriques Viva et la gèrent via les contrôles d’administration du Centre d’administration Microsoft 365. Actuellement, un administrateur général de Microsoft 365 ou SharePoint peut faire office d'administrateur d'informations.

Pour plus d’informations, consultez [Rôles Rubriques Viva](topic-experiences-roles.md).

## <a name="topic-management"></a>Gestion des rubriques

La gestion des rubriques est effectuée dans la page **Gérer les rubriques** dans le **Centre thématique** de votre organisation. Le centre thématique est créé pendant l’installation et sert de centre d’informations pour votre organisation. 

Alors que tous les utilisateurs titulaires d'une licence peuvent consulter les rubriques auxquelles ils sont connectés dans le centre de rubriques, seuls les utilisateurs ayant des autorisations *Gérer des rubriques* (gestionnaires d’informations) peuvent consulter et utiliser la page Gestion des rubriques.

Les responsables d’informations peuvent :

- Confirmez ou supprimez des rubriques qui ont été découverte dans votre client.
- Créez des rubriques manuellement si nécessaire (par exemple, si les informations fournies ne sont pas suffisantes pour être découvertes par l'IA).
- Modifier les pages de rubrique existantes.</br>

Pour plus d’information, consultez [Gérer les rubriques dans le centre thématique](manage-topics.md).  


## <a name="admin-controls"></a>Contrôles d’administration

Les contrôles d’administration dans Microsoft 365 centre d’administration vous permettent de gérer Les rubriques De LaSerrité. Ils permettent à un administrateur général Microsoft 365 ou SharePoint de :

- Contrôler quels utilisateurs de votre organisation sont autorisés à consulter les rubriques dans les pages modernes de SharePoint ou dans les résultats de recherche SharePoint.
- Contrôler les sites SharePoint qui seront analyser pour identifier les rubriques.
- Exclure des rubriques spécifiques.
- Contrôler les utilisateurs qui peuvent gérer les rubriques dans le centre thématique.
- Contrôler les utilisateurs qui peuvent créer et modifier des rubriques.
- Contrôler les utilisateurs qui peuvent consulter les rubriques.

Pour plus d’informations sur les contrôles d’administrateur, consultez [Attribuer des autorisations d’utilisateur](./plan-topic-experiences.md#user-permissions), [Gérer la visibilité d’une rubrique](./topic-experiences-knowledge-rules.md)et [Gérer la découverte de rubriques](./topic-experiences-discovery.md).

## <a name="topic-curation--feedback"></a>Traitement des rubriques et commentaires

L'IA s'efforcera continuellement de vous fournir des suggestions pour améliorer vos sujets au fur et à mesure que des modifications surviendront dans votre environnement. 

Les utilisateurs ayant des autorisations de modification ou de création de rubriques peuvent apporter des mises à jour aux pages des rubriques directement s’ils souhaitent apporter des corrections ou ajouter des informations supplémentaires. Ils peuvent également ajouter de nouvelles rubriques que l’IA n’a pas pu identifier. S'il y a suffisamment d'informations sur ces rubriques ajoutées manuellement et que l'IA est capable d'identifier ce type de rubrique, des suggestions supplémentaires de l'IA peuvent améliorer ces rubriques ajoutées manuellement. 

Les utilisateurs que vous autorisez à consulter les rubriques dans le cadre de leur travail quotidien peuvent se voir demander si la rubrique leur a été utile. Le système examine ces réponses et les utilise pour améliorer la mise en évidence de la rubrique, et vous aider à déterminer ce qui est affiché sur les résumés de rubrique et les détails des rubriques.

En outre, les utilisateurs ayant les autorisations appropriées peuvent identifier les éléments, tels que les conversations Yammer, qui sont pertinents pour un sujet, et les ajouter à une rubrique spécifique. 

Consultez [Découverte et traitement de rubrique](./topic-experiences-discovery-curation.md)


## <a name="see-also"></a>Voir aussi
