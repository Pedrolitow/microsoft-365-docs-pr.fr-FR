---
title: Vue d’ensemble de la rubrique (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Vue d’ensemble des expériences de rubrique.
ms.openlocfilehash: 8b06dd016295c8b0712a7c18c2296a318cd826ba
ms.sourcegitcommit: 18f95c4b7f74881b4a6ce71ad2ffa78a6ead5584
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "49731320"
---
# <a name="topic-experiences-overview-preview"></a>Vue d’ensemble de la rubrique (aperçu)

> [!Note] 
> Le contenu de cet article est destiné à Project cortex privé preview. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Les expériences de rubrique utilisent la technologie Microsoft AI, Microsoft 365, Delve, Microsoft Graph, Search, ainsi que d’autres composants et services pour créer un réseau de connaissances dans votre environnement Microsoft 365. 

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LhZP]  

</br>

Son objectif est de convertir les informations en connaissances et de les transmettre à vos utilisateurs dans les applications qu’ils utilisent quotidiennement, telles que les pages modernes SharePoint et Microsoft Search.

Les expériences de rubrique vous aident à résoudre un problème métier clé dans de nombreuses sociétés, en fournissant les informations aux utilisateurs lorsqu’ils en ont besoin. Par exemple, les nouveaux employés ont besoin d’en savoir plus sur de nombreuses nouvelles informations et de présenter les termes qu’ils ne connaissent pas lors de la lecture via les informations de l’entreprise. Pour en savoir plus, il se peut que l’utilisateur doive s’absenter de ce qu’il fait et consacrer un temps précieux à la recherche de détails, tels que des informations sur ce terme, les personnes de l’organisation qui sont un expert, ainsi que des sites et des documents associés au terme.

Les expériences de rubrique utilisent l’AI pour rechercher et identifier automatiquement les **rubriques** de votre organisation. Elle compile des informations les concernant, telles qu’une brève description, des experts techniques sur le sujet, ainsi que des sites, des fichiers et des pages qui y sont associés. Un responsable du savoir ou un collaborateur peut choisir de mettre à jour les informations de la rubrique selon vos besoins. Les rubriques sont accessibles à vos utilisateurs, ce qui signifie que pour chaque instance de la rubrique qui apparaît dans un site SharePoint moderne dans Actualités et pages, le texte est mis en surbrillance. Les utilisateurs peuvent choisir la rubrique pour en savoir plus à ce sujet dans la rubrique Détails. Des rubriques sont également disponibles dans la recherche SharePoint.


## <a name="how-topics-are-displayed-to-users"></a>Comment les rubriques sont affichées pour les utilisateurs

Lorsqu’une rubrique est mentionnée dans contenu sur les actualités et pages SharePoint, elle apparaît en surbrillance. Vous pouvez ouvrir le résumé de la rubrique à partir de la mise en surbrillance. Ouvrez les détails de la rubrique à partir du titre du résumé. La rubrique mentionnée peut être identifiée automatiquement ou avoir été ajoutée à la page à l’aide d’une référence directe à la rubrique par l’auteur de la page. 

   ![Points de section](../media/knowledge-management/saturn.png) </br> 


## <a name="knowledge-indexing"></a>Indexation des connaissances

La rubrique expériences utilise la technologie Microsoft AI pour identifier les **rubriques** de votre environnement Microsoft 365.

Une rubrique est une expression ou un terme qui est significatif ou important au sein de l’organisation. Il a une signification spécifique pour l’organisation et a des ressources qui lui sont associées, qui peuvent aider les utilisateurs à comprendre ce qu’ils sont et à trouver plus d’informations à leur sujet.

Lorsqu’une rubrique est identifiée et que AI détermine qu’elle dispose de suffisamment d’informations pour qu’elle soit une suggestion de rubrique, une **page de rubrique** est créée pour elle, qui contient des informations collectées par le biais de l’indexation des rubriques, telles que :

- Autres noms et/ou acronymes.
- Brève description de la rubrique.
- Utilisateurs pouvant être informé de la rubrique.
- Fichiers, pages et sites associés à la rubrique.

Vos administrateurs de connaissances peuvent choisir d’analyser tous les sites SharePoint de votre client pour consulter les rubriques, ou simplement en sélectionner certains.

## <a name="roles"></a>Rôles

Lorsque vous utilisez des expériences de rubrique dans votre environnement Microsoft 365, vos utilisateurs auront les rôles suivants :

- Visionneuse de rubrique : utilisateurs qui seront en mesure de voir des points de vue sur les sites modernes SharePoint pour lesquels ils disposent au moins d’un accès *en lecture* à, et dans Microsoft Search. Ils pourront sélectionner des points de section en surbrillance pour afficher les détails de la rubrique dans les pages de rubrique. Les visionneuses de rubrique seront en mesure de fournir des commentaires sur l’utilité d’une rubrique.

