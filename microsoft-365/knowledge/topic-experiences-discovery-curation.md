---
title: Découverte et curation de rubriques dans Sujets Microsoft Viva
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: cjtan
audience: admin
ms.topic: article
ms.service: ''
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-viva-topics
ms.localizationpriority: medium
description: Vue d’ensemble de la façon dont les rubriques sont découvertes dans Les rubriques de Topics.
ms.openlocfilehash: ef9bb8db55182475641020fddabf5654acfb9d0d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60150509"
---
# <a name="topic-discovery-and-curation-in-microsoft-viva-topics"></a>Découverte et curation de rubriques dans Sujets Microsoft Viva 

Ces rubriques organisent les informations selon les connaissances de votre environnement Microsoft 365 de travail. Nous avons tous lu des documents et des pages de site dans des termes que nous ne connaissez pas. De nombreuses fois, nous arrêtons ce que nous faisons pour consacrer beaucoup de temps à la recherche d’informations supplémentaires.

Cette rubrique utilise Microsoft Graph et l’IA pour identifier **les sujets** de votre organisation.  Une rubrique est une expression ou un terme qui a une signification spécifique pour l’organisation et qui comprend des ressources qui peuvent aider les personnes à comprendre ce qu’elle est et à trouver plus d’informations à son sujet. Il existe différents types de rubriques qui seront importants pour votre organisation. Initialement, les types de rubriques suivants peuvent être identifiés :

- Project
- Événement
- Organisation
- Emplacement
- Produit
- Travail créatif
- Champ d’étude

L’IA identifie les personnes et le contenu connectés à la rubrique, et si un nombre suffisant est découvert, il devient une rubrique suggérée. Il recherche les propriétés suivantes et les affiche sur une *page de rubrique*:

- Autres noms et/ou acronymes.
- Une brève description de la rubrique.
- Contacts qui sont peut-être bien informés sur la rubrique.
- Fichiers, pages et sites associés à la rubrique.

Les propriétés sont identifiées à partir des fichiers et des pages qui font partie des preuves permettant d’identifier la rubrique. D’autres noms et acronymes sont issus de ces fichiers et pages. La description courte est provenant de ces fichiers et pages, ou d’Internet via Wikipedia. Le fichier source, la page ou l’article Wikipedia est référencé avec les propriétés suggérées. Les utilisateurs sont suggérés en fonction de leurs contributions actives (par exemple, les modifications) dans les fichiers et les pages. Une référence au montant des contributions d’une personne particulière fournit un conseil sur la raison pour laquelle la personne a été identifiée. Les fichiers, les pages et les sites sont classés selon qu’ils sont au cœur de la rubrique ou s’ils peuvent donner une vue d’ensemble ou une présentation de la rubrique. 

Toutes les rubriques identifiées ne seront pas utiles à votre organisation. Il n’a peut-être pas identifié les autres noms, descriptions, personnes ou contenus appropriés. La possibilité d’ajouter des rubriques qui ne sont pas identifiées, de conserver les rubriques suggérées et de les organiser est donc essentielle pour améliorer la qualité des rubriques qui sont découvrables dans votre organisation.

Rubriques, lorsque le contexte est approprié, suggère que ces rubriques doivent être mises en surbrill SharePoint pages de site modernes dans votre client. Cette rubrique peut également être référencé directement sur la page SharePoint site moderne par un auteur de page. Lorsqu’un utilisateur est curieux d’en savoir plus sur un  sujet, il peut sélectionner la rubrique mise en évidence pour afficher une carte récapitulatif rubrique qui fournit une brève description. S’ils souhaitent en savoir plus, ils peuvent sélectionner un lien **Détails** de la rubrique dans le résumé pour ouvrir la page de rubrique détaillée.

![Points forts de la rubrique.](../media/knowledge-management/saturn.png) </br>

En outre, les utilisateurs pourront également trouver des rubriques par Recherche Microsoft.

## <a name="topic-curation-and-feedback"></a>Curation de rubrique et commentaires

