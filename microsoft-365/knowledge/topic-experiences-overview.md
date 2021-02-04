---
title: Vue d’ensemble des expériences de rubrique (aperçu)
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-topics
localization_priority: None
ROBOTS: NOINDEX, NOFOLLOW
description: Vue d’ensemble des expériences de rubrique.
ms.openlocfilehash: 46f98a9a247160d73e52c51df5f3001aa2f0f6e0
ms.sourcegitcommit: c0cfb9b354db56fdd329aec2a89a9b2cf160c4b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50094818"
---
# <a name="topic-experiences-overview-preview"></a>Vue d’ensemble des expériences de rubrique (aperçu)

> [!Note] 
> Le contenu de cet article est pour Project Private Preview. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Les expériences de rubrique utilisent la technologie Microsoft AI, Microsoft 365, Microsoft Graph, la recherche et d’autres composants et services pour créer un réseau de connaissances dans votre environnement Microsoft 365. 

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LhZP]  

</br>

Son objectif est de convertir les informations en connaissances et de les fournir à vos utilisateurs dans les applications qu’ils utilisent quotidiennement, telles que les pages modernes SharePoint et Recherche Microsoft.

Les expériences de rubrique permettent de résoudre un problème d’entreprise clé dans de nombreuses entreprises , en fournissant les informations aux utilisateurs lorsqu’ils en ont besoin. Par exemple, les nouveaux employés ont besoin d’apprendre beaucoup de nouvelles informations rapidement et de rencontrer des termes qu’ils ne connaissent pas lors de la lecture des informations de l’entreprise. Pour en savoir plus, l’utilisateur peut avoir besoin de s’éloigner de ce qu’il fait et de passer du temps précieux à rechercher des détails, tels que des informations sur ce qu’est le terme, qui dans l’organisation est un expert en la matière, et peut-être des sites et des documents liés au terme.

Les expériences de rubrique utilisent l’IA pour rechercher et identifier automatiquement **les rubriques** de votre organisation. Il compile les informations les concernant, telles qu’une brève description, les personnes qui travaillent sur la rubrique, ainsi que les sites, fichiers et pages qui y sont associés. Un gestionnaire de connaissances ou un collaborateur peut choisir de mettre à jour les informations de la rubrique selon les besoins. Les rubriques sont accessibles à vos utilisateurs, ce qui signifie que pour chaque instance de la rubrique qui apparaît dans un site SharePoint moderne dans les actualités et les pages, le texte est mis en surbrillant. Les utilisateurs peuvent choisir de sélectionner la rubrique pour en savoir plus à ce sujet via les détails de cette rubrique. Vous pouvez également trouver des rubriques dans la recherche SharePoint.


## <a name="how-topics-are-displayed-to-users"></a>Affichage des rubriques pour les utilisateurs

Lorsqu’une rubrique est mentionnée dans le contenu des actualités et des pages SharePoint, elle est mise en surbrillable. Vous pouvez ouvrir le résumé de la rubrique à partir du surbrillant. Ouvrez les détails de la rubrique à partir du titre du résumé. La rubrique mentionnée peut être identifiée automatiquement ou a été ajoutée à la page avec une référence directe à la rubrique par l’auteur de la page. 

   ![Points forts de la rubrique](../media/knowledge-management/saturn.png) </br> 


## <a name="knowledge-indexing"></a>Indexation des connaissances

Les expériences de rubrique utilisent la technologie Microsoft AI pour identifier **les rubriques** de votre environnement Microsoft 365.

Une rubrique est une expression ou un terme qui est important ou significatif d’un point de vue organisationnel. Il a une signification spécifique pour l’organisation et dispose de ressources liées à celle-ci qui peuvent aider les personnes à comprendre ce qu’il est et trouver plus d’informations à ce sujet. Il existe de nombreux types de rubriques qui seront importants pour votre organisation. À l’origine, la technologie Microsoft AI se concentre sur les types suivants :
- Project
- Événement
- Organisation
- Lieu
- Produit
- Travail créatif
- Champ d’étude


Lorsqu’une rubrique est identifiée et que l’IA détermine qu’elle dispose de suffisamment d’informations pour qu’elle soit une rubrique suggérée, une **page** de rubrique affiche les informations qui ont été recueillies par le biais de l’indexation des rubriques, telles que :

- Autres noms et/ou acronymes.
- Brève description de la rubrique.
- Personnes qui sont peut-être au fait de cette rubrique.
- Fichiers, pages et sites associés à la rubrique.

Vos administrateurs de connaissances peuvent choisir d’analyser tous les sites SharePoint de votre client pour des rubriques ou de sélectionner simplement certains sites.

Voir [la découverte et la curation des rubriques](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery-curation)

## <a name="roles"></a>Rôles

Lorsque vous utilisez les expériences Rubrique dans votre environnement Microsoft 365, vos utilisateurs auront les rôles suivants :

- Visionneuses de rubriques : utilisateurs qui pourront voir les  points forts de la rubrique sur les sites modernes SharePoint pour qui ils ont au moins un accès en lecture, et dans Microsoft Search (recherche Microsoft). Ils pourront sélectionner les points forts de la rubrique pour voir les détails des rubriques dans les pages de rubriques. Les visiteurs des rubriques pourront fournir des commentaires sur l’utilité d’une rubrique pour eux.

