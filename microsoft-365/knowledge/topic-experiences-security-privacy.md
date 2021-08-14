---
title: Sujets Microsoft Viva sécurité et confidentialité
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.reviewer: nkokoye, cjtan
audience: admin
ms.topic: article
ms.service: o365-administration
search.appverid: MET150
localization_priority: Normal
description: Découvrez comment planifier la sécurité et la confidentialité Sujets Microsoft Viva de l’utilisateur
ms.openlocfilehash: cf7e631970196b2995891ef302f9af33dd2ab0388b95a54ea04b4a3a24d0a838
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53864038"
---
# <a name="microsoft-viva-topics-security-and-privacy"></a>Sujets Microsoft Viva sécurité et confidentialité

Les rubriques utilisent les fonctionnalités de sécurité de contenu existantes dans Microsoft 365, ainsi que les contrôles administratifs, pour contrôler le contenu généré par l’IA qui est présenté aux utilisateurs de votre organisation. C’est la combinaison des paramètres de sécurité Microsoft 365 (autorisations pour les sites, fichiers et dossiers) et des paramètres d’administration Rubriques qui déterminent ce qu’un utilisateur donné peut voir dans les rubriques.

La configuration des rubriques ne modifie pas les contrôles d’accès existants sur le contenu de votre organisation. Les utilisateurs voient uniquement le contenu auquel ils ont accès.

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

- Les informations d’une rubrique ajoutée par l’IA ne sont visibles que pour les personnes ayant accès au contenu source.
- Le texte qui a été manuellement ajouté ou modifié par un collaborateur de rubrique ou un gestionnaire de connaissances est visible par tous les utilisateurs qui peuvent consulter cette rubrique.

Les visiteurs et les collaborateurs peuvent voir la liste des rubriques confirmées et publiées dans le centre de rubriques, mais les détails des rubriques qu’une personne donnée peut voir dépendent des autorisations dont elle dispose sur le matériel source et de la modification manuelle de la rubrique.

Le tableau suivant décrit ce que les utilisateurs (visiteurs de rubriques, collaborateurs et gestionnaires de connaissances) peuvent voir dans une rubrique donnée en fonction de leurs autorisations.

|Élément de rubrique|Ce que voient les utilisateurs|
|:---------|:------------------|
|Nom de la rubrique|Les utilisateurs peuvent voir le nom des rubriques dans le centre de rubriques. Certaines rubriques peuvent ne pas être visibles si les utilisateurs n’ont pas d’autorisations sur le contenu source ou ont une faible pertinence pour l’utilisateur.|
|Description de la rubrique|Les descriptions générées par l’intelligence artificielle ne sont visibles que pour les utilisateurs qui ont des autorisations sur le contenu source. Les descriptions entrées ou modifiées manuellement sont visibles par tous les utilisateurs.|
|Personnes|Les contacts épinglés sont visibles par tous les utilisateurs. Les contacts suggérés ne sont visibles que pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Fichiers|Les fichiers ne sont visibles que pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Pages|Les pages ne sont visibles que pour les utilisateurs qui ont des autorisations sur le contenu source.|
|Sites|Les sites ne sont visibles que pour les utilisateurs qui ont des autorisations sur le contenu source.|

## <a name="users-personal-and-private-data"></a>Données personnelles et privées des utilisateurs

Cette rubrique ne découvre que les rubriques des sites SharePoint que vous spécifiez. Le stockage personnel des utilisateurs, tel que les messages personnels ou les OneDrive n’est pas inclus.

## <a name="best-practices"></a>Meilleures pratiques

Les rubriques présentent des informations aux utilisateurs en fonction de leurs autorisations existantes sur le contenu. Microsoft 365 offre de nombreuses façons de s’assurer que le contenu sensible est limité aux utilisateurs appropriés. Au-delà des autorisations d’équipe ou [](../compliance/dlp-learn-about-dlp.md) de site standard, vous pouvez utiliser des étiquettes de sensibilité ou la protection contre la perte de données pour restreindre l’accès au contenu et aux révisions d’accès afin d’examiner régulièrement l’accès des utilisateurs aux informations [sensibles.](/azure/active-directory/governance/access-reviews-overview) [](../compliance/sensitivity-labels.md)

Nous vous recommandons d’utiliser ces outils pour vous assurer que vos autorisations de contenu sont définies correctement au sein de votre organisation. Les expériences de rubrique peuvent ensuite fournir des informations utiles et appropriées à vos utilisateurs.

S’il existe des rubriques que vous souhaitez exclure entièrement des expériences de rubrique, vous pouvez également :

- [Exclure les sites SharePoint sensibles de la découverte de rubrique.](topic-experiences-discovery.md#select-sharepoint-topic-sources) Le contenu de ces sites n’apparaît pas dans les expériences de rubrique.

- [Exclure les rubriques par leur nom.](topic-experiences-discovery.md#exclude-topics-by-name) Les rubriques explicitement exclues n’apparaissent pas dans les expériences de rubrique.

- Faire supprimer des rubriques dans le centre de rubriques par les gestionnaires de connaissances.

En outre, nous vous recommandons les meilleures pratiques ci-après :

- Embauchez des responsables de connaissances de différents secteurs de votre organisation. Le fait de disposer de gestionnaires de connaissances avec une grande variété d’expertise et d’accès au contenu sous-jacent utilisé par l’IA peut vous aider à organiser les connaissances les plus utiles pour vos utilisateurs et à supprimer les informations sensibles si elles sont trouvées.

- Configurer un flux de travail pour demander des modifications. Les gestionnaires de connaissances, les propriétaires d’équipe ou de site doivent avoir un processus par lequel ils peuvent demander l’exclusion de rubriques ou de sites au début de nouveaux projets au sein de votre organisation ou s’ils trouvent du contenu avec des paramètres d’autorisation inappropriés.

- Soyez attentif au public et du niveau de confidentialité des informations lorsque vous créez des descriptions de rubriques. Ces descriptions peuvent être visibles par les utilisateurs qui ne sont pas autorisés à accéder au contenu source de la rubrique.

Si vous pouvez modifier les autorisations sur les pages des rubriques individuelles pour restreindre l’accès à un groupe d’utilisateurs spécifique, nous vous déconseillons de mettre en place cette approche en raison du degré élevé d’effort d’administration requis.

## <a name="see-also"></a>Voir aussi

[Configurer Teams avec trois niveaux de protection](../solutions/configure-teams-three-tiers-protection.md)

[Planifier les expériences de sujets](plan-topic-experiences.md)

[Configurer les expériences de sujets](set-up-topic-experiences.md)
