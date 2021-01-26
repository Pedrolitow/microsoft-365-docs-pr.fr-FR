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
ms.collection:
- enabler-strategic
- m365initiative-topics
ROBOTS: NOINDEX, NOFOLLOW
localization_priority: None
ms.openlocfilehash: f7e8406ee7090387d4500f69955330466f28c6c0
ms.sourcegitcommit: 162c01dfaa2fdb3225ce4c24964c1065ce22ed5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "49976144"
---
# <a name="restrict-access-to-topics-in-topic-experiences"></a>Restreindre l’accès aux rubriques dans Expériences des rubriques

Dans Expériences de rubrique, les parties prenantes de votre organisation peuvent vouloir s’assurer que des rubriques spécifiques ne sont pas découvertes et exposées à vos utilisateurs sous licence. Par exemple, vous travaillez peut-être sur un projet dont vous ne souhaitez pas encore exposer d’informations. Bien que les autorisations Office 365 sur les sites, les fichiers et d’autres ressources empêchent les utilisateurs d’Expériences de rubrique d’afficher des informations sensibles dans des rubriques, il existe des protections supplémentaires pour empêcher la découverte de sujets spécifiques.

Bien que les administrateurs du savoir contrôlent les paramètres du réseau de connaissances afin d’empêcher la découverte de sujets, les gestionnaires de connaissances et les autres parties prenantes doivent savoir comment cela est fait pour pouvoir collaborer sur ce point.

> [!Important] 
> Cet article explique comment empêcher l’identification de rubriques par le biais de l’IA ou leur affichage dans votre environnement comme un dispositif de sécurité supplémentaire. Il est important de noter que dans Expériences des rubriques, les utilisateurs ne sont pas autorisés à afficher les informations d’une rubrique à partir des autorisations Office 365. Même si un utilisateur est en mesure d’afficher une rubrique, ses fichiers, ses sites et ses pages ne sont pas autorisés à afficher Office 365. Vous assurer que les autorisations sur les fichiers sensibles sont correctement définies doit être votre principal dispositif de sécurité.

## <a name="prevent-topics-from-being-identified"></a>Empêcher l’identification des rubriques

L’administrateur du savoir peut restreindre l’accès à des rubriques spécifiques en les empêchant d’être trouvés dans l’indexation initiale. Il existe deux façons de le faire dans les paramètres d’administration du réseau de connaissances dans le Centre d’administration Microsoft 365.
 
- [Sélectionnez des sites SharePoint à exclure](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery#select-sharepoint-topic-sources)de la découverte de rubriques : vous pouvez utiliser ce paramètre pour empêcher l’analyse de sites SharePoint spécifiques pour des rubriques.
- [Exclure les rubriques par leur nom](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-discovery#exclude-topics-by-name): les administrateurs peuvent utiliser ce paramètre pour empêcher la découverte de sujets spécifiques par leur nom. Dans les paramètres d’administration du réseau de connaissances, un administrateur peut télécharger une liste de rubriques à exclure dans un fichier CSV. Vous pouvez exclure les rubriques qui ont des correspondances exactes ou partielles d’un nom de rubrique.

## <a name="prevent-topics-from-being-viewed-by-specific-users"></a>Empêcher des utilisateurs spécifiques d’afficher des rubriques

Les administrateurs du savoir peuvent également sélectionner les personnes qui peuvent afficher [les rubriques de votre organisation.](https://docs.microsoft.com/microsoft-365/knowledge/topic-experiences-knowledge-rules) Ce paramètre vous permet de sélectionner les utilisateurs sous licence qui peuvent afficher toutes les rubriques. Par exemple, dans un environnement pilote, vous pouvez autoriser uniquement un petit groupe d’utilisateurs à afficher des rubriques.

## <a name="remove-topics-from-being-viewed"></a>Supprimer l’affichage des rubriques

Les gestionnaires de connaissances peuvent choisir [de supprimer des rubriques afin](https://docs.microsoft.com/microsoft-365/knowledge/manage-topics) que les utilisateurs ne les voient plus. Dans la page Gérer les rubriques dans le centre de **rubriques,** les gestionnaires de connaissances peuvent choisir de rejeter des rubriques spécifiques pour les empêcher d’être vues. Les rubriques peuvent être supprimées, qu’elles soient dans un état suggéré ou confirmé.

Les rubriques supprimées peuvent être ajoutées ultérieurement en tant que rubriques consultables si nécessaire. 


## <a name="see-also"></a>Voir aussi



  