- Collaborateurs : utilisateurs ayant le droit de modifier des rubriques existantes ou d’en créer de nouvelles. Les administrateurs du savoir attribuent des autorisations de collaborateur aux utilisateurs via les paramètres expériences de rubrique dans le Centre d’administration Microsoft 365. Notez que vous pouvez également choisir de donner à tous les visiteurs des rubriques l’autorisation de modifier et de créer des rubriques afin que tout le monde puisse contribuer aux rubriques qu’ils voient.

- Gestionnaires de connaissances : utilisateurs qui guident des rubriques tout au long du cycle de vie de la rubrique. Les gestionnaires de connaissances utilisent la page Gérer les rubriques dans le centre de **rubriques** pour confirmer les rubriques suggérées par l’IA, supprimer les rubriques qui ne sont plus pertinentes, ainsi que modifier des rubriques existantes ou en créer de nouvelles, et sont les seuls utilisateurs qui y ont accès. Les administrateurs du savoir attribuent des autorisations de gestionnaire de connaissances aux utilisateurs via les paramètres d’administration expériences de rubrique dans le Centre d’administration Microsoft 365. 

- Administrateurs du savoir : les administrateurs du savoir configurer les expériences de rubrique et les gérer via les contrôles d’administration dans le Centre d’administration Microsoft 365. Actuellement, un administrateur général Microsoft 365 ou SharePoint peut faire office d’administrateur de connaissances.

Pour plus [d’informations, voir](topic-experiences-roles.md) Rôles Expériences de rubrique.

## <a name="topic-management"></a>Gestion des rubriques

La gestion des rubriques est effectuée dans la page **Gérer les rubriques** dans le centre **de rubriques de votre organisation.** Le centre de rubriques est créé lors de l’installation et fait office de centre de connaissances pour votre organisation. 

Bien que tous les utilisateurs titulaires d’une licence puissent voir les rubriques avec qui ils sont connectés dans le centre de rubriques, seuls les utilisateurs ayant des autorisations Gérer les *rubriques* (gestionnaires de connaissances) pourront afficher et utiliser la page Gérer les rubriques.

Les gestionnaires de connaissances pourront :

- Confirmez ou supprimez les rubriques qui ont été découvertes dans votre client.
- Créez de nouvelles rubriques manuellement selon vos besoins (par exemple, si les informations fournies ne sont pas suffisantes pour qu’elles soient découvertes via l’IA).
- Modifier des pages de rubriques existantes.</br>

Pour [plus d’informations, voir](manage-topics.md) Gérer les rubriques dans le centre de rubriques.  


## <a name="admin-controls"></a>Contrôles d’administration

Les contrôles d’administration dans le Centre d’administration Microsoft 365 vous permettent de gérer votre réseau de connaissances. Ils permettent à un administrateur général microsoft 365 ou SharePoint de :

- Contrôler les utilisateurs de votre organisation autorisés à voir les rubriques dans les pages modernes SharePoint ou dans les résultats de recherche SharePoint.
- Contrôler les sites SharePoint qui seront analyser pour identifier les rubriques.
- Exclure des rubriques spécifiques de la recherche.
- Contrôler les utilisateurs qui peuvent gérer les rubriques dans le centre de rubriques.
- Contrôler les utilisateurs qui peuvent créer et modifier des rubriques.
- Contrôler l’utilisateur qui pourra afficher les rubriques.

Pour plus d’informations sur les [](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery) contrôles d’administration, [](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-knowledge-rules)voir attribuer des autorisations aux [utilisateurs,](https://docs.microsoft.com/microsoft-365/knowledge/plan-topic-experiences#user-permissions)gérer la visibilité des rubriques et gérer la découverte de rubriques.

## <a name="topic-curation--feedback"></a>Retour d'& de la & rubrique

L’IA s’efforce continuellement de vous fournir des suggestions pour améliorer vos rubriques à mesure que des modifications se produisent dans votre environnement. 

Les utilisateurs qui ont des autorisations de modification ou de création de rubriques peuvent effectuer des mises à jour des pages de rubriques directement s’ils souhaitent apporter des corrections ou ajouter des informations supplémentaires. Ils peuvent également ajouter de nouvelles rubriques que l’IA n’a pas pu identifier. S’il existe suffisamment d’informations sur ces rubriques ajoutées manuellement et que l’IA est en mesure d’identifier ce type de rubrique, des suggestions supplémentaires de l’IA peuvent améliorer ces rubriques ajoutées manuellement 

Les utilisateurs qui vous permettent d’accéder à des rubriques dans leur travail quotidien peuvent être invités à savoir si cette rubrique leur était utile. Le système examine ces réponses et les utilise pour améliorer la mise en évidence des rubriques et aider à déterminer ce qui est affiché dans les résumés des rubriques et dans les détails de la rubrique.

En outre, les utilisateurs ayant les autorisations adéquates peuvent baliser des éléments tels que Yammer conversation pertinente pour une rubrique et les ajouter à une rubrique spécifique. 

Voir [la découverte et la curation des rubriques](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery-curation)


## <a name="see-also"></a>Voir aussi

