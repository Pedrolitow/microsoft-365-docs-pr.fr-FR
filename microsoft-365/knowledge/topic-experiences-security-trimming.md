---
title: La rubrique rencontre un filtrage de sécurité (aperçu)
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
description: Vue d’ensemble de l’utilisation de la sécurité pour afficher les rubriques.
ms.openlocfilehash: 7e503082494d27f9418b8e09b8d20d01e4708fe9
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49698954"
---
# <a name="topic-experiences-security-trimming-preview"></a>La rubrique rencontre un filtrage de sécurité (aperçu)

> [!Note] 
> Le contenu de cet article est destiné à Project cortex privé preview. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Rubrique Experience les utilisateurs ne peuvent pas afficher les informations dans les rubriques que leurs autorisations Office 365 existantes les empêchent de voir. Tout ce qu’un utilisateur voit sur une page de rubrique (par exemple, des sites SharePoint, des documents, des fichiers) sera des informations qu’il est déjà autorisé à voir. Les expériences de rubrique ne modifient pas les autorisations existantes.

## <a name="why-two-users-may-have-different-views-of-the-same-topic"></a>Pourquoi deux utilisateurs peuvent-ils avoir différentes vues du même sujet ?

Lorsqu’une rubrique est créée via AI ou une opération manuelle, elle peut contenir une description de la rubrique, des noms de substitution, des personnes associées à la rubrique, ainsi que des sites, des pages et des fichiers liés à la rubrique. Lorsque ces informations s’affichent sur une page de rubrique, il est possible que deux utilisateurs qui visualisent le même sujet ne voient pas les mêmes informations.
  
Par exemple, lorsque l’utilisateur 1 affiche la page de la rubrique Neptune, il s’agit de ce qu’il peut voir.

![Rubrique Neptune pour l’utilisateur 1](../media/knowledge-management/user2-topic-view.png) </br> 

Toutefois, lorsque l’utilisateur 2 regarde sur la même page de rubrique Neptune, son affichage diffère de l’utilisateur 1.  L’utilisateur 2 est en mesure de voir le fichier de *vue d’ensemble du produit DG-2000* dans la section **fichiers et pages épinglés** de la page de rubrique, qui ne s’affiche pas pour l’utilisateur 1. 

![Rubrique Neptune pour l’utilisateur 2](../media/knowledge-management/user1-topic-view.png) </br> 

La différence entre ce que les utilisateurs peuvent voir dans la même rubrique est que les utilisateurs ne disposent pas des autorisations Office 365 pour afficher un site ou un fichier associé.  Les expériences de rubrique respectent les autorisations définies sur les éléments d’une rubrique et ne peuvent pas modifier l’accès à celles-ci. Dans notre exemple, l’utilisateur 1 ne peut pas afficher le fichier de *vue d’ensemble du produit DG-2000* dans sa page de rubrique pour Neptune, car l’utilisateur 1 ne dispose pas des autorisations Office 365 pour afficher le fichier.

Si un utilisateur ne parvient pas à voir suffisamment d’informations dans une rubrique pour qu’il soit utile, la rubrique ne sera pas disponible pour l’utilisateur. Dans ce cas, l’utilisateur ne voit pas la rubrique en surbrillance. Toutefois, un autre utilisateur disposant d’autorisations pour accéder à des informations supplémentaires dans la rubrique pour qu’il soit utile, sera en mesure de voir la rubrique.


## <a name="topic-permissions-for-knowledge-managers-and-topic-contributors"></a>Rubriques d’autorisations pour les responsables du savoir et les contributeurs

Les utilisateurs auxquels sont attribués des autorisations pour gérer les rubriques-gestionnaires de connaissances-seront en mesure d’afficher les informations qu’ils sont autorisés à voir dans les rubriques.

De même, les utilisateurs qui disposent des autorisations de création et de modification de rubrique-Contributor de rubrique-seront uniquement en mesure d’afficher les informations qu’ils sont autorisés à voir dans les rubriques. 


## <a name="ai-versus-manually-curated-topic-information"></a>Informations sur les rubriques de la préversion et la facilité organisée manuellement

Les rubriques peuvent contenir des informations générées par les IA et des informations ajoutées ou modifiées par des collaborateurs ou des responsables du savoir.

 - Les informations d’une rubrique qui a été ajoutée par AI sont visibles uniquement pour les personnes ayant accès au contenu source.
 - Les informations qui ont été ajoutées ou modifiées manuellement par un collaborateur de rubrique ou le gestionnaire de connaissances sont visibles par tous les utilisateurs qui peuvent voir la rubrique.

Le tableau suivant décrit ce que les utilisateurs-consultants, contributeurs et gestionnaires de connaissances peuvent voir dans un sujet donné en fonction de leurs autorisations.

|Élément de rubrique|Ce que les utilisateurs peuvent voir|
|:---------|:------------------|
|Nom de la rubrique|Les utilisateurs peuvent voir le nom de toutes les rubriques dans le Centre des rubriques. Il se peut que certaines rubriques ne soient pas visibles si elles ont une faible pertinence pour l’utilisateur.|
|Description de la rubrique|Les descriptions générées par les IA sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source. Les descriptions entrées ou modifiées manuellement sont visibles par tous les utilisateurs.|
|Personnes|Les personnes en attente sont visibles par tous les utilisateurs. Les personnes suggérées sont uniquement visibles par les utilisateurs disposant d’autorisations sur le contenu source.|
|Fichiers|Les fichiers ne sont visibles que pour les utilisateurs qui disposent d’autorisations sur le contenu source.|
|Pages|Les pages sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source.|
|Sites|Les sites sont visibles uniquement pour les utilisateurs qui disposent d’autorisations sur le contenu source.|




## <a name="see-also"></a>Voir aussi

