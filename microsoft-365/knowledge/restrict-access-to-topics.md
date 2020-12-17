---
title: Restreindre l’accès aux rubriques
description: Comment exclure des rubriques pour les empêcher d’être découvertes.
author: efrene
ms.author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection: enabler-strategic
ROBOTS: NOINDEX, NOFOLLOW
localization_priority: None
ms.openlocfilehash: b23d01585d9282132d9e55c74bb22bcdc6ca314a
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49698964"
---
# <a name="restrict-access-to-topics-in-topic-experiences"></a>Restreindre l’accès aux rubriques d’expériences

Dans les expériences de rubrique, les parties prenantes de votre organisation peuvent souhaiter s’assurer que des rubriques spécifiques ne sont pas découvertes et exposées à vos utilisateurs sous licence. Par exemple, vous pouvez travailler sur un projet pour lequel vous ne souhaitez pas exposer d’informations. Bien que les autorisations Office 365 sur les sites, les fichiers et les autres ressources empêchent les utilisateurs de consulter des informations sensibles dans les rubriques, il existe des mesures de sécurité supplémentaires pour empêcher les rubriques spécifiques d’être découvertes.

Tandis que les administrateurs du savoir contrôlent les paramètres du réseau de connaissances pour empêcher la découverte des rubriques, les responsables des connaissances et les autres parties prenantes ont besoin de savoir comment procéder afin qu’ils puissent travailler en collaboration sur ce.

> [!Important] 
> Cet article décrit les moyens d’empêcher l’identification des rubriques via les IA ou l’affichage dans votre environnement en tant que dispositif de sécurité supplémentaire. Il est important de noter que dans les expériences de rubrique, les utilisateurs ne sont pas autorisés à afficher quoi que ce soit dans une rubrique qu’ils ne sont pas autorisés à accéder par le biais des autorisations Office 365. Même si un utilisateur peut afficher un sujet, ses fichiers, ses sites et ses pages n’ont pas d’autorisations Office 365 à afficher ne seront pas visibles. Assurez-vous que les autorisations de fichiers sensibles sont définies correctement.

## <a name="prevent-topics-from-being-identified"></a>Empêcher l’identification des rubriques

Knowledge admin peut restreindre l’accès à des rubriques spécifiques en les empêchant de se trouver dans l’indexation initiale. Il existe deux façons de procéder dans les paramètres d’administrateur du réseau de connaissances dans le centre d’administration Microsoft 365.
 
- [Sélectionner les sites SharePoint à exclure de la découverte de rubrique](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery#select-sharepoint-topic-sources): vous pouvez utiliser ce paramètre pour empêcher que des sites SharePoint spécifiques soient analysés pour des rubriques.
- [Exclure les rubriques par nom](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery#exclude-topics-by-name): les administrateurs peuvent utiliser ce paramètre pour empêcher des rubriques spécifiques d’être découvertes par nom. Dans les paramètres d’administrateur du réseau de connaissances, un administrateur peut télécharger une liste de rubriques à exclure dans un fichier CSV. Vous pouvez exclure les rubriques qui ont des correspondances exactes ou partielles d’un nom de rubrique.

## <a name="prevent-topics-from-being-viewed-by-specific-users"></a>Empêcher l’affichage des rubriques par des utilisateurs spécifiques

Knowledge admins peut également [Sélectionner les personnes qui peuvent afficher les rubriques de votre organisation](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-knowledge-rules). Ce paramètre vous permet de sélectionner les utilisateurs sous licence qui peuvent afficher toutes les rubriques. Par exemple, dans un environnement pilote, vous pouvez uniquement autoriser un petit groupe d’utilisateurs à afficher des rubriques.

## <a name="remove-topics-from-being-viewed"></a>Supprimer les rubriques de l’affichage

Les gestionnaires de connaissances peuvent choisir de [supprimer des rubriques](https://docs.microsoft.com/microsoft-365/knowledge/manage-topics) afin que les utilisateurs ne puissent plus les voir. Sur la page **gérer les rubriques** dans le **Centre** des rubriques, les gestionnaires de connaissances peuvent choisir de rejeter des rubriques spécifiques afin de les empêcher d’être affichées. Les rubriques peuvent être supprimées, qu’elles soient dans un État suggéré ou confirmé.

Les rubriques supprimées peuvent ensuite être rajoutées en tant que rubriques affichables si nécessaire. 


## <a name="see-also"></a>Voir aussi



  






