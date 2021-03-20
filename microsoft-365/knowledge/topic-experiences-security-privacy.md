---
title: Sécurité et confidentialité des rubriques microsoft
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye, cjtan
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Découvrez comment planifier la sécurité et la confidentialité des rubriques microsoft
ms.openlocfilehash: 9ac7ea085be115ef06244422713099c01ec50a36
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50917343"
---
# <a name="microsoft-viva-topics-security-and-privacy"></a>Sécurité et confidentialité des rubriques microsoft

Les rubriques utilisent les fonctionnalités de sécurité de contenu existantes dans Microsoft 365, ainsi que les contrôles administratifs, pour contrôler le contenu généré par l’IA affiché aux utilisateurs de votre organisation. C’est la combinaison des paramètres de sécurité Microsoft 365 (autorisations sur les sites, fichiers et dossiers) et des paramètres d’administration Rubriques qui déterminent ce qu’un utilisateur donné peut voir dans les rubriques.

La configuration de Rubriques ne modifie pas les contrôles d’accès existants sur le contenu de votre organisation. Les utilisateurs voient uniquement ce à quoi ils ont déjà accès.

Cet article décrit le fonctionnement des rubriques du point de vue de la sécurité et les options dont les administrateurs de connaissances et les gestionnaires de connaissances ont besoin pour contrôler la visibilité des rubriques. Lisez cet article dans le cadre de [votre planification des rubriques.](plan-topic-experiences.md)

Vous devez être familiarisé avec [](topic-center-overview.md)les [rubriques,](topic-experiences-overview.md)le centre de rubriques et comment travailler avec des rubriques dans le centre de [rubriques](manage-topics.md) avant de lire cet article.

## <a name="what-users-can-see-in-topics"></a>Ce que les utilisateurs peuvent voir dans les rubriques

Pour voir les rubriques, un utilisateur doit :

