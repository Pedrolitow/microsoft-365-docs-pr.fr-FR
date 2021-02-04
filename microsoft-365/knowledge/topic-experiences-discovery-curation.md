---
title: 'Découverte et curation des rubriques Expériences de rubrique (prévisualisation) '
description: Vue d’ensemble de la découverte des rubriques.
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-topics
ROBOTS: NOINDEX, NOFOLLOW
localization_priority: None
ms.openlocfilehash: b9f4d0e33cb7a74b921681709e3ef68780dd76c4
ms.sourcegitcommit: c0cfb9b354db56fdd329aec2a89a9b2cf160c4b0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "50094842"
---
# <a name="topic-discovery-and-curation-preview"></a>Découverte et curation de rubrique (aperçu)

> [!Note] 
> Le contenu de cet article est pour Project Private Preview. [En savoir plus sur le Projet cortex](https://aka.ms/projectcortex).

Les expériences de rubrique convertissent les informations de connaissances en connaissances dans votre environnement Microsoft 365. Nous avons tous lu des documents et des pages de site dans des termes que nous ne connaissez pas. De nombreuses fois, nous arrêtons ce que nous faisons pour consacrer beaucoup de temps à la recherche d’informations supplémentaires.

Les expériences de rubrique utilisent Microsoft Graph et l’IA pour identifier **les rubriques** de votre organisation.  Une rubrique est une expression ou un terme qui a une signification spécifique pour l’organisation et qui possède des ressources associées qui peuvent aider les personnes à comprendre ce qu’il est et trouver plus d’informations à son sujet. Il existe de nombreux types de rubriques qui seront importants pour votre organisation. Initialement, les types de rubriques suivants peuvent être identifiés :
- Project
- Événement
- Organisation
- Lieu
- Produit
- Travail créatif
- Champ d’étude

L’IA identifie les personnes et le contenu connectés à la rubrique, et si un nombre suffisant est découvert, il devient une rubrique suggérée. Il recherche les propriétés suivantes et les affiche sur une **page Rubrique**:
- Autres noms et/ou acronymes.
- Brève description de la rubrique.
- Personnes qui sont peut-être au fait de cette rubrique.
- Fichiers, pages et sites associés à la rubrique.

Les propriétés sont identifiées à partir des fichiers et des pages qui font partie des preuves permettant d’identifier la rubrique. D’autres noms et acronymes sont issus de ces fichiers et pages. La description courte est provenant de ces fichiers et pages, ou d’Internet via Wikipedia. Le fichier source, la page ou l’article Wikipedia est référencé avec les propriétés suggérées. Les utilisateurs sont suggérés en fonction de leurs contributions actives (telles que les modifications) dans les fichiers et les pages. Une référence au montant des contributions d’une personne particulière fournit un conseil sur la raison pour laquelle la personne a été identifiée. Les fichiers, les pages et les sites sont classés selon qu’ils sont au cœur de la rubrique, s’ils peuvent donner une vue d’ensemble ou une présentation de la rubrique. 

Toutes les rubriques identifiées ne seront pas utiles à votre organisation ou ont identifié les autres noms ou une description corrects, les personnes ou le contenu appropriés, de sorte que la possibilité d’ajouter des rubriques qui n’ont pas été identifiées, de conserver des rubriques suggérées et de organiser des rubriques est essentielle pour améliorer la qualité des rubriques qui sont découvrables dans votre organisation.

Les expériences des rubriques, lorsque le contexte est approprié, suggèrent que ces rubriques soient mises en surbrillantes sur toutes les pages de site moderne SharePoint dans votre client. Cette rubrique peut également être référencé directement sur la page du site moderne SharePoint par un auteur de page. Lorsqu’un utilisateur est curieux d’en savoir plus sur un  sujet, il peut sélectionner la rubrique mise en évidence pour afficher une carte récapitulatif rubrique qui fournit une brève description. S’ils souhaitent en savoir plus, ils peuvent sélectionner un lien **Détails** de la rubrique dans le résumé pour ouvrir la page de rubrique détaillée.

![Points forts de la rubrique](../media/knowledge-management/saturn.png) </br>

En outre, les utilisateurs pourront également trouver des rubriques par le biais de Microsoft Search (recherche Microsoft).

## <a name="topic-curation-and-feedback"></a>Curation de rubrique et commentaires

Les expériences de rubriques sont les bienvenues dans la contribution humaine pour améliorer la qualité de vos rubriques. Alors que l’IA identifie et suggère initialement des rubriques, les modifications manuelles du contenu des collaborateurs, l’ajout manuel de rubriques, la confirmation des utilisateurs pour les propriétés et le contenu découverts par l’IA et les commentaires sur l’utilité des rubriques sont tous essentiels.

- Les rubriques peuvent être examinées par **les responsables de connaissances** de votre organisation. Le gestionnaire de connaissances peut consulter les rubriques qu’il est autorisé à consulter. Dans la page Gérer les rubriques du Centre de rubriques, ils peuvent choisir de confirmer les rubriques générées par l’IA (« sujets suggérés ») comme valides, de rejeter les rubriques pour empêcher que le contenu ne soit considéré comme une rubrique, de créer des rubriques qui n’ont pas été découvertes par l’IA ou d’identifier les rubriques qui pourraient bénéficier de quelques modifications par des experts techniques pour être plus utiles ou précises. Pour [plus d’informations, voir](manage-topics.md) Gérer les rubriques dans le centre de rubriques.

- Vous pouvez attribuer *des autorisations* créer et modifier des rubriques à n’importe quel utilisateur sous licence afin qu’il puisse apporter des modifications à des rubriques existantes ou créer de nouvelles rubriques. Cela permet aux utilisateurs qui sont informés de la rubrique de mettre à jour la page de rubrique directement pour apporter des corrections ou ajouter des informations supplémentaires. Ils peuvent également ajouter de nouvelles rubriques que l’IA n’a pas pu identifier. S’il existe suffisamment d’informations sur ces rubriques ajoutées manuellement et que l’IA est en mesure d’identifier ce type de rubrique, des suggestions supplémentaires de l’IA peuvent améliorer ces rubriques ajoutées manuellement. Ensemble, les humains et l’IA peuvent conserver des connaissances précises au fil du temps et ne pas avoir ce reste sur une seule personne. Pour [plus d’informations, voir](https://docs.microsoft.com/microsoft-365/knowledge/create-a-topic) Créer une rubrique et [Modifier](https://docs.microsoft.com/microsoft-365/knowledge/edit-a-topic) une rubrique.

- Même les utilisateurs qui ont uniquement accès en lecture à des rubriques (visionneuses de rubriques) sont invités à vérifier l’utilité de rubriques spécifiques. Les questions de commentaires sont posées sur la carte **récapitulatif rubrique** pour améliorer la valeur de la rubrique et ses informations. Les questions sur la qualité et l’utilité des suggestions d’IA sont présentées une par une aux utilisateurs. Les questions sont les suivantes :
1. L’identification de la rubrique dans la page SharePoint a-t-elle été utile ? Vous avez la possibilité de supprimer le surbrillant s’il n’est pas précis ou utile. Si suffisamment de personnes indiquent qu’une rubrique n’est pas correctement identifiée sur une page particulière, ce surbrillant sera finalement supprimé pour tous les utilisateurs. 

2. Indique si la rubrique suggérée est utile pour l’organisation. Si suffisamment de personnes indiquent que la rubrique suggérée est utile, la rubrique est automatiquement confirmée. Sinon, si la rubrique suggérée n’est pas utile, elle est automatiquement rejetée. Le Gestionnaire de connaissances peut observer cette activité dans l’affichage Gérer les rubriques.

3. Si les suggestions de personnes et de ressources sont utiles.

4. Dans la page d’accueil du Centre de rubriques, vous pouvez consulter les rubriques de votre organisation avec lesquelles vous êtes en relation. Vous pouvez choisir de rester répertorié dans la rubrique ou de vous supprimer vous-même. Ce commentaire est reflété à tous les utilisateurs qui découvrent cette rubrique. Voir [la vue d’ensemble](https://docs.microsoft.com/microsoft-365/knowledge/topic-center-overview) du centre de rubriques pour plus d’informations sur la page d’accueil du centre de rubriques.

Même avec des modifications humaines, l’IA recherche continuellement plus d’informations sur les sujets et recherche la vérification humaine. Par exemple, si l’IA pense que vous êtes une personne qui doit être répertoriée en tant qu’expert sur un sujet, elle vous demandera de le confirmer. 


## <a name="see-also"></a>Voir aussi