Cette rubrique vous permet d’apporter une contribution humaine pour améliorer la qualité de vos rubriques. Alors que l’IA identifie et suggère initialement des rubriques, les modifications manuelles du contenu des collaborateurs, l’ajout manuel de rubriques, la confirmation des utilisateurs pour les propriétés et le contenu découverts par l’IA et les commentaires sur l’utilité des rubriques sont tous essentiels.

- Les rubriques peuvent être examinées par **les responsables de connaissances** de votre organisation. Le gestionnaire de connaissances peut consulter les rubriques qu’il est autorisé à consulter. Dans la page Gérer les rubriques dans le centre de **rubriques,** ils peuvent choisir de confirmer les rubriques générées par l’IA (« sujets suggérés ») comme valides, de rejeter les rubriques pour empêcher que le contenu ne soit considéré comme une rubrique, de créer des rubriques qui n’ont pas été découvertes par l’IA ou d’identifier les rubriques qui pourraient bénéficier de quelques modifications par des experts techniques pour être plus utiles ou précises. Pour plus d’informations, [voir Gérer les rubriques dans le centre de rubriques.](manage-topics.md)

- Vous pouvez attribuer *des autorisations* créer et modifier des rubriques à n’importe quel utilisateur sous licence afin qu’il puisse apporter des modifications à des rubriques existantes ou créer de nouvelles rubriques. Cela permet aux utilisateurs qui sont informés de la rubrique de mettre à jour la page de rubrique directement pour apporter des corrections ou ajouter des informations supplémentaires. Ils peuvent également ajouter de nouvelles rubriques que l’IA n’a pas pu identifier. S’il existe suffisamment d’informations sur ces rubriques ajoutées manuellement et que l’IA est en mesure d’identifier ce type de rubrique, des suggestions supplémentaires de l’IA peuvent améliorer ces rubriques ajoutées manuellement. Ensemble, les humains et l’IA peuvent conserver des connaissances précises au fil du temps et ne pas avoir ce reste sur une seule personne. Pour plus d’informations, [voir Créer une rubrique et](./create-a-topic.md) modifier une [rubrique.](./edit-a-topic.md)

- Même les utilisateurs qui ont uniquement accès en lecture à des rubriques (visionneuses de rubriques) sont invités à vérifier l’utilité de rubriques spécifiques. Les questions de commentaires sont posées sur la carte **récapitulatif rubrique** pour améliorer la valeur de la rubrique et ses informations. Les questions sur la qualité et l’utilité des suggestions d’IA sont présentées une par une aux utilisateurs. Les questions sont les suivantes :

    1. Si l’identification de la rubrique dans la page SharePoint a été utile. Vous avez la possibilité de supprimer la mise en surbrill valeur si elle n’est pas précise ou utile. Si suffisamment de personnes indiquent qu’une rubrique n’est pas correctement identifiée sur une page particulière, ce surbrillant sera finalement supprimé pour tous les utilisateurs. 

    2. Indique si la rubrique suggérée est utile pour l’organisation. Si suffisamment de personnes indiquent que la rubrique suggérée est utile, la rubrique est automatiquement confirmée. Sinon, si la rubrique suggérée n’est pas utile, elle est automatiquement rejetée. Le gestionnaire de connaissances peut observer cette activité dans la page **Gérer les rubriques.**

    3. Si les suggestions de personnes et de ressources sont utiles.

    4. Dans la page d’accueil du centre de rubriques, vous pouvez voir les rubriques de votre organisation avec lesquelles vous êtes en relation. Vous pouvez choisir de rester répertorié dans la rubrique ou de vous supprimer vous-même. Ce commentaire est reflété à tous les utilisateurs qui découvrent cette rubrique. Pour plus d’informations sur la page d’accueil du centre de rubriques, voir la vue [d’ensemble du centre de rubriques.](./topic-center-overview.md)

Même avec des modifications humaines, l’IA recherche continuellement plus d’informations sur les sujets et recherche la vérification humaine. Par exemple, si l’IA pense que vous êtes une personne qui doit être répertoriée en tant qu’expert sur un sujet, elle vous demandera de le confirmer. 