- Avoir une licence Rubriques
- Être une [visionneuse de rubriques,](topic-experiences-knowledge-rules.md#change-who-can-see-topics-in-your-organization) [un collaborateur ou un gestionnaire de connaissances](topic-experiences-user-permissions.md)

Ces deux éléments permettent aux utilisateurs d’afficher l’accès au centre de rubriques et de voir les points forts et les fiches de sujet.

En outre, les [](topic-experiences-user-permissions.md) collaborateurs de rubriques ont des autorisations de création et de modification pour les rubriques, et les gestionnaires de connaissances peuvent confirmer ou supprimer des rubriques.

Lorsqu’une rubrique est découverte pour la première fois, les gestionnaires de connaissances peuvent la voir dans le centre de rubriques. Selon l’intégralité et la pertinence de la rubrique, les visiteurs peuvent voir ou non la rubrique présentée dans les fiches de rubrique.

Les rubriques peuvent contenir des informations générées par l’IA et des informations ajoutées ou modifiées par des collaborateurs de rubriques ou des gestionnaires de connaissances.

- Les informations d’une rubrique ajoutée par l’IA sont visibles uniquement pour les personnes qui ont accès au contenu source.
- Le texte qui a été manuellement ajouté ou modifié par un collaborateur de rubrique ou un gestionnaire de connaissances est visible par tous les utilisateurs qui peuvent consulter cette rubrique.

Les visiteurs et les collaborateurs peuvent voir la liste des rubriques confirmées et publiées dans le centre de rubriques, mais les détails des rubriques qu’une personne donnée peut voir dépendent des autorisations dont elle dispose sur le matériel source et de la modification manuelle de la rubrique.

Le tableau suivant décrit ce que les utilisateurs (visiteurs de rubriques, collaborateurs et gestionnaires de connaissances) peuvent voir dans une rubrique donnée en fonction de leurs autorisations.

|Élément de rubrique|Ce que les utilisateurs peuvent voir|
|:---------|:------------------|
|Nom de la rubrique|Les utilisateurs peuvent voir le nom de toutes les rubriques dans le centre de rubriques. Certaines rubriques peuvent ne pas être visibles si elles ont une faible pertinence pour l’utilisateur.|
|Description du sujet|Les descriptions générées par l’IA sont visibles uniquement pour les utilisateurs qui ont des autorisations sur le contenu source. Les descriptions entrées ou modifiées manuellement sont visibles pour tous les utilisateurs.|
|Personnes|Les personnes épinglées sont visibles par tous les utilisateurs. Les personnes suggérées sont visibles uniquement pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Fichiers|Les fichiers sont visibles uniquement pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Pages|Les pages sont visibles uniquement pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Sites|Les sites sont visibles uniquement pour les utilisateurs qui ont des autorisations sur le contenu source.|

## <a name="best-practices"></a>Les bonnes pratiques

Les rubriques présentent des informations aux utilisateurs en fonction de leurs autorisations existantes sur le contenu. Microsoft 365 offre de nombreuses façons de s’assurer que le contenu sensible est limité aux utilisateurs appropriés. Au-delà des autorisations d’équipe ou [](../compliance/data-loss-prevention-policies.md) de site standard, vous pouvez utiliser des étiquettes de sensibilité ou la protection contre la perte de données pour restreindre l’accès au contenu et aux révisions d’accès afin d’examiner régulièrement l’accès des utilisateurs aux informations [sensibles.](/azure/active-directory/governance/access-reviews-overview) [](../compliance/sensitivity-labels.md)

Nous vous recommandons d’utiliser ces outils pour vous assurer que vos autorisations de contenu sont définies correctement au sein de votre organisation. Les expériences de rubrique peuvent ensuite fournir des informations utiles et appropriées à vos utilisateurs.

S’il existe des rubriques que vous souhaitez exclure entièrement des expériences de rubrique, vous pouvez également :

- [Exclure les sites SharePoint sensibles de la découverte de rubriques.](topic-experiences-discovery.md#select-sharepoint-topic-sources) Le contenu de ces sites n’apparaîtra pas dans les expériences de rubrique.

- [Exclure les rubriques par nom.](topic-experiences-discovery.md#exclude-topics-by-name) Les rubriques explicitement exclues n’apparaissent pas dans les expériences de rubrique.

- Faire supprimer des rubriques dans le centre de rubriques par les gestionnaires de connaissances.

En outre, nous vous recommandons les meilleures pratiques ci-après :

- Embauchez des responsables de connaissances de différents secteurs de votre organisation. Le fait de disposer de gestionnaires de connaissances avec une grande variété d’expertise et d’accès au contenu sous-jacent utilisé par l’IA peut vous aider à organiser les connaissances les plus utiles pour vos utilisateurs et à supprimer les informations sensibles si elles sont trouvées.

- Configurer un flux de travail pour demander des modifications. Les gestionnaires de connaissances, les propriétaires d’équipe ou de site doivent avoir un processus par lequel ils peuvent demander l’exclusion de rubriques ou de sites au début de nouveaux projets au sein de votre organisation ou s’ils trouvent du contenu avec des paramètres d’autorisation inappropriés.

- Soyez conscient de l’audience et de la sensibilité des informations lors de la création de descriptions de rubriques. Ces descriptions peuvent être visibles pour les utilisateurs qui n’ont pas d’autorisations sur le contenu source de la rubrique.

Bien que vous pouvez modifier les autorisations sur des pages de rubriques individuelles pour restreindre l’accès à un groupe spécifique d’utilisateurs, nous ne recommandons pas cette approche en raison du degré élevé d’effort administratif requis.

## <a name="see-also"></a>Voir aussi

[Configurer Teams avec trois niveaux de protection](../solutions/configure-teams-three-tiers-protection.md)

[Planifier les expériences de sujets](plan-topic-experiences.md)

[Configurer les expériences de sujets](set-up-topic-experiences.md)