- Contributeurs : utilisateurs disposant de droits pour modifier des rubriques existantes ou en créer de nouvelles. Les administrateurs des connaissances attribuent des autorisations de collaborateur à des utilisateurs via la rubrique Experience Settings dans le centre d’administration 365 de Microsoft. Notez que vous pouvez également choisir d’accorder à tous les visiteurs de la rubrique l’autorisation de modifier et de créer des rubriques afin qu’ils puissent également contribuer aux rubriques qu’ils voient.

- Gestionnaires de connaissances : utilisateurs qui guident dans le cycle de vie d’une rubrique. Les gestionnaires de connaissances utilisent la page **gérer les rubriques** dans le Centre des rubriques pour confirmer ou supprimer des rubriques ai-suggérées, ainsi que pour modifier des rubriques existantes ou en créer de nouvelles, et sont les seuls utilisateurs qui y ont accès. Les administrateurs des connaissances attribuent des autorisations de gestionnaire de connaissances aux utilisateurs via la rubrique Experience Settings Admin dans le centre d’administration 365 de Microsoft. 

- Knowledge admins : Knowledge admins configurez des expériences de rubrique et gérez-le via les contrôles d’administration dans le centre d’administration 365 de Microsoft. Actuellement, un administrateur global ou SharePoint Microsoft 365 peut servir d’administrateur de connaissances.

Pour plus d’informations, voir la [rubrique Experiences Roles](topic-experiences-roles.md) .

## <a name="topic-management"></a>Gestion des rubriques

La gestion des rubriques est réalisée dans la page **gérer les rubriques** du **Centre de rubrique** de votre organisation. Le centre de rubrique est créé lors de l’installation et sert de centre de connaissances pour votre organisation. 

Bien que tous les utilisateurs sous licence soient en mesure de voir les rubriques auxquelles ils sont connectés dans le centre de la rubrique, seuls les utilisateurs disposant des autorisations *gérer les rubriques* (gestionnaires de connaissances) peuvent afficher et utiliser la page gérer les rubriques.

Les responsables des connaissances seront en mesure de :

- Confirmez ou rejetez des rubriques qui ont été découvertes dans votre client.
- Créez de nouvelles rubriques manuellement en fonction de vos besoins (par exemple, si vous n’avez pas suffisamment d’informations pour qu’elles soient découvertes via AI).
- Modifier des pages de rubrique existantes.</br>

Pour plus d’informations, voir [gérer les rubriques dans le Centre des rubriques](manage-topics.md) .  


## <a name="admin-controls"></a>Contrôles d’administration

Les contrôles d’administration dans le centre d’administration Microsoft 365 vous permettent de gérer votre réseau de connaissances. Ils permettent à un administrateur global ou SharePoint de Microsoft 365 de :

- Contrôlez les utilisateurs de votre organisation autorisés à consulter les rubriques dans les pages modernes SharePoint ou dans les résultats de la recherche SharePoint.
- Contrôlez les sites SharePoint qui seront analysés pour rechercher des rubriques.
- Configurer la découverte de rubrique pour exclure des rubriques spécifiques de la recherche.
- Contrôlez les utilisateurs qui peuvent gérer les rubriques dans le Centre des rubriques.
- Contrôler les utilisateurs qui peuvent créer et modifier des rubriques dans le Centre des rubriques.
- Contrôler l’utilisateur qui pourra consulter les rubriques.

Pour plus d’informations sur les contrôles d’administration, consultez la rubrique [Assign User Permissions](https://docs.microsoft.com/microsoft-365/knowledge/plan-topic-experiences#user-permissions), [Manage topic Visibility](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-knowledge-rules)et [Manage topic Discovery](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery) .

## <a name="topic-curation--feedback"></a>& des commentaires sur les de la rubrique

AI continue de fournir des suggestions pour améliorer vos rubriques lorsque des modifications sont apportées dans votre environnement. 

Les utilisateurs qui autorisent l’accès à consulter les rubriques de leur travail quotidien peuvent être invités à indiquer si le sujet a été utile. AI examine ces réponses et les utilise pour déterminer ce qui est affiché sur les résumés de rubrique et dans les détails de la rubrique.

Les utilisateurs disposant des autorisations modifier ou créer des rubriques peuvent effectuer des mises à jour directement des pages de rubrique si elles souhaitent apporter des corrections ou ajouter des informations supplémentaires. 

En outre, les utilisateurs disposant des autorisations appropriées peuvent baliser des éléments tels que la conversation Yammer qui concernent une rubrique, et les ajouter à une rubrique spécifique. 


## <a name="see-also"></a>Voir aussi

